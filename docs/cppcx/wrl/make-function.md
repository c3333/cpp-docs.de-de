---
title: Make-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: 0f2e81e3cd757214805817af2a355a93c1cfd096
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220469"
---
# <a name="make-function"></a>Make-Funktion

Initialisiert die angegebene Windows-Runtime-Klasse. Verwenden Sie diese Funktion, um eine Komponente zu instanziieren, die im selben Modul definiert ist.

## <a name="syntax"></a>Syntax

```cpp
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
```

### <a name="parameters"></a>Parameter

*T*<br/>
Eine benutzerdefinierte Klasse, die von erbt `WRL::RuntimeClass` .

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

Ein- `ComPtr<T>` Objekt, wenn erfolgreich, andernfalls **`nullptr`** .

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter Gewusst [wie: direktes Instanziieren von WRL-Komponenten](how-to-instantiate-wrl-components-directly.md) , um die Unterschiede zwischen dieser Funktion und [Microsoft:: WRL::D etails:: makeandinitialize](makeandinitialize-function.md)zu erlernen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft:: WRL-Namespace](microsoft-wrl-namespace.md)
