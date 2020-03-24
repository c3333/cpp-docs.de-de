---
title: RaiseException-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 3270057bf5b1b27a98bef1ab236291eab15d27ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213628"
---
# <a name="raiseexception-function"></a>RaiseException-Funktion

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>Parameter

*HR*<br/>
Der Ausnahme Code der Ausnahme, die ausgelöst wird. Das heißt, das HRESULT eines fehlgeschlagenen Vorgangs.

*dwexceptionflags*<br/>
Ein Flag, das eine fort Setz Bare Ausnahme angibt (der Flagwert ist 0 (null)) oder eine nicht fort Setz Bare Ausnahme (Flagwert ist nicht null). Standardmäßig ist die Ausnahme nicht fort setzbar.

## <a name="remarks"></a>Bemerkungen

Löst eine Ausnahme im aufrufenden Thread aus.

Weitere Informationen finden Sie unter der Windows `RaiseException`-Funktion.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
