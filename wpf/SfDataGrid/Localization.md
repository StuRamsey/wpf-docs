---
layout: post
title: Localization in SfDataGrid.
description: How to localize the SfDataGrid.
platform: wpf
control: SfDataGrid
documentation: ug
---


# Localization 

Localization is the process of translating the application resources into different language for the specific cultures. You can localize the SfDataGrid by [adding resource file](https://msdn.microsoft.com/library/aa992030.aspx). Application culture can be changed by setting `CurrentUICulture` before `InitializeComponent()` method. 

Below application culture changed to German.

{% tabs %}
{% highlight c# %}
public MainWindow()
{
    System.Threading.Thread.CurrentThread.CurrentUICulture = new System.Globalization.CultureInfo("de-DE");

    InitializeComponent();
}    
{% endhighlight %}
{% endtabs %}


To localize the SfDataGrid based on `CurrentUICulture` using resource files, follow the below steps. 

1.Create new folder and named as **Resources** in your application. 
2.Add the default resource file of SfDataGrid into **Resources** folder. You can download the Syncfusion.SfGrid.WPF.resx [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/Resource1113161640.zip).

![](Localization_images/Localization_img1.png)

3.Right-click on the Resources folder, select **Add** and then **NewItem**.

4.In `Add New Item` wizard, select the **Resource File** option and name the filename as **Syncfusion.SfGrid.WPF.&lt;culture name&gt;.resx**. For example, you have to give name as **Syncfusion.SfGrid.WPF.de.resx** for German culture.
 
5.The culture name that indicates the name of language and country. 

![](Localization_images/Localization_img2.png)

6.Now, select `Add` option to add the resource file in **Resources** folder.

![](Localization_images/Localization_img3.png)

7.Add the Name/Value pair in Resource Designer of **Syncfusion.SfGrid.WPF.de.resx** file and change its corresponding value to corresponding culture. 

![](Localization_images/Localization_img4.png)

![](Localization_images/Localization_img5.png)


## Localize when the resource file present in different assembly or different namespace?

By default, SfDataGrid try to read the resource file from executing assembly and its default namespace by using [Assembly.GetExecuteAssembly](https://msdn.microsoft.com/en-us/library/system.reflection.assembly.getexecutingassembly.aspx) method. When the resource file is located at different assembly or namespace, then you can let SfDataGrid know by using [GridResourceWrapper.SetResources](http://help.syncfusion.com/cr/cref_files/wpf/sfdatagrid/Syncfusion.SfGrid.WPF~Syncfusion.UI.Xaml.Grid.GridResourceWrapper~SetResources.html) method.

{% tabs %}
{% highlight c# %}
public MainWindow()
{
    System.Threading.Thread.CurrentThread.CurrentUICulture = new System.Globalization.CultureInfo("de-DE");            
    Syncfusion.UI.Xaml.Grid.GridResourceWrapper.SetResources("Assembly_name", "namespeace_name");
    InitializeComponent();
}
{% endhighlight %}
{% endtabs %}


## Editing default culture resource

You can edit default resource file by adding it to **Resources** folder of your application where SfDataGrid reads the static texts from here. You can download the default resource file from [here](http://www.syncfusion.com/downloads/support/directtrac/general/ze/Resource1113161640.zip).

![](Localization_images/Localization_img6.png)

Now, change the Name/Value pair in Resource Designer of **Syncfusion.SfGrid.WPF.resx** file.

![](Localization_images/Localization_img7.png)


![](Localization_images/Localization_img8.png)

