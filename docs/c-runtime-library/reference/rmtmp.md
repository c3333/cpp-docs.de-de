---
title: _rmtmp
ms.date: 4/2/2020
api_name:
- _rmtmp
- _o__rmtmp
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _rmtmp
helpviewer_keywords:
- removing temporary files
- _rmtmp function
- files [C++], temporary
- rmtmp function
- files [C++], removing
- temporary files [C++], removing
ms.assetid: 7419501e-2587-4f2a-b469-0dca07f84736
ms.openlocfilehash: ca5c693a1baed7e5f31219cdbee712b5c77f2a85
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917638"
---
# <a name="_rmtmp"></a>_rmtmp

Löscht temporäre Dateien.

## <a name="syntax"></a>Syntax

```C

int _rmtmp( void );
```

## <a name="return-value"></a>Rückgabewert

**_rmtmp** gibt die Anzahl der geschlossenen und gelöschten temporären Dateien zurück.

## <a name="remarks"></a>Hinweise

Die **_rmtmp** -Funktion bereinigt alle temporären Dateien im aktuellen Verzeichnis. Mit der-Funktion werden nur die von **tmpfile**erstellten Dateien entfernt. Verwenden Sie Sie nur in demselben Verzeichnis, in dem die temporären Dateien erstellt wurden.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_rmtmp**|\<stdio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [tmpfile](tmpfile.md).

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_flushall](flushall.md)<br/>
[tmpfile](tmpfile.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
