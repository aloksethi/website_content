---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Debugging STM32 using STM32CubeIDE"
subtitle: "Using Serial Wire Viewer (SWV) to have a fast trace function."
summary: ""
authors: []
tags: [STM32, ITM, SWO]
categories: []
date: 2021-01-22T14:53:46+02:00
lastmod: 2021-01-22T14:53:46+02:00
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
Instrumentation Trace Macrocell (ITM) unit is a trace source that can be used for debugging. Detailed information is available in ARM Cortex manual [Cortex M4 TRM](https://developer.arm.com/documentation/100166/0001/Instrumentation-Trace-Macrocell-Unit/ITM-functional-description), [CoreSight TRM](https://developer.arm.com/documentation/ddi0314/h/preface/about-this-book/using-this-book).

## uC side
I don't really understand the complete mechanism of tracing and all the acronyms around it. However, what I got from skimming the manuals and forums is that there is probably no configuration required in the firmware that is running on the uC. All it has to do is call ```ITM_SendChar()``` function with a byte of data. So, a sample implementation might look something like the following (Originally from uOS).

```
#include <stdio.h>
#include <stdarg.h>
#include "stm32f4xx.h" -->

#define TRACE_BUFF (64)

static ssize_t trace_write (const char* buf, size_t nbyte)
{
  for (size_t i = 0; i < nbyte; i++)
    {

      ITM_SendChar(*(buf+i));
    }

  return (ssize_t)nbyte; // all characters successfully sent
}

int trace_printf(const char* format, ...)
{
  static char buf[TRACE_BUFF];
  int ret;
  va_list ap;

  va_start (ap, format);


  // Print to the local buffer
  ret = vsnprintf (buf, sizeof(buf), format, ap);
  if (ret > 0)
    {
      // Transfer the buffer to the device
      ret = trace_write (buf, (size_t)ret);
    }

  va_end (ap);
  return ret;
}

```
```ITM_SendChar()``` function is defined in CMSIS drivers (core_m4.h in case of STM32F429).
## Debugger side
Traces will only come