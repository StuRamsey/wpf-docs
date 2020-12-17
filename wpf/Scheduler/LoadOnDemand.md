---
layout: post
title: Load appointments on demand in SfScheduler| WPF| Syncfusion
description: This section explains how to load appointments on demand from visible date ranges in the WPF Scheduler.  
platform: wpf
control: SfScheduler
documentation: ug
---
# Load On Demand in WPF Scheduler (SfScheduler)
The scheduler supports to loading appointment on-demand with loading indicator and it improves the loading performance when you have appointments range for multiple years.

![Load on-demand in WPF Scheduler](LoadOnDemand_Images/LoadOnDemand.gif)

## QueryAppointments event
The `QueryAppointments` event is used to load appointments in on-demand for the visible date range. You might start and stop the loading indicator animation before and after the appointments loaded using the `ShowBusyIndicator.`
The `QueryAppointmentsEventArgs` has the following members which provide information for the `QueryAppointments` event.

[VisibleDateRange](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.DateRange.html) - Gets the current visible date range of scheduler that is used to load the appointments.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfScheduler x:Name="Scheduler"
                        ViewType="Month" QueryAppointments="Scheduler_QueryAppointments">
</syncfusion:SfScheduler>
{% endhighlight %}
{% highlight c#%}
Scheduler.QueryAppointments += Scheduler_QueryAppointments;
private void Scheduler_QueryAppointments(object sender, QueryAppointmentsEventArgs e)
{
 Scheduler.ShowBusyIndicator = true;
 Scheduler.ItemsSource = this.GetAppointments(e.VisibleDateRange);
 Scheduler.ShowBusyIndicator = false;
}

private IEnumerable GetAppointments(DateRange dateRange)
 {
  // Add codes to generate appointments from the date range.
}
{% endhighlight %}
{% endtabs %}

The `QueryAppointments` will be raised once any one of the following action will be taken.

 * Once the [ViewChanged](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ViewChanged) event is raised, the `QueryAppointments` will be raised.

* If the appointment has been added, removed, or changed (Resize, drag, and drop) in the current time visible date range, then the `QueryAppointments` event will not be triggered. Since the appointments for that visible date range have been loaded already.

* The `QueryAppointments` event is triggered when the Schedule [ResourceCollection](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ResourceCollection) is updated to load appointments based on the changed resource collection.

* The `QueryAppointments` event will be triggered when the [ResourceGroupType](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ResourceGroupType) is changed.

## Load On Demand command
The Scheduler notifies by `LoadOnDemandCommand` when the user changes the visible date range. You can get a visible date range from the `QueryAppointmentsEventArgs.` The default value for this `ICommand` is null. The `QueryAppointmentsEventArgs` passed as a command parameter.

You can define a ViewModel class that implements command and handle it by the CanExecute and Execute methods to check and execute on-demand loading. In execute method, you can perform the following operations,
* You can start and stop the loading indicator animation before and after the appointments loaded using the `ShowBusyIndicator`.
* Once got appointment collection, you can load into the scheduler itemsource.

{% tabs %}
{% highlight xaml %}
<syncfusion:SfScheduler x:Name="Scheduler"
                        ViewType="Month" 
                        ShowBusyIndicator="{Binding ShowBusyIndicator}"
                        LoadOnDemandCommand="{Binding LoadOnDemandCommand}"
                        ItemsSource="{Binding Events}">
</syncfusion:SfScheduler>
{% endhighlight %}
{% highlight c#%}

public class LoadOnDemandViewModel : INotifyPropertyChanged
  {
    public ICommand LoadOnDemandCommand { get; set; }
    private IEnumerable events;
    public IEnumerable Events
      {
        get { return events; }
        set
          {
            events = value;
            this.RaisePropertyChanged("Events");
          }
      }
    private bool showBusyIndicator;
    public bool ShowBusyIndicator
    {
      get { return showBusyIndicator; }
      set
          {
            showBusyIndicator = value;
            this.RaisePropertyChanged("ShowBusyIndicator");
          }
    }
    
    public ObservableCollection<SchedulerResource> ResourceCollection
    {
      get { return resourceCollection; }
      set
        {
         resourceCollection = value;
         this.RaisePropertyChanged("ResourceCollection");
        }
    }
    public SchedulerViewModel()
    {
       this.LoadOnDemandCommand = new DelegateCommand(ExecuteOnDemandLoading, CanExecuteOnDemandLoading);
    }
       
    public event PropertyChangedEventHandler PropertyChanged;
    public async void ExecuteOnDemandLoading(object parameter)
    {
      this.ShowBusyIndicator = true;
      await Task.Delay(1000);
      await Application.Current.MainWindow.Dispatcher.BeginInvoke(DispatcherPriority.ApplicationIdle, new Action(() =>
            {
                this.Events = this.GetAppointments((parameter as QueryAppointmentsEventArgs).VisibleDateRange);
            }));
      this.ShowBusyIndicator = false;
    }

    private bool CanExecuteOnDemandLoading(object sender)
    {
      return true;
    }

    private IEnumerable GetAppointments(DateRange dateRange)
    {
      // Add Codes to generate appointments
    }

    private void RaisePropertyChanged(string propertyName)
    {
        this.PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(propertyName));
    } 
  }
{% endhighlight %}
{% endtabs %}

The `LoadOnDemandCommand` will be invoked once any one of the following actions will be taken.

* Once the [ViewChanged](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ViewChanged) event is raised, the `LoadOnDemandCommand` will also be raised.

* If the appointment has been added, removed, or changed (Resize, drag, and drop) in the current time visible date range, then the `LoadOnDemandCommand` will not be triggered. Since the appointments for that visible date range have been loaded already.

* The `LoadOnDemandCommand` is triggered when the Schedule [ResourceCollection](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ResourceCollection) is updated to load the appointments based on the changed resource collection.

* The `LoadOnDemandCommand` will be triggered when the [ResourceGroupType](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ResourceGroupType) is changed.

## Load On Demand for recurring appointment
The scheduler control calculates the recurring series and displays appointments from the series in the active view. You can get a pattern appointment from the `RecurrenceHelper.GetPatternAppointment` method If the recurrence appointment is in the visible date range.

* The recurrence appointment should be added to the Scheduler [ItemsSource](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) until the date of recurrence ends.

* If [RecurrenceRule](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.ScheduleAppointment.html#Syncfusion_UI_Xaml_Scheduler_ScheduleAppointment_RecurrenceRule) added with count or end date, you can use the [RecurrenceHelper.GetRecurrenceDateTimeCollection](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.RecurrenceHelper.html#Syncfusion_UI_Xaml_Scheduler_RecurrenceHelper_GetRecurrenceDateTimeCollection_System_String_System_DateTime_System_Nullable_System_DateTime__System_Nullable_System_DateTime__) method to get the recurrence date collection and compare recursive dates in the current visible date range. Then add the recurrence appointment in the scheduler [ItemsSource](https://help.syncfusion.com/cr/wpf/Syncfusion.UI.Xaml.Scheduler.SfScheduler.html#Syncfusion_UI_Xaml_Scheduler_SfScheduler_ItemsSource) If the recursive dates are in the current visible date range.

* If the `RecurrenceRule` is added without an end date, then the recurrence appointment should be added in the scheduler `ItemsSource` when all the visible dates changed from the recurrence start date.

N> [View sample in GitHub](https://github.com/SyncfusionExamples/load-on-demand-appointments-wpf-scheduler)