---
layout: post
title: 137-Styles-and-Templates
description: 1.3.7 styles and templates
platform: wpf
control: PivotGridControl
documentation: ug
---

# Styles and Templates

## Cell Styles

Column, row, summary, and value cells of a grid can be formatted independently by using the specific style properties as listed below:

* ColumnHeaderCellStyle – Specifies the style for column headers.
* RowHeaderCellStyle – Specifies the style for row headers.
* SummaryCellStyle – Specifies the style for summary cells.
* ValueCellStyle – Specifies the style for value cells.

The following properties of the cell can be customized.

<table>
<tr>
<th>
Property Name</th><th>
Description</th><th>
Type</th></tr>
<tr>
<td>
Background</td><td>
Gets or sets the background color of a grid cell.</td><td>
Brush</td></tr>
<tr>
<td>
FontFamily</td><td>
Gets or sets the font family of a grid cell.</td><td>
FontFamily</td></tr>
<tr>
<td>
FontSize</td><td>
Gets or sets the font size of a grid cell.</td><td>
int</td></tr>
<tr>
<td>
FontWeight</td><td>
Gets or sets the font weight of a grid cell.</td><td>
FontWeight</td></tr>
<tr>
<td>
Foreground</td><td>
Gets or sets the foreground color of a grid cell.</td><td>
Brush</td></tr>
</table>

### Defining the cell styles in PivotGrid

After defining the PivotGrid control, raise the Loaded event of PivotGrid control. Inside the `PivotGrid_Loaded()` event, set the properties of cell styles of PivotGrid control.

Please refer the below code snippet.

{% highlight C# %}

public partial class MainWindow: Window {
    public MainWindow() {
        InitializeComponent();
        pivotGrid += pivotGrid_Loaded;
    }

    void pivotGrid_Loaded(object sender, RoutedEventArgs e) {
        // Specifying the Background color for Grid column header
        pivotGrid.ColumnHeaderCellStyle.Background = new SolidColorBrush(Color.FromRgb(175, 209, 255));
        // Specifying the Background color for Grid row header
        pivotGrid.RowHeaderCellStyle.Background = new SolidColorBrush(Color.FromRgb(175, 209, 255));
        // Specifying the Background color for Grid summary cell
        pivotGrid.SummaryCellStyle.Background = new SolidColorBrush(Color.FromRgb(206, 225, 248));
        // Specifying the Font Family for Grid column header
        pivotGrid.ColumnHeaderCellStyle.FontFamily = new FontFamily("Arial");
        // Specifying the Font Family for Grid row header
        pivotGrid.RowHeaderCellStyle.FontFamily = new FontFamily("Arial");
        // Specifying the Font Family for Grid summary cell
        pivotGrid.SummaryCellStyle.FontFamily = new FontFamily("Calibri");
    }
}
    
{% endhighlight %}

![](Styles-and-Templates-images/PivotGrid shows customized styles.png)

## Cell Templates

Cell Templates feature of PivotGrid allows you to define the templates to change the appearance of elements, such as column, row, summary, and value cells that are present in the Grid. The style for each element in the Grid should be defined of type `PivotGridTemplateCell`. The customized template can be defined for the following properties of PivotGrid:

* ColumnHeaderCellStyle
* RowHeaderCellStyle
* SummaryHeaderStyle
* SummaryCellStyle
* ValueCellStyle

The expander’s in the Grid can also be customized with any UIElement and it should be named as “PART_Expander” to perform drill-up and drill-down operations.

### Defining Cell Templates in PivotGrid

After defining the PivotGrid control, define your own style for Row, Column, Value, Summary cells and assign that style to the corresponding property in PivotGrid control. 

Here, we defined our own style for row header cells by overriding expander icon and cell's TextBlock. After defining the style, we applied that style to `RowHeaderCellStyle` of PivotGrid control.

Please refer the below code snippet.

{% highlight xaml %}

    <Window.Resources>
        <ResourceDictionary>
            <ObjectDataProvider x:Key="data" ObjectType="{x:Type local:ProductSales}" MethodName="GetSalesData"/>
            
         <Style x:Key="rowStyle" TargetType="{x:Type syncfusion:PivotGridTemplateCell}">
                <Setter Property="MinHeight" Value="25"/>
                <Setter Property="Template">
                    <Setter.Value>
                        <ControlTemplate TargetType="{x:Type syncfusion:PivotGridTemplateCell}">
                            <StackPanel  Grid.Column="1" Orientation="Horizontal" Background="#FF119EDA">
                                <!--Expander control style, to enable expand/collapse control name should be "PART_Expander" -->
                                <Expander Margin="1" x:Name="PART_Expander" IsExpanded="{Binding IsExpanded,RelativeSource={RelativeSource TemplatedParent}}" Visibility="{Binding Converter={StaticResource expanderVisiblityConverter}}" Grid.Column="0" />

                                <!--Image block-->
                                <Image Margin="2,4,1,0" Grid.Column="1" VerticalAlignment="Top" HorizontalAlignment="Center">
                                    <Image.Style>
                                        <Style TargetType="{x:Type Image}">
                                            <Style.Triggers>
                                                <DataTrigger Binding="{Binding Path=Text, RelativeSource={RelativeSource TemplatedParent}}" Value="Car">
                                                    <Setter Property="Source" Value="{StaticResource Car}"/>
                                                    <Setter Property="Width" Value="32"/>
                                                    <Setter Property="Height" Value="32"/>
                                                </DataTrigger>
                                                <DataTrigger Binding="{Binding Path=Text, RelativeSource={RelativeSource TemplatedParent}}" Value="Bike">
                                                    <Setter Property="Source" Value="{StaticResource Bike}"/>
                                                    <Setter Property="Width" Value="32"/>
                                                    <Setter Property="Height" Value="32"/>
                                                </DataTrigger>
                                            </Style.Triggers>
                                        </Style>
                                    </Image.Style>
                                </Image>

                                <TextBlock Grid.Column="1" Margin="3,4,2,0"
                                           Text="{Binding Path=Text, RelativeSource={RelativeSource TemplatedParent}}" 
                                           TextWrapping="Wrap"
                                           VerticalAlignment="Top" FontFamily="Segoe UI" FontSize="12"
                                           />
                            </StackPanel>
                        </ControlTemplate>
                    </Setter.Value>
                </Setter>
            </Style>            
        </ResourceDictionary>
    </Window.Resources>
<Grid>
    <syncfusion:PivotGridControl HorizontalAlignment="Left" Name="pivotGrid" VerticalAlignment="Top" VisualStyle="Metro" ItemSource="{Binding   Source={StaticResource data}}">

        <syncfusion:PivotGridControl.PivotRows>
            <syncfusion:PivotItem FieldHeader="Product" FieldMappingName="Product" TotalHeader="Total" />
            <syncfusion:PivotItem FieldHeader="Date" FieldMappingName="Date" TotalHeader="Total" />
        </syncfusion:PivotGridControl.PivotRows>
        <syncfusion:PivotGridControl.PivotColumns>
            <syncfusion:PivotItem FieldHeader="Country" FieldMappingName="Country" TotalHeader="Total" />
            <syncfusion:PivotItem FieldHeader="State" FieldMappingName="State" TotalHeader="Total" />
        </syncfusion:PivotGridControl.PivotColumns>
        <syncfusion:PivotGridControl.PivotCalculations>
            <syncfusion:PivotComputationInfo CalculationName="Total" FieldName="Amount" Format="C" SummaryType="DoubleTotalSum" />
            <syncfusion:PivotComputationInfo CalculationName="Total" FieldName="Quantity" SummaryType="Count" />
        </syncfusion:PivotGridControl.PivotCalculations>

        <syncfusion:PivotGridControl.RowHeaderCellStyle>
            <syncfusion:PivotGridCellStyle Style="{StaticResource rowStyle}" />
        </syncfusion:PivotGridControl.RowHeaderCellStyle>

    </syncfusion:PivotGridControl>

</Grid>

{% endhighlight %}

![](Styles-and-Templates-images/PivotGrid shows templated cells.png)
