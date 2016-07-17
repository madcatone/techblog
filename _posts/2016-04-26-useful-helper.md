---
layout: post
title: "useful helper"
date: 2016-04-26 20:34:41
tags: gem helper
---

# 常用helper

## 邏輯判斷

```
  def controller?(*controller)
    controller.include?(params[:controller])
  end
  def action?(*action)
    action.include?(params[:action])
  end
  ### for hide/show some part of page
  def dev?
    Rails.env == 'development'
  end  
  def prod?
    Rails.env == 'production'
  end
  def admin?
    current_user.is_admin
  end
```

## 時間
```
  ### 距今
  def from_now?(time)
    time = Time.new(1970) if time.nil?
    distance_of_time_in_words(Time.now, time) rescue ''
  end
  ### 年-月-日 時:分:秒 YYYY-mm-dd HH:MM:SS
  def strftime?(time)
    value = time.strftime('%Y-%m-%d %H:%M:%S') rescue '' 
  end
  ### 時:分 HH:MM
  def strfhm?(time)
    value = time.strftime('%H:%M') rescue '' 
  end
  ### 時:分:秒 HH:MM:SS
  def strfhms?(time)
    value = time.strftime('%H:%M:%S') rescue '' 
  end
  ### 年-月-日 YYYY-mm-dd
  def strfymd?(time)
    value = time.strftime('%Y-%m-%d') rescue '' 
  end
  
  ### 本日的月份 Today - Month
  def strfM?
    #value = Time.zone.now.midnight.strftime('%B') rescue '' 
    value = I18n.l(Time.zone.now.midnight, :format => "%B")
  end
  ### 本日的日期 Today - day
  def strfD?
    value = Time.zone.now.midnight.strftime('%d') rescue '' 
  end
  ### 本日是星期幾 Today - whatday
  def strfW?
    value = I18n.l(Time.zone.now.midnight, :format => "%A")
  end
  ### 當下時間 時:分 Today - when
  def strfHM?
    value = Time.zone.now.strftime('%H:%M') rescue '' 
  end
```
