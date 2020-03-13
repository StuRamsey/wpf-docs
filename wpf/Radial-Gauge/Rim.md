---
layout: post
title: Rim | SfCircularGauge | Wpf | Syncfusion
description: Rim 
platform: wpf
control: SfCircularGauge
documentation: ug
---

# Rim 

Scale determines the structure of a circular gauge by using a circular rim. By setting the `StartAngle` and `SweepAngle` properties, you can change the shape of the circular gauge to a full-circular gauge, half-circular gauge, or quarter-circular gauge.

The `StartValue` and `EndValue` properties determine the overall range of the circular rim.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge  HeaderAlignment="Bottom">

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale StartAngle="270" SweepAngle="360" StartValue="0" EndValue="360"
                                     Interval="20" MinorTicksPerInterval="0" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale circularScale = new CircularScale();

circularScale.StartAngle = 270;

circularScale.SweepAngle = 360;

circularScale.StartValue = 0;

circularScale.EndValue = 360;

circularScale.Interval = 20;

circularScale.MinorTicksPerInterval = 0;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

circularScale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(circularScale);

{% endhighlight %}

{% endtabs %}

![Rim startValue enadValue image](Rim_images/Rim_StartValue_EnadValue.png)

## Rim customization

The color and thickness of the rim can be set by using the `RimStroke` and `RimStrokeThickness` properties.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale RadiusFactor="1" RimStrokeThickness="40" RimStroke="SkyBlue" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

 SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale circularScale = new CircularScale();

circularScale.RadiusFactor = 1;

circularScale.RimStrokeThickness = 40;

circularScale.RimStroke = new SolidColorBrush(Colors.SkyBlue);

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

circularScale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(circularScale);

{% endhighlight %}

{% endtabs %}

![Rim customization image](Rim_images/Rim_customization.png)

## Setting position for rim

You can customize the position of [`Scales`](https://help.syncfusion.com/cr/cref_files/wpf/gauge/Syncfusion.Gauge.WPF~Syncfusion.Windows.Gauge.CircularGauge~Scales.html) in the following two ways:
1.	 `RadiusFactor` property.
2.	 `Radius` property.

### Setting radius factor for rim

The value for `RadiusFactor` should be specified in offset value. 

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge>

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale RadiusFactor="0.7" RimStrokeThickness="30" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>
                
    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale circularScale = new CircularScale();

circularScale.RadiusFactor = 0.7;

circularScale.RimStrokeThickness = 30;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

circularScale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(circularScale);

{% endhighlight %}

{% endtabs %}

![Rim with RadiusFactor image](Rim_images/Rim_with_RadiusFactor.png)

### Setting radius for rim

You can set the `Radius` of rim in pixel value.

{% tabs %}

{% highlight xml %}

    <gauge:SfCircularGauge  HeaderAlignment="Bottom">

    <gauge:SfCircularGauge.Scales>

    <gauge:CircularScale Radius ="100" >

    <gauge:CircularScale.Pointers>

    <gauge:CircularPointer NeedlePointerVisibility="Hidden"/>

    </gauge:CircularScale.Pointers>

    </gauge:CircularScale>

    </gauge:SfCircularGauge.Scales>

    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

SfCircularGauge sfCircularGauge = new SfCircularGauge();

CircularScale circularScale = new CircularScale();

circularScale.Radius = 100;

CircularPointer circularPointer = new CircularPointer();

circularPointer.NeedlePointerVisibility = Visibility.Hidden;

circularScale.Pointers.Add(circularPointer);

sfCircularGauge.Scales.Add(circularScale);

{% endhighlight %}

{% endtabs %}

![Rim with Radius image](Rim_images/Rim_with_Radius.png)

### Show rim

The `ShowRim` property is a Boolean property, which is used to enable or disable the rim in circular gauge.

N> Default value of the ShowRim property is true.

{% tabs %}

{% highlight xml %}

       <gauge:SfCircularGauge  HeaderAlignment="Bottom">
           <gauge:SfCircularGauge.Scales >
                 <gauge:CircularScale ShowRim="False" x:Name="scale" >
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
            mainscale.ShowRim = false;
            CircularPointer circularPointer = new CircularPointer();
            circularPointer.NeedlePointerVisibility = Visibility.Hidden;
            mainscale.Pointers.Add(circularPointer);
            sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Show rim support in WPF Circular Gauge](Rim_images/show-rim.png)

### StartOffset and EndOffset for rim

* `StartOffset` - Sets the rim start offset position. Its range is from 0 to 1.
* `EndOffset` - Sets the rim end offset position. Its range is from 0 to 1.

{% tabs %}

{% highlight xml %}

        <gauge:SfCircularGauge x:Name="gauge">
             <gauge:SfCircularGauge.Scales >
                  <gauge:CircularScale  x:Name="scale" RimStartOffset="0.6" RimEndOffset="0.7" RimStroke="LightGray"  >
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
            mainscale.RimStroke = new SolidColorBrush(Colors.LightGray);
            mainscale.RimStartOffset = 0.6;
            mainscale.RimEndOffset = 0.7;
            CircularPointer circularPointer = new CircularPointer();
            circularPointer.NeedlePointerVisibility = Visibility.Hidden;
            mainscale.Pointers.Add(circularPointer);
            sfCircularGauge.Scales.Add(mainscale);
			
{% endhighlight %}

{% endtabs %}

![Start and End offset support in WPF Circular Gauge rim](Rim_images/rim-offset.png)