---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341651"
---
# <a name="_lsearch_s"></a>_lsearch_s

Führt eine lineare Suche für einen Wert aus. Eine Version von [_lsearch](lsearch.md) mit Sicherheitserweiterungen, so wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Das Objekt, nach dem gesucht werden soll.

*base*<br/>
Zeiger auf der Basis des zu durchsuchenden Arrays.

*number*<br/>
Anzahl der Elemente.

*Größe*<br/>
Die Größe jedes Array-Elements in Bytes.

*Vergleichen*<br/>
Ein Zeiger auf die Vergleichsroutine. Der zweite Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der dritte Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

*context*<br/>
Ein Zeiger auf ein Objekt, auf das in der Vergleichsfunktion möglicherweise zugegriffen werden kann.

## <a name="return-value"></a>Rückgabewert

Wenn *der Schlüssel* gefunden wird, gibt **_lsearch_s** einen Zeiger auf das Element des Arrays an der *Basis* zurück, das mit *dem Schlüssel*übereinstimmt. Wenn *der Schlüssel* nicht gefunden wird, gibt **_lsearch_s** einen Zeiger auf das neu hinzugefügte Element am Ende des Arrays zurück.

Wenn ungültige Parameter an die Funktion übergeben werden, wird der ungültige Parameterhandler aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und die Funktion gibt **NULL**zurück. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*key*|*base*|*Vergleichen*|*number*|*Größe*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Null**|any|any|any|any|**Einval**|
|any|**Null**|any|!= 0|any|**Einval**|
|any|any|any|any|Null|**Einval**|
|any|any|**Null**|ein|any|**Einval**|

## <a name="remarks"></a>Bemerkungen

Die **_lsearch_s-Funktion** führt eine lineare Suche nach dem *Wertschlüssel* in einem Array von *Zahlenelementen* mit jeweils *mehreren* Bytes durch. Im Gegensatz zu **bsearch_s** **erfordert _lsearch_s** nicht, dass das Array sortiert wird. Wenn *der Schlüssel* nicht gefunden wird, fügt **_lsearch_s** ihn am Ende des Arrays hinzu und erhöht die *Zahl*.

Die *Vergleichsfunktion* ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Arrayelemente vergleicht und einen Wert zurückgibt, der ihre Beziehung angibt. Die *Vergleichsfunktion* nimmt auch den Zeiger auf den Kontext als erstes Argument. **_lsearch_s-Aufrufe** *vergleichen* ein oder mehrere Male während der Suche, indem Sie Zeiger an zwei Arrayelemente bei jedem Aufruf übergeben. *compare* muss die Elemente vergleichen und dann entweder ungleich Null (d. h. die Elemente sind unterschiedlich) oder 0 (d. h. die Elemente sind identisch) zurückgegeben werden.

Der *Kontextzeiger* kann nützlich sein, wenn die gesuchte Datenstruktur Teil eines Objekts ist und die *Vergleichsfunktion* auf Member des Objekts zugreifen muss. Beispielsweise kann Code in der *Vergleichsfunktion* den leeren Zeiger in den entsprechenden Objekttyp und die Zugriffsmember dieses Objekts umsetzen. Das Hinzufügen des *Kontextzeigers* macht **_lsearch_s** sicherer, da zusätzlicher Kontext verwendet werden kann, um Reentrancy-Fehler zu vermeiden, die mit der Verwendung statischer Variablen verbunden sind, um Daten für die *Vergleichsfunktion* verfügbar zu machen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
