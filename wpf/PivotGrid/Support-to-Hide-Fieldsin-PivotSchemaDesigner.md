---
layout: post
title: 1369-Support-to-Hide-Fields-in-PivotSchemaDesigner
description:             1.3.6.9 support to hide fields in pivotschemadesigner 
platform: wpf
control: PivotGridControl
documentation: ug
---

# Hiding Fields in PivotSchemaDesigner

It is possible to hide the unnecessary fields from the PivotTable Field List using `ShowDisplayFieldsOnly` property.

If through *XAML*, please refer the below code sample.

{% highlight xaml %}

    <Grid>
        <Grid.ColumnDefinitions>
            <ColumnDefinition Width="*" />
            <ColumnDefinition Width=".35*" />
        </Grid.ColumnDefinitions>
        <syncfusion:PivotGridControl HorizontalAlignment="Left" Name="pivotGrid" VerticalAlignment="Top" VisualStyle="Metro" EnableValueEditing="True" ItemSource="{Binding   Source={StaticResource data}}">

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

        </syncfusion:PivotGridControl>

        <syncfusion:PivotSchemaDesigner Grid.Column="1" Name="shemaDesginer" ShowDisplayFieldsOnly="True" VisualStyle="Metro" PivotControl="{Binding ElementName=pivotGrid}"></syncfusion:PivotSchemaDesigner>
    </Grid>

{% endhighlight %}

Else if through *Code-Behind*, please refer the below code sample.

{% highlight C# %}

public partial class MainWindow: Window {
    PivotGridControl pivotGrid = new PivotGridControl();
    PivotSchemaDesigner schemaDesigner = new PivotSchemaDesigner();
    public MainWindow() {
        InitializeComponent();
        grid1.Children.Add(pivotGrid);
        pivotGrid.ItemSource = ProductSales.GetSalesData();
        PivotItem m_PivotItem = new PivotItem() {
            FieldHeader = "Product", FieldMappingName = "Product", TotalHeader = "Total"
        };
        PivotItem m_PivotItem1 = new PivotItem() {
            FieldHeader = "Date", FieldMappingName = "Date", TotalHeader = "Total"
        };
        PivotItem n_PivotItem = new PivotItem() {
            FieldHeader = "Country", FieldMappingName = "Country", TotalHeader = "Total"
        };
        PivotItem n_PivotItem1 = new PivotItem() {
            FieldHeader = "State", FieldMappingName = "State", TotalHeader = "Total"
        };
        // Adding PivotItem to PivotRows
        pivotGrid.PivotRows.Add(m_PivotItem);
        pivotGrid.PivotRows.Add(m_PivotItem1);
        // Adding PivotItem to PivotColumns
        pivotGrid.PivotColumns.Add(n_PivotItem);
        pivotGrid.PivotColumns.Add(n_PivotItem1);
        PivotComputationInfo m_PivotComputationInfo = new PivotComputationInfo() {
            CalculationName = "Amount", FieldName = "Amount", Format = "C", SummaryType = Syncfusion.PivotAnalysis.Base.SummaryType.DoubleTotalSum
        };
        PivotComputationInfo m_PivotComputationInfo1 = new PivotComputationInfo() {
            CalculationName = "Quantity", FieldName = "Quantity", SummaryType = Syncfusion.PivotAnalysis.Base.SummaryType.Count
        };
        pivotGrid.PivotCalculations.Add(m_PivotComputationInfo);
        pivotGrid.PivotCalculations.Add(m_PivotComputationInfo1);

        schemaDesigner.PivotControl = pivotGrid;
        schemaDesigner.ShowDisplayFieldsOnly = true;
        grid1.Children.Add(schemaDesigner);
        Grid.SetColumn(schemaDesigner, 1);
    }
}

{% endhighlight %}

![](PivotSchemaDesigner-Images/PivotTableFieldList when enabled showsdisplayfields only.png)

_PivotSchemaDesigner with ShowDisplayFieldsOnly_

![](PivotSchemaDesigner-Images/PivotTableFieldList when disbled showsdisplayfields only.png)

_PivotSchemaDesigner without ShowDisplayFieldsOnly_