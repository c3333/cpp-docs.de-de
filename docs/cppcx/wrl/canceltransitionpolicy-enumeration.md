---
title: CancelTransitionPolicy-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::CancelTransitionPolicy::TransitionFromCanceled
- module/Microsoft::WRL::CancelTransitionPolicy::RemainCanceled
- module/Microsoft::WRL::CancelTransitionPolicy
helpviewer_keywords:
- CancelTransitionPolicy Enumeration
ms.assetid: 5de49f7d-e5e3-43e9-bbca-666caf226cef
ms.openlocfilehash: e820b3fffb4a00e95a1210a5c0beb3229c6d1657
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214122"
---
# <a name="canceltransitionpolicy-enumeration"></a>CancelTransitionPolicy-Enumeration

Gibt an, wie sich der Versuch eines asynchronen Vorgangs in den Status "abgeschlossen" oder "Fehler" in Bezug auf einen vom Client angeforderten Zustand "abgebrochen" Verhalten soll.

## <a name="syntax"></a>Syntax

```cpp
enum CancelTransitionPolicy;
```

## <a name="members"></a>Members

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`RemainCanceled`|Wenn sich der asynchrone Vorgang derzeit in einem vom Client angeforderten Zustand "abgebrochen" befindet, weist dies darauf hin, dass er im Zustand "abgebrochen" bleibt und nicht in den Zustand "abgeschlossen" oder "Fehler" versetzt wird.|
|`TransitionFromCanceled`|Wenn sich der asynchrone Vorgang derzeit in einem vom Client angeforderten Zustand "abgebrochen" befindet, weist dies darauf hin, dass der Status von "abgebrochen" in den Endstatus "abgeschlossen" oder "Fehler" versetzt wird, der durch den-Befehl, der dieses Flag verwendet|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
