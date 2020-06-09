---
title: SafeIntException-Klasse
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeIntException Class
- SafeIntException
- SafeIntException.SafeIntException
- SafeIntException::SafeIntException
helpviewer_keywords:
- SafeIntException class
- SafeIntException, constructor
ms.assetid: 88bef958-1f48-4d55-ad4f-d1f9581a293a
ms.openlocfilehash: 8149a5e1216e26fafc1e0cd4a489cdad0551607c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615408"
---
# <a name="safeintexception-class"></a>SafeIntException-Klasse

Die `SafeInt`-Klasse verwendet `SafeIntException`, um festzustellen, warum ein mathematischer Vorgang nicht abgeschlossen werden kann.

> [!NOTE]
> Die neueste Version dieser Bibliothek finden Sie unter [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) .

## <a name="syntax"></a>Syntax

```cpp
class SafeIntException;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

name                                                    | Beschreibung
------------------------------------------------------- | ------------------------------------
[Safumtexception:: safumtexception](#safeintexception) | Erstellt ein `SafeIntException` -Objekt.

## <a name="remarks"></a>Hinweise

Die [SafeInt-Klasse](safeint-class.md) ist die einzige Klasse, die die `SafeIntException`-Klasse verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SafeIntException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „safeint.h“

**Namespace:** msl::utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>Safumtexception:: safumtexception

Erstellt ein `SafeIntException` -Objekt.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parameter

*code*<br/>
[in] Ein Aufzählungsdatenwert, der den aufgetretenen Fehler beschreibt.

### <a name="remarks"></a>Hinweise

Die möglichen Werte für *code* werden in der Datei „Safeint.h“ definiert. Der Einfachheit halber sind die möglichen Werte auch hier aufgeführt.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
