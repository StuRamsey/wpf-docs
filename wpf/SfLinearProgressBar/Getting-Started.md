---
layout: post
title: Getting Started | Linear ProgressBar | WPF | Syncfusion
description: How to create a simple application with Linear ProgressBar in WPF.
platform: WPF
control: SfLinearProgressBar
documentation: ug
---

# Creating a simple application with Linear ProgressBar

You can create a WPF application with the SfLinearProgressBar control using the following steps:

## Assembly deployment

Refer to the [control dependencies](https://help.syncfusion.com/wpf/control-dependencies#) section to get the list of assemblies or NuGet package that needs to be added as a reference to use the control in any application.

You can find more details about installing the NuGet package in a WPF application in the following link: [How to install nuget packages](https://help.syncfusion.com/wpf/nuget-packages)

## Adding control through designer

The SfLinearProgressBar control can be added to a WPF application by dragging it from the toolbox to a designer view. The following assembly reference will be added automatically:

* Syncfusion.SfProgressBar.WPF 

![wpf SfLinearProgressBar control added through designer](Getting-Started_images/wpf-SfLinearProgressBar-control-added-through-designer.png)

## Adding control manually in XAML

To add control manually in XAML, follow the given steps:

1.	Add the following required assembly reference to the project:
    * Syncfusion.SfProgressBar.WPF     
2.	Import Syncfusion WPF schema **http://schemas.syncfusion.com/wpf** in the XAML page.
3.	Declare the SfLinearProgressBar control in the XAML page.

{% tabs %}
{% highlight XAML %}
<Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:WpfApp4"
        xmlns:Syncfusion="http://schemas.syncfusion.com/wpf" x:Class="WpfApp4.MainWindow"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
     <Grid x:Name="grid">
        <Grid.RowDefinitions  >
            <RowDefinition Height="67*"/>
            <RowDefinition Height="143*"/>
        </Grid.RowDefinitions>
        <TextBlock Text="Linear" Margin="344,38,372.6,83.4"/>
        <Syncfusion:SfLinearProgressBar Progress="70" Margin="175,68,187.6,43.4"/>       
     </Grid>
</Window>
{% endhighlight %}
{% endtabs %}

## Adding control through code behind

To add control manually through code behind, follow the given steps:

1.	Add the following required assembly reference to the project:
   * Syncfusion.SfProgressBar.WPF
2.	Import the Linear ProgressBar namespace
    **using Syncfusion.UI.Xaml.ProgressBar;**
3.	Create an Linear Progressbar instance, and add it to the window.

{% tabs %}
{% highlight C# %}
using Syncfusion.UI.Xaml.ProgressBar;
namespace SfProgressBar
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {                  
        public MainWindow()
        {
            InitializeComponent();
            SfLinearProgressBar linear = new SfLinearProgressBar();          
            linear.Progress = 70;
            grid.Children.Add(linear);
        }      
    }
}
{% endhighlight %}
{% endtabs %}
![WPF Linear ProgressBar control added through code](Getting-Started_images/wpf-SfLinearProgressBar-control-added-manually.png)