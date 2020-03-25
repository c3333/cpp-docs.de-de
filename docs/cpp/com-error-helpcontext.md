---
title: _com_error::HelpContext
ms.date: 11/04/2016
f1_keywords:
- _com_error::HelpContext
helpviewer_keywords:
- HelpContext method [C++]
ms.assetid: 160d6443-9b68-4cf5-a540-50da951a5b2b
ms.openlocfilehash: b3c79bb069ef504680e83359d6ec90c803f16d9d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180588"
---
# <a name="_com_errorhelpcontext"></a>_com_error::HelpContext

**Microsoft-spezifisch**

Ruft die `IErrorInfo::GetHelpContext`-Funktion auf.

## <a name="syntax"></a>Syntax

```
DWORD HelpContext( ) const throw( );
```

## <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis `IErrorInfo::GetHelpContext` für das `IErrorInfo` Objekt zurück, das innerhalb des `_com_error`-Objekts aufgezeichnet wird. Wenn kein `IErrorInfo` Objekt aufgezeichnet wird, wird ein NULL-Wert zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Jeder Fehler beim Aufrufen der `IErrorInfo::GetHelpContext`-Methode wird ignoriert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
