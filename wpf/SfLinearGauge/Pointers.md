---
layout: post
title: Pointers | Linear Gauge | WPF | Syncfusion
description: Pointers in WPF Linear Gauge are used to indicate the value of an attribute.
platform: wpf
control: SfLinearGauge
documentation: ug
---

# Pointers

The `LinearGauge` provides support to mark values using the `BarPointer` and `SymbolPointer`.

## Bar pointer

`BarPointer` is used to mark scale values. It starts at the beginning of gauge and ends at the pointer value. You can add bar pointer using the `PointerType` property. 

{% tabs %}

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray"

     MinorTickStroke="Gray" LabelStroke="#424242" ScaleBarSize="20" MinorTicksPerInterval="3">

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer PointerType="BarPointer" Value="75" BarPointerStroke="#36D1DC"

    BarPointerStrokeThickness="10"/>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

            SfLinearGauge sfLinearGauge = new SfLinearGauge();

            LinearScale linearScale = new LinearScale();

            linearScale.ScaleBarStroke = new SolidColorBrush(Color.FromRgb(224, 224, 224));

            linearScale.MajorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.MinorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.LabelStroke = new SolidColorBrush(Color.FromRgb(66, 66, 66));

            linearScale.ScaleBarSize = 20;

            linearScale.MinorTicksPerInterval = 3;

            LinearPointer linearPointer1 = new LinearPointer();

            linearPointer1.PointerType = LinearPointerType.BarPointer;

            linearPointer1.Value = 75;

            linearPointer1.BarPointerStroke = new SolidColorBrush(Color.FromRgb(54, 209, 220));

            linearPointer1.BarPointerStrokeThickness = 10;

            linearScale.Pointers.Add(linearPointer1);

            sfLinearGauge.MainScale = linearScale;

{% endhighlight %}

{% endtabs %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img1.png)

### Bar pointer customization

The UI of `Bar pointer` is customized using the `BarPointerStroke` and `BarPointerStrokeThickness` properties.

{% tabs %}

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray" MinorTickStroke="Gray" LabelStroke="#424242"

    ScaleBarSize="20" MinorTicksPerInterval="3">

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer PointerType="BarPointer" Value="75" BarPointerStroke="Orange"

    BarPointerStrokeThickness="10"/>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

            SfLinearGauge sfLinearGauge = new SfLinearGauge();

            LinearScale linearScale = new LinearScale();

            linearScale.ScaleBarStroke = new SolidColorBrush(Color.FromRgb(224, 224, 224));

            linearScale.MajorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.MinorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.LabelStroke = new SolidColorBrush(Color.FromRgb(66, 66, 66));

            linearScale.ScaleBarSize = 20;

            linearScale.MinorTicksPerInterval = 3;

            LinearPointer linearPointer1 = new LinearPointer();

            linearPointer1.PointerType = LinearPointerType.BarPointer;

            linearPointer1.Value = 75;

            linearPointer1.BarPointerStroke = new SolidColorBrush(Colors.Orange);

            linearPointer1.BarPointerStrokeThickness = 10;

            linearScale.Pointers.Add(linearPointer1);

            sfLinearGauge.MainScale = linearScale;

{% endhighlight %}

{% endtabs %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img2.png)

## Symbol pointer

In `SymbolPointer`, the value is pointed by a symbol on the scale.

{% tabs %}

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale  ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray"

    MinorTickStroke="Gray" LabelStroke="#424242"

    ScaleBarSize="10" MinorTicksPerInterval="3">

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer PointerType="SymbolPointer" Value="60"

    SymbolPointerHeight="15" SymbolPointerWidth="15"

    SymbolPointerPosition="Above" SymbolPointerStroke="#5B86E5"/>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

            SfLinearGauge sfLinearGauge = new SfLinearGauge();

            LinearScale linearScale = new LinearScale();

            linearScale.ScaleBarStroke = new SolidColorBrush(Color.FromRgb(224, 224, 224));

            linearScale.MajorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.MinorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.LabelStroke = new SolidColorBrush(Color.FromRgb(66, 66, 66));

            linearScale.ScaleBarSize = 10;

            linearScale.MinorTicksPerInterval = 3;

            LinearPointer linearPointer = new LinearPointer();

            linearPointer.PointerType = LinearPointerType.SymbolPointer;

            linearPointer.Value = 60;

            linearPointer.SymbolPointerHeight = 15;

            linearPointer.SymbolPointerWidth = 15;

            linearPointer.SymbolPointerPosition = LinearSymbolPointersPosition.Above;

            linearPointer.SymbolPointerStroke = new SolidColorBrush(Color.FromRgb(91, 134, 229));

            linearScale.Pointers.Add(linearPointer);

            sfLinearGauge.MainScale = linearScale;

{% endhighlight %}

{% endtabs %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img3.png)

### Symbol pointer customization

You can modify the size of symbol pointer by changing the `SymbolPointerHeight` and `SymbolPointerWidth` properties. The stroke of symbol pointer is changed using the `SymbolPointerStroke` property. 

{% tabs %}

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray"

    MinorTickStroke="Gray" LabelStroke="#424242"

    ScaleBarSize="10" MinorTicksPerInterval="3">

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer   PointerType="SymbolPointer" Value="60"

    SymbolPointerHeight="15" SymbolPointerWidth="20"

    SymbolPointerStroke="DeepSkyBlue"/>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

            SfLinearGauge sfLinearGauge = new SfLinearGauge();

            LinearScale linearScale = new LinearScale();

            linearScale.ScaleBarStroke = new SolidColorBrush(Color.FromRgb(224, 224, 224));

            linearScale.MajorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.MinorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.LabelStroke = new SolidColorBrush(Color.FromRgb(66, 66, 66));

            linearScale.ScaleBarSize = 10;

            linearScale.MinorTicksPerInterval = 3;

            LinearPointer linearPointer = new LinearPointer();

            linearPointer.PointerType = LinearPointerType.SymbolPointer;

            linearPointer.Value = 60;

            linearPointer.SymbolPointerHeight = 15;

            linearPointer.SymbolPointerWidth = 20;

            linearPointer.SymbolPointerStroke = new SolidColorBrush(Colors.DeepSkyBlue);

            linearScale.Pointers.Add(linearPointer);

            sfLinearGauge.MainScale = linearScale;

{% endhighlight %}

{% endtabs %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img4.png)

## Positioning symbol pointer

The `SymbolPointer` in the scale can be placed above, below, or in between the scale by choosing the following options available in the `SymbolPointerPosition` property:

1.	Above

2.	Below (Default)

3.	Cross

{% tabs %}

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray"

    MinorTickStroke="Gray" LabelStroke="#424242"

    ScaleBarSize="10" MinorTicksPerInterval="3" >

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer  PointerType="SymbolPointer" Value="60"

    SymbolPointerPosition="Cross" SymbolPointerHeight="10" SymbolPointerWidth="10"

    SymbolPointerStroke="#5B86E5"/>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

            SfLinearGauge sfLinearGauge = new SfLinearGauge();

            LinearScale linearScale = new LinearScale();

            linearScale.ScaleBarStroke = new SolidColorBrush(Color.FromRgb(224, 224, 224));

            linearScale.MajorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.MinorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.LabelStroke = new SolidColorBrush(Color.FromRgb(66, 66, 66));

            linearScale.ScaleBarSize = 10;

            linearScale.MinorTicksPerInterval = 3;

            LinearPointer linearPointer = new LinearPointer();

            linearPointer.PointerType = LinearPointerType.SymbolPointer;

            linearPointer.Value = 60;

            linearPointer.SymbolPointerPosition = LinearSymbolPointersPosition.Cross;

            linearPointer.SymbolPointerHeight = 10;

            linearPointer.SymbolPointerWidth = 10;

            linearPointer.SymbolPointerStroke = new SolidColorBrush(Color.FromRgb(91, 134, 229));

            linearScale.Pointers.Add(linearPointer);
  
            sfLinearGauge.MainScale = linearScale;

{% endhighlight %}

{% endtabs %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img5.png)

### Change symbol pointer shapes

The `SymbolPointerStyle` property is used to select symbol pointer style.

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray"

    MinorTickStroke="Gray" LabelStroke="#424242"

    ScaleBarSize="10" MinorTicksPerInterval="3">

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer PointerType="SymbolPointer" Value="60"SymbolPointerStyle="Custom">

    <gauge:LinearPointer.SymbolPointerTemplate>
                               
    <DataTemplate>

    <Rectangle Width="10" Height="10" Stroke="Red" StrokeThickness="10">

    </Rectangle>

    </DataTemplate>
                                
    </gauge:LinearPointer.SymbolPointerTemplate>
                            
    </gauge:LinearPointer>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img6.png)

### Adding multiple pointers

In addition to the default pointer, you can add "n" number of pointers to a linear scale using the `Pointers` property.

{% tabs %}

{% highlight xml %}

    <gauge:SfLinearGauge>

    <gauge:SfLinearGauge.MainScale>

    <gauge:LinearScale ScaleBarStroke="#E0E0E0" MajorTickStroke="Gray"
    MinorTickStroke="Gray" LabelStroke="#424242"
    ScaleBarSize="20" MinorTicksPerInterval="3">

    <gauge:LinearScale.Pointers>

    <gauge:LinearPointer PointerType="SymbolPointer" Value="60"
     SymbolPointerHeight="15" SymbolPointerWidth="15" SymbolPointerPosition="Above" SymbolPointerStroke="#5B86E5"/>

    <gauge:LinearPointer PointerType="BarPointer" Value="75" BarPointerStroke="#36D1DC" BarPointerStrokeThickness="10"/>

    </gauge:LinearScale.Pointers>

    </gauge:LinearScale>

    </gauge:SfLinearGauge.MainScale>

    </gauge:SfLinearGauge>

{% endhighlight %}

{% highlight c# %}

           SfLinearGauge sfLinearGauge = new SfLinearGauge();

            LinearScale linearScale = new LinearScale();

            linearScale.ScaleBarStroke = new SolidColorBrush(Color.FromRgb(224, 224, 224));

            linearScale.MajorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.MinorTickStroke = new SolidColorBrush(Colors.Gray);

            linearScale.LabelStroke = new SolidColorBrush(Color.FromRgb(66, 66, 66));

            linearScale.ScaleBarSize = 20;

            linearScale.MinorTicksPerInterval = 3;

            LinearPointer linearPointer1 = new LinearPointer();

            linearPointer1.PointerType = LinearPointerType.BarPointer;

            linearPointer1.Value = 75;

            linearPointer1.BarPointerStroke = new SolidColorBrush(Color.FromRgb(54, 209, 220));

            linearPointer1.BarPointerStrokeThickness = 10;

            linearScale.Pointers.Add(linearPointer1);

            LinearPointer linearPointer = new LinearPointer();

            linearPointer.PointerType = LinearPointerType.SymbolPointer;

            linearPointer.Value = 60;

            linearPointer.SymbolPointerHeight = 15;

            linearPointer.SymbolPointerWidth = 15;

            linearPointer.SymbolPointerPosition = LinearSymbolPointersPosition.Above;

            linearPointer.SymbolPointerStroke = new SolidColorBrush(Color.FromRgb(91, 134, 229));

            linearScale.Pointers.Add(linearPointer);

            sfLinearGauge.MainScale = linearScale;


{% endhighlight %}

{% endtabs %}

![Pointers - Linear Gauge](Pointers_images/Pointers_img7.png)