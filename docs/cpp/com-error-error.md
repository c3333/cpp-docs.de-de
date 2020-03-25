---
title: _com_error::Error
ms.date: 11/04/2016
f1_keywords:
- _com_error::Error
- Error
helpviewer_keywords:
- Error method [C++]
ms.assetid: b53a15fd-198e-4276-afcd-13439c4807f7
ms.openlocfilehash: 8e2c52d10b15822703329dcea18944773f5784ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180757"
---
# <a name="_com_errorerror"></a>_com_error::Error

**Microsoft-spezifisch**

Ruft das HRESULT ab, das an den Konstruktor übergeben wird.

## <a name="syntax"></a>Syntax

```
HRESULT Error( ) const throw( );
```

## <a name="return-value"></a>Rückgabewert

Das unformatierte HRESULT-Element wurde an den Konstruktor übergeben.

## <a name="remarks"></a>Bemerkungen

Ruft das gekapselte HRESULT-Element in einem `_com_error`-Objekt ab.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[_com_error-Klasse](../cpp/com-error-class.md)
