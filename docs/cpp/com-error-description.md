---
title: _com_error::Description
ms.date: 11/04/2016
f1_keywords:
- _com_error::Description
helpviewer_keywords:
- Description method [C++]
ms.assetid: 88191e24-4ee8-44a6-8c4c-3758e22e0548
ms.openlocfilehash: de2275f096fe2fde96e64cbc3034602a1fde5e88
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180770"
---
# <a name="_com_errordescription"></a>_com_error::Description

**Microsoft-spezifisch**

Ruft die `IErrorInfo::GetDescription`-Funktion auf.

## <a name="syntax"></a>Syntax

```
_bstr_t Description( ) const;
```

## <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis `IErrorInfo::GetDescription` für das `IErrorInfo` Objekt zurück, das innerhalb des `_com_error`-Objekts aufgezeichnet wird. Das resultierende `BSTR` wird in einem `_bstr_t`-Objekt gekapselt. Wenn keine `IErrorInfo` aufgezeichnet wird, wird ein leerer `_bstr_t`zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Ruft die `IErrorInfo::GetDescription`-Funktion auf und ruft `IErrorInfo` im `_com_error`-Objekt aufgezeichnete ab. Jeder Fehler beim Aufrufen der `IErrorInfo::GetDescription`-Methode wird ignoriert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
