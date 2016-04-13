---
layout: post
title: 145-Display-the-Calculation-Columns-in-Row
description:         1.4.5 display the calculation columns in row?
platform: wpf
control: PivotGridControl
documentation: ug
---

# How to set defer layout update in PivotGrid?

It can be achieved by setting the property `DeferLayoutUpdate` to true via code or through the DeferLayoutUpdate check-box (UI option) inside PivotSchemaDesigner control. 

If through *XAML*, please refer the below code sample.

{% highlight xaml %}

        <syncfusion:PivotGridControl HorizontalAlignment="Left" Name="pivotGrid" VerticalAlignment="Top" 
                 DeferLayoutUpdate="True" ItemSource="{Binding   Source={StaticResource data}}" >
        </syncfusion:PivotGridControl>
     
{% endhighlight %}

Else if through *Code-behind*, please refer the below code sample.

{% highlight C# %}

        public MainWindow()
        {
            InitializeComponent();
            pivotGrid.DeferLayoutUpdate = true;
        } 
		
{% endhighlight %}

