---
layout: post
title: Contextmenu in WPF TabControlExt | Syncfusion
description: Learn about tab list menu and tabitem context menu in WPF TabControlExt and how to add custom context menu.
platform: wpf
control: TabControlExt
documentation: ug
---

# Context menu in WPF TabControl (TabControlExt)

This section explains how to show the tab list and tab item context menu and add custom context menu in [TabControl](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt.html).

## Default tab item context menu

You can close the one or more tab items by using the context menu. You can enable it by using the  [ShowTabItemContextMenu](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~ShowTabItemContextMenu.html) property to `true`. You can open this context menu by right click on tab header. The default value of `ShowTabItemContextMenu` property is `false`.

The built-in tabitem context menu has the following menu items:

* Close - Closes the selected tab item.
* Close All But This - Closes all the tab items, except the selected tab item.
* Close All - Closes all the tab items.

N> The [CloseMode](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~CloseMode.html) in `TabControl` is an enum that includes option `Hide` and `Delete`. When you click any default options (Close, Close All and Close All But This) in tabitem context menu and when the `CloseMode` is set to `Hide`, the tabitem moves to the hidden state or when the `CloseMode` is set to `Delete`, the tabitem is completely deleted from `TabControl`.

{% tabs %}
{% highlight XAML %}

<syncfusion:TabControlExt ShowTabItemContextMenu="True" 
                          CloseMode="Hide"
                          Name="tabControlExt">
    <syncfusion:TabItemExt Content="This is the first tab item"
                           Header="tabItem1"/>
</syncfusion:TabControlExt>

{% endhighlight %}
{% highlight C# %}

tabControlExt.ShowTabItemContextMenu = true;
tabControlExt.CloseMode = CloseMode.Hide;

{% endhighlight %}
{% endtabs %}

![Enable context menu of tab item in TabControl](Contextmenu_images/wpf-tabcontrol-contextmenu.gif)

N> View [Sample](https://github.com/SyncfusionExamples/syncfusion-wpf-tabcontrolext-examples/tree/master/Samples/ContextMenu) in GitHub

### Tab item context menu events

Closing the tab items using the context menu can be notified by following events.

* `Close` option - [OnCloseButtonClick](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~OnCloseButtonClick_EV.html) event
* `Close All But This` option - [OnCloseOtherTabs](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~OnCloseOtherTabs_EV.html ) event
* `Close All` option - [OnCloseAllTabs](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~OnCloseAllTabs_EV.html) event.

You can use the [CloseTabEventArgs.ClosingTabItems](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.CloseTabEventArgs~ClosingTabItems.html) property to find out which tabitem is closing from the `OnCloseOtherTabs` and  `OnCloseAllTabs` events and use the [CloseTabEventArgs.TargetTabItem](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.CloseTabEventArgs~TargetTabItem.html) property to find out which tabitem is closing from the `OnCloseButtonClick` event.

{% tabs %}
{% highlight XAML %}

<syncfusion:TabControlExt OnCloseAllTabs="TabControlExt_OnCloseAllTabs"
                          OnCloseButtonClick="TabControlExt_OnCloseButtonClick"
                          OnCloseOtherTabs="TabControlExt_OnCloseAllTabs"
                          Name="tabControlExt">
</syncfusion:TabControlExt>

{% endhighlight %}
{% highlight C# %}

tabControlExt.OnCloseAllTabs += TabControlExt_OnCloseAllTabs;
tabControlExt.OnCloseButtonClick += TabControlExt_OnCloseButtonClick;
tabControlExt.OnCloseOtherTabs += TabControlExt_OnCloseOtherTabs;

{% endhighlight %}
{% endtabs %}

You can handle this events as follows,

{% tabs %}
{% highlight C# %}

private void TabControlExt_OnCloseAllTabs(object sender, CloseTabEventArgs e) {
    var closingTabItems = e.ClosingTabItems;
}
private void TabControlExt_OnCloseButtonClick(object sender, CloseTabEventArgs e) {
    var closingTabItems = e.ClosingTabItems;
}
private void TabControlExt_OnCloseOtherTabs(object sender, CloseTabEventArgs e) {
    var closingTabItems = e.ClosingTabItems;
}

{% endhighlight %}
{% endtabs %}

### Adding custom context menu item for the tab items

You can add the custom context menu item for the tab item using the [TabItemExt.ContextMenuItems](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabItemExt~ContextMenuItems.html) property. You can enable it by setting the [TabControlExt.IsCustomTabItemContextMenuEnabled](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~IsCustomTabItemContextMenuEnabled.html) property to `true`. The default value of `TabControlExt.IsCustomTabItemContextMenuEnabled` property is `false`.

{% tabs %}
{% highlight XAML %}

<syncfusion:TabControlExt IsCustomTabItemContextMenuEnabled="True"
                          Name="tabControlExt" >
    <syncfusion:TabItemExt Header="tabItem1">
        
        <!--Adding custom context menu items-->
        <syncfusion:TabItemExt.ContextMenuItems>
            <syncfusion:CustomMenuItem Header="Edit" />
        </syncfusion:TabItemExt.ContextMenuItems>
    </syncfusion:TabItemExt>
</syncfusion:TabControlExt>

{% endhighlight %}
{% highlight C# %}

// Enable custom tabitem context menu
tabControlExt.IsCustomTabItemContextMenuEnabled = true;

// Adding custom context menu for the tabitem
CustomMenuItem customMenuItem = new CustomMenuItem();
customMenuItem.Header = "Edit";
tabItemExt1.ContextMenuItems.Add(customMenuItem);

{% endhighlight %}
{% endtabs %}

![Added custom context menu for tabitem in TabControl](Contextmenu_images/wpf-tabcontrol-customcontextmenu.png)

N> View [Sample](https://github.com/SyncfusionExamples/syncfusion-wpf-tabcontrolext-examples/tree/master/Samples/ContextMenu) in GitHub

### Show only custom context menu items

If you want to show only custom context menu items in the default context menu, then you can collapse the default context menu item using [TabControlExt.DefaultContextMenuItemVisibility](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~DefaultContextMenuItemVisibility.html) property value as `false`. The default value of `TabControlExt.DefaultContextMenuItemVisibility` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:TabControlExt IsCustomTabItemContextMenuEnabled="True"
                          DefaultContextMenuItemVisibility="Collapsed"
                          Name="tabControlExt" >
    <syncfusion:TabItemExt Header="tabItemExt1">
        <syncfusion:TabItemExt.ContextMenuItems>
            <syncfusion:CustomMenuItem Header="Edit" />
            <syncfusion:CustomMenuItem Header="Copy" />
            <syncfusion:CustomMenuItem Header="Paste" />
        </syncfusion:TabItemExt.ContextMenuItems>
    </syncfusion:TabItemExt>
</syncfusion:TabControlExt>

{% endhighlight %}
{% highlight C# %}

//Collapse the default contextmenu visibility
tabControlExt.DefaultContextMenuItemVisibility = Visibility.Collapsed;

//Adding custom context menu for the first tabitem
CustomMenuItem customMenuItem1 = new CustomMenuItem() { Header = "Edit"};
CustomMenuItem customMenuItem2 = new CustomMenuItem() { Header = "Copy"};
CustomMenuItem customMenuItem3 = new CustomMenuItem() { Header = "Paste"};

tabItemExt1.ContextMenuItems.Add(customMenuItem1);
tabItemExt1.ContextMenuItems.Add(customMenuItem2);
tabItemExt1.ContextMenuItems.Add(customMenuItem3);

{% endhighlight %}
{% endtabs %}

![Show only the custom context menu items in Default context menu](Contextmenu_images/wpf-tabcontrol-disabledefaultmenu.png)

N> View [Sample](https://github.com/SyncfusionExamples/syncfusion-wpf-tabcontrolext-examples/tree/master/Samples/ContextMenu) in GitHub

### Custom UI for default tab item context menu

You can customize the default tab item context menu appearance for the each tab items by using the [TabItemExt.TabItemContextMenuItemTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabItemExt~TabItemContextMenuItemTemplate.html) property.

{% tabs %}
{% highlight XAML %}

<Window.Resources>

    <!--Custom data template for the TabItem ContextMenu-->
    <DataTemplate x:Key="TabItemContextMenuItemTemplate"
          DataType="syncfusion:TabItemExt">
        <TextBlock FontFamily="Calibri"
                   Foreground="Blue"
                   FontStyle="Oblique"
                   Text="{Binding}"/>
    </DataTemplate>
</Window.Resources>

<syncfusion:TabControlExt ShowTabItemContextMenu="True" 
                          Name="tabControlExt">
    <syncfusion:TabItemExt TabItemContextMenuItemTemplate="{StaticResource TabItemContextMenuItemTemplate}"
                           Header="tabItem1"/>
    <syncfusion:TabItemExt TabItemContextMenuItemTemplate="{StaticResource TabItemContextMenuItemTemplate}"
                           Header="tabItem2" />
</syncfusion:TabControlExt>

{% endhighlight %}
{% endtabs %}

![Customize the default tab item context menu](Contextmenu_images/wpf-tabcontrol-style1.png)

N> View [Sample](https://github.com/SyncfusionExamples/syncfusion-wpf-tabcontrolext-examples/tree/master/Samples/Templates) in GitHub

## Tab list menu for switching tabs

You can easily navigate to any tab item by using the tab list menu which is placed in the top-right corner of the tab header panel .The header of all tab item’s are shown as a menu item in the tab list menu. You can hide this tab list menu by using the [ShowTabListContextMenu](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~ShowTabListContextMenu.html) property value as `false`.  The default value of `ShowTabListContextMenu` property is `true`.

{% tabs %}
{% highlight XAML %}

<syncfusion:TabControlExt ShowTabListContextMenu="True"
                          Name="tabControlExt">
    <syncfusion:TabItemExt Header="tabItem1" />
    <syncfusion:TabItemExt Header="tabItem2" />
</syncfusion:TabControlExt>

{% endhighlight %}
{% highlight C# %}

tabControlExt.ShowTabListContextMenu = true;

{% endhighlight %}
{% endtabs %}

![Tab items navigate by tab menu items](Tab-Item-Header_images/ShowTabListContextMenu.png)

N> View [Sample](https://github.com/SyncfusionExamples/syncfusion-wpf-tabcontrolext-examples/tree/master/Samples/ContextMenu) in GitHub

### Custom UI for tab list menu item

You can customize the tab list menu appearance by using the [TabListContextMenuItemTemplate](https://help.syncfusion.com/cr/wpf/Syncfusion.Tools.Wpf~Syncfusion.Windows.Tools.Controls.TabControlExt~TabListContextMenuItemTemplate.html ) property.

{% tabs %}
{% highlight XAML %}

<syncfusion:TabControlExt ShowTabListContextMenu="True" 
                          Name="tabControlExt" >
    <syncfusion:TabControlExt.TabListContextMenuItemTemplate>
        <DataTemplate>
            <TextBlock FontFamily="Calibri"
                       Foreground="Blue"
                       FontStyle="Oblique"
                       Text="{Binding}"/>
        </DataTemplate>
    </syncfusion:TabControlExt.TabListContextMenuItemTemplate>
    <syncfusion:TabItemExt Header="tabItem1" />
    <syncfusion:TabItemExt Header="tabItem2" />
</syncfusion:TabControlExt>

{% endhighlight %}
{% endtabs %}

![Customize the tab list context menu](Contextmenu_images/wpf-tabcontrol-style.png)

N> View [Sample](https://github.com/SyncfusionExamples/syncfusion-wpf-tabcontrolext-examples/tree/master/Samples/Templates) in GitHub