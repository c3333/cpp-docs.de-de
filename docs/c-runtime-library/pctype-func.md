---
title: __pctype_func
ms.date: 4/2/2020
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: a7972744d322cf16d056f70fff83f529a183020e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213644"
---
# <a name="__pctype_func"></a>__pctype_func

Ruft einen Zeiger auf ein Array an Zeichenklassifizierungsinformationen ab.

## <a name="syntax"></a>Syntax

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Array an Zeichenklassifizierungsinformationen.

## <a name="remarks"></a>Bemerkungen

Die Informationen in der Zeichen Klassifizierungs Tabelle sind nur für die interne Verwendung vorgesehen und werden von verschiedenen Funktionen verwendet, mit denen Zeichen vom Typ klassifiziert werden **`char`** . Weitere Informationen finden Sie im `Remarks`-Abschnitt von [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>Weitere Informationen

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
