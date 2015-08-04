---
layout: post
title: Setting-Tab-Scrolling-Time
description: setting tab scrolling time
platform: wpf
control: TabControlExt
documentation: ug
---

# Setting Tab Scrolling Time

Tab Scrolling Time is controlled by using the ScrollingTime property. This dependency property sets the value for Tab Scrolling Time in milliseconds.

Here is the code snippet to set the Tab Scrolling Time.


{% highlight xml %}
[XAML]



<!-- Adding TabControlExt with CloseButtonType is Both -->

<syncfusion:TabControlExt Name="tabControlExt" ScrollingTime="1000" >



    <!-- Adding TabItemExt -->

    <syncfusion:TabItemExt Name="tabItemExt1" Header="TabItemExt1">

    </syncfusion:TabItemExt>



    <!-- Adding TabItemExt -->

    <syncfusion:TabItemExt Name="tabItemExt2" Header="TabItemExt2">

    </syncfusion:TabItemExt>



    <!-- Adding TabItemExt -->

    <syncfusion:TabItemExt Name="tabItemExt3" Header="TabItemExt3">

    </syncfusion:TabItemExt>

</syncfusion:TabControlExt>
{% endhighlight %}

{% highlight c# %}
[C#]



// Creating instance of the TabControlExt control

TabControlExt tabControlExt = new TabControlExt();



// Creating the instance of StackPanel

StackPanel stackPanel = new StackPanel();



//  Creating instance of the TabItemExt 

TabItemExt tabItemExt1 = new TabItemExt();



// Setting header of the TabItemExt

tabItemExt1.Header = "TabItemExt1";           



// Adding TabItemExt to TabControlExt

tabControlExt.Items.Add(tabItemExt1);    



// Setting scroll time

tabControlExt.ScrollingTime = 1000;



// Adding control to the StackPanel

stackPanel.Children.Add(tabControlExt);
{% endhighlight %}


See Also

Tab Scroll Style, Tab Scroll Button

