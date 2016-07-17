---
layout: post
title: "techdoc markdown"
date: 2016-05-08 10:54:12
tags: gem document markdown
---

# 專案常用技術文檔格式

## 项目 

### 工时/timesheet 

| 字段名 | 英文名 | 字段类型 | 主键 |备注 | 
| :--------- |:---------:| -------------:| ------:| ------:| 
| 日期 * | date | date | | | 
| 项目名称 * | project_id | integer | true | | 
| 所属任务 * | task_id | integer | | | 
| 填报人 * | user_id | integer | true | | 
| 部门 | deparment_id | integer | true | | 
| 时间类型 * | kind | integer | | | 
| 工时(小时) | hours | float | | | 
| 状态 | state | string | | | 
| 来源 | source | integer | | | 
| 审批人 | approve_id | integer | | |
| 成本中心 | cost | decimal | | | 
| 工作内容 | content | string | | | 
| 存在问题 | issue | string | | | 
| 解决方案 | solution | string | | |

``` 
 状态:
   已保存:saved
   待审批:approving
   未通过:rejected
   已通过:approve 
 ---

 时间类型:
   1 :正常工时
   2 :加班工时
   3 :休假工时 
 ---

 来源:
   1 :填写
   2 :补填
   3 :导入 
``` 
	timesheet:
 		modelname: "工时管理"
		formname: "工时"
		date: "日期"
		project_id: "项目名称"
		task_id: "所属任务"
		user_id: "填报人"
		deparment_id: "部门"
		kind: "工时类型"
		source: "来源"
 		approve_id: "审批人"
		cost: "成本"
		content: "工作内容"
		issue: "存在问题"
		solution: "解决方案" 

>project_id:integer:index task_id:integer user_id:integer:index deparment_id:integer kind:integer hours:float state:string source:integer approve_id:integer 'cost:decimal{18,6}' content:text issue:text solution:text