---
layout: post
title: Reminder in SfSchedule | Syncfusion
description: This section explains about how to handle the reminder for ScheduleAppointment in SfSchedule.
platform: wpf
control: SfSchedule
documentation: ug
---

# Reminder

Schedule alerts you for particular appointment with reminder window when enable the [EnableReminderTimer](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~EnableReminderTimer.html) property.Reminder window supports to `Dismiss` or `DismissAll` or set the `SnoozeTime` for reminder appointments.

## Setting reminder for an Appointment
Reminder can be set by setting the [EnableReminderTimer](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~EnableReminderTimer.html) property is `true`.The remainder time can be set using the [ReminderTime](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.ScheduleAppointment~ReminderTime.html) property of ScheduleAppointment.
{%tabs%}
{% highlight xaml %}
<Grid>
    <syncfusion:SfSchedule x:Name="schedule" ScheduleType="Month"/>
</Grid>
{% endhighlight %}
{% highlight c# %}


	schedule.EnableReminderTimer = true;

	schedule.Appointments.Add(new ScheduleAppointment

	{

	StartTime = DateTime.Now.Date.AddHours(9),

	EndTime   = DateTime.Now.Date.AddHours(12),

	AppointmentBackground = new SolidColorBrush(Color.FromArgb(0xFf, 0xA2, 0xC1, 0x39)),

	Subject = "Business Meeting",

	ReminderTime = ReminderTimeType.TenHours

	});

	schedule.Appointments.Add(new ScheduleAppointment

	{

	StartTime = currentDate.Date.AddDays(1).AddHours(10),

	EndTime = currentDate.Date.AddDays(1).AddHours(16),

	AppointmentBackground = new SolidColorBrush(Color.FromArgb(0xFf, 0xD8, 0x00, 0x73)),

	Subject = "Auditing",

	ReminderTime = ReminderTimeType.TwoDays

	});

	schedule.Appointments.Add(new ScheduleAppointment

	{

	StartTime = DateTime.Now.Date.AddDays(7).AddHours(10),

	EndTime = DateTime.Now.Date.AddDays(7).AddHours(13),

	AppointmentBackground = new SolidColorBrush(Color.FromArgb(0xFf, 0xF0, 0x96, 0x09)),

	Subject = "Conference",

	ReminderTime = ReminderTimeType.TwoWeeks

	});

{% endhighlight %}
{% endtabs %}

![Reminder-Window](Reminder_images/Reminder_img1.jpeg)

N>Refer the following demo sample for [Reminder](https://github.com/syncfusion/wpf-demos/tree/master/SfSchedule.WPF/Samples/ReminderAlert)

## Configuring Reminder Duration
Reminder supports to set the reminder duration time to remind the appointments by using the [ReminderTime](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.ScheduleAppointment~ReminderTime.html) property of [ScheduleAppointment](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.ScheduleAppointment.html).

**Type of reminder duration**

* None
* ZeroMin
* FiveMin
* TenMin
* FifteenMin
* ThirtyMin
* OneHour
* TwoHours
* ThreeHours
* FourHours
* FiveHours
* SixHours
* SevenHours
* EightHours
* NineHours
* TenHours
* ElevenHours
* EighteenHours
* HalfDay
* OneDay
* TwoDays
* ThreeDays
* FourDays
* OneWeek
* TwoWeeks

{% highlight c# %}
schedule.Appointments[0].ReminderTime = ReminderTimeType.FifteenMin;
{% endhighlight %}


## Create a custom binding for ReminderTime
[ReminderTime](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.ScheduleAppointment~ReminderTime.html) supports to map your custom object with `ScheduleAppointment.ReminderTime`.

{% highlight c# %}
/// <summary>
/// Represents custom data properties.
/// </summary>
public class Meeting
{
    public String Subject { get; set; }
	public DateTime StartTime { get; set; }
	public DateTime EndTime { get; set; }
	public Brush AppointmentColor { get; set; }
	public ReminderTimeType ReminderTime { get; set; }
}
{% endhighlight %}

N>You can inherit this class from `INotifyPropertyChanged` for dynamic changes in custom data.


You can map those properties of `Meeting` class with our [SfSchedule](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule.html) control by using [AppointmentMapping](https://help.syncfusion.com/cr/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~AppointmentMapping.html) and [ScheduleAppointmentMapping](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.ScheduleAppointmentMapping.html).

{% tabs %}
{% highlight xaml %}
<syncfusion:SfSchedule x:Name="schedule" ScheduleType="Month" DataSource="{Binding Meetings}">
	<syncfusion:SfSchedule.AppointmentMapping>
		<syncfusion:ScheduleAppointmentMapping
			SubjectMapping="Subject"
			AppointmentBackgroundMapping="AppointmentColor"
			StartTimeMapping="StartTime"
			EndTimeMapping="EndTime"
			ReminderTimeMapping="ReminderTime">
		</syncfusion:ScheduleAppointmentMapping>
	</syncfusion:SfSchedule.AppointmentMapping>
</syncfusion:SfSchedule>
{% endhighlight %}
{% highlight c# %}
// Schedule data mapping for custom appointments
ScheduleAppointmentMapping dataMapping = new ScheduleAppointmentMapping();
dataMapping.SubjectMapping = "Subject";
dataMapping.StartTimeMapping = "StartTime";
dataMapping.EndTimeMapping = "EndTime";
dataMapping.AppointmentBackgroundMapping = "AppointmentColor";
dataMapping.ReminderTimeMapping = "ReminderTime";
schedule.AppointmentMapping = dataMapping;
{% endhighlight %}
{%endtabs%}

You can download the entire source code of this demo from here [ReminderDemo](https://github.com/SyncfusionExamples/SfSchedule_Reminder_Demo/tree/master/ReminderDemo)

## Handling Reminder events

### ReminderOpening event

**ReminderOpening** – occurs when appearing the reminder window.

`ReminderControlOpeningEventArgs` has following property.

**RemindAppCollection** – Gets list of reminder appointments.

You can prevent the reminder window opening through `ReminderControlOpeningEventArgs.Cancel` property of [ReminderOpening](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~ReminderOpening_EV.html) event.

{% highlight c# %}
this.Schedule.ReminderOpening += Schedule_ReminderOpening;
private void Schedule_ReminderOpening(object sender, ReminderControlOpeningEventArgs e)
{
    e.Cancel = true;
}

{% endhighlight %}

### ReminderClosed event

**ReminderClosed** – occurs when closing the reminder window.
`ReminderControlClosedEventArgs` provides information for [ReminderClosed](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~ReminderClosed_EV.html) event

### ReminderFormActionChanged event

**ReminderFormActionChanged** – occurs when change the reminder window action for the appointment

**ReminderFormActionChangedEventArgs** has following properties which provides information for [ReminderFormActionChanged](https://help.syncfusion.com/cr/cref_files/wpf/Syncfusion.SfSchedule.WPF~Syncfusion.UI.Xaml.Schedule.SfSchedule~ReminderFormActionChanged_EV.html) event.

**Action** - Gets the action of schedule appointments.

**Appointments** – Gets list of appointments that are changed.

**SnoozeTime** – Gets the snooze time of action changed appointments.

You can download the entire source code of this demo from here [ReminderEvents](https://github.com/SyncfusionExamples/SfSchedule_Reminder_Events/tree/master/ReminderEvents)
