---
layout: post
title: MDI/ TDI functionalities of Syncfusion DockingManager control for WPF
description: Features of MDI and TDI documents of DockingManager control for WPF
platform: wpf
control: DockingManager
documentation: ug
---

# MDI/ TDI functionalities

The MDI and TDI functionalities are applicable for the Document window in the DockingManager. So Document window can be displayed in both Multiple Document Interface and Tabbed Document Interface.

To change mode for the Document window, set the property `ContainerMode` with its respective values.

By default, the document state window is in TDI mode, that display child as tabbed document.

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager UseDocumentContainer="True" ContainerMode="TDI">        

<ContentControl x:Name="Content1" syncfusion:DockingManager.Header="Document1" />   

<ContentControl syncfusion:DockingManager.Header="Document2" syncfusion:DockingManager.State="Document" /> 

</syncfusion:DockingManager>

{% endhighlight %}

{% highlight C# %}

SyncDockingManager.UseDocumentContainer = true;

SyncDockingManager.ContainerMode = DocumentContainerMode.TDI;

DockingManager.SetState(Document1, DockState.Document);

DockingManager.SetState(Document2, DockState.Document);

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img1.jpeg)

To make the document child window as MDI document, set the `ContainerMode` as `MDI`

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager x:Name="DockingManager1" UseDocumentContainer="True" ContainerMode="MDI">        

<ContentControl x:Name="Content1" syncfusion:DockingManager.Header="Document1" syncfusion:DockingManager.State="Document"/>   

<ContentControl x:Name="Content2" syncfusion:DockingManager.Header="Document2" syncfusion:DockingManager.State="Document"/> 

</syncfusion:DockingManager>

{% endhighlight %}

{% highlight C# %}

//Tabbed Document Interface.

SyncDockingManager.ContainerMode = DocumentContainerMode.MDI;

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img2.jpeg)


## Setting MDI Window state

The state of the MDI Window can be set using the `SetMDIWindowState()` method of DocumentContainer. 

### Setting MDI WindowState as Minimized

{% tabs %}

{% highlight C# %}

DocumentContainer.SetMDIWindowState(Content1,MDIWindowState.Minimized);

{% endhighlight %}

{% highlight VB %}

DocumentContainer.SetMDIWindowState(Content1,MDIWindowState.Minimized)

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img3.jpeg)



### Setting MDI WindowState as Maximized

{% tabs %}

{% highlight C# %}

DocumentContainer.SetMDIWindowState(Content1,MDIWindowState.Maximized);

{% endhighlight %}

{% highlight VB %}

DocumentContainer.SetMDIWindowState(Content1,MDIWindowState.Maximized) 

{% endhighlight %}

{% endtabs %}

## Getting state of the MDI window

The state of the MDI window can be detect using the `GetMDIWindowState()` method of DocumentContainer.

{% tabs %}

{% highlight C# %}

DocumentContainer.GetMDIWindowState(Content1);

{% endhighlight %}

{% highlight VB %}

DocumentContainer.GetMDIWindowState(Content1) 

{% endhighlight %}

{% endtabs %}

## Detecting the maximized state of the MDI window

Maximized state of the MDI Container can get by `IsInMDIMaximizedState` property of DocumentContainer. The container can be fetched from the DockingManager using the `DocContainer` property.

{% tabs %}

{% highlight C# %}

(DockingManager1.DocContainer as DocumentContainer).IsInMDIMaximizedState = true;

{% endhighlight %}

{% highlight VB %}

TryCast(DockingManager1.DocContainer, DocumentContainer).IsInMDIMaximizedState = True 

{% endhighlight %}

{% endtabs %}

## Resizing MDI

MDI document window can be able to resize using the navigation arrows. To restrict resizing the MDI document windows, disable the Property `IsAllowMDIResize` of the `DocumentContainer` that can be get using the `DocContainer` property of the DockingManager. By default, its values is `True`.

{% tabs %}

{% highlight C# %}

(DockingManager1.DocContainer as DocumentContainer).IsAllowMDIResize = false;

{% endhighlight %}

{% highlight VB %}

TryCast(DockingManager1.DocContainer, DocumentContainer).IsAllowMDIResize = False 

{% endhighlight %}

{% endtabs %}

## Different Keyboard Navigation Modes

DockingManager allows to navigate between children (Both  TDI and MDI) windows easily using the keyboard keys with combination of `CTRL` `+` `TAB` in five different modes by `SwitchMode` property of the DockingManager.

There are five switch modes.

* Immediate
* List
* QuickTabs
* VS2005
* Vista Flip

### Immediate – Switch the MDI document windows immediately.

{% tabs %}

{% highlight C# %}

DockingManager1.SwitchMode =SwitchMode.Immediate;

{% endhighlight %}

{% highlight VB %}

DockingManager1.SwitchMode =SwitchMode.Immediate 

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img4.jpeg)


### List – Switch the MDI document windows in list format.

{% tabs %}

{% highlight C# %}

DockingManager1.SwitchMode = SwitchMode.List;

{% endhighlight %}

{% highlight VB %}

DockingManager1.SwitchMode =SwitchMode.List 

{% endhighlight %}


{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img5.jpeg)


### QuickTabs

{% tabs %}

{% highlight C# %}

DockingManager1.SwitchMode = SwitchMode.QuickTabs;

{% endhighlight %}

{% highlight VB %}

DockingManager1.SwitchMode =SwitchMode.QuickTabs 

{% endhighlight %}


{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img6.jpeg)


### VistaFlip

{% tabs %}

{% highlight C# %}

DockingManager1.SwitchMode = SwitchMode.VistaFlip;

{% endhighlight %}

{% highlight VB %}

DockingManager1.SwitchMode =SwitchMode.VistaFlip 

{% endhighlight %}


{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img7.jpeg)


### VS2005

{% tabs %}

{% highlight C# %}

DockingManager1.SwitchMode = SwitchMode.VS2005;

{% endhighlight %}

{% highlight VB %}

DockingManager1.SwitchMode =SwitchMode.VS2005 

{% endhighlight %}


{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img8.jpeg)


## Setting MDI Layout

DockingManager allows to set the different layout for the MDI windows with the different MDILayout values such as `Horizontal` , `Vertical` and `Cascade` layout through the `SetLayout()` method of DocumentContainer.

`Horizontal` - Arranges the MDI windows horizontally.


{% tabs %}

{% highlight C# %}

void DocumentContainer_Loaded(object sender, RoutedEventArgs e)
{
	(DockingManager1.DocContainer as DocumentContainer).SetLayout(MDILayout.Horizontal);
}

{%endhighlight%}

{% highlight VB %}

Private Sub DocumentContainer_Loaded(ByVal sender As Object, ByVal e As RoutedEventArgs)
	TryCast(DockingManager1.DocContainer, DocumentContainer).SetLayout(MDILayout.Horizontal)
End Sub 

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img9.jpeg)


 `Vertical` – Arranges the MDI windows vertically.

{% tabs %}

{% highlight C# %}

void DocumentContainer_Loaded(object sender, RoutedEventArgs e)
{
	(DockingManager1.DocContainer as DocumentContainer).SetLayout(MDILayout.Vertical);
}

{%endhighlight%}

{% highlight VB %}

Private Sub DocumentContainer_Loaded(ByVal sender As Object, ByVal e As RoutedEventArgs)
	TryCast(DockingManager1.DocContainer, DocumentContainer).SetLayout(MDILayout.Vertical)
End Sub 

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img10.jpeg)


`Cascade` - Arranges the layout in a cascade manner.

{% tabs %}

{%highlight C#%}

void DocumentContainer_Loaded(object sender, RoutedEventArgs e)
{
	(DockingManager1.DocContainer as DocumentContainer).SetLayout(MDILayout.Vertical);
}

{%endhighlight%}

{% highlight VB %}

Private Sub DocumentContainer_Loaded(ByVal sender As Object, ByVal e As RoutedEventArgs)
	TryCast(DockingManager1.DocContainer, DocumentContainer).SetLayout(MDILayout.Vertical)
End Sub 

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img11.jpeg)




## Closing a MDI Windows

To enable or disable closing functionality of the MDI windows, set `CanClose` an attached property of DockingManager with its respective values. By default, its value is `True`

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager x:Name="DockingManager1" UseDocumentContainer="True" ContainerMode="MDI"> 

<ContentControl x:Name="Content1" syncfusion:DockingManager.Header="Item1"
                syncfusion:DockingManager.State="Document" syncfusion:DockingManager.CanClose="False"/>   

</syncfusion:DockingManager>

{%endhighlight%}

{% highlight C# %}

DockingManager.SetCanClose(Content1, false);

{%endhighlight%}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img12.jpeg)


## Indexing an Item in TDI

A document window can be placed at different index position using the `SetTDIIndex()` method of the TDILayoutPanel. 

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager x:Name="DockingManager1" UseDocumentContainer="True">

<ContentControl x:Name="Content1" syncfusion:DockingManager.Header="Document1" syncfusion:DockingManager.State="Document"/>   

<ContentControl x:Name="Content2" syncfusion:DockingManager.Header="Document2" syncfusion:DockingManager.State="Document"/> 

</syncfusion:DockingManager>

{% endhighlight %}

{% endtabs %}

{% tabs %}

{% highlight C# %}

TDILayoutPanel.SetTDIIndex(Content1,0);

{% endhighlight %}

{% highlight VB %}

TDILayoutPanel.SetTDIIndex(Content1,0) 

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img13.jpeg)


## Drag / Drop support in TDI

The TDI document index can be changed by dragging and dropping it like Visual Studio. This functionality can be enabled or disabled through the property `IsTDIDragDropEnabled` of DockingManager.

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager UseDocumentContainer="True" IsTDIDragDropEnabled="True" >

<ContentControl syncfusion:DockingManager.Header="Document1" syncfusion:DockingManager.State="Document"/>

<ContentControl syncfusion:DockingManager.Header="Document2" syncfusion:DockingManager.State="Document"/>

<ContentControl syncfusion:DockingManager.Header="Document3" syncfusion:DockingManager.State="Document"/>

</syncfusion:DockingManager>

{% endhighlight %}

{% highlight C# %}

SyncDockingManager.IsTDIDragDropEnabled = true;

{% endhighlight %}

{% endtabs %}

## Customizing Close Menu

Menu items like `Close`, `CloseAll` and `CloseAllButThis` are available for the document window when two or more documents used in the DockingManager. To collapse the visibility of these menu item, set the property `ShowClose`, `ShowCloseAll` and `ShowCloseAllButThis` as `False`.

{% tabs %}

{% highlight XAML %}

<ContentControl syncfusion:DockingManager.Header="Item1"
                syncfusion:DockingManager.State="Document"
                syncfusion:DockingManager.ShowCloseMenuItem="False"
                syncfusion:DockingManager.ShowCloseAllMenuItem="False"
                syncfusion:DockingManager.ShowCloseAllButThisMenuItem="False"/>                                                 


<ContentControl syncfusion:DockingManager.Header="Item2"  
                syncfusion:DockingManager.State="Document"
                syncfusion:DockingManager.ShowCloseMenuItem="False"
                syncfusion:DockingManager.ShowCloseAllMenuItem="False"
                syncfusion:DockingManager.ShowCloseAllButThisMenuItem="False"/>             

{% endhighlight %}

{% highlight C# %}

//Closing Customization

DockingManager.SetShowCloseMenuItem(Item1, false);

DockingManager.SetShowCloseAllMenuItem(Item1, false);

DockingManager.SetShowCloseAllButThisMenuItem(Item1, false);

DockingManager.SetShowCloseMenuItem(Item2, false);

DockingManager.SetShowCloseAllMenuItem(Item2, false);

DockingManager.SetShowCloseAllButThisMenuItem(Item2, false);

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img14.jpeg)


## Grouping Document Tab Group

TDI document can be grouped like VisualStudio. It can be grouped by drag and Drop and also using the options in context menu items.

### Creating TabGroup using ContextMenu option

In DockingManager, new tab group can be created at horizontal or vertical side in the document area using `ContextMenu` option.

#### Creating Vertical Tab Group 

To create a vertical tab group in the Tabbed document, select the "New Vertical Tab Group" context menu item and also it can be created programmatically by calling the method `CreateVerticalTabGroup(UIElement)` of the DocumentContainer.

{% tabs %}

{% highlight C# %}

(DockingManager1.DocContainer as DocumentContainer).CreateVerticalTabGroup(Content1);

{% endhighlight %}

{% highlight VB %}

TryCast(DockingManager1.DocContainer, DocumentContainer).CreateVerticalTabGroup(Content1) 

{% endhighlight %}

{% endtabs %}

#### Creating Horizontal Tab Group 

To create a horizontal tab group in the Tabbed document, select the "New Horizontal Tab Group context menu item and also it can be created programmatically by calling the method `CreateHorizontalTabGroup(UIElement)` of the DocumentContainer.

{% tabs %}

{% highlight C# %}

(DockingManager1.DocContainer as DocumentContainer).CreateHorizontalTabGroup(Content1);

{% endhighlight %}

{% highlight VB %}

TryCast(DockingManager1.DocContainer, DocumentContainer).CreateHorizontalTabGroup(Content1)

{% endhighlight %}

{% endtabs %}

#### Adding Tab in a Group 

In TDI document, new tab group can be created by dragging the TabItem into the Document area and click the "New Tab Group" menu item from context menu item.

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img15.jpeg)


![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img16.jpeg)

### Creating TabGroup through mouse interaction without using ContextMenu option

In DockingManager, new tab group can be created at top, left, right and bottom side in the document area through mouse interaction. To enable this functionalities in DockingManager, the `TabSwitchSection` property should be set as `ActiveFiles` for document items and `ActiveToolWindows` for dock items.

#### ActiveFiles mode

When setting the TabSwitchSection as `ActiveFiles` for document panel, dock ability has been restricted and it always placed as a document window whenever it drag and drop.

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager x:Name="DockingManager1" UseDocumentContainer="True" IsVS2010DraggingEnabled="True">  

<ContentControl x:Name="Content1" syncfusion:DockingManager.Header="Item1" syncfusion:DockingManager.State="Document" syncfusion:DockingManager.TabSwitchSection="ActiveFiles"/>   

<ContentControl x:Name="Content2" syncfusion:DockingManager.Header="Item2" syncfusion:DockingManager.State="Document" syncfusion:DockingManager.TabSwitchSection="ActiveFiles"/> 

<ContentControl x:Name="Content3" syncfusion:DockingManager.Header="Item3" syncfusion:DockingManager.State="Document" syncfusion:DockingManager.TabSwitchSection="ActiveFiles"/>

</syncfusion:DockingManager>

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/TabGroupCreation_Top.png)

#### ActiveToolWindows mode

When setting the TabSwitchSection as ActiveToolWindows for Dock Panel. It can be docked in the Top, Bottom, Right and Left as a Dock or Document Window when drag and drop it on the TDI Manager based on the position of the window placed in the DragProvider. 

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager x:Name="DockingManager1" UseDocumentContainer="True" IsVS2010DraggingEnabled="True">    

<ContentControl x:Name="Content1" syncfusion:DockingManager.Header="Item1" syncfusion:DockingManager.State="Document" syncfusion:DockingManager.TabSwitchSection="ActiveFiles"/>   

<ContentControl x:Name="Content2" syncfusion:DockingManager.Header="Item2" syncfusion:DockingManager.State="Document" syncfusion:DockingManager.TabSwitchSection="ActiveFiles"/> 

<ContentControl x:Name="Content3" syncfusion:DockingManager.Header="Item3" syncfusion:DockingManager.DesiredWidthInDockedMode="200" syncfusion:DockingManager.DesiredHeightInDockedMode="50" syncfusion:DockingManager.State="Dock" syncfusion:DockingManager.TabSwitchSection="ActiveToolWindows"/>

</syncfusion:DockingManager>

{% endhighlight %}

{% endtabs %}

Dock window creation at left side:

![](MDI_TDIfunctionalities_images/DockWindowCreation_Left.png)

Document window creation at left side:

![](MDI_TDIfunctionalities_images/TabGroupCreation_Left.png)

N> These functionalities will effect only when `IsVs2010DraggingEnabled` property of DockingManager is true.

### Disable TabGroups

Vertical and Horizontal Tab Grouping feature can be enabled or disabled using the property `TabGroupEnabled` in DockingManager. 
 
To disabling Tab Groups, set TabGroupEnabled as `False`. So it does not display "New Horizontal Tab Group" and "New Vertical Tab Group" context menu items even when ShowHorizontalTabGroupMenuItem is true. Drag and drop support to create new tab group is also restricted.

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager TabGroupEnabled="False" />

{%endhighlight %}

{% highlight C# %}

SyncDockingManager.TabGroupEnabled = false;

{%endhighlight %}
 
{% endtabs %}

## VS2010 Behavior of TDI

TDI document of DockingManager can be changed to Float while dragging its TDI header. This functionality can be enabled or disabled using the property `IsVs2010DraggingEnabled`. By default, its value is `False`. 

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager UseDocumentContainer="True" IsVS2010DraggingEnabled="True">

<ContentControl syncfusion:DockingManager.Header="Document1" syncfusion:DockingManager.State="Document" />

</syncfusion:DockingManager>

{% endhighlight %}

{% highlight C# %}

SyncDockingManager.IsVS2010DraggingEnabled = true;

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img17.jpeg)


## TDI Header Renaming Support

To enable the functionality of editing the TDI document header when double click on document header at runtime, set the property `EnableDocumentTabHeaderEdit` of the DockingManager as `True`. By default, its value is `False`.

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager UseDocumentContainer="True" EnableDocumentTabHeaderEdit="True">

{% endhighlight %}

{% highlight C# %}

SyncDockingManager.EnableDocumentTabHeaderEdit = true;

{% endhighlight %}

{% endtabs %}

## Hiding TDI Header

To hide the TDI document header when a single document child present in a DockingManager set the property `HideTDIHeaderOnSingleChild` as `True`. By default its value is `False`.

{% tabs %}

{% highlight XAML %}

<syncfusion:DockingManager UseDocumentContainer="True" HideTDIHeaderOnSingleChild="True">

<ContentControl syncfusion:DockingManager.Header="Document1" syncfusion:DockingManager.State="Document" />

</syncfusion:DockingManager>

{% endhighlight %}

{% highlight C# %}

SyncDockingManager.HideTDIHeaderOnSingleChild = true;

{% endhighlight %}

{% endtabs %}

![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img18.jpeg)


## Add New button in Header Panel

In DockingManager, the New button can be added in the Document state windows using the `IsNewButtonEnabled` property of the DocumentTabControl. To achieve this, DocumentTabControl must be fetched from the DockingManager.

{% tabs %}

{% highlight C# %}

DocumentTabControl tab = VisualUtils.FindDescendant(DockingManager1,typeof (DocumentTabControl)) as DocumentTabControl;

if (tab != null)
{
   tab.IsNewButtonEnabled = true;
   tab.NewButtonBackground = Brushes.Green;
}


{% endhighlight %}

{% highlight VB %}

Dim tab As DocumentTabControl = TryCast(VisualUtils.FindDescendant(DockingManager1,GetType(DocumentTabControl)), DocumentTabControl)

If tab IsNot Nothing Then
   tab.IsNewButtonEnabled = True
   tab.NewButtonBackground = Brushes.Green
End If 

{% endhighlight %}

{% endtabs %}


![](MDI_TDIfunctionalities_images/MDI_TDIfunctionalities_img19.jpeg)


