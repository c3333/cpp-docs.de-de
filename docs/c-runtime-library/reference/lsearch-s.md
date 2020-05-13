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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: d8c421eb3c7a6a617ce073cbf5f36416294c1874
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920445"
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

*Zahl*<br/>
Anzahl der Elemente.

*size*<br/>
Die Größe jedes Array-Elements in Bytes.

*vergleichbar*<br/>
Ein Zeiger auf die Vergleichsroutine. Der zweite Parameter ist ein Zeiger auf den Schlüssel für die Suche. Der dritte Parameter ist ein Zeiger auf das Arrayelement, das mit dem Schlüssel verglichen werden soll.

*context*<br/>
Ein Zeiger auf ein Objekt, auf das in der Vergleichsfunktion möglicherweise zugegriffen werden kann.

## <a name="return-value"></a>Rückgabewert

Wenn *Key* gefunden wird, gibt **_lsearch_s** einen Zeiger auf das Element des Arrays an der *Basis* zurück, die mit dem *Schlüssel*übereinstimmt. Wenn *Key* nicht gefunden wird, gibt **_lsearch_s** einen Zeiger auf das neu hinzugefügte Element am Ende des Arrays zurück.

Wenn ungültige Parameter an die Funktion übergeben werden, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **null**zurück. Weitere Informationen finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Fehlerbedingungen

|*key*|*base*|*vergleichbar*|*Zahl*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Normal**|any|any|any|any|**Eingabe**|
|any|**Normal**|any|!= 0|any|**Eingabe**|
|any|any|any|any|Null|**Eingabe**|
|any|any|**Normal**|ein|any|**Eingabe**|

## <a name="remarks"></a>Hinweise

Die **_lsearch_s** -Funktion führt eine lineare Suche nach dem Wert *Schlüssel* in einem Array von *Zahlen* Elementen durch, wobei jede *Breite* Bytes beträgt. Anders als bei **bsearch_s**muss **_lsearch_s** das Array nicht sortiert werden. Wenn *Key* nicht gefunden wird, fügt **_lsearch_s** ihn am Ende des Arrays hinzu und erhöht die *Zahl*.

Die *Compare* -Funktion ist ein Zeiger auf eine vom Benutzer bereitgestellte Routine, die zwei Array Elemente vergleicht und einen Wert zurückgibt, der Ihre Beziehung angibt. Die *Compare* -Funktion nimmt auch den Zeiger auf den Kontext als erstes Argument an. bei **_lsearch_s** aufrufen wird ein oder mehrere Male während der Suche *verglichen* , wobei bei jedem Aufruf Zeiger auf zwei Array Elemente übergeben werden. *Compare* muss die Elemente vergleichen und dann entweder ungleich NULL (d.h. die Elemente unterscheiden sich) oder 0 (d.h. die Elemente sind identisch) zurückgeben.

Der *Kontext* Zeiger kann nützlich sein, wenn die durchsuchte Datenstruktur Teil eines Objekts ist und die *Vergleichs* Funktion auf Member des Objekts zugreifen muss. Beispielsweise kann der Code in der *Vergleichs* Funktion den void-Zeiger in den entsprechenden Objekttyp umwandeln und auf Member dieses Objekts zugreifen. Durch das Hinzufügen des *Kontext* Zeigers wird **_lsearch_s** sicherer, da zusätzlicher Kontext verwendet werden kann, um Fehler beim erneuten eintreten zu vermeiden, die mit der Verwendung statischer Variablen zum verfügbar machen von Daten für die *Vergleichs* Funktion einhergehen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Suchen und Sortieren](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
