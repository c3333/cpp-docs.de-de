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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs_s
helpviewer_keywords:
- mbsrtowcs_s function
ms.assetid: 4ee084ec-b15d-4e5a-921d-6584ec3b5a60
ms.openlocfilehash: 62ae534e8080b74ada49cca005811a049055cb65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338904"
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

*Preturnvalue*<br/>
Die Anzahl von konvertierten Zeichen.

*Wcstr*<br/>
Pufferadresse zum Speichern der resultierenden konvertierten Zeichenfolge mit Breitzeichen.

*sizeInWords*<br/>
Die Größe von *wcstr* in Wörtern (breite Zeichen).

*mbstr*<br/>
Indirekter Zeiger auf den Speicherort der Multibyte-Zeichenfolge, die konvertiert werden soll.

*count*<br/>
Die maximale Anzahl von breiten Zeichen, die im *wcstr-Puffer* gespeichert werden sollen, ohne die beendende NULL oder [_TRUNCATE](../../c-runtime-library/truncate.md).

*mbstate*<br/>
Ein Zeiger auf ein **mbstate_t** Konvertierungsstatusobjekt. Wenn dieser Wert ein NULL-Zeiger ist, wird ein statisches internes Konvertierungszustandsobjekt verwendet. Da das interne **mbstate_t** Objekt nicht threadsicher ist, wird empfohlen, immer einen eigenen *mbstate-Parameter* zu übergeben.

## <a name="return-value"></a>Rückgabewert

Null, wenn die Konvertierung erfolgreich ist, oder ein Fehlercode bei einem Fehler.

|Fehlerzustand|Rückgabewert und **errno**|
|---------------------|------------------------------|
|*wcstr* ist ein Nullzeiger und *sizeInWords* > 0|**Einval**|
|*mbstr* ist ein Nullzeiger|**Einval**|
|Die Zeichenfolge, auf die indirekt von *mbstr* verwiesen wird, enthält eine Multibyte-Sequenz, die für das aktuelle Gebietsschema nicht gültig ist.|**EILSEQ**|
|Der Zielpuffer ist zu klein, um die konvertierte Zeichenfolge zu enthalten (es sei denn, *die Anzahl* ist **_TRUNCATE;** weitere Informationen finden Sie unter Hinweise)|**ERANGE**|

Wenn eine dieser Bedingungen auftritt, wird die Ausnahme für ungültige Parameter aufgerufen, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion einen Fehlercode zurück und setzt **errno,** wie in der Tabelle angegeben.

## <a name="remarks"></a>Bemerkungen

Die **mbsrtowcs_s-Funktion** konvertiert eine Zeichenfolge mit Multibyte-Zeichen, auf die *mbstr* indirekt zeigt, in breite Zeichen, auf die im Puffer von *wcstr*verwiesen wird, indem der Konvertierungsstatus in *mbstate*verwendet wird. Die Konvertierung wird für jedes Zeichen fortgesetzt, bis eine der folgenden Bedingungen eintritt:

- Ein Multibyte-Nullzeichen wird erkannt.

- Ein ungültiges Multibytezeichen wird erkannt.

- Die Anzahl der im *wcstr-Puffer* gespeicherten breiten Zeichen entspricht *der Anzahl*.

Die Zielzeichenfolge *wcstr* ist immer null-beendet, auch im Falle eines Fehlers, es sei denn, *wcstr* ist ein Nullzeiger.

Wenn *count* der sonderwert [_TRUNCATE](../../c-runtime-library/truncate.md)ist, **konvertiert mbsrtowcs_s** so viel von der Zeichenfolge, wie in den Zielpuffer passt, während er dennoch Platz für einen Nullabschluss lässt.

Wenn **mbsrtowcs_s** die Quellzeichenfolge erfolgreich konvertiert, wird die Größe in breiten Zeichen der konvertierten Zeichenfolge und des NULL-Terminators in *&#42;pReturnValue*gesetzt, vorausgesetzt *pReturnValue* ist kein Nullzeiger. Dies tritt auch dann auf, wenn das *wcstr-Argument* ein Nullzeiger ist und Sie die erforderliche Puffergröße bestimmen können. Beachten Sie, dass, wenn *wcstr* ein Nullzeiger ist, *die Anzahl* ignoriert wird.

Wenn *wcstr* kein Nullzeiger ist, wird dem von *mbstr* verwiesenen Zeigerobjekt ein Nullzeiger zugewiesen, wenn die Konvertierung beendet wurde, weil ein beendendes Nullzeichen erreicht wurde. Andernfalls wird es ggf. der Adresse unmittelbar nach dem letzten konvertierten Multibytezeichen zugewiesen. Auf diese Weise kann ein nachfolgender Funktionsaufruf die Konvertierung an der Stelle neu starten, an der der Aufruf beendet wurde.

Wenn *mbstate* ein Nullzeiger ist, wird das interne **mbstate_t** statisches Konvertierungsstatusobjekt verwendet. Da dieses interne statische Objekt nicht threadsicher ist, wird empfohlen, einen eigenen *mbstate-Wert* zu übergeben.

Wenn **mbsrtowcs_s** auf ein Multibyte-Zeichen trifft, das im aktuellen Gebietsschema ungültig ist, setzt es -1 in *&#42;pReturnValue*, legt den Zielpuffer *wcstr* auf eine leere Zeichenfolge fest, setzt **errno** auf **EILSEQ**und gibt **EILSEQ**zurück.

Wenn sich die Sequenzen, auf die *mbstr* und *wcstr* zeigten, überlappen, ist das Verhalten von **mbsrtowcs_s** nicht definiert. **mbsrtowcs_s** wird von der Kategorie LC_TYPE des aktuellen Gebietsschemas beeinflusst.

> [!IMPORTANT]
> Stellen Sie sicher, dass *sich wcstr* und *mbstr* nicht überlappen und diese *Anzahl* die Anzahl der zu konvertierenden Multibyte-Zeichen korrekt wiedergibt.

Die **mbsrtowcs_s** Funktion unterscheidet sich von [mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md) durch ihre Neustartfähigkeit. Der Konvertierungsstatus wird in *mbstate* für nachfolgende Aufrufe derselben oder anderer neustartbarer Funktionen gespeichert. Wenn sowohl Funktionen, die neu gestartet werden können, als auch Funktionen, die nicht neu gestartet werden könnnen, verwendet werden, sind die Ergebnisse undefiniert. Eine Anwendung sollte z. B. **mbsrlen** anstelle von **mbslen**verwenden, wenn anstelle von **mbstowcs_s**ein nachfolgender Aufruf **von mbsrtowcs_s** verwendet wird.

In C++ wird die Verwendung dieser Funktion durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="exceptions"></a>Ausnahmen

Die **mbsrtowcs_s-Funktion** ist multithreadsicher, wenn keine Funktion im aktuellen Thread **setlocale** aufruft, solange diese Funktion ausgeführt wird und das *mbstate-Argument* kein Nullzeiger ist.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**mbsrtowcs_s**|\<wchar.h>|

## <a name="see-also"></a>Siehe auch

[Datenkonvertierung](../../c-runtime-library/data-conversion.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs_s, _mbstowcs_s_l](mbstowcs-s-mbstowcs-s-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
