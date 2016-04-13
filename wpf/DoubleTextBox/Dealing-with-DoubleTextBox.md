---
layout: post
title: Dealing with Syncfusion DoubleTextBox control for WPF
description: Dealing with Syncfusion DoubleTextBox control for WPF
platform: wpf
control: DoubleTextBox
documentation: ug
---

# Dealing with DoubleTextBox

## Watermark

The Watermark text is the dummy content displayed in the DoubleTextBox when the value is null. It can be set using the `WatermarkText` property. To enable Watermark text, the `WatermarkTextIsVisible` property need to set to true. By default its value is false.

N> WatermarkText is visible only when the value of DoubleTextBox is null.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="DoubleTextBox1" Height="25"
                          Width="100" Value="{x:Null}" UseNullOption="True"
						  WatermarkText="Type Here" WatermarkTextIsVisible="True"/>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

DoubleTextBox DoubletextBox1 = new DoubleTextBox();

DoubletextBox1.Width = 100;

DoubletextBox1.Height = 25;

DoubletextBox1.Value =null;

DoubletextBox1.UseNullOption = true;

DoubletextBox1.WatermarkText = "Type Here";

DoubletextBox1.WatermarkTextIsVisible = true;

Grid1.Children.Add(DoubletextBox1);


{% endhighlight %}

{% highlight VB %}

Dim DoubletextBox1 As DoubleTextBox =  New DoubleTextBox() 
 
DoubletextBox1.Width = 100
 
DoubletextBox1.Height = 25
 
DoubletextBox1.Value =Nothing
 
DoubletextBox1.UseNullOption = True
 
DoubletextBox1.WatermarkText = "Type Here"
 
DoubletextBox1.WatermarkTextIsVisible = True
 
Grid1.Children.Add(DoubletextBox1)

{% endhighlight %}

{% endtabs %}

![](Dealing-with-DoubleTextBox-images/Dealing-with-DoubleTextBox-img1.jpeg)

WatermarkText automatically collapses when the control is in focus. When the control loses its focus the WatermarkText comes to the visible state if the Value is null and the WatermarkTextIsVisible is true.

## Binding Value

Data binding is the process of establishing a connection between the application UI and business logic. Data binding can be unidirectional (source -> target or target <- source) or bidirectional (source <-> target). The data can bind to the DoubleTextBox through the Value property.

The following example shows a simple binding between the value of the DoubleTextBox and another DoubleTextBox value that reflects the typed value:

![](Dealing-with-DoubleTextBox-images/Dealing-with-DoubleTextBox-img2.jpeg)


To bind values other than double values, the Value Converter need to use. The following example shows a simple binding between the value of the DoubleTextBox and the Textbox text that reflects the typed value:

{% tabs %}

{% highlight XAML %}

<StackPanel>

<StackPanel.Resources>

<c:StringToDoubleConverter x:Key="stringToDoubleConverter"/>

</StackPanel.Resources>

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Width="150" Margin="10"/>

<TextBox x:Name="textBox" Width="150" Margin="10"
         Text="{Binding ElementName=doubleTextBox,Path=Value,Mode=TwoWay,
		 Converter={StaticResource stringToDoubleConverter}}"/>

</StackPanel>


{% endhighlight %}

{% endtabs %}

![](Dealing-with-DoubleTextBox-images/Dealing-with-DoubleTextBox-img3.jpeg)


## Keyboard and Mouse support

Up or down key arrows allows to spin the values of DoubleTextBox one step up or down. Mouse Scroll in the DoubleTextBox spin the values one step up or down. This spin behavior in the DoubleTextBox, can be restricted by setting the `IsScrollingOnCircle` property to `false`. By default, its value is `true`.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Width="150"
                          Height="25" Value ="10" IsScrollingOnCircle="False"/>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.Width = 150;

doubleTextBox.Height = 25;

doubleTextBox.Value = 10;

doubleTextBox.IsScrollingOnCircle = false;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 
 
doubleTextBox.Width = 150
 
doubleTextBox.Height = 25
 
doubleTextBox.Value = 10
 
doubleTextBox.IsScrollingOnCircle = False
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

## IsReadOnly

If the DoubleTextBox is read-only, then no user input or edits are allowed but programmatic changes can be made. The user can still select text and the cursor still appears. 

To enable this feature set `IsReadOnly` to `true`. By default its value is `false`.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" IsReadOnly="True"/>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.IsReadOnly = true;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 
 
doubleTextBox.IsReadOnly = True
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

## EnterToMoveNext

On pressing the Enter key in the DoubleTextBox, then the Focus moves to the next element in the application. To restrict this feature the `EnterToMoveNext` property need to set to `false`. By default its value is `true`.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" EnterToMoveNext="False"/>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.EnterToMoveNext = false;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 
 
doubleTextBox.EnterToMoveNext = False
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

## TextSelectionOnFocus

The `TextSelectionOnFocus` property allows the DoubleTextBox to act like standard text boxes when the cursor hovers over. To restrict this behavior set its value as false. By default the value is true.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" TextSelectionOnFocus="False"/>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.TextSelectionOnFocus = true;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 

doubleTextBox.TextSelectionOnFocus = True

Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}


## Extended Scrolling

The `EnableExtendedScrolling` property is used to change the values based on the click and drag direction of the mouse movements. The range will increase when the mouse moves to the right or top of the screen, and will decrease when the mouse moves in the direction of the left or bottom of the screen. Before that, the control should be in an unfocused state. The default value is false.

### Adding Extended Scrolling to an Application

The EnableExtendedScrolling property must be set either in XAML or the code file.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Width="120" Height="25" Value ="93" EnableExtendedScrolling="True"/>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.Width = 120;

doubleTextBox.Height = 25;

doubleTextBox.Value = 93;

doubleTextBox.EnableExtendedScrolling = true;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 
 
doubleTextBox.Width = 120
 
doubleTextBox.Height = 25
 
doubleTextBox.Value = 93
 
doubleTextBox.EnableExtendedScrolling = True
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

![](Dealing-with-DoubleTextBox-images/Dealing-with-DoubleTextBox-img4.jpeg)


## Range Adorner

To show the adorner range based on the minimum and maximum values, the EnableRangeAdorner property need to set to True. By Default its value is false.

{% tabs %}

{% highlight XAML %}

<syncfusion:DoubleTextBox x:Name="doubleTextBox" Width="150" Height="25"
                          Value ="50" MaxValue="100" MinValue="10"
						  EnableRangeAdorner="True"/>


{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

Syncfusion.Windows.Shared.DoubleTextBox doubleTextBox = new Syncfusion.Windows.Shared.DoubleTextBox();

doubleTextBox.Width = 100;

doubleTextBox.Height = 25;

doubleTextBox.Value = 50;

doubleTextBox.MinValue = 10;

doubleTextBox.MaxValue = 100;

doubleTextBox.EnableRangeAdorner = true;

Grid1.Children.Add(doubleTextBox);

{% endhighlight %}

{% highlight VB %}

Dim doubleTextBox As Syncfusion.Windows.Shared.DoubleTextBox =  New Syncfusion.Windows.Shared.DoubleTextBox() 
 
doubleTextBox.Width = 100
 
doubleTextBox.Height = 25
 
doubleTextBox.Value = 50
 
doubleTextBox.MinValue = 10
 
doubleTextBox.MaxValue = 100
 
doubleTextBox.EnableRangeAdorner = True
 
Grid1.Children.Add(doubleTextBox)

{% endhighlight %}

{% endtabs %}

![](Dealing-with-DoubleTextBox-images/Dealing-with-DoubleTextBox-img5.jpeg)


