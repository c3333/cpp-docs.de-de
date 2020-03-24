---
title: _com_error::ErrorMessage
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorMessage
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
ms.openlocfilehash: b5e884956b5a51d3c714f1a81dc6945409f74f4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180666"
---
# <a name="_com_errorerrormessage"></a>_com_error::ErrorMessage

**Microsoft-spezifisch**

Ruft die Zeichenfolgenmeldung für das im `_com_error`-Objekt gespeicherte HRESULT ab.

## <a name="syntax"></a>Syntax

```
const TCHAR * ErrorMessage( ) const throw( );
```

## <a name="return-value"></a>Rückgabewert

Gibt die Zeichen folgen Meldung für das HRESULT zurück, das innerhalb des `_com_error` Objekts aufgezeichnet wurde. Wenn HRESULT ein zugeordneter 16-Bit- [wCode](../cpp/com-error-wcode.md)ist, wird eine generische Meldung "`IDispatch error #<wCode>`" zurückgegeben. Wenn keine Nachricht gefunden wird, wird eine generische Meldung "`Unknown error #<hresult>`" zurückgegeben. Die zurückgegebene Zeichenfolge ist entweder eine Unicode- oder eine Multibyte-Zeichenfolge, abhängig vom Zustand des _UNICODE-Makros.

## <a name="remarks"></a>Bemerkungen

Ruft den passenden Systemmeldungs Text für HRESULT ab, der innerhalb des `_com_error` Objekts aufgezeichnet wird. Der Text der Systemmeldung wird durch Aufrufen der Win32 [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) -Funktion abgerufen. Die zurückgegebene Zeichenfolge wird von der `FormatMessage`-API zugeordnet und wird ausgegeben, wenn das `_com_error`-Objekt zerstört wird.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
