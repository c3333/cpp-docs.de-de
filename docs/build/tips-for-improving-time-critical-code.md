---
title: Tipps zum Verbessern von zeitkritischem Code
ms.date: 11/04/2016
helpviewer_keywords:
- _lsearch function
- qsort function
- background tasks
- standard sort routines
- clock cycle losses
- code, time-critical
- memory [C++], monitoring usage
- execution, speed improvements
- local heap performance
- optimization [C++], time-critical code
- performance [C++], time-critical code
- threading [C++], performance
- cache [C++], hits and misses
- linear search performance
- page faults
- best practices, time-critical code
- searching [C++], improving performance
- sorting data, improving performance
- threading [C++], best practices
- threading [C++], background tasks
- lists, sorting
- bsearch function
- MFC [C++], performance
- sort routines
- programs [C++], performance
- _lfind function
- heap allocation, time-critical code performance
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
ms.openlocfilehash: a2cc8062368b89e38b5f96b3134742123af24310
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231480"
---
# <a name="tips-for-improving-time-critical-code"></a>Tipps zum Verbessern von zeitkritischem Code

Für das Schreiben von schnellem Code müssen Sie alle Aspekte Ihrer Anwendung und der Interaktion mit dem System verstehen. In den folgenden Themen finden Sie Alternativen zu einigen der offensichtlicheren Codierungstechniken, damit Sie sicherstellen können, dass die zeitkritischen Teile Ihres Codes eine zufriedenstellende Leistung erbringen.

Zusammenfassend ist für das Verbessern von zeitkritischem Code Folgendes erforderlich:

- Sie müssen wissen, welche Teile Ihres Programms schnell sein müssen

- Sie müssen die Größe und Geschwindigkeit Ihres Codes kennen.

- Sie müssen die Kosten neuer Funktionen kennen.

- Sie müssen die erforderliche Mindestarbeit kennen, um die Aufgabe zu erledigen.

Sie können den Leistungsmonitor (perfmon.exe) verwenden, um Informationen zur Leistung Ihres Codes zu sammeln.

## <a name="sections-in-this-article"></a>Abschnitte in diesem Artikel

- [Cachefehler und Seitenfehler](#_core_cache_hits_and_page_faults)

- [Sortieren und Suchen](#_core_sorting_and_searching)

- [MFC- und Klassenbibliotheken](#_core_mfc_and_class_libraries)

- [Freigegebene Bibliotheken](#vcovrsharedlibraries)

- [Heaps](#_core_heaps)

- [Threads](#_core_threads)

- [Kleines Workingset](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a> Cachefehler und Seitenfehler

Fehler bei Cachetreffern, sowohl im internen als auch im externen Cache, und Seitenfehler (das Zugreifen auf sekundären Speicher für Programmanweisungen und Daten) verlangsamen die Leistung eines Programms.

Ein CPU-Cachetreffer kann Ihr Programm 10 bis 20 Uhrzyklen kosten. Ein externer Cachetreffer kann 20 bis 40 Uhrzyklen kosten. Ein Seitenfehler kann eine Million Uhrzyklen kosten (ausgehend von einem Prozessor, der 500 Millionen Anweisungen/Sekunde verarbeitet und eine Zeit von 2 Millisekunden für einen Seitenfehler braucht). Daher ist es im besten Interesse der Programmausführung, Code zu schreiben, der die Anzahl von Fehlern bei Cachetreffern und Seitenfehlern verringert.

Ein Grund für langsame Programme ist, dass diese mehr Seitenfehler oder mehr Cachefehler als erforderlich verursachen. Um dies zu vermeiden, ist es wichtig, Datenstrukturen mit einer guten Positionierung von Verweisen zu verwenden, was bedeutet, aufeinander bezogene Dinge zusammenzuhalten. Manchmal erweist sich eine Datenstruktur, die großartig aussieht, aufgrund einer schlechten Positionierung von Verweisen als schrecklich, manchmal ist es umgekehrt. Hier sind zwei Beispiele:

- Dynamisch zugeordnete verknüpfte Listen können die Programmleistung reduzieren, denn wenn Sie nach einem Element suchen oder eine Liste bis zum Ende durchlaufen, kann jede übersprungene Verknüpfung einen Cachefehler oder einen Seitenfehler verursachen. Eine Listenimplementierung auf der Basis von einfachen Array ist tatsächlich möglicherweise wegen besseren Zwischenspeicherns und weniger Seitenfehlern viel schneller – selbst wenn man die Tatsache berücksichtigt, dass das Array schwerer wächst, ist es möglicherweise immer noch schneller.

- Hashtabellen, die dynamisch zugewiesene verknüpfte Listen verwenden, können die Leistung verschlechtern. Durch Erweiterung können Hashtabellen, die dynamisch zugeordnete verknüpftet Listen zum Speichern ihrer Inhalte verwenden, eine wesentlichere schlechtere Leistung zeigen. Tatsächlich ist in der letztendlichen Analyse eine einfache lineare Suche durch ein Array tatsächlich möglicherweise schneller (je nach Umständen). Arraybasierte Hashtabellen (das sogenannte „geschlossene Hashing“) ist eine oft übersehene Implementierung, die oft eine erstklassige Leistung zeigt.

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a> Sortieren und Suchen

Das Sortieren ist im Vergleich zu vielen typischen Vorgängen an sich zeitaufwendig. Die beste Methode, um eine unnötige Verlangsamung zu vermeiden, besteht darin, das Sortieren in kritischen Zeiten zu vermeiden. Möglicherweise können Sie Folgendes tun:

- Verzögern der Sortierung bis zu einem Zeitpunkt, der für die Leistung nicht kritisch ist

- Sortieren der Daten zu einem früheren Zeitpunkt, der für die Leistung nicht kritisch ist

- Reines Sortieren des Teils der Daten, der wirklich sortiert werden muss

Manchmal können Sie die Liste in sortierter Reihenfolge erstellen. Gehen Sie sorgfältig vor, denn wenn Sie Daten in sortierter Reihenfolge einfügen müssen, ist möglicherweise eine kompliziertere Datenstruktur mit einer schlechten Positionierung von Hinweisen erforderlich, die zu Cachefehlern und Seitenfehlern führen kann. Es gibt keinen Ansatz, der in allen Fällen funktioniert. Probieren Sie mehrere Ansätze aus, und messen Sie die Unterschiede.

Hier sind einige allgemeine Tipps für das Sortieren:

- Verwenden Sie eine vordefinierte Sortierung, um Fehler zu minimieren.

- Jede Arbeit, die Sie vorab erledigen können, um die Komplexität der Sortierung zu reduzieren, lohnt sich. Wenn eine einmalige Übergabe Ihrer Daten die Vergleiche vereinfacht und die Sortierung von O(n log n) zu O(n) reduziert, werden Sie nahezu immer davon profitieren.

- Denken Sie über die Positionierung der Hinweise des Sortierungsalgorithmus und die Daten nach, mit denen dieser erwartungsgemäß ausgeführt wird.

Es gibt weniger Alternativen für Suchen als für die Sortierung. Wenn die Suche zeitkritisch ist, ist eine binäre oder Hashtabellensuche nahezu immer am besten, aber wie bei der Sortierung müssen Sie die Positionierung im Hinterkopf behalten. Eine lineare Suche durch ein kleines Array kann schneller sein als eine binäre Suche durch eine Datenstruktur mit vielen Zeigern, die zu Seitenfehlern oder Cachefehlern führen kann.

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a> MFC- und Klassenbibliotheken

Die Microsoft Foundation Classes (MFC) können das Schreiben von Code erheblich vereinfachen. Wenn Sie zeitkritischen Code schreiben, sollte Ihnen der einigen der Klassen innewohnende Mehraufwand bewusst sein. Untersuchen Sie den MFC-Code, den Ihr zeitkritischer Code verwendet, um zu sehen, ob er Ihren Leistungsanforderungen entspricht. In der folgenden Liste sind die MFC-Klassen und -Funktionen aufgeführt, die Ihnen bewusst sein sollten:

- `CString` MFC ruf die C-Laufzeitbibliothek auf, um Speicher dynamisch für [CString](../atl-mfc-shared/reference/cstringt-class.md) zu belegen. Allgemein gesagt ist `CString` ebenso effizient wie jede andere dynamisch zugeordnete Zeichenfolge. Wie bei jeder dynamisch zugewiesenen Zeichenfolge besteht der Mehraufwand der dynamischen Zuordnung und Freigabe. Häufig erfüllt ein einfaches **`char`** -Array im Stapel denselben Zweck und ist schneller. Verwenden Sie nicht `CString`, um eine konstante Zeichenfolge zu speichern. Verwenden Sie stattdessen `const char *`. Jeder Vorgang, den Sie mit einem `CString`-Objekt durchführen, hat irgendeinen Mehraufwand. Möglicherweise ist es schneller, die [Zeichenfolgenfunktionen](../c-runtime-library/string-manipulation-crt.md) der Laufzeitbibliothek zu verwenden.

- `CArray` Ein [CArray](../mfc/reference/carray-class.md) bietet eine Art von Flexibilität, die ein reguläres Array nicht bietet, aber Ihr Programm benötigt diese möglicherweise nicht. Wenn Sie bestimmte Grenzen für das Array kennen, können Sie stattdessen ein globales festes Array verwenden. Wenn Sie `CArray` benutzen, verwenden Sie `CArray::SetSize`, um die Größe festzulegen und die Anzahl der Elemente anzugeben, um die es wachsen kann, wenn eine Neuzuordnung erforderlich ist. Andernfalls kann das Hinzufügen von Elementen dazu führen, dass Ihr Array häufig neu zugeordnet und kopiert wird, was ineffizient ist und den Arbeitsspeicher fragmentieren kann. Ihnen sollte auch bewusst sein, dass beim Einfügen eines Elements in ein Array `CArray` nachfolgende Elemente im Arbeitsspeicher verschiebt und möglicherweise das Array vergrößern muss. Diese Aktionen können zu Cachefehlern und Seitenfehlern führen. Wenn Sie den Code durchsehen, den die MFC verwenden, sehen Sie möglicherweise, dass Sie etwas Spezifischeres für Ihr Szenario schreiben können, um die Leistung zu verbessern. Da `CArray` eine Vorlage ist, können Sie beispielsweise `CArray`-Spezialisierungen für bestimmte Typen bereitstellen.

- `CList` [CList](../mfc/reference/clist-class.md) ist eine doppelt verknüpfte Liste, was bedeutet, dass die Elementeinfügung am Anfang, am Ende und an einer bekannten Position (`POSITION`) in der Liste schnell ist. Für die Suche nach einem Element nach Wert oder Index ist jedoch eine sequenzielle Suche erforderlich, die langsam sein kann, wenn die Liste lang ist. Wenn für Ihren Code keine doppelt verknüpfte Liste erforderlich ist, sollten Sie die Verwendung von `CList` in Betracht ziehen. Die Verwendung einer einfach verknüpften Liste spart den Mehraufwand der Aktualisierung eines zusätzlichen Zeigers für alle Vorgänge sowie den Arbeitsspeicher für diesen Zeiger. Der zusätzliche Arbeitsspeicher ist nicht hervorragend, aber eine weitere Gelegenheit für Cachefehler oder Seitenfehler.

- `IsKindOf` Diese Funktion kann mehrere Aufrufe generieren und auf eine Menge Arbeitsspeicher in verschiedenen Datenbereichen zugreifen, was zu einer schlechten Positionierung von Verweisen führt. Sie ist nützlich für einen Debugbuild (zum Beispiel in einem ASSERT-Aufruf), Sie sollten aber vermeiden, sie in einem Releasebuild zu verwenden.

- `PreTranslateMessage` Verwenden Sie `PreTranslateMessage`, wenn eine bestimmte Fensterstruktur Tastaturbeschleuniger benötigt oder Sie eine Verarbeitung von Meldungen in das Nachrichtensystem einfügen müssen. `PreTranslateMessage` ändert MFC-Dispatchmeldungen. Wenn Sie `PreTranslateMessage` überschreiben, tun Sie das nur auf der erforderlichen Ebene. Es ist beispielsweise nicht erforderlich, `CMainFrame::PreTranslateMessage` zu überschreiben, wenn Sie nur an Meldungen interessiert sind, die an untergeordnete Elemente einer bestimmten Ansicht gehen. Überschreiben Sie stattdessen `PreTranslateMessage` für die Ansichtsklasse.

   Umgehen Sie nicht den normalen Dispatchpfad, indem Sie `PreTranslateMessage` verwenden, um Meldungen zu verarbeiten, die an ein beliebiges Fenster gesendet werden. Verwenden Sie für diesen Zweck [Fensterprozeduren](../mfc/registering-window-classes.md) und MFC-Meldungszuordnungen.

- `OnIdle` Ereignisse im Leerlauf können zu unerwarteten Zeiten auftauchen, beispielsweise zwischen `WM_KEYDOWN`- und `WM_KEYUP`-Ereignissen. Timer können eine effizientere Methode zum Auslösen Ihres Codes sein. Erzwingen Sie nicht, dass `OnIdle` wiederholt aufgerufen wird, indem falsche Meldungen generiert werden oder immer `TRUE` von einer Überschreibung von `OnIdle` zurückgegeben wird, wodurch Ihr Thread niemals in den Ruhezustand kommen würde. Auch hier kann ein Timer oder ein separater Thread angemessener sein.

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a> Freigegebene Bibliotheken

Eine Wiederverwendung von Code ist wünschenswert. Wenn Sie jedoch den Code einer anderen Person verwenden, sollten Sie sicherstellen, dass Sie genau wissen, was dieser an den Stellen bewirkt, an denen Leistung für Sie wichtig ist. Diese beste Möglichkeit, um dies zu verstehen, besteht darin, den Quellcode Schritt für Schritt durchzugehen oder mit Tools wie PView oder dem Leistungsmonitor zu messen.

## <a name="heaps"></a><a name="_core_heaps"></a> Heaps

Verwenden Sie mehrere Heaps mit Vorsicht. Mit zusätzlichen mit `HeapCreate` und `HeapAlloc` erstellen Heaps können Sie einen relevanten Satz von Zuordnungen verwalten und dann verwerfen. Sichern Sie nicht zu viel Arbeitsspeicher zu. Wenn Sie mehrere Heaps verwenden, achten Sie besonders auf die Menge des Arbeitsspeichers, der anfangs zugesichert wird.

Anstelle von mehreren Heaps können Sie Hilfsfunktionen verwenden, um eine Schnittstelle zwischen Ihrem Code und dem Standardheap bereitzustellen. Hilfsfunktionen vereinfachen benutzerdefinierte Zuordnungsstrategien, die die Leistung Ihrer Anwendung verbessern können. Wenn Sie beispielsweise oft kleine Zuordnungen durchführen, sollten Sie diese Zuordnungen möglicherweise auf einen Teil des Standardheaps lokalisieren. Sie können einen großen Speicherblock zuordnen und dann eine Hilfsfunktion verwenden, um untergeordnete Zuordnungen von diesem Block durchzuführen. Dann haben Sie keine zusätzlichen Heaps mit ungenutztem Speicher, da die Zuordnung aus dem Standardheap kommt.

In einigen Fällen kann die Verwendung des Standardheaps jedoch die Positionierung von Verweisen reduzieren. Verwenden Sie den Prozess-Viewer, Spy++ oder den Leistungsmonitor, um die Auswirkung der Verschiebung von Objekten von Heap zu Heap zu messen.

Messen Sie Ihre Heaps, damit Sie jede Zuordnung im Heap erklären können. Verwenden Sie die [Debugheaproutinen](/visualstudio/debugger/crt-debug-heap-details) der C-Runtime, um einen Prüfpunkt und eine Sicherung für Ihren Heap festzulegen. Sie können die Ausgabe in ein Tabellenkalkulationsprogramm wie Microsoft Excel lesen und Pivottables verwenden, um die Ergebnisse anzuzeigen. Beachten Sie die Gesamtanzahl, die Größe und die Verteilung der Zuordnungen. Vergleichen Sie diese mit der Größe der Workingsets. Sehen Sie sich auch das Clustering der Objekte verwandter Größe an.

Sie können außerdem die Leistungsindikatoren ansehen, um die Speicherauslastung zu überwachen.

## <a name="threads"></a><a name="_core_threads"></a> Threads

Für Hintergrundaufgaben ist eine effektive Handhabung von Leerläufen möglicherweise schneller als die Verwendung von Threads. Es ist einfacher, die Positionierung von Hinweisen in einem Programm mit einem einzigen Thread zu verstehen.

Eine gute Faustregel ist, einen Thread nur dann zu verwenden, wenn eine Betriebssystembenachrichtigung, die Sie blockiert haben, am Stamm der Hintergrundarbeit liegt. Threads sind in einem solchen Fall die beste Lösung, weil es unpraktisch ist, einen Hauptthread in einem Ereignis zu blockieren.

Threads stellen außerdem Kommunikationsprobleme dar. Sie müssen die Kommunikationsverbindung zwischen Ihren Threads verwalten, mit einer Liste von Meldungen oder indem Sie freigegebenen Speicher zuordnen und verwenden. Für die Verwaltung der Kommunikationsverbindung ist normalerweise eine Synchronisierung erforderlich, um Racebedingungen und Deadlockprobleme zu vermeiden. Diese Komplexität kann leicht zu Fehlern und Leistungsproblemen führen.

Weitere Informationen finden Sie unter [Leerlaufschleifenverarbeitung](../mfc/idle-loop-processing.md) und [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="small-working-set"></a><a name="_core_small_working_set"></a> Kleines Workingset

Kleinere Workingsets bedeuten eine bessere Positionierung von Verweisen, weniger Seitenfehler und mehr Cachetreffer. Die Verarbeitung von Workingsets ist die engste Metrik, die das Betriebssystem direkt für das Messen der Positionierung von Verweisen bereitstellt.

- Zum Festlegen der oberen und unteren Grenzwerte des Workingsets verwenden Sie [SetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize).

- Zum Abrufen der oberen und unteren Grenzwerte des Workingsets verwenden Sie [GetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize).

- Zum Anzeigen der Größe des Workingsets verwenden Sie Spy++.

## <a name="see-also"></a>Siehe auch

[Codeoptimierung](optimizing-your-code.md)
