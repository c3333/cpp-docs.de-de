---
title: 'TN059: Verwenden von MFC MBCS-Unicode-Konvertierungsmakros'
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: 657381d8247aef14b2c725996dfeb11d0e0535fe
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749444"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Verwenden von MFC MBCS/Unicode-Umwandlungsmakros

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

In diesem Hinweis wird beschrieben, wie die Makros für die MBCS/Unicode-Konvertierung verwendet werden, die in AFXPRIV definiert sind. H. Diese Makros sind am nützlichsten, wenn Ihre Anwendung direkt mit der OLE-API umgeht oder aus irgendeinem Grund häufig zwischen Unicode und MBCS konvertieren muss.

## <a name="overview"></a>Übersicht

In MFC 3.x wurde eine spezielle DLL verwendet (MFCANS32. DLL), um automatisch zwischen Unicode und MBCS zu konvertieren, wenn OLE-Schnittstellen aufgerufen wurden. Diese DLL war eine fast transparente Ebene, die es ermöglichte, OLE-Anwendungen so zu schreiben, als ob die OLE-APIs und -Schnittstellen MBCS wären, obwohl sie immer Unicode sind (außer auf dem Macintosh). Obwohl diese Ebene bequem war und es ermöglichte, Anwendungen schnell von Win16 nach Win32 zu portieren (MFC, Microsoft Word, Microsoft Excel und VBA, sind nur einige der Microsoft-Anwendungen, die diese Technologie verwendet haben), hatte es manchmal einen erheblichen Leistungseinschlag. Aus diesem Grund verwendet MFC 4.x diese DLL nicht und spricht stattdessen direkt mit den Unicode OLE-Schnittstellen. Dazu muss MFC beim Aufruf einer OLE-Schnittstelle in Unicode in MBCS konvertieren und beim Implementieren einer OLE-Schnittstelle häufig von Unicode in MBCS konvertieren. Um dies effizient und einfach zu handhaben, wurden eine Reihe von Makros erstellt, um diese Konvertierung zu erleichtern.

Eine der größten Hürden beim Erstellen eines solchen Satzes von Makros ist die Speicherzuweisung. Da die Zeichenfolgen nicht an Ort und Stelle konvertiert werden können, muss neuer Speicher für die konvertierten Ergebnisse zugewiesen werden. Dies hätte mit Code ähnlich dem folgenden durchgeführt werden können:

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

Dieser Ansatz ist eine Reihe von Problemen. Das Hauptproblem ist, dass es viel Code zum Schreiben, Testen und Debuggen ist. Etwas, das ein einfacher Funktionsaufruf war, ist jetzt viel komplexer. Darüber hinaus gibt es dabei einen erheblichen Laufzeitaufwand. Speicher muss auf dem Heap zugewiesen und bei jeder Konvertierung freigegeben werden. Schließlich müsste der obige Code `#ifdefs` für Unicode- und Macintosh-Builds entsprechend hinzugefügt werden (die diese Konvertierung nicht erfordern).

Die Lösung, die wir entwickelt haben, ist, einige Makros zu erstellen, die 1) den Unterschied zwischen den verschiedenen Plattformen maskieren und 2) ein effizientes Speicherzuweisungsschema verwenden, und 3) sind einfach in den vorhandenen Quellcode einzufügen. Hier ist ein Beispiel für eine der Definitionen:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Verwenden Sie dieses Makro anstelle des obigen Codes und die Dinge sind viel einfacher:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Es gibt zusätzliche Aufrufe, bei denen konvertierung erforderlich ist, aber die Verwendung der Makros ist einfach und effektiv.

Die Implementierung jedes Makros verwendet die _alloca()-Funktion, um Speicher aus dem Stapel anstelle des Heaps zuzuweisen. Das Zuweisen von Speicher aus dem Stapel ist viel schneller als das Zuweisen von Speicher auf dem Heap, und der Speicher wird automatisch freigegeben, wenn die Funktion beendet wird. Darüber hinaus vermeiden die `MultiByteToWideChar` Makros `WideCharToMultiByte`das Aufrufen (oder ) mehr als einmal. Dies geschieht, indem etwas mehr Speicher als nötig zugewiesen wird. Wir wissen, dass ein MBC in höchstens einen **WCHAR** konvertiert wird und dass wir für jeden **WCHAR** maximal zwei MBC-Bytes haben werden. Durch die Zuweisung etwas mehr als notwendig, aber immer genug, um die Konvertierung zu behandeln, wird der zweite Aufruf des zweiten Aufrufs an die Konvertierungsfunktion vermieden. Der Aufruf der Hilfsfunktion `AfxA2Whelper` reduziert die Anzahl der Argument-Pushs, die ausgeführt werden müssen, um die `MultiByteToWideChar` Konvertierung durchzuführen (dies führt zu kleinerem Code, als wenn er direkt aufgerufen wird).

Damit die Makros über Platz zum Speichern der temporären Länge verfügen, ist es notwendig, eine lokale Variable namens _convert zu deklarieren, die dies in jeder Funktion tut, die die Konvertierungsmakros verwendet. Dies geschieht durch Aufrufen des USES_CONVERSION Makros, wie oben im Beispiel zu sehen.

Es gibt sowohl generische Konvertierungsmakros als auch OLE-spezifische Makros. Diese beiden verschiedenen Makrosätze werden im Folgenden erläutert. Alle Makros befinden sich in AFXPRIV. H.

## <a name="generic-conversion-macros"></a>Generische Konvertierungsmakros

Die generischen Konvertierungsmakros bilden den zugrunde liegenden Mechanismus. Das im vorherigen Abschnitt Gezeigte Makrobeispiel und die Implementierung, A2W, ist ein solches "generisches" Makro. Es bezieht sich nicht speziell auf OLE. Der Satz generischer Makros ist unten aufgeführt:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Neben Textkonvertierungen gibt es auch Makros und Hilfsfunktionen `DEVMODE` `BSTR`zum Konvertieren von , , und OLE zugewiesenen `TEXTMETRIC`Zeichenfolgen. Diese Makros gehen über den Rahmen dieser Diskussion hinaus - siehe AFXPRIV. H für weitere Informationen zu diesen Makros.

## <a name="ole-conversion-macros"></a>OLE-Konvertierungsmakros

Die OLE-Konvertierungsmakros wurden speziell für die Handhabung von Funktionen entwickelt, die **OLESTR-Zeichen** erwarten. Wenn Sie die OLE-Header untersuchen, werden viele Verweise auf **LPCOLESTR** und **OLECHAR**angezeigt. Diese Typen werden verwendet, um auf den Typ von Zeichen zu verweisen, die in OLE-Schnittstellen in einer Weise verwendet werden, die nicht plattformspezifisch ist. **OLECHAR** ordnet **char** in Win16- und Macintosh-Plattformen und **WCHAR** in Win32 zu.

Um die Anzahl der **#ifdef** Direktiven im MFC-Code auf ein Minimum zu beschränken, haben wir für jede Konvertierung ein ähnliches Makro wie ole-Zeichenfolgen. Die folgenden Makros werden am häufigsten verwendet:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Auch hier gibt es ähnliche Makros für textMETRIC, DEVMODE, BSTR und OLE zugewiesene Zeichenfolgen. Siehe AFXPRIV. H für weitere Informationen.

## <a name="other-considerations"></a>Weitere Überlegungen

Verwenden Sie die Makros nicht in einer engen Schleife. Sie möchten z. B. nicht die folgende Art von Code schreiben:

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Der obige Code kann dazu führen, dass Megabyte Arbeitsspeicher `lpsz` auf dem Stapel zugewiesen werden, je nachdem, was der Inhalt der Zeichenfolge ist! Es dauert auch Zeit, um die Zeichenfolge für jede Iteration der Schleife zu konvertieren. Verschieben Sie stattdessen solche konstanten Konvertierungen aus der Schleife:

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Wenn die Zeichenfolge nicht konstant ist, kapseln Sie den Methodenaufruf in eine Funktion. Dadurch kann der Konvertierungspuffer jedes Mal freigegeben werden. Beispiel:

```cpp
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

Geben Sie niemals das Ergebnis eines der Makros zurück, es sei denn, der Rückgabewert impliziert, dass eine Kopie der Daten vor der Rückgabe erstellt wird. Dieser Code ist z. B. fehlerhaft:

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

Der obige Code könnte behoben werden, indem der Rückgabewert in etwas geändert wird, das den Wert kopiert:

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

Die Makros sind einfach zu bedienen und einfach in Ihren Code einzufügen, aber wie Sie aus den obigen Vorbehalten erkennen können, müssen Sie vorsichtig sein, wenn Sie sie verwenden.

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
