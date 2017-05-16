---
layout: post
title: Kanban Cards | SfKanban | wpf | Syncfusion
description: This section describes how the card can be customized using CardTemplate and how to set the IndicatorColorPalette to Kanban. 
platform: wpf
control: SfKanban
documentation: ug
---

# Cards

The default elements of a card can be customized using the below properties of [`KanbanModel`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel.html).

* [`Title`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~Title.html)         - Used to set the title of a card.
* [`ImageURL`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~ImageURL.html)      - Used to set the image URL of a card. The image will be displayed at right side in default card template.
* [`Category`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~Category.html)      - Used to set the category of a card. Based on the category the cards will be added to the respective columns. 
* [`Description`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~Description.html)   - Used to set the description text of a card.
* [`ColorKey`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~ColorKey.html)      - Used to specify the indicator color key. The color value of the corresponding key should be added in [`IndicatorColorPalette`](https://help.syncfusion.com/cr/cref_files/uwp/sfkanban/frlrfSyncfusionUIXamlKanbanIndicatorColorPaletteClassTopic.html) collection of [`SfKanban`](https://help.syncfusion.com/cr/cref_files/uwp/sfkanban/index.html#frlrfSyncfusionUIXamlKanbanSfKanbanClassTopic.html).
* [`Tags`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~Tags.html)     - Used to specify the tags of a card. The tags will be displayed at bottom in default card template.
* [`ID`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.KanbanModel~ID.html)     - Used to set the ID of a card.

{% highlight C# %}

new KanbanModel()
{

    Title = "Universal App",

    ID = "27654",

    Description = "Incorporate feedback into functional specifications",

    Category = "Open",

    ColorKey = "Low",

    Tags = new string[] { "Deployment" },

    ImageURL = new Uri("/images/icon.jpg")
};


{% endhighlight %}

Following code snippet is used to define the colors for each key.

{% tabs %}

{% highlight xaml %}

<kanban:SfKanban.IndicatorColorPalette>

    <kanban:ColorMapping Key="Low" Color="Blue"/>

    <kanban:ColorMapping Key="Normal" Color="Green" />

    <kanban:ColorMapping Key="High" Color="Red" />

</kanban:SfKanban.IndicatorColorPalette>

{% endhighlight %}

{% highlight C# %}

IndicatorColorPalette indicatorColorPalette = new IndicatorColorPalette();

indicatorColorPalette.Add(new ColorMapping() { Key = "Low", Color = Colors.Blue });

indicatorColorPalette.Add(new ColorMapping() { Key = "High", Color = Colors.Red });

indicatorColorPalette.Add(new ColorMapping() { Key = "Normal", Color = Colors.Green });

sfKanban.IndicatorColorPalette = indicatorColorPalette;

{% endhighlight %}

{% endtabs %}

![](SfKanban_images/CardCustomization.png)

## Template

You can replace the entire card template with your own design using [`SfKanban.CardTemplate`](https://help.syncfusion.com/cr/cref_files/wpf/sfkanban/Syncfusion.SfKanban.WPF~Syncfusion.UI.Xaml.Kanban.SfKanban~CardTemplate.html) property. The following code snippet and screenshot illustrates this.

{% highlight xaml %}

<kanban:SfKanban.CardTemplate>
    
    <DataTemplate>
    
        <Border BorderBrush="Black"
    
                BorderThickness="0.75"
    
                CornerRadius="10"
    
                Background="AliceBlue"
    
                Margin="0,5,0,5">
    
            <Grid Margin="10,5,5,10">
    
                <Grid.ColumnDefinitions>
    
                    <ColumnDefinition Width="7*" />
    
                    <ColumnDefinition Width="3*" />
                
                </Grid.ColumnDefinitions>
                
                <Grid.RowDefinitions>
                
                    <RowDefinition Height="Auto" />
                
                    <RowDefinition Height="Auto" />
                
                </Grid.RowDefinitions>
                
                <TextBlock Text="{Binding Path=Title}"
                
                           FontWeight="Bold"
                
                           FontSize="16" />
                
                <TextBlock Grid.Row="1"
                
                           FontSize="14"
                
                           HorizontalAlignment="Left"
                
                           Text="{Binding Description}"
                
                           TextWrapping="WrapWholeWords" />
                
                <Border Grid.Row="1"
                
                        Grid.Column="1"
                
                        Height="50"
                
                        CornerRadius="50"
                
                        Width="50"
                
                        BorderBrush="Silver"
                
                        BorderThickness=".75">
                
                    <Border.Background>
                
                        <ImageBrush ImageSource="{Binding ImageURL}" />
                
                    </Border.Background>
                
                </Border>
            
            </Grid>
        
        </Border>

    </DataTemplate>

</kanban:SfKanban.CardTemplate>

{% endhighlight %}


![](SfKanban_images/CardTemplate.png)