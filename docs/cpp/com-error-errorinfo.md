---
title: _com_error::ErrorInfo
ms.date: 11/04/2016
f1_keywords:
- _com_error::ErrorInfo
helpviewer_keywords:
- ErrorInfo method [C++]
ms.assetid: 071b446c-4395-4fb8-bd3d-300a8b25f5cd
ms.openlocfilehash: cedb9ccadc63166c43d980333d93a195254700d8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180705"
---
# <a name="_com_errorerrorinfo"></a>_com_error::ErrorInfo

**Microsoft-spezifisch**

Ruft das `IErrorInfo`-Objekt ab, das an den Konstruktor übergeben wurde.

## <a name="syntax"></a>Syntax

```
IErrorInfo * ErrorInfo( ) const throw( );
```

## <a name="return-value"></a>Rückgabewert

Unformatiertes `IErrorInfo`-Element, das an den Konstruktor übergeben wird.

## <a name="remarks"></a>Bemerkungen

Ruft das gekapselte `IErrorInfo` Element in einem `_com_error`-Objekt ab oder NULL, wenn kein `IErrorInfo` Element aufgezeichnet wird. Der Aufrufer muss `Release` für das zurückgegebene Objekt aufzurufen, wenn er seine Verwendung beendet.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
