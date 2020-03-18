---
title: Klassen für Arrays, Listen und Zuordnungen
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [MFC], classes
- list classes [MFC]
- collection classes [MFC], maps
- map classes [MFC]
- collection classes [MFC], lists
ms.assetid: 81a13a7f-0c2c-4efd-b6bb-b4e624a0743d
ms.openlocfilehash: f5fe4acb35074e924555029d715ccbc23b55f49a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446512"
---
# <a name="array-list-and-map-classes"></a>Klassen für Arrays, Listen und Zuordnungen

Zum Verarbeiten von Daten Aggregaten stellt die Klassenbibliothek eine Gruppe von Auflistungs Klassen – Arrays, Listen und Zuordnungen – bereit, die eine Vielzahl von Objekt-und vordefinierten Typen enthalten können. Die Sammlungen werden dynamisch angepasst. Diese Klassen können in jedem Programm verwendet werden, unabhängig davon, ob Sie für Windows geschrieben wurden oder nicht. Sie sind jedoch besonders nützlich für das Implementieren der Datenstrukturen, die Ihre Dokument Klassen im Anwendungs Framework definieren. Sie können problemlos spezialisierte Auflistungs Klassen ableiten, oder Sie können Sie basierend auf den Vorlagen Klassen erstellen. Weitere Informationen zu diesen Ansätzen finden Sie im Artikel [Sammlungen](../mfc/collections.md). Eine Liste der Vorlagen Sammlungs Klassen finden Sie im Artikel [Vorlagen Klassen für Arrays, Listen und](../mfc/template-classes-for-arrays-lists-and-maps.md)Zuordnungen.

Arrays sind eindimensionale Datenstrukturen, die im Arbeitsspeicher zusammenhängend gespeichert werden. Sie unterstützen sehr schnellen Zufalls Zugriff, da die Speicheradresse eines beliebigen Elements berechnet werden kann, indem der Index des Elements mit der Größe eines Elements multipliziert wird und das Ergebnis der Basisadresse des Arrays hinzugefügt wird. Arrays sind jedoch sehr kostspielig, wenn Sie Elemente in das Array einfügen müssen, da das gesamte Array hinter dem eingefügten Element verschoben werden muss, um Platz für das einzufügende Element zu schaffen. Arrays können bei Bedarf vergrößert und verkleinert werden.

Listen ähneln Arrays, werden jedoch sehr unterschiedlich gespeichert. Jedes Element in einer Liste enthält auch einen Zeiger auf das vorherige und das nächste Element, sodass es zu einer doppelt verknüpften Liste wird. Es ist sehr schnell, Elemente hinzuzufügen oder zu löschen, da dadurch nur einige Zeiger geändert werden müssen. Das Durchsuchen einer Liste kann jedoch teuer sein, da alle Suchvorgänge an einer der Listen enden gestartet werden müssen.

Zuordnungen verknüpfen einen Schlüsselwert mit einem Datenwert. Beispielsweise könnte der Schlüssel einer Zuordnung eine Zeichenfolge und die Daten einen Zeiger auf eine Liste sein. Sie würden die Karte bitten, den Zeiger zu erhalten, der einer bestimmten Zeichenfolge zugeordnet ist. Kartenlookups sind schnell, da Maps Hash Tabellen für Schlüssel suchen verwenden. Das Hinzufügen und Löschen von Elementen ist auch schnell. Zuordnungen werden häufig mit anderen Datenstrukturen als hilfsindizes verwendet. MFC verwendet eine besondere Art von Zuordnung, die als [Nachrichten](../mfc/mapping-messages.md) Zuordnung bezeichnet wird, um Windows-Meldungen einem Zeiger auf die Handlerfunktion für diese Nachricht zuzuordnen.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
