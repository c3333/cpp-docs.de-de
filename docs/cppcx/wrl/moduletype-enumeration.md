---
title: ModuleType-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
ms.openlocfilehash: 8425a15d594f7b8b30027d3576ee86015b656130
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213719"
---
# <a name="moduletype-enumeration"></a>ModuleType-Enumeration

Gibt an, ob ein Modul einen In-Process-Server oder einen Out-of-Process-Server unterstützen sollte.

## <a name="syntax"></a>Syntax

```cpp
enum ModuleType;
```

## <a name="members"></a>Members

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`InProc`|Ein in-Process-Server.|
|`OutOfProc`|Einen Out-of-Process-Server.|
|`DisableCaching`|Deaktivieren Sie den Cache Mechanismus für das Modul.|
|`InProcDisableCaching`|Kombination aus `InProc` und `DisableCaching`.|
|`OutOfProcDisableCaching`|Kombination aus `OutOfProc` und `DisableCaching`.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
