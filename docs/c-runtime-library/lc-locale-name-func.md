---
title: ___lc_locale_name_func
ms.date: 4/2/2020
api_name:
- ___lc_locale_name_func
- _o____lc_locale_name_func
api_location:
- msvcrt.dll
- msvcr110.dll
- msvcr100.dll
- msvcr90.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___lc_locale_name_func
helpviewer_keywords:
- ___lc_locale_name_func
ms.assetid: ef858308-872e-43de-95e0-9b1b4084343e
ms.openlocfilehash: c48041c6c01e22c7771c0b5449de2cc8df1a2df0
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912972"
---
# <a name="___lc_locale_name_func"></a>___lc_locale_name_func

Interne CRT-Funktion. Ruft die aktuellen Gebietsschemanamen des Threads ab.

## <a name="syntax"></a>Syntax

```cpp
wchar_t** ___lc_locale_name_func(void);
```

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den aktuellen Gebietsschemanamen des Threads enthält.

## <a name="remarks"></a>Hinweise

`___lc_locale_name_func` ist eine interne CRT-Funktion, die von anderen CRT-Funktionen verwendet wird, um den aktuellen Gebietsschemanamen aus dem lokalen Threadspeicher für CRT-Daten abzurufen. Diese Information ist auch mit Verwendung der Funktion [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) oder der Funktionen [Setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) verfügbar.

Interne CRT-Funktionen sind implementierungsspezifisch und mit jedem neuen Release Änderungen unterworfen. Ihre Verwendung in einem Code wird nicht empfohlen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|`___lc_locale_name_func`|crt\src\setlocal.h|

## <a name="see-also"></a>Weitere Informationen

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
