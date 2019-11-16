---
layout: post
title: IsBusy | Busy Indicator | wpf | Syncfusion
description: isbusy
platform: wpf
control: Busy Indicator
documentation: ug
---

# IsBusy

The IsBusy property in the BusyIndicator control is used to determine whether an animation needs to be executed or not.

{% tabs %}

{% highlight xaml %}

<Grid Background="CornflowerBlue">

    <Navigation:SfBusyIndicator IsBusy="True"/>

</Grid>

{% endhighlight %}

{% highlight c# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();

busyIndicator.IsBusy = true;

{% endhighlight %}

{% endtabs %}

![](IsBusy_images/IsBusy_img1.png)

Busy Indicator
{:.caption}
