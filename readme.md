jqtimeline : A timeline Plugin for jQuery
=========================================

[See a demo and examples here](http://goto.io/jqtimeline/)

jquery.jqtimeline is a lightweight, simple and elegent timeline plugin for jQuery to show a set of important events on a timeline. Data input is a simple json arrary of timeline events. This plugin can be easily integrated with any other jQuery plugins. Can be use to create Social apps, showing blog timeline, social posts timeline etc.

Requirements
------------
* [jQuery](http://jquery.com/) (>= 1.7)

Usage
-----

```javascript
$('#someDiv').jqtimeline(options);
```

```options``` is an optional javascript object with parameters explained below.

Options
-------

- **startYear**
int : The stating year of the timeline. 
*default: current_year - 1*

- **numYears**
int : Number of years to be shown on the timeline
*default: 3*

- **gap**
int : This is the distance between the lines on the timeline (in px). If you increase this value length of timeline is increased.
*default: 25*

- **showToolTip**
boolean : To showtooltip when user hovers on an event on timeline.
*default: true*

- **groupEventWithinPx**
int : If the events are very close to each other on the timeline its hard for a user to click on an specific event. This attribute is use to group events within specific px range to show a common tooltip. Check the demo to know more 
*default: 6*

- **events**
Arrar[] : Array of events to be shown on the timeline. Dont confuse this with javascript/jquery event object. The format of event object is given in next section.
*default: null*

- **click**
function : The function to be called when a user clicked on a specific event. This function is passed with jQuery Event object and the Timeline event object.
*default: null*

Example : 
```javascript
$('#myTimeline').jqtimeline({
							numYears:4,
							startYear:2011,
							click:function(e,event){
								alert(event.name);
							}
						});
```

Timeline Event object
---------------------

```javascript
var eventObj = {id:*unique_id*, name:*name_of_the_event*,on:*date_on_which_event_occured*};
```

Methods
-------

After initializing the plugin the plugin object is stored in the html element as jquery data so that you can get it to invoke any method.

```javascript
$('#someDiv').jqtimeline(options);
```
To get the plugin object simple do the following :

```javascript
var timelineObj = $('#someDiv').data('jqtimeline');
timelineObj.method();
```

Where method can be any of the following : 

- **addEvent([event_obj])**
Use to dynamically add timeline event to timeline. Argument can be an Event Object or array of Event Object

	```javascript
	var eventObj = {id=1, name="Dummy Event",on : new Date()};
	timelineObj.addEvent(eventObj);
	```

- **deleteEvent**
Delete a timeline Event from the timeline. Pass the event id or arrayof id to delete event from timeline

	```javascript
	timelineObj.deleteEvent(1);
	timelineObj.deleteEvent([2,3,4]); // Will delete event with id 2,3 and 4
	```

- **getAllEvents**
Get all the event as an array present on the timeline. 

	```javascript
	timelineObj.getAllEvents();
	```

- **getAllEventsElements**
Get all the Html elements shown as events on the timeline. Use to attach an event handler or what ever you want to do with them

	```javascript
	timelineObj.getAllEventsElements();
	```
- - -

This software is made available under the open source MIT License. &copy; 2012 [Gaurav Tiwari](http://www.goto.io)