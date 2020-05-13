---
title: mbsrtowcs_s
ms.date: 4/2/2020
api_name:
- mbsrtowcs_s
- _o_mbsrtowcs_s
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
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 72a20396b2f0f75d79baa64619deef8a0c1e00ba
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915502"
---
# <a name="mbsrtowcs_s"></a>mbsrtowcs_s

Konvertieren einer Zeichenfolge mit Multibytezeichen im aktuellen Gebietsschema in die entsprechende Zeichenfolge mit Breitzeichen. Eine Version von [mbsrtowcs](mbsrtowcs.md) mit Sicherheitserweiterungen wie sie unter [Sicherheitserweiterungen im CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben ist.

## <a name="syntax"></a>Syntax

```C
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t * wcstr,
   size_t sizeInWords,
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
);
template <size_t size>
errno_t mbsrtowcs_s(
   size_t * pReturnValue,
   wchar_t (&wcstr)[size],
   const char ** mbstr,
   size_t count,
   mbstate_t * mbstate
); // C++ only
```

### <a name="parameters"></a>Parameter

*pReturnValue*<br/>
Die Anzahl von konvertierten Zeichen.

*wcstr*<br/>
Pufferadresse zum Speichern der resultierenden konvertierten Zeichenfolge mit Breitzeichen.

*sizin words*<br/>
Die Größe von *wcstr* in Wörtern (breit Zeichen).

*mbstr*<br/>
Indirekter Zeiger auf den Speicherort der Multibyte-Zeichenfolge, die konvertiert werden soll.

*count*<br/>
Die maximale Anzahl von breit Zeichen, die im *wcstr* -Puffer gespeichert werden sollen, ohne das abschließende Null-Zeichen oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungs Zustands Objekt. Wenn dieser Wert ein NULL-Zeiger ist, wird ein statisches internes Konvertierungszustandsobjekt verwendet. Da das interne **mbstate_t** Objekt nicht Thread sicher ist, wird empfohlen, immer ihren eigenen *mbstate* -Parameter zu übergeben.

## <a name="return-value"></a>Rückgabewert

Null, wenn die Konvertierung erfolgreich ist, oder ein Fehlercode bei einem Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*wcstr* ist ein NULL-Zeiger und *sizeIn Words* > 0|**Eingabe**|
|*mbstr* ist ein NULL-Zeiger.|**Eingabe**|
|Die Zeichenfolge, auf die von *mbstr* indirekt verwiesen wird, enthält eine Multibytezeichen-Sequenz, die für das aktuelle Gebiets Schema ungültig ist.|**EILSEQ**|
|Der Ziel Puffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, die *Anzahl* ist **_TRUNCATE**; Weitere Informationen finden Sie unter Hinweise).|**ERANGE**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion einen Fehlercode zurück und legt **errno** wie in der Tabelle angegeben fest.

## <a name="remarks"></a>Hinweise

Die **mbsrtowcs_s** -Funktion konvertiert eine Zeichenfolge von Multibytezeichen, auf die von *mbstr* indirekt gezeigt wird, in im Puffer gespeicherte breit Zeichen, auf die von *wcstr*verwiesen wird, unter Verwendung des in *mbstate*enthaltenen Konvertierungs Zustands. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Multibyte-Nullzeichen wird erkannt.

- Ein ungültiges Multibytezeichen wird erkannt.

- Die Anzahl der breit Zeichen, die im *wcstr* -Puffer gespeichert sind, ist " *count*".

Die Ziel Zeichenfolge *wcstr* wird immer mit Null beendet, auch im Falle eines Fehlers, es sei denn, *wcstr* ist ein NULL-Zeiger.

Wenn *count* der besondere Wert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, konvertiert **mbsrtowcs_s** einen Großteil der Zeichenfolge, die in den Ziel Puffer passt, während er weiterhin Platz für ein NULL-Terminator bleibt.

Wenn **mbsrtowcs_s** die Quell Zeichenfolge erfolgreich konvertiert, wird die Größe der konvertierten Zeichenfolge in breit Zeichen und der NULL-Terminator in *&#42;pReturnValue*eingefügt, sofern *pReturnValue* kein NULL-Zeiger ist. Dies tritt auch dann auf, wenn das *wcstr* -Argument ein NULL-Zeiger ist und Sie die erforderliche Puffergröße bestimmen können. Beachten Sie, dass die *Anzahl* ignoriert wird, wenn *wcstr* ein NULL-Zeiger ist.

Wenn *wcstr* kein NULL-Zeiger ist, wird dem Zeiger Objekt, auf das von *mbstr* verwiesen wird, ein NULL-Zeiger zugewiesen, wenn die Konvertierung beendet wird, da ein abschließendes NULL-Zeichen erreicht wurde. Andernfalls wird es ggf. der Adresse unmittelbar nach dem letzten konvertierten Multibytezeichen zugewiesen. Auf diese Weise kann ein nachfolgender Funktionsaufruf die Konvertierung an der Stelle neu starten, an der der Aufruf beendet wurde.

Wenn *mbstate* ein NULL-Zeiger ist, wird das interne Bibliothek- **mbstate_t** -Konvertierungs Zustands Objekt verwendet. Da dieses interne statische Objekt nicht Thread sicher ist, wird empfohlen, dass Sie Ihren eigenen *mbstate* -Wert übergeben.

Wenn **mbsrtowcs_s** auf ein Multibytezeichen stößt, das im aktuellen Gebiets Schema ungültig ist, wird-1 *in&#42;pReturnValue*eingefügt, der Ziel *Puffer wcstr* auf eine leere Zeichenfolge festgelegt, **errno** auf **EILSEQ**festgelegt und " **EILSEQ**" zurückgegeben.

Wenn die Sequenzen, auf die von *mbstr* und *wcstr* verwiesen wird, überlappen, ist das Verhalten von **mbsrtowcs_s** nicht definiert. **mbsrtowcs_s** wird von der LC_TYPE Kategorie des aktuellen Gebiets Schemas beeinflusst.

> [!IMPORTANT]
> Stellen Sie sicher, dass sich *wcstr* und *mbstr* nicht überlappen *und dass die* Anzahl der zu konvertierenden Multibytezeichen korrekt widerspiegelt.

Die **mbsrtowcs_s** -Funktion unterscheidet [sich von mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) durch die Neustart Fähigkeit. Der Konvertierungs Zustand wird für nachfolgende Aufrufe der gleichen oder anderer Neu startbarer Funktionen in *mbstate* gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert. Beispielsweise sollte eine Anwendung **mbsrlen** anstelle von **mbslen**verwenden, wenn ein nachfolgender **mbsrtowcs_s** anstelle von **mbstowcs_s**verwendet wird.

In C++ wird die Verwendung dieser Funktion durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **mbsrtowcs_s** -Funktion ist multithreadsicher, wenn keine Funktion im aktuellen Thread **setlocale** aufruft, solange diese Funktion ausgeführt wird und das *mbstate* -Argument kein NULL-Zeiger ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Weitere Informationen

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
