---
title: Ausnahme Behandlungs Makros
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 7fcd8221ba5f121749cf366a93cc8a6d8d00ed7c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833438"
---
# <a name="exception-handling-macros"></a>Ausnahme Behandlungs Makros

Diese Makros bieten Unterstützung für die Ausnahmebehandlung.

|Name|Beschreibung|
|-|-|
|[_ATLCATCH](#_atlcatch)|Anweisung (en) zum Behandeln von Fehlern, die in der zugeordneten auftreten `_ATLTRY` .|
|[_ATLCATCHALL](#_atlcatchall)|Anweisung (en) zum Behandeln von Fehlern, die in der zugeordneten auftreten `_ATLTRY` .|
|[_ATLTRY](#_atltry)|Markiert einen überwachten Code Abschnitt, bei dem möglicherweise ein Fehler auftritt.|

## <a name="requirements"></a>Anforderungen:

**Header:** atldef. h

## <a name="_atlcatch"></a><a name="_atlcatch"></a> _ATLCATCH

Anweisung (en) zum Behandeln von Fehlern, die in der zugeordneten auftreten `_ATLTRY` .

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parameter

*e*<br/>
Die abzufangende Ausnahme.

### <a name="remarks"></a>Bemerkungen

Wird in Verbindung mit der `_ATLTRY`-Eigenschaft verwendet. Löst in C++ [catch (catlexception e)](../../cpp/try-throw-and-catch-statements-cpp.md) auf, um einen bestimmten Typ von C++-Ausnahmen zu verarbeiten.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a> _ATLCATCHALL

Anweisung (en) zum Behandeln von Fehlern, die in der zugeordneten auftreten `_ATLTRY` .

```
_ATLCATCHALL
```

### <a name="remarks"></a>Bemerkungen

Wird in Verbindung mit der `_ATLTRY`-Eigenschaft verwendet. Löst in C++ [catch (...)](../../cpp/try-throw-and-catch-statements-cpp.md) auf, um alle Typen von C++-Ausnahmen zu verarbeiten.

## <a name="_atltry"></a><a name="_atltry"></a> _ATLTRY

Markiert einen überwachten Code Abschnitt, bei dem möglicherweise ein Fehler auftritt.

```
_ATLTRY
```

### <a name="remarks"></a>Bemerkungen

Wird in Verbindung mit [_ATLCATCH](#_atlcatch) oder [_ATLCATCHALL](#_atlcatchall)verwendet. Löst den C++-Symbol [Versuch](../../cpp/try-throw-and-catch-statements-cpp.md)aus.

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
