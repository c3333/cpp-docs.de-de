---
title: FactoryCacheFlags-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 3381b2bcfcbf298270b547199ae614291855a2f7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88843273"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags-Enumeration

Bestimmt, ob Factory-Objekte zwischengespeichert werden.

## <a name="syntax"></a>Syntax

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>Bemerkungen

Standardmäßig wird die Richtlinie zum Zwischenspeichern der Factory als [ModuleType](moduletype-enumeration.md) -Vorlagen Parameter angegeben, wenn Sie ein [Modul](module-class.md) Objekt erstellen. Um diese Richtlinie zu überschreiben, geben Sie einen **factorycacheflags** -Wert an, wenn Sie ein Factory-Objekt erstellen.

| Richtlinie | Beschreibung |
|-|-|
|`FactoryCacheDefault`|Die Cachingrichtlinie des- `Module` Objekts wird verwendet.|
|`FactoryCacheEnabled`|Aktiviert das Zwischenspeichern von Fabriken unabhängig von dem `ModuleType` Vorlagen Parameter, der zum Erstellen eines-Objekts verwendet wird `Module` .|
|`FactoryCacheDisabled`|Deaktiviert das Zwischenspeichern von Fabriken unabhängig von dem `ModuleType` Vorlagen Parameter, der zum Erstellen eines-Objekts verwendet wird `Module` .|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft:: WRL-Namespace](microsoft-wrl-namespace.md)
