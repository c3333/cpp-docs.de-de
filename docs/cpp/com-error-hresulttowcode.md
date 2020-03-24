---
title: _com_error::HRESULTToWCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::HRESULTToWCode
helpviewer_keywords:
- HRESULTToWCode method [C++]
ms.assetid: ff3789f5-1047-41a0-b7e3-86dd8f638dba
ms.openlocfilehash: 35a497c273f15c9755d3607e7907a3a48dad8dc8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180562"
---
# <a name="_com_errorhresulttowcode"></a>_com_error::HRESULTToWCode

**Microsoft-spezifisch**

Ordnet 32-Bit-HRESULT einem 16-Bit-`wCode`zu.

## <a name="syntax"></a>Syntax

```
static WORD HRESULTToWCode(
   HRESULT hr
) throw( );
```

#### <a name="parameters"></a>Parameter

*HR*<br/>
Das 32-Bit-HRESULT, das einem 16-Bit-`wCode`zugeordnet werden soll.

## <a name="return-value"></a>Rückgabewert

aus dem 32-Bit-HRESULT zugeordnete 16-Bit-`wCode`.

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [_com_error:: wCode](../cpp/com-error-wcode.md) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error::WCode](../cpp/com-error-wcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error-Klasse](../cpp/com-error-class.md)
