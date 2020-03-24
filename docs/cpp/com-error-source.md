---
title: _com_error::Source
ms.date: 11/04/2016
f1_keywords:
- _com_error::Source
helpviewer_keywords:
- Source method [C++]
ms.assetid: 55353741-fabc-4b0c-9787-b5a69bb189f2
ms.openlocfilehash: 43dd21297ddd54863d535402dddd59243d589eec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180523"
---
# <a name="_com_errorsource"></a>_com_error::Source

**Microsoft-spezifisch**

Ruft die `IErrorInfo::GetSource`-Funktion auf.

## <a name="syntax"></a>Syntax

```
_bstr_t Source() const;
```

## <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis `IErrorInfo::GetSource` für das `IErrorInfo` Objekt zurück, das innerhalb des `_com_error`-Objekts aufgezeichnet wird. Das resultierende `BSTR` wird in einem `_bstr_t`-Objekt gekapselt. Wenn keine `IErrorInfo` aufgezeichnet wird, wird ein leerer `_bstr_t`zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Jeder Fehler beim Aufrufen der `IErrorInfo::GetSource`-Methode wird ignoriert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
