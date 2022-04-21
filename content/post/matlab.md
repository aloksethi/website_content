---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Matlab Plots"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2019-11-01T14:33:41+02:00
lastmod: 2019-11-01T14:33:41+02:00
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
tags: ["Matlab"]
---
Different color names, marker styles and line styles 
```
% color names and markers
color_name = {'red','green', 'blue', 'black', 'magenta', 'cyan', 'yellow'};
line_style = {':','--','-'};
marker_style = {'o','v','^','s','d','p'};
```
Clearing a figure
```
fig_handle = figure(fig_num);
clf(fig_num); %clear the figure
```

Setting font of the axis and text
```
% for arial
set(0,'defaultAxesFontName', 'Arial')
set(0,'defaultTextFontName', 'Arial')

% for Times new roman
set(0,'defaultAxesFontName', 'Times') 
set(0,'defaultTextFontName', 'Times')
```

Setting font size and weight of the axis labels
```
handle_axis = get(gca, 'Xlabel');
set(handle_axis, 'FontSize', 10, 'FontWeight', 'bold')
handle_axis = get(gca, 'Ylabel');
set(handle_axis, 'FontSize', 10, 'FontWeight', 'bold')
```
Legend options
```
legend('FE_{4/1} + FE_{8/1}','FE_{4/1} + FE_{8/2}' ,'FontName', 'Arial', 'FontSize', 12, 'Location', 'best', 'box','off') % box options helps if figure is small and legend text is big
```

Tags that can be used with `plot`
```
'Color', color_name{1}
'LineStyle', line_style{1}
'LineWidth', 1.5
'Marker', marker_style{1} 
'MarkerEdgeColor', color_name{1}
'MarkerFaceColor', [0.5,0.5,0.5]
'MarkerSize', 8
``` 
Adding latex equations
```
eqtext = '$$F_n={1 \over \sqrt{5}}';
eqtext = [eqtext '\left[\left({1+\sqrt{5}\over 2}\right)^n -'];
eqtext = [eqtext '\left({1-\sqrt{5}\over 2}\right)^n\right]$$'];

text(1, 5, eqtext, 'Interpreter', 'Latex', 'FontSize', 12, 'Color', 'k')
```

Split figures (Method 1, using subplot)
```
%% subplots with a main title and separate titles

sgtitle('Main title') %sgtitle is 

subplot(2,2,1)
plot(x_data, y_data,'-r'), grid on, title('subplot1'),legend('Simulated'), xlabel('X'), ylabel('Y')

subplot(2,2,2)
plot(x_data, y_data,'-g'), grid on, title('subplot2'),legend('Simulated'), xlabel('X'), ylabel('Y')

subplot(2,2,3)
plot(x_data, y_data,'-b'), grid on, title('subplot3'),legend('Simulated'), xlabel('X'), ylabel('Y')

subplot(2,2,4)
plot(x_data, y_data,'-k'), grid on, title('subplot4'),legend('Simulated'), xlabel('X'), ylabel('Y')
```

Split figures (Method 2, using nexttile)
```
fig_num = 2;
hf = figure(fig_num);
clf(fig_num)

t_handle = tiledlayout(hf, 2,1, 'Padding', 'tight', 'TileSpacing', 'compact'); 

ah=nexttile;
hold on
ah.Box='on'; % for having a box
title('4 sub-arrays combining: Single RFIC','FontSize',12)
grid on
 
xticklabels('')

ah=nexttile;
hold on
ah.Box='on';

% this creates title for individual tile
title('4 sub-arrays combining: Two RFICs','FontSize',12)
grid on
 
% this creates lable for whole figure 
xlabel(t_handle, 'Azimuth Angle (degrees)', 'FontName', 'Arial', 'FontWeight', 'Bold')
ylabel(t_handle, 'Normalized Beam Pattern (dB)', 'FontName', 'Arial', 'FontWeight', 'Bold')
```
Two Y axis
```
yyaxis left
plot(x_data,y_data,'-r')

yyaxis right
plot(x_data,10-y_data,'-g')
```
Axis limits
```
xlim([-10 10])
ylim([-10 10])
```
Getting rid of tick labels
```
 xticklabels('')
```
Exporting figure for publication
```
% this is inbuilt now
hf = figure(fig_num);
filename = '..\figures\rad_pat.pdf';

exportgraphics(hf, filename,'BackgroundColor','none','ContentType','vector')
% export_fig('-transparent','untitled.pdf') %this is an external funciton
```

Importing data from virtuoso that was exported via VIVA
```
importdata('filename.matlab',',',1) %comma is delimmiter and 1 is number of header lines
```

Importing S parameters
```
sparam_fname = 'mmcov4_LNA_testline_smpm_conn2.s2p';
sobj = sparameters(sparam_fname);

freq = sobj.Frequencies/1e9;
s11 = squeeze(sobj.Parameters(1,1,:));
s21 = 20*log10(abs(squeeze(sobj.Parameters(2,1,:))));
```

Importing data from excel files
```
% excel file has different sheets named, 'ant', 'mmwbus', 'mmwbusinterchip'. Each sheet has a header too.
% the structure will have memebers as name of those headers.

excel_fname = 'pcb_losses.xlsx';
ant_losses = readtable(excel_fname, 'Sheet', 'ant');
mbus_losses = readtable(excel_fname, 'Sheet', 'mmwbus');
mbus_interchip_losses = readtable(excel_fname, 'Sheet', 'mmwbusinterchip');

fdata_mchip = mbus_interchip_losses.freq/1e9;
mchip_vloss = 10.^(mbus_interchip_losses.V_S21/10); % excel sheet has a header named "V_S21"
mchip_hloss = 10.^(mbus_interchip_losses.H_S21/10);
mean_mchip_loss = 10*log10(abs((mchip_vloss + mchip_hloss)/2));
```