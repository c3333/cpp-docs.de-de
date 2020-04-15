---
title: mbsrtowcs
ms.date: 4/2/2020
api_name:
- mbsrtowcs
- _o_mbsrtowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: 509046e1c55d89cd78b09076838983691423a1ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338884"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

Konvertiert eine Zeichenfolge mit Multibytezeichen im aktuellen Gebietsschema in die entsprechende Zeichenfolge mit Breitzeichen, mit der Möglichkeit des Neustarts in der Mitte eines Multibytezeichens. Es ist eine sicherere Version dieser Funktion verfügbar. Informationen dazu finden Sie unter [mbsrtowcs_s](mbsrtowcs-s.md).

## <a name="syntax"></a>Syntax

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>Parameter

*Wcstr*<br/>
Adresse zum Speichern der resultierenden konvertierten Zeichenfolge mit Breitzeichen.

*mbstr*<br/>
Indirekter Zeiger auf den Speicherort der zu konvertierenden Zeichenfolge mit Multibytezeichen.

*count*<br/>
Die maximale Anzahl von Zeichen (keine Bytes), die in *wcstr*konvertiert und gespeichert werden sollen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungsstatusobjekt. Wenn dieser Wert ein NULL-Zeiger ist, wird ein statisches internes Konvertierungszustandsobjekt verwendet. Da das interne **mbstate_t** Objekt nicht threadsicher ist, wird empfohlen, immer einen eigenen *mbstate-Parameter* zu übergeben.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Zeichen zurück, die erfolgreich konvertiert wurden, nicht einschließlich des abschließenden Zeichens NULL, sofern vorhanden. Gibt (size_t)(-1) zurück, wenn ein Fehler aufgetreten ist, und setzt **errno** auf EILSEQ.

## <a name="remarks"></a>Bemerkungen

Die **mbsrtowcs-Funktion** konvertiert eine Zeichenfolge mit Multibyte-Zeichen, auf die indirekt von *mbstr*verwiesen wird, in breite Zeichen, auf die im Puffer verwiesen wird, auf die von *wcstr*verwiesen wird, indem der Konvertierungsstatus in *mbstate*verwendet wird. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis entweder ein beendendes Null-Multibyte-Zeichen gefunden wird, eine Multibyte-Sequenz, die nicht einem gültigen Zeichen im aktuellen Gebietsschema entspricht, gefunden wird oder bis *Zählzeichen* konvertiert wurden. Wenn **mbsrtowcs** auf das Multibyte-Nullzeichen (''''''' vor oder wenn *die Anzahl* stattfindet) trifft, konvertiert es es in ein 16-Bit-Beenden-NULL-Zeichen und stoppt es.

Daher ist die breite Zeichenfolge bei *wcstr* nur dann null-beendet, wenn **mbsrtowcs** während der Konvertierung auf ein Multibyte-Nullzeichen trifft. Wenn sich die Sequenzen, auf die *mbstr* und *wcstr* zeigten, überlappen, ist das Verhalten von **mbsrtowcs** nicht definiert. **mbsrtowcs** ist von der Kategorie LC_TYPE des aktuellen Gebietsschemas betroffen.

Die **mbsrtowcs-Funktion** unterscheidet sich von [mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) durch ihre Neustartfähigkeit. Der Konvertierungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise sollte eine Anwendung **mbsrlen** anstelle von **mbslen**verwenden, wenn anstelle von **mbstowcs**ein nachfolgender Aufruf von **mbsrtowcs** verwendet wird.

Wenn *wcstr* kein Nullzeiger ist, wird dem von *mbstr* verwiesenen Zeigerobjekt ein Nullzeiger zugewiesen, wenn die Konvertierung beendet wurde, weil ein beendendes Nullzeichen erreicht wurde. Andernfalls wird es ggf. der Adresse unmittelbar nach dem letzten konvertierten Multibytezeichen zugewiesen. Auf diese Weise kann ein nachfolgender Funktionsaufruf die Konvertierung an der Stelle neu starten, an der der Aufruf beendet wurde.

Wenn das *wcstr-Argument* ein Nullzeiger ist, wird das *Count-Argument* ignoriert, und **mbsrtowcs** gibt die erforderliche Größe in breiten Zeichen für die Zielzeichenfolge zurück. Wenn *mbstate* ein NULL-Zeiger ist, verwendet die Funktion ein nicht threadsicheres statisches **mbstate_t** Konvertierungsstatusobjekt. Wenn die Zeichensequenz *mbstr* keine entsprechende Multibyte-Zeichendarstellung hat, wird eine -1 zurückgegeben und der **Errno** auf **EILSEQ**gesetzt.

Wenn *mbstr* ein Nullzeiger ist, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt -1 zurück.

In C++ hat diese Funktion eine Vorlagenüberladung, mit der die neuere, sichere Entsprechung dieser Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **mbsrtowcs-Funktion** ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, solange diese Funktion ausgeführt wird und das *mbstate-Argument* kein Nullzeiger ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
