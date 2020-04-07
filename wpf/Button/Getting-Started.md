---
layout: post
title: Getting Started | Button | WPF | Syncfusion
description: Learn how to add WPF Button (ButtonAdv) control and its basic features like image sizing options and size modes to an application here. 
platform: wpf
control: ButtonAdv
documentation: ug
----

# Getting Started with Button

This section provides an overview of how to work with Button control. It describes the control structure, the control initialization  and the image setting to the control.

## Control structure

![Getting Started](Getting-Started_images/Getting-Started_img1.png)

Control Structure
{:.caption}

## Assembly deployment

Refer [ButtonAdv](https://help.syncfusion.com/wpf/control-dependencies#buttonadv) control dependencies section to get the list of assemblies or [NuGet package](https://help.syncfusion.com/wpf/visual-studio-integration/nuget-packages) needs to be added as reference to use the ButtonAdv control in any application.

## Creating simple application with Button

In this walk through, will create WPF application that contains Button control. By the following ways, one can add the controls:

1. [Adding control via designer](#Adding-control-via-designer)

2. [Adding control manually in XAML](#Adding-control-manually-in-XAML)

3. [Adding control manually in C#](#Adding-control-manually-in-C#)

### Adding control via designer

Button control can be added to the application by dragging **ButtonAdv** from toolbox and dropping it in designer view. After dropping the control in designer view, the assembly **Syncfusion.Shared.WPF** gets added into the project automatically. The following code snippets will also be added into the XAML.

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv x:Name="buttonAdv" Label="Button"/>

{% endhighlight %}
{% endtabs %}

![Getting Started](Getting-Started_images/Getting-Started_img2.png)

N> **syncfusion** in XAML is an auto generated namespace.

### Adding control manually in XAML

In order to add the control manually in XAML, follow the below steps.

1. Add the below required assembly reference to the project.

    * Syncfusion.Shared.WPF

2. Import Syncfusion WPF schema **http://schemas.syncfusion.com/wpf** in XAML page.

3. Declare ButtonAdv control in XAML page.

{% tabs %}
{% highlight xaml %}

  <Window xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:local="clr-namespace:Buttonadv_GetStart_Sample"
         xmlns:syncfusion="http://schemas.syncfusion.com/wpf"
         xmlns:Syncfusion="http://schemas.microsoft.com/netfx/2009/xaml/presentation"
         mc:Ignorable="d"
         Title="MainWindow" Height="450" Width="800">
        <Grid>
        <syncfusion:ButtonAdv Height="44"  VerticalAlignment="Center" HorizontalAlignment="Center" Width="162"/>
    </Grid>
</Window>
{% endhighlight %}
{% endtabs %}

### Adding control manually in C#

In order to the add control manually in C#, do the below steps.

1. Add the below required assembly reference to the project.

    * Syncfusion.Shared.WPF

2. Import namespace using **Syncfusion.Windows.Tools.Controls**;.

3. Create ButtonAdv control instance and add it to the window.

{% tabs %}
{% highlight xaml %}

<Window xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
         xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
         xmlns:local="clr-namespace:Buttonadv_GetStart_Sample"
         xmlns:syncfusion="http://schemas.syncfusion.com/wpf"
         xmlns:Syncfusion="http://schemas.microsoft.com/netfx/2009/xaml/presentation"
         mc:Ignorable="d"
         Title="MainWindow" Height="450" Width="800">
        <Grid x:Name="Root">
        </Grid>
</Window>

{% endhighlight %}
{% highlight c# %}



 using Syncfusion.Windows.Tools.Controls;
  {
   public MainWindow()
   {
        {
            InitializeComponent();
            ButtonAdv button = new ButtonAdv();
            button.Height=44;
            button.Width=31;
            Root.Childran.Add(button);
        }
    }

{% endhighlight  %}
{% endtabs %}

## Setting label

The label on the button is a text that explains its action to the end-user. Apply the text by using the [Label](https://help.syncfusion.com/cr/wpf/Syncfusion.Shared.Wpf~Syncfusion.Windows.Tools.Controls.ButtonAdv~Label.html) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv Label="Log-in"/>

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Log-in";

{% endhighlight %}
{% endtabs %}

![Setting Label](Getting-Started_images/Getting-Started_img4.png)

## Setting size mode

Size mode is used to render button control in different pre-defined sizes based on application demand. Apply the size mode by setting the [SizeMode](https://help.syncfusion.com/cr/wpf/Syncfusion.Shared.Wpf~Syncfusion.Windows.Tools.Controls.ButtonAdv~SizeMode.html) property.

 The **SizeMode** is an enumeration which contains the following values:

* Small
* Normal
* Large

### Small mode

When the mode is set to **Small**, the control is displayed without the label. Only icon will be present in it.

{% tabs %}
{% highlight xaml %}

<sync:ButtonAdv SizeMode="Small" Label="Log-in"/>

{% endhighlight %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Log-in";
button.SizeMode = SizeMode.Small;

{% endhighlight  %}
{% endtabs %}

![Small Mode](Getting-Started_images/Getting-Started_img3.png)

### Normal mode

In a normal size button, a small image with the text on the side will be displayed.

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv SizeMode="Normal" Label="Log-in"/>

{% endhighlight %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Log-in";
button.SizeMode = SizeMode.Normal;

{% endhighlight %}
{% endtabs %}

![Normal Mode](Getting-Started_images/Getting-Started_img4.png)

### Large mode

In a large size button, a large image along with the text at the bottom will be displayed.

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv SizeMode="Large" Label="Log-in"/>

{% endhighlight  %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Log-in";
button.SizeMode = SizeMode.Large;

{% endhighlight %}
{% endtabs %}

![Large Mode](Getting-Started_images/Getting-Started_img5.png)

## Setting image

The image option helps to provide pictorial representation of the button. Image can be added either using the [SmallIcon](https://help.syncfusion.com/cr/wpf/Syncfusion.Shared.Wpf~Syncfusion.Windows.Tools.Controls.ButtonAdv~SmallIcon.html) property or [LargeIcon](https://help.syncfusion.com/cr/wpf/Syncfusion.Shared.Wpf~Syncfusion.Windows.Tools.Controls.ButtonAdv~LargeIcon.html) property.

**SmallIcon** — This property will be used to set the image when size mode is **Normal** or **Small**.
**LargeIcon** — This property will be used to set the image when size mode is **Large**.

### Setting small icon

The **SmallIcon** property can be set as follows:

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv SizeMode="Small" Label="Syncfusion" SmallIcon="syncfusion.png"/>

{% endhighlight %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Syncfusion";
button.SizeMode = SizeMode.Small;
button.SmallIcon = new BitmapImage(new Uri("syncfusion.png"));

{% endhighlight %}
{% endtabs %}

![Setting Image](Getting-Started_images/Getting-Started_img6.png)

The **SmallIcon** property can be set even when the SizeMode is **Normal**:

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv SizeMode="Normal" SmallIcon="syncfusion.png" Label="Syncfusion"/>

{% endhighlight %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Syncfusion";
button.SizeMode = SizeMode.Normal;
button.SmallIcon = new BitmapImage(new Uri("syncfusion.png"));

{% endhighlight  %}
{% endtabs %}

![Normal-Image](Getting-Started_images/Getting-Started_img7.png)

### Setting large icon

The **LargeIcon** property can be set as follows:

{% tabs %}
{% highlight xaml %}

<sync:ButtonAdv SizeMode="Large" LargeIcon="syncfusion.png" Label="Syncfusion"/>

{% endhighlight %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button.Label = "Syncfusion";
button.SizeMode = SizeMode.Large;
button.SmallIcon = new BitmapImage(new Uri("syncfusion.png"));

{% endhighlight %}
{% endtabs %}

![Large Mode Image](Getting-Started_images/Getting-Started_img8.png)

## Setting icon width and height

Icon width and icon height can be set using [IconWidth](https://help.syncfusion.com/cr/wpf/Syncfusion.Shared.Wpf~Syncfusion.Windows.Tools.Controls.ButtonAdv~IconWidth.html) and [IconHeight] (https://help.syncfusion.com/cr/wpf/Syncfusion.Shared.Wpf~Syncfusion.Windows.Tools.Controls.ButtonAdv~IconHeight.html) properties respectively.

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv x:Name="button1" SizeMode="Normal" IconHeight="20" IconWidth="20"  Label="Syncfusion"  SmallIcon ="syncfusion.png"  />

{% endhighlight %}
{% highlight c# %}

ButtonAdv button = new ButtonAdv();
button1.Label = "Syncfusion";
button1.IconWidth=20;
button1.IconHeight=20;
button1.SmallIcon = new BitmapImage(new Uri("syncfusion.png"));
{% endhighlight %}
{% endtabs %}

![Icon Size Image](Getting-Started_images/Getting-Started_img9.png)

{% tabs %}
{% highlight xaml %}

<syncfusion:ButtonAdv x:Name="button2"  SizeMode="Normal" IconHeight="30" IconWidth="30"  Label="Syncfusion"  SmallIcon ="syncfusion.png"  />

{% endhighlight %}
{% highlight c# %}

ButtonAdv button1 = new ButtonAdv();
button2.Label = "Syncfusion";
button2.IconWidth=30;
button2.IconHeight=30;
button2.SmallIcon = new BitmapImage(new Uri("syncfusion.png"));
{% endhighlight %}
{% endtabs %}

![Icon Size](Getting-Started_images/Getting-Started_img10.png)