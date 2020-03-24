---
title: MakeAndInitialize-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: 28d9e586a766a131e7ab6280859845810c1d9814
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213797"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize-Funktion

Initialisiert die angegebene Windows-Runtime-Klasse. Verwenden Sie diese Funktion, um eine Komponente zu instanziieren, die im selben Modul definiert ist.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine benutzerdefinierte Klasse, die von `WRL::RuntimeClass`erbt.

*TArg1*<br/>
Der Typ des Arguments 1, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg2*<br/>
Der Typ des Arguments 2, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg3*<br/>
Der Typ des Arguments 3, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg4*<br/>
Der Typ des Arguments 4, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg5*<br/>
Der Typ des Arguments 5, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg6*<br/>
Der Typ des Arguments 6, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg7*<br/>
Der Typ des Arguments 7, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg8*<br/>
Der Typ des Arguments 8, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*TArg9*<br/>
Der Typ des Arguments 9, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg1*<br/>
Argument 1, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg2*<br/>
Argument 2, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg3*<br/>
Argument 3, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg4*<br/>
Argument 4, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg5*<br/>
Argument 5, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg6*<br/>
Argument 6, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg7*<br/>
Argument 7, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg8*<br/>
Argument 8, das an die angegebene Lauf Zeit Klasse übermittelt wird.

*arg9*<br/>
Argument 9, das an die angegebene Lauf Zeit Klasse übermittelt wird.

## <a name="return-value"></a>Rückgabewert

Der HRESULT-Wert.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter Gewusst [wie: direktes Instanziieren von WRL-Komponenten](how-to-instantiate-wrl-components-directly.md) , um die Unterschiede zwischen dieser Funktion und [Microsoft:: WRL:: Make](make-function.md)zu erlernen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL::Details-Namespace](microsoft-wrl-details-namespace.md)
