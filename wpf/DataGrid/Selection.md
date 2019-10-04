---
layout: post
title: Selection in WPF DataGrid | Syncfusion
description: How to select the rows or cells in DataGrid
platform: wpf
control: SfDataGrid
documentation: ug
---

# Selection

SfDataGrid allows you to select one or more rows or cells. For selecting specific row or group of rows you have to set [SelectionUnit](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionUnit.html) as [Row](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionUnit.html) and for selecting a specific cell or group of cells you have to set  `SelectionUnit` as [Cell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionUnit.html) or [Any](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionUnit.html). In [SelectionUnit.Any](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionUnit.html) option you can select the row by clicking on row header.

### Current Cell Navigation

Keyboard navigation through the cells and rows is determined based on the [NavigationMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~NavigationMode.html) property. [NavigationMode.Cell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.NavigationMode.html) allows you to navigate between the cells in a row as well as between rows. [NavigationMode.Row](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.NavigationMode.html) allows you to navigate only between rows. It is not possible to set `NavigationMode.Row` when cell selection is enabled (`SelectionUnit` is Cell or Any). 

### Selection Modes

The `SelectionUnit` and [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) properties together define the behavior of selection in SfDataGrid. If the `SelectionMode` is [Single](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html), you can able to select single row or cell, and if the SelectionMode is `Extended` or `Multiple`, you can able to select multiple rows or cell, and if you want to disable the selection you need to set SelectionMode as `None`,

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfDataGrid x:Name=”dataGrid”
                       SelectionUnit="Row"
                       NavigationMode="Cell"
                       SelectionMode="Single"
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% endtabs %}

![Single mode row selection in WPF DataGrid](Selection_images/Selection_img1.png)


### Disable selection for rows and columns

You can disable selection and navigation on particular column by setting [GridColumn.AllowFocus](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~AllowFocus.html) property. You can disable selection on particular row or cell or column by handling [CurrentCellActivating](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellActivating_EV.html)  event. 

N> It is not possible to select header rows, table summary rows, unbound rows which are above the table summary row when it’s placed in top and the unbound rows which are below table summary rows when it’s placed in bottom of SfDataGrid. 

## Multiple Row or Cell Selection

The SfDataGrid allows you to select multiple rows or cells by setting [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) property as [Extended](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) or [Multiple](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html),  where you can select multiple rows or cells by dragging the mouse on SfDataGrid and also using the key modifiers.

While using `Extended`, you can select multiple rows or cells by pressing the key modifiers <kbd>Ctrl</kbd> and <kbd>Shift</kbd>. 

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       SelectionUnit="Cell"
                       NavigationMode="Cell"
                       SelectionMode="Extended"
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% endtabs %}

![Extended mode cell selection in WPF DataGrid](Selection_images/Selection_img2.png)


N> When the [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) as [Multiple](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html), you can select or deselect multiple rows and cells by clicking the respective cell or row.  Also in multiple selection pressing navigation keys will move only the current cell and you can select or deselect by pressing <kbd>space</kbd> key.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       SelectionUnit="Cell"
                       NavigationMode="Cell"
                       SelectionMode="Multiple"
                       ItemsSource="{Binding Orders}">
{% endhighlight %}
{% endtabs %}

![Multiple mode cell selection in WPF DataGrid](Selection_images/Selection_img3.png)

## CheckBox column selection

`SfDataGrid` allows you to select/deselect rows via `CheckBox` using [GridCheckBoxSelectorColumn](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCheckBoxSelectorColumn.html). Please refer [this](https://help.syncfusion.com/wpf/datagrid/column-types#gridcheckboxselectorcolumn) section. 

## Get Selected Rows and Cells

The [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItem.html) property returns the data object of the selected row and the [SelectedIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedIndex.html) property returns the index of the `SelectedItem` in SfDataGrid. `SelectedItem` denotes the first selected row in multiple selection. 

The [CurrentItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentItem.html) returns the data object that currently has the focus and the [CurrentColumn](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentColumn.html) denotes the [GridColumn](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn.html) that currently has the focus. The [CurrentCellInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellInfo.html) returns an instance [GridCellInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCellInfo.html) which contains the information about the cell that currently has the focus. 

### Row Selection

You can gets all the selected records through [SelectedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItems.html) property and you can also get all selected rows information through [SfDataGrid.SelectionController.SelectedRows](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.IGridSelectionController~SelectedRows.html) which is the collection of [GridRowInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridRowInfo.html). 

### Cell Selection

You can get all selected cells information through [SfDataGrid.SelectionController.SelectedCells](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.IGridSelectionController~SelectedCells.html) property which is the collection of [GridSelectedCellsInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectedCellsInfo.html).

You can get the selected cells as [GridCellInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCellInfo.html) collection by using [GetSelectedCells](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GetSelectedCells.html) method.

{% tabs %}
{% highlight c# %}

List<GridCellInfo> selectedCells = this.dataGrid.GetSelectedCells();

{% endhighlight %}
{% endtabs %}

### CurrentItem vs SelectedItem

Both [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItem.html) and [CurrentItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentItem.html) returns the same data object when there is single cell or row is selected in SfDataGrid. When you have selected more than one rows or cells, the record that had been selected initially is maintained in `SelectedItem` and the record that currently have focus is maintained in `CurrentItem`. 

## Programmatic selection

### Process selection using properties

You can select a single row or cell by setting [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItem.html) property or [SelectedIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedIndex.html) property. 

{% tabs %}
{% highlight c# %}

var recordIndex = this.dataGrid.ResolveToRecordIndex(5);
this.dataGrid.SelectedIndex = recordIndex;

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}

var record = this.dataGrid.GetRecordAtRowIndex(6);
this.dataGrid.SelectedItem = record;

{% endhighlight %}
{% endtabs %}

In Row selection, you can select multiple rows by adding data objects to [SelectedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItems.html) property.

{% tabs %}
{% highlight c# %}

var viewModel = this.dataGrid.DataContext as ViewModel;

foreach(var order in viewModel.Orders)
{

    if (order.Country == "Mexico")
    this.dataGrid.SelectedItems.Add(order);
}

{% endhighlight %}
{% endtabs %}

![Programmatic selection of records using SelectedItems property in WPF DataGrid](Selection_images/Selection_img4.png)


### Process selection using methods

You can select range of rows through [SelectRows](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectRows.html) method in row selection.

{% tabs %}
{% highlight c# %}

this.dataGrid.SelectRows(3, 7);

{% endhighlight %}
{% endtabs %}

![Programmatic selection of records using SelectRows method in WPF DataGrid](Selection_images/Selection_img5.png)


You can select a specific cell by using the [SelectCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectCell.html) method in cell selection.

{% tabs %}
{% highlight c# %}

var record = this.dataGrid.GetRecordAtRowIndex(3);
var column = this.dataGrid.Columns[1];
this.dataGrid.SelectCell(record, column);

{% endhighlight %}
{% endtabs %}

![Programmatic selection of cell using SelectCell method in WPF DataGrid](Selection_images/Selection_img6.png)


You can select a range of cells through [SelectCells](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectCells.html) method in cell selection.

{% tabs %}
{% highlight c# %}

public MainWindow()
{
    InitializeComponent();
    this.dataGrid.Loaded += dataGrid_Loaded;
    this.dataGrid.SelectionController = new GridSelectionControllerExt(this.dataGrid);
}

private void dataGrid_Loaded(object sender, RoutedEventArgs e)
{
    var firstRecord = this.dataGrid.GetRecordAtRowIndex(3);
    var lastRecord = this.dataGrid.GetRecordAtRowIndex(7);
    var firstColumn = this.dataGrid.Columns[1];
    var lastColumn = this.dataGrid.Columns[3];
    this.dataGrid.SelectCells(firstRecord, firstColumn, lastRecord, lastColumn);
    (this.dataGrid.SelectionController as GridSelectionControllerExt).rowColumnIndex = new RowColumnIndex(7, 3);

    //Updates the PressedRowColumnIndex value in the GridBaseSelectionController.
    (this.dataGrid.SelectionController as GridSelectionControllerExt).UpdatePressedIndex();
}

public class GridSelectionControllerExt : GridCellSelectionController
{    

    //Overrides the GridCellSelectionController class to update the PressedRowColumnIndex.

    public GridSelectionControllerExt(SfDataGrid datagrid)
        : base(datagrid)
    {
    }

    private RowColumnIndex rowColumnIndex;

    public RowColumnIndex RowColumnIndex
    {
        get { return rowColumnIndex; }
        set { rowColumnIndex = value; }
    }

    //Updates the PressedRowColumnIndex to maintain the ShiftSelection.

    public void UpdatePressedIndex()
    {
    this.isInShiftSelection = true;
    this.PressedRowColumnIndex = RowColumnIndex;
    }
}

{% endhighlight %}
{% endtabs %}

![Programmatic selection of cells using SelectCells method in WPF DataGrid](Selection_images/Selection_img7.png)


You can select all the rows or cells using [SelectAll](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectAll.html) method.

{% tabs %}
{% highlight c# %}

this.dataGrid.SelectAll();

{% endhighlight %}
{% endtabs %}

### Process Current Cell

When you set the [CurrentItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentItem.html) to particular record, the [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) will be moved to corresponding record when the [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) is [Multiple](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) or [Extended](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) and the selection will added to the particular record item when the `SelectionMode` is [Single](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html).

{% tabs %}
{% highlight c# %}

var viewModel = this.dataGrid.DataContext as ViewModel;
this.dataGrid.CurrentItem = viewModel.Orders.FirstOrDefault(order => order.Country == "Spain");

{% endhighlight %}
{% endtabs %}

You can move the [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) to a particular rowColumnIndex by using the [MoveCurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~MoveCurrentCell.html) method.

{% tabs %}
{% highlight c# %}

this.dataGrid.MoveCurrentCell(new RowColumnIndex(3,2), false);

{% endhighlight %}
{% endtabs %}

### Clear Selection

You can clear the selection by using the [ClearSelection](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ClearSelections.html) method. In Row Selection you can also remove the selection by setting null to [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItem.html) or clearing the [SelectedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItems.html) property.

{% tabs %}
{% highlight c# %}

this.dataGrid.SelectionController.ClearSelections(true);

{% endhighlight %}
{% endtabs %}

You can clear selection on group of cells by using the [UnSelectCells](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~UnSelectCells.html) method in cell selection.

{% tabs %}
{% highlight c# %}

var firstRecord = this.dataGrid.GetRecordAtRowIndex(3);
var lastRecord = this.dataGrid.GetRecordAtRowIndex(7);
var firstColumn = this.dataGrid.Columns[1];
var lastColumn = this.dataGrid.Columns[3];
this.dataGrid.UnSelectCells(firstRecord, firstColumn, lastRecord, lastColumn);

{% endhighlight %}
{% endtabs %}

You can clear the selection on particular cell by using the [UnSelectCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~UnSelectCell.html) method in cell selection.

{% tabs %}
{% highlight c# %}

var removeRecord = this.dataGrid.GetRecordAtRowIndex(5);
var removeColumn = this.dataGrid.Columns[2];
this.dataGrid.UnSelectCell(removeRecord, removeColumn);

{% endhighlight %}
{% endtabs %}

![Programmatic removal of selection for a cell using UnSelectCell method in WPF DataGrid](Selection_images/Selection_img8.png)


## Selection in Master-Details View

Master-Details View provides support to select one or more rows or cells in [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html). You can’t able to maintain the selection in both ParentDataGrid and `DetailsViewDataGrid`. Selection will be maintained either in ParentDataGrid or in `DetailsViewDataGrid`.

![Selection in Master-Details View in WPF DataGrid](Selection_images/Selection_img9.png)


### Getting SelectedDetailsViewDataGrid

You can get the currently selected [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) by using the [SelectedDetailsViewGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectedDetailsViewGrid.html) property of parent DataGrid.

{% tabs %}
{% highlight c# %}

var detailsViewDataGrid = this.dataGrid.SelectedDetailsViewGrid;

{% endhighlight %}
{% endtabs %}

For accessing nested level [SelectedDetailsViewGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectedDetailsViewGrid.html) ,

{% tabs %}
{% highlight c# %}

var detailsViewDataGrid = this.dataGrid.SelectedDetailsViewGrid.SelectedDetailsViewGrid;

{% endhighlight %}
{% endtabs %}

### Getting SelectedItem from DetailsViewDataGrid

You can get the selected record of [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) by using the [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItem.html) property.

{% tabs %}
{% highlight c# %}

var detailsViewDataGrid = this.datagrid.SelectedDetailsViewGrid;
var SelectedItem = detailsViewDataGrid.SelectedItem;

{% endhighlight %}
{% endtabs %}

You can get the `SelectedItem` while it’s changed using [SelectionChanged](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionChanged_EV.html) event of `ViewDefinition.DataGrid`. 

{% tabs %}
{% highlight xaml %}
<syncfusion:GridViewDefinition RelationalColumn="OrderDetails">
    <syncfusion:GridViewDefinition.DataGrid>
        <syncfusion:SfDataGrid x:Name="FirstDetailsViewGrid" 
                               SelectionChanged="FirstDetailsViewGrid_SelectionChanged">
        </syncfusion:SfDataGrid>
    </syncfusion:GridViewDefinition.DataGrid>
</syncfusion:GridViewDefinition>

{% endhighlight %}

{% highlight c# %}

FirstDetailsViewGrid.SelectionChanged+=FirstDetailsViewGrid_SelectionChanged;

private void FirstDetailsViewGrid_SelectionChanged(object sender, Syncfusion.UI.Xaml.Grid.GridSelectionChangedEventArgs e)
{
    var SelectedItem = (e.OriginalSender as DetailsViewDataGrid).SelectedItem;
}

{% endhighlight %}
{% endtabs %}

N> You can get the SelectedIndex and SelectedItems also in selection changed event.

You can refer [here](http://help.syncfusion.com/wpf/sfdatagrid/master-details-view#handling-events-for-detailsviewdatagrid) to wire the events for `ViewDefinition.DataGrid` based on `AutoPopulateRelations` for different levels.

### Get the CurrentItem of DetailsViewDataGrid

You can get the current record of the [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) by using the [CurrentItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentItem.html) property.

{% tabs %}
{% highlight c# %}

var detailsViewDataGrid = this.datagrid.SelectedDetailsViewGrid;
var CurrentItem = detailsViewDataGrid.CurrentItem;

{% endhighlight %}
{% endtabs %}



You can get the `CurrentItem` while it’s changed using [SelectionChanged](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionChanged_EV.html) event of `ViewDefinition.DataGrid`.

{% tabs %}
{% highlight xaml %}

<syncfusion:GridViewDefinition RelationalColumn="OrderDetails">
    <syncfusion:GridViewDefinition.DataGrid>
        <syncfusion:SfDataGrid x:Name="FirstDetailsViewGrid" 
                               SelectionChanged="FirstDetailsViewGrid_SelectionChanged">
        </syncfusion:SfDataGrid>
    </syncfusion:GridViewDefinition.DataGrid>
</syncfusion:GridViewDefinition>

{% endhighlight %}

{% highlight c# %}

FirstDetailsViewGrid.SelectionChanged+=FirstDetailsViewGrid_SelectionChanged;

private void FirstDetailsViewGrid_SelectionChanged(object sender, Syncfusion.UI.Xaml.Grid.GridSelectionChangedEventArgs e)
{
    var SelectedItem = (e.OriginalSender as DetailsViewDataGrid).CurrentItem;
}

{% endhighlight %}
{% endtabs %}

You can refer [here](http://help.syncfusion.com/wpf/sfdatagrid/master-details-view#handling-events-for-detailsviewdatagrid) to wire the events from `ViewDefinition.DataGrid` based on `AutoPopulateRelations` for different levels.

### Get CurrentCell of DetailsViewDataGrid

You can get the [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) of [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) by using the [SelectedDetailsViewGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectedDetailsViewGrid.html) property. You can use different events of `ViewDefinition.DataGrid` like [CurrentCellBeginEdit](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellBeginEdit_EV.html), [CurrentCellActivated](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellActivated_EV.html) to get the `CurrentCell`.

{% tabs %}
{% highlight c# %}

var currentCell = this.dataGrid.SelectedDetailsViewGrid.SelectionController.CurrentCellManager.CurrentCell;

{% endhighlight %}
{% endtabs %}

You can get the `CurrentCell` using `CurrentCellBeginEdit` event `ViewDefinition.DataGrid`.

{% tabs %}
{% highlight xaml %}

<syncfusion:GridViewDefinition RelationalColumn="OrderDetails">
    <syncfusion:GridViewDefinition.DataGrid>
        <syncfusion:SfDataGrid x:Name="FirstLevelNestedGrid"                                                   
                               CurrentCellBeginEdit=" FirstLevelNestedGrid_CurrentCellBeginEdit">
        </syncfusion:SfDataGrid>
    </syncfusion:GridViewDefinition.DataGrid>
</syncfusion:GridViewDefinition>

{% endhighlight %}

{% highlight c# %}

this.FirstLevelNestedGrid.CurrentCellBeginEdit += FirstLevelNestedGrid_CurrentCellBeginEdit;

void FirstLevelNestedGrid_CurrentCellBeginEdit(object sender, CurrentCellBeginEditEventArgs args)
{
    var detailsViewDataGrid = args.OriginalSender as DetailsViewDataGrid;
    var currentCell = detailsViewDataGrid.SelectionController.CurrentCellManager.CurrentCell;
}

{% endhighlight %}
{% endtabs %}

You can refer [here](http://help.syncfusion.com/wpf/sfdatagrid/master-details-view#handling-events-for-detailsviewdatagrid) to wire the events from the [ViewDefinition.DataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridViewDefinition~DataGrid.html) based on `AutoPopulateRelations` for different levels.

### Programmatic Selection in DetailsViewDataGrid

You can select data objects while loading DetailsViewDataGrid using [DetailsViewLoading](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~DetailsViewLoading_EV.html) event.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid Name="dataGrid" 
                       DetailsViewLoading="dataGrid_DetailsViewLoading" >
</syncfusion:SfDataGrid>

{% endhighlight %}

{% highlight c# %}

this.dataGrid.DetailsViewLoading += dataGrid_DetailsViewLoading;

void dataGrid_DetailsViewLoading(object sender, DetailsViewLoadingAndUnloadingEventArgs e)
{
    var record = e.DetailsViewDataGrid.GetRecordAtRowIndex(e.DetailsViewDataGrid.GetFirstDataRowIndex());
    e.DetailsViewDataGrid.SelectedItem = record;
}

{% endhighlight %}
{% endtabs %}

### Getting the parent of DetailsViewDataGrid

You can get the immediate parent of `DetailsViewDataGrid` through [GetParentDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.Helpers.SelectionHelper~GetParentDataGrid.html) helper method.

{% tabs %}
{% highlight c# %}

using Syncfusion.UI.Xaml.Grid.Helpers;
var parentDataGrid = this.dataGrid.SelectedDetailsViewGrid.GetParentDataGrid();

{% endhighlight %}
{% endtabs %}

You can get the top level DataGrid for the `DetailsViewDataGrid` through the [GetTopLevelParentDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.Helpers.SelectionHelper~GetTopLevelParentDataGrid.html) helper method.

{% tabs %}
{% highlight c# %}

using Syncfusion.UI.Xaml.Grid.Helpers;
var dataGrid = this.detailsViewDataGrid.GetTopLevelParentDataGrid();

{% endhighlight %}
{% endtabs %}

### Getting the DetailsViewDataGrid based on index

You can get the [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) based on row index through [GetDetailsViewGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.Helpers.SelectionHelper~GetDetailsViewGrid.html) helper method.

{% tabs %}
{% highlight c# %}

var detailsViewDataGrid = this.dataGrid.GetDetailsViewGrid(2);

{% endhighlight %}
{% endtabs %}

You can also get the `DetailsViewDataGrid` based on the record index and relational column name using `GetDetailsViewGrid` method.

{% tabs %}
{% highlight c# %}

var detailsViewDataGrid = this.dataGrid.GetDetailsViewGrid(0, "ProductDetails");

{% endhighlight %}
{% endtabs %}

### Programmatically expanding and scrolling DetailsViewDataGrid 

You can expand the `DetailsViewDataGrid` programmatically by calling `ExpandDetailsViewAt` method by passing the record index.

{% tabs %}
{% highlight c# %}

int parentRowIndex = 2;
var recordIndex = this.dataGrid.ResolveToRecordIndex(parentRowIndex);
var record = this.dataGrid.View.Records[recordIndex];

if (!record.IsExpanded)
    this.dataGrid.ExpandDetailsViewAt(recordIndex);

{% endhighlight %}
{% endtabs %}

If the expanded `DetailsViewDataGrid` is not in view, then you can scroll using [DetailsViewManager.BringIntoView](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewManager~BringIntoView.html) method.

{% tabs %}
{% highlight c# %}

int recordIndex = 20;
int index = 0;
int parentRowIndex = 25;
datagrid.ExpandDetailsViewAt(recordIndex);

foreach (var def in this.dataGrid.DetailsViewDefinition)
{

    if (def.RelationalColumn == "ProductDetails")
    {
        index = this.dataGrid.DetailsViewDefinition.IndexOf(def);
        index = parentRowIndex + index + 1;
    }
}

//Get the Details view based upon the recordIndex and Column name
SfDataGrid detailsViewDataGrid = datagrid.GetDetailsViewGrid(recordIndex, "OrderDetails");

//Get the DetailsViewManager using Reflection
var propertyInfo = dataGrid.GetType().GetField("DetailsViewManager", System.Reflection.BindingFlags.Instance | System.Reflection.BindingFlags.NonPublic);
DetailsViewManager detailsViewManager = propertyInfo.GetValue(dataGrid) as DetailsViewManager;

if (detailsViewDataGrid == null)
{
    detailsViewManager.BringIntoView(index);
    detailsViewDataGrid = this.dataGrid.GetDetailsViewGrid(this.dataGrid.ResolveToRecordIndex(recordIndex), " OrderDetails ");
}

{% endhighlight %}
{% endtabs %}

![Programmatic expansion and scrolling of Master-Details View in WPF DataGrid](Selection_images/Selection_img10.png)


You can get the sample from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/MasterDetailsViewSample1099992369.zip).

### Programmatically select the records in DetailsViewDataGrid which is not in view

#### Scrolling to the DetailsViewDataGrid

You can expand the [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) by using `ExpandDetailsViewAt` helper method. If the `DetailsViewDataGrid` is already expanded, you can use [ScrollInView](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ScrollInView.html) method to bring it into view. You can also use [DetailsViewManager.BringIntoView](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewManager~BringIntoView.html) method to get the `DetailsViewDataGrid` into view.

{% tabs %}
{% highlight c# %}

//Find DetailsViewDataRow index based on relational column
int index = 0;
int parentRowIndex = 25;

foreach (var def in this.dataGrid.DetailsViewDefinition)
{

    if (def.RelationalColumn == "ProductDetails")
    {
        index = this.dataGrid.DetailsViewDefinition.IndexOf(def);
        index = parentRowIndex + index + 1;
    }
}

//Get the DetailsViewManager using Reflection
var propertyInfo = dataGrid.GetType().GetField("DetailsViewManager", System.Reflection.BindingFlags.Instance | System.Reflection.BindingFlags.NonPublic);
DetailsViewManager detailsViewManager = propertyInfo.GetValue(dataGrid) as DetailsViewManager;
var rowColumnIndex = new RowColumnIndex(index, 1);

//Get the DetailsViewDataGrid by passing the corresponding row index and relation name
var detailsViewDataGrid = this.dataGrid.GetDetailsViewGrid(this.dataGrid.ResolveToRecordIndex(parentRowIndex), "ProductDetails");

//If the DetailsViewDataGrid is not in view, then you can call the BringIntoView method.

if (detailsViewDataGrid == null)
{
    detailsViewManager.BringIntoView(index);
    detailsViewDataGrid = this.dataGrid.GetDetailsViewGrid(this.dataGrid.ResolveToRecordIndex(parentRowIndex), "ProductDetails");    
}

else
{
    //If the DetailsViewDataGrid is already expanded, bring that into view
    dataGrid.ScrollInView(rowColumnIndex);
}

{% endhighlight %}
{% endtabs %}
                
#### Select the record in the DetailsViewDataGrid

You can select the record of the `DetailsViewDataGrid` programmatically at run time by setting the corresponding child grid record index to the [SfDataGrid.SelectedIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedIndex.html) property.

{% tabs %}
{% highlight c# %}

detailsViewDataGrid.SelectedIndex = childIndex;

{% endhighlight %}
{% endtabs %}

You can get the sample from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/SelectDetailsviewRecord1830272123.zip).

### Customizing the SelectionController for DetailsViewDataGrid

The [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) process the selection operations in selection controller. Below are the built-in selection controllers,

[GridSelectionController](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionController.html) – Process selection operations when selection unit as row.

[GridCellSelectionController](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCellSelectionController.html) – Process selection operations when selection unit as cell or Any.

You can customize the default row selection behavior by overriding `GridSelectionController` class and set it to `DetailsViewDataGrid.SelectionController`.

The below code-snippet explains you about the customization of `GridSelectionController` class.

{% tabs %}
{% highlight c# %}

this.dataGrid.DetailsViewLoading += dataGrid_DetailsViewLoading;

void dataGrid_DetailsViewLoading(object sender, DetailsViewLoadingAndUnloadingEventArgs e)
{

    if (!(e.DetailsViewDataGrid.SelectionController is GridSelectionControllerExt))
    e.DetailsViewDataGrid.SelectionController = new GridSelectionControllerExt (e.DetailsViewDataGrid);
}
public class GridSelectionControllerExt : GridSelectionController
{      
    public GridSelectionControllerExt(SfDataGrid datagrid)
        : base(datagrid)
    {             
    }
}

{% endhighlight %}
{% endtabs %}

## Scrolling Rows or Columns

### Automatic scrolling on Drag Selection

SfDataGrid will scrolls rows and columns automatically when you try to perform the drag selection like in excel. You can enable or disable AutoScrolling by setting the [AutoScroller.AutoScrolling](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.AutoScroller~AutoScrolling.html) property.

{% tabs %}
{% highlight c# %}

this.dataGrid.AutoScroller.AutoScrolling = AutoScrollOrientation.Both;

{% endhighlight %}
{% endtabs %}

### Scroll to particular RowColumnIndex

You can scroll programmatically to particular cell using [ScrollInView](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ScrollInView.html) method by passing row and column index. 

{% tabs %}
{% highlight c# %}

int rowIndex = this.dataGrid.GetLastDataRowIndex();
int columnIndex = this.dataGrid.GetLastColumnIndex();
this.dataGrid.ScrollInView(new RowColumnIndex(rowIndex, columnIndex));

{% endhighlight %}
{% endtabs %}

### Scroll to SelectedItem

You can scroll programmatically to the `SelectedItem` using the `ScrollInView` method.

{% tabs %}
{% highlight c# %}

using Syncfusion.UI.Xaml.Grid.Helpers;
var rowIndex = this.datagrid.ResolveToRowIndex(this.datagrid.SelectedItem);
var columnIndex = this.datagrid.ResolveToStartColumnIndex();
this.datagrid.ScrollInView(new RowColumnIndex(rowIndex, columnIndex));

{% endhighlight %}
{% endtabs %}

## Mouse and Keyboard Behaviors

### Keyboard Behavior

<table>
<tr>
<th>
Key or KeyCombinations
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
<kbd>DownArrow</kbd>
</td>
<td>
Moves CurrentCell directly below the active current cell. If the CurrentCell is in last row, pressing Down arrow does nothing.
</td>
</tr>
<tr>
<td>
<kbd>UpArrow</kbd>
</td>
<td>
Moves the CurrentCell directly above the active current cell. If the CurrentCell is in first row, pressing Up arrow does nothing.
</td>
</tr>
<tr>
<td>
<kbd>LeftArrow</kbd>
</td>
<td>
Moves the current cell to previous to the active current cell. If the CurrentCell is in first cell, pressing Left arrow does nothing. If the focused row is group header, the group will be collapsed when it is in expanded state.
</td>
</tr>
<tr>
<td>
<kbd>RightArrow</kbd>
</td>
<td>
Moves the current cell to next to the active current cell. If the CurrentCell is in last cell, pressing Right arrow does nothing. If the focused row is group header, the group will expanded when it is in collapsed state.
</td>
</tr>
<tr>
<td>
<kbd>Home</kbd> / <kbd> Ctrl</kbd> + <kbd>LeftArrow</kbd>
</td>
<td>
Moves the current cell to the first cell of the current row.
</td>
</tr>
<tr>
<td>
<kbd>End</kbd> / <kbd>Ctrl</kbd> + <kbd>RightArrow</kbd>
</td>
<td>
Moves the current cell to the last cell of the current row.
</td>
</tr>
<tr>
<td>
<kbd>PageDown</kbd>
</td>
<td>
The SfDataGrid will be scrolled to next set of rows that are not displayed in view, including the row that are partially displayed and the current cell is set to last row.
</td>
</tr>
<tr>
<td>
<kbd>PageUp</kbd>
</td>
<td>
The SfDataGrid will be scrolled to previous set of rows that are not displayed in view, including the row that are partially displayed and the current cell is set to the first row.
</td>
</tr>
<tr>
<td>
<kbd>Tab</kbd>
</td>
<td>
Moves the current cell to next to the active current cell. If the active current cell is the last cell of the current row, the focus will moved to first cell of the row next to the current row.If the active current cell is the last cell of the last row, the focus will be moved to next control in the tab order of the parent container.
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Tab</kbd>
</td>
<td>
Moves the current cell to previous to the active current cell. If the active current cell is the first cell of the current row, the current cell will moved to last cell of the row previous to the current row.If the active current cell is the first cell of the first row, the focus will be moved to previous control in the tab order of the parent container.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>DownArrow</kbd>
</td>
<td>
Moves the current cell to the current column of the last row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>UpArrow</kbd>
</td>
<td>
Moves the current cell to the current column of the first row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>Home</kbd>
</td>
<td>
Moves the current cell to the first cell of the first row.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>End</kbd>
</td>
<td>
Moves the current cell to the last cell of the last row.
</td>
</tr>
<tr>
<td>
<kbd>Enter</kbd>
</td>
<td>
If the active current cell is in edit mode, the changes will committed and moves the current cell to below the active current cell. If the active current cell is in last row, commits changes only and retains in the same cell.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>Enter</kbd>
</td>
<td>
Commits only the changes when the current cell in edit mode and retains the focus in same cell.
</td>
</tr>
<tr>
<td>
<kbd>F2</kbd>
</td>
<td>
If the {{'[DataGrid.AllowEditing](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~AllowEditing.html)'| markdownify }} property is true and the {{'[GridColumn.AllowEditing](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~AllowEditing.html)'| markdownify }} property is true for the current column, the current cell enters into edit mode.
</td>
</tr>
<tr>
<td>
<kbd>Esc</kbd>
</td>
<td>
If the current cell is in edit mode, reverts the changes that had been done in the current cell. If the underlying source implements the {{'[IEditableObject](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject#"")'| markdownify }}, on pressing of Esc key for the second time will cancel the edit mode for entire row.
</td>
</tr>
<tr>
<td>
<kbd>Delete</kbd>
</td>
<td>
If the current cell is not in edit mode, the current row will be deleted.
</td>
</tr>
<tr>
<td>
<kbd>Ctrl</kbd> + <kbd>A</kbd>
</td>
<td>
All rows or cells will be selected.
</td>
</tr>
</table>
N> When the [NavigationMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~NavigationMode.html) is in [Row](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.NavigationMode.html), the Right Arrow and Left Arrow only work for grouping headers and the following keys <kbd>Tab</kbd>, <kbd>Shift</kbd> + <kbd>Tab</kbd>, <kbd>Delete</kbd>, <kbd>Home</kbd>, <kbd>End</kbd> will not work. 

### Shift Key Combinations

When the [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) is set to [Extended](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html), you can select multiple rows or cells using the navigation keys along with the <kbd>Shift</kbd> key. Before navigation starts, the current cell will be marked as a pressed cell and the selection will be done in all rows or cells between the pressed cell and current cell. 

<table>
<tr>
<th>
Key Combinations
</th>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>DownArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>UpArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>RightArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>LeftArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Home</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> +<kbd> End</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>PageDown</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>PageUp</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>DownArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd> Ctrl</kbd> + <kbd>UpArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>RightArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>LeftArrow</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>Home</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>End</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>PageDown</kbd>
</td>
</tr>
<tr>
<td>
<kbd>Shift</kbd> + <kbd>Ctrl</kbd> + <kbd>PageUp</kbd>
</td>
</tr>
</table>

### Mouse Behavior

You can enable/disable the selection when the mouse button is in pressed state by setting the AllowSelectionOnPointerPressed property.

When the [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) is set to [Extended](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html), you can select multiple rows or cells by clicking on any cell along with <kbd>ctrl</kbd> and <kbd>Shift</kbd> key. When you click a cell along with <kbd>Ctrl</kbd> key, you can select or deselect the particular row or cell. When you click a cell along with <kbd>Shift</kbd> key, you can select the range rows or cells from the pressed cell to the current cell.

### Customizing mouse and keyboard behaviors

You can customize mouse and keyboard behaviors by overriding the selection controller. You can refer the section `Customizing Selection Behaviors` to override the selection controller.

## Events Processed on Selection

### CurrentCellActivating Event

The [CurrentCellActivating](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellActivating_EV.html) event will occurs before moving the current cell to particular cell. [CurrentCellActivatingEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatingEventArgs.html) has following members which provides information for `CurrentCellActivatingEvent`.

[ActivationTrigger](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatingEventArgs~ActivationTrigger.html) – Returns the reason for moving the current cell.

[CurrentRowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatingEventArgs~CurrentRowColumnIndex.html) – [RowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.ScrollAxis.RowColumnIndex.html) of the cell where the current cell need to move.

[PreviousRowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatingEventArgs~PreviousRowColumnIndex.html) – `RowColumnIndex` of the cell from where the current cell was move.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       CurrentCellActivating="dataGrid_CurrentCellActivating"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}

{% highlight c# %}

this.dataGrid.CurrentCellActivating += dataGrid_CurrentCellActivating;

void dataGrid_CurrentCellActivating(object sender, CurrentCellActivatingEventArgs args)
{
}

{% endhighlight %}
{% endtabs %}

You can cancel the current cell moving process within this event by setting [GridCurrentCellActivatingEventArgs.Cancel](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatingEventArgs_members.html) as true.

{% tabs %}
{% highlight c# %}

void dataGrid_CurrentCellActivating(object sender, CurrentCellActivatingEventArgs args)
{
    var provider = this.dataGrid.View.GetPropertyAccessProvider();
    var record = this.dataGrid.GetRecordAtRowIndex(args.CurrentRowColumnIndex.RowIndex);

    if (record == null)
        return;
        
    var column = this.dataGrid.Columns[this.dataGrid.ResolveToGridVisibleColumnIndex(args.CurrentRowColumnIndex.ColumnIndex)];
    var cellValue = provider.GetValue(record, column.MappingName);

    if (cellValue.ToString() == "1001")
        args.Cancel = true;
}

{% endhighlight %}
{% endtabs %}

### CurrentCellActivated Event

The [CurrentCellActivated](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellActivated_EV.html) event will occur once the current cell is moved to corresponding cell. [CurrentCellActivatedEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatedEventArgs.html) has following members which provides information for `CurrentCellActivated` event.

[ActivationTrigger](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatedEventArgs~ActivationTrigger.html) – Returns the reason of the current cell movement.

[CurrentRowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatedEventArgs~CurrentRowColumnIndex.html) – `RowColumnIndex` of the cell where the current cell was moved.

[PreviousRowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellActivatedEventArgs~PreviousRowColumnIndex.html) – `RowColumnIndex` of the cell from where the current cell has been moved.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       CurrentCellActivated="dataGrid_CurrentCellActivated"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}

{% highlight c# %}

this.dataGrid.CurrentCellActivated += dataGrid_CurrentCellActivated;

void dataGrid_CurrentCellActivated(object sender, CurrentCellActivatedEventArgs args)
{
}

{% endhighlight %}
{% endtabs %}

### SelectionChanging Event

[SelectionChanging](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionChanging_EV.html) event occurs before processing the selection to particular row or cell. This event will be triggered only to the keyboard and mouse interactions. [GridSelectionChangingEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionChangingEventArgs.html) has the following members which provides the information for `SelectionChanging` event.  

[AddedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionChangingEventArgs~AddedItems.html) – Collection of [GridRowInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridRowInfo.html) or [GridCellInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCellInfo.html) where the selection going to process.

[RemovedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionChangingEventArgs~RemovedItems.html) – Collection of `GridRowInfo` or `GridCellInfo` where the selection going to remove.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       SelectionChanging="dataGrid_SelectionChanging"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}

{% highlight c# %}

this.dataGrid.SelectionChanging += dataGrid_SelectionChanging;

void dataGrid_SelectionChanging(object sender, GridSelectionChangingEventArgs e)
{
}

{% endhighlight %}
{% endtabs %}

You can cancel the selection process within this event by setting [GridSelectionChangingEventArgs.Cancel](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionChanging_EV.html) property as true.

{% tabs %}
{% highlight c# %}

private void Datagrid_SelectionChanging(object sender, GridSelectionChangingEventArgs e)
{
    var unBoundRow = e.AddedItems.Where(rowInfo => (rowInfo as GridRowInfo).IsUnBoundRow).ToList();
  
    if (unBoundRow.Count() > 0)
        e.Cancel = true;
}

{% endhighlight %}
{% endtabs %}

### SelectionChanged Event

The [SelectionChanged](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionChanged_EV.html) event will occurs once the selection process has been completed for particular row or cell in SfDataGrid. [GridSelectionChangedEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionChangedEventArgs.html) has following members which provides information for `SelectionChanged` event.

[AddedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionChangedEventArgs~AddedItems.html) – Collection of [GridRowInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridRowInfo.html) or [GridCellInfo](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCellInfo.html) where the selection has been processed.

[RemovedItems](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionChangedEventArgs~RemovedItems.html) – Collection of `GridRowInfo` or `GridCellInfo` from where the selection has been removed.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       SelectionChanged="dataGrid_SelectionChanged"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}

{% highlight c# %}

this.dataGrid.SelectionChanged += dataGrid_SelectionChanged;

void dataGrid_SelectionChanged(object sender, GridSelectionChangedEventArgs e)
{
}

{% endhighlight %}
{% endtabs %}

## Appearance

### Changing Selection Background and Foreground

You can change the selection background and foreground using [RowSelectionBrush](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowSelectionBrush.html), [GroupRowSelectionBrush](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupRowSelectionBrush.html) and [SelectionForeGroundBrush](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionForegroundBrush.html) properties. The `RowSelectionBrush` is only applied to the rows other than summary rows and the [GroupRowSelectionRows](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupRowSelectionBrush.html) is applied for caption summary and group summary rows.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AllowGrouping="True"
                       ShowGroupDropArea="True"
                       RowSelectionBrush="#FFDFF3F4"
                       GroupRowSelectionBrush="#FFC8E3E3"
                       SelectionForegroundBrush="DarkBlue"
                       SelectionMode="Extended"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}
{% endtabs %}

![Appearance customization of rows in WPF DataGrid](Selection_images/Selection_img11.png)


### Changing Current Cell Border Style

You can change the current cell border thickness and border color using [CurrentCellBorderThickness](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~CurrentCellBorderThickness.html) and [CurrentCellBorderBrush](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~CurrentCellBorderBrush.html) property.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       CurrentCellBorderBrush="Red"
                       CurrentCellBorderThickness="1.6"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}
{% endtabs %}

![Appearance customization of current cell in WPF DataGrid](Selection_images/Selection_img12.png)


### Customizing Row Selection Border

You can customize the row selection by editing the control template of corresponding row controls.

Data Row / Add New Row – [VirtualizingCellsControl](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.VirtualizingCellsControl.html)

CaptionSummary Row – [CaptionSummaryRowControl](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CaptionSummaryRowControl.html)

GroupSummary Row – [GroupSummaryRowControl](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupSummaryRowControl.html)

UnBound Row – [UnBoundRowControl](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.UnBoundRowControl.html) 

Filter Row - FilterRowControl

{% tabs %}
{% highlight xaml %}

<Style TargetType="{x:Type syncfusion:VirtualizingCellsControl}">
    <Setter Property="Background" Value="Transparent" />
    <Setter Property="BorderBrush" Value="Gray" />
    <Setter Property="BorderThickness" Value="0" />
    <Setter Property="IsTabStop" Value="False" />
    <Setter Property="FocusVisualStyle" Value="{x:Null}" />
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type syncfusion:VirtualizingCellsControl}">
                <Grid>
                    <Border x:Name="PART_RowBorder"
                            BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}"/>
                    <Rectangle x:Name="PART_CurrentFocusRow"
                               Margin="{TemplateBinding CurrentFocusBorderMargin}"
                               Stroke="DarkGray"
                               StrokeDashArray="2,2"
                               StrokeThickness="1"
                               Visibility="{TemplateBinding CurrentFocusRowVisibility}" />
                    <Border Background="{TemplateBinding RowHoverBackgroundBrush}"
                            BorderBrush="{TemplateBinding RowHoverBackgroundBrush}"
                            BorderThickness="{TemplateBinding RowHighlightBorderThickness}"
                            Clip="{TemplateBinding HighlightBorderClipRect}"
                            SnapsToDevicePixels="True"
                            Visibility="{TemplateBinding HighlightSelectionBorderVisiblity}" />
                    <Rectangle Clip="{TemplateBinding RowBackgroundClip}" 
                               Fill="{TemplateBinding Background}" />
                    <!-- Adding new border to show border for whole selected row -->
                    <Border x:Name="PART_SelectionBorder"
                            BorderBrush="Red"
                            BorderThickness="1.5,1.5,1.5,2.5"
                            Opacity="0.75"
                            Background="{TemplateBinding RowSelectionBrush}"
                            Clip="{TemplateBinding SelectionBorderClipRect}"
                            Visibility="{TemplateBinding SelectionBorderVisiblity}" />
                    <Border BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}">
                        <ContentPresenter />
                    </Border>
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

{% endhighlight %}
{% endtabs %}

![Customization of row selection border in WPF DataGrid](Selection_images/Selection_img13.png)


### Customizing Cell Selection

You can customize the cell selection by editing the control template of the corresponding cell control.

DataRow / AddNewRow – [GridCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCell.html)

UnBound Row – [GridUnBoundRowCell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridUnBoundRowCell.html)

Filter Row - GridFilterRowCell

{% tabs %}
{% highlight xaml %}

<Style TargetType="{x:Type syncfusion:GridCell}">
    <Setter Property="Background" Value="Transparent" />
    <Setter Property="BorderBrush" Value="Gray" />
    <Setter Property="BorderThickness" Value="0,0,1,1" />
    <Setter Property="Padding" Value="0,0,0,0" />
    <Setter Property="FocusVisualStyle" Value="{x:Null}" />
    <Setter Property="IsTabStop" Value="False" />
    <Setter Property="VerticalContentAlignment" Value="Center"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type syncfusion:GridCell}">
                <Grid SnapsToDevicePixels="True">
                    <Border Background="{TemplateBinding CellSelectionBrush}"
                            SnapsToDevicePixels="True"
                            Visibility="{TemplateBinding SelectionBorderVisibility}" />
                    <Border x:Name="PART_GridCellBorder"
                            Background="{TemplateBinding Background}"
                            BorderBrush="{TemplateBinding BorderBrush}"
                            BorderThickness="{TemplateBinding BorderThickness}"
                            SnapsToDevicePixels="True">
                        <Grid>
                            <ContentPresenter Margin="{TemplateBinding Padding}" />
                        </Grid>
                    </Border>
                    <Border Background="Transparent"
                            BorderBrush="Red"
                            BorderThickness="0.5"
                            IsHitTestVisible="False"
                            SnapsToDevicePixels="True"
                            Margin="0,0,1,1"
                            Visibility="{TemplateBinding CurrentCellBorderVisibility}" />
                    <!—Adding new border to show inner border to the CurrentCellBorder -->
                    <Border Background="Transparent"
                            BorderBrush="Red"
                            BorderThickness="0.5"
                            IsHitTestVisible="False"
                            SnapsToDevicePixels="True"
                            Margin="2,2,3,3"
                            Visibility="{TemplateBinding CurrentCellBorderVisibility}" />
                    <Border x:Name="PART_InValidCellBorder"
                            Width="10"
                            Height="10"
                            HorizontalAlignment="Right"
                            Visibility="Collapsed"
                            VerticalAlignment="Top"
                            SnapsToDevicePixels="True">
                        <ToolTipService.ToolTip>
                            <ToolTip Background="#FFDB000C"
                                     Placement="Right"
                                     PlacementRectangle="20,0,0,0"
                                     Tag="{TemplateBinding ErrorMessage}"
                                     Template="{StaticResource ValidationToolTipTemplate}" />
                            </ToolTipService.ToolTip>
                        <Path Data="M0.5,0.5 L12.652698,0.5 12.652698,12.068006 z"
                              Fill="Red"
                              SnapsToDevicePixels="True"
                              Stretch="Fill" />
                    </Border>
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>

{% endhighlight %}
{% endtabs %}

![Custom cell selection for WPF SfDataGrid](Selection_images/Selection_img14.png)


## Binding Selection Properties

You can bind the selection properties like [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedItem.html), [SelectedIndex](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectedIndex.html) and [CurrentItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentItem.html) to the properties in ViewModel directly. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       SelectedItem="{Binding DataGridSelectedItem, Mode=TwoWay}"
                       CurrentItem="{Binding DataGridCurrentItem,Mode=TwoWay}"
                       SelectedIndex="{Binding DataGridSelectedIndex,Mode=TwoWay}"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}
{% endtabs %}

In DetailsView, it is not possible to bind selection properties directly with ViewModel. You can use [Behavior](https://msdn.microsoft.com/en-in/library/system.windows.interactivity.behavior) to achieve this requirement. 

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}">
    <interactivity:Interaction.Behaviors>
    <!-- Binding code behind properties to SelectionBehavior dependency properties -->
        <local:SelectionBehavior AttachedDetailsViewSelectedItem="{Binding DetailsViewSelectedItem, Mode=TwoWay}" 
                                  AttachedDetailsViewSelectedIndex="{Binding DetailsViewSelectedIndex,Mode=TwoWay}"
                                  AttachedDetailsViewCurrentItem="{Binding DetailsViewCurrentItem, Mode=TwoWay}" 
    </interactivity:Interaction.Behaviors>
    <syncfusion:GridViewDefinition RelationalColumn="OrdersDetailsFirstNested">
        <syncfusion:GridViewDefinition.DataGrid>
            <syncfusion:SfDataGrid x:Name="FirstDetailsViewGrid"
                                   AutoGenerateColumns="True"/>
        </syncfusion:GridViewDefinition.DataGrid>
    </syncfusion:GridViewDefinition>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}

public class SelectionBehavior : Behavior<SfDataGrid>
{
 
    public object AttachedDetailsViewSelectedItem
    {
        get { return (object)GetValue(AttachedDetailsViewSelectedItemProperty); }
        set { SetValue(AttachedDetailsViewSelectedItemProperty, value); }
    }

    public static readonly DependencyProperty AttachedDetailsViewSelectedItemProperty =
    DependencyProperty.Register("AttachedDetailsViewSelectedItem", typeof(object), typeof(SelectionBehavior), new PropertyMetadata(null));

    public object AttachedDetailsViewSelectedIndex
    {
        get { return (object)GetValue(AttachedDetailsViewSelectedIndexProperty); }
        set { SetValue(AttachedDetailsViewSelectedIndexProperty, value); }
    }

    public static readonly DependencyProperty AttachedDetailsViewSelectedIndexProperty =
    DependencyProperty.Register("AttachedDetailsViewSelectedIndex", typeof(object), typeof(SelectionBehavior), new PropertyMetadata(null));

    public object AttachedDetailsViewCurrentItem
    {
        get { return (object)GetValue(AttachedDetailsViewCurrentItemProperty); }
        set { SetValue(AttachedDetailsViewCurrentItemProperty, value); }
    }

    public static readonly DependencyProperty AttachedDetailsViewCurrentItemProperty =
    DependencyProperty.Register("AttachedDetailsViewCurrentItem", typeof(object), typeof(SelectionBehavior), new PropertyMetadata(null));

    protected override void OnAttached()
    {
        base.OnAttached();
        this.AssociatedObject.Loaded += AssociatedObject_Loaded;
    }

    void AssociatedObject_Loaded(object sender, System.Windows.RoutedEventArgs e)
    {
        (this.AssociatedObject.DetailsViewDefinition[0] as GridViewDefinition).DataGrid.SelectionChanged += DetailsViewDataGridSelectionChanged;
    }

    void DetailsViewDataGridSelectionChanged(object sender, GridSelectionChangedEventArgs e)
    {
        this.AttachedDetailsViewSelectedItem = (e.OriginalSender as SfDataGrid).SelectedItem;
        this.AttachedDetailsViewSelectedIndex = (e.OriginalSender as SfDataGrid).SelectedIndex;
        this.AttachedDetailsViewCurrentItem = (e.OriginalSender as SfDataGrid).CurrentItem;
    }

    protected override void OnDetaching()
    {
        base.OnDetaching();
        this.AssociatedObject.Loaded -= AssociatedObject_Loaded;
    }
}

{% endhighlight %}
{% endtabs %}

You can get the sample from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/BindingProperties1330432406.zip)

## Customizing Selection Behaviors

The SfDataGrid process the selection operations in selection controller. Below are the built-in selection controllers,

[GridSelectionController](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionController.html) – Process selection operations when selection unit as row.

[GridCellSelectionController](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCellSelectionController.html) – process selection operations when selection unit as cell or Any.

You can customize the default row selection behaviors by overriding `GridSelectionController` class and set it to `SfDataGrid.SelectionController`.

{% tabs %}
{% highlight c# %}

this.dataGrid.SelectionController = new GridSelectionControllerExt(this.dataGrid);

public class GridSelectionControllerExt:GridSelectionController
{

    public GridSelectionControllerExt(SfDataGrid dataGrid):base(dataGrid)
    {     
    }
}

{% endhighlight %}
{% endtabs %}

### Changing Enter Key Behavior

By default, while pressing <kbd>Enter</kbd> key the current cell will be moved to next focused cell in the same column. You can change the behavior by overriding the corresponding selection controllers based on [SelectionUnit](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionUnit.html).

You can change the <kbd>Enter</kbd> key behavior by overriding [ProcessKeyDown](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionController~ProcessKeyDown.html) method in selection controller. In this method you have to create new [KeyEventArgs](https://msdn.microsoft.com/en-us/library/system.windows.input.keyeventargs) which refers the <kbd>Tab</kbd> key and processes the <kbd>Tab</kbd> key action.

{% tabs %}
{% highlight c# %}

public class GridSelectionControllerExt:GridSelectionController
{

    public GridSelectionControllerExt(SfDataGrid dataGrid):base(dataGrid)
    {   
    }
    
    protected override void ProcessKeyDown(KeyEventArgs args)
    {

        if (args.Key == Key.Enter)
        {

            //Creates new KeyEventArgs to refer the Tab key.
            KeyEventArgs arguments = new KeyEventArgs(args.KeyboardDevice, args.InputSource, args.Timestamp, Key.Tab) { RoutedEvent = args.RoutedEvent };

            //Base ProcessKeyDown is invoked to process Tab key operations.
            base.ProcessKeyDown(arguments);
            args.Handled = arguments.Handled;
            return;
        }
        base.ProcessKeyDown(args);
    }
}

{% endhighlight %}
{% endtabs %}

### Selecting all rows in a group when expanding

You can select all the rows in the group which is expanding through mouse click. To achieve this, you have to set [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) as [Extended](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) or [Multiple](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) and also need to override [HandlePointerOperations](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridBaseSelectionController~HandlePointerOperations.html) method in selection controller.

{% tabs %}
{% highlight c# %}

public class GridSelectionControllerExt:GridSelectionController
{

    public GridSelectionControllerExt(SfDataGrid dataGrid)
        :base(dataGrid)
    {     
    }
    
    public override void HandlePointerOperations(GridPointerEventArgs args, Syncfusion.UI.Xaml.ScrollAxis.RowColumnIndex rowColumnIndex)
    {
        base.HandlePointerOperations(args, rowColumnIndex);

        if (args.Operation == PointerOperation.Released)
        {

            if (this.DataGrid.View.TopLevelGroup != null)
            {

                //Get the group from the DisplayElements by resolving record index of corresponding row index
                var group = this.DataGrid.View.TopLevelGroup.DisplayElements[this.DataGrid.ResolveToRecordIndex(rowColumnIndex.RowIndex)];

                if (group != null && group is Group)
                SelectGroupRows(group as Group);
            }
        }
    }
    
    private void SelectGroupRows(Group group)
    {
 
        if (group == null || !group.IsExpanded)
            return;
 
        //Check whether the group contains inner level groups.
 
        if (group.Groups == null)
 
        {
 
            //Get the corresponding start index of record by getting it from DisplayElements .
            var startIndex = this.DataGrid.View.TopLevelGroup.DisplayElements.IndexOf(group as Group);
 
            //Resolve the recordIndex to RowIndex.
            var startRowIndex = this.DataGrid.ResolveToRowIndex(startIndex);
 
            //Gets the count of rows in the group.
            var count = group.ItemsCount + this.DataGrid.GroupSummaryRows.Count;
 
            //Select the rows from corresponding start and end row index
            this.DataGrid.SelectionController.SelectRows(startRowIndex, startRowIndex + count);
        }
 
        else
        {
 
            foreach (var gr in group.Groups)
            {
 
                //Called recursively, to traverse it inner level of group.
                SelectGroupRows(gr);
                var startIndex = this.DataGrid.View.TopLevelGroup.DisplayElements.IndexOf(group as Group);
                var startRowIndex = this.DataGrid.ResolveToRowIndex(startIndex);
 
                //Get the corresponding end index of the group by getting it from DisplayElements using the inner level group.
                var endIndex = this.DataGrid.View.TopLevelGroup.DisplayElements.IndexOf(gr as Group);
                var endRowIndex = this.DataGrid.ResolveToRowIndex(endIndex);
                this.DataGrid.SelectionController.SelectRows(startRowIndex, endRowIndex);
            }
        }
    }
}

{% endhighlight %}
{% endtabs %}

### Selecting the column when clicking header

You can select entire column on clicking column header by handling [MouseLeftButtonUp](https://msdn.microsoft.com/en-us/library/system.windows.uielement.mouseleftbuttonup) event of SfDataGrid. You have to set [SelectionUnit](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SelectionUnit.html) as [Cell](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionUnit.html) or [Any](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionUnit.html) and [SelectionMode](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SelectionMode.html) as [Extended](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) or [Multiple](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridSelectionMode.html) to achieve this behavior. 

By default the sorting operation will be performed while clicking on column header where you can disable this action by setting [AllowSorting](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~AllowSorting.html) as false or [SortClickAction](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~SortClickAction.html) as [DoubleClick](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SortClickAction.html).

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       SelectionUnit="Cell"
                       SortClickAction="DoubleClick"
                       SelectionMode="Extended"
                       ItemsSource="{Binding Orders}">

{% endhighlight %}

{% highlight c# %}

this.dataGrid.MouseLeftButtonUp += dataGrid_MouseLeftButtonUp;
private void dataGrid_MouseLeftButtonUp(object sender, MouseButtonEventArgs e)
{
 
    if (e.ClickCount != 1)
        return;
    var visualContainer = this.dataGrid.GetVisualContainer();
 
    //Getting row and column index from the current pointer position.
    var rowColumnIndex = visualContainer.PointToCellRowColumnIndex(e.GetPosition(visualContainer));
    var columnIndex = this.dataGrid.ResolveToGridVisibleColumnIndex(rowColumnIndex.ColumnIndex);
 
    //Return if rowColumnIndex does not refer the HeaderCell
 
    if (this.dataGrid.GetHeaderIndex() != rowColumnIndex.RowIndex || columnIndex < 0)
        return;
 
    //Gets the first record of the DataGrid.
    var firstRowData = this.dataGrid.GetRecordAtRowIndex(dataGrid.GetFirstDataRowIndex());
 
    //Gets the last record of the DataGrid.
    var lastRowData = this.dataGrid.GetRecordAtRowIndex(dataGrid.GetLastDataRowIndex());
 
    if (firstRowData == null || lastRowData == null)
        return;
 
    //Gets the column of the pointer position.
    var column = this.dataGrid.Columns[columnIndex];
 
    //Selects the entire column
    this.dataGrid.SelectCells(firstRowData, column, lastRowData, column);
}

{% endhighlight %}
{% endtabs %}

You can get the sample from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/SelectColumn1411579311.zip).

![Column selection when clicking column header in WPF DataGrid](Selection_images/Selection_img15.png)


### Avoid CaptionSummaryRow selection on Grouping

While grouping any column, by default the first CaptionSummaryRow will be selected when the [CurrentItem](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentItem.html) is null. You can change this action by overriding the [ProcessOnGroupChanged](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridBaseSelectionController~ProcessOnGroupChanged.html) method in selection controller. 

{% tabs %}
{% highlight c# %}

public class GridSelectionControllerExt : GridSelectionController
{
 
    public GridSelectionControllerExt(SfDataGrid dataGrid) : base(dataGrid)
    {
    }       
 
    protected override void ProcessOnGroupChanged(GridGroupingEventArgs args)
    {
        base.ProcessOnGroupChanged(args);
        var removedItems = new List<object>();
 
        //Refresh the selection only in record rows.
        this.RefreshSelectedItems(ref removedItems);
 
        //Updates the current cell and current row.
        this.UpdateCurrentRowIndex();
    }
}

{% endhighlight %}
{% endtabs %}