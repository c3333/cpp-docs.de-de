---
title: _com_error::GUID
ms.date: 11/04/2016
f1_keywords:
- _com_error::GUID
helpviewer_keywords:
- GUID method [C++]
ms.assetid: e84c2c23-d02e-48f8-b776-9bd6937296d2
ms.openlocfilehash: d5b05cd4e26f89d42ea23b605f5e6560795a0cfa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180640"
---
# <a name="_com_errorguid"></a>_com_error::GUID

**Microsoft-spezifisch**

Ruft die `IErrorInfo::GetGUID`-Funktion auf.

## <a name="syntax"></a>Syntax

```
GUID GUID( ) const throw( );
```

## <a name="return-value"></a>Rückgabewert

Gibt das Ergebnis `IErrorInfo::GetGUID` für das `IErrorInfo` Objekt zurück, das innerhalb des `_com_error`-Objekts aufgezeichnet wird. Wenn kein `IErrorInfo` Objekt aufgezeichnet wird, wird `GUID_NULL`zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Jeder Fehler beim Aufrufen der `IErrorInfo::GetGUID`-Methode wird ignoriert.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
