---
title: 从正负样本研究DME和DGME
date: 2022-08-10 19:27:35
tags: paper阅读笔记
---

## Paper Information

- Title

Learning Disjunctive Multiplicity Expressions and Disjunctive Generalize Multiplicity Expression From Both Positive and Negative Examples.
- Author

Yeting Li, Haiming Chen, Zixuan Chen

## Introduction

### Background

XML是什么？XML 被设计用来结构化、存储以及传输信息。（摘自菜鸟教程的定义）

```xml
<note>
<to>Tove</to>
<from>Jani</from>
<heading>Reminder</heading>
<body>Don't forget me this weekend!</body>
</note>
```

XML Schema在XML管理中发挥重要作用，好处有：
- 查询处理与优化
- 数据库应用开发
- 数据整理与交换

但是XML schema的使用只占30.2%，能正常用的只有24.5%。因此对于schema合理性的推断与检查，就显得非常重要。
Schema推断还可以用于schema清洗与噪声处理。

- XML的相关介绍：https://www.runoob.com/xml/xml-intro.html

- 从给定的schema推断其架构：https://docs.microsoft.com/zh-cn/dotnet/api/system.xml.schema.xmlschemainference.inferschema?redirectedfrom=MSDN&view=net-6.0#overloads

- Positive Example: https://xueshu.baidu.com/usercenter/paper/show?paperid=8b14ee2751b4749a422b0c0804add03b


### Motivation
Focus: unordered schemas

研究出发点：
1. Tree pattern query minimization. Schema是树结构，因此对其做合理的类型推断可以有效降低在这棵树上搜索时所需要的时空资源。

2. Boost learning algorithm for twig queris（小枝查询），其实也是做查询上的优化策略。

重要概念：
1. DMS: Disjunctive Multiplicity Schema
2. DTD: Document Type Definition
3. RE: Regular Expression
4. DME: Disjunctive Multiplicity Expression
5. Positive & Negative Example

之前的研究，主要立足于positive examples。但如果反过来从negative examples做研究，可能会更有用：
1. negative example有helpful information in practice
2. 只用positive examples的学习算法需要的样本太大，一般不能有那么多做支持
3. negative example可以有效缩小solution space

### Our Work

从positive example和negative example中，对DME做研究 -> 但这是一个NP-complete问题 -> 用GA（遗传算法）来解决这一问题

算法：iDME

也支持仅用positive或negative的example做learning。

DME可扩展至DGME（Disjunctive generalized multiplicity expression）

总结：
- 仅用positive example：iDME和state-of-the-art都可以有可接受的结果
- 用positive和negative example：对于DMEs和DGMEs都支持高精准度

### Contribution

- positive和negative两种example都用，支持并行的GA算法
- 提出DGME，并有更加精准的iDGME
- DME和DGME都可获得较高的精确度

### Extension