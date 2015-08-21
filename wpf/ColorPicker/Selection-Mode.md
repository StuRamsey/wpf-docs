---
layout: post
title: Selection-Mode
description: selection mode
platform: wpf
control: ColorPicker
documentation: ug
---

# Selection Mode

ColorPicker and ColorEdit controls can be displayed in two different modes. They are HSV and RGB modes. The VisualizationStyle property is used to switch between these modes.

To set the ColorSelection Mode as "HSV" for ColorEdit control, use the below code.

{% highlight xml %}

<!-- Adding ColorEdit -->
<syncfusion:ColorEdit  Margin="20" VisualizationStyle="HSV" Name="colorEdit"/><
{% endhighlight %}

{% highlight C# %}

//Creating an instance of color edit
ColorEdit colorEdit = new ColorEdit();

//Setting selection mode as HSVcolorEdit.
VisualizationStyle = ColorSelectionMode.HSV;    

//Adding control to the window
this.Content = colorEdit;
{% endhighlight %}




![](Selection-Mode_images/Selection-Mode_img1.jpeg)





To set the ColorSelection Mode as "HSV" for ColorPicker control, use the below code.


{% highlight C# %}




//Creating an instance of color picker

ColorPicker colorPicker = new ColorPicker();



//Setting selection mode as HSV

colorPicker.VisualizationStyle = ColorSelectionMode.HSV;    



//Adding control to the window

this.Content = colorPicker;

{% endhighlight %}



![](Selection-Mode_images/Selection-Mode_img2.jpeg)





To set the ColorSelection Mode as "RGB" for ColorEdit control, use the below code.

{% highlight C# %}




//Creating an instance of color edit

ColorEdit colorEdit = new ColorEdit();



//Setting selection mode as RGB

colorEdit.VisualizationStyle = ColorSelectionMode.RGB; 



//Adding control to the window

this.Content = colorEdit;
{% endhighlight %}




![](Selection-Mode_images/Selection-Mode_img3.jpeg)




To set the ColorSelection Mode as "RGB" for ColorPicker control, use the below code.

{% highlight C# %}




//Creating an instance of color picker

ColorPicker colorPicker = new ColorPicker();



//Setting selection mode as RGB

colorPicker.VisualizationStyle = ColorSelectionMode.RGB;



//Adding control to the window

this.Content = colorPicker;
{% endhighlight %}




![](Selection-Mode_images/Selection-Mode_img4.jpeg)



