---
layout: post
title: rails常用的Callback與Validate方法
tags:
  - callback
  - rails
  - validate
---
# Callback and Validate

## 常用的Callback方法

### 必填
> validates_presence_of :name, :code

### 字串長度
> validates_length_of :name, :minimum => 2 #maximum
> validates_length_of :name, :in => 6..20
> validates_length_of :phone, :is => 11

### 驗證數字
> validates_numericality_of :age, :only_integer => true
> validates_numericality_of :age, :greater_than => 18 
> #greater_than_or_equal_to, equal_to, less_than, less_than_or_equal_to

### 唯一性
> validates_uniqueness_of :code, :scope => :year, :message => "你的 code 重复了", :on => :create

### 格式正確
> validates_format_of :email, :with => /\A([\w>%\+\-]+)@([\w\-]+>)+([\w]{2,})\z/i
> validates_format_of :url, :with =>  /(^$)|(^(http|https):\/\/[a-z0-9]+([\->]{1}[a-z0-9]+)*>[a-z]{2,5}(([0-9]{1,5})?\/.*)?$)/ix

## 可用的Callback
下面列出了所有可用的 Active Record Callback and Validate，按各操作時觸發的顺序：

### 創建、更新
```
before_validation
after_validation
before_save
around_save
before_create
around_create
after_create
after_save
```

### 刪除
```
before_destroy
around_destroy
after_destroy
```

## 跳過Callback
```
decrement
decrement_counter
delete
delete_all
increment
increment_counter
toggle
touch
update_column
update_columns
update_all
update_counters
```

## 關連删除
> has_many :users, dependent: :destroy
