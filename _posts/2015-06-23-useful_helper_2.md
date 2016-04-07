---
layout: post
title: "Useful Rails Helper part2"
date: 2015-06-23 17:15:01
tags: rails helper
---

# 常用helper part2

## 時間
```
  def from_now?(time)
    time = Time.new(1970) if time.nil?
    distance_of_time_in_words(Time.now, time) rescue ''
  end
  ### YYYY-mm-dd HH:MM:SS
  def strftime?(time)
    value = time.strftime('%Y-%m-%d %H:%M:%S') rescue '' 
  end
  ### HH:MM
  def strfhm?(time)
    value = time.strftime('%H:%M') rescue '' 
  end
  ### HH:MM:SS
  def strfhms?(time)
    value = time.strftime('%H:%M:%S') rescue '' 
  end
  ### YYYY-mm-dd
  def strfymd?(time)
    value = time.strftime('%Y-%m-%d') rescue '' 
  end
  ### Today - Month
  def strfM?
    #value = Time.zone.now.midnight.strftime('%B') rescue '' 
    value = I18n.l(Time.zone.now.midnight, :format => "%B")
  end
  ### Today - day
  def strfD?
    value = Time.zone.now.midnight.strftime('%d') rescue '' 
  end
  ### Today - whatday
  def strfW?
    value = I18n.l(Time.zone.now.midnight, :format => "%A")
  end
  ### Today - when
  def strfHM?
    value = Time.zone.now.strftime('%H:%M') rescue '' 
  end
```