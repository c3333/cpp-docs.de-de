---
title: fsetpos
ms.date: 4/2/2020
api_name:
- fsetpos
- _o_fsetpos
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
- fsetpos
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
ms.openlocfilehash: 8fa6ec1f37703ce51e0c9c565d766c56cf164322
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82910182"
---
# <a name="fsetpos"></a>fsetpos

Legt den Indikator für die Position im Stream fest

## <a name="syntax"></a>Syntax

```C
int fsetpos(
   FILE *stream,
   const fpos_t *pos
);
```

### <a name="parameters"></a>Parameter

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

*POS*<br/>
Speicher des Positionsindikators

## <a name="return-value"></a>Rückgabewert

Bei erfolgreichem Erfolg gibt " **f** " den Wert 0 zurück. Bei einem Fehler gibt die Funktion einen Wert ungleich 0 (null) zurück und legt **errno** auf eine der folgenden (in errno definierten) Manifest-Konstanten fest. H): **EBADF**, d. h., es ist kein Zugriff auf die Datei möglich, oder das *Objekt, auf das verweist,* ist keine gültige Dateistruktur. oder **EINVAL**, d. h., es wurde ein ungültiger Wert für *Stream* oder *POS* übermittelt. Wenn ein ungültiger Parameter übergeben wird, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben wird.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **fsetpos** -Funktion legt den Datei Positionsindikator für den *Stream* auf den Wert von *POS*fest, der in einem vorherigen **fgetpos** -aufrufungstyp für *Stream*abgerufen wird. Die-Funktion löscht den Dateiende-Indikator und macht alle Auswirkungen von [ungetc](ungetc-ungetwc.md) auf *Stream*unerledigt. Nach dem Aufruf von **fsetpos**kann der nächste Vorgang für den *Stream* entweder Input oder Output sein.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fsetpos**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Siehe das Beispiel für [fgetpos](fgetpos.md)

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[fgetpos](fgetpos.md)<br/>
