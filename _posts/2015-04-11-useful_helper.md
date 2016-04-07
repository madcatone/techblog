---
layout: post
title: "Useful Rails Helper"
date: 2015-04-11 11:21:26
tags: rails helper
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