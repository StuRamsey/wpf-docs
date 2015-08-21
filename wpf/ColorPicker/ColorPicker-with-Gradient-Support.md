---
layout: post
title: ColorPicker-with-Gradient-Support
description: colorpicker with gradient support
platform: wpf
control: ColorPicker
documentation: ug
---

# ColorPicker with Gradient Support

Color Picker now comes with Gradient tool which returns a brush of type Solid, Linear or Radial. The offsets can be added or dropped dynamically and its position can be changed to produce different color combinations.

![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img1.jpeg)



## Interactive Features with Gradient Support

The following are the key features of the ColorPicker with Gradient support.

### Brush Mode

This property specifies whether Brush is of type Solid or Gradient. The following code snippets illustrate this:

{% highlight xml %}


<Syncfusion:ColorPicker x:Name="colorPicker"  BrushMode="Solid"   ></  Syncfusion: ColorPicker >
<Syncfusion: ColorPicker x:Name="colorPicker"  BrushMode="Gradient"   ></  Syncfusion: ColorPicker >
{% endhighlight %}

{% highlight C# %}


ColorPicker colorPicker = new ColorPicker ();
colorPicker.BrushMode =  BrushModes.Solid;
colorPicker.BrushMode =  BrushModes.Gradient;

{% endhighlight %}



![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img2.jpeg)





![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img3.jpeg)





### Enable Solid To Gradient Switch

This property specifies whether switching between Solid and Gradient BrushMode and vice-versa is enabled at runtime or not.

The following code examples illustrate this:

{% highlight xml %}


<Syncfusion: ColorPicker x:Name="colorPicker"  EnableSolidToGradientSwitch="true"   ></  Syncfusion: ColorPicker >
<Syncfusion:ColorEdit x:Name="colorPicker"  EnableSolidToGradientSwitch="false"   ></  Syncfusion: ColorEdit >
{% endhighlight %}

{% highlight C# %}


ColorPicker colorPicker = new ColorPicker ();
colorPicker.EnableSolidToGradientSwitch =  true;
colorPicker.EnableSolidToGradientSwitch =  false;
{% endhighlight %}




![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img4.jpeg)





![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img5.jpeg)





### IsGradientPropertyEnabled

ColorPicker with Gradient tool comes with a Gradient Editor to change the Start Point/End Point when Brush is of type LinearGradient and Gradient Origin is Center/Radius, if Brush is of type RadialGradient dynamically.  IsGradientPropertyEnabled property specifies whether GradientEditor is made visible or hidden.

The following code example illustrate this:

{% highlight xml %}


<Syncfusion:ColorPicker x:Name="colorPicker"  IsGradientEditorEnabled="true"   ></  Syncfusion: ColorPicker >
<Syncfusion: ColorPicker x:Name="colorPicker"  IsGradientEditorEnabled="false"   ></  Syncfusion: ColorPicker >
{% endhighlight %}

{% highlight C# %}


ColorPicker colorPicker = new ColorPicker ();
colorPicker.IsGradientEditorEnabled =  true;
colorPicker. IsGradientEditorEnabled =  false;
{% endhighlight %}




![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img6.jpeg)





![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img7.jpeg)



### GradientPropertyEditorMode

The property specifies whether GradientEditor should be displayed as a Popup or in extended mode.

{% highlight xml %}


<Syncfusion:ColorPicker x:Name="colorPicker"    GradientPropertyEditorMode="Popup" ></ Syncfusion: ColorPicker >
<Syncfusion: ColorPicker x:Name="colorPicker"  GradientPropertyEditorMode="Extended"  ></Syncfusion: ColorPicker >
{% endhighlight %}

{% highlight C# %}



ColorPicker colorPicker = new ColorPicker ();
colorPicker.GradientPropertyEditorMode =  GradientPropertyEditorMode.Popup;
colorPicker. GradientPropertyEditorMode =  GradientPropertyEditorMode.Extended;
{% endhighlight %}


The GradientEditor is displayed accordingly.

### IsAlphaVisible in ColorPicker

ColorPicker now allows you to restrict the change in Alpha value, thus maintaining it as a constant. This can be achieved by setting _IsAlphaVisible_property to false. This collapses the slider which changes the alpha value in RGB mode and text block for editing alpha value is collapsed in HSV mode.

The following code example illustrate this:

{% highlight xml %}


<syncfusion:ColorPicker IsAlphaVisible="True"></syncfusion:ColorPicker> 
 <syncfusion:ColorPicker IsAlphaVisible="false"></syncfusion:ColorPicker>
{% endhighlight %}

{% highlight C# %}


ColorPicker colorPicker = new ColorPicker();
colorPicker.IsAlphaVisible = true;
colorPicker.IsAlphaVisible = false;
{% endhighlight %}


![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img8.jpeg)





![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img9.jpeg)





![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img10.jpeg)





![](ColorPicker-with-Gradient-Support_images/ColorPicker-with-Gradient-Support_img11.jpeg)



