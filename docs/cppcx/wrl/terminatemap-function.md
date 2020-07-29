---
title: TerminateMap-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::TerminateMap
helpviewer_keywords:
- TerminateMap function
ms.assetid: 1c314a61-da5d-49bb-ac44-c34ee3c23b66
ms.openlocfilehash: 2aa4d6733d2a4e458ff8abff192778d52a4522b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233495"
---
# <a name="terminatemap-function"></a>TerminateMap-Funktion

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
inline bool TerminateMap(
   _In_ ModuleBase *module,
   _In_opt_z_ const wchar_t *serverName,
    bool forceTerminate) throw()
```

### <a name="parameters"></a>Parameter

*Mond*<br/>
Ein [Modul](module-class.md).

*Servername*<br/>
Der Name einer Teilmenge der Klassenfactorys in dem Modul, das durch das Parameter *Modul*angegeben wird.

*forcebeendigung*<br/>
**`true`** um die Klassenfactorys unabhängig davon zu beenden, welche aktiv sind; **`false`** das Beenden der Klassenfactorys, wenn eine Factory aktiv ist.

## <a name="return-value"></a>Rückgabewert

**`true`**, wenn alle Klassenfactorys beendet wurden. andernfalls **`false`** .

## <a name="remarks"></a>Bemerkungen

Fährt die Klassenfactorys im angegebenen Modul herunter.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Siehe auch

[Microsoft:: WRL::D etails-Namespace](microsoft-wrl-details-namespace.md)
