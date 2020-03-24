---
title: _com_error::_com_error
ms.date: 11/04/2016
f1_keywords:
- _com_error::_com_error
helpviewer_keywords:
- _com_error method [C++]
ms.assetid: 0a69e46c-caab-49ef-b091-eee401253ce6
ms.openlocfilehash: 4ac902f0fda90f77526ef53139ef0d523d8c22e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180783"
---
# <a name="_com_error_com_error"></a>_com_error::_com_error

**Microsoft-spezifisch**

Erstellt ein **_com_error** -Objekt.

## <a name="syntax"></a>Syntax

```
_com_error(
   HRESULT hr,
   IErrorInfo* perrinfo = NULL,
   bool fAddRef=false) throw( );

_com_error( const _com_error& that ) throw( );
```

#### <a name="parameters"></a>Parameter

*HR*<br/>
HRESULT-Informationen.

*perrinfo*<br/>
`IErrorInfo`-Objekt

*abadressf*<br/>
Der Standard bewirkt, dass der Konstruktor die adressf für eine `IErrorInfo`-Schnittstelle ungleich NULL aufruft. Dies ermöglicht die korrekte Verweis Zählung in dem allgemeinen Fall, in dem der Besitz der Schnittstelle an das **_com_error** Objekt übermittelt wird, z. b.:

```cpp
throw _com_error(hr, perrinfo);
```

Wenn Sie nicht möchten, dass Ihr Code den Besitz an das **_com_error** Objekt überträgt, und der `AddRef` erforderlich ist, um die `Release` im **_com_error** Dekonstruktor zu versetzen, erstellen Sie das Objekt wie folgt:

```cpp
_com_error err(hr, perrinfo, true);
```

*,*<br/>
Ein vorhandenes **_com_error** -Objekt.

## <a name="remarks"></a>Bemerkungen

Der erste Konstruktor erstellt ein neues-Objekt, wenn ein HRESULT und ein optionales `IErrorInfo` Objekt angegeben werden. Die zweite erstellt eine Kopie eines vorhandenen **_com_error** Objekts.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
