﻿---
title: 'Lync Server 2013: Plan for Shared Line Appearance'
TOCTitle: Plan for Shared Line Appearance
ms:assetid: a35c83d8-f531-445b-a8d2-d5d8cec77c6b
ms:mtpsurl: https://technet.microsoft.com/zh-cn/library/Mt712151(v=OCS.15)
ms:contentKeyID: 72522148
ms.date: 05/19/2016
mtps_version: v=OCS.15
ms.translationtype: HT
---

# Plan for Shared Line Appearance in Lync Server 2013

 

_**上一次修改主题：** 2016-03-21_

Read this topic to learn how to plan for Shared Line Appearance (SLA) in Lync Server 2013, Cumulative Update April 2016.

Shared Line Appearance is a feature in Lync Server 2013, Cumulative Update April 2016 for handling multiple calls on a specific number called a shared number. SLA can configure any enterprise voice enabled Lync user as a shared number with multiple lines to respond to multiple calls. The calls are not actually received on the shared number, instead they are forwarded to users that act as delegates for the shared number. Any one of the delegates can pick up the call while the rest of the delegates get a notification on their phone about who picked up the call and which line has become busy as a result. Both the number of lines and the delegates are configurable for a shared number in SLA. In addition, advanced options, such as BusyOption (what happens in a situation when all lines are busy) and MissedCallOption (the case in which none of the delegates pick up a call), can also be configured for a shared number.

SLA is supported only on the following phone devices (it is not supported for Lync clients on computers, mobile phones, or other devices):

  - Polycom VVX300 with firmware update 5.4.1

  - Polycom VVX400 with firmware update 5.4.1

  - Polycom VVX500 with firmware update 5.4.1

  - Polycom VVX600 with firmware update 5.4.1

SLA is a new feature in Lync Server 2013, Cumulative Update April 2016.

For information about deploying SLA, see [Deploy Shared Line Appearance in Lync Server 2013](lync-server-2013-deploy-shared-line-appearance.md).

## Feature List

Setting up an SLA group enables the following:

  - All delegates in the group can answer inbound calls to the same shared number. The calls can be PSTN-based or SIP-based.

  - Delegates can hold and pick up calls.

  - Delegates can transfer calls to a number outside of the SLA group.

  - Delegates can see how many calls are currently on the shared number, and view the status of each of those calls.

  - You can configure a maximum number of concurrent calls for the shared number. You can also set how you want additional calls to be handled after this maximum is reached. Excess calls can be rejected with a busy signal, forwarded to an alternate number, or forwarded to voice mail.

  - You can configure how you want missed calls (calls not picked up after a certain time) to be handled. If you enable voice mail for the group identity, missed calls automatically go to voice mail. If you do not have voice mail enabled for the group identity (shared number), you can choose for missed calls to be rejected with a busy signal, forwarded to an alternate number, or disconnected.

