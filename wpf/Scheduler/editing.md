---
layout: post
title: Editing in WPF Scheduler | Syncfusion
description: This section explains about how to edit the appointment and handle the appointment while editing in WPF Scheduler.
platform: wpf
control: SfSchedule
documentation: ug
---

# Editing
This section gives you editing details of scheduler appointments and also explained about the appointment resizing and drag drop operations.

## Editing Appointment
Scheduler supports to edit the appointment in by using 'Appointment Editor' UI window. User can use this window by double click over the appointment or right click over the appointment and select the edit option from the `ContextMenu`.

ContextMenu edit option

![WPF Scheduler appointment editing using contextmenu](editing_images/appointment-edit-contextmenu.png)

Appointment editor window

![WPF Scheduler appointment editor window](editing_images/appointment-editor-window.png)

### AppointmentEditorOpening event
Scheduler notifies by  [AppointmentEditorOpening](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentEditorOpening_EV.html) when user opens the appointment editor UI window to edit the appointment. 
[AppointmentEditorOpeningEventArgs](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorOpeningEventArgs.html) has following members which provides information for `AppointmentEditorOpening` event.

[Action](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorOpeningEventArgs~Action.html) - Gets the action(add or delete or edit) for the selected appointment.

[Appointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorOpeningEventArgs~Appointment.html) - Gets the selected appointment details.

`RecurrenceEditMode` - Get or Sets the edit mode to perform the edit option to edit the occurrence or series for recurrence appointment.
    
	* User - Default window dialog will appear when editing a recurrence appointment from the end-user itself.
    * Occurrence - Edit the particular occurrence alone in recurrence appointment. Default window dialog will not appear.
    * Series - Edit the entire series in recurrence appointment. Default window dialog will not appear.

[SelectedResource](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorOpeningEventArgs~SelectedResource.html) - Gets the selected appointment resource details if scheduler does have the resource.

[StartTime](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorOpeningEventArgs~StartTime.html) - Gets the appointment start time

[Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) - To avoid the default appointment editor showing by enabling this property. 

For example, to use custom the appointment editor window instead of default appointment editor window you can handle [AppointmentEditorOpening](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentEditorOpening_EV.html) event.

{% tabs %}
{% highlight c# %}
this.schedule.AppointmentEditorOpening += Schedule_AppointmentEditorOpening;
private void Schedule_AppointmentEditorOpening(object sender, AppointmentEditorOpeningEventArgs e)
{
    //To handle the default appointment editior window by setting the e.Cancel value as true.
    e.Cancel = true;
    if (e.Appointment != null)
    {
        //Display the custom appointment editor window to edit the appointment
    }
    else
    {
        //Display the custom appointment editor window to add new appointment
    }
}
{% endhighlight %}
{% endtabs %}

#### AppointmentEditorClosed
Scheduler notifies by [AppointmentEditorClosed](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentEditorClosed_EV.html) when user close the appointment editor window.
[AppointmentEditorClosedEventArgs](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorClosedEventArgs.html) event has following members which provides information for `AppointmentEditorClosed` event.

[Action](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorClosedEventArgs~Action.html) - Gets the action of appointment which is add or delete or edit.

[EditedAppointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorClosedEventArgs~EditedAppointment.html) - Gets the edited appointment details if appointment editor closed with edit action.

[OriginalAppointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorClosedEventArgs~OriginalAppointment.html) - Gets the selected appointment details.

[IsNew](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorClosedEventArgs~IsNew.html) - Gets the appointment is new or not. 

[Handled](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEditorClosedEventArgs~Handled.html) - To handle appointment editor changes update into the Scheduler `Appointments` collection.

For example, to handle the appointment adding for today's date, you can handle the `AppointmentEditorClosed` event.

{% tabs %}
{% highlight c# %}
this.schedule.AppointmentEditorClosed += Schedule_AppointmentEditorClosed;
private void Schedule_AppointmentEditorClosed(object sender, AppointmentEditorClosedEventArgs e)
{
    var appointment = e.EditedAppointment as ScheduleAppointment;
    if (appointment != null)
    {
        if (appointment.StartTime.Day == DateTime.Now.Day)
            e.Handled = true;
    }
}
{% endhighlight %}
{% endtabs %}

## Disable appointment editing
Scheduler supports to prevent the editing for appointments by using [AllowEditing](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AllowEditing.html) property.

{% tabs %}
{% highlight xaml %}
<Schedule:SfSchedule x:Name="Schedule" AllowEditing="False"/>
{% endhighlight %}
{% highlight c# %}
this.Schedule.AllowEditing = false;
{% endhighlight %}
{% endtabs %}

## Create read only appointment
Scheduler supports to create the read only appointment by using [ReadOnly]((https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.ScheduleAppointment~ReadOnly.html)) property. If you enable this property, user will not be able to perform edit, resize and drag drop operations.

{% tabs %}
{% highlight c# %}
//// Creating an instance for schedule appointment collection
ScheduleAppointmentCollection scheduleAppointmentCollection = new ScheduleAppointmentCollection();
////Adding schedule appointment in schedule appointment collection 
scheduleAppointmentCollection.Add(new ScheduleAppointment()
{
    StartTime = new DateTime(2017, 05, 08, 10, 0, 0),
    EndTime = new DateTime(2017, 05, 10, 10, 0, 0),
    Subject = "Anniversary",
    Location = "Hutchison road",
    ReadOnly = true,
    AppointmentBackground = Brushes.Green
});

//Adding schedule appointment collection to Appointments of SfSchedule
this.Schedule.Appointments = scheduleAppointmentCollection;
{% endhighlight %}
{% endtabs %}

![WPF Scheduler read only appointment](editing_images/read-only-appointment.png)

## Appointment deleting
Scheduler supports three ways to remove the selected appointment
1. Pressing Delete key
2. Using `ContextMenu` delete option.
3. Using AppointmentEditor.

### AppointmentDeleting event
Scheduler notifies by [AppointmentDeleting](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentDeleting_EV.html) event when user delete the appointment.
[AppointmentDeletingEventArgs](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDeletingEventArgs.html) has following members which provides information for `AppointmentDeleting` event.

`Appointment` - Gets the selected appointment
`MappedObject` - Gets the binding object details of selected appointment if schedule appointments are mapped with custom object.
`RecurrenceEditMode` - Gets or sets whether to delete particular occurrence or appointment sequence when delete a recurrence appointment. You can let end-user handle this option (using built-in dialog shown in scheduler) or define it by yourself using `AppointmentDeleting` event. 
    * User - Default window dialog will appear when deleting a recurrence appointment from the end-user itself.
    * Occurrence - Delete the particular occurrence alone in recurrence appointment. Default window dialog will not appear.
    * Series - Delete the entire series in recurrence appointment. Default window dialog will not appear.
[Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) - By enabling this property, avoid deleting the appointment. 

## Appointment resizing
Scheduler supports to resize the appointment using the option `Resize`option from the `ScheduleAppointment` context menu. This support is available for all views except 'Month' view.

![WPF Scheduler appointment resizing using contextmenu](editing_images/appointment-resizing-contextmenu.png)

### AppointmentStartResizing event
Scheduler notifies by [AppointmentStartResizing](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentStartResizing_EV.html) event when user start to resize the appointment.

[AppointmentStartResizingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentStartResizingEventArgs.html) has following members which provides information for `AppointmentStartResizing` event.

[Appointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentStartResizingEventArgs~Appointment.html) - Get the appointment details that is start to resize.
[Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) - Setting value to true, cancels the triggered action.

{% tabs %}
{% highlight c# %}
this.schedule.AppointmentStartResizing += Schedule_AppointmentStartResizing;
private void Schedule_AppointmentStartResizing(object sender, AppointmentStartResizingEventArgs e)
{
    //To notify when start to resize the appointment.    
}
{% endhighlight %}
{% endtabs %}

### AppointmentResizing event
Scheduler notifies by [AppointmentResizing](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentResizing_EV.html) event when user resizing the appointment.

[AppointmentResizingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentResizingEventArgs.html) has following members which provides information for `AppointmentResizing` event.

[Appointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentStartResizingEventArgs~Appointment.html) - Gets the resizing appointment details.

[From](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentResizingEventArgs~From.html) - Gets the appointment start time.

[To](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentResizingEventArgs~To.html) - Gets the appointment end time.

[ResizeType](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentResizingEventArgs~ResizeType.html) - Gets the resize type for appointment whether it is resizing from start or end.

[RefreshAppointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentResizingEventArgs~RefreshAppointment.html) - Get or Sets appointment need to be refresh or not. 

{% tabs %}
{% highlight c# %}
this.schedule.AppointmentResizing += Schedule_AppointmentResizing;
private void Schedule_AppointmentStartResizing(object sender, AppointmentResizingEventArgs e)
{
    //To notify when resizing the appointment.    
}
{% endhighlight %}
{% endtabs %}


### AppointmentEndResizing event
Scheduler notifies by [AppointmentEndResizing](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentEndResizing_EV.html) event when user ends the appointment resizing.

[AppointmentEndResizingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndResizingEventArgs.html) has following members which provides information for `AppointmentEndResizing` event.

[Appointment](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndResizingEventArgs~Appointment.html) - Gets the resizing appointment details.

[From](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndResizingEventArgs~From.html) - Gets the appointment start time.

[To](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndResizingEventArgs~To.html) - Gets the appointment end time.

[ResizeType](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndResizingEventArgs~ResizeType.html) - Gets the resize type for appointment whether it is resizing from start or end.

[Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) - Setting value to true, cancels the triggered action.

{% tabs %}
{% highlight c# %}
this.schedule.AppointmentEndResizing += Schedule_AppointmentResizing;
private void Schedule_AppointmentStartResizing(object sender, AppointmentEndResizingEventArgs e)
{
    //To notify when resizing is completed for an appointment.    
}
{% endhighlight %}
{% endtabs %}

## Drag and drop
Scheduler supports to reschedule the appointment by performing the drag and drop operation. This support is available for all views. 

### DragStarting event
Scheduler notifies by [DragStarting](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~DragStarting_EV.html) when start to drag the appointment.
[DragStartingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.DragStartingEventArgs.html) has following members which provides information for `DragStarting` event.

[Appointment](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.DragStartingEventArgs~Appointment.html) - Get the selected appointment.
[Cancel](https://docs.microsoft.com/en-us/dotnet/api/system.componentmodel.canceleventargs.cancel) - Setting the value as `true` to prevent the drag and drop operation.

{% tabs %}
{% highlight c# %}
this.schedule.DragStarting += Schedule_DragStarting;
private void Schedule_DragStarting(object sender, DragStartingEventArgs e)
{
    //To notify when start to drag the appointment.
}
{% endhighlight %}
{% endtabs %}

### AppointmentDragging event
Scheduler notifies by [AppointmentDragging](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentDragging_EV.html) when drag the appointment.
[AppointmentDraggingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDraggingEventArgs.html) has following members which provides information for `AppointmentDragging` event.

[Appointment](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDraggingEventArgs~Appointment.html) - Gets the selected appointment.
[From](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDraggingEventArgs~From.html) - Gets the selected appointment start time.
[RefreshAppointment](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDraggingEventArgs~RefreshAppointment.html) - Gets or sets the bool value to update the appointment `StartTime` and `EndTime` while dragging the appointment or not. 
[Resource](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDraggingEventArgs~Resources.html) - Gets the resource details if the selected appointment presenting the resource.
[To](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentDraggingEventArgs~To.html) - Gets the selected appointment end time.

{% tabs %}
{% highlight c# %}
this.Schedule.AppointmentDragging += Schedule_AppointmentDragging;
private void Schedule_AppointmentDragging(object sender, AppointmentDraggingEventArgs e)
{
    //To notify when dragging the appointment.
}
{% endhighlight %}
{% endtabs %}

### AppointmentStartDragging event
Scheduler notifies by [AppointmentStartDragging](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentStartDragging_EV.html) when user start to drag the appointment.
[AppointmentStartDraggingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentStartDraggingEventArgs.html) has following members which provides information for `AppointmentStartDragging` event.

[Appointment](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentStartDraggingEventArgs~Appointment.html) - Gets the selected appointment.

{% tabs %}
{% highlight c# %}
this.schedule.AppointmentStartDragging += Schedule_AppointmentStartDragging;
private void Schedule_AppointmentStartDragging(object sender, AppointmentStartDraggingEventArgs e)
{
    //To notify when start to drag the appointment        
}
{% endhighlight %}
{% endtabs %}
### AppointmentEndDragging event
Scheduler notifies by [AppointmentEndDragging](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentEndDragging_EV.html) when user ends to drag the appointment.
[AppointmentEndDraggingEventArgs](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndDraggingEventArgs.html) has following members which provides information for `AppointmentEndDragging` event.

[Appointment](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndDraggingEventArgs~Appointment.html) - Gets the selected appointment.
[From](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndDraggingEventArgs~From.html) - Gets the selected appointment start time.
[Resource](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndDraggingEventArgs~Resources.html) - Gets the resource details if the selected appointment does have added in resource.
[To](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.AppointmentEndDraggingEventArgs~To.html) - Gets the selected appointment end time.


{% tabs %}
{% highlight c# %}
this.schedule.AppointmentEndDragging += Schedule_AppointmentEndDragging;
private void Schedule_AppointmentEndDragging(object sender, AppointmentEndDraggingEventArgs e)
{
    //To notify when the appointment dragging is end.
}
{% endhighlight %}
{% endtabs %}