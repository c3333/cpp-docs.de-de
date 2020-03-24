---
title: Microsoft::WRL::Wrappers-Namespace
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers
helpviewer_keywords:
- Wrappers namespace
ms.assetid: 36ac38c7-1fc3-42da-a879-5c68661dc9e1
ms.openlocfilehash: ece26b3f9928d44a593de830cf8a25c57e4c2d89
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213745"
---
# <a name="microsoftwrlwrappers-namespace"></a>Microsoft::WRL::Wrappers-Namespace

Definiert Resource Acquisition Is Initialization (RAII)-Wrapper Typen, die die Lebensdauer Verwaltung von Objekten, Zeichen folgen und Handles vereinfachen.

## <a name="syntax"></a>Syntax

```cpp
namespace Microsoft::WRL::Wrappers;
```

## <a name="members"></a>Members

### <a name="typedefs"></a>TypeDefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|`FileHandle`|`HandleT<HandleTraits::FileHandleTraits>`|

### <a name="classes"></a>Klassen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CriticalSection-Klasse](criticalsection-class.md)|Stellt ein kritisches Abschnitts Objekt dar.|
|[Ereignisklasse (WRL)](event-class-wrl.md)|Stellt ein Ereignis dar.|
|[HandleT-Klasse](handlet-class.md)|Stellt ein Handle für ein-Objekt dar.|
|[HString-Klasse](hstring-class.md)|Bietet Unterstützung für die Bearbeitung von HSTRING-Handles.|
|[HStringReference-Klasse](hstringreference-class.md)|Stellt ein HSTRING dar, das aus einer vorhandenen Zeichenfolge erstellt wird.|
|[Mutex-Klasse](mutex-class.md)|Stellt ein Synchronisierungs Objekt dar, das exklusiv eine freigegebene Ressource steuert.|
|[RoInitializeWrapper-Klasse](roinitializewrapper-class.md)|Initialisiert die Windows-Runtime.|
|[Semaphore-Klasse](semaphore-class.md)|Stellt ein Synchronisierungs Objekt dar, das eine freigegebene Ressource steuert, die eine begrenzte Anzahl von Benutzern unterstützen kann.|
|[SRWLock-Klasse](srwlock-class.md)|Stellt eine schlanke Lese-/Schreibsperre dar.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** corewrappers. h

**Namespace:** Microsoft:: WRL:: Wrapper

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
