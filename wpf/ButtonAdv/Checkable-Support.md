---
layout: post
title: Checkable-Support
description: checkable support
platform: wpf
control: ButtonAdv
documentation: ug
---

# Checkable Support

The ButtonAdv Control can also be used as checkboxes, if the IsCheckable property is set to true.

You can set the ButtonAdv control in checked state using the following code examples:

{% highlight html %}
[XAML]<sync:ButtonAdv SizeMode="Normal" IsCheckable="True" IsChecked="True"/>
{% endhighlight %}
{% highlight c# %}
[C#]ButtonAdv button = new ButtonAdv()button.Label = "Hello World";button.SizeMode = SizeMode.Large;button.SmallIcon = new BitmapImage(new Uri("employee.png"));button.IsCheckable = true;button.IsChecked = true;

{% endhighlight  %}

![](Checkable-Support_images/Checkable-Support_img1.png)



