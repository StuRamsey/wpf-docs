---
layout: post
title: Styles and Templates in SfDataGrid
description: How to apply styles and templates in SfDataGrid
platform: wpf
control: SfDataGrid
documentation: ug
---

# Styles and Templates

The appearance of SfDataGrid and its inner elements (example: Cell, Row, Header, Summary and etc.) can be customized using various properties exposed and editing its Style. 

## Control Structure of SfDataGrid

![](Styles-and-Templates_images/Styles-and-Templates_img1.png)

## Customizing Default Containers
SfDataGrid arrange the cell and row content using cell and row container’s. Below screenshot shows the VisualTree of SfDataGrid where HeaderCell loaded into the HeaderCellControl and data cells loaded into the VirtualizingCellsControl container. VirtualizingCellsControl container consist of GridCell to load the cell content.

![](Styles-and-Templates_images/Styles-and-Templates_img31.png)

[RowGenerator](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.RowGenerator.html) class processes the creation and re-using of containers for SfDataGrid. You create your own containers by overriding RowGenerator class and set it [SfDataGrid.RowGenerator](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowGenerator.html). Thus, it is possible to customize the row and cell containers by customizing the RowGeneration which cannot be done with styling and conditional styling customization options.

### Row containers
Below table shows the different types of grid rows and its container.
<table>
<tr>
<td>
{{'**RowType**'| markdownify }}
</td>
<td>
{{'**Container**'| markdownify }}
</td>
</tr>
<tr>
<td>
DataRow
</td>
<td>
VirtualizingCellsControl
</td>
</tr>
<tr>
<td>
UnboundRow
</td>
<td>
UnBoundRowControl
</td>
</tr>
<tr>
<td>
FilterRow
</td>
<td>
FilterRowControl
</td>
</tr>
<tr>
<td>
DetailsViewDataRow
</td>
<td>
DetailsViewRowControl
</td>
</tr>
<tr>
<td>
TableSummaryRow
</td>
<td>
TableSummaryRowControl
</td>
</tr>
<tr>
<td>
HeaderRow
</td>
<td>
HeaderRowControl
</td>
</tr>
<tr>
<td>
AddNewRow
</td>
<td>
AddNewRowControl
</td>
</tr>
<tr>
<td>
CaptionSummaryRow
</td>
<td>
CaptionSummaryRowControl
</td>
</tr>
<tr>
<td>
GroupSummaryRow
</td>
<td>
GroupSummaryRowControl
</td>
</tr>
<tr>
<td>
StackedHeaderRow
</td>
<td>
GridStackedHeaderCellControl
</td>
</tr>
</table>

### Animating the data row when property changes

You can customize the [DataRow](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DataRow.html) operations by overriding the `DataRow` class. You have to override the GetDataRow method in [RowGenerator](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.RowGenerator.html) to load the customized `DataRow`.
Similarly, you can able to customize:
1. [GridUnboundRow](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridUnBoundRow.html)
2. [FilterRow](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.RowFilter.FilterRow.html)
3. [SpannedDataRow](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SpannedDataRow.html)

The below code example shows how to animate the `DataRow` when the row data is changed.
{% tabs %}
{% highlight c# %}
this.dataGrid.RowGenerator = new CustomRowGenerator(this.dataGrid);

public class CustomDataRow : DataRow
{
    public CustomDataRow()
        : base()
    {                  
    }
     
    protected Storyboard sb = null;
    protected override void OnRowDataChanged()
    {
        base.OnRowDataChanged();
        if (this.WholeRowElement != null)
        {
            DoubleAnimation animation = new DoubleAnimation
            {
                From = 0,
                To = 1,
                Duration = new Duration(TimeSpan.FromMilliseconds(2000)),
                AutoReverse = true,
                FillBehavior = FillBehavior.Stop
            };

            Storyboard.SetTarget(animation, this.WholeRowElement);
            Storyboard.SetTargetProperty(animation, new PropertyPath(Path.OpacityProperty));
            sb = new Storyboard();
            sb.Children.Add(animation);
            sb.Begin();
        }        
    }             
}

public class CustomRowGenerator : RowGenerator
{
    public CustomRowGenerator(SfDataGrid dataGrid)
        : base(dataGrid)
    { }

    protected override GridDataRow GetDataRow<T>(RowType type)
    {
        //Set the customized DataRow.
        if (typeof(T) == typeof(DataRow))
            return new CustomDataRow();
        return base.GetDataRow<T>(type);
    }
}
{% endhighlight %}
{% endtabs %}

You can download a working demo for the above customization from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/wpf-953049514).
![](Styles-and-Templates_images/Styles-and-Templates_img32.png)

The below code example shows how to change the background color of the `VirtualizingCellsControl` when the value has been changed for a particular cell. This can be done by hooking the `DataContextChanged` and `PropertyChanged` event.
{% tabs %}
{% highlight c# %}
this.dataGrid.RowGenerator = new CustomRowGenerator(this.dataGrid);

public class CustomVirtualizingCellsControl : VirtualizingCellsControl
{
    public CustomVirtualizingCellsControl()
        : base()
    {
        this.DataContextChanged += CustomVirtualizingCellsControl_DataContextChanged;
    }

    private void CustomVirtualizingCellsControl_DataContextChanged(object sender, DependencyPropertyChangedEventArgs e)
    {
        var newValue = e.NewValue as INotifyPropertyChanged;
        newValue.PropertyChanged += NewValue_PropertyChanged;
    }      
    private void NewValue_PropertyChanged(object sender, PropertyChangedEventArgs e)
    {
        if (e.PropertyName == "CustomerID")
            this.Background = new SolidColorBrush(Colors.Pink);
    }
}

public class CustomRowGenerator : RowGenerator
{
    public CustomRowGenerator(SfDataGrid dataGrid)
        : base(dataGrid)
    { }

    protected override VirtualizingCellsControl GetVirtualizingCellsControl<T>()
    {
        //Set the customized VirtualizingCellsControl
        if (typeof(T) == typeof(VirtualizingCellsControl))
            return new CustomVirtualizingCellsControl();
        return base.GetVirtualizingCellsControl<T>();
    }
}
{% endhighlight %}
{% endtabs %}

You can download a working demo for the above customization from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/VirtualizingControl-1405123935.zip).

### Cell containers
Below table shows the different types of cells and its container.
<table>
<tr>
<td>
{{'**CellType**'| markdownify }}
</td>
<td>
{{'**Container**'| markdownify }}
</td>
</tr>
<tr>
<td>
GridCell
</td>
<td>
OrientedCellsPanel
</td>
</tr>
<tr>
<td>
GridUnBoundRowCell
</td>
<td>
OrientedCellsPanel
</td>
</tr>
<tr>
<td>
GridFilterRowCell
</td>
<td>
OrientedCellsPanel
</td>
</tr>
</table>

### Animating the data cell when property changes

You can customize the [GridCell](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCell.html) behavior by overriding the `GridCell` class. You have to override the GetGridCell method in [RowGenerator](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.RowGenerator.html) to load the customized `GridCell`.
Similarly, you can able to customize:
1. [GridUnBoundRowCell](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridUnBoundRowCell.html)
2. [GridFilterRowCell](https://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.RowFilter.GridFilterRowCell.html)
The below code example shows how to animate the cell based on the changes occur in another cell using the `DataContextChanged` and `PropertyChanged` events.
{% tabs %}
{% highlight c# %}
this.dataGrid.RowGenerator = new CustomRowGenerator(this.dataGrid);

public class CustomGridCell : GridCell
{       
    public CustomGridCell() : base()
    {
        this.DataContextChanged += CustomGridCell_DataContextChanged;            
    }
     
    private void CustomGridCell_DataContextChanged(object sender, DependencyPropertyChangedEventArgs e)
    {
        var newData = e.NewValue as INotifyPropertyChanged;
        newData.PropertyChanged += Data_PropertyChanged;
    }
    protected Storyboard sb = null;
    private void Data_PropertyChanged(object sender, PropertyChangedEventArgs e)
    {
        if (e.PropertyName == "CustomerID")
        {
            DoubleAnimation animation = new DoubleAnimation
            {
                From = 0,
                To = 1,
                Duration = new Duration(TimeSpan.FromMilliseconds(2000)),
                AutoReverse = false,
                FillBehavior = FillBehavior.HoldEnd
            };

            Storyboard.SetTarget(animation, this);
            Storyboard.SetTargetProperty(animation, new PropertyPath(Path.OpacityProperty));
            sb = new Storyboard();
            sb.Children.Add(animation);
            sb.Begin();
        }
    }

    protected override void Dispose(bool isDisposing)
    {
        this.DataContextChanged -= CustomGridCell_DataContextChanged;
        base.Dispose(isDisposing);
    }
}

public class CustomRowGenerator : RowGenerator
{
    public CustomRowGenerator(SfDataGrid dataGrid)
        : base(dataGrid)
    {
    }

    protected override GridCell GetGridCell<T>()
    {
        return new CustomGridCell();
    }
}
{% endhighlight %}
{% endtabs %}

You can download a working demo for the above customization from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/Gridcell-1615427562).

## Editing Style in Visual Studio Designer

You can edit the SfDataGrid style in Visual Studio Designer by right clicking it in design View and click **Edit Template**.

![](Styles-and-Templates_images/Styles-and-Templates_img2.png)

By clicking **Edit a Copy**, it will generate default template of SfDataGrid in **XAML view** and you can edit the default style.

## Editing DataGrid Elements Style in Visual Studio Designer

You can edit the SfDataGrid elements style in Visual Studio Designer by right clicking it in designer view and click **Edit Additional Templates**.

![](Styles-and-Templates_images/Styles-and-Templates_img3.png)

You can edit or create new style for the following SfDataGrid elements through **Edit Additional Templates** option,

1. HeaderStyle
2. HeaderTemplate
3. CellStyle
4. RowStyle
5. GroupDropAreaStyle
6. CaptionSummaryCellStyle
7. CaptionSummaryRowStyle
8. GroupSummaryCellStyle
9. GroupSummaryRowStyle
10. TableSummaryCellStyle
11. TableSummaryRowStyle
12. UnBoundRowCellStyle
13. UnBoundRowStyle
14. FilterPopupStyle
15. FilterPopupTemplate
16. DetailsViewDataGridStyle

N> Visual Studio Editing option is available from Visual Studio 2012 and higher versions only.

## Writing Style by TargetType

The appearance of SfDataGrid and its inner elements can be customized by writing style of TargetType to those control. If the key is not specified, then the style will be applied to all the SfDataGrid in its scope. You can apply specific to SfDataGrid or column or cell using various properties exposed.
 
## Styling Record cell

The record cells can be customized by writing style of TargetType [GridCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCell.html). You can set to particular SfDataGrid by setting [SfDataGrid.CellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CellStyle.html) property and the particular column can be styled by setting [GridColumn.CellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~CellStyle.html) property. Underlying record will be the DataContext for `GridCell`.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridCell" x:Key="customCellStyle">
        <Setter Property="Background" Value="Bisque" />
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid" 
                       CellStyle="{StaticResource customCellStyle}"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

You can also set the `CellStyle` to particular column in below way.

{% tabs %}
{% highlight xaml %}
<syncfusion:GridTextColumn MappingName="OrderID">
    <syncfusion:GridTextColumn.CellStyle>
        <Style TargetType="syncfusion:GridCell">
            <Setter Property="Background" Value="LightBlue" />
        </Style>
    </syncfusion:GridTextColumn.CellStyle>
</syncfusion:GridTextColumn>
{% endhighlight %}
{% endtabs %}

N> `GridColumn.CellStyle` takes higher priority than `SfDataGrid.CellStyle` property.

![](Styles-and-Templates_images/Styles-and-Templates_img4.png)

### Changing Grid line border as dotted line

You can change the gridline border as dotted line by customizing [GridCell.BorderBrush](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Windows.Controls.Control.BorderBrush)&rd=true) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridCell">
        <Setter Property="BorderBrush">
            <Setter.Value>
                <DrawingBrush Viewport="0,0,7,7" ViewportUnits="Absolute" TileMode="Tile">
                    <DrawingBrush.Drawing>
                        <DrawingGroup>
                            <GeometryDrawing Brush="Black">
                                <GeometryDrawing.Geometry>
                                    <GeometryGroup>
                                        <RectangleGeometry Rect="0,0,50,50" />
                                        <RectangleGeometry Rect="50,50,50,50" />
                                    </GeometryGroup>
                                </GeometryDrawing.Geometry>
                            </GeometryDrawing>
                        </DrawingGroup>
                    </DrawingBrush.Drawing>
                </DrawingBrush>
            </Setter.Value>
        </Setter>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img5.png)

### Changing Grid line color

You can also change the gridline color by setting [GridCell.BorderBrush](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.Windows.Controls.Control.BorderBrush)&rd=true) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridCell">
        <Setter Property="BorderBrush" Value="Green" />
    </Style>
</Window.Resources>
{% endhighlight %}
{% endtabs %}

## Styling Record row

The record rows can be customized by writing style of TargetType [VirtualizingCellsControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.VirtualizingCellsControl.html). You can set to particular SfDataGrid by setting [SfDataGrid.RowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:VirtualizingCellsControl" x:Key="customRowStyle">
        <Setter Property="Background" Value="Bisque"/>
    </Style>
</Window.Resources>
<syncfusion:SfDataGrid x:Name="dataGrid"
                       ItemsSource="{Binding Orders}" 
                       RowStyle="{StaticResource customRowStyle}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img6.png)

## Alternating Row Style

You can style the alternate rows by setting [SfDataGrid.AlternatingRowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AlternatingRowStyle.html) and [SfDataGrid.RowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowStyle.html) property. AlternateRowStyle will be applied based on [SfDataGrid.AlternationCount](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AlternationCount.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:VirtualizingCellsControl" x:Key="alternatingRowStyle">
        <Setter Property="Background" Value="LightBlue"/>
    </Style>

    <Style TargetType="syncfusion:VirtualizingCellsControl" x:Key="RowStyle">
        <Setter Property="Background" Value="Bisque"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid" 
                       AlternatingRowStyle="{StaticResource alternatingRowStyle}" 
                       AlternationCount="3"
                       RowStyle="{StaticResource RowStyle}"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img7.png)

## Selection

The foreground and background for the selected row, cell can be customized by setting [SfDataGrid.RowSelectionBrush](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowSelectionBrush.html) and [SfDataGrid.SelectionForegroundBrush](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionForegroundBrush.html) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       RowSelectionBrush="DarkBlue"  
                       SelectionForegroundBrush="Bisque"
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img8.png)

## Styling Column Header

### Styling Header cell

The header cell can be customized by writing style of TargetType [GridHeaderCellControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridHeaderCellControl.html). You can set to particular SfDataGrid by setting [SfDataGrid.HeaderStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~HeaderStyle.html) property and the particular column can be styled by setting [GridColumn.HeaderStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~HeaderStyle.html) property.

N> `GridColumn.HeaderStyle` takes higher priority than `SfDataGrid.HeaderStyle` property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridHeaderCellControl" x:Key="headerStyle">
        <Setter Property="FontWeight" Value="Bold"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       HeaderStyle="{StaticResource headerStyle}"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img9.png)

### Styling DetailsViewDataGrid header

The header style can be applied to [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) alone by setting [HeaderStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~HeaderStyle.html) property to `DetailsViewDataGrid` in both XAML and code behind.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridHeaderCellControl" x:Key="header">
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
			ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="Details">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="FirstDetailsViewGrid"
                                       HeaderStyle="{StaticResource header}">
                </syncfusion:SfDataGrid>
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

If [SfDataGrid.AutoGenerateRelations](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGenerateRelations.html) is true, you can set the header style to DetailsViewDataGrid in [SfDataGrid.AutoGenerateRelations](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGeneratingRelations_EV.html) event.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid" 
                       AutoGenerateRelations="True"                                
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% highlight c# %}
this.dataGrid.AutoGeneratingRelations += dataGrid_AutoGeneratingRelations;

void dataGrid_AutoGeneratingRelations
              (object sender, Syncfusion.UI.Xaml.Grid.AutoGeneratingRelationsArgs e)
{
            e.GridViewDefinition.DataGrid.HeaderStyle = (Style)this.Resources["header"];
}
{% endhighlight %}
{% endtabs %}

### Styling Stacked Headers

The appearance of stacked header can be customized by writing style of TargetType [GridStackedHeaderCellControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridStackedHeaderCellControl.html).

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridStackedHeaderCellControl">
        <Setter Property="FontWeight" Value="ExtraBold"/>
        <Setter Property="FontSize" Value="14"/>
        <Setter Property="Foreground" Value="DarkBlue"/>
    </Style>
</Window.Resources>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img10.png)

### Setting different styles to StackedHeader

You can apply the different style to stacked header by overriding the [default renderer](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CellRenderers.html) of StackedHeader.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <Style x:Key="style1" TargetType="syncfusion:GridStackedHeaderCellControl">
        <Setter Property="Background" Value="LightBlue" />
        <Setter Property="FontFamily" Value="Segoe UI" />
        <Setter Property="FontStyle" Value="Italic" />
        <Setter Property="FontWeight" Value="Bold"/>
    </Style>
    <Style x:Key="style2" TargetType="syncfusion:GridStackedHeaderCellControl">
        <Setter Property="Background" Value="Bisque" />
        <Setter Property="FontFamily" Value="Courier New" />
        <Setter Property="FontStyle" Value="Oblique" />
        <Setter Property="FontWeight" Value="Bold"/>
    </Style>
</Application.Resources>
{% endhighlight %}
{% highlight c# %}
//Default GridStackedCellRenderer is removed.
this.dataGrid.CellRenderers.Remove("StackedHeader");
//Customized GridStackedCellRenderer is added.
this.dataGrid.CellRenderers.Add("StackedHeader", new GridCustomStackedRenderer());

public class GridCustomStackedRenderer : GridStackedHeaderCellRenderer
{
    public GridCustomStackedRenderer()
    {

    }
    public override void OnInitializeEditElement(DataColumnBase dataColumn, GridStackedHeaderCellControl uiElement, object dataContext)
    {
        if (dataColumn.ColumnIndex == 0)
            uiElement.Style = App.Current.Resources["style1"] as Style;
        else if (dataColumn.ColumnIndex == 2) 
            uiElement.Style = App.Current.Resources["style2"] as Style;            
        base.OnInitializeEditElement(dataColumn, uiElement, dataContext);
    }
}
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img11.png)

## Setting Default Style for one column

You can also skip the cell styling for particular column from other setting like [SfDataGrid.CellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CellStyle.html) by setting [GridColumn.CellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~CellStyle.html) to null. Likewise, you can skip all the style properties in particular column (example: `HeaderStyle`). 

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridCell" x:Key="customCellStyle">
        <Setter Property="Background" Value="Bisque" />
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid" 
                       CellStyle="{StaticResource customCellStyle}"
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn MappingName="OrderID" 
                                   CellStyle="{x:Null}" />        
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.dataGrid.Columns["OrderID"].CellStyle = null;
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img12.png)

## Styling CaptionSummary 

### Styling CaptionSummary cells

The caption summary cells can be customized by writing style of TargetType [GridCaptionSummaryCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCaptionSummaryCell.html). You can set to particular SfDataGrid by setting [SfDataGrid.CaptionSummaryCellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CaptionSummaryCellStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridCaptionSummaryCell" x:Key="customCaptionSummaryCell">
       <Setter Property="FontWeight" Value="Bold"/>
       <Setter Property="Foreground" Value="DarkBlue"/>
       <Setter Property="FontStyle" Value="Italic"/>
       <Setter Property="FontSize" Value="14"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid" 
                       ShowGroupDropArea="True"
                       CaptionSummaryCellStyle="{StaticResource customCaptionSummaryCell}"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img13.png)

### Styling CaptionSummary rows

The caption summary rows can be customized by writing style of TargetType [GridCaptionSummaryRowControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CaptionSummaryRowControl.html). You can set to particular SfDataGrid by setting [SfDataGrid.CaptionSummaryRowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CaptionSummaryRowStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:CaptionSummaryRowControl" x:Key="captionSummaryRowStyle">
        <Setter Property="FontWeight" Value="SemiBold"/>
       <Setter Property="Background" Value="Bisque"/>
       <Setter Property="FontStyle" Value="Oblique"/>
       <Setter Property="FontSize" Value="18"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ShowGroupDropArea="True"
                       CaptionSummaryRowStyle="{StaticResource captionSummaryRowStyle}"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img14.png)

## Styling GroupSummary

### Styling GroupSummary cells

The group summary cells can be customized by writing style of TargetType [GridGroupSummaryCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridGroupSummaryCell.html). You can set to particular SfDataGrid by setting [SfDataGrid.GroupSummaryCellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupSummaryCellStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridGroupSummaryCell" x:Key="customGroupSummary">
       <Setter Property="FontWeight" Value="SemiBold"/>
       <Setter Property="Foreground" Value="DarkBlue"/>
       <Setter Property="FontStyle" Value="Oblique"/>
       <Setter Property="FontSize" Value="14"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ShowGroupDropArea="True"
                       GroupSummaryCellStyle="{StaticResource customGroupSummary}"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img15.png)

### Styling GroupSummary rows

The group summary rows can be customized by writing style of TargetType [GridGroupSummaryRowControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupSummaryRowControl.html). You can set to particular SfDataGrid by setting [SfDataGrid.GroupSummaryRowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupSummaryRowStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GroupSummaryRowControl" x:Key="customGroupSummaryRowControl">
        <Setter Property="Background" Value="Bisque"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       GroupSummaryRowStyle="{StaticResource customGroupSummaryRowControl}"
                       ShowGroupDropArea="True"                                                
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img16.png)

## Styling TableSummary

### Styling TableSummary cells

The table summary cells can be customized by writing style of TargetType [GridTableSummaryCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridTableSummaryCell.html). You can set to particular SfDataGrid by setting [SfDataGrid.TableSummaryCellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~TableSummaryCellStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style x:Key="customTableSummary" TargetType="syncfusion:GridTableSummaryCell">
            <Setter Property="Foreground" Value="DarkBlue" />
            <Setter Property="FontSize" Value="16" />
            <Setter Property="FontWeight" Value="Bold" />
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ItemsSource="{Binding Orders}"
                       TableSummaryCellStyle="{StaticResource customTableSummary}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img17.png)

### Styling TableSummary rows

The table summary rows can be customized by writing style of TargetType [GridTableSummaryRowControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.TableSummaryRowControl.html). You can set to particular SfDataGrid by setting [SfDataGrid.TableSummaryRowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~TableSummaryRowStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:TableSummaryRowControl" x:Key="tableSummaryRowStyle">
        <Setter Property="Background" Value="Bisque"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"                
                       ItemsSource="{Binding Orders}" 
                       TableSummaryRowStyle="{StaticResource tableSummaryRowStyle}"  />
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img18.png)

## Styling UnboundRows

### Styling unbound row cells

The unbound row cells can be customized by writing style of TargetType [GridUnBoundRowCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridUnBoundRowCell.html). You can set to particular SfDataGrid by setting [SfDataGrid.UnBoundRowCellStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~UnBoundRowCellStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Style TargetType="syncfusion:GridUnBoundRowCell" x:Key="style">
    <Setter Property="FontWeight" Value="SemiBold"/>
</Style>

<syncfusion:SfDataGrid x:Name="sfDataGrid"                                                                                                            
                       ItemsSource="{Binding YearlySalesDetails}"                            
                       UnBoundRowCellStyle="{StaticResource style}"/>              
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img19.png)

### Styling unbound row 

The unbound rows can be customized by writing style of TargetType [UnBoundRowControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.UnBoundRowControl.html). You can set to particular SfDataGrid by setting [SfDataGrid.UnBoundRowStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~UnBoundRowStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Style TargetType="syncfusion:UnBoundRowControl" x:Key="rowStyle">
    <Setter Property="Foreground" Value="blue"/>
</Style>

<syncfusion:SfDataGrid x:Name="sfDataGrid"                                                                                                            
                       ItemsSource="{Binding YearlySalesDetails}" 
                       UnBoundRowStyle="{StaticResource rowStyle}"/>                      
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img20.png)

## Styling AddNewRow

The appearance of AddNewRow can customized by writing style of TargetType [AddNewRowControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.AddNewRowControl.html).

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style  TargetType="Syncfusion:AddNewRowControl">
        <Setter Property="AddNewRowText" Value="Enter value to add new row"/>
        <Setter Property="FontWeight" Value="Bold"/>        
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid" 
                       AddNewRowPosition="Top"
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img21.png)

## Styling RowHeader

The appearance of header row can be customized by writing style of TargetType [HeaderRowControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.HeaderRowControl.html).

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:HeaderRowControl">
        <Setter Property="Background" Value="Bisque"/>
        <Setter Property="BorderThickness" Value="1"/>
    </Style>
</Window.Resources>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img22.png)

### Displaying row index in row header cell

The appearance of row header can be customized by writing style of TargetType [RowHeaderCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridRowHeaderCell.html).

You can also display the row index value in the row header cell by customizing its style.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GridRowHeaderCell">
        <Setter Property="Template">
            <Setter.Value>
                <ControlTemplate TargetType="syncfusion:GridRowHeaderCell">
                    <Border x:Name="PART_RowHeaderCellBorder"
                        Background="Bisque"
                        BorderBrush="{TemplateBinding BorderBrush}"
                        BorderThickness="{TemplateBinding BorderThickness}">
                        <Grid>
                            <!--RowIndex is displayed here -->
                            <TextBlock HorizontalAlignment="Center"
                                    VerticalAlignment="Center"
                                    Text="{Binding RowIndex,
                                    RelativeSource={RelativeSource TemplatedParent}}"
                                    TextAlignment="Center" />
                        </Grid>
                    </Border>
                </ControlTemplate>
            </Setter.Value>
        </Setter>
    </Style>
</Window.Resources>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img23.png)

## Template Selectors

The [DataTemplateSelectors](https://msdn.microsoft.com/en-us/library/system.windows.controls.datatemplateselector.aspx) can be used to set the custom templates to the cell or rows based on the data. You can set to particular SfDataGrid by setting [SfDataGrid.CellTemplateSelector](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~CellTemplateSelector.html) and the template can be set to particular column by setting [GridColumn.CellTemplateSelector](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~CellTemplateSelector.html).

Here, custom template applied to TotalPrice and CustomerID columns.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <DataTemplate x:Key="CellTemplate1">
        <TextBlock Foreground="DarkBlue" Text="{Binding Path=Value}" />
    </DataTemplate>
    <DataTemplate x:Key="CellTemplate2">
        <TextBlock Foreground="DarkRed" Text="{Binding Path=Value}" />
    </DataTemplate>
</Application.Resources>

<Window.Resources>
        <local:GridCellTemplateSelector x:Key="templateSelector"/>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ItemsSource="{Binding Orders}" 
                       CellTemplateSelector="{StaticResource templateSelector}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTemplateColumn MappingName="TotalPrice" 
                                       SetCellBoundValue="True" />
        <syncfusion:GridTemplateColumn MappingName="CustomerName" SetCellBoundValue="True"/>
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
public class GridCellTemplateSelector : DataTemplateSelector
{
    public override DataTemplate SelectTemplate(object item, DependencyObject container)
    {
        var data = (item as DataContextHelper).Record as OrderInfo;
        //custom logic is checked.
        if (data.TotalPrice < 1005)
            return Application.Current.Resources["CellTemplate1"] as DataTemplate;
        else
            return Application.Current.Resources["CellTemplate2"] as DataTemplate;
    }
}
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img24.png)

### Changing HeaderTemplates

You can customize the appearance of particular SfDataGrid column header by setting [SfDataGrid.HeaderTemplate](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~HeaderTemplate.html) and the particular column header can be customized by setting [GridColumn.HeaderTemplate](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~HeaderTemplate.html).

{% tabs %}
{% highlight xaml %}
<DataTemplate x:Key="headerTemplate">
    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition Width="*" />
        </Grid.ColumnDefinitions>
        <TextBlock Grid.Column="0" VerticalAlignment="Center"
            Foreground="Black" Text="{Binding}" />
        <Image Source="/Assets/S3.png" Grid.Column="1" />
    </Grid>
</DataTemplate>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ItemsSource="{Binding Orders}" 
                       HeaderTemplate="{StaticResource headerTemplate}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img25.png)

### Loading different editor elements in a same column

The different editor elements can be loaded in a same template column conditionally based on data by setting [GridTemplateColumn.EditTemplateSelector](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridTemplateColumn~EditTemplateSelector.html).
 
{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <DataTemplate x:Key="DatePicker">
        <DatePicker/>
    </DataTemplate>

    <DataTemplate x:Key="textbox">
        <TextBox/>
    </DataTemplate>
</Application.Resources>

<Window.Resources>
    <local:GridCellEditTemplateSelector x:Key="editSelector"/>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"  
                       AllowEditing="True"            
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTemplateColumn HeaderText="Employee Name"           
                                       MappingName="CustomerName" 
                                       EditTemplateSelector="{StaticResource editSelector}" />
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

For example, in the below code example TextBox or DatePicker will be loaded based on TotalPrice property of Underlying data.

{% tabs %}
{% highlight c# %}
public class GridCellEditTemplateSelector : DataTemplateSelector
{
    public override DataTemplate SelectTemplate(object item, DependencyObject container)
    {
        if((item as OrderInfo).TotalPrice < 1005)
            return Application.Current.Resources["textbox"] as DataTemplate;
        else
            return Application.Current.Resources["DatePicker"] as DataTemplate;            
    }        
}
{% endhighlight %}
{% endtabs %}

## Styling DetailsViewDataGrid

The appearance of [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) can be customized by writing style of TargetType `DetailsViewDataGrid`. You can set to particular SfDataGrid by setting [SfDataGrid.DetailsViewDataGridStyle](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~DetailsViewDataGridStyle.html) property.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="{x:Type syncfusion:DetailsViewDataGrid}" x:Key="detailsViewStyle">
        <Setter Property="Background" Value="Bisque" />
        <Setter Property="BorderBrush" Value="Blue" />
        <Setter Property="FontWeight" Value="Bold"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid" 
                       AutoGenerateRelations="True"   
                       DetailsViewDataGridStyle="{StaticResource detailsViewStyle}"           
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img26.png)

## Styling Filter popup

[Refer here for filter popup styling](http://help.syncfusion.com/wpf/sfdatagrid/filtering#appearance-customization)
 
## Styling Sort icon

The appearance of sort indicator can be customized by editing the style of [GridHeaderCellControl](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridHeaderCellControl.html). Once the `GridHeaderCellControl` style is edited, go to PART_SortButtonPresenter.

### Default GridHeaderCellControl style

{% tabs %}
{% highlight xaml %}
<syncfusion:SortDirectionToVisibilityConverter x:Key="sortDirectionToVisibilityConverter" />
<syncfusion:SortDirectionToWidthConverter x:Key="sortDirectionToWidthConverter" />
<Style TargetType="syncfusion:GridHeaderCellControl">
    <Setter Property="Background" Value="Red" />
    <Setter Property="BorderBrush" Value="Gray" />
    <Setter Property="BorderThickness" Value="0,0,1,1" />
    <Setter Property="HorizontalContentAlignment" Value="Left" />
    <Setter Property="Padding" Value="5,3,5,3" />
    <Setter Property="Foreground" Value="Gray" />
    <Setter Property="FontSize" Value="14" />
    <Setter Property="FontWeight" Value="Normal" />
    <Setter Property="IsTabStop" Value="False" />
    <Setter Property="syncfusion:VisualContainer.WantsMouseInput" Value="True" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="syncfusion:GridHeaderCellControl">
                <Grid>
                    <VisualStateManager.VisualStateGroups>
                        <VisualStateGroup x:Name="HiddenColumnsResizingStates">
                            <VisualState x:Name="PreviousColumnHidden">
                                <Storyboard>
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_HeaderCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="3, 0, 1, 1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="HiddenState">
                                <Storyboard>
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_HeaderCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="3, 0, 3, 1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            <VisualState x:Name="NormalState" />

                            <VisualState x:Name="LastColumnHidden">
                                <Storyboard>
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_HeaderCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="0, 0, 3, 1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                        </VisualStateGroup>
                        <VisualStateGroup x:Name="CommonStates">
                            <VisualState x:Name="MouseOver" />
                            <VisualState x:Name="Normal" />
                        </VisualStateGroup>
                        <VisualStateGroup x:Name="BorderStates">
                            <VisualState x:Name="NormalCell" />
                            <VisualState x:Name="FrozenColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_HeaderCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="0,0,1,1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            <VisualState x:Name="FooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_FooterCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="1,0,1,1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            <VisualState x:Name="BeforeFooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_FooterCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="0,0,0,1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
                                                                      Duration="1"
                                                                      Storyboard.TargetName="PART_HeaderCellBorder"
                                                                      Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0" Value="0,0,0,1" />
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                        </VisualStateGroup>
                    </VisualStateManager.VisualStateGroups>
                    <Border x:Name="PART_FooterCellBorder"
                            Background="{TemplateBinding Background}"
                            BorderBrush="{TemplateBinding BorderBrush}" />
                    <Border x:Name="PART_HeaderCellBorder"
                            Background="{TemplateBinding Background}"
                            BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}"
                            SnapsToDevicePixels="True">
                        <Grid Margin="{TemplateBinding Padding}" SnapsToDevicePixels="True">
                            <Grid.ColumnDefinitions>
                                <ColumnDefinition Width="*" />
                                <ColumnDefinition Width="Auto" />
                                <ColumnDefinition Width="Auto" />
                            </Grid.ColumnDefinitions>

                            <ContentPresenter HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}"
                                              VerticalAlignment="Center"
                                              Focusable="False" />

                            <Border x:Name="PART_FilterPopUpPresenter" />

                            <Grid x:Name="PART_SortButtonPresenter"
                                    Grid.Column="1"
                                    SnapsToDevicePixels="True">
                                <Grid.ColumnDefinitions>
                                    <ColumnDefinition Width="0" MinWidth="{Binding Path=SortDirection, Mode=OneWay, RelativeSource={RelativeSource TemplatedParent}, Converter={StaticResource sortDirectionToWidthConverter}}" />
                                    <ColumnDefinition Width="*" />
                                </Grid.ColumnDefinitions>

                                <Path Width="8.938"
                                      Height="8.138"
                                      HorizontalAlignment="Center"
                                      VerticalAlignment="Center"
                                      Data="F1M753.644,-13.0589L753.736,-12.9639 753.557,-12.7816 732.137,8.63641 732.137,29.7119 756.445,5.40851 764.094,-2.24384 764.275,-2.42352 771.834,5.1286 796.137,29.4372 796.137,8.36163 774.722,-13.0589 764.181,-23.5967 753.644,-13.0589z"
                                      Fill="Gray"
                                      SnapsToDevicePixels="True"
                                      Stretch="Fill"
                                      Visibility="{Binding Path=SortDirection,
                                                  RelativeSource={RelativeSource TemplatedParent},
                                                  ConverterParameter=Ascending,
                                                  Converter={StaticResource sortDirectionToVisibilityConverter}}">
                                    <Path.RenderTransform>
                                        <TransformGroup>
                                            <TransformGroup.Children>
                                                <RotateTransform Angle="0" />
                                                <ScaleTransform ScaleX="1" ScaleY="1" />
                                            </TransformGroup.Children>
                                        </TransformGroup>
                                    </Path.RenderTransform>
                                </Path>

                                <Path Width="8.938"
                                      Height="8.138"
                                      HorizontalAlignment="Center"
                                      VerticalAlignment="Center"
                                      Data="F1M181.297,177.841L181.205,177.746 181.385,177.563 202.804,156.146 202.804,135.07 178.497,159.373 170.847,167.026 170.666,167.205 163.107,159.653 138.804,135.345 138.804,156.42 160.219,177.841 170.76,188.379 181.297,177.841z"
                                      Fill="Gray"
                                      SnapsToDevicePixels="True"
                                      Stretch="Fill"
                                      Visibility="{Binding Path=SortDirection,
                                                  RelativeSource={RelativeSource TemplatedParent},
                                                  ConverterParameter=Decending,
                                                  Converter={StaticResource sortDirectionToVisibilityConverter}}">
                                    <Path.RenderTransform>
                                        <TransformGroup>
                                            <TransformGroup.Children>
                                                <RotateTransform Angle="0" />
                                                <ScaleTransform ScaleX="1" ScaleY="1" />
                                            </TransformGroup.Children>
                                        </TransformGroup>
                                    </Path.RenderTransform>
                                </Path>

                                <TextBlock Grid.Column="1"
                                           Margin="0,-4,0,0"
                                           VerticalAlignment="Center"
                                           FontSize="10"
                                           Foreground="{TemplateBinding Foreground}"
                                           SnapsToDevicePixels="True"
                                           Text="{TemplateBinding SortNumber}"
                                           Visibility="{TemplateBinding SortNumberVisibility}" />

                            </Grid>

                            <syncfusion:FilterToggleButton x:Name="PART_FilterToggleButton"
                                                           Grid.Column="2"
                                                           HorizontalAlignment="Stretch"
                                                           VerticalAlignment="Stretch"
                                                           SnapsToDevicePixels="True"
                                                           Visibility="{TemplateBinding FilterIconVisiblity}" />

                        </Grid>
                    </Border>

                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
{% endhighlight %}
{% endtabs %}

Totally two paths will be present under the PART_SortButtonPresenter. You can change the appearance of Ascending sort indicator by customizing first path present in this. 
Here, height and color of the indicator is customized in the below code example.

### Customizing Ascending Sort Indicator

{% tabs %}
{% highlight xaml %}
<Path Data="F1M753.644,-13.0589L753.736,-12.9639 753.557,-12.7816 732.137,8.63641 732.137,29.7119 756.445,5.40851 764.094,-2.24384 764.275,-2.42352 771.834,5.1286 796.137,29.4372 796.137,8.36163 774.722,-13.0589 764.181,-23.5967 753.644,-13.0589z" 
        Fill="DarkBlue" 
        HorizontalAlignment="Center" 
        Height="15" 
        Stretch="Fill" 
        SnapsToDevicePixels="True"
        VerticalAlignment="Center"
        Width="12">
    <Path.RenderTransform>
        <TransformGroup>
            <RotateTransform Angle="0"/>
            <ScaleTransform ScaleY="1" ScaleX="1"/>
        </TransformGroup>
    </Path.RenderTransform>
    <Path.Visibility>
        <Binding ConverterParameter="Ascending" Path="SortDirection" RelativeSource="{RelativeSource TemplatedParent}">
            <Binding.Converter>
                <syncfusion:SortDirectionToVisibilityConverter/>
            </Binding.Converter>
        </Binding>
    </Path.Visibility>
</Path>
{% endhighlight %}
{% endtabs %}

And also, you can change the appearance of Descending sort indicator by customizing second path present in PART_SortButtonPresenter. For example, in the below code example height and color of the indicator is changed.

![](Styles-and-Templates_images/Styles-and-Templates_img27.png)

### Customizing Descending Sort Indicator

{% tabs %}
{% highlight xaml %}
<Path Data="F1M181.297,177.841L181.205,177.746 181.385,177.563 202.804,156.146 202.804,135.07 178.497,159.373 170.847,167.026 170.666,167.205 163.107,159.653 138.804,135.345 138.804,156.42 160.219,177.841 170.76,188.379 181.297,177.841z"
        Fill="DarkGreen" 
        HorizontalAlignment="Center" 
        Height="15"
        Stretch="Fill" 
        SnapsToDevicePixels="True" 
        VerticalAlignment="Center" 
        Width="11">
    <Path.RenderTransform>
        <TransformGroup>
            <RotateTransform Angle="0"/>
            <ScaleTransform ScaleY="1" ScaleX="1"/>
        </TransformGroup>
    </Path.RenderTransform>
    <Path.Visibility>
        <Binding ConverterParameter="Decending" Path="SortDirection" RelativeSource="{RelativeSource TemplatedParent}">
            <Binding.Converter>
                <syncfusion:SortDirectionToVisibilityConverter/>
            </Binding.Converter>
        </Binding>
    </Path.Visibility>
</Path>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img28.png)

## Styling GroupDropArea

The appearance of `GroupDropArea` can be customized by writing style of TargetType [GroupDropArea](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupDropArea.html). You can disable the water mark displayed in GroupDropArea by setting [WaterMarkTextVisibility](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupDropArea~WatermarkTextVisibility.html) as Collapsed.

{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GroupDropArea">
        <Setter Property="BorderBrush" Value="Blue"/>
        <Setter Property="Foreground" Value="DarkBlue"/>
        <Setter Property="FontWeight" Value="Medium"/>
        <Setter Property="WatermarkTextVisibility" Value="Visible"/>
    </Style>
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       ShowGroupDropArea="True"
                       ItemsSource="{Binding Orders}"/>
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img29.png)

## Showing busy indicator before loading records

You can show the indication of data loading with the help of BusyIndicator by setting BusyIndicator.IsBusy as True and you can stop it by setting BusyIndicator.IsBusy as false in the ItemsSourceChanged event.

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfBusyIndicator Name="sfBusyIndicator"
                            IsBusy="True"
                            Margin="5"
                            VerticalAlignment="Center"
                            AnimationType="Gear"/>
{% endhighlight %}
{% highlight c# %}
sfDataGrid.Loaded += sfDataGrid_Loaded;
sfDataGrid.ItemsSourceChanged += sfDataGrid_ItemsSourceChanged;

async void sfDataGrid_Loaded(object sender, RoutedEventArgs e)
{
    this.sfDataGrid.ItemsSource = await (this.DataContext as ViewModel).GetRecords();
}

void sfDataGrid_ItemsSourceChanged(object sender, GridItemsSourceChangedEventArgs e)
{
    sfBusyIndicator.IsBusy = false;
}
{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img30.png)

## VisualStyle

The ppearance of the SfDataGrid control is customized using the [VisualStyle](https://help.syncfusion.com/cr/cref_files/wpf/sfskinmanager/Syncfusion.SfSkinManager.WPF~Syncfusion.SfSkinManager.VisualStyles.html) property of `SfSkinManager`. Refer to the following built-in themes and available assemblies:

<table>
<tr>
<td>
{{'**Style**'| markdownify }}
</td>
<td>
{{'**Assemblies**'| markdownify }}
</td>
</tr>
<tr>
<td>
Metro
</td>
<td>
Syncfusion.Themes.Metro.Wpf.dll
</td>
</tr>
<tr>
<td>
Lime
</td>
<td>
Syncfusion.Themes.Lime.Wpf.dll
</td>
</tr>
<tr>
<td>
Saffron
</td>
<td>
Syncfusion.Themes.Saffron.Wpf.dll
</td>
</tr>
<tr>
<td>
Blend
</td>
<td>
Syncfusion.Themes.Blend.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2013White
</td>
<td>
Syncfusion.Themes.Office2013White.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2013LightGray
</td>
<td>
Syncfusion.Themes.Office2013LightGray.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2013DarkGray
</td>
<td>
Syncfusion.Themes.Office2013DarkGray.Wpf.dll
</td>
</tr>
<tr>
<td>
VisualStudio2013
</td>
<td>
Syncfusion.Themes.VisualStudio2013.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2010Black
</td>
<td>
Syncfusion.Themes.Office2010Black.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2010Blue
</td>
<td>
Syncfusion.Themes.Office2010Blue.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2010Silver
</td>
<td>
Syncfusion.Themes.Office2010Silver.Wpf.dll
</td>
</tr>
<tr>
<td>
Office365
</td>
<td>
Syncfusion.Themes.Office365.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2016Colorful
</td>
<td>
Syncfusion.Themes.Office2016Colorful.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2016White
</td>
<td>
Syncfusion.Themes.Office2016White.Wpf.dll
</td>
</tr>
<tr>
<td>
Office2016DarkGray
</td>
<td>
Syncfusion.Themes.Office2016DarkGray.Wpf.dll
</td>
</tr>
<tr>
<td>
VisualStudio2015
</td>
<td>
Syncfusion.Themes.VisualStudio2015.Wpf.dll
</td>
</tr>
</table>

### Apply VisualStyle to SfDataGrid

Any built-in themes can be applied to SfDataGrid by setting VisualStyle attached property of the SfSkinManager. To apply theme for the SfDatagrid control, follow the code example:

{% tabs %}
{% highlight xaml %}

	<syncfusion:SfDataGrid x:Name="dataGrid"
							AddNewRowPosition="Top"
							AllowFiltering="True"
							sfSkin:SfSkinManager.VisualStyle="Office2016Colorful"
							ItemsSource="{Binding OrdersDetails}"
							NavigationMode="Cell"
							ShowGroupDropArea="True"
							HideEmptyGridViewDefinition="True"
							ShowRowHeader="True" />
						
{% endhighlight %}
{% highlight c# %}

	SfSkinManager.SetVisualStyle(dataGrid, VisualStyles.Office2016Colorful);	

{% endhighlight %}
{% endtabs %}

![](Styles-and-Templates_images/Styles-and-Templates_img35.png)

### Apply themes at runtime

To apply built-in themes at runtime, use VisualStyle property. Here the ComboBox control is used to switch various built-in themes that are referred in assembly references. 

![](Styles-and-Templates_images/Styles-and-Templates_img33.png)

{% tabs %}
{% highlight xaml %}

	<syncfusion:SfDataGrid x:Name="dataGrid"
							AddNewRowPosition="Top"
							AllowFiltering="True"
							sfSkin:SfSkinManager.VisualStyle="Office2016Colorful"
							ItemsSource="{Binding OrdersDetails}"
							NavigationMode="Cell"
							ShowGroupDropArea="True"
							HideEmptyGridViewDefinition="True"
							ShowRowHeader="True" />
							
	<StackPanel Margin="5">
		<TextBlock Margin="5" FontSize="12" FontWeight="Bold" Text="Visual Styles:" />
							
		<ComboBox x:Name="StylesComboBox" ItemsSource="{Binding Path=ComboBoxItemsSource}" FocusVisualStyle="{x:Null}" 
					SelectedIndex="1" Height="30" VerticalContentAlignment="Center" Margin="5">
			<interactivity:Interaction.Triggers>
				<interactivity:EventTrigger EventName="SelectionChanged">
					<local:VisualThemesTriggerAction TargetName="dataGrid" />
				</interactivity:EventTrigger>
			</interactivity:Interaction.Triggers>
		</ComboBox>
	</StackPanel>

{% endhighlight %}
{% highlight c# %}

	public class VisualThemesTriggerAction : TargetedTriggerAction<ComboBox>
	{
		SfDataGrid grid = (Application.Current.MainWindow as VisualStylesDemo.MainWindow).dataGrid;

		/// <summary>
		/// Invokes the specified parameter.
		/// </summary>
		/// <param name="parameter">The parameter.</param>
		protected override void Invoke(object parameter)
		{
			var cb = this.AssociatedObject as ComboBox;
			// Apply Visual Style based on the selected theme
			switch (cb.SelectedItem.ToString())
			{
				case "Metro":
					SfSkinManager.SetVisualStyle(grid, VisualStyles.Metro);
					break;           
				case "Office2016Colorful":
					SfSkinManager.SetVisualStyle(grid, VisualStyles.Office2016Colorful);
					break;
				case "VisualStudio2015":
					SfSkinManager.SetVisualStyle(grid, VisualStyles.VisualStudio2015);
					break;
				default:
					SfSkinManager.SetVisualStyle(grid, VisualStyles.Default);
					break;
			}
		}
	}

{% endhighlight %}
{% endtabs %}

## ThemeStudio 

### Applying themes in ThemeStudio

Predefined themes can be applied by choosing themes from the theme list. It is available in the DropDown option near the Personalize heading. Refer to the following link to apply theme in [ThemeStudio](https://help.syncfusion.com/wpf/themes/theme-studio#applying-predefined-themes-in-theme-studio) for the Syncfusion controls.

### Applying the custom theme in SfDataGrid application

To apply the custom theme, generate the resource dictionary xaml file from ThemeStudio. Refer to the following link to generate the resource dictionary file and then apply the [custom theme](https://help.syncfusion.com/wpf/themes/theme-studio#applying-generated-resource-xaml-in-application) to SfDataGrid control. 

#### Adding XAML files to WPF application

<ul>
<li> Open Visual Studio 20xx and create WPF project. </li>

<li> Add necessary dll for the controls used. For example, add SfDataGrid control to the application. SfDataGrid control requires Syncfusion.SfGrid.WPF, Syncfusion.Data.WPF, and Syncfusion.Shared.WPF assembly in the application. </li>

<li> In ThemeStudio, you can get the customized style of SfDataGrid from the Output folder as described in the export topic. </li>

<li> From the Output folder, browse the Syncfusion controls folder and add the required XAML file to the project. </li> 
  
      ![](Styles-and-Templates_images/Styles-and-Templates_img37.png)

<li> Now initialize the SfDataGrid control in the MainWindow.xaml as follows: </li>


{% tabs %}
{% highlight xaml %}

	<syncfusion:SfDataGrid x:Name="dataGrid"
							AddNewRowPosition="Top"
							AllowFiltering="True"
							ItemsSource="{Binding OrdersDetails}"
							NavigationMode="Cell"
							ShowGroupDropArea="True"
							HideEmptyGridViewDefinition="True"
							ShowRowHeader="True" />
							
							
{% endhighlight %}
{% endtabs %}

<li> Merge the SfDataGrid.xaml in the application resources using MergedDictionaries.</li>

{% tabs %}
{% highlight xaml %}

	<Application.Resources>
		<ResourceDictionary>
			<ResourceDictionary.MergedDictionaries>
				<ResourceDictionary Source="..\VisualStudioDemos\CS\SfDataGrid.xaml"/>
			</ResourceDictionary.MergedDictionaries>
		</ResourceDictionary>
	</Application.Resources>

{% endhighlight %}
{% endtabs %}

<li> Run the sample and the following output will be obtained: </li>

     ![](Styles-and-Templates_images/Styles-and-Templates_img36.png)

</ul>

### Importing and exporting the custom theme in ThemeStudio

#### Import the custom theme

To import the custom theme in ThemeStudio, click Import button for choosing *.wpft file containing customized skin color values. After importing custom theme, the loaded custom skin color applied to the controls can be visualized. Refer to the following link to [import the custom theme](https://help.syncfusion.com/wpf/themes/theme-studio#importing-custom-theme-to-theme-studio).

#### Export the custom theme

To export the custom theme in ThemeStudio, click Export button to display a popup that contains option to select the controls to be exported. Refer to the following link to [export the custom theme](https://help.syncfusion.com/wpf/themes/theme-studio#exporting-custom-theme-from-theme-studio).