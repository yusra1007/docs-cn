---
title: 控制执行计划
aliases: ['/docs-cn/dev/control-execution-plan/']
---

# 控制执行计划

SQL 性能调优的前两个章节介绍了如何理解 TiDB 的执行计划以及 TiDB 如何生成一个执行计划。本章节将介绍当你确定了执行计划所存在的问题时，可以使用哪些手段来控制执行计划的生成。本章节主要包括以下三方面内容：

- [Optimizer Hints](/optimizer-hints.md)中，我们会介绍如何使用 Hint 来指导 TiDB 生成执行计划。
- 但是使用 Hint 会侵入性地更改 SQL，在一些场景下并不能简单的插入 Hint。在[执行计划管理](/sql-plan-management.md)中，我们会介绍 TiDB 如何使用另一种语法来非侵入地控制执行计划的生成，同时还会介绍后台自动对执行计划进行演进的手段。该手段可用来减轻诸如版本升级等原因造成的执行计划不稳定和集群性能下降的问题。
- 最后在[优化规则及表达式下推的黑名单](/blocklist-control-plan.md)中，我们会介绍黑名单的使用。

除以上手段之外，执行计划还会被一部分系统变量所影响。通过在系统级或会话级对变量进行修改，能够控制执行计划的生成。自 v7.1.0 起，TiDB 引入了一个相对特殊的变量 [`tidb_opt_fix_control`](/system-variables.md#tidb_opt_fix_control-从-v657-和-v710-版本开始引入)。这个变量能够接受多个控制项，用来更细粒度地控制优化器的行为，避免集群升级后优化器行为变化导致的性能回退。详细介绍请参考 [Optimizer Fix Controls](/optimizer-fix-controls.md)。
