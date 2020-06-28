---
layout: post
title: Collection editor support in WPF PropertyGrid control | Syncfusion
description: Learn about Collection editor support the properties of selected object in Syncfusion WPF PropertyGrid control and more details.
platform: wpf
control: PropertyGrid 
documentation: ug
---

# Collection Editor in WPF PropertyGrid

You can add, remove or edit the collection type property item by using the `Collection Editor` in the [PropertyGrid](https://help.syncfusion.com/cr/wpf/Syncfusion.PropertyGrid.Wpf~Syncfusion.Windows.PropertyGrid.PropertyGrid.html).

## How to add or remove items in collection using collection editor

You can add or remove the new items into the collection type properties by clicking the `Add` or `Remove` button. If you want to add the items into `SelectedObject` collection, you must click the `Ok` button to update the added items into the collection, otherwise it is not updated. 

![PropertyGrid collection Editor with collection as selected object](CollectionEditor_Images/CollectionEditor_Structure.png)

N> Collection type property must be derived from the `IList` type to add or remove the items in collection property of `SelectedObject`. The `IList` type collection property element must contains the parameterless constructor to update the items in the collection, otherwise you can only remove the items in the collection property.

N> You cannot able to editing and modifying the collection for primitives types and string (List<int>, List<string>). 


## Collection Editor for selected collection object

If you directly assign the collection instance as [SelectedObject](https://help.syncfusion.com/cr/wpf/Syncfusion.PropertyGrid.Wpf~Syncfusion.Windows.PropertyGrid.PropertyGrid~SelectedObject.html), it generates value editor for the each collection property items.

{% tabs %}
{% highlight C# %}

public class Persons {
    public string Name { get; set; }
    public string Address { get; set; }
    public override string ToString() {
        return Name;
    }
}

public class ViewModel {
    private ObservableCollection<Person> persons = new ObservableCollection<Person>();
    public ObservableCollection<Person> Persons {
        get {
            return persons;
        }
        set {
            persons = value;
        }
    }

    public ViewModel() {
        persons.Add(new Person() { Name = "Mark", Address = "United States" });
        persons.Add(new Person() { Name = "Smith", Address = "United States" });

    }
}

{% endhighlight %}
{% endtabs %}
 
{% tabs %}
{% highlight xaml %}

<syncfusion:PropertyGrid PropertyExpandMode="NestedMode"
                         SelectedObject="{Binding Persons}" 
                         x:Name="propertyGrid">
    <syncfusion:PropertyGrid.DataContext>
        <local:ViewModel></local:ViewModel>
    </syncfusion:PropertyGrid.DataContext>
</syncfusion:PropertyGrid>

{% endhighlight %}
{% highlight C# %}

PropertyGrid propertyGrid = new PropertyGrid();
propertyGrid.DataContext = new ViewModel();
propertyGrid.SetBinding(PropertyGrid.SelectedObjectProperty, new Binding("Persons"));
propertyGrid1.PropertyExpandMode = PropertyExpandModes.NestedMode;

{% endhighlight %}
{% endtabs %}

![PropertyGrid collection Editor with collection as selected object](CollectionEditor_Images/Direct.png)

N> View [Sample](https://github.com/SyncfusionExamples/wpf-property-grid-examples/tree/master/Samples/DirectCollectionEditor) on GitHub

## Collection Editor for selected object's collection property

You can add, remove or edit the collection type property item by using the `Collection Editor`.

{% tabs %}
{% highlight C# %}

public class Customer {
    public int ID { get; set; }
    public string Name { get; set; }
    public string Phone { get; set; }
}

public class Employee {
    public int ID { get; set; }
    public string Name { get; set; }
    public string Phone { get; set; }
}

public class CustomerCollection : ObservableCollection<Customer> {
    public CustomerCollection() { }
    public override string ToString() {
        return "Customer List";
    }
}

public class EmployeeList : List<Employee> {
    public EmployeeList() { }
    public override string ToString() {
        return "Employee List";
    }
}

public class Product {
    public int CompanyID { get; set; }
    public string ProductName { get; set; }
    public CustomerCollection Customers { get; set; }
    public EmployeeList Employees { get; set; }
}

public class ViewModel {
    public Product DemoProduct { get; set; }

    public ViewModel() {
        DemoProduct = new Product()
        {
            CompanyID = 157,
            ProductName = "Laptop",
            Customers = new CustomerCollection
            {
                new Customer() { ID = 0, Name = "John", Phone = "2065349857" },
                new Customer() { ID = 1, Name = "Peter", Phone = "2065981189" }
            },

            Employees = new EmployeeList
            {
                new Employee() { ID = 0, Name = "Mark", Phone = "2065489864" },
                new Employee() { ID = 1, Name = "David", Phone = "2063481135" }
            }
        };
    }
}

{% endhighlight %}
{% endtabs %}
 
{% tabs %}
{% highlight xaml %}

<syncfusion:PropertyGrid SelectedObject="{Binding DemoProduct}" 
                         x:Name="propertyGrid">
    <syncfusion:PropertyGrid.DataContext>
        <local:ViewModel></local:ViewModel>
    </syncfusion:PropertyGrid.DataContext>
</syncfusion:PropertyGrid>

{% endhighlight %}
{% highlight C# %}

PropertyGrid propertyGrid = new PropertyGrid();
propertyGrid.DataContext = new ViewModel();
propertyGrid.SetBinding(PropertyGrid.SelectedObjectProperty, new Binding("DemoProduct"));

{% endhighlight %}
{% endtabs %}

![PropertyGrid with Collection Editor](CollectionEditor_Images/CollectionEditor.gif)

N> View [Sample](https://github.com/SyncfusionExamples/wpf-property-grid-examples/tree/master/Samples/CollectionEditor) on GitHub

## Collection Editor for nested collection property

You can update the nested collection property item by using the `Collection Editor`.

![PropertyGrid with nested Collection Editor](CollectionEditor_Images/Nested.png)

{% tabs %}
{% highlight C# %}

public class AddressDetails {
    public int DoorNo { get; set; }
    public string City { get; set; }
}

public class Supplier {
    public int ID { get; set; }
    public string Name { get; set; }
    public string Phone { get; set; }
    public ObservableCollection<AddressDetails> Address { get; set; }
}

public class SupplierList : List<Supplier> {
    public SupplierList() : base() { }
    public override string ToString()
    {
        return "Supplier List";
    }
}

public class Product {
    public int ID { get; set; }
    public string ProductName { get; set; }
    public SupplierList Suppliers { get; set; }
}

public ViewModel() {
    DemoProduct = new Product() {
        ID = 0,
        ProductName = "Office Table",
        Suppliers = new SupplierList
        {
            new Supplier()
            {
                ID = 0,
                Name = "Jack Plank",
                Phone = "2065559857",
                Address = new ObservableCollection<AddressDetails>()
                {
                    new AddressDetails
                    {
                        City="Mexico",
                        DoorNo=456
                    }
                }
            }
        }
    };
}

{% endhighlight %}
{% endtabs %}
 
{% tabs %}
{% highlight xaml %}

<syncfusion:PropertyGrid SelectedObject="{Binding DemoProduct}" 
                         x:Name="propertyGrid">
    <syncfusion:PropertyGrid.DataContext>
        <local:ViewModel></local:ViewModel>
    </syncfusion:PropertyGrid.DataContext>
</syncfusion:PropertyGrid>

{% endhighlight %}
{% highlight C# %}

PropertyGrid propertyGrid = new PropertyGrid();
propertyGrid.DataContext = new ViewModel();
propertyGrid.SetBinding(PropertyGrid.SelectedObjectProperty, new Binding("DemoProduct"));

{% endhighlight %}
{% endtabs %}

![PropertyGrid with nested Collection Editor](CollectionEditor_Images/CollectionEditor_Nested.gif)

N> View [Sample](https://github.com/SyncfusionExamples/wpf-property-grid-examples/tree/master/Samples/NestedCollectionEditor) on GitHub