﻿---
title: Lync Server 2013：持久聊天服务器的组件和拓扑
TOCTitle: 持久聊天服务器的组件和拓扑
ms:assetid: 6a0a14a0-baad-44e9-b26e-4d192c0a0e70
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Gg398500(v=OCS.15)
ms:contentKeyID: 49313151
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Lync Server 2013 持久聊天服务器的组件和拓扑

 

_**上一次修改主题：** 2012-10-05_

持久聊天服务器既支持单服务器配置，也支持多服务器配置。 持久聊天服务器还可以在 Lync Server 2013Standard Edition Server 上运行。这些配置包括以下 持久聊天服务器组件和拓扑。

## 持久聊天服务器组件

安装最新版本的 持久聊天服务器需要以下组件：

  - 一台或多台运行 持久聊天服务器并提供以下服务的计算机：
    
      - 持久聊天服务
    
      - 合规性服务，在启用合规性时打开
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>在 Lync Server 2013 中，用于文件上载/下载的 持久聊天 Web 服务现已与 Lync Server 2013前端服务器并置。<br />
    用于聊天室管理的 持久聊天 Web 服务也已与 Lync Server 2013前端服务器并置。</td>
    </tr>
    </tbody>
    </table>


  - 为承载用于存储聊天室内容、聊天室和类别的 持久聊天内容数据库而承载 SQL Server 后端数据库的服务器（如果使用镜像，则存在多台服务器）。
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/Dn783119.note(OCS.15).gif" title="note" alt="note" />注意：</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>后端数据库可存储聊天历史记录数据，包括有关创建的类别和 持久聊天聊天室的信息。</td>
    </tr>
    </tbody>
    </table>


  - 如果启用合规性，则为用于承载 持久聊天合规性数据库（其中存储用于合规性目的的合规性事件和聊天内容）的 SQL Server 后端数据库的服务器（如果使用镜像，则有多台服务器）。

要从一台单独的计算机（例如管理控制台）管理 持久聊天服务器，请在该计算机上使用 Lync Server 控制面板。然后必须将该计算机部署在一个 Active Directory 域服务 域中，并且林根中至少要有一台全局编录服务器。

有关 持久聊天服务器的软硬件要求的详细信息，请参阅 [Lync Server 2013 中持久聊天服务器的技术要求](lync-server-2013-technical-requirements-for-persistent-chat-server.md)以及可支持性文档中的 [支持的适用于 Lync Server 2013 的硬件](lync-server-2013-supported-hardware.md)和 [Lync Server 2013 中的服务器软件和基础结构支持](lync-server-2013-server-software-and-infrastructure-support.md)。

## 支持的并置

Lync Server 2013 支持多种并置方案，为您提供了极大的灵活性：您可以在一台服务器上运行多个组件以节省硬件成本（如果组织规模较小）；也可以在不同服务器上运行单个组件（如果组织规模较大，对可伸缩性和性能具有一定的要求）。在决定是否并置组件之前，一定要考虑可伸缩性因素。

如果启用合规性，则 持久聊天合规性服务将与 Lync Server 2013前端服务器并置。

可在 Standard Edition Server 上部署 持久聊天服务器。 持久聊天服务器后端服务器和 持久聊天合规性数据库可在本地 SQL Server Express后端服务器上的 Standard Edition Server 上并置。有关可在这些位置并置的组件的详细信息，请参阅可支持性文档中的 [Lync Server 2013 中支持的服务器并置](lync-server-2013-supported-server-collocation.md)。

对于 Lync Server 2013企业版， 持久聊天服务器无法在 Enterprise Edition Server 上并置。 持久聊天服务器的 SQL Server 数据库可与 企业版前端池的 后端服务器数据库并置。用于 持久聊天合规性的 SQL Server 数据库也还与 企业版 池的 后端服务器数据库并置。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>承载 持久聊天数据库的服务器可以承载其他数据库。但是，在考虑将 持久聊天数据库与其他数据库并置时，请注意，如果存储多个用户的消息，则 持久聊天数据库所需的磁盘空间会变得很大。因此，建议不要将 持久聊天数据库与后端数据库并置。</td>
</tr>
</tbody>
</table>


如果将 持久聊天数据库与后端数据库并置，则可将单个 SQL Server 实例用于任意或全部数据库，也可以对每个数据库使用不同的 SQL Server 实例，但存在以下限制：

  - 每个 SQL Server 实例只能包含单个后端数据库和单个 持久聊天数据库。

有关所有服务器角色和数据库并置的详细信息，请参阅可支持性文档中的 [Lync Server 2013 中支持的服务器并置](lync-server-2013-supported-server-collocation.md)。

## 持久聊天服务器拓扑

持久聊天服务器 支持以下拓扑：

  - Lync Server 2013 Enterprise Edition 单服务器 持久聊天服务器前端服务器

  - Lync Server 2013 Enterprise Edition 多服务器 持久聊天服务器前端服务器

  - 使用 SQL Server Express 的 Lync Server 2013Standard Edition Server

  - 使用 Standard Edition Server 作为下一个跃点服务器的单独服务器上的 Lync Server 2013Standard Edition Server 和 持久聊天服务器

可以使用 拓扑生成器将 持久聊天服务器添加到 Lync Server 2013 部署中。可向您的拓扑中添加单服务器或多服务器 持久聊天服务器池。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>在使用 拓扑生成器创建具有单个服务器的 持久聊天服务器池后，您无法向该池添加其他服务器。</td>
</tr>
</tbody>
</table>


## 单服务器拓扑

持久聊天服务器的最低配置和最简单的部署是单 持久聊天服务器前端服务器拓扑。此部署要求具有一台运行 持久聊天服务器的服务器（如果已启用合规性，该服务器可以运行合规性服务）、一台承载 SQL Server 数据库的服务器，如果有合规性要求，该 SQL Server 数据库用于存储合规性数据。

<table>
<thead>
<tr class="header">
<th><img src="images/Gg398794.important(OCS.15).gif" title="important" alt="important" />重要提示：</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>您不能向作为 拓扑生成器中的单服务器部署启动的 持久聊天服务器池添加其他服务器。即使您使用的是单个服务器，也建议您使用多服务器池拓扑以便稍后添加更多服务器（如有必要）。</td>
</tr>
</tbody>
</table>


下图显示了具有合规性的单个 持久聊天服务器前端服务器拓扑的所有必需组件和可选组件。

**一台持久聊天服务器**

![带合规性服务的单服务器拓扑](images/Gg398500.9168fa52-61e0-4d17-a14d-45fd32e81456(OCS.15).jpg "带合规性服务的单服务器拓扑")

## 多服务器拓扑

为提供更大的容量和更强的可靠性，您可以根据 [在 Lync Server 2013 中规划持久聊天服务器](lync-server-2013-planning-for-persistent-chat-server.md)中的说明部署多服务器拓扑。多服务器拓扑最多可以包含四台运行 持久聊天服务器的活动计算机（高可用性和灾难恢复配置允许最多八台，其余四台处于待机状态），每台服务器可支持多达 20,000 个并发用户，4 台服务器总共可支持 80,000 个连接到 持久聊天服务器池的并发用户。多服务器拓扑与单服务器拓扑相同，只不过它有多台服务器承载 持久聊天服务器，并且缩放性更高。多台运行 持久聊天服务器的计算机应与 Lync Server 和合规性服务位于同一 Active Directory 域服务 域中。

下图显示了带有多台运行 持久聊天服务器的计算机、可选的合规性服务和单独的合规性数据库的多服务器拓扑的所有组件。

**多台持久聊天服务器**

![多服务器拓扑](images/Gg398500.19aea898-28df-4d9b-903c-f72ef062d919(OCS.15).jpg "多服务器拓扑")

多服务器拓扑提供了服务器池功能。在服务器池中， 持久聊天服务可以传达并共享数据。例如，可从系统中的任何 持久聊天服务获得最初已发布到某项 持久聊天服务的聊天历史记录。可使用任何 持久聊天服务访问通过某项 持久聊天服务上载的文件。用户可以连接到不同的 持久聊天服务器前端服务器，并可以相互聊天和通信。

TCP 8011 的默认端口可将服务器连接至服务器池，供 持久聊天服务用来进行相互通信，或用于管理用途。

