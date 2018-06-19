﻿---
title: Lync Server 2013：SIP 中继概述
TOCTitle: SIP 中继概述
ms:assetid: 204f2c21-436f-4b2d-93ea-d6db98fa2952
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398285(v=OCS.15)
ms:contentKeyID: 49312217
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的 SIP 中继概述

 

_**上一次修改主题：** 2012-10-05_

部署 SIP 中继对于简化组织的电信和准备实时通信的最新增强功能来说可能是重要的一步。SIP 中继的主要优点之一是可以在中央站点中合并组织的公用电话交换网 (PSTN) 连接，与早期的时分多路复用 (TDM) 中继相反，后者通常要求在每个分支站点部署单独的中继。

## Lync Server 中的 SIP 中继

Lync Server 2013 SIP 中继功能支持下列内容：

  - 企业防火墙内外的企业用户可以拨打由符合 E.164 标准的号码指定的本地电话或长途电话，该电话将作为相应服务提供商的一项服务终止于 PSTN 上。

  - 通过拨打与企业防火墙内外的企业用户关联的外线直拨分机 (DID) 号码，任何 PSTN 订阅者都可以与该企业用户取得联系。

## 节省成本

可以大大节省与 SIP 中继有关的成本：

  - 通过 SIP 中继拨打长途电话通常可以大幅降低成本。

  - 可以节省可管理性成本并降低部署的复杂性。

  - 如果可以以极低的成本将 SIP 中继直接连接到 ITSP，则可以消除基本速率接口 (BRI) 和主速率接口 (PRI) 的费用。在 TDM 中继中，服务提供商按分钟对呼叫计费。SIP 中继的成本可能基于带宽使用，能够以更小、更经济的增量购买带宽。（实际成本取决于选择的 ITSP 的服务模型。）

## SIP 中继与承载 PSTN 网关或 IP-PBX

由于 SIP 中继直接连接到服务提供商，因此可以消除 PSTN 网关及其管理成本和复杂性。使用 SIP 中继可以减少维护和管理工作，从而大幅节省成本。

## 扩展的 VoIP 服务

语音功能通常是部署 SIP 中继的主要动机，但是语音支持只是第一步。通过使用 SIP 中继，可以扩展 VoIP 功能和启用 Lync Server 2013，从而提供更丰富的一组服务。例如：

  - 针对未运行 Lync Server 2013 的设备的增强状态检测可以更好地与移动电话集成，从而使您可以查看用户使用移动电话通话的时间。

  - 通过使用 E9-1-1 紧急呼叫，应答 911 呼叫的机构可以通过电话号码确定呼叫者的位置。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>与 ITSP 联系以获取他们支持并且可以为贵组织启用的服务列表。</td>
</tr>
</tbody>
</table>
