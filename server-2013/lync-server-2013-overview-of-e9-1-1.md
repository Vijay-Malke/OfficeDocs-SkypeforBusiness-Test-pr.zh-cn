﻿---
title: Lync Server 2013：E9-1-1 概述
TOCTitle: E9-1-1 概述
ms:assetid: c01e6774-bc9f-4c5b-a60b-478b7317b2b7
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg412936(v=OCS.15)
ms:contentKeyID: 49314120
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中的 E9-1-1 概述

 

_**上一次修改主题：** 2012-10-29_

Microsoft Lync Server 2013 支持来自 Lync 客户端和 Lync Phone Edition 设备的增强型 9-1-1 (E9-1-1) 呼叫。将 Lync Server 配置用于 E9-1-1 时，从 Lync 2013 或 Lync Phone Edition 发出的紧急呼叫包括 位置信息服务数据库中的紧急响应位置 (ERL) 信息。ERL 包含市政（即街道）地址，以及有助于确定在办公楼和其他多租户设施中的更精确位置的其他信息。当用户发出紧急呼叫时， Lync Server 会通过 中介服务器将呼叫音频以及位置和回拨信息路由到 E9-1-1 服务提供商。E9-1-1 服务提供商会使用呼叫者的市政地址，将呼叫路由到为呼叫者的位置提供服务的公共安全应答点 (PSAP)，并沿着 PSAP 用来查找呼叫者的 ERL 的紧急服务查询键 (ESQK) 进行发送。

Lync Server 支持通过以下两种方法将紧急呼叫路由到 E9-1-1 服务提供商：

  - 到合格的 E9-1-1 服务提供商的会话初始协议 (SIP) 中继连接

  - 到基于公用电话交换网 (PSTN) 的 E9-1-1 服务提供商的紧急位置标识号 (ELIN) 网关

使用 SIP 中继 E9-1-1 服务提供商时，可以将 ERL 添加到 位置信息服务数据库，然后根据 E9-1-1 服务提供商所维护的主街道地址指南 (MSAG) 验证这些位置。如果 E9-1-1 服务提供商收到不含位置信息的呼叫或所含位置未根据 MSAG 进行验证的呼叫，则该服务提供商会将该呼叫路由至全国/地方紧急呼叫响应中心 (ECRC)，该中心配备的经过专门培训的员工可口头获得呼叫者的位置，并且在可能的情况下手动将该呼叫路由至相应的 PSAP。（一些 SIP 中继 E9-1-1 服务提供商还向客户提供 ECRC 的 PSTN 外线直拨分机 (DID) 号码，这在 SIP 中继因任何原因失败时提供了路由 9-1-1 呼叫的备选方式。）

与时分多路复用 (TDM) 电话和基于 IP 的位置固定的专用交换机 (PBX) 电话不同， Lync 终结点可以是移动的。在部署 E9-1-1 功能时， Lync Server 有助于确保无论呼叫者身在何处，都会将紧急呼叫路由到为呼叫者位置提供服务的 PSAP。例如，如果用户的总部位于华盛顿州的雷德蒙德，而用户从位于堪萨斯州的威奇托的分支机构的计算机发出紧急呼叫，则基于 SIP 中继或 PSTN 的 E9-1-1 服务提供商会将该呼叫路由至威奇托的 PSAP，而不是雷德蒙德的 PSAP。

使用 ELIN 网关时，也可以将 ERL 添加到 位置信息服务数据库，但是仍包括每个位置的 ELIN 号码。ELIN 号码会在紧急呼叫过程中变为紧急呼叫号码。然后，您必须确保 PSTN 运营商将 ELIN 上载到自动位置标识 (ALI) 数据库。

<table>
<colgroup>
<col style="width: 100%" />
</colgroup>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>连接 Lync 的模拟设备无法接收来自 位置信息服务的位置信息或将位置传输到 E9-1-1 服务提供商。如果您使用 SIP 中继 E9-1-1 服务提供商选项并需要通过模拟电话支持 E9-1-1，则有以下两个选项：
<ul>
<li><p><strong>传统 PS-ALI 选项</strong>   如果您在每个站点（其中部署了模拟电话且每个模拟电话都有一个 DID）上都具有本地 PSTN 网关，则可以通过专用交换机/自动位置标识 (PS-ALI) 服务提供商直接设置模拟设备的位置。在这种情况下，您可配置精心制作的 Lync 语音策略并将其分配给模拟设备联系人对象，以便从这些电话发出的 E9-1-1 呼叫可直接通过本地网关路由至为该站点服务的 PSTN 提供商（而不是将该呼叫路由至 E9-1-1 服务提供商 SIP 中继）。发出紧急呼叫后，与 PSTN 中继关联的 PS-ALI 提供商的数据库会将每个模拟电话的 DID 映射到一个物理位置并将此位置提供给 PSAP。每当将电话移至不同的 ERL 时，必须通过 PS-ALI 服务提供商更新这些记录。</p></li>
<li><p><strong>E9-1-1 服务提供商选项</strong>   您可向 E9-1-1 服务提供商注册模拟电话 DID 及其对应的 ERL，前提是 E9-1-1 服务提供商支持这样做。如果提供商从 Lync Server 收到不含 PIDF-LO 数据的呼叫，则提供商可查看呼叫者的 DID 号码是否存在数据库匹配项。通过使用从数据库检索到的 ERL，提供商可自动将紧急呼叫路由至正确的 PSAP，该 PSAP 将收到模拟设备的 DID 和允许调度程序查找呼叫者位置的 ESQK 记录。</p></li>
</ul>
如果您使用 ELIN 网关选项并需要通过模拟电话支持 E9-1-1，则可以直接向 PS-ALI 服务提供商提供模拟设备的位置，如上面第一个选项中所述。</td>
</tr>
</tbody>
</table>


从 Lync Server 的角度来看，E9-1-1 过程可以分为两个阶段：

  - 阶段 1：获取位置

  - 阶段 2：将紧急呼叫路由至 E9-1-1 服务提供商

本节介绍这些阶段的工作原理。

如果您计划将基础结构配置为自动检测客户端位置，则首先需要确定将使用哪些网络元素将呼叫者映射到不同位置。有关可能的选项的详细信息，请参阅 [在 Lync Server 2013 中定义用于确定位置的网络元素](lync-server-2013-defining-the-network-elements-used-to-determine-location.md)。

## 本节内容

  - [在 Lync Server 2013 中获取位置](lync-server-2013-acquiring-a-location.md)

  - [在 Lync Server 2013 中使用 SIP 中继路由 E9-1-1 呼叫](lync-server-2013-routing-e9-1-1-calls-by-using-a-sip-trunk.md)

  - [在 Lync Server 2013 中使用 ELIN 网关路由 E9-1-1 呼叫](lync-server-2013-routing-e9-1-1-calls-by-using-an-elin-gateway.md)

