---
title: Grundlagen zu HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 29ca2e3df4981db22a10281ba2a2938fc91d5b46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620002"
---
# <a name="html-basics"></a>Grundlagen zu HTML

Die meisten Browser können die HTML-Quelle der Seiten untersuchen, die Sie durchsuchen. Wenn Sie die Quelle anzeigen, sehen Sie eine Reihe von HTML-Tags (Hypertext Markup Language), die von spitzen Klammern (<>) umgeben sind und mit Text vermischt werden.

In den folgenden Schritten werden HTML-Tags zum Erstellen einer einfachen Webseite verwendet. In diesen Schritten geben Sie nur-Text in eine Datei in Editor ein, nehmen einige Änderungen vor, speichern die Datei und laden die Seite im Browser erneut, um Ihre Änderungen anzuzeigen.

#### <a name="to-create-an-html-file"></a>So erstellen Sie eine HTML-Datei

1. Öffnen Sie Editor oder einen beliebigen nur-Text-Editor.

1. Wählen Sie im Menü **Datei** die Option **neu**aus.

1. Geben Sie die folgenden Zeilen ein:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. Wählen Sie im Menü **Datei** die Option **Speichern**aus, und speichern Sie die Datei unter c:\webpaar\first.htm. Lassen Sie die Datei im Editor geöffnet.

1. Wechseln Sie zu Ihrem Browser, und wählen Sie im Menü **Datei** die Option **Öffnen**aus, oder geben Sie *file://C:/Webpages/First.htm* in das Bearbeitungsfeld URL des Browsers ein. Es sollte eine leere Seite mit der Fenster Beschriftung "Top HTML Tags" angezeigt werden.

   Beachten Sie, dass die Tags gekoppelt sind und in spitzen Klammern eingeschlossen werden. Bei Tags wird die Groß-/Kleinschreibung nicht beachtet, aber die Groß-/Kleinschreibung wird häufig verwendet, um Tags

   Das \<HTML> -Tag startet das Dokument, und das Tag \</HTML> endet es. Endtags (nicht immer erforderlich) sind identisch mit dem Starttag, haben jedoch vor dem Tag einen Schrägstrich (/). Zwischen der Spitze Klammer (<) und dem Anfang des Tags dürfen keine Leerzeichen stehen.

1. Wechseln Sie zurück zu Notepad, und geben Sie nach der Zeile Folgendes ein \</HEAD> :

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. Wählen Sie im Menü **Datei** die Option **Speichern**aus.

1. Wechseln Sie zurück zu Ihrem Browser, und aktualisieren Sie die Seite.

   Die Wörter werden im Client Bereich des Browserfensters angezeigt. Beachten Sie, dass das Wagen Rücklauf Zeichen ignoriert wird. Wenn Sie einen Zeilenumbruch durchsetzen möchten, müssen Sie `<BR>` nach der ersten Zeile ein Tag einschließen.

   Fügen Sie für alle nachfolgenden Schritte den Text an einer beliebigen \<BODY> Stelle zwischen und ein, \</BODY> um den Text des Dokuments hinzuzufügen.

1. Fügen Sie einen Header hinzu:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Fügen Sie ein Bild hinzu, indem Sie eine GIF-Datei verwenden, die im gleichen Verzeichnis wie die Seite gespeichert ist:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Fügen Sie eine Liste hinzu:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Um die Liste stattdessen zu zählen, verwenden Sie die gekoppelten \<OL> Tags und anstelle der \</OL> \<UL> \</UL> Tags und.

Das sollte Ihnen den Einstieg erleichtern. Wenn eine gute Funktion auf einer Webseite angezeigt wird, können Sie ermitteln, wie Sie erstellt wurde, indem Sie die HTML-Quelle untersuchen. Mit HTML-Editoren wie Microsoft-Front Page können sowohl einfache als auch erweiterte Seiten erstellt werden.

Hier ist die gesamte HTML-Quelle für die Datei, die Sie gerade aufgebaut haben:

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

Eine umfassende Beschreibung der Tags, Attribute und Erweiterungen finden Sie in der Hypertext Markup Language (HTML)-Spezifikation:

[Neueste veröffentlichte Version von HTML](https://www.w3.org/TR/html/) unter W3C.org.

## <a name="see-also"></a>Siehe auch

[Grundlagen der MFC-Internetprogrammierung](mfc-internet-programming-basics.md)
