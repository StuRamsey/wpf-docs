---
layout: post
title: Disable toolbar items| PDF Viewer | Wpf | Syncfusion
description: disable toolbar items
platform: wpf
control: PDF Viewer
documentation: ug
---

# Disable toolbar items

To remove the toolbar altogther use PdfDocumentView control instead of PdfViewerControl as described in the [Load PDF without ToolStrip in viewer](https://help.syncfusion.com/wpf/pdfviewer/how-to/load-pdf-without-toolstrip-in-viewer) section. Individual toolbar items from the default toolbar of PDF Viewer can be removed selectively. The following code snippet illustrates disabling the open file button. 


{% tabs %}
{% highlight c# %}

private void MainWindow_Loaded(object sender, RoutedEventArgs e)
{
	//Get the instance of the toolbar using its template name

	DocumentToolbar toolbar = pdfViewerControl.Template.FindName("PART_Toolbar", pdfViewerControl) as DocumentToolbar;

	//Get the instance of the open file button using its template name

	Button openButton = (Button)toolbar.Template.FindName("PART_ButtonOpen", toolbar);

	//Set the visibility of the button to collapsed 

	openButton.Visibility = System.Windows.Visibility.Collapsed;
}

{% endhighlight %}


{% highlight vbnet %}

Private Sub Window_Loaded(sender As Object, e As RoutedEventArgs)

    'Get the instance of the toolbar using its template name
    Dim toolbar As DocumentToolbar = CType(pdfViewerControl.Template.FindName("PART_Toolbar", pdfViewerControl), DocumentToolbar)

    'Get the instance of the open file button using its template name
    Dim openButton As Button = CType(toolbar.Template.FindName("PART_ButtonOpen", toolbar), Button)

    'Set the visibility of the button to collapsed 
    openButton.Visibility = Visibility.Collapsed

End Sub

{% endhighlight %}
{% endtabs %}

Similarly other toolbar items can be disabled. The following table lists the template names of the rest of the toolbar items along with their respective types in the order they appear in the toolbar. 

<table>
<tr>
<th>Toolbar item</th>
<th>Template name</th>
<th>Type</th>
</tr>
<tr>
<td>Save button</td>
<td>PART_ButtonSave</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Print button</td>
<td>PART_ButtonPrint</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Navigation toolbar separator</td>
<td>Part_NavigationToolsSeparator</td>
<td>System.Windows.Shapes.Rectangle</td>
</tr>
<tr>
<td>First page button</td>
<td>PART_ButtonGoToFirstPage</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Previous page button</td>
<td>PART_ButtonGoToPreviousPage</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Current page number</td>
<td>PART_TextCurrentPageIndex</td>
<td>System.Windows.Controls.TextBox</td>
</tr>
<tr>
<td>Page count </td>
<td>PART_LableTotalPageCount</td>
<td>System.Windows.Controls.TextBlock</td>
</tr>
<tr>
<td>Next page button</td>
<td>PART_ButtonGoToNextPage</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Last page button</td>
<td>PART_ButtonGoToLastPage</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Zoom toolbar separator</td>
<td>Part_ZoomToolsSeparator_0</td>
<td>System.Windows.Shapes.Rectangle</td>
</tr>
<tr>
<td>Current zoom</td>
<td>PART_ComboBoxCurrentZoomLevel</td>
<td>System.Windows.Controls.ComboBox</td>
</tr>
<tr>
<td>Zoom in button</td>
<td>PART_ButtonZoomIn</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Zoom out button</td>
<td>PART_ButtonZoomOut</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Zoom toolbar separator</td>
<td>PART_ZoomToolsSeparator_1</td>
<td>System.Windows.Shapes.Rectangle</td>
</tr>
<tr>
<td>Fitwidth button</td>
<td>PART_ButtonFitWidth</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Fitpage button</td>
<td>PART_ButtonFitPage</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Annotation toolbar separator</td>
<td>PART_AnnotationToolsSeparator</td>
<td>System.Windows.Shapes.Rectangle</td>
</tr>
<tr>
<td>Ink button</td>
<td>PART_Ink</td>
<td>System.Windows.Controls.Primitives.ToggleButton</td>
</tr>
<tr>
<td>Highlight button</td>
<td>PART_Highlight</td>
<td>System.Windows.Controls.Primitives.ToggleButton</td>
</tr>
<tr>
<td>Underline button</td>
<td>PART_Underline</td>
<td>System.Windows.Controls.Primitives.ToggleButton</td>
</tr>
<tr>
<td>Strikethrough button</td>
<td>PART_Strikethrough</td>
<td>System.Windows.Controls.Primitives.ToggleButton</td>
</tr>
<tr>
<td>Shapes button</td>
<td>PART_Shapes</td>
<td>System.Windows.Controls.Primitives.ToggleButton</td>
</tr>
<tr>
<td>Text search button</td>
<td>PART_ButtonTextSearch</td>
<td>System.Windows.Controls.Button</td>
</tr>
<tr>
<td>Fill button</td>
<td>PART_Fill</td>
<td>System.Windows.Controls.Primitives.ToggleButton</td>
</tr>
</table>

The bookmark button on the left pane will be hidden when bookmark navigation feature is disabled using the below code snippet

{% tabs %}
{% highlight c# %}

pdfViewerControl.IsBookmarkEnabled = false;

{% endhighlight %}


{% highlight vbnet %}

pdfViewerControl.IsBookmarkEnabled = false;

{% endhighlight %}
{% endtabs %}
