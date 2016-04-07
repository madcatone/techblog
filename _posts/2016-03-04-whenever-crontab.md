---
layout: post
title: "Whenever and Crontab"
date: 2016-03-04 13:54:09
tags: gem whenever crontab
---

# Whenever use guide
some tip for [whenever] using

[whenever]:https://github.com/javan/whenever
## Installation
add  `gem 'whenever'` to *Gemfile*

## Init.
`cd /project`
`wheneverize .`

It generate file => `config/schedule.rb` like:

```
# Use this file to easily define all of your cron jobs.
#
# It's helpful, but not entirely necessary to understand cron before proceeding.
# http://en.wikipedia.org/wiki/Cron
# 出力先のログファイルの指定
set :output, 'log/crontab.log'
# ジョブの実行環境の指定
#set :environment, :production
set :environment, :development
env :PATH, ENV['PATH'] #要用bundle時必須要加
# Example:
#
# set :output, "/path/to/my/cron_log.log"
#
# every 2.hours do
#   command "/usr/bin/some_great_command"
#   runner "MyModel.some_method"
#   rake "some:great:rake:task"
# end
#
# every 4.days do
#   runner "AnotherModel.prune_old_records"
# end

# Learn more: http://github.com/javan/whenever
#every 2.minutes do
    #runner "Wechatuser.reset_remark"
#end

#every '*/2 * * * * ' do
    ##runner "Wechatuser.reset_remark"
    #rake "vote:reset"
#end

every 1.day, :at => '0:05 am' do
  rake "vote:reset"
end
```

## Crontab syntex
```
# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed
```

## Whenever syntex

### ex:1
```
every '*/2 * * * * ' do
    rake "vote:reset"
end
```
exec rake vote:reset every 2 minutes

### ex:2
```
every 1.day, :at => '0:05 am' do
  rake "vote:reset"
end
```
exec rake vote:reset every day at 00:05 am

## *Task*

manual create file in /lib/tasks/_whatever_.rake like:
```
# /lib/tasks/vote.rake
namespace :vote do
  desc "Reset vote"

  task :reset => :environment do
      puts "Reset vote quata to five for development/production"
      Model.all.each do |t|
      	t.tickets = '5'
      	t.save
      end
  end
end
```