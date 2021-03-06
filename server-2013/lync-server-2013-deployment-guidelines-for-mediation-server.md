﻿---
title: Lync Server 2013：中介服务器部署准则
TOCTitle: 中介服务器部署准则
ms:assetid: 7cc22b87-18d9-45e6-8402-015abd20f2e5
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398622(v=OCS.15)
ms:contentKeyID: 49313373
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 中介服务器部署准则

 

_**上一次修改主题：** 2016-12-08_

本主题介绍 中介服务器部署的一些规划准则。阅读这些准则后，建议使用 规划工具创建和查看可能的备用拓扑，这些备用拓扑可以充当您决定要部署的最终定制拓扑的模型。

## 并置或独立的 中介服务器？

默认情况下，在中央站点上的 Standard Edition Server 或 前端池中的 前端服务器上并置 中介服务器。可以处理的公用电话交换网 (PSTN) 呼叫数和池中所需的计算机数取决于以下因素：

  - 中介服务器池控制的对等网关数

  - 通过这些网关的高流量时段

  - 媒体旁路 中介服务器的呼叫占所有呼叫的百分比

规划时，请确保考虑未进行媒体旁路配置的 PSTN 呼叫和 A/V 会议的媒体处理要求，同时考虑处理必须支持的忙时呼叫数量的信号交互所需的处理要求。如果没有足够的 CPU，则必须部署一个独立的 中介服务器池；PSTN 网关、IP-PBX 和 SBC 需划分为子集，这些子集由一个池中的并置 中介服务器和一个或多个独立池中的独立 中介服务器控制。

如果已部署的 PSTN 网关、IP-PBX 或会话边界控制器 (SBC) 不支持与 中介服务器池交互的正确功能（包括如下功能），则需要将它们与包含 中介服务器的独立池相关联：

  - 在池中的 中介服务器之间执行网络层域名系统 (DNS) 负载平衡（或者将流量统一路由到池中的所有 中介服务器）

  - 接受来自池中任意 中介服务器的流量

您可以使用 Microsoft Lync Server 2013 规划工具来评估将前端池与中介服务器并置是否能够处理负载。如果您的环境不能满足这些要求，则必须部署独立的 中介服务器池。

## 中央站点和分支站点注意事项

中央站点的 中介服务器可用于为分支站点的 IP-PBX 或 PSTN 网关路由呼叫。但是，如果部署 SIP 中继，则必须在每个中继终止的站点上部署一台 中介服务器。使用中央站点的 中介服务器为分支站点的 IP-PBX 或 PSTN 网关路由呼叫时，不需要使用媒体旁路。但是，如果可以启用媒体旁路，则可以降低媒体路径延迟，从而改善媒体质量，因为媒体路径不再需要遵循信号路径。媒体旁路还将减少池中的处理负载。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>媒体旁路将不会与每个 PSTN 网关、IP-PBX 和 SBC 进行交互操作。Microsoft 与认证合作伙伴一起对一组 PSTN 网关和 SBC 进行了测试，另外也对 Cisco IP-PBX 进行了一些测试。只有 <a href="http://go.microsoft.com/fwlink/p/?linkid=268730">http://go.microsoft.com/fwlink/p/?LinkId=268730</a> 上的“统一通信开放式互操作性程序 – Lync Server”中列出的产品和版本才支持媒体旁路。</td>
</tr>
</tbody>
</table>


如果要求具有分支站点恢复能力，则必须在分支站点部署 Survivable Branch Appliance 或部署 前端服务器、 中介服务器和网关的组合。（分支站点恢复能力的假定前提是该站点上的状态和会议不可恢复。）有关分支站点的语音规划指导，请参阅 [在 Lync Server 2013 中规划分支站点语音恢复能力](lync-server-2013-planning-for-branch-site-voice-resiliency.md)。

对于与 IP-PBX 的交互，如果 IP-PBX 不能正确支持与多个早期对话的早期媒体交互以及 RFC 3960 交互，则从 IP-PBX 到 Lync 终结点的传入呼叫中的开头问候语可能会被截断。如果中央站点上的 中介服务器为 IP-PBX 路由呼叫，其中路由终止于分支站点，这种行为可能更为严重，因为完成信号需要更长时间。如果遇到这种行为，在分支站点部署 中介服务器是避免截断开头几个词的唯一方法。

最后，如果中央站点具有 TDM PBX，或者 IP-PBX 仍然需要 PSTN 网关，则必须在连接 中介服务器和 PBX 的呼叫路由上部署网关。

<table>
<thead>
<tr class="header">
<th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>要提高独立的中介服务器的媒体性能，应在这些服务器的网络适配器上启用接收方缩放 (RSS)。通过启用 RSS，服务器上的多个处理器能够以并行方式处理传入数据包。有关详细信息，请参阅“Windows Server 中的接收方伸缩改进”，网址为 <a href="http://go.microsoft.com/fwlink/p/?linkid=268731">http://go.microsoft.com/fwlink/p/?LinkId=268731</a>。有关如何启用 RSS 的详细信息，请参阅网络适配器文档。</td>
</tr>
</tbody>
</table>

