---
layout: post
title: Data Binding | CheckListBox | wpf | Syncfusion
description: data binding
platform: wpf
control: CheckListBox
documentation: ug
---

# Data Binding

The control can be populated using ItemsSource property and DisplayMemberPath property used to display the items in the CheckListBox. The below code snippet will be used to bind the ItemsSource to the CheckListBox.

{% tabs %}
{%highlight xaml%}

<syncfusion:CheckListBox x:Name="checkListBox" IsCheckOnFirstClick="True" DisplayMemberPath="Name" ItemsSource="{Binding CheckListItems}" />

{%endhighlight%}

{%highlight c#%}

public class ViewModel : INotifyPropertyChanged
{
    public event PropertyChangedEventHandler PropertyChanged;
    private ObservableCollection<Model> _checkListItems;
    public ObservableCollection<Model> CheckListItems
    {
        get
        {
            return _checkListItems;
        }
        set
        {
            _checkListItems = value;
            RaisePropertyChanged("CheckListItems");
        }
    }
    public ViewModel()
    {
        CheckListItems = new ObservableCollection<Model>();
        CheckListItems.Add(new Model() { Name = "Mexico", Description = "Mexico" });
        CheckListItems.Add(new Model() { Name = "Canada", Description = "Canada "});
        CheckListItems.Add(new Model() { Name = "Bermuda", Description = "Bermuda” });   
        CheckListItems.Add(new Model() { Name = "Beize", Description = "Beize”});               
        CheckListItems.Add(new Model() { Name = "Panama", Description = "Panama" });     
    }
    public void RaisePropertyChanged(string PropertyName)
    {
        if (PropertyChanged != null)
        {
            PropertyChanged(this, new PropertyChangedEventArgs(PropertyName));
        }
    }
}
public class Model
{
    public string Name { get; set; }
    public string Description { get; set; }
}

{%endhighlight%}
{% endtabs %}

![](Getting-Started_images/Getting-Started_img1.png)