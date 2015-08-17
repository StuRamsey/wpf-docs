---
layout: post
title: Zooming-and-Panning
description: zooming and panning
platform: wpf
control: SfMap
documentation: ug
---

# Zooming and Panning

The Zooming and Panning feature of the Map control allows you to zoom in and out and navigate the map.

## Zooming

The zooming feature enables you to zoom in and out of the map to show in-depth information. It is controlled by the ZoomLevel property of the map. When the zoom level of the Map control is increased, the map is zoomed in. When the zoom level is decreased, then the map is zoomed out.

### Properties Related to Zooming

The following properties are related to the zooming feature of the Maps control:

1. ZoomLevel
2. EnableZoom
3. MinZoom
4. MaxZoom

#### ZoomLevel

ZoomLevel is the primary property of the zooming feature. It controls the map’s scale size while zooming. Initially, the zoom level is 1. ZoomLevel cannot be less than 1.

#### EnableZoom

The EnableZoom property enables or disables the zooming feature. A “True” value of this property enables the zooming feature and “False” disables the zooming feature.

#### MinZoom

The MinZoom property is used to set the minimum zoom level of the map. 

####  MaxZoom

The MaxZoom property is used to set the maximum zoom level of the Map control.

Sample code for setting zooming feature properties:

{% highlight xml %}


[XAML]

<syncfusion:SfMap ZoomLevel="3" MinZoom="1" MaxZoom="20" EnableZoom="True">                

</syncfusion:SfMap >
{% endhighlight %}


### Methods to Zoom the Map

Maps can be zoomed by using the following methods:

1. By changing the ZoomLevel.
2. Through the Zoom method.
3. Through the mouse scroll.

#### Changing the ZoomLevel

A map can be zoomed by changing the zoom level of the Map control. Incrementing the ZoomLevel, zooms in the map and decrementing the ZoomLevel, zooms out the map.

#### Through the Zoom method

Maps can be zoomed through the Zoom method. The Zoom method has the parameter zoom value. The map can be zoomed or scaled with the zoom value parameter.

{% highlight C# %}

[C#]   

   SfMap syncMap = new SfMap();

   ShapeFileLayer shapeLayer = new ShapeFileLayer();

   shapeLayer.Uri = "MapApp.ShapeFiles.world1.shp";

   syncMap.Layers.Add(shapeLayer);

   syncMap.Zoom(5);

{% endhighlight %}

#### Through a mouse wheel event

In addition to the pinching event, the map can be zoomed with mouse events.  When the mouse is scrolled up, the map is zoomed in. When the mouse is scrolled down, the map is zoomed out.

![](Zooming-and-Panning_images/Zooming-and-Panning_img1.png)



### Panning the map

The panning feature enables navigation through the map.

Properties related to Panning are:

* EnablePan

#### Enable and disable pan

The EnablePan property enables or disables the panning feature of the map. A “True” value enables the panning feature. A “False” value disables the panning feature of the map.

{% highlight xml %}


<syncfusion:SfMap ShowCoords="True" LatitudeLongitudeType="Decimal" EnablePan="True">         

            <syncfusion:SfMap.Layers>

                <syncfusion:ShapeFileLayer   Uri="MapApp.world1.shp">                    

                </syncfusion:ShapeFileLayer>

            </syncfusion:SfMap.Layers>

        </syncfusion:SfMap >
{% endhighlight %}


### Ways to pan the map

There are two methods for panning the map. They are:

1. Through the Pan method.
2. By dragging the map.

#### Through the Pan method

The map can be panned with the Pan method in the Maps control. The Pan method has two parameters: x and y.  The map is translated with respect to the x and y parameters.

##### Code sample for the Pan method:

{% highlight C# %}

[C#]   

        SfMap syncMap = new SfMap();

            syncMap.EnablePan = true;

            ShapeFileLayer layer = new ShapeFileLayer();

            layer.Uri = "App2.world1.shp";

            syncMap.Layers.Add(layer);

            syncMap.Pan(200, 200);
{% endhighlight %}


#### Dragging the map

The map can be panned by dragging the map through mouse interactions. This works automatically for touch events.

> _Note: The map can be panned only when some parts of the map are outside the view of the control._

![](Zooming-and-Panning_images/Zooming-and-Panning_img2.png)


