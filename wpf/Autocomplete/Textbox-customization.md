---
layout: post
title: Textbox customization | SfTextBoxExt | wpf | Syncfusion
description: This section provides the details how to customizing features in WPF SfTextBoxExt control using following properties.
platform: wpf
control: SfTextBoxExt
documentation: ug
---

# Textbox customization 

AutoComplete provides the user-friendly customizing options for both text box and drop-down. This section explains how to customize the entire AutoComplete control.


## Water mark 

[Watermark](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~Watermark.html) property, allows the users to specify some information when the text is empty. For illustration, let us create a simple textbox where the user is asked to enter names separated by a comma.

{% tabs %}
{% highlight xaml %}

            <editors:SfTextBoxExt HorizontalAlignment="Center" 
                                  VerticalAlignment="Center" 
                                  Width="300" 
                                  Height="50"
                                  Watermark="Enter names separated by comma (Ex : John, Kate)"/>

{% endhighlight %}
{% endtabs %}

![Watermark_Text](Watermark_images/Watermark_img1.png)

N> The Watermark property is of the object type. So, any framework elements can be hosted as Watermark content. The following example shows how to host an image and text as Watermark content.

{% tabs %}
{% highlight xaml %}

            <editors:SfTextBoxExt HorizontalAlignment="Center"
                                  VerticalAlignment="Center" 
                                  Height="50"
                                  Width="300">
                <editors:SfTextBoxExt.Watermark>
                    <StackPanel Orientation="Horizontal">
                        <Image Source="Windows 8.png" 
                               Margin="2"/>
                        <TextBlock Text="Search Windows" 
                                   HorizontalAlignment="Center" 
                                   VerticalAlignment="Center" 
                                   Opacity="0.5"/>
                    </StackPanel>
                </editors:SfTextBoxExt.Watermark>
            </editors:SfTextBoxExt>

{% endhighlight %}
{% endtabs %}

![Watermark_View](Watermark_images/Watermark_img2.png)

### Water mark template 

Any business object can be bound to the Watermark property and that object can be decorated by applying the [WatermarkTemplate](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~WatermarkTemplate.html)  property.

{% tabs %}
{% highlight xaml %}

    <Window.Resources>
        <DataTemplate x:Key="WatermarkTemplate">
            <TextBlock Text="{Binding}" 
                       FontStyle="Italic" 
                       Opacity="1"/>
        </DataTemplate>
    </Window.Resources>
    <Window.Content>
        <Grid>
            <editors:SfTextBoxExt HorizontalAlignment="Center" 
                                  VerticalAlignment="Center"
                                  Width="200"
                                  Height="40"
                                  Watermark="Type here"
                                  WatermarkTemplate="{StaticResource WatermarkTemplate}">
            </editors:SfTextBoxExt>
        </Grid>
    </Window.Content>

{% endhighlight %}
{% endtabs %}

![Watermark_View](Watermark_images/Watermark_img3.png)


## Customizing the text box

The [Text](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~IgnoreCase.html#), [FontSize](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~IgnoreCase.html#), [FontWeight](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~IgnoreCase.html#), and [FontFamily](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~IgnoreCase.html#) properties are used to customize the text box.

{% tabs %}

{% highlight xaml %}

 <editors:SfTextBoxExt x:Name="textBoxExt" 
                              Text="TextBox"
                              FontSize="20"
                              FontWeight="Bold"
                              FontFamily="Times New Roman"
                              HorizontalAlignment="Center" 
                              VerticalAlignment="Center" 
                              Width="200">
            </editors:SfTextBoxExt>

{% endhighlight %}

{% endtabs %}

![AutoComplete Customization](Auto-Complete_images/Customization.png)



## Setting the Dropdown Icon 

This feature allows the users to set the drop-down icon for the text box control using the [ShowDropDownButton](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfInput.Wpf~Syncfusion.Windows.Controls.Input.SfTextBoxExt~ShowDropDownButton.html).

{% tabs %}

{% highlight xaml %}

        <editors:SfTextBoxExt HorizontalAlignment="Center" 
                              VerticalAlignment="Center" 
                              Width="300"
                              Height="40"
                              ShowDropDownButton="True"
                              SearchItemPath="Name"
                              AutoCompleteMode="Suggest"
                              AutoCompleteSource="{Binding Employees}" />

{% endhighlight %}

{% endtabs %}

![DropdownIcon](Auto-Complete_images/DropDownIcon.png)
