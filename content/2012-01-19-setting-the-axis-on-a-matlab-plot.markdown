---
layout: post
title: "Setting the Axis on a MATLAB Plot"
date: 2012-01-19 06:00
comments: true
categories: matlab
---
I ran into a situation where I was progromatically making a plot and I wanted it to be formatted correctly each time. This saves me effort from having to manually fix aspects of the plot that aren’t set. 

The trouble is, MATLAB doesn’t make this particularly easy. There’s lots of figure handles and such that need to be manipulated. Here’s a code snippet that a) creates a figure b) lets you manually set the axis properties and c) plots data on that axis. 

```matlab
figure(2); % Create figure #2. Note this figure does NOT have an axis associated  
		% with it. If you call 'hold on' it WILL create a default axis.
axes1 = axes('Parent',gcf,'YScale','log','YMinorTick','on',...
    'YMinorGrid','on',...
    'YGrid','on',...
    'XGrid','on'); % Creates a semilog axis with logarithmic y-axis, etc.
hold(axes1,'all'); % Prevents subsequent plots from changing the axis property
plot(...,'Parent',axes1);  % Plot data on this new axis. I don't think this is strictly 
 % necessary, but can help if you have trouble.
```

So, there you go. Don’t forget you can use the following to add title, labels, and set the axis limits:

```matlab
title({'Title line 1','Title line 2'},'FontSize',12);
xlabel('X label','FontSize',12);
ylabel('Y label','FontSize',12);
ylim([1e-012 1]);
xlim([1 10]);
```