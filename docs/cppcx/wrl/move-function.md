---
title: Move-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 65fe85e95453165430c7ef3cfd4c4bb2babd9868
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213706"
---
# <a name="move-function"></a>Move-Funktion

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Arguments.

*arg*<br/>
Ein Argument, das verschoben werden soll.

## <a name="return-value"></a>Rückgabewert

Der Parameter " *arg* " nach Verweis-oder rvalue-reference-Merkmalen, sofern vorhanden, wurden entfernt.

## <a name="remarks"></a>Bemerkungen

Verschiebt das angegebene Argument von einem Speicherort zu einem anderen.

Weitere Informationen finden Sie im Abschnitt Verschiebungs **Semantik** von [rvalue reference declarator: & &](../../cpp/rvalue-reference-declarator-amp-amp.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
