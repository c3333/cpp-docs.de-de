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
ms.openlocfilehash: e118d7e3cce47ebb93cef16319a8fc45aab1118b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349946"
---
# <a name="safeintexception-class"></a>SafeIntException-Klasse

Die `SafeInt`-Klasse verwendet `SafeIntException`, um festzustellen, warum ein mathematischer Vorgang nicht abgeschlossen werden kann.

> [!NOTE]
> Die neueste Version dieser Bibliothek [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)befindet sich unter .

## <a name="syntax"></a>Syntax

```cpp
class SafeIntException;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                    | BESCHREIBUNG
------------------------------------------------------- | ------------------------------------
[SafeIntException::SafeIntException](#safeintexception) | Erstellt ein `SafeIntException` -Objekt.

## <a name="remarks"></a>Bemerkungen

Die [SafeInt-Klasse](../safeint/safeint-class.md) ist die einzige Klasse, die die `SafeIntException`-Klasse verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SafeIntException`

## <a name="requirements"></a>Anforderungen

**Header:** „safeint.h“

**Namespace:** msl::utilities

## <a name="safeintexceptionsafeintexception"></a><a name="safeintexception"></a>SafeIntException::SafeIntException

Erstellt ein `SafeIntException` -Objekt.

```cpp
SafeIntException();

SafeIntException(
   SafeIntError code
);
```

### <a name="parameters"></a>Parameter

*Code*<br/>
[in] Ein Aufzählungsdatenwert, der den aufgetretenen Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Die möglichen Werte für *code* werden in der Datei „Safeint.h“ definiert. Der Einfachheit halber sind die möglichen Werte auch hier aufgeführt.

- `SafeIntNoError`
- `SafeIntArithmeticOverflow`
- `SafeIntDivideByZero`
