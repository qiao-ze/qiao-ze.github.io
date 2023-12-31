---
title: 学期工作计划表
keywords: 计划
desc: teedoc 生成静态博客页面, 第一篇博客
author: derk
date: 2023-11-26
tags: hello, blog, teedoc
---




## 上半年工作计划表

正文

```mermaid
 gantt
     dateFormat  YYYY-MM-DD
     title 2024年上半年工作计划表
     section A section
     Completed task             :done,    des1, 2014-01-06,2014-01-08
     Active task                :active,  des2, 2014-01-09, 3d
     Future task                :         des3, after des2, 5d
     Future task2               :         des4, after des3, 5d
 
     section Critical tasks
     Completed task in the critical line :crit, done, 2014-01-06,24h
     Implement parser and jison          :crit, done, after des1, 2d
     Create tests for parser             :crit, active, 3d
     Future task in critical line        :crit, 5d
     Create tests for renderer           :2d
     Add to mermaid                      :1d
 
     section Documentation
     Describe gantt syntax               :active, a1, after des1, 3d
     Add gantt diagram to demo page      :after a1  , 20h
     Add another diagram to demo page    :doc1, after a1  , 48h
 
     section Last section
     Describe gantt syntax               :after doc1, 3d
     Add gantt diagram to demo page      : 20h
     Add another diagram to demo page    : 48h
```

