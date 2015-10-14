---
layout: post
title: Binding-with-any-object
description: binding with any object
platform: wpf
control: PropertyGrid 
documentation: ug
---

# Binding with any object

Denotes the object for which PropertyGrid displays Properties. You can set the SelectedObject property to any object.

Binding SelectedObject in an Application

When the SelectedObject property binds to an object, the properties of that object is then parsed and displayed in the PropertyGrid. In the below example, properties of the Customer class is parsed and displayed in the PropertyGrid.




{% highlight xml %}

<syncfusion:PropertyGrid x:Name="propertyGrid"  Width="350"  BorderBrush="Gray"  BorderThickness="3"  HorizontalAlignment="Center"  VerticalAlignment="Center" />

{% endhighlight %}

{% highlight c# %}

  /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
            this.propertyGrid.SelectedObject = new Customer();
        }
    }
 
    public class Customer
    {
        private string _name;
        private int _age;
        private DateTime _dateOfBirth;
        private string _SSN;
        private string _address;
        private string _email;
        private bool _frequentBuyer;
        [CategoryAttribute("ID Settings"), DescriptionAttribute("Name of the customer")]
        public string Name
        {
            get
            {
                return _name;
            }
            set
            {
                _name = value;
            }
        }
 
        [CategoryAttribute("ID Settings"),
        DescriptionAttribute("Social Security Number of the customer")]
        public string SSN
        {
            get
            {
                return _SSN;
            }
            set
            {
                _SSN = value;
            }
        }
        [CategoryAttribute("ID Settings"),
        DescriptionAttribute("Address of the customer")]
        public string Address
        {
            get
            {
                return _address;
            }
            set
            {
                _address = value;
            }
        }
        [CategoryAttribute("ID Settings"),
        DescriptionAttribute("Date of Birth of the Customer (optional)")]
        public DateTime DateOfBirth
        {
            get
            {
                return _dateOfBirth;
            }
            set
            {
                _dateOfBirth = value;
            }
        }
        [CategoryAttribute("ID Settings"), DescriptionAttribute("Age of the customer")]
        public int Age
        {
            get
            {
                return _age;
            }
            set
            {
                _age = value;
            }
        }
        [CategoryAttribute("Marketting Settings"), DescriptionAttribute("If the customer as bought more than 10 times, this is set to true")]
        public bool FrequentBuyer
        {
            get
            {
                return _frequentBuyer;
            }
            set
            {
                _frequentBuyer = value;
            }
        }
        [CategoryAttribute("Marketting Settings"), DescriptionAttribute("Most current e-mail of the customer")]
        public string Email
        {
            get
            {
                return _email;
            }
            set
            {
                _email = value;
            }
        }
    } 
}

{% endhighlight %}

![](Binding-with-any-object_images/Binding-with-any-object_img1.png)





### Properties

SelectedObject Table

<table>
<tr>
<th>
Property </th><th>
Description </th><th>
Type </th><th>
Data Type </th><th>
Reference links </th></tr>
<tr>
<td>
SelectedObject</td><td>
Denotes the object for which PropertyGrid displays properties. User can set the SelectedObject property to any object.</td><td>
DependencyProperty</td><td>
ObjectDefault Value : Null</td><td>
</td></tr>
</table>


### Sample Link

1. Select Start -> Programs -> Syncfusion -> Essential Studio xx.x.x.xx -> Dashboard.
2. Select   Run Locally Installed Samples in WPF Button.
3. Now expand the PropertyGrid treeview item in the Sample Browser.
4. Choose any one of the samples listed under it to launch. 



