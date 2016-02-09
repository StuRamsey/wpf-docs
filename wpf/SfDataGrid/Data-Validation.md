---
layout: post
title: Data Validation support in SfDataGrid.
description: How to validate the data in SfDataGrid.
platform: wpf
control: SfDataGrid
documentation: ug
---

# Data Validation

SfDataGrid allows you to validate the data and display hints in case of validation is not passed. In case of invalid data, error icon is displayed at the top right corner of [GridCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCell.html). When mouse over the error icon, error information will be displayed in tooltip.
 
## Built-in validations

Built-in validations through IDataErrorInfo, INotifyDataErrorInfo and Data annotation attributes, can be enabled by setting[SfDataGrid.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GridValidationMode.html) or [GridColumn.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GridValidationMode.html) properties.

 `GridColumn.GridValidationMode` takes priority than `SfDataGrid.GridValidationMode`.
 
* `GridValidation.InEdit` - display error icon & tips and also doesn’t allows the users to commit the invalid data without allowing users to edit other cells.
* `GridValidation.InView` - displays error icons and tips alone.
* `GridValidation.None` - disables build-in validation support.

## Built-in validation using IDataErrorInfo / INotifyDataErrorInfo

SfDataGrid provides support to validate the data based on [IDataErrorInfo](https://msdn.microsoft.com/en-us/library/system.componentmodel.idataerrorinfo.aspx)/[INotifyDataErrorInfo](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.aspx).
 
### Using IDataErrorInfo
 
You can validate the data by inheriting the [IDataErrorInfo](https://msdn.microsoft.com/en-us/library/system.componentmodel.idataerrorinfo.aspx) interface in model class.

{% tabs %}
{% highlight c# %}
public class OrderInfo : IDataErrorInfo 
{
    private string country;

    public string Country
    {
        get { return country; }
        set { country = value; }
    }     

    [Display(AutoGenerateField = false)]
    public string Error
    {
        get
        {
            return string.Empty;
        }
    }

    public string this[string columnName]
    {
        get 
        {
            if (!columnName.Equals("Country"))
                return string.Empty;

            if (this.Country.Contains("Germany") || this.Country.Contains("UK"))
                return "Delivery not available for the country " + this.Country;

            return string.Empty;
        }
    }        
}
{% endhighlight %}
{% endtabs %}

Enable built-in validation support by setting [SfDataGrid.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GridValidationMode.html) or [GridColumn.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GridValidationMode.html) property to `InEdit` or `InView`.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid" 
                       ItemsSource="{Binding Orders}"                        
                       AllowEditing="True"                           
                       GridValidationMode="InView"/>
{% endhighlight %}
{% highlight c# %}
this.dataGrid.GridValidationMode = GridValidationMode.InView;
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img1.png)

### INotifyDataErrorInfo

You can validate the data by inheriting the [INotifyDataErrorInfo](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.aspx) interface in model class.

{% tabs %}
{% highlight c# %}
public class OrderInfo : INotifyDataErrorInfo
{
    private List<string> errors = new List<string>();    

    private string shippingCity;

    public string ShipCity
    {
        get { return shippingCity; }
        set { shippingCity = value; }
    }

    public System.Collections.IEnumerable GetErrors(string propertyName)
    {
        if (!propertyName.Equals("ShipCity"))
            return null;

        if (this.ShipCity.Contains("México D.F."))
            errors.Add("Delivery not available for the city " + this.ShipCity);

        return errors;
    }

    [Display(AutoGenerateField = false)]
    public bool HasErrors
    {
        get
        {
            return false;
        }
    }
    public event EventHandler<DataErrorsChangedEventArgs> ErrorsChanged;
}
{% endhighlight %}
{% endtabs %}

Enable built-in validation support by setting [SfDataGrid.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GridValidationMode.html) or [GridColumn.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GridValidationMode.html) property to `InEdit` or `InView`.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid" 
                        ItemsSource="{Binding Orders}"                                                    
                        AllowEditing="True"                                                
                        GridValidationMode="InView"/>
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img2.png)

## Built-in validation using Data Annotation

You can validate the data using **data annotation attributes** by setting [SfDataGrid.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GridValidationMode.html) or [GridColumn.GridValidationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridColumn~GridValidationMode.html) property to `InEdit` or `InView`.

### Using different annotations

The numeric type like int, double, decimal properties can be validated using [Range attributes](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.rangeattribute.aspx).

{% tabs %}
{% highlight c# %}
private int orderID;
[Range(1001, 1005, ErrorMessage = "OrderID between 1001 and 1005 alone processed")]        
public int OrderID
{
    get { return orderID; }
    set { orderID = value; }
}

private decimal price;
[Range(typeof(decimal),"12","20")]
public decimal Price
{
    get { return price; }
    set { price = value; }
}
{% endhighlight %}
{% endtabs %}

The string type property can be validated using [Required](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.requiredattribute.aspx), [String Length attributes](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.stringlengthattribute.aspx)

{% tabs %}
{% highlight c# %}
private string shippingCity;
[Required]
public string ShipCity
{
    get { return shippingCity; }
    set { shippingCity = value; }
}

private string customerName;
[StringLength(17)]
public string CustomerName
{
    get { return customerName; }
    set { customerName = value; }
}
{% endhighlight %}
{% endtabs %}

The data that has heterogeneous type (combination of number, special character) can be validated using [RegularExpressions](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.regularexpressionattribute.aspx).

{% tabs %}
{% highlight c# %}
[RegularExpressionAttribute(@"^[a-zA-Z]{1,40}$", ErrorMessage="Numbers and special characters not allowed")]
public string CustomerID
{
    get { return customerId; }
    set { customerId = value; }
}
{% endhighlight %}
{% endtabs %}

## Custom validation through events

You can validate the cells and rows using [CurrentCellValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValidating_EV.html) and [RowValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowValidating_EV.html) events. SfDataGrid will not allow user to edit other cell / row if validation failed.

### Cell Validation

You can validate the cells using [CurrentCellValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValidating_EV.html) event when the cell is edited. `CurrentCellValdiating` event occurs when the edited cells tries to commit the data or lose the focus. 

[CurrentCellValidatingEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.CurrentCellValidatingEventArgs.html) provides information to `CurrentCellValidating` event for validating the cell. `CurrentCellValidatingEventArgs.OriginalSender` returns the DataGrid fired this event for DetailsView. 

`CurrentCellValidatingEventArgs.NewValue` returns the edited value and you can set the validation status using `CurrentCellValidatingEventArgs.IsValid` property.

{% tabs %}
{% highlight c# %}
this.dataGrid.CurrentCellValidating += dataGrid_CurrentCellValidating;

void dataGrid_CurrentCellValidating(object sender, CurrentCellValidatingEventArgs args)
{
    if (args.NewValue.ToString().Equals("1004"))
    {
        args.IsValid = false;
        args.ErrorMessage = "OrdrerID 1004 cannot be passed";
    }
}
{% endhighlight %}
{% endtabs %}

[SfDataGrid.CurrentCellValidated](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValidated_EV.html) event triggered when the cell has finished validating with valid data.

{% tabs %}
{% highlight c# %}
this.dataGrid.CurrentCellValidated += dataGrid_CurrentCellValidated;

void dataGrid_CurrentCellValidated(object sender, CurrentCellValidatedEventArgs args)
{
            
}
{% endhighlight %}
{% endtabs %}

### Row Validation

You can validate the row using [RowValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowValidating_EV.html) event when the cell is edited. The `RowValidating` event occurs when the edited cells tries to commit the row data or lose the focus.
 
[RowValidatingEventArgs](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.RowValidatingEventArgs.html) provides information to `RowValidtaing` event for validating row. `RowValidatingEventArgs.OriginalSender` returns the DataGrid fired this event for DetailsView. 

`RowValidatingEventArgs.RowData` returns the edited value and you can set the validation status using `RowValidatingEventArgs.IsValid` property.

{% tabs %}
{% highlight c# %}
this.dataGrid.RowValidating += dataGrid_RowValidating;

void dataGrid_RowValidating(object sender, RowValidatingEventArgs args)
{
    var data = args.RowData.GetType().GetProperty("CustomerID").GetValue(args.RowData);
    if(data.ToString().Equals("AROUT"))
    {                
        args.IsValid = false;
        args.ErrorMessages.Add("CustomerID", "Customer AROUT cannot be passed");
    }
}
{% endhighlight %}
{% endtabs %}

[SfDataGrid.RowValidated](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowValidated_EV.html) event triggered when the row has finished validating with valid row data.

{% tabs %}
{% highlight c# %}
this.dataGrid.RowValidated += dataGrid_RowValidated;   

void dataGrid_RowValidated(object sender, RowValidatedEventArgs args)
{
            
}
{% endhighlight %}
{% endtabs %}

## Error icon and tip customization

### Customizing error icon

You can customize the error icon by editing `GridCell` style.

#### Change the shape of error icon

You can change the validation error template shape of the GridCell by changing the `Data` property of the path in the `PART_InValidCellBorder` of GridCell.

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
                    <VisualStateManager.VisualStateGroups>
                    
                        <VisualStateGroup x:Name="IndicationStates">  
                                              
                            <VisualState x:Name="HasError">                            
                                <Storyboard>
                                    <DoubleAnimationUsingKeyFrames Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="Width">
                                        <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                        <EasingDoubleKeyFrame KeyTime="0" Value="10" />
                                    </DoubleAnimationUsingKeyFrames>
                                    <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" 
                                                                   Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="(UIElement.Visibility)">
                                        <DiscreteObjectKeyFrame KeyTime="00:00:00" Value="{x:Static Visibility.Visible}"/>
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                            <VisualState x:Name="NoError">
                                <Storyboard BeginTime="0">
                                    <DoubleAnimationUsingKeyFrames Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="Width">
                                        <EasingDoubleKeyFrame KeyTime="0" Value="1" />
                                        <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                    </DoubleAnimationUsingKeyFrames>
                                    <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" 
                                                                   Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="(UIElement.Visibility)">
                                        <DiscreteObjectKeyFrame KeyTime="00:00:00" Value="{x:Static Visibility.Collapsed}"/>
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>  
                                                      
                        </VisualStateGroup>
                        
                        <VisualStateGroup x:Name="BorderStates">
                        
                            <VisualState x:Name="NormalCell"/>
                            
                            <VisualState x:Name="FrozenColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											Value="0,0,1,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>                                
                            </VisualState>
                            
                            <VisualState x:Name="FooterColumnCell">                            
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="1,0,1,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                            <VisualState x:Name="BeforeFooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="0,0,0,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                        </VisualStateGroup>
                                                
                    </VisualStateManager.VisualStateGroups>
                    
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
						    BorderBrush="{TemplateBinding CurrentCellBorderBrush}"
						    BorderThickness="{TemplateBinding CurrentCellBorderThickness}"
						    IsHitTestVisible="False"
						    SnapsToDevicePixels="True"
						    Margin="0,0,1,1"
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
                        <Path Data="M15.396557,23.044006C14.220558,23.044006 13.268559,23.886993 13.268559,24.927994 13.268559,25.975006 14.220558,26.817001 15.396557,26.817001 16.572557,26.817001 17.523547,25.975006 17.523547,24.927994 17.523547,23.886993 16.572557,23.044006 15.396557,23.044006z M15.467541,5.1819992C15.447552,5.1819992 15.436566,5.1829987 15.436566,5.1829987 13.118533,5.5049973 13.055545,7.3330002 13.055545,7.3330002L13.055545,9.2929993 13.626531,16.539001C13.983558,18.357002 14.243538,19.020004 14.243538,19.020004 15.275555,19.975006 16.203567,19.25 16.203567,19.25 16.976548,18.565994 17.028552,16.962997 17.028552,16.962997 17.956563,9.2929993 17.696553,7.1029968 17.696553,7.1029968 17.608571,5.2839966 15.823561,5.1849976 15.490551,5.1819992 15.481549,5.1819992 15.473553,5.1819992 15.467541,5.1819992z M15.56355,0C15.56355,0 21.710574,4.1259995 31.581613,2.8030014 31.581613,2.8030014 33.634629,26.556992 15.56355,32 15.56355,32 -0.10249132,27.548004 0.00050565118,2.9670029 0.0005058694,2.9670029 10.72555,3.6309967 15.56355,0z"
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

![](Data-Validation_images/Data-Validation_img3.png)

#### Change the color of error icon

You can change the validation error template color of the GridCell by changing the `Fill` property of the path in the `PART_InValidCellBorder` of GridCell.

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
                    <VisualStateManager.VisualStateGroups>
                        <VisualStateGroup x:Name="IndicationStates">

                            <VisualState x:Name="HasError">
                                <Storyboard>
                                    <DoubleAnimationUsingKeyFrames Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="Width">
                                        <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                        <EasingDoubleKeyFrame KeyTime="0" Value="10" />
                                    </DoubleAnimationUsingKeyFrames>
                                    <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" 
                                                                   Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="(UIElement.Visibility)">
                                        <DiscreteObjectKeyFrame KeyTime="00:00:00" Value="{x:Static Visibility.Visible}"/>
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="NoError">
                                <Storyboard BeginTime="0">
                                    <DoubleAnimationUsingKeyFrames Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="Width">
                                        <EasingDoubleKeyFrame KeyTime="0" Value="1" />
                                        <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                    </DoubleAnimationUsingKeyFrames>
                                    <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" 
                                                                   Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="(UIElement.Visibility)">
                                        <DiscreteObjectKeyFrame KeyTime="00:00:00" Value="{x:Static Visibility.Collapsed}"/>
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                        </VisualStateGroup>
                        
                        <VisualStateGroup x:Name="BorderStates">
                            <VisualState x:Name="NormalCell"/>
                            <VisualState x:Name="FrozenColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="0,0,1,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                            <VisualState x:Name="FooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="1,0,1,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                            <VisualState x:Name="BeforeFooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="0,0,0,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                        </VisualStateGroup>
                        
                    </VisualStateManager.VisualStateGroups>
                    
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
						    BorderBrush="{TemplateBinding CurrentCellBorderBrush}"
						    BorderThickness="{TemplateBinding CurrentCellBorderThickness}"
						    IsHitTestVisible="False"
						    SnapsToDevicePixels="True"
						    Margin="0,0,1,1"
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
	                          Fill="Orange"
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

![](Data-Validation_images/Data-Validation_img4.png)

#### Change the cursor on error icon

You can change the validation error template cursor of the GridCell by changing the `Cursor` property of the path codes in the `PART_InValidCellBorder` of GridCell.

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
                    <VisualStateManager.VisualStateGroups>
                    
                        <VisualStateGroup x:Name="IndicationStates">

                            <VisualState x:Name="HasError">
                                <Storyboard>
                                    <DoubleAnimationUsingKeyFrames Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="Width">
                                        <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                        <EasingDoubleKeyFrame KeyTime="0" Value="10" />
                                    </DoubleAnimationUsingKeyFrames>
                                    <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" 
                                                                   Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="(UIElement.Visibility)">
                                        <DiscreteObjectKeyFrame KeyTime="00:00:00" Value="{x:Static Visibility.Visible}"/>
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>

                            <VisualState x:Name="NoError">
                                <Storyboard BeginTime="0">
                                    <DoubleAnimationUsingKeyFrames Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="Width">
                                        <EasingDoubleKeyFrame KeyTime="0" Value="1" />
                                        <EasingDoubleKeyFrame KeyTime="0" Value="0" />
                                    </DoubleAnimationUsingKeyFrames>
                                    <ObjectAnimationUsingKeyFrames BeginTime="00:00:00" 
                                                                   Storyboard.TargetName="PART_InValidCellBorder" 
                                                                   Storyboard.TargetProperty="(UIElement.Visibility)">
                                        <DiscreteObjectKeyFrame KeyTime="00:00:00" Value="{x:Static Visibility.Collapsed}"/>
                                    </ObjectAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                        </VisualStateGroup>
                        
                        <VisualStateGroup x:Name="BorderStates">
                        
                            <VisualState x:Name="NormalCell"/>
                            
                            <VisualState x:Name="FrozenColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="0,0,1,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                            <VisualState x:Name="FooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="1,0,1,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                            <VisualState x:Name="BeforeFooterColumnCell">
                                <Storyboard BeginTime="0">
                                    <ThicknessAnimationUsingKeyFrames BeginTime="0"
										                              Duration="1"
										                              Storyboard.TargetName="PART_GridCellBorder"
										                              Storyboard.TargetProperty="BorderThickness">
                                        <EasingThicknessKeyFrame KeyTime="0"
											                     Value="0,0,0,1"/>
                                    </ThicknessAnimationUsingKeyFrames>
                                </Storyboard>
                            </VisualState>
                            
                        </VisualStateGroup>
                        
                    </VisualStateManager.VisualStateGroups>
                    
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
						    BorderBrush="{TemplateBinding CurrentCellBorderBrush}"
						    BorderThickness="{TemplateBinding CurrentCellBorderThickness}"
						    IsHitTestVisible="False"
						    SnapsToDevicePixels="True"
						    Margin="0,0,1,1"
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
                              Cursor="Hand"
                              Stretch="Fill" />

                    </Border>
                </Grid>
            </ControlTemplate>
        </Setter.Value>
    </Setter>
</Style>
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img5.png)

### Customizing error tip

You can customize the error tip by editing the style of `ValidationToolTipTemplate`. Get the style of `ValidationToolTipTemplate` by editing the GridCell style.

#### Change the background and foreground color of error tip

You can change the error tip background color by setting `Background` property of the border in `ValidationToolTipTemplate`. The error tip foreground color can be changed by setting `Foreground` property of the TextBlock in `ValidationTolTipTemplate`.

{% tabs %}
{% highlight xaml %}
<ControlTemplate x:Key="ValidationToolTipTemplate">
    <Grid x:Name="Root"
		  Margin="5,0"
		  Opacity="0"
		  RenderTransformOrigin="0,0">
        <Grid.RenderTransform>
            <TranslateTransform x:Name="xform" X="-25" />
        </Grid.RenderTransform>
        <VisualStateManager.VisualStateGroups>
        
            <VisualStateGroup x:Name="OpenStates">
            
                <VisualStateGroup.Transitions>
                
                    <VisualTransition GeneratedDuration="0" />
                    
                    <VisualTransition GeneratedDuration="0:0:0.2" To="Open">
                        <Storyboard>
                            <DoubleAnimation Duration="0:0:0.2"
								             Storyboard.TargetName="xform"
								             Storyboard.TargetProperty="X"
								             To="0">
                                <DoubleAnimation.EasingFunction>
                                    <BackEase Amplitude=".3" EasingMode="EaseOut" />
                                </DoubleAnimation.EasingFunction>
                            </DoubleAnimation>
                            <DoubleAnimation Duration="0:0:0.2"
								Storyboard.TargetName="Root"
								Storyboard.TargetProperty="Opacity"
								To="1" />
                        </Storyboard>
                    </VisualTransition>
                </VisualStateGroup.Transitions>
                
                <VisualState x:Name="Closed">
                    <Storyboard>
                        <DoubleAnimation Duration="0"
							             Storyboard.TargetName="Root"
							             Storyboard.TargetProperty="Opacity"
							             To="0" />
                    </Storyboard>
                </VisualState>
                
                <VisualState x:Name="Open">
                    <Storyboard>
                        <DoubleAnimation Duration="0"
							             Storyboard.TargetName="xform"
							             Storyboard.TargetProperty="X"
							             To="0" />
                        <DoubleAnimation Duration="0"
							             Storyboard.TargetName="Root"
							             Storyboard.TargetProperty="Opacity"
							             To="1" />
                    </Storyboard>
                </VisualState>
                
            </VisualStateGroup>
            
        </VisualStateManager.VisualStateGroups>

        <Border Margin="4,4,-4,-4"
			    Background="#052A2E31"
			    CornerRadius="5" />
        <Border Margin="3,3,-3,-3"
			    Background="#152A2E31"
			    CornerRadius="4" />
        <Border Margin="2,2,-2,-2"
			    Background="#252A2E31"
			    CornerRadius="3" />
        <Border Margin="1,1,-1,-1"
			    Background="#352A2E31"
			    CornerRadius="2" />

        <Border Background="Orange" CornerRadius="2" />
        <Border CornerRadius="2">
            <TextBlock MaxWidth="250"
                       Margin="8,4,8,4"
                       Foreground="Black"
                       Text="{TemplateBinding Tag}"
                       TextWrapping="Wrap"
                       UseLayoutRounding="false" />
        </Border>
    </Grid>
</ControlTemplate>
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img6.png)

### Showing error details in RowHeader

SfDataGrid support to show the error icon in [GridRowHeaderCell](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridRowHeaderCell.html) based on [IDataErrorInfo.Error](https://msdn.microsoft.com/en-us/library/system.componentmodel.idataerrorinfo.error.aspx) or [INotifyDataErrorInfo.HasErrors](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.haserrors.aspx) property.

#### Using IDataErrorInfo

You can show the error information in row header by setting [IDataErrorInfo.Error](https://msdn.microsoft.com/en-us/library/system.componentmodel.idataerrorinfo.error.aspx). `IDataErrorInfo.Error` will be displayed as error message in tooltip.

{% tabs %}
{% highlight c# %}
[Display(AutoGenerateField = false)]
public string Error
{
    get
    {
        if (this.Country.Contains("Germany") || this.Country.Contains("UK"))
            return "Delivery not available for the country " + this.Country;

        return string.Empty;
    }
}
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img7.png)

#### Using INotifyDataErrorInfo

You can show the error information in row header by setting [INotifyDataErrorInfo.HasErrors](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.haserrors.aspx). By default error message “Row Containing Error” will be displayed.  You can change this by changing `RowErrorMessage` in the **resx** file.

{% tabs %}
{% highlight c# %}
[Display(AutoGenerateField = false)]
public bool HasErrors
{
    get
    {
        if (this.ShipCity.Contains("México D.F."))
            return true;
        return false;
    }
}
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img8.png)

## Validation with Master-Details View

Master-Details View allows you to [validate](#_Data_Validation) the bound data is valid or not. 
You can do both built-in and custom validation of data in `DetailsViewDataGrid`.

### Built-in validations

You can validate the bound data based on [IDataErrorInfo](https://msdn.microsoft.com/en-us/library/system.componentmodel.idataerrorinfo.aspx)/[INotifyDataErrorInfo](https://msdn.microsoft.com/en-us/library/system.componentmodel.inotifydataerrorinfo.aspx) or [Data Annotation](https://msdn.microsoft.com/en-us/library/system.componentmodel.dataannotations.aspx) Attributes by setting [GridValdiationMode](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~GridValidationMode.html) property of [ViewDefinition.DataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridViewDefinition~DataGrid.html).

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"                                  
                       NavigationMode="Cell"
                       AutoGenerateColumns="True"                              
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="ProductDetails">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="FirstLevelNestedGrid" 
                                       GridValidationMode="InView"                                                                                         
                                       AutoGenerateColumns="True">                                                                                  
                </syncfusion:SfDataGrid>
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

When the relation is auto-generated, the data can be validated by setting `GridValdiationMode` property to `AutoGeneratingRelations.GridvIewDefinition.DataGrid` in [AutoGeneratingRelations](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGeneratingRelations_EV.html) event handler.

{% tabs %}
{% highlight c# %}
dataGrid.AutoGenerateRelations = true;

dataGrid.AutoGeneratingRelations +=dataGrid_AutoGeneratingRelations;

void dataGrid_AutoGeneratingRelations(object sender, Syncfusion.UI.Xaml.Grid.AutoGeneratingRelationsArgs e)
{
    e.GridViewDefinition.DataGrid.GridValidationMode = GridValidationMode.InView;
}
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img9.png)

### Custom validation through events

Master-Details View support to validate the cells and rows using [CurrentCellValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValidating_EV.html) and [RowValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowValidating_EV.html) events.

#### Cell Validation

You can validate the cells using [CurrentCellValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValidating_EV.html) event of [ViewDefinition.DataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridViewDefinition~DataGrid.html) when the cell is edited. `CurrentCellValdiating` event occurs when the edited cells tries to commit the data or lose the focus. 

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"                                  
                       NavigationMode="Cell"                           
                       AutoGenerateColumns="True"                              
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="ProductDetails">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="FirstLevelNestedGrid"  
                                       AllowEditing="True"                                                                  CurrentCellValidating="FirstLevelNestedGrid_CurrentCellValidating"                                       
                                       AutoGenerateColumns="True">                                                                                                      
                </syncfusion:SfDataGrid>
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

<br/>

{% tabs %}
{% highlight c# %}
this.FirstLevelNestedGrid.CurrentCellValidating +=FirstLevelNestedGrid_CurrentCellValidating;

private void FirstLevelNestedGrid_CurrentCellValidating(object sender, CurrentCellValidatingEventArgs args)
{
    if(args.NewValue.ToString().Equals("Bike2"))
    {
        args.IsValid = false;
        args.ErrorMessage = "Order ID 1002 not ordererd Bike2";
    }
}
{% endhighlight %}
{% endtabs %}

[CurrentCellValidated](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~CurrentCellValidated_EV.html) event [ViewDefinition.DataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridViewDefinition~DataGrid.html) triggered when the cell has finished validating with valid data

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"                                  
                       NavigationMode="Cell"                                                 
                       AutoGenerateColumns="True"                              
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="ProductDetails">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="FirstLevelNestedGrid"  
                                       AllowEditing="True"                                                                              CurrentCellValidated="FirstLevelNestedGrid_CurrentCellValidated"                                       
                                       AutoGenerateColumns="True">                                                                                  
                </syncfusion:SfDataGrid>
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}

<br/>

{% tabs %}
{% highlight c# %}
this.FirstLevelNestedGrid.CurrentCellValidated +=FirstLevelNestedGrid_CurrentCellValidated;

private void FirstLevelNestedGrid_CurrentCellValidated(object sender, CurrentCellValidatedEventArgs args)
{

}
{% endhighlight %}
{% endtabs %}

When the relation is auto-generated, you can wire the `CurrentCellValidating` and `CurrentCellValidated` events for `AutoGeneratingRelations.GridvIewDefinition.DataGrid` in [AutoGeneratingRelations](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGeneratingRelations_EV.html) event handler.

{% tabs %}
{% highlight c# %}
dataGrid.AutoGenerateRelations = true;

dataGrid.AutoGeneratingRelations +=dataGrid_AutoGeneratingRelations;

void dataGrid_AutoGeneratingRelations(object sender, Syncfusion.UI.Xaml.Grid.AutoGeneratingRelationsArgs e)
{
    e.GridViewDefinition.DataGrid.CurrentCellValidating += FirstLevelNestedGrid_CurrentCellValidating;
    e.GridViewDefinition.DataGrid.CurrentCellValidated += FirstLevelNestedGrid_CurrentCellValidated;
}
{% endhighlight %}
{% endtabs %}

#### Row Validation
 
You can validate the row using [RowValidating](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowValidating_EV.html) event of [ViewDefinition.DataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridViewDefinition~DataGrid.html) when the cell is edited. 

The `RowValidating` event occurs when edited cells tries to commit the row data or lose the focus. 

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"                                  
                       NavigationMode="Cell"
                       AutoGenerateColumns="True"                              
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="ProductDetails">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="FirstLevelNestedGrid"  
                                       AllowEditing="True"                                                                              RowValidating="FirstLevelNestedGrid_RowValidating"
                                       AutoGenerateColumns="True">                                                                                  
                </syncfusion:SfDataGrid>
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}
<br/>
{% tabs %}
{% highlight c# %}
this.FirstLevelNestedGrid.RowValidating +=FirstLevelNestedGrid_RowValidating;

private void FirstLevelNestedGrid_RowValidating(object sender, RowValidatingEventArgs args)
{
    var data = args.RowData.GetType().GetProperty("ProductName").GetValue(args.RowData);
    if (data.ToString().Equals("Bike1"))
    {
        args.IsValid = false;
        args.ErrorMessages.Add("ProductName", "Product Bike 1 cannot be orderer for OrderID 1002");
    }
}
{% endhighlight %}
{% endtabs %}

[RowValidated](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~RowValidated_EV.html) of [ViewDefinition.DataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridViewDefinition~DataGrid.html) event triggered when the row has finished validating with valid row data.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfDataGrid x:Name="dataGrid"                                  
                       NavigationMode="Cell"
                       AutoGenerateColumns="True"                              
                       ItemsSource="{Binding Orders}">
    <syncfusion:SfDataGrid.DetailsViewDefinition>
        <syncfusion:GridViewDefinition RelationalColumn="ProductDetails">
            <syncfusion:GridViewDefinition.DataGrid>
                <syncfusion:SfDataGrid x:Name="FirstLevelNestedGrid"  
                                       AllowEditing="True"                                                                                                                    
                                       RowValidated="FirstLevelNestedGrid_RowValidated"
                                       AutoGenerateColumns="True">                                                                                                  </syncfusion:SfDataGrid>
            </syncfusion:GridViewDefinition.DataGrid>
        </syncfusion:GridViewDefinition>
    </syncfusion:SfDataGrid.DetailsViewDefinition>
</syncfusion:SfDataGrid>
{% endhighlight %}
{% endtabs %}
<br/>
{% tabs %}
{% highlight c# %}
this.FirstLevelNestedGrid.RowValidated +=FirstLevelNestedGrid_RowValidated;

private void FirstLevelNestedGrid_RowValidated(object sender, RowValidatedEventArgs args)
{

}
{% endhighlight %}
{% endtabs %}

When the relation is auto-generated, you can wire the `RowValidating` and `RowValidated` events for `AutoGeneratingRelations.GridvIewDefinition.DataGrid` in [AutoGeneratingRelations](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.SfDataGrid~AutoGeneratingRelations_EV.html) event handler.

{% tabs %}
{% highlight c# %}
dataGrid.AutoGenerateRelations = true;

dataGrid.AutoGeneratingRelations +=dataGrid_AutoGeneratingRelations;

void dataGrid_AutoGeneratingRelations(object sender, Syncfusion.UI.Xaml.Grid.AutoGeneratingRelationsArgs e)
{
    e.GridViewDefinition.DataGrid.RowValidating += FirstLevelNestedGrid_RowValidating;
    e.GridViewDefinition.DataGrid.RowValidated += FirstLevelNestedGrid_RowValidated;
}
{% endhighlight %}
{% endtabs %}

## Validation with Checkbox column

SfDataGrid doesn’t support to validate the [GridCheckBoxColumn](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCheckBoxColumn.html) through validating events. 

You can validate the check box column value by setting `ValidationHelper.IsCurrentCellValidated` and `ValidationHelper.IsCurrentRowValidated` static properties by calling [SetCurrentRowValdiated](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.ValidationHelper~SetCurrentRowValidated.html) and [SetCurrentCellValidated](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.ValidationHelper~SetCurrentCellValidated.html) methods from [ValidationHelper](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.ValidationHelper.html).

{% tabs %}
{% highlight c# %}
using Syncfusion.UI.Xaml.Grid.Helpers;

this.dataGrid.CurrentCellValueChanged += dataGrid_CurrentCellValueChanged;

void dataGrid_CurrentCellValueChanged(object sender, CurrentCellValueChangedEventArgs args)
{
    int columnIndex = this.dataGrid.ResolveToGridVisibleColumnIndex(args.RowColumnIndex.ColumnIndex);

    //We are enabling the RowValidating, CellValidating event if the changes happen in GridCheckBoxColumn
    if (this.dataGrid.Columns[columnIndex].CellType == "CheckBox")
    {
        this.dataGrid.GetValidationHelper().SetCurrentRowValidated(false);
        this.dataGrid.GetValidationHelper().SetCurrentCellValidated(false);
    }
}
{% endhighlight %}
{% endtabs %}

![](Data-Validation_images/Data-Validation_img10.png)

## Limitations
 
1. Non editable columns will not support custom validation except [GridCheckBoxColumn](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridCheckBoxColumn.html).
2. `CurrentCellValidating` event will not triggered for [GridTemplateColumn](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridTemplateColumn.html) and [GridUnboundColumn](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridUnBoundColumn.html). 
