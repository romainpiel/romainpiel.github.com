---
layout: post
title: "TextChronometer - live 'time ago' TextView"
date: 2013-07-22 17:45
comments: true
categories: 
---
The other day I was using Twitter for Android and I noticed something that we can call a bug. Timestamps in the timeline don't get updated until the list view gets scrolled. If you are an Android developer, you know that this behaviour is expected. Views will only get updated when the adapter calls getView() and the view is getting populated.

![Twitter example](http://d.pr/i/7beE+)

But obviously this is wrong. If I browse my timeline, then let my screen on and get back to it after one hour, I don't want to see the same time.

The reason why developers don't bother is mainly because the SDK doesn't offer any solution with this exact purpose.
- DigitalClock (or its new version, TextClock) are designed to display a simple clock. TextClock can have different formats of date but the "ago" form is not one of them.
- Chronometer could be enough but we'd still have to tweak it to have a nice result.

[Here is my solution](https://github.com/RomainPiel/TextChronometer). I bet it's not perfect but it does the job. The custom view is called [TextChronometer](https://github.com/RomainPiel/TextChronometer/blob/master/TextChronometer/src/main/java/com/romainpiel/textchronometer/TextChronometer.java) (I may want to change that name in the future). Just include it in your layout:

```xml
<com.romainpiel.textchronometer.TextChronometer
     android:id="@+id/timestamp"
     android:layout_width="wrap_content"
     android:layout_height="match_parent"/>
```

Then to set it up:

```java
textChronometer.setTime(timeInMillis);	
```

I'm providing a [sample](https://github.com/RomainPiel/TextChronometer/tree/master/TextChronometer-sample) showing how to use it in an adapter (nothing really fancy in there).

![TextChronometer sample ListActivity](http://d.pr/i/J16b+)

Current state of the project is very basic and I imagine it can be improved a lot. If you have any suggestion, feel free to contribute.