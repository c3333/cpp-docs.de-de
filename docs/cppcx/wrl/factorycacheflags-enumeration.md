---
title: FactoryCacheFlags-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 250c8c8e7ade72bd1a9cd63f0b515774058f0723
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214005"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags-Enumeration

Bestimmt, ob Factory-Objekte zwischengespeichert werden.

## <a name="syntax"></a>Syntax

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Bemerkungen

Standardmäßig wird die Richtlinie zum Zwischenspeichern der Factory als [ModuleType](moduletype-enumeration.md) -Vorlagen Parameter angegeben, wenn Sie ein [Modul](module-class.md) Objekt erstellen. Um diese Richtlinie zu überschreiben, geben Sie einen **factorycacheflags** -Wert an, wenn Sie ein Factory-Objekt erstellen.

|||
|-|-|
|`FactoryCacheDefault`|Die Cachingrichtlinie des `Module` Objekts wird verwendet.|
|`FactoryCacheEnabled`|Aktiviert das Zwischenspeichern von Fabriken unabhängig vom `ModuleType` Vorlagen Parameter, der zum Erstellen eines `Module` Objekts verwendet wird.|
|`FactoryCacheDisabled`|Deaktiviert das Zwischenspeichern von Fabriken unabhängig vom `ModuleType` Vorlagen Parameter, der zum Erstellen eines `Module` Objekts verwendet wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
