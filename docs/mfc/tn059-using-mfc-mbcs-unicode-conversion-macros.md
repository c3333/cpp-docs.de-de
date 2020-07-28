---
title: 'TN059: Verwenden von MFC MBCS-Unicode-Konvertierungs Makros'
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
ms.openlocfilehash: d689e87b8f2804fe99804c6ca37a48bac01df263
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87182732"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059: Verwenden von MFC MBCS/Unicode-Umwandlungsmakros

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

In diesem Hinweis wird beschrieben, wie die Makros für die in afxpriv definierte MBCS/Unicode-Konvertierung verwendet werden. Micha. Diese Makros sind besonders nützlich, wenn Ihre Anwendung direkt mit der OLE-API umgeht oder aus irgendeinem Grund häufig zwischen Unicode und MBCS konvertiert werden muss.

## <a name="overview"></a>Übersicht

In MFC 3. x wurde eine spezielle dll (MFCANS32.DLL) zum automatischen konvertieren zwischen Unicode und MBCS verwendet, als OLE-Schnittstellen aufgerufen wurden. Diese DLL war eine fast transparente Ebene, die das Schreiben von OLE-Anwendungen ermöglichte, als ob es sich bei den OLE-APIs und Schnittstellen um MBCS handelt, obwohl es sich immer um Unicode handelt (mit Ausnahme von Macintosh). Wenngleich diese Ebene praktisch war und zulässige Anwendungen schnell von Win16 nach Win32 portiert werden konnten (MFC, Microsoft Word, Microsoft Excel und VBA, sind nur einige der Microsoft-Anwendungen, die diese Technologie verwendet haben), gab es manchmal bedeutende Leistungseinbußen. Aus diesem Grund verwendet MFC 4. x diese DLL nicht und spricht stattdessen direkt mit den OLE-Schnittstellen von Unicode. Zu diesem Zweck muss MFC bei der Erstellung einer OLE-Schnittstelle in Unicode in MBCS konvertieren und bei der Implementierung einer OLE-Schnittstelle häufig in MBCS konvertieren. Um dies effizient und einfach zu handhaben, wurde eine Reihe von Makros erstellt, um die Konvertierung zu vereinfachen.

Eine der größten Hürden bei der Erstellung eines solchen Satzes von Makros ist die Speicher Belegung. Da die Zeichen folgen nicht an Ort und Stelle konvertiert werden können, muss neuer Arbeitsspeicher für die konvertierten Ergebnisse zugewiesen werden. Dies könnte mit Code geschehen, der etwa wie folgt aussieht:

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

Diese Vorgehensweise ist eine Reihe von Problemen. Das Hauptproblem besteht darin, dass es sich um viel Code zum Schreiben, testen und Debuggen handelt. Etwas, bei dem es sich um einen einfachen Funktions aufrufging, ist nun viel komplexer. Außerdem gibt es einen erheblichen Lauf Zeitaufwand. Der Arbeitsspeicher muss dem Heap zugeordnet und bei jeder Konvertierung freigegeben werden. Schließlich muss der obige Code `#ifdefs` für Unicode-und Macintosh-Builds, die diese Konvertierung nicht benötigen, angemessen hinzugefügt werden.

Die Lösung, mit der wir uns aufkamen, besteht darin, einige Makros zu erstellen, bei denen 1) den Unterschied zwischen den verschiedenen Plattformen maskiert und 2) ein effizientes Speicher Belegungs Schema verwendet und 3) leicht in den vorhandenen Quellcode eingefügt werden können. Im folgenden finden Sie ein Beispiel für eine der Definitionen:

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

Die Verwendung dieses Makros anstelle des obigen Codes und die Dinge sind viel einfacher:

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

Es gibt zusätzliche Aufrufe, bei denen eine Konvertierung erforderlich ist, aber die Verwendung der Makros ist einfach und effektiv.

Die-Implementierung jedes Makros verwendet die _alloca ()-Funktion, um Speicher aus dem Stapel anstelle des Heaps zuzuordnen. Das belegen von Speicher aus dem Stapel ist wesentlich schneller als das belegen von Speicher auf dem Heap, und der Speicher wird automatisch freigegeben, wenn die Funktion beendet wird. Außerdem vermeiden die Makros das Aufrufen von `MultiByteToWideChar` (oder `WideCharToMultiByte` ) mehr als einmal. Dies erfolgt durch Zuweisen eines etwas größeren Speichers als notwendig. Wir wissen, dass ein MBC in höchstens einen **WCHAR** -Wert konvertiert, und dass für jede **WCHAR** -Datei maximal zwei MBC-Bytes vorhanden sein werden. Durch die Zuweisung eines etwas mehr als notwendig, aber immer genug, um die Konvertierung zu verarbeiten, wird der zweite callsecond-Rückruf der Konvertierungs Funktion vermieden. Der Aufruf der-Hilfsfunktion `AfxA2Whelper` reduziert die Anzahl von Argument pushvorgängen, die durchgeführt werden müssen, um die Konvertierung auszuführen (Dies führt zu einem kleineren Code, als wenn er direkt aufgerufen wird `MultiByteToWideChar` ).

Damit die Makros über Speicherplatz verfügen, um eine temporäre Länge zu speichern, muss eine lokale Variable namens _convert deklariert werden, die diese Funktion in jeder Funktion verwendet, die die Konvertierungs Makros verwendet. Dies erfolgt durch Aufrufen des USES_CONVERSION-Makros, wie oben in diesem Beispiel gezeigt.

Es gibt sowohl generische Konvertierungs Makros als auch OLE-spezifische Makros. Diese beiden unterschiedlichen Makro Sätze werden unten erläutert. Alle Makros befinden sich in afxpriv. Micha.

## <a name="generic-conversion-macros"></a>Generische Konvertierungs Makros

Die generischen Konvertierungs Makros bilden den zugrunde liegenden Mechanismus. Das Makro Beispiel und die Implementierung, die im vorherigen Abschnitt, A2W, gezeigt wurden, sind ein solches "generisches" Makro. Er bezieht sich nicht speziell auf OLE. Der Satz generischer Makros ist im folgenden aufgeführt:

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

Neben der Durchführung von Text Konvertierungen gibt es auch Makros und Hilfsfunktionen zum Konvertieren von `TEXTMETRIC` , `DEVMODE` , `BSTR` und von OLE zugeordneten Zeichen folgen. Diese Makros gehen über den Rahmen dieser Diskussion hinaus (siehe afxpriv). H, um weitere Informationen zu diesen Makros zu finden.

## <a name="ole-conversion-macros"></a>OLE-Konvertierungs Makros

Die OLE-Konvertierungs Makros sind speziell für die Handhabung von Funktionen konzipiert, die **OleStr** -Zeichen erwarten. Wenn Sie die OLE-Header untersuchen, werden viele Verweise auf " **lpcolestr** " und " **OLECHAR**" angezeigt. Diese Typen werden verwendet, um auf den Typ von Zeichen zu verweisen, die in OLE-Schnittstellen auf eine Weise verwendet werden, die nicht spezifisch für die Plattform ist. **OLECHAR** ist **`char`** in Win16-und Macintosh-Plattformen und **WCHAR** in Win32 zugeordnet.

Um die Anzahl der **#ifdef** Direktiven im MFC-Code auf ein Mindestmaß zu beschränken, haben wir ein ähnliches Makro für jede Konvertierung, bei der OLE-Zeichen folgen beteiligt sind. Die folgenden Makros werden am häufigsten verwendet:

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

Auch hier gibt es ähnliche Makros für das Ausführen von TextMetric-, DEVMODE-, BSTR-und OLE-zugeordneten Zeichen folgen. Weitere Informationen finden Sie unter afxpriv. H, um weitere Informationen zu finden.

## <a name="other-considerations"></a>Weitere Überlegungen

Verwenden Sie die Makros nicht in einer engen Schleife. Sie möchten z. b. nicht die folgende Art von Code schreiben:

```cpp
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

Der obige Code könnte dazu führen, dass je nachdem, was der Inhalt der Zeichenfolge ist, Megabyte an Arbeitsspeicher im Stapel zugeordnet werden `lpsz` . Außerdem dauert es Zeit, die Zeichenfolge für jede Iterationen der Schleife zu konvertieren. Verschieben Sie stattdessen solche Konstanten Konvertierungen aus der Schleife:

```cpp
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

Wenn die Zeichenfolge nicht konstant ist, Kapseln Sie den Methodenaufrufe in eine Funktion. Dadurch kann der Konvertierungs Puffer jedes Mal freigegeben werden. Beispiel:

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

Gibt nie das Ergebnis einer der Makros zurück, es sei denn, der Rückgabewert impliziert vor der Rückgabe eine Kopie der Daten. Der folgende Code ist z. b. schlecht:

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

Der obige Code kann korrigiert werden, indem der Rückgabewert in einen Wert geändert wird, der den Wert kopiert:

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

Die Makros sind einfach zu verwenden und können einfach in Ihren Code eingefügt werden, aber wie Sie von den vorstehenden Einschränkungen wissen, müssen Sie bei der Verwendung vorsichtig vorgehen.

## <a name="see-also"></a>Weitere Informationen

[Technische Hinweise nach Zahl](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise nach Kategorie](../mfc/technical-notes-by-category.md)
