---
title: Ausnahmebehandlung von Makros
ms.date: 11/04/2016
f1_keywords:
- atldef/ATL::_ATLCATCH
- atldef/ATL::_ATLCATCHALL
- atldef/ATL::_ATLTRY
helpviewer_keywords:
- exception handling, macros
- C++ exception handling, macros
ms.assetid: a8385d34-3fb0-4006-a42a-de045cacf0f4
ms.openlocfilehash: 2beffbbed0efee799005190bd7fd071a2087e4d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330086"
---
# <a name="exception-handling-macros"></a>Ausnahmebehandlung von Makros

Diese Makros unterstützen die Ausnahmebehandlung.

|||
|-|-|
|[_ATLCATCH](#_atlcatch)|Anweisung(en) zur Behandlung von Fehlern, die in der zugeordneten `_ATLTRY`auftreten.|
|[_ATLCATCHALL](#_atlcatchall)|Anweisung(en) zur Behandlung von Fehlern, die in der zugeordneten `_ATLTRY`auftreten.|
|[_ATLTRY](#_atltry)|Markiert einen geschützten Codeabschnitt, in dem möglicherweise ein Fehler auftritt.|

## <a name="requirements"></a>Anforderungen:

**Kopfzeile:** atldef.h

## <a name="_atlcatch"></a><a name="_atlcatch"></a>_ATLCATCH

Anweisung(en) zur Behandlung von Fehlern, die in der zugeordneten `_ATLTRY`auftreten.

```
_ATLCATCH(e)
```

### <a name="parameters"></a>Parameter

*E*<br/>
Die zu fangende Ausnahme.

### <a name="remarks"></a>Bemerkungen

Wird in Verbindung mit der `_ATLTRY`-Eigenschaft verwendet. Löst [C++-catch(CAtlException e)](../../cpp/try-throw-and-catch-statements-cpp.md) für die Behandlung eines bestimmten Typs von C++-Ausnahmen auf.

## <a name="_atlcatchall"></a><a name="_atlcatchall"></a>_ATLCATCHALL

Anweisung(en) zur Behandlung von Fehlern, die in der zugeordneten `_ATLTRY`auftreten.

```
_ATLCATCHALL
```

### <a name="remarks"></a>Bemerkungen

Wird in Verbindung mit der `_ATLTRY`-Eigenschaft verwendet. Löst [C++catch(...)](../../cpp/try-throw-and-catch-statements-cpp.md) für die Behandlung aller Arten von C++-Ausnahmen.

## <a name="_atltry"></a><a name="_atltry"></a>_ATLTRY

Markiert einen geschützten Codeabschnitt, in dem möglicherweise ein Fehler auftritt.

```
_ATLTRY
```

### <a name="remarks"></a>Bemerkungen

Wird in Verbindung mit [_ATLCATCH](#_atlcatch) oder [_ATLCATCHALL](#_atlcatchall)verwendet. Auflöst auf das C++-Symbol [try](../../cpp/try-throw-and-catch-statements-cpp.md).

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
