---
title: Grundlagen zu HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 6d3a692eab47a1309ee0248b51ab8563fb077d5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377245"
---
# <a name="html-basics"></a>Grundlagen zu HTML

Die meisten Browser können die HTML-Quelle der seiten untersuchen, die Sie durchsuchen. Wenn Sie die Quelle anzeigen, sehen Sie eine Reihe von HTML-Tags (Hypertext Markup Language), umgeben von spitzen Klammern (<>), die mit Text durchsetzt sind.

In den folgenden Schritten werden HTML-Tags verwendet, um eine einfache Webseite zu erstellen. In diesen Schritten geben Sie Nur-Text in eine Datei in Notepad ein, nehmen einige Änderungen vor, speichern die Datei und laden die Seite im Browser neu, um die Änderungen anzuzeigen.

#### <a name="to-create-an-html-file"></a>So erstellen Sie eine HTML-Datei

1. Öffnen Sie Notepad oder einen beliebigen Klartext-Editor.

1. Wählen Sie im Menü **Datei** **Neue**aus.

1. Geben Sie die folgenden Zeilen ein:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Wählen Sie im Menü **Datei** die Option **Speichern**aus, und speichern Sie die Datei als c:-webpages-First.htm. Lassen Sie die Datei im Editor geöffnet.

1. Wechseln Sie zu Ihrem Browser, und wählen Sie im Menü **Datei** die Option **Öffnen**aus, oder geben Sie *file://C:/webpages/first.htm* in das URL-Bearbeitungsfeld des Browsers ein. Es sollte eine leere Seite mit der Fensterbeschriftung "Top HTML Tags" angezeigt werden.

   Beachten Sie, dass die Tags gekoppelt sind und in spitzen Klammern enthalten sind. Tags werden nicht für die Groß-/Kleinschreibung verwendet, aber die Großschreibung wird häufig verwendet, um Tags hervorstechen zu lassen.

   Das \<Tag-HTML-> startet das \<Dokument, und das Tag /HTML-> beendet es. Ending-Tags (nicht immer erforderlich) sind identisch mit dem Start-Tag, haben jedoch einen Schrägstrich (/) vor dem Tag. Zwischen der spitzen Halterung (<) und dem Anfang des Tags sollten keine Leerzeichen vorhanden sein.

1. Wechseln Sie zurück zu Notepad, und geben Sie nach der \<Zeile /HEAD>:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Wählen Sie im Menü **Datei** die Option **Speichern**aus.

1. Wechseln Sie zurück zu Ihrem Browser und aktualisieren Sie die Seite.

   Die Wörter werden im Clientbereich des Browserfensters angezeigt. Beachten Sie, dass Ihr Wagenrücklauf ignoriert wird. Wenn Sie einen Zeilenumbruch haben möchten, müssen Sie ein `<BR>` Tag nach der ersten Zeile einschließen.

   Fügen Sie bei allen folgenden Schritten \<den Text \<irgendwo zwischen BODY> und /BODY> ein, die dem Textkörper des Dokuments hinzugefügt werden sollen.

1. Hinzufügen einer Kopfzeile:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Fügen Sie ein Bild hinzu, indem Sie eine GIF-Datei verwenden, die im selben Verzeichnis wie Ihre Seite gespeichert ist:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Hinzufügen einer Liste:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Um stattdessen die Liste \<zu nummeriert, verwenden Sie die tags \<"> UL>" und "/UL>"> gekoppelte OL->- und \</OL-tags. \<

Das sollte Einen anfange. Wenn auf einer Webseite ein großartiges Feature angezeigt wird, können Sie herausfinden, wie es erstellt wurde, indem Sie die HTML-Quelle untersuchen. HTML-Editoren wie Microsoft Front Page können verwendet werden, um sowohl einfache als auch erweiterte Seiten zu erstellen.

Hier ist die gesamte HTML-Quelle für die Datei, die Sie erstellt haben:

```html
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Eine vollständige Beschreibung von Tags, Attributen und Erweiterungen finden Sie in der HTML-Spezifikation (Hypertext Markup Language):

[Neueste veröffentlichte Version von HTML](https://www.w3.org/TR/html/) bei W3C.org.

## <a name="see-also"></a>Siehe auch

[Grundlagen der MFC-Internetprogrammierung](../mfc/mfc-internet-programming-basics.md)
