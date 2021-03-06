﻿---
title: Lync Server 2013 池故障转移和池故障回复的恢复时间
TOCTitle: 池故障转移和池故障回复的恢复时间
ms:assetid: 902c658f-8442-4d0d-b3ad-bf795ecd550d
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/JJ205079(v=OCS.15)
ms:contentKeyID: 49313595
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的池故障转移和池故障回复的恢复时间

 

_**上一次修改主题：** 2012-09-10_

对于池故障转移和池故障回复，恢复时间目标 (RTO) 的工程目标为 30 分钟。这是管理员确定存在灾难并启动故障转移过程之后，故障转移发生所需的时间。此时间不包括管理员评估情况并作出决策所需的时间，也不包括用户在故障转移完成后再次登录所需的时间。

对于池故障转移和池故障回复，恢复点目标 (RPO) 的工程目标为 30 分钟。这表示测量可能因灾难、因备份服务的复制延迟丢失的数据的时间。例如，如果池在上午 10:00 出现下降，且 RPO 为 30 分钟，则在上午 9:30 至上午 10:00 间写入池的数据可能并未复制到备份池中，可能会丢失。

本文档中的所有 RTO 和 RPO 数字均假定两个数据中心位于同一在两个网站间具有高速度、低延迟传输的世界区域中。这些数字是针对具有 40,000 个同时活动的用户和 200,000 个已启用有关预定义的用户模型（在该模型中，数据复制没有备份日志）的 Lync 的用户的池测量而来的。这些数字可能根据测试和验证性能发生改变。

