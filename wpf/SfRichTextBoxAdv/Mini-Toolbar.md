---
title: Mini Toolbar
description: mini toolbar
platform: wpf
control: SfRichTextBoxAdv
documentation: ug
keywords: mini-toolbar
---
# Mini Toolbar

The SfRichTextBoxAdv supports built-in mini toolbar to provide rich text formatting options such as Bold, Italic etc. The following screenshot shows built-in mini toolbar of SfRichTextBoxAdv control.
![](Mini-Toolbar_images/Mini-Toolbar_img1.jpeg)

## Enable/Disable Mini Toolbar

In SfRichTextBoxAdv, the built-in mini toolbar is enabled by default. It is possible to enable/disable the built-in mini toolbar. The following code example demonstrates how to disable the built-in mini toolbar in SfRichTextBoxAdv.
{% tabs %}
{% highlight xaml %}
<RichTextBoxAdv:SfRichTextBoxAdv x:Name="richTextBoxAdv" EnableMiniToolBar="False" xmlns:RichTextBoxAdv="clr-namespace:Syncfusion.Windows.Controls.RichTextBoxAdv;assembly=Syncfusion.SfRichTextBoxAdv.Wpf" />

{% endhighlight %}
{% highlight c# %}
//Disables the built-in mini tool bar in SfRichTextBoxAdv.<br/>richTextBoxAdv.EnableMiniToolBar = false;

{% endhighlight %}

{% endtabs %}
