---
layout: post
title: Editing | SfDataGrid | WPF | Syncfusion
description: editing
platform: wpf
control: SfDataGrid
documentation: ug
---

# Editing 

SfDataGrid provides support for editing and it can be enabled or disabled by setting [SfDataGrid.AllowEditing](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~AllowEditing.html) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       AllowEditing="True"
                       AutoGenerateColumns="True"
                       ItemsSource="{Binding Orders}" />
{% endhighlight %}

{% highlight c# %}
dataGrid.AllowEditing = true;
{% endhighlight %}
{% endtabs %}

You can enable or disable editing for particular column by setting [GridColumn.AllowEditing](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~AllowEditing.html) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:GridTextColumn AllowEditing="True" MappingName="OrderID" />
{% endhighlight %}

{% highlight c# %}
dataGrid.Columns["OrderID"].AllowEditing = true;
{% endhighlight %}
{% endtabs %}

N> [GridColumn.AllowEditing](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumnBase~AllowEditing.html) takes higher priority than [SfDataGrid.AllowEditing](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~AllowEditing.html).

![](Editing_images/Editing_img1.jpeg)


N> It is mandatory to set the [NavigationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~NavigationMode.html) to Cell to enable [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) navigation and editing.

### Entering into edit mode

You can enter into edit mode by pressing <kbd>F2</kbd> key or clicking (touch also supported) the cell. You can allow users to edit the cell in single click (OnTap) or double click (OnDoubleTab) by setting by [EditTrigger](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~EditTrigger.html) property.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       AllowEditing="True" 
                       EditTrigger="OnTap"
                       ItemsSource="{Binding Orders}" />
{% endhighlight %}


{% highlight c# %}
dataGrid.EditTrigger = EditTrigger.OnTap;
{% endhighlight %}
{% endtabs %}

### Cursor placement

When the cell enters into edit mode, cursor is placed based on [EditorSelectionBehavior](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfGridBase~EditorSelectionBehavior.html) property. 

SelectAll – selects the text of edit element loaded inside cell.

MoveLast – places the cursor at the last of edit element loaded inside cell.  

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"
                       AllowEditing="True"
                       EditorSelectionBehavior="SelectAll"
                       ItemsSource="{Binding Orders}" />
{% endhighlight %}

{% highlight c# %}
dataGrid.EditorSelectionBehavior = EditorSelectionBehavior.SelectAll;
{% endhighlight %}
{% endtabs %}

## Support for IEditableObject

SfDataGrid supports to commit and roll back the changes in row level when underlying data object implements [IEditableObject](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject.aspx) interface. 

The editing changes in a row will be committed only when user move to next row or pressing enter key in [EndEdit](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject.endedit.aspx). Also when user press <kbd> Esc </kbd> key, then the changes made in a row will be reverted in [CancelEdit](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject.canceledit.aspx). 

`IEditableObject` has the following methods to capture editing, 

[BeginEdit](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject.beginedit.aspx) – Gets called to begin edit on underlying data object when cell in a row get into edit mode. 

[CancelEdit](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject.canceledit.aspx) – Gets called when user press the <kbd>Esc</kbd> key to discard the changes in a row since last `BeginEdit` call. 

[EndEdit](https://msdn.microsoft.com/en-us/library/system.componentmodel.ieditableobject.endedit.aspx) – Gets called when user move to the next row or press Enter key  to commit changes in underlying data object since last `BeginEdit` call. 

In the below code snippet explains the simple implementation of IEditableObject.

{% tabs %}
{% highlight c# %}

public class Employee : NotificationObject, IEditableObject
{
    private string _Name;
    private int _ContactID;
    private string _Title;
    private DateTime _BirthDate;
    private string _Gender;
    private double _SickLeaveHours;
    private double _Salary;
    
    protected Dictionary<string, object> BackUp()
    {
        var dict = new Dictionary<string, object>();
        var itemProperties = this.GetType().GetTypeInfo().DeclaredProperties;
        foreach (var pDescriptor in itemProperties)
        {
            if (pDescriptor.CanWrite)
                dict.Add(pDescriptor.Name, pDescriptor.GetValue(this));
        }
        return dict;
    }

    public string Name
    {
        get { return this._Name; }
        set
        {
            this._Name = value;
            this.RaisePropertyChanged("Name");
        }

    }

    public string Title
    {
        get { return this._Title; }
        set
        {
            this._Title = value;
            this.RaisePropertyChanged("Title");
        }
    }

    public int ContactID
    {
        get { return this._ContactID; }
        set
        {
            this._ContactID = value;
            this.RaisePropertyChanged("ContactID");
        }
    }

    public DateTime BirthDate
    {
        get { return this._BirthDate; }
        set
        {
            this._BirthDate = value;
            this.RaisePropertyChanged("BirthDate");
        }
    }

    public string Gender
    {
        get { return this._Gender; }
        set
        {
            this._Gender = value;
            this.RaisePropertyChanged("Gender");
        }
    }

    public double SickLeaveHours
    {
        get { return this._SickLeaveHours; }
        set
        {
            this._SickLeaveHours = value;
            this.RaisePropertyChanged("SickLeaveHours");
        }
    }

    public double Salary
    {
        get { return this._Salary; }
        set
        {
            this._Salary = value;
            this.RaisePropertyChanged("Salary");
        }
    }

    private int _EmployeeID;

    public int EmployeeID
    {
        get { return this._EmployeeID; }
        set
        {
            this._EmployeeID = value;
            this.RaisePropertyChanged("EmployeeID");
        }
    }

    private Dictionary<string, object> storedValues;

    public void BeginEdit()
    {
        this.storedValues = this.BackUp();
    }

    public void CancelEdit()
    {
        if (this.storedValues == null)
            return;

        foreach (var item in this.storedValues)
        {
            var itemProperties = this.GetType().GetTypeInfo().DeclaredProperties;
            var pDesc = itemProperties.FirstOrDefault(p => p.Name == item.Key);
            if (pDesc != null)
                pDesc.SetValue(this, item.Value);
        }
    }

    public void EndEdit()
    {
        if (this.storedValues != null)
        {
            this.storedValues.Clear();
            this.storedValues = null;
        }
        Debug.WriteLine("End Edit Called");
    }
}

public class NotificationObject : INotifyPropertyChanged
{
    public void RaisePropertyChanged(string propName)
    {
        if (this.PropertyChanged != null)
        this.PropertyChanged(this, new PropertyChangedEventArgs(propName));
    }

    public event PropertyChangedEventHandler PropertyChanged;

}
{% endhighlight %}
{% endtabs %}

## Events

SfDataGrid triggers the following events during editing. 

### CurrentCellBeginEdit Event

[CurrentCellBeginEdit](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellBeginEdit_EV.html) event occurs when the [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) enter into edit mode. [CurrentCellBeginEditEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellBeginEditEventArgs.html) has following members which provides information for `CurrentCellBeginEdit` event.

* [Cancel](https://msdn.microsoft.com/query/dev10.query?appId=Dev10IDEF1&l=EN-US&k=k(System.ComponentModel.CancelEventArgs.Cancel)&rd=true) : When set to ‘true’, the event is canceled and the `CurrentCell` does not enter into the edit mode.
* [RowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellBeginEditEventArgs~RowColumnIndex.html) : Gets the current row column index of the DataGrid.
* [Column](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellBeginEditEventArgs~Column.html) : Gets the Grid Column of the SfDataGrid.

{% tabs %}
{% highlight c# %}

this.dataGrid.CurrentCellBeginEdit += dataGrid_CurrentCellBeginEdit;
void dataGrid_CurrentCellBeginEdit(object sender, Syncfusion.UI.Xaml.Grid.CurrentCellBeginEditEventArgs args)
{
    
}

{% endhighlight %}
{% endtabs %}

### CurrentCellEndEdit Event

[CurrentCellEndEdit](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellEndEdit_EV.html) event occurs when the [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) exits the edit mode. [CurrentCellEndEditEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellEndEditEventArgs.html) has following members which provides information for `CurrentCellEndEdit` event.

* [RowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellEndEditEventArgs~RowColumnIndex.html) : Gets the value for the current row column index.

{% tabs %}
{% highlight c# %}

this.dataGrid.CurrentCellEndEdit += dataGrid_CurrentCellEndEdit;
void dataGrid_CurrentCellEndEdit(object sender, Syncfusion.UI.Xaml.Grid.CurrentCellEndEditEventArgs args)
{
    
}

{% endhighlight %}
{% endtabs %}

### CurrentCellValueChanged Event

[CurrentCellValueChanged](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValueChanged_EV.html) event occurs whenever a value changes in GridColumn's that supports editing. [CurrentCellValueChangedEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellValueChangedEventArgs.html) has following members which provides information for `CurrentCellValueChanged` event.

* [Column](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellBeginEditEventArgs~Column.html) : Gets the Grid Column of the SfDataGrid.
* [RowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellValueChangedEventArgs~RowColumnIndex.html) : Gets the value of the current RowColumnIndex.

{% tabs %}
{% highlight c# %}

this.dataGrid.CurrentCellValueChanged += dataGrid_CurrentCellValueChanged;
void dataGrid_CurrentCellValueChanged(object sender, Syncfusion.UI.Xaml.Grid.CurrentCellValueChangedEventArgs args)
{
    
}

{% endhighlight %}
{% endtabs %}

N> GridComboBoxColumn and GridMultiColumnDropList, you have to use the CurrentCellDropDownSelectionChanged event.

### CurrentCellDropDownSelectionChanged Event

[CurrentCellDropDownSelectionChanged](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellDropDownSelectionChanged_EV.html) event occurs whenever the `SelectedItem` of `GridMultiColumnDropDownList` and `GridComboBoxColumn` column changed.

[CurrentCellDropDownSelectionChangedEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellDropDownSelectionChangedEventArgs.html) has following members which provides information for `CurrentCellDropDownSelectionChanged` event.

* [RowColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellDropDownSelectionChangedEventArgs~RowColumnIndex.html) – Gets the RowColumnIndex of the corresponding item that were selected from the drop-down control.
* [SelectedIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellDropDownSelectionChangedEventArgs~SelectedIndex.html) – Gets the index of the corresponding item that were selected from the drop-down control.
* [SelectedItem](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellDropDownSelectionChangedEventArgs~SelectedItem.html) – Gets the data item that were selected from the drop-down control.

{% tabs %}
{% highlight c# %}

this.dataGrid.CurrentCellDropDownSelectionChanged += dataGrid_CurrentCellDropDownSelectionChanged;
void dataGrid_CurrentCellDropDownSelectionChanged(object sender, CurrentCellDropDownSelectionChangedEventArgs args)
{
    
}

{% endhighlight %}
{% endtabs %}

## Programmatically edit the cell

### BeginEdit

SfDataGrid allows you to edit the cell programmatically by calling the [BeginEdit](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~BeginEdit.html) method. Initially the [CurrentCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~CurrentCell.html) need to set before calling the `BeginEdit` method when the CurrentCell value is null.

{% tabs %}
{% highlight c# %}
this.dataGrid.Loaded += dataGrid_Loaded;
void dataGrid_Loaded(object sender, RoutedEventArgs e)
{
    RowColumnIndex rowColumnIndex = new RowColumnIndex(3, 2);
    this.dataGrid.MoveCurrentCell(rowColumnIndex);
    this.dataGrid.SelectionController.CurrentCellManager.BeginEdit();
}
{% endhighlight %}
{% endtabs %}

### EndEdit

You can call the [EndEdit](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCurrentCellManager~EndEdit.html) method to programmatically end edit. 

{% tabs %}
{% highlight c# %}
this.dataGrid.Loaded += dataGrid_Loaded;        
void dataGrid_Loaded(object sender, RoutedEventArgs e)
{
    RowColumnIndex rowColumnIndex = new RowColumnIndex(3, 2);
    this.dataGrid.MoveCurrentCell(rowColumnIndex);
    this.dataGrid.SelectionController.CurrentCellManager.EndEdit();
}

{% endhighlight %}
{% endtabs %}

### CancelEdit

You can use the [CurrentCellBeginEdit](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellBeginEdit_EV.html) event to cancel the editing operation for the corresponding cell.

{% tabs %}
{% highlight c# %}

this.dataGrid.CurrentCellBeginEdit += dataGrid_CurrentCellBeginEdit;
void dataGrid_CurrentCellBeginEdit(object sender, Syncfusion.UI.Xaml.Grid.CurrentCellBeginEditEventArgs args)
{
    var recordindex = this.dataGrid.ResolveToRecordIndex(args.RowColumnIndex.RowIndex);
    var columnindex = this.dataGrid.ResolveToGridVisibleColumnIndex(args.RowColumnIndex.ColumnIndex);
    var mappingname = this.dataGrid.Columns[columnindex].MappingName;
    var record = this.dataGrid.View.Records.GetItemAt(recordindex);
    var cellvalue = this.dataGrid.View.GetPropertyAccessProvider().GetValue(record, mappingname);
    if (args.RowColumnIndex == new RowColumnIndex(3, 2))
    args.Cancel = true;
}

{% endhighlight %}
{% endtabs %}

## Mouse and Keyboard operations for UIElement inside Template

You can directly load edit element using GridTemplateColumn.CellTemplate property. In this case, you can provide focus and control (keyboard and mouse) to the UIElement inside CellTemplate in the below ways,

### Providing focus to the control inside the Template

You can focus to the particular UIElement loaded inside template when cell gets activated by setting [FocusedManager.FocusedElement](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.FocusManagerHelper~FocusedElementProperty.html) attached property. 

{% tabs %}
{% highlight xaml %}

<syncfusion:GridTemplateColumn HeaderText="Customer ID" 
                               MappingName="CustomerID" >
    <syncfusion:GridTemplateColumn.CellTemplate>
        <DataTemplate>
            <TextBlock syncfusion:FocusManagerHelper.FocusedElement="True"
                       FontStyle="Italic"
                       FontWeight="SemiBold"
                       Padding="2,0"
                       Text="{Binding CustomerID}" />
        </DataTemplate>
    </syncfusion:GridTemplateColumn.CellTemplate>
</syncfusion:GridTemplateColumn>

{% endhighlight %}
{% endtabs %}

### Providing keyboard control to UIElement inside CellTemplate

You can allow `UIElement` loaded inside `CellTemplate` to handle keyboard interaction by setting [FocusManagerHelper.WantsKeyInput](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.FocusManagerHelper~WantsKeyInputProperty.html) attached property to `GridColumn`. 

{% tabs %}
{% highlight xaml %}
<syncfusion:GridTemplateColumn MappingName="ProductId"  
                               syncfusion:FocusManagerHelper.WantsKeyInput= "True">
    <syncfusion:GridTemplateColumn.CellTemplate>
        <DataTemplate>
            <Grid>
                <TextBox x:Name="text" Text="{Binding ProductId}"/>
            </Grid>
        </DataTemplate>
    </syncfusion:GridTemplateColumn.CellTemplate>
</syncfusion:GridTemplateColumn>

{% endhighlight %}
{% endtabs %}

N> Enter and Tab keys are always handled by SfDataGrid only.

### Providing mouse control to UIElement inside template

You can allow `UIElement` loaded inside template to handle mouse interaction in required cases by setting [VisualContainer.WantsMouseInput](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.VisualContainer~WantsMouseInputProperty.html) attached property to `GridColumn`.

{% tabs %}
{% highlight xaml %}

<syncfusion:SfDataGrid x:Name="dataGrid"
                       AutoGenerateColumns="False" 
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.Columns>
        <syncfusion:GridTemplateColumn MappingName="ProductName">
            <syncfusion:GridTemplateColumn.CellTemplate>
                <DataTemplate>
                    <ComboBox ItemsSource="{Binding ComboItems, Source={StaticResource viewModel}}" 
                              syncfusion:VisualContainer.WantsMouseInput="True" />
                </DataTemplate>
            </syncfusion:GridTemplateColumn.CellTemplate>
        </syncfusion:GridTemplateColumn>
    </syncfusion:SfDataGrid.Columns>
</syncfusion:SfDataGrid>

{% endhighlight %}
{% endtabs %}

## How to

### Change the foreground of edited cells to keep track of changes

You can change the foreground color of edited cells through the CellStyleSelector.

Please follow the below steps to highlight the edited cells.

1. Add new property `EditedColumns` in data object to maintain edited column `MappingName`.
2. Add the MappingName of the column to ` EditedColumns`, in CurrentCellValueChanged to keep track of edited columns in data object. 

{% tabs %}
{% highlight c# %}

this.dataGrid.CurrentCellValueChanged+=dataGrid_CurrentCellValueChanged;
private void dataGrid_CurrentCellValueChanged(object sender, CurrentCellValueChangedEventArgs args)
{
    if (!(args.Record as OrderInfo).EditedColumns.Contains(args.Column.MappingName))
        (args.Record as OrderInfo).EditedColumns.Add(args.Column.MappingName);
    //updates the current row index
    this.dataGrid.UpdateDataRow(args.RowColumnIndex.RowIndex);
}

{% endhighlight %}
{% endtabs %}

3. Create a style of TargetType `GridCell` and change the Foreground using CellStyleSelector based on ` EditedColumns` property in data object.

{% tabs %}
{% highlight xaml %}
<Application.Resources>
    <Style x:Key="cellStyle" TargetType="syncfusion:GridCell">
        <Setter Property="Foreground" Value="DarkOrange" />
    </Style>
</Application.Resources>

<Window.Resources>
    <local:CellStyleSelector x:Key="cellStyleSelector" />
</Window.Resources>

<syncfusion:SfDataGrid x:Name="dataGrid"
                       CellStyleSelector="{StaticResource cellStyleSelector}"
                       AllowEditing="True"
                       ItemsSource="{Binding Path=OrdersDetails}"
                       ShowRowHeader="True">
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

{% tabs %}
{% highlight c# %}
public class CellStyleSelector : StyleSelector
{
    public override Style SelectStyle(object item, DependencyObject container)
    {
        var gridCell = container as GridCell;
        if (gridCell.ColumnBase == null || gridCell.ColumnBase.GridColumn == null)
            base.SelectStyle(item, container);
            
        var record = item as OrderInfo;
        if (record.EditedColumns.Contains(gridCell.ColumnBase.GridColumn.MappingName))        
            return App.Current.Resources["cellStyle"] as Style;
            
        return base.SelectStyle(item, container);
    }
}
{% endhighlight %}
{% endtabs %}

![](Editing_images/Editing_img2.jpeg)


### Allow editing when pressing minus key

SfDataGrid does not allow the cell to get into the edit mode while pressing the <kbd>Minus</kbd>key or any special character. You can overcome this behavior by customizing the SfDataGrid class, and overriding its OnTextInput () method.

{% tabs %}
{% highlight c# %}
public class SfDataGridExt : SfDataGrid
{
    public SfDataGridExt()
    : base()
    {
    }
    
    protected override void OnTextInput(TextCompositionEventArgs e)
    {
        if (!SelectionController.CurrentCellManager.HasCurrentCell)
        {
            base.OnTextInput(e);
            return;
        }

        //Get the Current Row and Column index from the CurrentCellManager
        var rowColumnIndex = SelectionController.CurrentCellManager.CurrentRowColumnIndex;
        RowGenerator rowGenerator = this.RowGenerator;
        //Get the row from the Row index
        var dataRow = rowGenerator.Items.FirstOrDefault(item => item.RowIndex == rowColumnIndex.RowIndex);
        //Check whether the datarow is null or not and the type as DataRow
        if (dataRow != null && dataRow is DataRow)
        {
            //Get the column from the VisibleColumn collection based on the column index
            var dataColumn = dataRow.VisibleColumns.FirstOrDefault(column => column.ColumnIndex == rowColumnIndex.ColumnIndex);
            //Convert the input text to char type 
            char text;
            char.TryParse(e.Text, out text);
            //Skip if the column is GridTemplateColumn and the column is not already in editing 
            //Allow Editing only pressed letters digits and Minus sign key 
            if (dataColumn != null && !(dataColumn.GridColumn is GridTemplateColumn) && !dataColumn.IsEditing && SelectionController.CurrentCellManager.BeginEdit() && (e.Text.Equals("-") || char.IsLetterOrDigit(text)))
                dataColumn.Renderer.PreviewTextInput(e);
        }
        base.OnTextInput(e);
    }
}
{% endhighlight %}
{% endtabs %}