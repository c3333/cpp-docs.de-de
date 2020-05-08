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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: fc9310a95165944b7f516c1f8c48d8d4d1e56117
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915481"
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

*wcstr*<br/>
Adresse zum Speichern der resultierenden konvertierten Zeichenfolge mit Breitzeichen.

*mbstr*<br/>
Indirekter Zeiger auf den Speicherort der zu konvertierenden Zeichenfolge mit Multibytezeichen.

*count*<br/>
Die maximale Anzahl von Zeichen (nicht Bytes), die konvertiert und in *wcstr*gespeichert werden sollen.

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungs Zustands Objekt. Wenn dieser Wert ein NULL-Zeiger ist, wird ein statisches internes Konvertierungszustandsobjekt verwendet. Da das interne **mbstate_t** Objekt nicht Thread sicher ist, wird empfohlen, immer ihren eigenen *mbstate* -Parameter zu übergeben.

## <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Zeichen zurück, die erfolgreich konvertiert wurden, nicht einschließlich des abschließenden Zeichens NULL, sofern vorhanden. Gibt (size_t) (-1) zurück, wenn ein Fehler aufgetreten ist, und legt **errno** auf EILSEQ fest.

## <a name="remarks"></a>Hinweise

Die **mbsrtowcs** -Funktion konvertiert eine Zeichenfolge von Multibytezeichen, auf die von *mbstr*indirekt verwiesen wird, in breit Zeichen, die im Puffer gespeichert werden, auf die von *wcstr*verwiesen wird, indem der in *mbstate*enthaltene Konvertierungs Zustand verwendet wird. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis entweder ein abschließendes NULL-Multibytezeichen gefunden wird, eine multibytefolge, die keinem gültigen Zeichen im aktuellen Gebiets Schema entspricht, oder bis *Zähl* Zeichen konvertiert wurden. Wenn **mbsrtowcs** das Multibytezeichen-NULL Zeichen (' \ 0 ') erkennt, entweder vor oder wenn die *Anzahl* auftritt, wird es in ein 16-Bit-abschließende Null-Zeichen konvertiert und beendet.

Folglich ist die Zeichenfolge mit breit Zeichen bei *wcstr* nur dann NULL-terminiert, wenn **mbsrtowcs** während der Konvertierung ein Multibytezeichen NULL findet. Wenn die Sequenzen, auf die von *mbstr* und *wcstr* verwiesen wird, überlappen, ist das Verhalten von **mbsrtowcs** nicht definiert. **mbsrtowcs** ist von der LC_TYPE Kategorie des aktuellen Gebiets Schemas betroffen.

Die **mbsrtowcs** -Funktion unterscheidet [sich von mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md) durch die neustarbarkeit. Der Konvertierungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert.  Beispielsweise sollte eine Anwendung **mbsrlen** anstelle von **mbslen**verwenden, wenn ein nachfolgender Befehl von **mbsrtowcs** anstelle von **mbstowcs**verwendet wird.

Wenn *wcstr* kein NULL-Zeiger ist, wird dem Zeiger Objekt, auf das von *mbstr* verwiesen wird, ein NULL-Zeiger zugewiesen, wenn die Konvertierung beendet wird, da ein abschließendes NULL-Zeichen erreicht wurde. Andernfalls wird es ggf. der Adresse unmittelbar nach dem letzten konvertierten Multibytezeichen zugewiesen. Auf diese Weise kann ein nachfolgender Funktionsaufruf die Konvertierung an der Stelle neu starten, an der der Aufruf beendet wurde.

Wenn das *wcstr* -Argument ein NULL-Zeiger ist, wird das *count* -Argument ignoriert, und **mbsrtowcs** gibt die erforderliche Größe in breit Zeichen für die Ziel Zeichenfolge zurück. Wenn *mbstate* ein NULL-Zeiger ist, verwendet die Funktion ein nicht Thread sicheres statisches internes **mbstate_t** -Konvertierungs Zustands Objekt. Wenn die Zeichen Sequenz *mbstr* nicht über eine entsprechende Multibytezeichen-Zeichen Darstellung verfügt, wird-1 zurückgegeben, und **errno** ist auf **EILSEQ**festgelegt.

Wenn *mbstr* ISA NULL-Zeiger ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legt diese Funktion **errno** auf **EINVAL** fest und gibt-1 zurück.

In C++ hat diese Funktion eine Vorlagenüberladung, mit der die neuere, sichere Entsprechung dieser Funktion aufgerufen wird. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **mbsrtowcs** -Funktion ist multithreadsicher, solange keine Funktion im aktuellen Thread **setlocale** aufruft, solange diese Funktion ausgeführt wird und das *mbstate* -Argument kein NULL-Zeiger ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
