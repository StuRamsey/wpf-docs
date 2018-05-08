---
layout: post
title: Null Value support | CurrencyTextBox | wpf | Syncfusion
description: null value support
platform: wpf
control: CurrencyTextBox 
documentation: ug
---

# Null Value Support

CurrencyTextBox accepts null values. To enable the null option you have to set the UseNullOption property to true. You can also set the NullValue property for the CurrencyTextBox. When you set the null value to the Value property, by default the value of the NullValue (Default value is null)property will be assigned to the Value property. 

{% tabs %}
{% highlight xaml %}

<syncfusion:CurrencyTextBox x:Name="currencyTextBox" Height="25" Width="150" UseNullOption="True" NullValue="100"/>

{% endhighlight %}

{% highlight C# %}

Syncfusion.Windows.Shared.CurrencyTextBox currencyTextBox = new  Syncfusion.Windows.Shared.CurrencyTextBox();
currencyTextBox.Width = 100;
currencyTextBox.Height = 25;
currencyTextBox.UseNullOption = true;
currencyTextBox.NullValue = 100;

{% endhighlight %}
{% endtabs %}

In this sample, the NullValue (NullValue = 1) is set to the Value property of the CurrencyTextBox because the default value of the Value property is zero.

![](Null-Value-support_images/Null-Value-support_img1.png)

{% tabs %}
{% highlight xaml %}

<syncfusion:CurrencyTextBox x:Name="currencyTextBox" Height="25" Width="150" UseNullOption="True" NullValue="{x:Null}"/>

{% endhighlight %}

{% highlight C# %}

Syncfusion.Windows.Shared.CurrencyTextBox currencyTextBox = new   Syncfusion.Windows.Shared.CurrencyTextBox();
currencyTextBox.Width = 100;
currencyTextBox.Height = 25;
currencyTextBox.UseNullOption = true;
currencyTextBox.NullValue = null;

{% endhighlight %}
{% endtabs %}

In this sample, the NullValue (NullValue = null) is set to the Value property of the CurrencyTextBox. (Default value of the Value property is 0).

![](Null-Value-support_images/Null-Value-support_img2.png)
