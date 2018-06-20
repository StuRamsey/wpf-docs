---
layout: post
title: ExportToExcel in SfDataGrid.
description: How to export the SfDataGrid to excel.
platform: wpf
control: SfDataGrid
documentation: ug
---

# Export to Excel

SfDataGrid provides support to export data to excel. It also provides support for grouping, filtering, sorting, paging, unbound rows, merged cells, stacked headers and Details View while exporting.

The following assemblies needs to be added for exporting to excel.

* Syncfusion.SfGridConverter.WPF
* Syncfusion.XlsIO.Base

You can export SfDataGrid to excel by using the [ExportToExcel](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.GridExcelExportExtension~ExportToExcel.html) extension method present in the [Syncfusion.UI.Xaml.Grid.Converter](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/webtoc.html) namespace.

{% tabs %}
{% highlight c# %}
using Syncfusion.UI.Xaml.Grid.Converter;
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

N> SfDataGrid exports data to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating exported work sheets. 

## Exporting options

Exporting operation can be customized by passing [ExcelExportingOptions](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions.html) instance as argument to `ExportToExcel` method. 

### Export Mode

By default, actual value only will be exported to excel. If you want to export the display text, you need to set [ExportMode](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportMode.html) property as `Text`. 

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportMode = ExportMode.Text;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Export groups with outlines

By default, all the groups in dataGrid will be exported in expanded state. You can enable outlines in excel based on groups by setting the [AllowOutlining](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~AllowOutlining.html) property as `true` in [ExcelExportingOptions](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions.html). 

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.AllowOutlining = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img1.png)

### Exclude columns while exporting

By default, all the columns (including hidden columns) in SfDataGrid will be exported to Excel. If you want to exclude some columns while exporting to Excel, you can use [ExcludeColumns](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExcludeColumns.html) field in [ExcelExportingOptions](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions.html).

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcludeColumns.Add("CustomerName");
options.ExcludeColumns.Add("Country");
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

Here, the columns having `CustomerName` and `Country` as MappingName are excluded while exporting.

### Excel Version

While exporting to Excel, you can specify the excel version by using [ExcelVersion](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExcelVersion.html) property.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Exporting stacked headers

You can export stacked headers to excel by setting [ExportStackedHeaders](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportStackedHeaders.html) property to `true`.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportStackedHeaders = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Exporting merged cells

You can export merged cells to excel by setting [ExportMergedCells](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportMergedCells.html) property as `true`.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportMergedCells = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Exporting unbound rows

You can export unbound rows to excel by setting [ExportUnBoundRows](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportUnBoundRows.html) property as `true`.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportUnBoundRows = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Changing start row and column index while exporting

You can export the data to specified row index and column index in worksheet, by setting [StartRowIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~StartRowIndex.html) and [StartColumnIndex](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~StartColumnIndex.html) properties.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.StartColumnIndex = 3;
options.StartRowIndex = 3;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img2.png)

## Saving options

### Save directly to file

After exporting to excel, you can save exported workbook directly to file system by using [SaveAs](https://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.IWorkbook~SaveAs.html) method.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Save as stream

After exporting to excel, you can save exported workbook to stream by using [SaveAs](https://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.IWorkbook~SaveAs.html) method.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
FileStream fileStream = new FileStream("Output.xlsx", FileMode.Create);
workBook.SaveAs(fileStream);
{% endhighlight %}
{% endtabs %}

You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/faq). 

### Save using File dialog

After exporting to excel, you can save exported workbook by opening [FileDialog](https://msdn.microsoft.com/en-us/library/system.windows.forms.filedialog.aspx). 

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];

SaveFileDialog sfd = new SaveFileDialog
{
    FilterIndex = 2,
    Filter = "Excel 97 to 2003 Files(*.xls)|*.xls|Excel 2007 to 2010 Files(*.xlsx)|*.xlsx|Excel 2013 File(*.xlsx)|*.xlsx"
};

if (sfd.ShowDialog() == true)
{
    using (Stream stream = sfd.OpenFile())
    {

        if (sfd.FilterIndex == 1)
            workBook.Version = ExcelVersion.Excel97to2003;

        else if (sfd.FilterIndex == 2)
            workBook.Version = ExcelVersion.Excel2010;

        else
            workBook.Version = ExcelVersion.Excel2013;
        workBook.SaveAs(stream);
    }

    //Message box confirmation to view the created workbook.

    if (MessageBox.Show("Do you want to view the workbook?", "Workbook has been created",
                        MessageBoxButton.YesNo, MessageBoxImage.Information) == MessageBoxResult.Yes)
    {

        //Launching the Excel file using the default Application.[MS Excel Or Free ExcelViewer]
        System.Diagnostics.Process.Start(sfd.FileName);
    }
}
{% endhighlight %}
{% endtabs %}

## Opening exported excel without saving

You can open the exported workbook without saving by using [SfSpreadsheet](http://help.syncfusion.com/wpf/sfspreadsheet) control.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
Window window1 = new Window();
SfSpreadsheet spreadsheet = new SfSpreadsheet();
spreadsheet.Open(workBook);
window1.Content = spreadsheet;
window1.Show();
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img3.png)

## Export Paging

While exporting data to excel, if paging is used, current page only will be exported, by default. If you want to export all pages, you need to set [ExportAllPages](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportAllPages.html) property as `true`.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportAllPages = true;            
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

By default, all data will be exported to single sheet. If you want to export each page to different sheets, you need to use [ExportPageOptions](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportPageOptions.html) property.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportAllPages = true;
options.ExportPageOptions = ExportPageOptions.ExportToDifferentSheets;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

## Export SelectedItems to Excel

By default, entire grid will be exported to Excel. You can export selected items only by passing `SelectedItems` to 
[ExportToExcel](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.GridExcelExportExtension~ExportToExcel(SfDataGrid,ObservableCollection%7BObject%7D,ExcelExportingOptions,IWorksheet).html) method.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
ExcelEngine excelEngine = new ExcelEngine();
IWorkbook workBook = excelEngine.Excel.Workbooks.Create();
workBook.Worksheets.Create();
dataGrid.ExportToExcel(dataGrid.SelectedItems, options, workBook.Worksheets[0]);
workBook.Version = ExcelVersion.Excel2013;
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img4.png)

## Export to HTML

You can save exported workbook as HTML by using [SaveAsHtml](https://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.IWorkbook~SaveAsHtml.html) method.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAsHtml("Sample.html", HtmlSaveOptions.Default);
{% endhighlight %}
{% endtabs %}

It is also possible to save worksheet as HTML by using [SaveAsHtml](http://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.IWorkbook~SaveAsHtml.html) method. You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet#save-worksheet-as-html) for this.

## Export to Mail

You can export SfDataGrid to mail by converting it into Excel and save exported worksheet as HTML. Then exported HTML contents is embedded in mail body.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2010;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];

workBook.Worksheets[0].UsedRange.BorderInside(ExcelLineStyle.Thick, ExcelKnownColors.Black);
workBook.Worksheets[0].UsedRange.BorderAround(ExcelLineStyle.Thick, ExcelKnownColors.Black);
workBook.Worksheets[0].SaveAsHtml("test.htm", Syncfusion.XlsIO.Implementation.HtmlSaveOptions.Default);

System.Net.Mail.MailMessage myMessage = new System.Net.Mail.MailMessage();

myMessage.To.Add("Support@syncfusion.com");
myMessage.From = new MailAddress("Support@syncfusion.com");
myMessage.Priority = MailPriority.High;
myMessage.Subject = "Order Details";
myMessage.IsBodyHtml = true;
myMessage.Body = new StreamReader("test.htm").ReadToEnd();

SmtpClient client = new SmtpClient("smtp.office365.com", 587);

client.EnableSsl = true;
client.UseDefaultCredentials = false;
client.Credentials = new NetworkCredential("Support@syncfusion.com", "test");

int count = 0;

while (count < 3)
{

    try
    {
        client.Send(myMessage);
        count = 3;
    }

    catch (Exception ex)
    {
        Console.WriteLine(ex.Message);
        Console.WriteLine(String.Format("Sending Mail Attemp - {0}", count.ToString()));
        Thread.Sleep(60000);
        count++;
    }
}
Console.WriteLine("Mail has been sent...");
{% endhighlight %}
{% endtabs %}

## Export to XML

You can save exported workbook as `Xml` file also by using [SaveAsXml](https://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.IWorkbook~SaveAsXml.html) methods.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAsXml("Sample.xml", ExcelXmlSaveType.MSExcel);
{% endhighlight %}
{% endtabs %}

## Export to CSV

You can save exported workbook as CSV by using `SaveAs` method.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.csv", ",");
{% endhighlight %}
{% endtabs %}

Similarly, you can save exported worksheet also to CSV. You can refer [XlsIO documentation.](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet#save-worksheet-as-csv) 

## Row Height and Column Width customization 

After exporting data to excel, you can set different row height and column width for the columns based on your requirement. You can refer [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation#adjust-row-height-and-column-width) for more information. 

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].SetRowHeight(2, 50);
workBook.Worksheets[0].SetColumnWidth(2, 50);
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

## Styling cells based on CellType in Excel

You can customize the cell styles based on `CellType` by using [ExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ExportingEventHandler.html).

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExportingEventHandler = ExportingHandler;
options.AllowOutlining = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void ExportingHandler(object sender, GridExcelExportingEventArgs e)
{

      if (e.CellType == ExportCellType.HeaderCell)
      {
          e.CellStyle.BackGroundBrush = new SolidColorBrush(Colors.LightPink);
          e.CellStyle.ForeGroundBrush = new SolidColorBrush(Colors.White);
          e.Handled = true;
      }

      else if (e.CellType == ExportCellType.RecordCell)
      {
          e.CellStyle.BackGroundBrush = new SolidColorBrush(Colors.LightSkyBlue);
          e.Handled = true;
      }

      else if (e.CellType == ExportCellType.GroupCaptionCell)
      {
          e.CellStyle.BackGroundBrush = new SolidColorBrush(Colors.Wheat);
          e.Handled = true;
      }
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img5.png)

## Cell customization in Excel while exporting

You can customize the cells by setting [CellsExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html) in `ExcelExportingOptions`.

### Customize cell value while exporting

You can customize the call values while exporting to excel by using [CellsExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html) and `ExcelExportingOptions`.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.CellsExportingEventHandler = CellExportingHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void CellExportingHandler(object sender, GridCellExcelExportingEventArgs e)
{            

     // Based on the column mapping name and the cell type, we can change the cell 
                                          //values while exporting to excel.
     if (e.CellType == ExportCellType.RecordCell && e.ColumnName == "IsClosed")
     {

         //if the cell value is True, "Y" will be displayed else "N" will be displayed.

         if (e.CellValue.Equals(true))
             e.Range.Cells[0].Value = "Y";

         else
             e.Range.Cells[0].Value = "N";
         e.Handled = true;
      }
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img6.png)

Here, cell values are changed for `IsClosed` column based on custom condition.

### Changing row style in excel based on data

You can customize the rows based on the record values by using [CellsExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html).

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.CellsExportingEventHandler = CellExportingHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void CellExportingHandler(object sender, GridCellExcelExportingEventArgs e)
{           

     if (!(e.NodeEntry is RecordEntry))
        return;
     var record = e.NodeEntry as RecordEntry;

     if ((record.Data as OrderInfo).Country == "Mexico")
     {
         e.Range.CellStyle.ColorIndex = ExcelKnownColors.Green;
         e.Range.CellStyle.Font.Color = ExcelKnownColors.White;
     }
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img7.png)

Here, records having the `Country` name as `Mexico` are customized.

### Customize the cells based on Column Name

You can customize the cells based on [GridCellExcelExportingEventArgs.ColumnName](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.GridCellExcelExportingEventArgs~ColumnName.html) property in the [CellsExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~CellsExportingEventHandler.html).

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.CellsExportingEventHandler = CellExportingHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void CellExportingHandler(object sender, GridCellExcelExportingEventArgs e)
{

    if (e.ColumnName != "OrderID")
        return;

    e.Range.CellStyle.Font.Size = 12;
    e.Range.CellStyle.Font.Color = ExcelKnownColors.Pink;
    e.Range.CellStyle.Font.FontName = "Segoe UI";
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img8.png)

Here, `OrderID` column cells are customized while exporting.

## Customize exported workbook and worksheet

SfDataGrid exports to excel by using [XlsIO](http://help.syncfusion.com/file-formats/xlsio/overview). You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/working-with-excel-worksheet) for manipulating workbook and sheet after exporting. 

### Workbook
SfDataGrid provides option to return [ExcelEngine](https://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.ExcelEngine.html) from that you can get exported workbook. This allows you to protect, encrypt and add worksheet before saving. 

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();         
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

### Worksheet customization

SfDataGrid provides support to export to already existing file or worksheet. 

In the below code snippet, worksheet is created and passed to `ExportToExcel` method. In the same way, you can open already existing excel also using `XlsIO`. 

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
ExcelEngine excelEngine = new ExcelEngine();
IWorkbook workBook = excelEngine.Excel.Workbooks.Create();
dataGrid.ExportToExcel(dataGrid.View, options, workBook.Worksheets[0]);
workBook.Version = ExcelVersion.Excel2013;
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

Before saving workbook, you need to set the specific excel version by using [IWorkbook.Version](https://help.syncfusion.com/cr/cref_files/file-formats/xlsio/Syncfusion.XlsIO.Base~Syncfusion.XlsIO.IWorkbook~Version.html) property. Here, you can directly manipulate the data in the worksheet. You can refer [here](http://help.syncfusion.com/file-formats/xlsio/worksheet-rows-and-columns-manipulation) for more information.

#### Setting borders

You can set borders to excel cells by directly accessing worksheet after exporting data.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].UsedRange.BorderInside(ExcelLineStyle.Dash_dot, ExcelKnownColors.Black);
workBook.Worksheets[0].UsedRange.BorderAround(ExcelLineStyle.Dash_dot, ExcelKnownColors.Black);
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img9.png)

#### Enabling Filters

You can show filters in exported worksheet by enabling filter for the exported range in the worksheet.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].AutoFilters.FilterRange = workBook.Worksheets[0].UsedRange;
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img10.png)

While using `stacked headers`, you can specify the `range` based on Stacked headers count.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
options.ExportStackedHeaders = true;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
var range = "A" + (dataGrid.StackedHeaderRows.Count + 1).ToString() + ":" + workBook.Worksheets[0].UsedRange.End.AddressLocal;
excelEngine.Excel.Workbooks[0].Worksheets[0].AutoFilters.FilterRange = workBook.Worksheets[0].Range[range];
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

You can refer [XlsIO documentation](http://help.syncfusion.com/file-formats/xlsio/worksheet-cells-manipulation#data-filtering).

#### Customize the range of cells

You can customize the range of cells after exporting to excel by directly manipulating worksheet.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ExcelVersion = ExcelVersion.Excel2013;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.Worksheets[0].Range["A2:A6"].CellStyle.Color = System.Drawing.Color.LightSlateGray;
workBook.Worksheets[0].Range["A2:A6"].CellStyle.Font.Color = ExcelKnownColors.White;
workBook.SaveAs("Sample.xlsx");
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img11.png)

## Exporting DetailsView

By default, [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) will be exported to Excel. You can customize its exporting operation by using [ChildExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html).

### Excluding DetailsViewDataGrid while exporting

You can exclude particular `DetailsViewDataGrid` while exporting, by using the [ChildExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html) and [GridChildExportingEventArgs.Cancel](https://msdn.microsoft.com/en-us/library/system.componentmodel.canceleventargs.cancel.aspx) .

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.ChildExportingEventHandler = ChildExportingHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void ChildExportingHandler(object sender, GridChildExportingEventArgs e)
{
       var recordEntry = e.NodeEntry as RecordEntry;

       if ((recordEntry.Data as OrderInfo).OrderID == 1002)
          e.Cancel = true;
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img12.png)

Here, `DetailsViewDataGrid` is not exported for the parent record having `OrderID` as 1002.

### Excluding DetailsViewDataGrid columns from exporting

You can exclude [DetailsViewDataGrid](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.DetailsViewDataGrid.html) columns while exporting, by using [ChildExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html) and [GridChildExportingEventArgs.ExcludeColumns](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.GridChildExportingEventArgs~ExcludeColumns.html).

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();            
options.ChildExportingEventHandler = ChildExportingHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void ChildExportingHandler(object sender, GridChildExportingEventArgs e)
{            
      e.ExcludeColumns.Add("OrderID");
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img13.png)

Here, `OrderID` column is displayed in `DetailsViewDataGrid` and it is excluded while exporting to excel.

### Customizing DetailsViewDataGrid cells

Like parent DataGrid, You can customize the `DetailsViewDataGrid` cells also by using [CellsExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~ChildExportingEventHandler.html). Based on [GridCellExcelExportingEventArgs.GridViewDefinition](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.GridCellExcelExportingEventArgs~GridViewDefinition.html) property, you can identify the particular `DetailsViewDataGrid` and customize it.

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();
options.CellsExportingEventHandler = CellExportingHandler;
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
var workBook = excelEngine.Excel.Workbooks[0];
workBook.SaveAs("Sample.xlsx");

private static void CellExportingHandler(object sender, GridCellExcelExportingEventArgs e)
{

    if (e.GridViewDefinition == null || e.GridViewDefinition.RelationalColumn != "ProductDetails")
        return;

    if (e.ColumnName == "OrderID")
    {
        e.Range.CellStyle.Font.Size = 12;
        e.Range.CellStyle.Font.Color = ExcelKnownColors.Blue;
        e.Range.CellStyle.Font.FontName = "Segoe UI";
    }
}
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img14.png)


## Performance

Using [ExcelExportingOptions.CellsExportingEventHandler](http://help.syncfusion.com/cr/cref_files/wpf/sfgridconverter/Syncfusion.SfGridConverter.WPF~Syncfusion.UI.Xaml.Grid.Converter.ExcelExportingOptions~CellsExportingEventHandler.html) and changing settings for each cell will consume more memory and time consumption. So, avoid using `CellsExportingEventHandler` and instead of you can do the required settings in the exported sheet.
 
### Formatting column without using CellsExportingEventHandler

You can perform cell level customization such as row-level styling, formatting particular column in the exported worksheet. 

In the below code snippet, NumberFormat for `Unit Price` column is changed in the exported sheet after exporting without using CellsExportingEventHandler. 

Reference:
[http://help.syncfusion.com/file-formats/xlsio/working-with-cell-or-range-formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-cell-or-range-formatting)

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();                   
options.ExportMode = ExportMode.Value;                 
options.ExcelVersion = ExcelVersion.Excel2013;           
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];
workBook.ActiveSheet.Columns[4].NumberFormat = "0.0";
{% endhighlight %}
{% endtabs %}


![](Export-to-Excel_images/Export-to-Excel_img15.png)

### Alternate row styling without using CellsExportingEventHandler

In the below code snippet, the background color of rows in excel is changed based on row index using conditional formatting for better performance.

Reference:
[http://help.syncfusion.com/file-formats/xlsio/working-with-conditional-formatting](http://help.syncfusion.com/file-formats/xlsio/working-with-conditional-formatting)

{% tabs %}
{% highlight c# %}
var options = new ExcelExportingOptions();                   
options.ExportMode = ExportMode.Value;                 
options.ExcelVersion = ExcelVersion.Excel2013;           
var excelEngine = dataGrid.ExportToExcel(dataGrid.View, options);
IWorkbook workBook = excelEngine.Excel.Workbooks[0];

IConditionalFormats condition = workBook.ActiveSheet.Range[2,1,this.dataGrid.View.Records.Count+1,this.dataGrid.Columns.Count].ConditionalFormats;
IConditionalFormat condition1 = condition.AddCondition();
condition1.FormatType = ExcelCFType.Formula;
condition1.FirstFormula = "MOD(ROW(),2)=0";
condition1.BackColorRGB = System.Drawing.Color.Pink;
IConditionalFormat condition2 = condition.AddCondition();
condition2.FormatType = ExcelCFType.Formula;
condition2.FirstFormula = "MOD(ROW(),2)=1";
condition2.BackColorRGB = System.Drawing.Color.LightGray;
{% endhighlight %}
{% endtabs %}

![](Export-to-Excel_images/Export-to-Excel_img16.png)


