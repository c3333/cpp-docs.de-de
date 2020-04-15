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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: ed17963dc7331962c3ac0d522db2843822ec5f79
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81346785"
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

*Behandeln*<br/>
Suchhandle, das von einem vorherigen Aufruf an **_findfirst**zurückgegeben wurde.

## <a name="return-value"></a>Rückgabewert

Wenn dies erfolgreich ist, **gibt _findclose** 0 zurück. Andernfalls gibt es -1 zurück und setzt **errno** auf **ENOENT**, was darauf hinweist, dass keine übereinstimmenden Dateien mehr gefunden wurden.

## <a name="remarks"></a>Bemerkungen

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**_findclose**|\<io.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Systemaufrufe](../../c-runtime-library/system-calls.md)<br/>
[Dateinamen-Suchfunktionen](../../c-runtime-library/filename-search-functions.md)<br/>
