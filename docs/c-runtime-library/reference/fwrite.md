---
title: fwrite
ms.date: 4/2/2020
api_name:
- fwrite
- _o_fwrite
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
- fwrite
helpviewer_keywords:
- streams, writing data to
- fwrite function
ms.assetid: 7afacf3a-72d7-4a50-ba2e-bea1ab9f4124
ms.openlocfilehash: ab1e172374cd117b07cc62923d291fbd3972882e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919449"
---
# <a name="fwrite"></a>fwrite

Schreibt Daten in einen Stream.

## <a name="syntax"></a>Syntax

```C
size_t fwrite(
   const void *buffer,
   size_t size,
   size_t count,
   FILE *stream
);
```

### <a name="parameters"></a>Parameter

*ert*<br/>
Zeiger auf die zu schreibenden Daten.

*size*<br/>
Elementgröße in Bytes.

*count*<br/>
Maximale Anzahl zu schreibender Elemente.

*Streich*<br/>
Zeiger auf die **FILE**-Struktur.

## <a name="return-value"></a>Rückgabewert

bei einem Fehler wird die Anzahl der tatsächlich geschriebenen vollständigen **Elemente zurückgegeben** . Dies ist möglicherweise kleiner als *die Anzahl,* wenn ein Fehler auftritt. Außerdem kann im Fall eines Fehlers möglicherweise der Dateipositionszeiger nicht bestimmt werden. Wenn ein Daten *Strom* oder ein *Puffer* ein NULL-Zeiger ist oder wenn im Unicode-Modus eine ungerade Anzahl von zu schreibenden Bytes angegeben wird, ruft die Funktion den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt 0 zurück.

## <a name="remarks"></a>Hinweise

Die **fwrite** -Funktion schreibt bis zum *zählen* *von Elementen* vom *Puffer* in den Ausgabestream. *stream* Der dem *Stream* zugeordnete Dateizeiger (sofern vorhanden) wird um die Anzahl der tatsächlich geschriebenen Bytes erhöht. Wenn der *Stream* im Textmodus geöffnet ist, wird jeder Zeilenvorschub durch ein Wagen Rücklauf-Zeilenvorschub Paar ersetzt. Diese Ersetzung hat keine Auswirkung auf den Rückgabewert.

Wenn der *Stream* im Unicode-Übersetzungsmodus geöffnet wird – z. b. wenn der *Stream* durch Aufrufen von **fopen** geöffnet wird und ein Modusparameter verwendet wird, der **CCS = Unicode**enthält, **CCS = UTF-16LE**oder **CCS = UTF-8**, oder, wenn der Modus in einen Unicode-Übersetzungsmodus geändert wird, indem **_setmode** und ein Modusparameter, der **_O_WTEXT**, **_O_U16TEXT**oder **_O_U8TEXT**–-*Puffer* enthält, als Zeiger auf ein Array von **wchar_t** interpretiert wird, das UTF-16-Daten enthält. Der Versuch, in diesem Modus eine ungerade Anzahl von Bytes zu schreiben, führt zu einem Parametervalidierungsfehler.

Da diese Funktion den aufrufenden Thread sperrt, ist sie threadsicher. Eine nicht sperrende Version finden Sie unter **_fwrite_nolock**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Funktion|Erforderlicher Header|
|--------------|---------------------|
|**fwrite**|\<stdio.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Ein Beispiel hierfür finden Sie unter [fread](fread.md).

## <a name="see-also"></a>Weitere Informationen

[Stream-E/A](../../c-runtime-library/stream-i-o.md)<br/>
[_setmode](setmode.md)<br/>
[fread](fread.md)<br/>
[_fwrite_nolock](fwrite-nolock.md)<br/>
[_write](write.md)<br/>
