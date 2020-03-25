---
title: _com_error::HelpFile
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpFile
helpviewer_keywords:
- HelpFile method [C++]
ms.assetid: d2d3a0a1-6b62-4d52-a818-3cfae545a4af
ms.openlocfilehash: 775adfa7d5dd5aca098edcd793c2164d65fe7efa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190221"
---
# <a name="_com_errorhelpfile"></a>_com_error::HelpFile

**Microsoft-spezifisch**

Ruft die `IErrorInfo::GetHelpFile`-Funktion auf.

## <a name="syntax"></a>Syntax

```
_bstr_t HelpFile() const;
```

## <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis `IErrorInfo::GetHelpFile` für das `IErrorInfo` Objekt zurück, das innerhalb des `_com_error`-Objekts aufgezeichnet wird. Das resultierende BSTR wird in einem `_bstr_t`-Objekt gekapselt. Wenn keine `IErrorInfo` aufgezeichnet wird, wird ein leerer `_bstr_t`zurückgegeben.

## <a name="remarks"></a>Hinweise

Jeder Fehler beim Aufrufen der `IErrorInfo::GetHelpFile`-Methode wird ignoriert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[_com_error-Klasse](../cpp/com-error-class.md)
