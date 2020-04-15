---
title: _get_doserrno
ms.date: 4/2/2020
api_name:
- _get_doserrno
- _o__get_doserrno
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_doserrno
- get_doserrno
helpviewer_keywords:
- get_doserrno function
- _get_doserrno function
ms.assetid: 7fec7be3-6e39-4181-846b-8ef24489361c
ms.openlocfilehash: 2d5d4e224b39e9fa597e12975d27fa5720fbfbc7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81345260"
---
# <a name="_get_doserrno"></a>_get_doserrno

Ruft den vom Betriebssystem zurückgegebenen Fehlerwert ab, bevor er in einen **Errnowert** übersetzt wird.

## <a name="syntax"></a>Syntax

```C
errno_t _get_doserrno(
   int * pValue
);
```

### <a name="parameters"></a>Parameter

*pValue*<br/>
Ein Zeiger auf eine ganze Zahl, die mit dem aktuellen Wert des **_doserrno** globalen Makros gefüllt werden soll.

## <a name="return-value"></a>Rückgabewert

Wenn **_get_doserrno** erfolgreich ist, gibt er Null zurück. Wenn es fehlschlägt, wird ein Fehlercode zurückgegeben. Wenn *pValue* **NULL**ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

## <a name="remarks"></a>Bemerkungen

Das **_doserrno** globale Makro wird während der CRT-Initialisierung auf Null gesetzt, bevor die Prozessausführung beginnt. Es wird auf einen Betriebssystemfehlerwert gesetzt, der von jeder Funktion auf Systemebene zurückgegeben wird, die einen Betriebssystemfehler zurückgibt, und wird während der Ausführung niemals auf Null gesetzt. Wenn Sie Code schreiben, um den von einer Funktion zurückgegebenen Fehlerwert zu überprüfen, löschen Sie **immer _doserrno,** indem Sie [_set_doserrno](set-doserrno.md) vor dem Funktionsaufruf verwenden. Da ein anderer Funktionsaufruf **_doserrno**überschreiben kann, überprüfen Sie den Wert, indem **Sie _get_doserrno** unmittelbar nach dem Funktionsaufruf verwenden.

Für tragbare Fehlercodes wird [_get_errno](get-errno.md) anstelle von **_get_doserrno** empfohlen.

Mögliche Werte **_doserrno** von _doserrno \<werden in errno.h> definiert.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_get_doserrno**|\<stdlib.h>, \<cstdlib> (C++)|\<errno.h >, \<cerrno > (C++)|

**_get_doserrno** ist eine Microsoft-Erweiterung. Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[_set_doserrno](set-doserrno.md)<br/>
[errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
