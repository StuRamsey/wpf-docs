---
layout: post
title: Setting Value in WPF SfDatePicker control | Syncfusion
description: This page explains about how to set or select a date in various ways from the WPF SfDatePicker control.
platform: wpf
control: SfDatePicker
documentation: ug
---

# Setting date in WPF SfDatePicker

We can change the value of [SfDatePicker](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker.html) by using the [SfDateSelector](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDateSelector.html) and keyboard interaction.

## Setting Date using property

We can set or change the selected date by using [DateTime](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~DateTime.html) property. If we not assign any value for the `DateTime` property, it will automatically assign the current system date as `DateTime` property value.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker  Value="5/30/2021"
                          Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.Value = new DateTime(2021,5,30);

{% endhighlight %}
{% endtabs %}

![SfDatePicker displaying selected value](Features_images/Features_img17.png)

## Setting Null Value

If we want to set null value for the `SfDatePicker`, set the [AllowNull](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~AllowNull.html) property as `true` and [DateTime](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~DateTime.html) property as `null`. If `AllowNull` property is `false`, then the current system date is updated in  `DateTime` property and displayed instead of `null`. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker  AllowNull="True" 
                          DateTime="{x:Null}"
                          Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.AllowNull = true;
sfDatePicker.DateTime = null;

{% endhighlight %}
{% endtabs %}

![SfDatePicker displaying null value](Features_images/Features_img13.png)

## Setting WaterMark text

We can prompt the user with some information by using the [Watermark](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~Watermark.html) property. This will apply on when the `SfDatePicker` contains the [DateTime](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~DateTime.html) property as `null` and [AllowNull](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~AllowNull.html) property as `true` . If `AllowNull` property is `false`, then the current system date is updated in  `DateTime` property and displayed instead of `Watermark` text. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker Watermark="Select the Date"
                         AllowNull="True"  
                         DateTime="{x:Null}"
                         Name="sfDatePicker" >
</syncfusion:SfDatePicker>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.Watermark = "Select the Date";
sfDatePicker.AllowNull = true;
sfDatePicker.DateTime = null;

{% endhighlight %}
{% endtabs %}

![SfDatePicker with watermark text](Appearance-and-Styling_images/Watermark.png)

### Setting WaterMark Template

We can change the template of the `Watermark` by using the [WatermarkTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~WatermarkTemplate.html) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker Name="sfDatePicker" 
                         AllowNull="True" 
                         DateTime="{x:Null}" 
                         Watermark="Select the Date" >
    <syncfusion:SfDatePicker.WatermarkTemplate >
        <DataTemplate>
            <Border Background="Yellow">
                <TextBlock Foreground="Blue"
                           FontWeight="Bold"  
                           Text="{Binding}" 
                           TextAlignment="Center"/>
            </Border>
        </DataTemplate>
    </syncfusion:SfDatePicker.WatermarkTemplate>
</syncfusion:SfDatePicker>

{% endhighlight %}
{% endtabs %}

![SfDatePicker with watermarktemplate](Appearance-and-Styling_images/WatermarkTemplate.png)

## Set selected value on lost focus

If we want to update the selected date of `SfDateSelector` to the `SfDatePicker.DateTime` property by moving the focus from `SfDateSelector` to anywhere, use the [SetValueOnLostFocus](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~SetValueOnLostFocus.html) property value as `true`. By default, the selected date of `SfDateSelector` can be sets to the `SfDatePicker.DateTime` property only by clicking the `OK` button, otherwise the selected value not updated by the move focus.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker  SetValueOnLostFocus="True" 
                          Name="sfDatePicker" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.SetValueOnLostFocus = true;

{% endhighlight %}
{% endtabs %}

![SfDatePicker value updated on when SfDateSelector lost its focus](Features_images/Features_img15.gif)

## Setting the date using editing

If we want to perform the validation after the user completely entering their date inputs, use the [AllowInlineEditing](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~AllowInlineEditing.html) property value as `true`. Then the entered date value is validated with the [FormatString](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~FormatString.html) property value by pressing the `Enter` key or lost focus. If entered value is not suit with `FormatString` property, the selected date will be set as default format value.

By default, the user entering each input numbers are automatically validated with the `FormatString` formats and assigned the proper value for it, then it will move to next input part of the date format.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker Name="sfDatePicker" 
                         AllowInlineEditing="True" />

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.AllowInlineEditing = true;

{% endhighlight %}
{% endtabs %}

![SfDatePicker with inline date editing](Features_images/AllowInlineEditing.gif)

## Setting the Input Scope for the On-Screen Keyboard

We can change the input type of the on-screen keyboard by using the [InputScope](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~InputScope.html) property. When the `InputScope` property set to `Number`, only the numeric keypad will be visible in the on-screen keyboard.

N> The [AllowInlineEditing](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~AllowInlineEditing.html) property must be set to `True` for this property to take effect.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker Name="sfDatePicker" 
                         AllowInlineEditing="True" 
                         InputScope="Number"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker= new SfDatePicker();
sfDatePicker.AllowInlineEditing = true;
sfDatePicker.InputScope = InputScopeNameValue.Date;

{% endhighlight %}
{% endtabs %}

![SfDatePicker with Input Scope for the On-Screen Keyboard](Features_images/Features_img14.png)

## Restrict selecting date limit

we can restrict the user to select a date in the specific date limit by setting the value for the [MinDate](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~MinDate.html) and [MaxDate](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~MaxDate.html) properties. If we assign the value for the `DateTime` property lower than `MinDate`, then `MinDate` will be the selected date. If we assign the value for the `DateTime` property higher than `MaxDate`, then `MaxDate` will be the selected date.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDatePicker MinDate="1/1/2020"
                         MaxDate="6/30/2020" 
                         Name="sfDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.MinDate = new DateTime(2020, 1, 1);
sfDatePicker.MaxDate = new DateTime(2020, 6, 30);


{% endhighlight %}
{% endtabs %}

![SfTimePicker with max-min date range](Features_images/Features_img16.png)

Here, the users can select the year from `2019` to `2021` only. 

## Date changed notification

When the selected date of `SfDatePicker`is changed, it will be notified by using the [ValueChanged](https://help.syncfusion.com/cr/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfDatePicker~ValueChanged_EV.html) event. You can get the details about the checked item in [ItemCheckedEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.ItemCheckedEventArgs.html).

* **OldValue** : Gets a date which is previously selected.

* **NewValue** : Gets a date which is currently selected.

{% tabs %}
{% highlight XAML %}

<syncfusion:SfDatePicker ValueChanged="SfdatePicker_ValueChanged" 
                         Name="sfDatePicker"/>

{% endhighlight %}
{% highlight C# %}

SfDatePicker sfDatePicker = new SfDatePicker();
sfDatePicker.ValueChanged += SfdatePicker_ValueChanged;

{% endhighlight %}
{% endtabs %}

You can handle the event as follows:

{% tabs %}
{% highlight C# %}

private void SfdatePicker_ValueChanged(DependencyObject d, DependencyPropertyChangedEventArgs e) {          
    Console.WriteLine("The Old selected Date: " + e.OldValue.ToString());
    Console.WriteLine("The Newly selected Date: " + e.NewValue.ToString());            
}

{% endhighlight %}
{% endtabs %}

Click [here](https://github.com/SyncfusionExamples/wpf-date-picker-examples/tree/master/Samples/Value-setting) to download the sample that showcases the input types and selected date with its notification supports.