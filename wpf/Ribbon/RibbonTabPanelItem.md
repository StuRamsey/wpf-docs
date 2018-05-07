---
layout: post
title: Ribbon TabPanelItem for Syncfusion's Ribbon control for WPF
description: Ribbon TabPanelItem for Syncfusion's Ribbon control for WPF
platform: wpf
control: Ribbon
documentation: ug
---
# Ribbon TabPanelItem

`RibbonTabPanelItem` is used to display items below application Close button and above the `RibbonBar` content area. It is usually aligned in the right side of the Ribbon and we can place desire items like emoji's, help button etc., in this Tab panel.


{% tabs %}

{% highlight XAML %}

<syncfusion:Ribbon Name="_ribbon" HorizontalAlignment="Stretch" VerticalAlignment="Top">
<syncfusion:RibbonTab Name="_ribbonTab" Caption="HOME"  IsChecked="True">
<syncfusion:RibbonBar Name="_ribbonBar">
<syncfusion:RibbonMenuItem  Header="NEW" Width="100"></syncfusion:RibbonMenuItem>
</syncfusion:RibbonBar>
</syncfusion:RibbonTab>
<syncfusion:Ribbon.TabPanelItem>
<syncfusion:RibbonButton SizeForm="Small" Label="Help"/>
</syncfusion:Ribbon.TabPanelItem>
</syncfusion:Ribbon>

{% endhighlight %}

{% endtabs %}

Create instance of RibbonButton and assign it to TabPanelItem property of Ribbon through code behind.

{% tabs %}

{% highlight C# %}

RibbonButton _ribbonButton = new RibbonButton() { Label="Help"};
_ribbon.TabPanelItem = _ribbonButton;

{% endhighlight %}

{% highlight VB %}

Dim _ribbonButton As New RibbonButton() With {.Label="Help"}
_ribbon.TabPanelItem = _ribbonButton

{% endhighlight %}
 
{% endtabs %}

![](RibbonTabPanelItem_images/RibbonTabPanelItem_img1.jpg)


