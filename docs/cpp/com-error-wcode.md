---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190195"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Microsoft-spezifisch**

Ruft den 16-Bit-Fehlercode ab, der dem gekapselten HRESULT zugeordnet ist.

## <a name="syntax"></a>Syntax

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>Rückgabewert

Liegt das HRESULT im Bereich von 0x80040200 bis 0x8004FFFF, gibt die `WCode`-Methode das HRESULT minus 0x80040200; zurück. Andernfalls wird 0 (null) zurückgegeben.

## <a name="remarks"></a>Bemerkungen

Die `WCode`-Methode wird verwendet, um eine Zuordnung rückgängig zu machen, die im com-Unterstützungs Code erfolgt. Der Wrapper für eine `dispinterface`-Eigenschaft oder-Methode ruft eine Unterstützungs Routine auf, die die Argumente verpackt und `IDispatch::Invoke`aufruft. Wenn bei der Rückgabe ein Fehler HRESULT von `DISP_E_EXCEPTION` zurückgegeben wird, werden die Fehlerinformationen aus der `EXCEPINFO` Struktur abgerufen, die an `IDispatch::Invoke`übermittelt wurde. Der Fehlercode kann entweder ein 16-Bit-Wert sein, der im `wCode`-Member der `EXCEPINFO` Struktur gespeichert ist, oder ein vollständiger 32-Bit-Wert im `scode`-Member der `EXCEPINFO` Struktur. Wenn eine 16-Bit-`wCode` zurückgegeben wird, muss Sie zunächst einem 32-Bit-Fehler HRESULT zugeordnet werden.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error-Klasse](../cpp/com-error-class.md)
