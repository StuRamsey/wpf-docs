---
layout: post
title: ToolTip Support | SfDateTimeRangeNavigator | wpf | Syncfusion
description: tooltip support
platform: wpf
control: SfDateTimeRangeNavigator
documentation: ug
---

# Tooltip Support

The date-time range navigator control provides tooltip support to sliders. Sliders are used to select a particular region of data in the control. Tooltips for sliders show the selected start and end date-time values. You can view the exact date values with the milliseconds precision.

## Properties

The following properties are used to customize the tooltip settings:

### Property

<table>
<tr>
<th>
Property Name</th><th>
Description</th></tr>
<tr>
<td>
ShowToolTip</td><td>
Shows or hides the tooltip.</td></tr>
<tr>
<td>
ToolTipLabelFormat</td><td>
Sets the date-time label format for the tooltip.</td></tr>
<tr>
<td>
LeftToolTipTemplate</td><td>
Sets the data template for the left tooltip.</td></tr>
<tr>
<td>
RightToolTipTemplate</td><td>
Sets the data template for the right tooltip.</td></tr>
</table>

{% tabs %}

{% highlight xaml %}

<chart:SfDateTimeRangeNavigator x:Name="RangeNavigator" 

ItemsSource="{Binding StockPriceDetails}" XBindingPath="_Date" 

ShowToolTip="true" ToolTipLabelFormat ="MMM/dd/yyyy">

<chart:SfDateTimeRangeNavigator.LeftToolTipTemplate>

<DataTemplate>

-----------------------

</DataTemplate>

</chart:SfDateTimeRangeNavigator.LeftToolTipTemplate>

<chart:SfDateTimeRangeNavigator.Content>

</chart:SfDateTimeRangeNavigator.Content>

</chart:SfDateTimeRangeNavigator>

{% endhighlight %}

{% highlight c# %}

SfDateTimeRangeNavigator rangeNavigator = new SfDateTimeRangeNavigator()
{

    ItemsSource = new ViewModel().StockPriceDetails,

    XBindingPath = "Date",

    ShowToolTip = true,

    ToolTipLabelFormat = "yyyy/MMM/dd",

    LeftToolTipTemplate = grid.Resources["tooltipTemplate"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![](ToolTip-Support_images/ToolTip-Support_img1.png)
