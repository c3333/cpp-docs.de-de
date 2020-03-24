---
title: Platform::CallbackContext-Enumeration
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 1daa3988fcb985dab9d3083233a3703a20cc2fdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214264"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext-Enumeration

Gibt den Threadkontext an, in dem eine Rückruffunktion (Ereignishandler) ausgeführt wird.

## <a name="syntax"></a>Syntax

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Members

|Typcode|BESCHREIBUNG|
|---------------|-----------------|
|Any|Die Rückruffunktion kann in jedem beliebigen Threadkontext ausgeführt werden.|
|identisch|Die Rückruffunktion kann nur in dem Threadkontext ausgeführt werden, der den asynchronen Vorgang gestartet hat.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens unterstützter Client:** Windows 8

**Mindestens unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Metadaten:** platform.winmd
