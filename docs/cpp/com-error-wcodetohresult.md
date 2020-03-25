---
title: _com_error::WCodeToHRESULT
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCodeToHRESULT
helpviewer_keywords:
- WCodeToHRESULT method [C++]
ms.assetid: 0ec43a4b-ca91-42d5-b270-3fde9c8412ea
ms.openlocfilehash: f2194e0e54a93d3227b84d893f9d3f208d972d09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180510"
---
# <a name="_com_errorwcodetohresult"></a>_com_error::WCodeToHRESULT

**Microsoft-spezifisch**

Ordnet einen 16-Bit- *wCode* dem 32-Bit-HRESULT zu.

## <a name="syntax"></a>Syntax

```
static HRESULT WCodeToHRESULT(
   WORD wCode
) throw( );
```

#### <a name="parameters"></a>Parameter

*wCode*<br/>
Der 16-Bit- *wCode* , der 32-Bit-HRESULT zugeordnet werden soll.

## <a name="return-value"></a>Rückgabewert

32-Bit-HRESULT, das aus dem 16-Bit- *wCode*zugeordnet ist.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [wCode](../cpp/com-error-wcode.md) -Member-Funktion.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error-Klasse](../cpp/com-error-class.md)
