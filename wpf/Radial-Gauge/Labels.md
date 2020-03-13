---
layout: post
title: Labels | SfCircularGauge | Wpf | Syncfusion
description: This section describes the label stroke customization, label font customization, setting position for labels, setting smart labels for SfCircularGauge control.
platform: wpf
control: SfCircularGauge
documentation: ug
---

# CircularScale Labels customization

The `Scale` labels associate numeric values with major scale tick marks.

## Label stroke customization

The label color can be changed using the `LabelStroke` property.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale LabelStroke="DeepPink">

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.LabelStroke = new SolidColorBrush(Colors.DeepPink);

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Label stroke customization image](Labels_images/Label_Stroke_customization.png)

## Label font customization

The label font can be customized using the `FontSize`, `FontFamily`, and `FontStyle` properties.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale FontFamily="Monotype Corsiva" FontSize="20" 

    FontStyle="Italic" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>
                        
    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

sfCircularGauge.FontSize = 20;

sfCircularGauge.FontFamily = new FontFamily("Monotype Corsiva");

sfCircularGauge.FontStyle = FontStyles.Italic;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Label font customization image](Labels_images/Label_Font_customization.png)

## Setting position for labels

  The `Labels` can be placed inside the scale, outside the scale, or on the scale using the following two ways:
     
     1. Placing the labels by selecting one of the options available in the `LabelPosition` property.

      They are,

1.	Inside (Default)

2.	Outside

3.	Custom

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale LabelPosition="Outside" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.LabelPosition = LabelPosition.Outside;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Setting position for labels image](Labels_images/Setting_Position_for_labels.png)

2.	Positioning the labels far away from the ticks using the `LabelOffset` property. First, set the `LabelPosition` to custom, and then position the label using the `LabelOffset` property.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale LabelPosition="Custom" LabelOffset="0.5" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.LabelPosition = LabelPosition.Custom;

mainscale.LabelOffset = 0.5;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Positioning labels image](Labels_images/Positioning_labels .png)

### Setting smart labels

Smart labels allow to change the numeric scale type of the labels displayed in a gauge scale and customize the labels by adding prefixes or suffixes to the scale labels.

### Enable/disable smart labels

The `EnableSmartLabels` property is a Boolean property that enables or disables the smart label feature of the circular gauge.

## Setting numeric scale type

The `NumericScaleType` property allows to set the type of label. The following types can be applied to labels:

•	Auto

•	Thousands

•	Millions

•	Billions

•	Trillions

•	Quadrillions

•	Quintillions

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale StartValue="0" EndValue="500" EnableSmartLabels="True" NumericScaleType="Thousands">

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.StartValue = 0;

mainscale.EndValue = 500;

mainscale.EnableSmartLabels = true;

mainscale.NumericScaleType = NumericScaleType.Thousands;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Setting smart labels image](Labels_images/Setting_Smart_labels.png)

## Setting number of fraction digits for labels

The `NoOfFractionDigit` property is used to set the number of fractional digits to be displayed in the scale labels.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale NoOfFractionalDigit="3">

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.NoOfFractionalDigit = 3;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Fraction_Digits_fo_lables](Labels_images/Fraction_Digits_for_lables.png)

## Setting postfix and prefix for labels

You can postfix/prefix values to the scale labels using the `LabelPostfix` and `LabelPrefix` properties, respectively.

### Label postfix

The `LabelPostfix` property allows to postfix the values to the scale labels.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale LabelPostfix="k">

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.LabelPostfix = "k";

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Postfix for lables image](Labels_images/Postfix_for_lables.png)

### Label prefix

The `LabelPrefix` property allows to prefix the values to the scale labels.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale LabelPrefix="$">

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale mainscale = new CircularScale();

mainscale.LabelPrefix = "$";

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

mainscale.Pointers.Add(circularPointer);

{% endhighlight %}

{% endtabs %}

![Prefix for lables image](Labels_images/Prefix_for_lables.png)

### Show labels

The `ShowLabels` property is a Boolean property, which is used to enable or disable the labels in circular gauge.

N> Default value of the ShowLabels property is true.

{% tabs %}

{% highlight xml %}

      <gauge:SfCircularGauge>
           <gauge:SfCircularGauge.Scales >
                 <gauge:CircularScale ShowLabels="False" x:Name="scale" RimStroke="LightGray" >
                        <gauge:CircularScale.Pointers>
                            <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>
                        </gauge:CircularScale.Pointers>
                    </gauge:CircularScale>
                </gauge:SfCircularGauge.Scales>
		</gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

 SfCircularGauge sfCircularGauge = new SfCircularGauge();
            CircularScale mainscale = new CircularScale();
            mainscale.ShowLabels = false;
			mainscale.RimStroke = new SolidColorBrush(Colors.LightGray);
            CircularPointer circularPointer = new CircularPointer();
            circularPointer.NeedlePointerVisibility = Visibility.Hidden;
            mainscale.Pointers.Add(circularPointer);
            sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![WPF Circular Gauge Label Image](Labels_images/Show-labels.png)

### Edge label customization

You can customize the edge label by using the `ShowFirstLabel` and `ShowLastLabel` properties, which are Boolean properties.

* `ShowFirstLabel` property is used to enable or disable first label. Default value of the ShowFirstLabel property is true.

* `ShowLastLabel` property is used to enable or disable the last label. Default value of the ShowLastLabel property is true.

{% tabs %}

{% highlight xml %}

      <gauge:SfCircularGauge>
           <gauge:SfCircularGauge.Scales >
                 <gauge:CircularScale ShowFirstLabel = "False" StartValue = "0" EndValue = "12" Interval ="1" MinorTicksPerInterval = "5" StartAngle = "270" SweepAngle = "360" x:Name="scale" RimStroke="LightGray" >
                        <gauge:CircularScale.Pointers>
                            <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>
                        </gauge:CircularScale.Pointers>
                    </gauge:CircularScale>
                </gauge:SfCircularGauge.Scales>
		</gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

            SfCircularGauge sfCircularGauge = new SfCircularGauge();
            CircularScale mainscale = new CircularScale();
            mainscale.StartValue = 0;
            mainscale.Interval = 1;
            mainscale.MinorTicksPerInterval = 5;
            mainscale.EndValue = 12;
            mainscale.StartAngle = 270;
            mainscale.SweepAngle = 360;
            mainscale.ShowFirstLabel = false;
            mainscale.RimStroke = new SolidColorBrush(Colors.LightGray);
            CircularPointer circularPointer = new CircularPointer();
            circularPointer.NeedlePointerVisibility = Visibility.Hidden;
            mainscale.Pointers.Add(circularPointer);
            sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![WPF Circular Gauge Label Image](Labels_images/Label-edge-customization.png)

## Events

You can change the default label by hooking the `LabelCreated` event. Based on your requirements, the labels can be changed by using the `LabelText` property of `LabelCreatedEventArgs`.

{% tabs %}

{% highlight xml %}

       <gauge:SfCircularGauge>
            <gauge:SfCircularGauge.Scales >
                    <gauge:CircularScale  x:Name="scale"  LabelCreated="scale_LabelCreated" SweepAngle="360" StartAngle="270" StartValue="0" EndValue="16" Interval="2" RimStroke="LightGray" MinorTicksPerInterval="1" ShowLastLabel="False"  >
                        <gauge:CircularScale.Pointers>
                            <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>
                        </gauge:CircularScale.Pointers>
                    </gauge:CircularScale>
             </gauge:SfCircularGauge.Scales>
		</gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

            SfCircularGauge sfCircularGauge = new SfCircularGauge();
            CircularScale mainscale = new CircularScale();
            mainscale.StartValue = 0;
            mainscale.Interval = 2;
            mainscale.MinorTicksPerInterval = 1;
            mainscale.EndValue = 16;
            mainscale.StartAngle = 270;
            mainscale.SweepAngle = 360;
			mainscale.LabelCreated += scale_LabelCreated;
            mainscale.ShowLastLabel = false;
            mainscale.RimStroke = new SolidColorBrush(Colors.LightGray);
            CircularPointer circularPointer = new CircularPointer();
            circularPointer.NeedlePointerVisibility = Visibility.Hidden;
            mainscale.Pointers.Add(circularPointer);
            sfCircularGauge.Scales.Add(mainscale);
			
		   private void scale_LabelCreated(object sender, LabelCreatedEventArgs e)
           {
            switch ((string)e.LabelText)
            {

                case "0":
                    e.LabelText = "N";
                    break;
                case "2":
                    e.LabelText = "NE";
                    break;
                case "4":
                    e.LabelText = "E";
                    break;
                case "6":
                    e.LabelText = "SE";
                    break;
                case "8":
                    e.LabelText = "S";
                    break;
                case "10":
                    e.LabelText = "SW";
                    break;
                case "12":
                    e.LabelText = "W";
                    break;
                case "14":
                    e.LabelText = "NW";
                    break;
            }
        }

{% endhighlight %}

{% endtabs %}

![Label Created Event Image](Labels_images/Label_Created.png)