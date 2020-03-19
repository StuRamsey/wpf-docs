---
layout: post
title: Annotations support for Syncfusion SfCircularGauge control in WPF.
description: This section describes Setting view to annotation and it's feature in SfCircularGauge control WPF platform.
platform: wpf
control: SfCircularGauge
documentation: ug
---

#Annotations in WPF Circular Gauge (SfCircularGauge)

SfCircularGauge supports Annotations, which allows you to mark the specific area of interest in circular gauge. You can place custom views as annotations. The text and images also can be added by using Annotations property.

## Setting view annotation

When the annotation allows you to place custom elements, a gauge can be initialized to the element, and this can be used to place the annotation in another gauge. The Following properties are used to customize the Annotations:

* `Angle` : Used to place the View at the given Angle.
* `Offset` : Used to move the View from the center to edge of the circular gauge. The value should be range from 0 to 1.

The following code is used to create the Annotations.

{% tabs %}

{% highlight xaml %}

    <gauge:SfCircularGauge>
                <gauge:SfCircularGauge.Annotations>
                    <gauge:GaugeAnnotation Angle="270" Offset="0">
                        <gauge:GaugeAnnotation>
                            <TextBlock Text="75" FontSize="25" Height="30" Foreground="LightSkyBlue" Width="35"  HorizontalAlignment="Center" VerticalAlignment="Center"/>
                        </gauge:GaugeAnnotation>
                    </gauge:GaugeAnnotation>
                </gauge:SfCircularGauge.Annotations>
                <gauge:SfCircularGauge.Scales>
                    <gauge:CircularScale x:Name="scale" SweepAngle="360" RimStroke="LightGray"  RimStrokeThickness="30" RangePointerPosition="Custom" RangePointerOffset="0.5">
                        <gauge:CircularScale.Pointers>
                            <gauge:CircularPointer PointerType="RangePointer" RangePointerStrokeThickness="30" RangeCap="Both" RangePointerStroke="LightSkyBlue" Value="75"/>
                        </gauge:CircularScale.Pointers>
                  </gauge:CircularScale>
              </gauge:SfCircularGauge.Scales>
    </gauge:SfCircularGauge>

{% endhighlight %}

{% highlight c# %}

            SfCircularGauge sfCircularGauge = new SfCircularGauge();
            CircularScale mainscale = new CircularScale();
            mainscale.RangePointerPosition = RangePointerPosition.Custom;
            mainscale.SweepAngle = 360;
            mainscale.RimStroke = new SolidColorBrush(Colors.LightGray);
            mainscale.RimStrokeThickness = 30;
            TextBlock annotationText = new TextBlock();
            annotationText.Text = "95";
            annotationText.FontSize = 25;
            annotationText.Height = 30;
            annotationText.Foreground = new SolidColorBrush(Colors.LightSkyBlue);
            annotationText.Width = 35;
            annotationText.HorizontalAlignment = HorizontalAlignment.Center;
            annotationText.VerticalAlignment = VerticalAlignment.Center;
            GaugeAnnotation gaugeAnnotation = new GaugeAnnotation();
            gaugeAnnotation.Content = annotationText;
            gaugeAnnotation.Angle = 270;
            gaugeAnnotation.Offset = 0;
            CircularGaugeAnnotationCollection annotations = new CircularGaugeAnnotationCollection();
            annotations.Add(gaugeAnnotation);
            sfCircularGauge.Annotations = annotations;
            CircularPointer circularPointer = new CircularPointer();
            circularPointer.PointerType = PointerType.RangePointer;
            circularPointer.RangePointerStrokeThickness = 30;
            circularPointer.RangeCap = RangeCap.Both;
            circularPointer.RangePointerStroke = new SolidColorBrush(Colors.LightSkyBlue);
            circularPointer.Value = 75;
            mainscale.Pointers.Add(circularPointer);
            sfCircularGauge.Scales.Add(mainscale);

{% endhighlight %}

{% endtabs %}

![Annotations image for SfCircularGauge](Getting-Started_images/Annotations.png)

