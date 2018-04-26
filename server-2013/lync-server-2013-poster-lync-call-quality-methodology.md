﻿---
title: Lync 呼叫质量方法
TOCTitle: 招贴：Lync 呼叫质量方法
ms:assetid: a069f4e5-4f80-4f0f-8657-2e07276b6b41
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Dn593600(v=OCS.15)
ms:contentKeyID: 61084819
ms.date: 12/10/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync 呼叫质量方法

 

_**上一次修改主题：** 2016-12-08_

本文是 [Lync 呼叫质量方法](http://go.microsoft.com/fwlink/?linkid=391841)招贴的配套文章，您可以从下载中心下载此招贴。

![说明 CQM 过程的招贴](images/Dn594589.d239e04a-1c3b-4f0e-93af-88b85198615a(OCS.15).jpg "说明 CQM 过程的招贴")

您可以使用此招贴了解 CQM，即适用于 Lync 2013 和 2010 的呼叫质量方法 (Call Quality Methodology)，它有助于您发现和消除影响包含企业语音功能的 Lync 实施的呼叫质量和用户体验的问题。呼叫质量方法是一个新的故障排除和服务管理框架，可以让相关人员更好地集中精力改进 Lync 中的企业语音服务。在本文中，您可以了解 CQM 的更多信息、它所监控的服务器和解决方案的种类，以及可以对收集的遥测技术数据执行哪些操作。

如果您有关于如何使用 CQM 的问题，您可以将问题提交到 cqmfeedback@microsoft.com。

此招贴解释了以下方面的内容：

  - 什么是 Lync CQM？

  - 设置优先级：运行趋势查询

  - PCD

  - 托管/非托管

  - 服务器设备路线

  - 最后一公里路线

  - 终结点路线

  - 服务管理

  - 棋盘游戏规则

## 什么是 Lync CQM？

呼叫质量方法是一个新的故障排除和服务管理框架，可以让相关人员更好地集中精力改进 Lync 中的企业语音服务。如果使用 CQM，只需要较少的努力即可确保企业语音服务的呼叫质量和用户满意度。[Lync Server 网络连接指南](http://go.microsoft.com/fwlink/p/?linkid=390677)中更为详细地介绍了 CQM。本文和配套招贴是关于这方面的内容的概要。

CQM 将系统故障排除细分为三条路径或“路线”。它们是：服务器设备路线 - 关注服务器和服务器之间的链路；终结点路线 - 关注用于进行呼叫的用户设备和介质；最后一公里路线 - 关系到传统电话交换网呼叫的集成。

每条路线分成与特定领域或主题相关的若干段，在每个段都进行相关定义，定义什么样的级别是可接受的质量级别、为达到该质量级别而采取的操作、为维护该质量级别而采用的服务管理计划，然后在介绍完这些内容后接着讨论下一主题。

该招贴以三人棋盘游戏的形式展示了 Lync CQM，在该游戏中，三位游戏者各走一条路线。下载中附带的牌用于模拟呼叫质量必须克服的障碍。三条路径中包含了关于目标的提示和建议、如何到达目标，以及针对在实际应用中首先采用哪条路线的设置优先级指南（在游戏中，平等对待所有三条路线）。

CQM 在早期版本的 Lync 中使用起来怎样？CQM 是针对 Lync 2013 的新服务，但其大部分功能可以适应在 Lync 2010 中使用。CQM 在一定程度上可以用于 Microsoft Office Communicator，但对此未经测试，不提供支持。

如果您有关于如何使用 CQM 的问题，您可以将问题提交到 cqmfeedback@microsoft.com。

## 设置优先级：运行趋势查询

在 CQM 中，第一步是用两个星期时间运行每一个趋势查询，然后分析结果。按最大流参与者、最高不良流比率和管理领域（您控制的领域）设置修正操作的优先级。如果音频/视频多点控制单元 (AV MCU) 或中介查询显示的结果较差，请从红色路线（即服务器设备路线）开始。 如果有线或无线查询显示的结果较差，请从蓝色路线（即最后一公里路线）开始。如果 VPN 或外部查询显示的结果较差，请从绿色（即终结点路线）开始。

选择某条路线开始后，定义每个区域的目标（申明），努力达到该目标（到达），然后实施相应的过程以盯住目标（维护）。您也可以将该招贴作为一个游戏，用来帮助理解 CQM 背后的原理。

## PCD

PreCall Diagnostics 工具 (PCD) 将帮助您识别和诊断您的外围网络中的问题（QoE 数据库不收集关于您的边缘或外围网络的信息），还可用于对最后一公里中的连接进行故障排除。该工具既作为 Windows 8 Modern 应用提供，又作为 Windows 桌面应用提供，可从 http://apps.microsoft.com/windows/en-us/app/lync-2013-precall-diagnostics/9607fe33-2b51-403d-9615-c23f248e7c88 获得。

## 托管/非托管

Lync Server 部署和网络基础结构通常可分为托管空间和非托管空间。托管空间包括整个内部有线网络和服务器基础结构。非托管空间是无线基础结构和外部网络基础结构。

进行此区分增加了数据的清晰性，有助于组织集中精力处理对用户的语音和视频质量有明显影响的工作负载。用户对于从您拥有的基础结构（托管）进行的呼叫和从部分受控于某些其他实体的基础结构（非托管）进行的呼叫有不同的预期。这并不是说为了获得出色的 Lync Server 体验，要将无线用户保留为使用他们自己的设备。

提升非托管空间中的语音质量要求在托管空间中具有较高的质量。考虑将无线 (Wi-Fi) 作为托管还是非托管空间取决于您的组织。在这两种空间中实现运行状况正常的环境所需的技术是不同的，所用的解决方案亦不同。

## 服务器设备路线

服务器设备路线的第 1 段关系到 Lync 实施中的实际服务器。收集关于服务器本身和其在实施中所担任的角色的 KHI 数据，分析结果。必要时，修正发现的任何问题。与 KHI 招贴配套的关于[关键运行状况指示器](lync-server-2013-poster-key-health-indicators.md)的文章中提供了有关此主题的更多详细信息。

下一段关系到 AV MCU 服务器和中介服务器之间的媒体流。首先确定您的不良流阈值的目标。不良流通常 PacketLossRate \> 0.01 或 PacketLossRateMax \> 0.05。需要的另一个目标是 PoorStreamsRatio \< 2%。接下来，使用详细查询查找具有不良流的 AVMCU 和中介服务器对，调查产生不良流的原因，考虑不良流路径中的网络设备，修正不良流，为网络设备定义最优或“金牌”配置。为了维持您的成就，实施相应的流程和工具来管理配置漂移、报告新的问题领域。

接下来，检查中介服务器和公用电话交换网 (PSTN) 网关之间的媒体流。首先确定您的不良流阈值的目标。不良流通常 PacketLossRate \> 0.01 或 PacketLossRateMax \> 0.05。需要的另一个目标是 PoorStreamsRatio \< 2%。接下来，使用详细查询查找具有不良流的中介服务器和网关对，调查产生不良流的原因，考虑不良流路径中的网络设备，修正不良流，为网络设备定义最优或“金牌”配置。为了维持您的成就，实施相应的流程和工具来管理配置漂移、报告新的问题领域。

最后，检查 PSTN 网关的运行状况指标。确定显示运行状况的统计信息并根据它们定义目标。由于可以使用许多能使用的网关，因而此处不提供具体指导。确定目标后，根据需要进行修正以达到目标；在该过程中您可能会为网关定义“金牌”或最优配置。为了维持您的成就，实施相应的流程和工具来管理配置漂移、报告新的问题领域。请注意，固件和软件更新可能会更改您的配置或导致您更改“金牌”配置的定义，所以在进行这些活动时应谨慎。

## 最后一公里路线

在将客户端连接到网络所用的两种方式中，普遍预期有线方式可提供最高的质量，所以这种方式必须是您处理最后一公里问题时最初关注的焦点。可使用 CQM 有线查询 (LastMile\_0\_Wired) 和它提供的不良流比率。对具有 300 个以上的流的站点，建议定义 \< 5% 的目标 PoorStreamsRatio。为达到您的目标，按从最差到最好的顺序修正子网，并实施 QoS。

优化有线连接的质量后，提高无线连接质量就比较容易了，因为在每个位置无线基础结构都位于有线内核之上。在具有良好的有线连接质量的站点中，出现不良无线流一定是由特定的无线组件导致的。CQM 无线查询 (LastMile\_1\_Wireless) 在某个日期范围内运行，并返回您的环境中 Lync 客户端与会议服务器或中介服务器之间双向发生的所有内部无线流。对具有 300 个以上的流的站点，建议定义 \< 5% 的目标 PoorStreamsRatio。为达到您的目标，按从最差到最好的顺序修正子网，并实施 QoS。

## 终结点路线

首先使用头戴式耳机或其他已知可在使用 Lync 时产生质量可接受的流的设备来探查终结点路线。对具有 100 个以上的流的实施，建议定义 \> 3.6 的目标 AvgSendListen MOS。通过找出存在问题的设备并进行修复或更换来达到目标。

接下来，检查用于处理最终用户呼叫的设备或电脑。建议的目标质量指标是 \> 1 的 AudioMic GlitchRate。在确定用户系统的最佳系统配置时，定义包括驱动程序版本在内的“金牌”电脑配置。

现在检查音频流在 Lync 终结点系统中使用的网络路径，该路径可能成为导致音频质量较差的原因。如果音频通过 VPN 连接进行传输，您可能会遇到延迟问题。一个内部 Lync 客户端如果无法为双方呼叫或对等呼叫建立到另一个内部 Lync 客户端的直接流媒体，就会使用通过 Lync 边缘服务器中继的路径，这同样会导致延迟问题，同时增加了出现丢失和抖动的可能性。建议您定义这样一个质量指标 - 通过 VPN 的媒体的百分比：0%。在您进行修正以达到设置的目标时，找出存在问题的子网并调查防火墙规则、包封装器和其他相关网络设备配置。

IP 数据包可以使用传输控制协议 (TCP) 或用户数据报协议 (UDP)。TCP 最适合用于数据流。UDP 是无连接的，用于媒体时更有效率，因为 TCP 恢复机制无法处理实时媒体中的丢失问题。Lync 始终优先选用 UDP，但如果无法建立 UDP 会话，就会恢复为使用 TCP。基于 TCP 的媒体会话呈现的质量比基于 UDP 的差。建议使用这样一个质量定义 - 基于 TCP 的连接所占百分比：0%。在您进行修正以达到设置的目标时，找出存在问题的子网并调查防火墙规则、包封装器和其他相关网络设备配置。

## 服务管理

服务管理是 CQM 的终态，是所有三条路线的终点。为保持较高级别的呼叫质量，监视以下领域：

1.  **用户** - 修正活动的结果应体现为用户满意度明显提高。对此您可以通过问题调查表或其他反馈机制进行衡量。您还可以公布质量指标。

2.  **流程** - 定义将 CQM 付诸实践的每日、每周和每月流程。监视频率开始时在进行修正期间较高（每日），稳定后变低（每月）。

3.  **工具** - 确定用于衡量和修正的工具。您可能会发现自动运行 CQM 查询对支持您的流程很有用。进行修正（例如对网络元素强制应用标准配置或对不良流中的丢失问题进行故障排除）可能需要其他工具。

## 棋盘游戏规则

您可以将此招贴用作 CQM 实施的参考，或作为一个用来实践相关概念的游戏。要玩此游戏，您需要一个六个面的骰子和提供的牌。牌的可下载版本可以打印在标准 Avery 5871 商业卡片上。

该游戏是 3 人游戏。游戏者可以使用三条路径达到所需质量并到达中心服务管理状态，这三天路径是：服务器设备、终结点、最后一公里。每条路的沿途设有停靠站，您在那里申明质量目标、达到目标、维护系统的某个方面。将牌放在上述指示的区域，然后抽 5 张牌。检查抽取的牌并将其放到相关的棋盘段上。每个游戏者逐步穿过其路径上的牌，穿过时申明质量目标、到达这些目标、维护服务级别。在所有游戏者都达到中心的服务管理状态后，游戏结束。游戏牌下载中提供了更详细的规则。

要**申明**质量目标，请检查适用于该目标的参数，大声说出您愿意选择接受哪些，不愿意接受哪些。我们推荐了起点，但必须由您作最后决定。KHI 数据例外，对于 KHI 数据例，应使用由 Microsoft 确立的标准。请参阅配套的 KHI 招贴。

要**到达**游戏中的目标，请使用提供的牌替代 KHI 数据和系统查询。如果游戏开始时您没有抽到与给定方面相关的牌，您可以继续通过它。如果抽到相关牌，则投掷骰子。如果掷出的点数小于牌上指示的数字，您就赢了。如果掷出的点数等于或大于指示的数字，则必须再次抽牌。如果牌指示两个或更多个游戏者需要投掷骰子，他们都必须有效地投掷骰子。

要在游戏中进行**维护**，请大声说出与 Lync 环境的那方面相关的服务管理计划。

## 另请参阅

#### 其他资源

[Lync Server 网络连接指南](http://go.microsoft.com/fwlink/p/?linkid=390677)  
[关键运行状况指示器：维护正常运行的 Lync 服务器的基础](http://go.microsoft.com/fwlink/?linkid=391838)  
[Lync 呼叫质量方法](http://go.microsoft.com/fwlink/?linkid=391841)
