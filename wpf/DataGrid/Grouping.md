---
layout: post
title: Grouping in WPF DataGrid control | Syncfusion
description: Learn about column grouping support in Syncfusion WPF DataGrid (SfDataGrid) control and more details.
platform: wpf
control: SfDataGrid
documentation: ug
---

# Grouping in WPF DataGrid (SfDataGrid)

DataGrid allows you to group the data against one or more columns. When grouping is applied, the data is organized into a hierarchical structure based on matching column values and it is sorted by ascending order.
 
SfDataGrid allows you to group the data in below ways,

* UI Grouping
* Programmatic Grouping

## UI grouping

You can allow end-user to group the data by setting  [SfDataGrid.AllowGrouping](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AllowGrouping.html) property to `true` , where user can drag and drop the column into `GroupDropArea` to group based on that column.
 
When the column is grouped, records that have an identical value in the column are combined to form a group. The GroupDropArea can be enabled by setting the [SfDataGrid.ShowGroupDropArea](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ShowGroupDropArea.html) property to `true`.


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AllowGrouping="False"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True" />    
{% endhighlight %}
{% highlight c# %}
this.dataGrid.AllowGrouping = true;
{% endhighlight %}
{% endtabs %}

You can enable or disable grouping on particular column by setting the [GridColumn.AllowGrouping](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~AllowGroupingProperty.html) property.


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AutoGenerateColumns="False"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTextColumn AllowGrouping="True" MappingName="OrderID" />
        <syncfusion:GridTextColumn AllowGrouping="False" MappingName="CustomerID" />        
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.dataGrid.Columns["OrderID"].AllowGrouping = true;
this.dataGrid.Columns["CustomerID"].AllowGrouping = true;
{% endhighlight %}
{% endtabs %}


N> [GridColumn.AllowGrouping](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~AllowGroupingProperty.html) takes higher priority than [SfDataGrid.AllowGrouping](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AllowGrouping.html).

![WPF DataGrid Grouping](Grouping_images/Grouping_img1.png)

The data can be grouped by an unlimited number of columns. To group more than one columns, drag-and-drop the desired columns in to `GroupDropArea`.

![WPF DataGrid grouped by multiple columns](Grouping_images/Grouping_img2.png)

Each group is identified by its `CaptionSummaryRows` and it is used to organize the data into a hierarchical tree structure based on identical values of that column. The underlying records in each caption summary row can be expanded or collapsed by clicking its group caption.


Each `CaptionSummaryRow` carries information about a particular group like group name, number of items (records) in the group, etc. You can refer [Caption Summaries](http://help.syncfusion.com/wpf/sfdatagrid/summaries#caption-summaries) section, for more information about `CaptionSummaryRow`.

## Programmatic grouping

SfDataGrid allows you to group the data programmatically by adding or removing [GroupColumnDescription](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription.html) to [SfDataGrid.GroupColumnDescriptions](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupColumnDescriptions.html) collection.

For example, if you want to group the OrderID column programmatically, define its [MappingName](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~MappingName.html) to [ColumnName](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription~ColumnName.html) property of `GroupColumnDescription`. Then add the `GroupColumnDescription` to the `SfDataGrid.GroupColumnDescriptions` collection.


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True">
    <syncfusion:SfDataGrid.GroupColumnDescriptions>
        <syncfusion:GroupColumnDescription ColumnName="OrderID" />
    </syncfusion:SfDataGrid.GroupColumnDescriptions>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.dataGrid.GroupColumnDescriptions.Add(new GroupColumnDescription() { ColumnName = "OrderID" });
{% endhighlight %}
{% endtabs %}


You can group more than one column programmatically.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"                               
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True">

    <syncfusion:SfDataGrid.GroupColumnDescriptions>
        <syncfusion:GroupColumnDescription ColumnName="OrderID" />
        <syncfusion:GroupColumnDescription ColumnName="CustomerID" />
    </syncfusion:SfDataGrid.GroupColumnDescriptions>

</syncfusion:SfDataGrid>
{% endhighlight %}
{% highlight c# %}
this.dataGrid.View.BeginInit();
this.dataGrid.GroupColumnDescriptions.Add(new GroupColumnDescription() { ColumnName = "OrderID" });
this.dataGrid.GroupColumnDescriptions.Add(new GroupColumnDescription() { ColumnName = "CustomerID" });
this.dataGrid.View.EndInit();
{% endhighlight %}
{% endtabs %}

## Group based on display text

You can group the column in DataGrid based on the value being displayed in cell by setting [GridColumn.GroupMode](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GroupMode.html) as `Display`.
In the below example, OrderID column displays value with one decimal digit in cell. But when you group, groups will be created based on actual value considering all decimal digits of value (Refer right side screen shot). You can group based value displayed in the cell by setting [GridColumn.GroupMode](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GroupMode.html) as `Display` (Refer left side screen shot for the same data).

{% tabs %}
{% highlight xaml %}
<Syncfusion:GridNumericColumn NumberDecimalDigits="1" MappingName="OrderID" HeaderText="OrderID" GroupMode="Display"/>
{% endhighlight %}
{% highlight c# %}
this.datagrid.Columns["OrderID"].GroupMode = DataReflectionMode.Display;
{% endhighlight %}
{% endtabs %}

![WPF DataGrid column grouped based on displat text](Grouping_images/Grouping_img11.png)

### Group caption based on DisplayMember when grouping GridComboBoxColumn and GridMultiColumnDropDownList

In SfDataGrid, you can group the column based on display value and also the same can be displayed  in caption summary by setting [GridColumn.GroupMode](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GroupMode.html) as `Display`.

{% tabs %}
{% highlight xaml %}
<Syncfusion:GridComboBoxColumn ItemsSource="{Binding ComboItemsSource}" MappingName="ShipId" DisplayMemberPath="ShipCity" SelectedValuePath="ShipId" GroupMode="Display"/>
{% endhighlight %}
{% highlight c# %}
this.datagrid.Columns.Add(new GridComboBoxColumn()
{
    ItemsSource = viewModel.ComboItemsSource,
    DisplayMemberPath = "ShipCity",
    MappingName = "ShipId",
    SelectedValuePath = "ShipId",
    GroupMode = DataReflectionMode.Display
});
{% endhighlight %}
{% endtabs %}

![WPF DataGrid grouped based on display member of combobox column](Grouping_images/Grouping_img12.png)

## Clearing or removing group

You can remove all the groups by clearing [SfDataGrid.GroupColumnDescriptions](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupColumnDescriptions.html) collection.


{% tabs %}
{% highlight c# %}
this.dataGrid.GroupColumnDescriptions.Clear();
{% endhighlight %}
{% endtabs %}


You can ungroup the column programmatically at runtime by removing [GroupColumnDescription](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription.html)  from [SfDataGrid.GroupColumnDescriptions](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupColumnDescriptions.html) collection.


{% tabs %}
{% highlight c# %}
this.dataGrid.View.BeginInit();            
this.dataGrid.GroupColumnDescriptions.Remove(this.dataGrid.GroupColumnDescriptions[0]);
this.dataGrid.View.EndInit();
{% endhighlight %}
{% endtabs %}


To ungroup the column in UI, click the close button on column header or drag the column header from the `GroupDropArea` and drop it on the header row.

![Displaying ungrouping of column in UI for WPF SfDataGrid](Grouping_images/Grouping_img3.png)


## Hiding the column when grouped

You can hide the column header when the particular column gets grouped by setting [SfDataGrid.ShowColumnWhenGrouped](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ShowColumnWhenGrouped.html) property to `false`.

 
{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}"
                        ShowColumnWhenGrouped="False"
                        ShowGroupDropArea="True" />
{% endhighlight %}
{% highlight c# %}
this.dataGrid.ShowColumnWhenGrouped = false;
{% endhighlight %}
{% endtabs %}


![Displaying how to hide a grouped column in WPF SfDataGrid](Grouping_images/Grouping_img4.png)

## Freezing caption rows when scrolling 

You can freeze the group caption of the group in view until its records scrolled out of the view by setting the [SfDataGrid.AllowFrozenGroupHeaders](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AllowFrozenGroupHeaders.html) property to `true`.
 
{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"                            
                        AutoGenerateColumns="True"
                        AllowFrozenGroupHeaders="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True" />

{% endhighlight %}
{% highlight c# %}
this.dataGrid.AllowFrozenGroupHeaders = true;
{% endhighlight %}
{% endtabs %}


![WPF DataGrid with frozen caption summary rows](Grouping_images/Grouping_img5.png)

## Expanding or collapsing the groups

By default, you can view the records in each group by expanding or collapsing its group caption.

You can allow end-user to expand or collapse the groups programmatically at runtime.
 
### Expand groups while grouping
 
You can expand all the groups while grouping by setting [SfDataGrid.AutoExpandGroups](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoExpandGroups.html) to `true`. So, when user group any column, then all groups will be in expanded state.
 
{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AutoExpandGroups="True"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True" />
{% endhighlight %}
{% highlight c# %}
this.dataGrid.AutoExpandGroups = true;
{% endhighlight %}
{% endtabs %}

### Programmatically expand or collapse the groups

#### Expand or collapse all the Groups

You can expand or collapse all the groups at programmatically at runtime by using [SfDataGrid.ExpandAllGroup](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ExpandAllGroup.html) and [SfDataGrid.CollapseAllGroup](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CollapseAllGroup.html) methods.


{% tabs %}
{% highlight c# %}
this.dataGrid.ExpandAllGroup();
this.dataGrid.CollapseAllGroup();
{% endhighlight %}
{% endtabs %}


#### Expand or Collapse the Group based on its level

You can expand or collapse the group based on its level by using [SfDataGrid.ExpandGroupsAtLevel](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ExpandGroupsAtLevel.html) and [SfDataGrid.CollapseGroupsAtLevel](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CollapseGroupsAtLevel.html) methods.


{% tabs %}
{% highlight c# %}
this.dataGrid.ExpandGroupsAtLevel(2);
this.dataGrid.CollapseGroupsAtLevel(2);
{% endhighlight %}
{% endtabs %}


#### Expand or Collapse the specific Group

You can expand or collapse specific group by using [SfDataGrid.ExpandGroup](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~ExpandGroup.html) and [SfDataGrid.CollapseGroup](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CollapseGroup.html) methods.


{% tabs %}
{% highlight c# %}
var group = (dataGrid.View.Groups[0] as Group);
this.dataGrid.ExpandGroup(group);
this.dataGrid.CollapseGroup(group);
{% endhighlight %}
{% endtabs %}

## Customize indent column width 

You can customize the width of IndentColumn in SfDataGrid by using [IndentColumnWidth](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~IndentColumnWidth.html) property as like below.

{% tabs %}
{% highlight xaml %}
<Syncfusion:SfDataGrid x:Name="dataGrid"                                      
                       AllowGrouping="True"
                       IndentColumnWidth="50"
                       ShowGroupDropArea="True"
                       ItemsSource="{Binding OrderInfoCollection }">
{% endhighlight %}
{% highlight c# %}
this.dataGrid.IndentColumnWidth = 50;
{% endhighlight %}
{% endtabs %}

## GroupDropArea customization

### GroupDropArea text

You can change the `GroupDropArea’ s` text can by setting [SfDataGrid.GroupDropAreaText](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupDropAreaText.html) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       GroupDropAreaText="Drag and drop the columns here"
                       ItemsSource="{Binding Orders}"
                       ShowGroupDropArea="True" />
{% endhighlight %}
{% endtabs %}


![WPF DataGrid with custom group drop area text](Grouping_images/Grouping_img6.png)

### GroupDropArea height and appearance


SfDataGrid allows you to customize the appearance and height of `GroupDropArea` by writing the style of TargetType `GroupDropArea`.


{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <Style TargetType="syncfusion:GroupDropArea">
        <Setter Property="Height" Value="80" />        
        <Setter Property="Foreground" Value="Red" />
        <Setter Property="Background" Value="Pink" />
    </Style>
</Window.Resources>

{% endhighlight %}
{% endtabs %}


![Displaying customization of GroupDropDrea in WPF SfDataGrid](Grouping_images/Grouping_img7.png)

### Expanding GroupDropArea while loading


By default, the `GroupDropArea` will be expanded while dragging the column towards the `GroupDropArea`. You can set the `GroupDropArea` to be always expanded by setting the [SfDataGrid.IsGroupDropAreaExpanded](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~IsGroupDropAreaExpanded.html) property to `true`. 

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AutoGenerateColumns="True"
                        IsGroupDropAreaExpanded="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True" />
{% endhighlight %}
{% highlight c# %}
this.dataGrid.IsGroupDropAreaExpanded = true;
{% endhighlight %}
{% endtabs %}


## Custom grouping

DataGrid allows you to group the data based on custom logic when the built-in grouping functionality doesn’t meet your requirement. 

To perform custom grouping on a particular column , specify the custom logic through [GroupColumnDescription.Converter](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupColumnDescriptions.html) property and the column name to [GroupColumnDescription.ColumnName](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription~ColumnNameProperty.html) property.

For an example, the Date column is grouped based on the week basis in the following example.

 
{% tabs %}
{% highlight c# %}
public class GroupDateTimeConverter : IValueConverter
{
    public object Convert(object value, System.Type targetType, object parameter, CultureInfo culture)
    {
        var saleinfo = value as SalesByDate;
        var dt = DateTime.Now;
        var days = (int)Math.Floor((dt - saleinfo.Date).TotalDays);
        var dayofweek = (int)dt.DayOfWeek;
        var difference = days - dayofweek;

        if (days <= dayofweek)
        {

            if (days == 0)
                return "TODAY";

            if (days == 1)
                return "YESTERDAY";
            return saleinfo.Date.DayOfWeek.ToString().ToUpper();
        }

        if (difference > 0 && difference <= 7)
            return "LAST WEEK";

        if (difference > 7 && difference <= 14)
            return "TWO WEEKS AGO";

        if (difference > 14 && difference <= 21)
            return "THREE WEEKS AGO";

        if (dt.Year == saleinfo.Date.Year && dt.Month == saleinfo.Date.Month)
            return "EARLIER THIS MONTH";

        if (DateTime.Now.AddMonths(-1).Month == saleinfo.Date.Month)
            return "LAST MONTH";
        return "OLDER";
    }

    public object ConvertBack(object value, System.Type targetType, object parameter, CultureInfo culture)
    {
        throw new System.NotImplementedException();
    }
}
{% endhighlight %}
{% endtabs %}


Now , assign the `GroupDateTimeConverter` into [GroupColumnDescription.Converter](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupColumnDescriptions.html) and set `Date` property to [GroupColumnDescription.ColumnName](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription~ColumnNameProperty.html) property.


{% tabs %}
{% highlight xaml %}
<Window.Resources>
    <local:GroupDateTimeConverter x:Key="customGroupDateTimeConverter" />        
</Window.Resources>
  
<syncfusion:SfDataGrid  x:Name="dataGrid"                          
                        AutoGenerateColumns="True"                          
                        ItemsSource="{Binding DailySalesDetails}">

    <syncfusion:SfDataGrid.GroupColumnDescriptions>
        <syncfusion:GroupColumnDescription ColumnName="Date" Converter="{StaticResource customGroupDateTimeConverter}" />
    </syncfusion:SfDataGrid.GroupColumnDescriptions>
        
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}


![WPF DataGrid grouped based on custom logic](Grouping_images/Grouping_img8.png)

You can download samples from below location,
Custom grouping when ItemsSource is ObservableCollection [click here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/CustomGroupingDemo541349132.zip)
Custom grouping when ItemsSource is DataTable [click here]( http://www.syncfusion.com/downloads/support/directtrac/general/ze/DataTableCustomGrouping1799878748.zip)

You can refer [here](http://help.syncfusion.com/wpf/sfdatagrid/sorting#custom-sorting) to apply custom sorting when grouping is applied.

### Sorting the grouped column records 

In custom grouping, you can sort all the inner records of each group by setting [GroupColumnDescription.SortGroupRecords](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription~SortGroupRecords.html)
sorted based on the column name described in [GroupColumnDescription](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupColumnDescription.html).

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid.GroupColumnDescriptions>
    <syncfusion:GroupColumnDescription ColumnName="SickLeaveHours"
                                       Converter="{StaticResource customGrouping}"
                                       SortGroupRecords="True" />
</syncfusion:SfDataGrid.GroupColumnDescriptions>
{% endhighlight %}
{% highlight c# %}
GroupColumnDescription groupColumnDesc = new GroupColumnDescription()
{
    ColumnName = "SickLeaveHours",
    Converter = new CustomGroupingConverter(),
    SortGroupRecords = true
};
dataGrid.GroupColumnDescriptions.Add(groupColumnDesc);
{% endhighlight %}
{% endtabs %}

In the below screenshot custom grouping is applied based on `SickLeaveHours` column and the inner records in each group are sorted based on `SickLeaveHours` value.


![Displaying customization of sorting inner records of groups in WPF SfDataGrid](Grouping_images/Grouping_img10.png)

## Sorting groups based on summary values

DataGrid allows you to sort the groups based its summary values. You can sort the groups based on summary aggregate value  by using [SfDataGrid. SummaryGroupComparer](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SummaryGroupComparer.html) property.


Follow the below steps to sort the groups based on caption aggregate value.

### Define custom group comparer with custom sort logic

In the below code snippet, the `OrderID` column compared and sorted based on the number of order count in each `OrderID`.
 
{% tabs %}
{% highlight c# %}
public class SortGroupComparers : IComparer<Group>, ISortDirection
{
    public ListSortDirection SortDirection { get; set; }

    public int Compare(Group x, Group y)
    {

        int cmp = 0;
        var xgroupSummary = Convert.ToInt32((x as Group).GetSummaryValue(x.SummaryDetails.SummaryRow.SummaryColumns[0].MappingName, "Count"));
        var ygroupSummary = Convert.ToInt32((y as Group).GetSummaryValue(x.SummaryDetails.SummaryRow.SummaryColumns[0].MappingName, "Count"));
        cmp = ((IComparable)xgroupSummary).CompareTo(ygroupSummary);

        if (this.SortDirection == ListSortDirection.Descending)
            cmp = -cmp;
        return cmp;
    }
}
{% endhighlight %}
{% endtabs %}

### Defining custom group comparer to DataGrid

Custom group comparer can be defined in SfDataGrid using [SfDataGrid.SummaryGroupComparer](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~SummaryGroupComparer.html) property. `SummaryGroupComparer` maintains the custom comparers and the custom comparer gets called when corresponding column is grouped.


{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid  x:Name="dataGrid"
                        AllowSorting="True"
                        AutoGenerateColumns="True"
                        ItemsSource="{Binding Orders}"
                        ShowGroupDropArea="True"
                        SummaryGroupComparer="{StaticResource groupComparer}">

    <syncfusion:SfDataGrid.GroupColumnDescriptions>
        <syncfusion:GroupColumnDescription ColumnName="OrderID" />
    </syncfusion:SfDataGrid.GroupColumnDescriptions>

    <syncfusion:SfDataGrid.CaptionSummaryRow>
        <syncfusion:GridSummaryRow Title="Items Count: {IDCount}" ShowSummaryInRow="True">
            <syncfusion:GridSummaryRow.SummaryColumns>
                <syncfusion:GridSummaryColumn Name="IDCount"
                                                Format="'{Count}'"
                                                MappingName="OrderID"
                                                SummaryType="CountAggregate" />
            </syncfusion:GridSummaryRow.SummaryColumns>
        </syncfusion:GridSummaryRow>
    </syncfusion:SfDataGrid.CaptionSummaryRow>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}


![Displaying grouping in WPF SfDataGrid using custom group comparer](Grouping_images/Grouping_img9.png)

You can download the sample demo [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/SortBySummaryDemo-355692747.zip).


## Grouping events

### GroupExpanding event

The [SfDataGrid.GroupExpanding](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupExpanding_EV.html) event occurs when the group is being expanded.
 
The [GroupChangingEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangingEventArgs.html) of the `GroupExpanding` event provides the information about the expanding group and it has the following members.

[Group](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangingEventArgs~Group.html) - Gets the group that’s being expanded.

[Cancel](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.ComponentModel.CancelEventArgs.Cancel)&rd=true) – Decides whether to cancel the group expansion.
 
You can cancel the group expansion by setting [GroupChangingEventArgs.Cancel](http://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.ComponentModel.CancelEventArgs.Cancel)&rd=true) to `true`.


{% tabs %}
{% highlight c# %}
this.dataGrid.GroupExpanding += dataGrid_GroupExpanding;

void dataGrid_GroupExpanding(object sender, Syncfusion.UI.Xaml.Grid.GroupChangingEventArgs e)
{

    if (e.Group.Key.Equals(1001))    
        e.Cancel = true;    
}       
{% endhighlight %}
{% endtabs %}

### GroupExpanded event

The [SfDataGrid.GroupExpanded](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupExpanded_EV.html) event occurs after the group is expanded.

 
The [GroupChangedEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangedEventArgs.html) of the `GroupExpanded` event provides the information about the expanded group and it has the following member.

[Group](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangedEventArgs~Group.html) - Gets the expanded group.

### GroupCollapsing event 

The [SfDataGrid.GroupCollapsing](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupCollapsing_EV.html) event occurs when the group is being collapsed.

The [GroupChangingEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangingEventArgs.html)  of the `GroupCollapsing` event provides the information about the collapsing group and it contains the following member.

[Group](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangingEventArgs~Group.html) - Gets the group that’s being collapsed.

[Cancel](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.ComponentModel.CancelEventArgs.Cancel)&rd=true) – Decides whether to cancel the group collapsing.

 
You can cancel the group is being collapsed by using [GroupChangingEventArgs.Cancel](http://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.ComponentModel.CancelEventArgs.Cancel)&rd=true) of `GroupCollapsing` event.


{% tabs %}
{% highlight c# %}
this.dataGrid.GroupCollapsing += dataGrid_GroupCollapsing;

void dataGrid_GroupCollapsing(object sender, GroupChangingEventArgs e)
{

    if (e.Group.Key.Equals(1001))    
        e.Cancel = true;    
}
{% endhighlight %}
{% endtabs %}

### GroupCollapsed event
 
The [SfDataGrid.GroupCollapsed](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GroupCollapsed_EV.html) event occurs after the group is collapsed.
 
[GroupChangedEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangedEventArgs.html) of the `GroupCollapsed` event  provides the information about collapsed group and it contains the following member.

[Group](http://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GroupChangedEventArgs~Group.html) - Gets the collapsed group.
