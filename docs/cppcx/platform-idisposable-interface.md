---
title: Platform::IDisposable-Schnittstelle
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: 0024edbad0bb3311a0497be67fc8bcfc954602e1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214239"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable-Schnittstelle

Wird verwendet, um nicht verwaltete Ressourcen freizugeben.

## <a name="syntax"></a>Syntax

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Attributes

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**Versionattribute**(NTDDI_WIN8)

### <a name="members"></a>Members

Die IDisposable-Schnittstelle erbt von der IUnknown-Schnittstelle. IDisposable verfügt auch über die folgenden Membertypen:

**Methoden**

Die IDisposable-Schnittstelle verfügt über die folgenden Methoden.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|Dispose|Wird verwendet, um nicht verwaltete Ressourcen freizugeben.|

### <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens unterstützter Client:** Windows 8

**Mindestens unterstützter Server:** Windows Server 2012

**Namespace:** Platform
