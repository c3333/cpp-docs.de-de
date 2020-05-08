---
title: _findclose
ms.date: 4/2/2020
api_name:
- _findclose
- _o__findclose
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _findclose
- findclose
helpviewer_keywords:
- _findclose function
- findclose function
ms.assetid: 9216c573-0878-444c-b5d7-cdaf16fb9163
ms.openlocfilehash: dffe2ff71f1eecaec78c75867ebb7e34a963ee3a
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82911809"
---
# <a name="_findclose"></a>_findclose

Schließt das angegebene Suchhandle und gibt zugeordnete Ressourcen frei.

## <a name="syntax"></a>Syntax

```C
int _findclose(
   intptr_t handle
);
```

### <a name="parameters"></a>Parameter

*bewältigen*<br/>
Das Suchhandle, das von einem vorherigen- **_findfirst**zurückgegeben wurde.

## <a name="return-value"></a>Rückgabewert

Bei erfolgreicher Ausführung gibt **_findclose** 0 zurück. Andernfalls wird-1 zurückgegeben und **errno** auf **ENOENT**festgelegt, um anzugeben, dass keine weiteren übereinstimmenden Dateien gefunden werden konnten.

## <a name="remarks"></a>Hinweise

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Systemaufrufe](../../c-runtime-library/system-calls.md)<br/>
[Dateinamen-Suchfunktionen](../../c-runtime-library/filename-search-functions.md)<br/>
