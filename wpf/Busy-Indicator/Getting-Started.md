---
layout: post
title: Getting Started | Busy Indicator | wpf | Syncfusion
description: getting started
platform: wpf
control: Busy Indicator
documentation: ug
---

# Getting Started

Namespace: Syncfusion.Windows.Controls.Notification.

Assembly: Syncfusion.SfBusyIndicator.WPF (in Syncfusion.SfBusyIndicator.WPF.dll)

The following code example shows how to create the SfBusyIndicator from XAML and code behind respectively.

{% tabs %}

{% highlight xaml %}

<Page xmlns:Notification="clr-namespace:Syncfusion.Windows.Controls.Notification;assembly=Syncfusion.SfBusyIndicator.WPF">

    <Grid Background="CornflowerBlue">

        <Notification:SfBusyIndicator/>

    </Grid>

</Page>

{% endhighlight  %}

{% highlight c# %}

SfBusyIndicator busyIndicator = new SfBusyIndicator();

{% endhighlight  %}

{% endtabs %}
