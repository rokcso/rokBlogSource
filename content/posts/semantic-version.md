---
title: "语义化版本控制规范 2.0.0"
date: "2023-06-29"
draft: false
slug: "semantic-version"
summary: ""
tags: ["笔记"]
description: "seo description"
toc: true
readTime: true
autonumber: true
math: true
showTags: false
hideBackToTop: false
---

> link: [语义化版本控制规范 2.0.0](https://semver.org/lang/zh-CN/)

版本号格式：主版本号.次版本号.修订号

版本号递增规则：

1. 主版本号：当有不向下兼容的功能发布时
2. 次版本号：当有可向下兼容的功能发布时
3. 修订号：当有可向下兼通的**问题修正**发布时

注意：构建号与版本号不同，不受此规范约束。

## 规范重点摘要

1. 标准的版本号必须使用 X.Y.Z 格式（对应 major.minor.patch），且 X、Y、Z 为非负整数，数字前方禁止补零（如 01 是不被允许的），禁止留白。范例：1.3.2、3.0.0 等等
2. 新版本号标记的内容发布后，禁止再使用该版本号发布任何内容，往后任何内容变更都必须新起一个版本号
3. 开发初始阶段（非稳定版），主版本号设定为零
4. 每当主版本号递增时，次版本号和修订号必须归零；每当次版本号递增时，修订号必须归零
5. 先行版本号（非稳定版）标注在正式版本号之后，使用「-」连接，先行版本号由 ASCII 字母、数字 [0-9A-Za-z] 以及分隔符英文句点「.」组成，数字前方禁止补零，禁止留白。范例：1.0.0-alpha、1.0.0-beta.1、1.0.0-0.2.1、1.0.0-x.7.a.13 等等
6. 版本编译信息标注在（正式或先行）版本号之后，使用「+」连接，版本编译信息标识符由 ASCII 字母、数字 [0-9A-Za-z] 以及分隔符英文句点「.」组成，禁止留白。范例：1.0.0+001、1.0.0-beta.1+sha.34f8h4 等等

## 版本优先级

1. 排序时仅考虑主版本号、次版本号、修订号、先行版本号进行比较，版本编译信息不影响版本优先级

注意：避免使用难以明确优先级的先行版本号。先行版本一般可使用 alpha < beta < rc 标识。

## 其他提示

1. 初始开发版本建议为 0.1.0
2. 当软件要被用于生产环境时就可以发布 1.0.0
3. v2.3.1 不是一个语义化版本号，v 只是 version 的缩写，是版本号的标签
4. 检查语义化版本号正确性的正则表达式：

```javascript
^(?P<major>0|[1-9]\d*)\.(?P<minor>0|[1-9]\d*)\.(?P<patch>0|[1-9]\d*)(?:-(?P<prerelease>(?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*)(?:\.(?:0|[1-9]\d*|\d*[a-zA-Z-][0-9a-zA-Z-]*))*))?(?:\+(?P<buildmetadata>[0-9a-zA-Z-]+(?:\.[0-9a-zA-Z-]+)*))?$
```

Link: https://regex101.com/r/Ly7O1x/3/