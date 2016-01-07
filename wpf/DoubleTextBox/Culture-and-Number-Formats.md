---
layout: post
title: Culture and NumberFormat for DoubleTextBox
description: Culture and NumberFormat for DoubleTextBox control
platform: wpf
control: DoubleTextBox
documentation: ug
---

# Culture and Number Formats

## Culture

DoubleTextBox provides globalization support through the `Culture` property. The `Culture` property used to format the values based on the respective culture.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Height="25"
                         Width="150" Culture="en-US" Value="1234567"/>


{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.Width = 150;

doubleTextBox.Height = 25;

doubleTextBox.Value = 1234567;

doubleTextBox.Culture = new CultureInfo("en-US");

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 
 
doubleTextBox.Width = 150
 
doubleTextBox.Height = 25
 
doubleTextBox.Value = 1234567
 
doubleTextBox.Culture = New CultureInfo("en-US")
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

![](Culture-and-Number-Formats-images/Culture-and-Number-Formats-img1.jpeg)


## Number Format

The Number Format can be customize either by using the `NumberFormat` property or the `NumberGroupSeparator`, `NumberGroupSizes`, `NumberDecimalDigits`, and `NumberDecimalSeparator` properties of DoubleTextBox.

The following code illustrate how to customize the numberformat using NumberFormat property.

The Namespace used for NumberFormatInfo as follows:


{% tabs %}

{% highlight XAML %}

<Window x:Class="Application_New.MainWindow"

xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"

xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"

xmlns:numberformat="clr-namespace:System.Globalization;assembly=mscorlib"

xmlns:syncfusion="http://schemas.syncfusion.com/wpf"

Title="MainWindow" Height="350" Width="525">

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

using System.Globalization;

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Height="25"
                          Width="200" Value="123456789012345">

<syncfusion:DoubleTextBox.NumberFormat>

<numberformat:NumberFormatInfo NumberGroupSeparator="/"
              NumberDecimalDigits="4" NumberDecimalSeparator="*"/>

</syncfusion:DoubleTextBox.NumberFormat>

</syncfusion:DoubleTextBox>


{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

DoubleTextBox doubleTextBox = new DoubleTextBox();

doubleTextBox.Width = 150;

doubleTextBox.Height = 25;

doubleTextBox.Value = 1234567;

doubleTextBox.NumberFormat = new NumberFormatInfo()

{

NumberGroupSeparator = "/",

NumberDecimalDigits = 4,

NumberDecimalSeparator = "*"

};



{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As DoubleTextBox =  New DoubleTextBox() 
 
doubleTextBox.Width = 150
 
doubleTextBox.Height = 25
 
doubleTextBox.Value = 1234567
 
doubleTextBox.NumberFormat = Function NumberFormatInfo() As Shadows
 
NumberGroupSeparator = "/",
 
NumberDecimalDigits = 4,
 
NumberDecimalSeparator = "*"
 
End Function


{% endhighlight %}

{% endtabs %}

![](Culture-and-Number-Formats-images/Culture-and-Number-Formats-img2.jpeg)


The following code illustrate how to set NumerGroupSeparator, NumberDecimalDigits and NumberDecimalSeparator.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Height="25"
                          Width="200" Value="123456789012345"
                          NumberGroupSeparator="/" NumberDecimalDigits="4"
                          NumberDecimalSeparator="*"/>


{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

DoubleTextBox doubleTextBox = new DoubleTextBox();

doubleTextBox.Width = 170;

doubleTextBox.Height = 25;

doubleTextBox.Value = 123456789012345;

doubleTextBox.NumberGroupSeparator = "/";

doubleTextBox.NumberDecimalSeparator = "*";

doubleTextBox.NumberDecimalDigits = 4;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As DoubleTextBox =  New DoubleTextBox() 
 
doubleTextBox.Width = 170
 
doubleTextBox.Height = 25
 
doubleTextBox.Value = 123456789012345
 
doubleTextBox.NumberGroupSeparator = "/"
 
doubleTextBox.NumberDecimalSeparator = "*"
 
doubleTextBox.NumberDecimalDigits = 4
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

![](Culture-and-Number-Formats-images/Culture-and-Number-Formats-img3.jpeg)


