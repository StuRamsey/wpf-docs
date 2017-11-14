---
layout: post
title: Axis and its types. 
description: Axis behavior and its types.
platform: wpf
control: SfChart
documentation: ug
---


# Axis

[`ChartAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis.html#) is used to locate a data point inside the chart area. Generally, to locate a data point two axes are required along vertical and horizontal direction. The vertical axis or y-axis usually represents numerical values. The horizontal axis or x-axis represents categorical or numerical or date and time values. 

The following are the API’s in ChartAxis

* [`ArrangeRect`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~ArrangeRect.html#) – Represents the bounds of chart axis size. 
* [`VisibleRange`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~VisibleRange.html#) – Represent the axis start and end values.
* [`VisibleLabels`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~VisibleLabels.html#) – Represents the axis label collection which are visible in axis.

The following topics explains in detail about the axis and its parts

## Header

In [`ChartAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis.html#) you can define any object as header using [`Header`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~Header.html#) property. The following code example demonstrates the defining header in primary and secondary axis. 

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Header="Metals"/>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Header="Values(In Tonnes)"/>

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis() { Header = "Medals" };

chart.SecondaryAxis = new NumericalAxis() { Header = "Values(In Tonnes)" };

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img1.jpeg)


**Header** **Customization**

Default appearance of the header can be customized using [`HeaderTemplate`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~HeaderTemplate.html#) property. The following code snippet demonstrates the header customization.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="headerTemplate1">

            <Border BorderBrush="Black" CornerRadius="5" BorderThickness="1">

                    <TextBlock Text="Demands" FontSize="12" 
                                   
                               FontStyle="Italic" 
                                   
                               FontWeight="Bold" Margin="3"/>

            </Border>

        </DataTemplate>

        <DataTemplate x:Key="headerTemplate2">

            <Border BorderBrush="Black" CornerRadius="5" BorderThickness="1">

                    <TextBlock FontSize="12" Margin="3"
                                   
                               FontStyle="Italic" FontWeight="Bold"/>

            </Border>

        </DataTemplate>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.PrimaryAxis>

        <syncfusion:CategoryAxis HeaderTemplate="{StaticResource headerTemplate1}"/>

    </syncfusion:SfChart.PrimaryAxis>

    <syncfusion:SfChart.SecondaryAxis>

        <syncfusion:NumericalAxis Header="Values(In Tonnes)"
                                          
                                  HeaderTemplate="{StaticResource headerTemplate2}"/>

    </syncfusion:SfChart.SecondaryAxis>
        
</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    HeaderTemplate = chart.Resources["headerTemplate1"] as DataTemplate

};

chart.SecondaryAxis = new NumericalAxis()
{

    HeaderTemplate = chart.Resources["headerTemplate2"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img2.jpeg)


**HeaderStyle**

[`HeaderStyle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~HeaderStyle.html#) property is used to provide style for the axis header. The following code example explains header style customization.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Header="Metals" >

<syncfusion:CategoryAxis.HeaderStyle>

<syncfusion:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Black"> 

</syncfusion:LabelStyle>

</syncfusion:CategoryAxis.HeaderStyle>

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Header="Values(In Tonnes)"/>

<syncfusion:NumericalAxis.HeaderStyle>

<syncfusion:LabelStyle FontFamily="Algerian" FontSize="13" Foreground="Black"> 

</syncfusion:LabelStyle>

</syncfusion:NumericalAxis.HeaderStyle>

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

LabelStyle style = new LabelStyle()
{

    FontFamily = new FontFamily("Algerian"),

    FontSize = 13,

    Foreground = new SolidColorBrush(Colors.Black)

};

chart.PrimaryAxis = new CategoryAxis()
{

    Header = "Medals",

    LabelStyle = style

};

chart.SecondaryAxis = new NumericalAxis()
{

    Header = "Values(In Tonnes)",

    LabelStyle = style

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img3.jpeg)

## Axis Labels

Labels will be generated by the range and the values binded to [`XBindingPath`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartSeriesBase~XBindingPath.html#) or [`YBindingPath`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.XyDataSeries~YBindingPath.html#) properties.



**Positioning** **the** **Labels**

The [`LabelsPosition`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsPosition.html#) property is used to position the axis label either inside or outside the chart plotting area. By default, LabelsPosition is outside.

**Inside**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  LabelsPosition="Inside">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    LabelsPosition = AxisElementPosition.Inside

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img4.jpeg)


**LabelRotationAngle**

[`LabelRotationAngle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelRotationAngle.html#) property allows you to define the angle for the label content. The following code example illustrates the [`LabelRotationAngle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelRotationAngle.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelRotationAngle="90" >

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

     LabelRotationAngle = 90

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img5.jpeg)

**Custom** **Labels**

SfChart allows user to define the labels for the axis. For defining the axis label you have to set the [`LabelContent`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxisLabel~LabelContent.html#) and [`Position`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxisLabel~Position.html#) property .You can define the labels using [`CustomLabels`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~CustomLabels.html#) property as in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis >

<syncfusion:CategoryAxis.CustomLabels>

<syncfusion:ChartAxisLabel Position="0" LabelContent="0-1"/>

<syncfusion:ChartAxisLabel Position="1" LabelContent="1-2"/>

<syncfusion:ChartAxisLabel Position="2" LabelContent="2-3"/>

<syncfusion:ChartAxisLabel Position="3" LabelContent="3-4"/>

<syncfusion:ChartAxisLabel Position="4" LabelContent="4-5"/>

<syncfusion:ChartAxisLabel Position="5" LabelContent="5-5"/>

</syncfusion:CategoryAxis.CustomLabels>

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

CategoryAxis axis = new CategoryAxis();

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 0, LabelContent = "0-1" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 1, LabelContent = "1-2" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 2, LabelContent = "2-3" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 3, LabelContent = "3-4" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 4, LabelContent = "4-5" });

axis.CustomLabels.Add(new ChartAxisLabel() { Position = 5, LabelContent = "5-5" });

chart.PrimaryAxis = axis;

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img6.jpeg)


You can also directly bind the collection of labels to the [`LabelsSource`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsSource.html#) property for defining custom labels. The following code example demonstrates the defining the label collection in code behind and binding the property in XAML page.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelsSource="{Binding Labels}" ContentPath="Content" PositionPath="Position">

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight C# %}

chart.PrimaryAxis = new CategoryAxis()
{

    ContentPath ="Content",

    PositionPath = "Position",

    LabelsSource = Labels

};


public List<LabelItem> Labels { get; set; }

Labels = new List<LabelItem>

{

    new LabelItem() {Position=0, Content = "0-1"},

    new LabelItem() {Position=1, Content = "1-2"},

    new LabelItem() {Position=2, Content = "2-3"},

    new LabelItem() {Position=3, Content = "3-4"},

    new LabelItem() {Position=4, Content = "4-5"},

    new LabelItem() {Position=5, Content = "5-6"},

    new LabelItem() {Position=6, Content = "6-7"},

    new LabelItem() {Position=7, Content = "7-8"},

};

public class LabelItem

{

    public string Content { get; set; }

    public int Position { get; set; }

}

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img7.jpeg)


**Label** **Formatting**

Axis labels can be formatting by predefined formatting types based on the axis types.

**DateTimeAxis**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis LabelFormat="MMM/dd" FontSize="12" >

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelFormat = "MM/dd",

    FontSize = 12

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img8.jpeg)


**TimeSpanAxis**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:TimeSpanAxis LabelFormat="g" ></syncfusion:TimeSpanAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new TimeSpanAxis()
{

    LabelFormat = "g",

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img9.jpeg)


**NumericalAxis**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis LabelFormat="0.00" />

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    LabelFormat = "0.00",

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img10.jpeg)


**Adding** **Units** **to** **Labels**

To display the measuring units, it can be added as a prefix or suffix to the axis labels. This can be achieved using the [`PrefixLabelTemplate`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~PrefixLabelTemplate.html#) and [`PostfixLabelTemplate`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~PostfixLabelTemplate.html#) properties.

**PrefixLabelTemplate**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="prefixLabelTemplate">

             <TextBlock FontSize="10" VerticalAlignment="Center" 
                               
                               Text="$"/>

        </DataTemplate>
                
    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.SecondaryAxis>

         <syncfusion:NumericalAxis FontSize="10" 
                                          
                                   PrefixLabelTemplate="{StaticResource prefixLabelTemplate}"/>

    </syncfusion:SfChart.SecondaryAxis>

 </syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    PrefixLabelTemplate = chart.Resources["prefixLabelTemplate"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img11.jpeg)


**PostfixLabelTemplate**

{% tabs %}

{% highlight xaml %}

  <syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="postfixLabelTemplate">

             TextBlock FontSize="10" VerticalAlignment="Center" Text="K"/>

        </DataTemplate>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.SecondaryAxis>

        <syncfusion:NumericalAxis FontSize="10" 
                                          
                                  PostfixLabelTemplate="{StaticResource postfixLabelTemplate}"/>

    </syncfusion:SfChart.SecondaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    PostfixLabelTemplate = chart.Resources["postfixLabelTemplate"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img12.jpeg)


**LabelTemplate**

[`LabelTemplate`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelTemplate.html#) property allows you to define the appearance for the axis labels .the following code example illustrates the [`LabelTemplate`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelTemplate.html#) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <DataTemplate x:Key="labelTemplate">

            <Border Background="Gray" CornerRadius="5" >

                    <TextBlock Text="{Binding LabelContent}" Foreground="White"
                                   
                                FontStyle="Normal" FontSize="10" 
                                   
                                FontWeight="Bold" Margin="3"/>

                    <Border.Effect>

                        <DropShadowEffect ShadowDepth="6" Direction="315"
                                              
                                          Color="LightGray" Opacity="0.25"
                                              
                                          BlurRadius="0.8" />

                    </Border.Effect>

            </Border>

       </DataTemplate>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.PrimaryAxis>

        <syncfusion:CategoryAxis LabelTemplate="{StaticResource labelTemplate}"/>

    </syncfusion:SfChart.PrimaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelTemplate = chart.Resources["labelTemplate"] as DataTemplate

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img13.jpeg)


**LabelExtent**

This property allows us to set the distance between the axis header and the axis using [`LabelExtent`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelExtent.html#) property.The following code snippet defines the [`LabelExtent`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelExtent.html#) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Header="Demand" LabelExtent="50" >

</syncfusion:CategoryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Header = "Demand",

    LabelExtent = 50

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img14.jpeg)


**Smart** **Axis** **Labels**

When there are more number of axis labels, they may overlap with each other. SfChart provides support to handle the overlapping labels using the [`LabelsIntersectAction`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsIntersectAction.html#) property. By default the [`LabelsIntersectAction`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsIntersectAction.html#) value is Hide.

The following are the options for intersecting action.

* None
* Hide
* MultipleRows
* Rotate

**None**

None option is used to display all the label even if it intersects. The following code snippet demonstrates the LabelsIntersectAction as None option.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelsIntersectAction="None"/>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelsIntersectAction = AxisLabelsIntersectAction.None

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img15.jpeg)


**Hide**

Hide option is used to hide the labels if it intersects .You can define the hide as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelsIntersectAction="Hide"/>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelsIntersectAction = AxisLabelsIntersectAction.Hide

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img16.jpeg)


**MultipleRows**

This option is used to move the labels to next row if it intersects .The following code demonstrates the MultipleRows option in [`LabelsIntersectAction`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsIntersectAction.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelsIntersectAction="MultipleRows">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelsIntersectAction = AxisLabelsIntersectAction.MultipleRows

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img17.jpeg)


**Auto**

This option in [`LabelsIntersectAction`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsIntersectAction.html#) property is used to rotate the labels if it intersects .The following code snippet and image demonstrates the rotate option in [`LabelsIntersectAction`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelsIntersectAction.html#) property.

{% tabs %}

{% highlight xml %}

<syncfusion:CategoryAxis LabelsIntersectAction="Auto">

</syncfusion:CategoryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelsIntersectAction = AxisLabelsIntersectAction.Auto

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img18.jpeg)


**EdgeLabelsDrawingMode**

SfChart provides support to customize the position of the edge labels in axis using the [`EdgeLabelsDrawingMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsDrawingMode.html#) property. [`EdgeLabelsDrawingMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsDrawingMode.html#) property default value is center.

The following are the customizing options in [`EdgeLabelsDrawingMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsDrawingMode.html#).

* Center- Positions the label with tick line as center.
* Fit- Position the gridline inside based on the edge label size.
* Hide- Hides the edge labels.
* Shift- Shifts the edge labels to the left or right so that it comes inside the chart area.

**Center**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Center" >

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Center

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img19.jpeg)

**Shift**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Shift" ></syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Shift

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img20.jpeg)


**Hide**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Hide">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Hide

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img21.jpeg)


**Fit**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  EdgeLabelsDrawingMode="Fit">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EdgeLabelsDrawingMode = EdgeLabelsDrawingMode.Fit

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img22.jpeg)


**EdgeLabelsVisibilityMode**

The visibility of the extreme labels of the axis can be controlled using [`EdgeLabelsVisibilityMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsVisibilityMode.html#) property. By default the default option in [`EdgeLabelsVisibilityMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsVisibilityMode.html#) is set, which displays the edge label based on auto interval calculations .The following image depicts the default option in [`EdgeLabelsVisibilityMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsVisibilityMode.html#) while zooming.

![](Axis_images/Axis_img23.jpeg)


**Always** **Visible**

AlwaysVisible option in [`EdgeLabelsVisibilityMode`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EdgeLabelsVisibilityMode.html#) is used to view the edge labels even while performing zooming.

The following code example and image demonstrates the AlwaysVisible option while zooming.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis EdgeLabelsVisibilityMode="AlwaysVisible" 

EnableScrollBar="True">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.AlwaysVisible

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img24.jpeg)


**Visible**

Visible option is used to display the edge labels (first and last label) irrespective of the auto interval calculation until zooming (i.e., in normal state)

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis EdgeLabelsVisibilityMode="Visible" EnableScrollBar="True" >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    EdgeLabelsVisibilityMode = EdgeLabelsVisibilityMode.Visible

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img25.jpeg)


**Axis Label Border**

[`ChartAxis`](https://help.syncfusion.com/wpf/sfchart/axis) provides support to place border around its label.To place the border around axis, we should enable  [`ShowLabelBorder`] property of axis and it can be set as shown in the below code snippet,

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis ShowLabelBorder="True"/>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

</syncfusion:NumericalAxis ShowLabelBorder="True"  />       

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
            
{
     ShowLabelBorder = true,                
};

chart.SecondaryAxis = new NumericalAxis()

{
    ShowLabelBorder = true
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/label1.png)

The border color and width can be customized with [`LabelBorderBrush`] and [`LabelBorderWidth`] properties of chart axis and it can be set as shown in the below code snippet,

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelBorderWidth="3" ShowLabelBorder="True" LabelBorderBrush="Red"/>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

</syncfusion:NumericalAxis ShowLabelBorder="True"  LabelBorderWidth="3" LabelBorderBrush="Red"/>       

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
            
{
    ShowLabelBorder = true,  

    LabelBorderWidth = 3,

    LabelBorderBrush = new SolidColorBrush(Colors.Red)
           
};

chart.SecondaryAxis = new NumericalAxis()

{
       ShowLabelBorder = true,

       LabelBorderWidth = 3,

       LabelBorderBrush = new SolidColorBrush(Colors.Red),
               
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/label2.png)


## Grid lines

By default, gridlines are automatically added to the [`ChartAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis.html#) in its defined intervals. SfChart supports customization of gridline. The visibility of the gridlines can be controlled using the [`ShowGridLines`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~ShowGridLines.html#) property.

The following code example illustrates the [`ShowGridLines`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~ShowGridLines.html#) property as false in the primary axis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  ShowGridLines="False"  >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    ShowGridLines = false
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img26.jpeg)


Style can also be applied to Major and Minor Gridlines using [`MajorGridLineStyle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~MajorGridLineStyle.html#) and [`MinorGridLineStyle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~MinorGridLineStyle.html#) properties.

**MajorGridLineStyle**

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

     <syncfusion:SfChart.Resources>

         <Style TargetType="Line" x:Key="lineStyle">

                <Setter Property="StrokeThickness" Value="2"/>

                <Setter Property="Stroke" Value="Black"/>

                <Setter Property="StrokeDashArray" Value="3,3"/>

        </Style>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.PrimaryAxis>

            <syncfusion:NumericalAxis MajorGridLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.PrimaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    MajorGridLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img27.jpeg)


**MinorGridLineStyle**

Minor gridlines will be added automatically when the small tick lines is defined inside the chart area.

{% tabs %}

{% highlight xaml %}

  <syncfusion:SfChart x:Name="chart">

      <syncfusion:SfChart.Resources>

            <Style TargetType="Line" x:Key="lineStyle">

                    <Setter Property="StrokeThickness" Value="1"/>

                    <Setter Property="Stroke" Value="DarkGray"/>

                    <Setter Property="StrokeDashArray" Value="3,3"/>

            </Style>

        </syncfusion:SfChart.Resources>

        <syncfusion:SfChart.SecondaryAxis>

                <syncfusion:NumericalAxis SmallTicksPerInterval="3" 
                                          
                                          MinorGridLineStyle="{StaticResource lineStyle}"/>

       </syncfusion:SfChart.SecondaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    SmallTicksPerInterval = 3,

    MinorGridLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img28.jpeg)


## Tick lines

Tick line are the small lines which is drawn on the axis line representing the axis labels .Tick lines will be drawn outside of the axis by default. 

**TickLineSize**

Tick lines thickness can be customized using [`TickLineSize`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~TickLineSize.html#) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  TickLineSize="10" ></syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

   TickLineSize = 10 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img29.jpeg)


**Positioning** **the** **Major** **Tick** **Lines**

Tick lines can be positioned inside or outside of the chart area using [`TickLinesPosition`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~TickLinesPosition.html#) property. By default the tick lines will positioned outside of the chart area. The following code example demonstrates the positioning tick lines inside chart area.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis TickLinesPosition="Inside">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

   TickLinesPosition = AxisElementPosition.Inside
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img30.jpeg)


**Customization**

Style can be applied to major tick lines using [`MajorTickLineStyle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~MajorTickLineStyle.html#) property .The following code snippet demonstrates the styling of major tick lines.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

    <syncfusion:SfChart.Resources>

        <Style TargetType="Line" x:Name="lineStyle">

            <Setter Property="StrokeThickness" Value="1"/>

            <Setter Property="Stroke" Value="Black"/>

            <Setter Property="StrokeDashArray" Value="3,3"/>

        </Style>

    </syncfusion:SfChart.Resources>

    <syncfusion:SfChart.SecondaryAxis>

                <syncfusion:NumericalAxis TickLineSize="10"
                                          
                                          MajorTickLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.SecondaryAxis>

 </syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    TickLineSize = 10,

    MajorTickLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img31.jpeg)


**MinorTickLines**

Minor tick lines can be added by defining [`SmallTicksPerInterval`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.RangeAxisBase~SmallTicksPerInterval.html#) property. This property will add the tick lines  to every interval.

The following code example demonstrates the small ticks set for every interval.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis Interval="1" SmallTicksPerInterval="4" >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    SmallTicksPerInterval = 4
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img32.jpeg)


**Positioning** **the** **minor** **tick** **lines**

Minor tick lines can be positioned inside or outside using [`SmallTickLinesPosition`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.RangeAxisBase~SmallTickLinesPosition.html#) property. By default the minor tick lines will be positioned outside.

The following code example demonstrates the positioning of minor tick lines inside the chart area.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis SmallTicksPerInterval="2" SmallTickLinesPosition="Inside">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    SmallTicksPerInterval = 2,

    SmallTickLinesPosition = AxisElementPosition.Inside
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img33.jpeg)


**Customization** **of** **Minor** **Ticklines**

The thickness of the minor tick lines can be customized using [`SmallTickLineSize`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.RangeAxisBase~SmallTickLineSize.html#) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis Interval="1" SmallTicksPerInterval="3" SmallTickLineSize="10">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    SmallTicksPerInterval = 3,

    SmallTickLineSize = 10
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img34.jpeg)

Styling customization of minor tick lines can be defined using [`MinorTickLineStyle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~MinorTickLineStyle.html#) property. The following code example and image demonstrates the style for minor tick lines.

{% tabs %}

{% highlight xaml %}

 <syncfusion:SfChart x:Name="chart">

     <syncfusion:SfChart.Resources>

                <Style TargetType="Line" x:Name="lineStyle" >

                    <Setter Property="StrokeThickness" Value="0.5"/>

                    <Setter Property="Stroke" Value="Black"/>

                </Style>

     </syncfusion:SfChart.Resources>

     <syncfusion:SfChart.SecondaryAxis>

            <syncfusion:NumericalAxis FontSize="12"  Interval="1"
                                          
                                      SmallTicksPerInterval="3" 
                                          
                                      TickLineSize="10" SmallTickLineSize="5"
                                          
                                      MinorTickLineStyle="{StaticResource lineStyle}"/>

    </syncfusion:SfChart.SecondaryAxis>

</syncfusion:SfChart>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    SmallTicksPerInterval = 3,

    TickLineSize = 10,

    SmallTickLineSize = 5

    MinorTickLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img35.jpeg)


N> For category axis, small tick lines is not applicable since it is rendered based on index positions.

## AxisLine

SfChart provides support to customize the style of the axis line by defining the [`AxisLineStyle`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~AxisLineStyle.html#) property as shown in the below code snippet.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  Interval="1" >

<syncfusion:NumericalAxis.AxisLineStyle>

<Style TargetType="Line"  >

<Setter Property="StrokeThickness" Value="2"/>

<Setter Property="Stroke" Value="Red"/>

<Setter Property="StrokeDashArray" Value="2,2"/>

</Style>

</syncfusion:NumericalAxis.AxisLineStyle>

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    Interval = 1,

    AxisLineStyle = chart.Resources["lineStyle"] as Style 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img36.jpeg)


**Applying** **Padding** **to** **the** **Axis** **line**

The padding to the axis line is defined using [`AxisLineOffset`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~AxisLineOffset.html#) property. The following code example demonstrates the setting [`AxisLineOffset`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~AxisLineOffset.html#) for x axis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis AxisLineOffset="20" >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    AxisLineOffset = 20
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img37.jpeg)


## Origin Customization

SfChart allows you to customize the origin.By default the axis will be rendered having (0,0) as origin in x and y axes.

**ShowAxisNextToOrigin**

[`ShowAxisNextToOrigin`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~ShowAxisNextToOrigin.html#) property is used to move the axis line to the origin value in [`Origin`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~Origin.html#) property based on the x or y axes. .The following code example demonstrates shifting the axis in the origin value in numerical axis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Origin="3" ShowAxisNextToOrigin="True">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Origin = 3,

    ShowAxisNextToOrigin = true 
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img38.jpeg)


**Positioning** **the** **Header** 

The following image demonstrates the default positioning of header when the axis is moved inside based on the origin value.

![](Axis_images/Axis_img39.jpeg)


If you want to position the header outside of the chart area then you can set the Far option in [`HeaderPosition`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~HeaderPosition.html#) property.

The following code example demonstrates the positioning of the header outside even when the axis is moved inside.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis HeaderPosition="Far"

Origin="3" ShowAxisNextToOrigin="True" Header="Value(In Tonnes)" >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Origin = 3,

    ShowAxisNextToOrigin = true,

    Header = "Value(In Tonnes)",

    HeaderPosition = AxisHeaderPosition.Far
    
};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img40.jpeg)


**Adding** **Origin** **line**

The origin line can be added to chart area by setting the [`ShowOrigin`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~ShowOrigin.html#) property to true .The following code example demonstrates the displaying origin line at (3,0) position value as set in [`Origin`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~Origin.html#) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Origin="3" ShowOrigin="True">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Origin = 3,

    ShowOrigin = true 

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img41.jpeg)


## Types of Axis

[`ChartAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis.html#) supports the following types.

* NumericalAxis
* CategoryAxis
* DateTimeAxis
* DateTimeCategoryAxis
* TimeSpanAxis
* LogarithmicAxis

You can choose any type of [`ChartAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis.html#), like [`DateTimeAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#), [`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#), [`CategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis.html#), [`LogarithmicAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.LogarithmicAxis.html#) or [`TimeSpanAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis.html#) depending on the value type. [`DateTimeCategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeCategoryAxis.html#) is a special type, used to plot date and time values for the given data points.

### NumericalAxis

[`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) is used to plot numerical values to the chart. [`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) can be defined for both [`PrimaryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.SfChart~PrimaryAxis.html#) and [`SecondaryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.SfChart~SecondaryAxis.html#). The following code snippet shows how to define the [`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis >

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis();

chart.SecondaryAxis = new NumericalAxis();

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img42.jpeg)


**Customizing** **the** **NumericalAxis** **Range**

[`Maximum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~Maximum.html#) property used for setting the maximum value for the axis range and [`Minimum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~Minimum.html#) property is used for setting the minimum value for the axis range.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Maximum="2750" Minimum="250" Interval="250">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Maximum = 2750,

    Minimum = 250,

    Interval = 250

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img43.jpeg)


N> If  minimum or maximum value is set, the other value is calculated by default internally.

**StartRangeFromZero**

[`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) will calculate the range based on the data points binded to the axis. To start the range from zero have to define the [`StartRangeFromZero`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~StartRangeFromZero.html#) property to True. The following code example demonstrates the NumericalAxis range starting from zero.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis StartRangeFromZero="True">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

   StartRangeFromZero = true

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img44.jpeg)


N> By default, Range is calculated between the minimum and maximum value of the data points.

### CategoryAxis

[`CategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis.html#) is an indexed based axis that plots values based on the index of the data point collection. The points are equally spaced here. The following code example initializes the [`CategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis >

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis();

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img45.jpeg)


**LabelPlacement**

In [`CategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis.html#), labels is placed based on tick lines using [`LabelPlacement`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis~LabelPlacement.html#) property. By default the labels is placed OnTicks. The following code example demonstrates placing the label between ticks in [`CategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis.html#)

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis LabelPlacement="BetweenTicks">

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    LabelPlacement = LabelPlacement.BetweenTicks

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img46.jpeg)


### DateTimeAxis

[`DateTimeAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is used to plot DateTime values. The [`DateTimeAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) is widely used to make financial charts in places like the Stock Market, where index plotting is done every day.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  LabelFormat="MMM-dd"></syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    LabelFormat = "MMM-dd"

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img47.jpeg)


**Customizing** **the** **Range**

[`Minimum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~Minimum.html#) and [`Maximum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~Maximum.html#) properties behavior is same as in NumericalAxis instead of setting numerical value, you have to set date time values.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  Minimum="2015/01/10" Maximum="2015/07/01" LabelFormat="MMM-dd" 

IntervalType="Months" Interval="1">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    Minimum = new DateTime(2015,01,10),

    Maximum = new DateTime(2015,07,01),

    LabelFormat = "MMM-dd",

    IntervalType = DateTimeIntervalType.Months,

    Interval = 1

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img48.jpeg)


**Business** **Hours** **Range** **Calculation**

SfChart provides support to plot only the business hours in DateTimeAxis.This support is enabled by setting [`EnableBusinessHours`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~EnableBusinessHours.html#) property to true.

The following properties are used for business hour range calculation

* [`OpenTime`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~OpenTime.html#)- Represents the open working time of a day.
* [`CloseTime`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~CloseTime.html#)- Represents the close working time of a day.
* [`WorkingDays`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~WorkingDays.html#)- Represents the working days of a week.

The following code snippet demonstrates the business hours support in DateTimeAxis

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis EnableBusinessHours="True" OpenTime="9" 

CloseTime="24" WorkingDays="Friday,Saturday,Sunday,Monday,Tuesday,Wednesday,Sunday">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    EnableBusinessHours = true,

    OpenTime = 9,

    CloseTime = 24,

    WorkingDays = Day.Friday | Day.Saturday | Day.Sunday |
                Day.Monday | Day.Tuesday| Day.Wednesday| Day.Sunday

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img49.jpeg)


### DateTimeCategoryAxis

[`DateTimeCategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeCategoryAxis.html#) is a special type of axis used mainly with financial series. All the data points are plotted with equal spaces, similar to [`CategoryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CategoryAxis.html#), thereby removing space for missing dates. Intervals and range for the axis are calculated similar to [DateTimeAxis](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#). There are no visual gaps between points, even when the difference between two points is more than a year.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeCategoryAxis LabelFormat="MMM-dd" >

</syncfusion:DateTimeCategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeCategoryAxis()
{

    LabelFormat = "MMM-dd"

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img50.jpeg)


### TimeSpan Axis

[`TimeSpanAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis.html#) is used to plot the time span values in the [`PrimaryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.SfChart~PrimaryAxis.html#). [`TimeSpanAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis.html#) has the advantage of plotting data with milliseconds difference. The limitation of [`TimeSpanAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis.html#) is that it can only accept timespan values (hh:mm:ss) and date time values are not accepted.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:TimeSpanAxis >

</syncfusion:TimeSpanAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new TimeSpanAxis();

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img51.jpeg)


**Customizing** **the** **Range**

The following code snippet demonstrates the [`Minimum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis~Minimum.html#) and [`Maximum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis~Maximum.html#) properties for [`TimeSpanAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.TimeSpanAxis.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:TimeSpanAxis Minimum="00:00:00" Maximum="00:10:00">

</syncfusion:TimeSpanAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new TimeSpanAxis()
{

    Minimum = new TimeSpan(00, 00, 00),

    Maximum = new TimeSpan(00, 10, 00)

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img52.jpeg)


### LogarithmicAxis

[`LogarithmicAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.LogarithmicAxis.html#) is used to plot the logarithmic scale for the chart. The Logarithmic values will be plotted based on the logarithmic base value as 10.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:LogarithmicAxis />

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new LogarithmicAxis();

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img53.jpeg)


**Logarithmic** **Base**

You can also change the base for logarithmic values. By default the logarithmic values is calculated the base from 10.The following code example demonstrates the logarithmic values in y axis calculated from base 2.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:LogarithmicAxis LogarithmicBase="2">

</syncfusion:LogarithmicAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new LogarithmicAxis()
{

    LogarithmicBase = 2

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img54.jpeg)


**Customizing** **the** **Range**

The following code snippet demonstrates the range customization of [`LogarithmicAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.LogarithmicAxis.html#) based on [`Minimum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.LogarithmicAxis~Minimum.html#) and [`Maximum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.LogarithmicAxis~Maximum.html#) properties.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:LogarithmicAxis Minimum="100" Maximum="7000" >

</syncfusion:LogarithmicAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new LogarithmicAxis()
{

    Minimum = 100,

    Maximum = 7000

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img55.jpeg)


## Customizing the Intervals

[`ChartAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis.html#) calculates the range and intervals automatically based on the data points. The axis range and interval can be defined using the [`Minimum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~Minimum.html#), [`Maximum`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~Maximum.html#) and [`Interval`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~Interval.html#) properties.

**NumericalAxis**

The following code snippet demonstrates the interval customization in NumericalAxis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis Interval="250">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    Interval = 250

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img56.jpeg)


**CategoryAxis**

The following code snippet demonstrates the interval customization in CategoryAxis.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:CategoryAxis Interval="2">

</syncfusion:CategoryAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new CategoryAxis()
{

    Interval = 2

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img57.jpeg)

**DateTimeAxis**

The DateTimeAxis interval value corresponds to the type specified in the [`IntervalType`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~IntervalType.html#) property.

For instance, if the Interval is set as 2 and [`IntervalType`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~IntervalType.html#) is set as Days, the labels are plotted for every two days. The following are the options for [`IntervalType`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~IntervalType.html#) property

Auto
* Days
* Hours
* Milliseconds
* Minutes
* Months
* Seconds
* Years

The default [`IntervalType`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis~IntervalType.html#) of a [`DateTimeAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis_members.html#) is Auto. It calculates the type automatically and the interval, accordingly.

The following code snippet demonstrates the DateTimeAxis having one month interval.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  Interval="1"  IntervalType="Months" LabelFormat="MMM-dd"></syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    Interval = 1,

    IntervalType = DateTimeIntervalType.Months,

    LabelFormat = "MMM-dd"

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img58.jpeg)


**DesiredIntervalsCount**

[`DesiredIntervalsCount`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~DesiredIntervalsCount.html#) property is used to specify the count of the axis labels between the first and last label. The following sample code defines the [`DesiredIntervalsCount`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~DesiredIntervalsCount.html#) property.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis DesiredIntervalsCount="7">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    DesiredIntervalsCount = 7

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img59.jpeg)


**Maximum** **Labels**

[`MaximumLabels`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~MaximumLabels.html#) property defines the count of the axis labels in the 100 pixels.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis  MaximumLabels="2">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

<syncfusion:ColumnSeries ItemsSource="{Binding Demands}" XBindingPath="Demand" YBindingPath="Year2010">

<syncfusion:ColumnSeries.YAxis>

<syncfusion:NumericalAxis MaximumLabels="2" >

</syncfusion:NumericalAxis>

</syncfusion:ColumnSeries.YAxis>

</syncfusion:ColumnSeries>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
{

    MaximumLabels = 2

};

NumericalAxis axis = new NumericalAxis() { MaximumLabels = 2 };

ColumnSeries series = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2010",

    YAxis = axis

};

chart.Series.Add(series);

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img60.jpeg)


## Apply Padding to the Range

The [`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#) and [`DateTimeAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.DateTimeAxis.html#) have a [`RangePadding`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~RangePadding.html#) property that can be used to add padding to the range of a chart’s axes.

### DateTimeRangePadding

By default the date time range padding is auto.

![](Axis_images/Axis_img61.jpeg)

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="Additional">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.Additional

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img62.jpeg)


**Round**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="Round">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.Round

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img63.jpeg)


**None**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:DateTimeAxis  RangePadding="None">

</syncfusion:DateTimeAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new DateTimeAxis()
{

    RangePadding = DateTimeRangePadding.None

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img64.jpeg)


### NumericalRangePadding

The following types are available for [`NumericalAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis.html#):

* Additional
* None
* Normal
* Round
* Auto

By default, the default [`RangePadding`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.NumericalAxis~RangePadding.html#) value for [`PrimaryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.SfChart~PrimaryAxis.html#) is Auto and for [`SecondaryAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.SfChart~SecondaryAxis.html#), the default value is Round.

![](Axis_images/Axis_img65.jpeg)


**Normal**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="Normal">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.Additional

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img66.jpeg)


**Additional**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="Additional">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.Additional

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img67.jpeg)


**None**

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  RangePadding="None">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    RangePadding = NumericalPadding.None

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img68.jpeg)


##  Applying Padding to the Axis

[`PlotOffset`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~PlotOffset.html#) property is used to provide padding to the axis. The following code snippet demonstrates the padding applied to both x and y axes.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  PlotOffset="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

<syncfusion:SfChart.SecondaryAxis>

<syncfusion:NumericalAxis PlotOffset="30">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    PlotOffset = 30

};

chart.SecondaryAxis = new NumericalAxis()
{

    PlotOffset = 30

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img69.jpeg)


## Auto Interval Calculation on Zooming

[`EnableAutoIntervalOnZooming`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EnableAutoIntervalOnZooming.html#) property is used to maintain the interval even it is in zooming state only if we set the interval to the axis. Default value of this property is true. While zooming based on the auto range padding the interval will be calculated.

![](Axis_images/Axis_img70.jpeg)


If you set [`EnableAutoIntervalOnZooming`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~EnableAutoIntervalOnZooming.html#) as False, the intervals will be calculated on the interval based on the axis while zooming.

{% tabs %}

{% highlight xaml %}

<syncfusion:SfChart.PrimaryAxis>

<syncfusion:NumericalAxis  EnableScrollBar="True" Interval="1"

EnableAutoIntervalOnZooming="False">

</syncfusion:NumericalAxis>

</syncfusion:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis = new NumericalAxis()
{

    EnableScrollBar = true,

    EnableAutoIntervalOnZooming = false,

    Interval = 1

};

{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img71.jpeg)


## Multiple Axes

SfChart provides a way to arrange multiple series inside the same chart area, giving the chart more space than x-axis and y-axis. These axes can be arranged in a stacking order or in a side by side pattern.

By default, all the series are plotted based on primary and secondary axis. You can add more axes by adding additional axis to the series. There are two properties [`XAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CartesianSeries~XAxis.html#) and [`YAxis`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.CartesianSeries~YAxis.html#) in all the series type which is used to provide Multiple axes support, except [`AccumulationSeries`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.AccumulationSeriesBase.html#).

{% tabs %}

{% highlight xaml %}

<syncfusion:ColumnSeries ItemsSource="{Binding Demands}"

XBindingPath="Demand"  YBindingPath="Year2011">

</syncfusion:ColumnSeries>

<syncfusion:LineSeries  ItemsSource="{Binding Demands}"

XBindingPath="Date"  YBindingPath="Year2011">

<syncfusion:LineSeries.XAxis>

<syncfusion:DateTimeAxis />

</syncfusion:LineSeries.XAxis>

<syncfusion:LineSeries.YAxis>

<syncfusion:NumericalAxis/>

</syncfusion:LineSeries.YAxis>

</syncfusion:LineSeries>

{% endhighlight %}

{% highlight c# %}

ColumnSeries series1 = new ColumnSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Demand",

    YBindingPath = "Year2011"
    
};

LineSeries series2 = new LineSeries()
{

    ItemsSource = new ViewModel().Demands,

    XBindingPath = "Date",

    YBindingPath = "Year2011",

};

series2.XAxis = new DateTimeAxis()
{

    Header = "Additional X Axis"

};

series2.YAxis = new NumericalAxis()
{

    Header = "Additional Y Axis"

};

chart.Series.Add(series1);

chart.Series.Add(series2);


{% endhighlight %}

{% endtabs %}

![](Axis_images/Axis_img72.jpeg)

In the above image, the LineSeries is plotted based on additional X & Y axis and ColumnSeries (or remaining series) is plotted against the primary and secondary axis.


## Multi-level Labels

[`Axis`](https://help.syncfusion.com/wpf/sfchart/axis) can be customized with multiple levels of label by using its [`MultiLevelLabels`] property. These labels are placed based on the provided [`Start`] and [`End`] range values and we can add any number of labels to an axis. The below code snippet shows how to set a multilevel label,

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5" Text="Quarter 1" />

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
     ShowLabelBorder = true,
            
};
            
ChartMultiLevelLabel label = new ChartMultiLevelLabel()
           
{
 
       Start = -0.5,

       End = 2.5,

       Text = "Quarter 1"

};

chart.PrimaryAxis.MultiLevelLabels.Add(label);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label3.png)

**Regarding** **Start** **and** **End** **Property**

[`Start`] and [`End`] properties of [`ChartMultiLevelLabel`] are type of objects, we can provide the start and end values for a multi-level label based on its Axis type. It is described  in the following table,

<table>
<tr>
<th>S.No</th>
<th>Axis Type</th>
<th>Start/End value</th>
<th>Example</th>
</tr>
<tr>
<td>1</td>
<td>CategoryAxis</td>
<td>Index-Based</td>
<td>Start=0(zeroth index position) End = 1(first index position)</td>
</tr>
<tr>
<td>2</td>
<td>DateTimeCategoryAxis</td>
<td>Index-Based</td>
<td>Start = 0(zeroth index position) End = 1(first index position)</td>
</tr>
<tr>
<td>3</td>
<td>NumericalAxis</td>
<td>Value-Based</td>
<td>Start= 5( Value) End= 10( Value)</td>
</tr>
<tr>
<td>4</td>
<td>LogarithmicAxis</td>
<td>Value-Based</td>
<td>Start= 10(Value) End= 1000(Value)</td>
</tr>
<tr>
<td>5</td>
<td>DateTimeAxis</td>
<td>Value-Based</td>
<td>Start = "2017/01/01" End="2017/01/02"</td>
</tr>
<tr>
<td>6</td>
<td>TimeSpanAxis</td>
<td>Value-Based</td>
<td>Start = "00:00:01" End="00:00:05"</td>
</tr>
</table>


**Customizing** **multi-level** **labels**

**Border** **Customization**

[`ChartMultiLevelLabel's`] border width and color can be customized with [`LabelBorderWidth`] and [`LabelBorderBrush`] properties of chart axis.It can be set as shown in the below code snippet,

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis  LabelBorderBrush="Red" LabelBorderWidth="3"  ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5" Text="Quarter 1"  />

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
    LabelBorderWidth = 3,

    ShowLabelBorder = true,

    LabelBorderBrush = new SolidColorBrush(Colors.Red),
            
};
            
ChartMultiLevelLabel label = new ChartMultiLevelLabel()
           
{
 
       Start = -0.5,

       End = 2.5,

       Text = "Quarter 1",

       BorderWidth = 4

};

chart.PrimaryAxis.MultiLevelLabels.Add(label);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label4.png)


**Border** **Type**

[`Chart Axis`]((https://help.syncfusion.com/wpf/sfchart/axis)) provides support to various types of border for [`ChartMultiLevelLabels`] and it can be applied by using its [`MultiLevelLabelsBorderType`] property.The default [`MultiLevelLabelsBorderType`] is [`Rectangle`]. The another supported border types are [`Brace`],[`None`] and [`WithoutTopAndBottomBorder`].

**Rectangle**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis  ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1" />

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2"/>

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3"/>

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4"/>

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis  ShowLabelBorder="True">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low"/>

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium"/>

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High"/>
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
     ShowLabelBorder = true,          
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1",
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{
      ShowLabelBorder = true,
};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low"
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label5.png)


**Brace**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis MultiLevelLabelsBorderType="Brace" ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1"  />

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2"  />

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3"  />

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4" />

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis MultiLevelLabelsBorderType="Brace" ShowLabelBorder="True">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low" />

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium"/>

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High" />
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
   ShowLabelBorder = true,
  
   MultiLevelLabelsBorderType = BorderType.Brace
            
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1",
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2",
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3",
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4",
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{
   ShowLabelBorder = true,

   MultiLevelLabelsBorderType = BorderType.Brace
};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low",
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium",
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High",
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);


{% endhighlight %}

{% endtabs %}

![](Axis_images/label6.png)

**None**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis  MultiLevelLabelsBorderType="None" ShowLabelBorder="True">

<chart:CategoryAxis>

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1" />

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2" />

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3" />

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4" />

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis MultiLevelLabelsBorderType="None" ShowLabelBorder="True">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low" />

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium" />

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High" />
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>


{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
    ShowLabelBorder = true,          

    MultiLevelLabelsBorderType = BorderType.None
            
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3"
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{
    
    ShowLabelBorder = true,          

    MultiLevelLabelsBorderType = BorderType.None

};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low"
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);


{% endhighlight %}

{% endtabs %}

![](Axis_images/label7.png)

**WithoutTopAndBottomBorder**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis   ShowLabelBorder="True" MultiLevelLabelsBorderType="WithoutTopAndBottomBorder">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1"/>

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2" />

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3" />

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4" />

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis  ShowLabelBorder="True" MultiLevelLabelsBorderType="WithoutTopAndBottomBorder">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low" />

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium"/>

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High"/>
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
   ShowLabelBorder = true,

   MultiLevelLabelsBorderType = BorderType.WithoutTopAndBottomBorder
            
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1",
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2",
           
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3",
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4",
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{
    
    ShowLabelBorder = true,

   MultiLevelLabelsBorderType = BorderType.WithoutTopAndBottomBorder

};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low",
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium",
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High",
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label8.png)


**Text** **Customization**

[`ChartMultiLevelLabel's`] text can be customized with its [`FontSize`], [`FontFamily`] and [`Foreground`] property and it is shown in below code snippet,

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis  ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="11.5" FontFamily="Algerian" Foreground="Blue" FontSize="14" Text="Year - 2016"/>

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
      ShowLabelBorder = true,            
};
            
ChartMultiLevelLabel label = new ChartMultiLevelLabel()
           
{
 
    Start = -0.5,
                
    End = 11.5,
                
    Text = "Year - 2016",
                
    Foreground = new SolidColorBrush(Colors.Blue),
                
    FontSize = 14,
                
    FontFamily = new FontFamily("Algerian")

};

chart.PrimaryAxis.MultiLevelLabels.Add(label);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label9.png)


**Label** **Alignment**

The text of [`ChartMultiLevelLabel`] can be aligned with its [`LabelAlignment`] property. The default value of [`LabelAlignment`] property is Center.

**Center**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis  ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1" />

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2"/>

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3"/>

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4"/>

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis ShowLabelBorder="True">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low"/>

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium"/>

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High"/>
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
     ShowLabelBorder = true,                       
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1",
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4"
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{
      ShowLabelBorder = true,            
};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low"
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label13.png)


**Near**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1"   LabelAlignment="Near" />

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2"  LabelAlignment="Near"/>

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3"  LabelAlignment="Near"/>

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4"  LabelAlignment="Near"/>

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis ShowLabelBorder="True">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low"  LabelAlignment="Near"/>

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium"  LabelAlignment="Near"/>

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High"  LabelAlignment="Near"/>
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
    ShowLabelBorder = true,                       
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1",
    
     LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2",

    LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3",

    LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4",

     LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{   
    ShowLabelBorder = true,            
};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low",

     LabelAlignment = LabelAlignment.Near
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium",

    LabelAlignment = LabelAlignment.Near
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High",

     LabelAlignment = LabelAlignment.Near
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label10.png)


**Far**

{% tabs %}

{% highlight xaml %}

<chart:SfChart.PrimaryAxis>

<chart:CategoryAxis  ShowLabelBorder="True">

<chart:CategoryAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="-0.5" End="2.5"  Text="Quarter 1"   LabelAlignment="Far" />

<chart:ChartMultiLevelLabel Start="2.5" End="5.5" Text="Quarter 2"  LabelAlignment="Far"/>

<chart:ChartMultiLevelLabel Start="5.5" End="8.5" Text="Quarter 3"  LabelAlignment="Far"/>

<chart:ChartMultiLevelLabel Start="8.5" End="11.5" Text="Quarter 4"  LabelAlignment="Far"/>

</chart:CategoryAxis.MultiLevelLabels>

</chart:CategoryAxis>

</chart:SfChart.PrimaryAxis>

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis  ShowLabelBorder="True">
                    
<chart:NumericalAxis.MultiLevelLabels>
                    
<chart:ChartMultiLevelLabel Start="32" End="36"  Text="Low"  LabelAlignment="Far"/>

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium"  LabelAlignment="Far"/>

<chart:ChartMultiLevelLabel Start="42" End="48" Text="High" LabelAlignment="Far"/>
                    
</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.PrimaryAxis =  new CategoryAxis()
            
{
      ShowLabelBorder = true,          
};

ChartMultiLevelLabel label1 = new ChartMultiLevelLabel()
            
{
                
     Start = -0.5,

     End = 2.5,

     Text = "Quarter 1",
    
     LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label1);

ChartMultiLevelLabel label2 = new ChartMultiLevelLabel()
           
{
    
    Start = 2.5,
                
    End = 5.5,
                
    Text = "Quarter 2",

    LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label2);

ChartMultiLevelLabel label3 = new ChartMultiLevelLabel()

{
     
    Start = 5.5,
                
    End = 8.5,
                
    Text = "Quarter 3",

    LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label3);

ChartMultiLevelLabel label4 = new ChartMultiLevelLabel()

{
     Start = 8.5,
               
     End = 11.5,
                
     Text = "Quarter 4",

     LabelAlignment = LabelAlignment.Near
            
};

chart.PrimaryAxis.MultiLevelLabels.Add(label4);

chart.SecondaryAxis = new NumericalAxis()

{
      ShowLabelBorder = true,          
};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
     Start = 32,
                
     End = 36,
     
     Text = "Low",

     LabelAlignment = LabelAlignment.Near
            
};
            
chart.SecondaryAxis.MultiLevelLabels.Add(label5);
            
ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
    Start = 36,
                
    End = 42,
    
    Text = "Medium",

    LabelAlignment = LabelAlignment.Near
};

chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
     Start = 42,
     
     End = 48,
    
     Text = "High",

     LabelAlignment = LabelAlignment.Near
};

chart.SecondaryAxis.MultiLevelLabels.Add(label7);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label11.png)

The text of [`ChartMultiLavelLabel`] text will automatically trim, when the text width exceeds the width of [`ChartMultiLevelLabel`] and it is shown below,

{% tabs %}

{% highlight xaml %}

<chart:SfChart.SecondaryAxis>

<chart:NumericalAxis ShowLabelBorder="True">

<chart:NumericalAxis.MultiLevelLabels>

<chart:ChartMultiLevelLabel Start="32" End="36" Text="Low Temperature"/>

<chart:ChartMultiLevelLabel Start="36" End="42" Text="Medium Temperature"/>
                        
<chart:ChartMultiLevelLabel Start="42" End="48" Text="High Temperature"/>

</chart:NumericalAxis.MultiLevelLabels>

</chart:NumericalAxis>

</chart:SfChart.SecondaryAxis>

{% endhighlight %}

{% highlight c# %}

chart.SecondaryAxis = new NumericalAxis()
            
{
     ShowLabelBorder = true,          
};

ChartMultiLevelLabel label5 = new ChartMultiLevelLabel()
            
{
                
        Start = 32,
        
        End = 36,
        
        Text = "Low Temperature"
};

chart.SecondaryAxis.MultiLevelLabels.Add(label5);

ChartMultiLevelLabel label6 = new ChartMultiLevelLabel()

{
        Start = 36,
                
        End = 42,
        
        Text = "Medium Temperature"
            
};
    
chart.SecondaryAxis.MultiLevelLabels.Add(label6);

ChartMultiLevelLabel label7 = new ChartMultiLevelLabel()

{
                
       Start = 42,
               
       End = 48,
       
       Text = "High Temperature"
 
 };

 chart.SecondaryAxis.MultiLevelLabels.Add(label7);

{% endhighlight %}

{% endtabs %}

![](Axis_images/label12.png)


## Events

* [`ActualRangeChanged`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~ActualRangeChanged_EV.html#)   - Occurs at the when the range is changed in the axis.
* [`LabelCreated`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelCreated_EV.html#)- Occurs when labels is created.
* [`AxisBoundChanged`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~AxisBoundsChanged_EV.html#)- Occurs when the bounds of the axis changed.
* [`LabelClicked`](http://help.syncfusion.com/cr/cref_files/wpf/sfchart/Syncfusion.SfChart.WPF~Syncfusion.UI.Xaml.Charts.ChartAxis~LabelCreated_EV.html#)- Occurs when labels are clicked. Supports for 2D axis.
