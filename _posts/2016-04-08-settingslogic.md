---
layout: post
title: "SettingsLogic"
date: 2016-04-08 11:15:20
tags: gem settingslogic
---

# SettingsLogic

## Install
add in Gemfile
`gem 'settingslogic'`

## How to use
### 1. Establish a rb file in model
```
class Settings < Settingslogic
  source "#{Rails.root}/config/settings.yml"
  namespace Rails.env
end
```

### 2. Establish a yml file in config/settings.yml
```
defaults: &defaults
  cool:
    saweet: nested settings

development:
  <<: *defaults

test:
  <<: *defaults

production:
  <<: *defaults
```

## Use it
```
>> Rails.env
=> "development"

>> Settings.cool
=> "#<Settingslogic::Settings ... >"

>> Settings.cool.saweet
=> "nested settings"
```