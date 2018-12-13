---
layout: post
title:  Organize Pages using PDF Viewer WPF | Syncfusion
description: Rotate, delete and reorder pages of the PDF Document using Syncfusion PDF Viewer WPF.
platform: wpf
control: PDF Viewer
documentation: ug
---

# Organize pages

Organize pages support allows you to rotate, rearrange, and delete pages from a PDF document using a miniature preview of the PDF pages.

Use the following steps to organize the PDF page(s) in `PdfViewerControl`:

1.	Click the organize page button in the left pane, this displays the organize pages pane in the `PdfViewerControl`.

![Organize Page Button](OrganizePages_Images/OrganizePages_Image_0.png)

2.	You can rotate or delete a specific page using context menu that appears when hovering the mouse over the pages.

![Page toolbar](OrganizePages_Images/OrganizePages_Image_1.png)

3.	You can rotate or delete multiple pages using the organize pages toolbar.

![Organize Pages toolbar](OrganizePages_Images/OrganizePages_Image_2.png)

N> You can use Ctrl/Shift keys to select multiple pages. Also, you can select all pages using Ctrl+A shortcut key. You cannot delete all the pages from the document. 

4.	You can rearrange the page(s) by dragging and dropping them.

![Rearrange pages](OrganizePages_Images/OrganizePages_Image_3.png)

## Rotating PDF page(s)

You can rotate PDF page(s) in clockwise, anti-clockwise or to a specific angle using the `Rotate` method. Refer to the following code example to rotate a page from code behind.

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Rotating the pages with index 0 and 1 to 90 degree
    pdfviewer.PageOrganizer.Rotate(new int[]{0,1},Syncfusion.Pdf.PdfPageRotateAngle.RotateAngle90);
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
   'Rotating the pages with index 0 and 1 to 90 degree
   pdfviewer.PageOrganizer.Rotate(new int[]{0,1}, Syncfusion.Pdf.PdfPageRotateAngle.RotateAngle90)
End Sub

{% endhighlight %}
{% endtabs %}

### Rotating PDF page(s) Clockwise

You can rotate PDF page(s) clockwise using the `PageOrganizer.RotateClockwise` method. 

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Rotating the pages with index 0 and 1 in clockwise
    pdfviewer.PageOrganizer.RotateClockwise(new int[] { 0, 1 });
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Rotating the pages with index 0 and 1 in clockwise
    pdfviewer.PageOrganizer.RotateClockwise(new int[] { 0, 1 })
End Sub

{% endhighlight %}
{% endtabs %}

### Rotating PDF page(s) Counterclockwise

You can rotate PDF page(s) in counterclockwise using the `PageOrganizer.RotateCounterclockwise` method. 

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Rotating the pages with index 0 and 1 in counterclockwise
    pdfviewer.PageOrganizer.RotateCounterclockwise (new int[] { 0, 1 });
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Rotating the pages with index 0 and 1 in counterclockwise
    pdfviewer.PageOrganizer.RotateCounterclockwise (new int[] { 0, 1 })
End Sub

{% endhighlight %}
{% endtabs %}

## Rearranging PDF pages

You can rearrange the existing PDF document pages using the `ReArrange(int[])` method.  This method uses zero based start index. 

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Rearrange the page by index
    pdfviewer.PageOrganizer.ReArrange(new int[] { 1, 0 });
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Rearrange the page by index
    pdfviewer.PageOrganizer.ReArrange(new int[] { 1, 0 })
End Sub

{% endhighlight %}
{% endtabs %}

N> If any of the already existing page index is not present in rearranged array, then that page will be removed.

## Removing PDF page(s)

You can remove the PDF page(s) from the PDF document using the RemoveAt method in PageOrganizer.
To remove the page at specific index from PDF document, refer to the following code example. 

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Remove a page at index 0
    pdfviewer.PageOrganizer.RemoveAt(0);
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Remove a page at index 0
    pdfviewer.PageOrganizer.RemoveAt(0)
End Sub

{% endhighlight %}
{% endtabs %}

To remove the set of pages from PDF document, refer to the following code example.

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Removing the pages at index 0 and 1
    pdfviewer.PageOrganizer.RemovePages(new int[] { 0, 1 });
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Removing the pages at index 0 and 1
    pdfviewer.PageOrganizer.RemovePages(new int[] { 0, 1 })
End Sub

{% endhighlight %}
{% endtabs %}

## Acquiring page rotation

You can get the rotation angle of a PDF page in terms of `PdfPageRotateAngle` using `PageOrganizer.GetPageRotation()` method.

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Gets rotation angle of page with index 0 
    PdfPageRotateAngle rotatedAngle = pdfviewer.PageOrganizer.GetPageRotation(0);
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Gets rotation angle of page with index 0 
    Dim rotatedAngle As PdfPageRotateAngle = pdfviewer.PageOrganizer.GetPageRotation(0)
End Sub

{% endhighlight %}
{% endtabs %}

## Disabling page organizer

You can remove the page organizer icon from left pane of the ‘PdfViewerControl’ by setting the ‘PageOrganizerSettings.IsIconVisible’ property to false. 
Refer to the following code example to disable the organize page.

{% tabs %}
{% highlight c# %}

private void button1_Click(object sender, RoutedEventArgs e)
{
    //Removing the page organizer icon from left pane. 
    pdfviewer.PageOrganizerSettings.IsIconVisible = false;
}

{% endhighlight %}
{% highlight VB %}

Private Sub button1_Click(sender As Object, e As RoutedEventArgs) 
    'Removing the page organizer icon from left pane. 
    pdfviewer.PageOrganizerSettings.IsIconVisible = false
End Sub

{% endhighlight %}
{% endtabs %}

## Keyboard shortcuts

The following keyboard shortcuts are available at miniature preview mode to organize the PDF pages:

•	Delete key: Deletes the selected page from the PDF document.
•	Ctrl+A: Selects all pages in the PDF document.
•	Shift+Arrow/MouseButton: Selects a set of consecutive pages in the PDF document.
•	Ctrl+MouseButton: Selects the clicked pages in the PDF document. 
