---
title: Verschachteln des Hilfemenüs
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: 1bd70af6f24ee6f9873b89b2060f4b2d90149c90
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620132"
---
# <a name="help-menu-merging"></a>Verschachteln des Hilfemenüs

Wenn ein Objekt innerhalb eines Containers aktiv ist, gibt das Kontextmenü für die Zusammenführung von OLE-Dokumenten dem Objekt die gesamte Kontrolle über das Menü **Hilfe** . Folglich sind die Hilfe Themen des Containers nicht verfügbar, es sei denn, der Benutzer deaktiviert das Objekt. Die aktive Dokument Kapselungs Architektur erweitert die Regeln für die direkte Menü Zusammenführung, damit sowohl der Container als auch ein aktives Dokument, das aktiv ist, das Menü gemeinsam verwenden können. Die neuen Regeln sind einfach zusätzliche Konventionen darüber, welche Komponente welchen Teil des Menüs besitzt und wie das freigegebene Menü erstellt wird.

Die neue Konvention ist einfach. In aktiven Dokumenten verfügt das Menü **Hilfe** über zwei Menü Elemente der obersten Ebene, die wie folgt organisiert sind:

`Help`

`Container Help >`

`Object Help    >`

Wenn beispielsweise ein Word-Abschnitt im Office-Binder aktiv ist, wird das Menü " **Hilfe** " wie folgt angezeigt:

`Help`

`Binder Help >`

`Word Help   >`

Beide Menü Elemente sind Kaskadierende Menüs, in denen alle zusätzlichen Menü Elemente, die für den Container und das Objekt spezifisch sind, für den Benutzer bereitgestellt werden. Welche Elemente hier angezeigt werden, hängt vom Container und den beteiligten Objekten ab.

Um dieses zusammengeführte **Hilfe** Menü zu erstellen, ändert die aktive Dokument Kapselungs Architektur die normale OLE-Dokumenten Prozedur. Gemäß OLE-Dokumenten kann die zusammengeführte Menüleiste sechs Gruppen von Menüs enthalten, d. b. **Datei**, **Bearbeiten**, **Container**, **Objekt**, **Fenster**, **Hilfe**, in dieser Reihenfolge. In jeder Gruppe können NULL oder mehr Menüs vorhanden sein. Die Gruppen **Datei**, der **Container**und das **Fenster** gehören zum Container, und die Gruppen **Bearbeiten**, **Objekt** und **Hilfe** gehören zum-Objekt. Wenn das Objekt die Zusammenführung des Menüs durchführen möchte, wird eine leere Menüleiste erstellt und an den Container weitergeleitet. Der Container fügt dann seine Menüs ein, indem er aufgerufen wird `IOleInPlaceFrame::InsertMenus` . Das-Objekt übergibt auch eine-Struktur, bei der es sich um ein Array von sechs Long-Werten (**olemenugroupbreiten**) handelt. Nachdem Sie die Menüs eingefügt haben, markiert der Container, wie viele Menüs in den einzelnen Gruppen hinzugefügt wurden, und gibt dann zurück. Dann fügt das-Objekt seine Menüs ein und achtet auf die Anzahl der Menüs in jeder Containergruppe. Zum Schluss übergibt das Objekt die zusammengeführte Menüleiste und das Array (das die Anzahl der Menüs in jeder Gruppe enthält) an OLE, das ein undurchsichtiges "Menu Descriptor"-handle zurückgibt. Später übergibt das-Objekt das Handle und die zusammengeführte Menüleiste über an den Container `IOleInPlaceFrame::SetMenu` . Zu diesem Zeitpunkt zeigt der Container die zusammengeführte Menüleiste an und übergibt auch das Handle an OLE, damit OLE die ordnungsgemäße Verteilung von Menü Meldungen durchführen kann.

In der geänderten aktiven Dokument Prozedur muss das-Objekt zuerst die **olemenugroupbreiten** -Elemente auf 0 (null) initialisieren, bevor es an den Container übergeben wird. Der Container führt dann eine normale Menü Einfügung mit einer Ausnahme aus: der Container **Help** fügt ein Hilfemenü als letztes Element ein und speichert den Wert 1 im letzten (sechsten) Eintrag des **olemenugroupwidth** -Arrays (d. h. die Breite [5], die zur Hilfe Gruppe des Objekts gehört). Dieses **Hilfemenü** enthält nur ein Element, bei dem es sich um ein Untermenü handelt. das Menü "**Container Help** >", wie zuvor beschrieben.

Das-Objekt führt dann den normalen Menü Einfügungs Code aus, mit dem Unterschied, dass vor dem Einfügen des **Hilfe** Menüs der sechste Eintrag des **olemenugroupbreiten** -Arrays überprüft wird. Wenn der Wert 1 lautet und der Name des letzten Menüs **Hilfe** (oder die entsprechende lokalisierte Zeichenfolge) ist, fügt das-Objekt das **Hilfemenü** als Untermenü des **Hilfe** Menüs des Containers ein.

Das-Objekt legt dann das sechste Element von **olemenugroupbreiten** auf NULL fest und erhöht das fünfte Element um eins. Dadurch weiß OLE, dass das Menü **Hilfe** zum Container gehört, und die Menü Meldungen, die dem Menü (und den zugehörigen Untermenüs) entsprechen, sollten an den Container weitergeleitet werden. Der Container ist dann dafür verantwortlich, **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**und andere Menü bezogene Meldungen weiterzuleiten, die zum Teil des Objekts im Menü **Hilfe** gehören. Dies erfolgt mithilfe **WM_INITMENU** , um ein Flag zu löschen, das dem Container mitteilt, ob der Benutzer zum **Hilfe** Menü des Objekts navigiert ist. Der Container überwacht dann **WM_MENUSELECT** , ob ein beliebiges Element im Hilfemenü ein-oder **austreten** wird, das der Container nicht selbst hinzugefügt hat. Beim Einstieg bedeutet dies, dass der Benutzer in ein Objektmenü navigiert ist, sodass der Container das Flag "im Objekt-Hilfe Menü" festlegt und den Status dieses Flags verwendet, um alle **WM_MENUSELECT**, **WM_INITMENUPOPUP**und **WM_COMMAND** Meldungen als minimal an das Objekt Fenster weiterzuleiten. (Beim Beenden löscht der Container das Flag und verarbeitet dann die gleichen Nachrichten selbst.) Der Container sollte das Fenster verwenden, das von der Funktion des-Objekts `IOleInPlaceActiveObejct::GetWindow` als Ziel für diese Nachrichten zurückgegeben wird.

Wenn das Objekt im sechsten Element von **olemenugroupbreiten**eine NULL-Werte erkennt, wird es gemäß den normalen OLE-Dokumenten Regeln fortgesetzt. Dieses Verfahren behandelt Container, die an der Zusammenführung des **Hilfe** Menüs beteiligt sind, ebenso wie die, die dies nicht tun.

Wenn vom-Objekt aufgerufen wird `IOleInPlaceFrame::SetMenu` , überprüft der Container, bevor die zusammengeführte Menüleiste angezeigt wird, ob das **Hilfemenü** neben dem Inhalt des Containers ein zusätzliches Untermenü enthält. Wenn dies der Fall ist, verlässt der Container das Menü " **Hilfe** " in der zusammengeführten Menüleiste. Wenn das **Hilfemenü** nicht über ein zusätzliches Untermenü verfügt, entfernt der Container das zugehörige **Hilfemenü** von der zusammengeführten Menüleiste. Dieses Verfahren behandelt Objekte, die an der Zusammenführung des **Hilfe** Menüs beteiligt sind, sowie die Objekte, die dies nicht tun.

Wenn es zum schlusszeit ist, das Menü zu disassemblieren, entfernt das-Objekt zusätzlich zum Entfernen der anderen eingefügten Menüs das eingefügte **Hilfe** Menü. Wenn der Container seine Menüs entfernt, entfernt er zusätzlich zu **Help** den anderen Menüs, die er eingefügt hat, sein Hilfemenü.

## <a name="see-also"></a>Siehe auch

[Aktive Dokumente-Container](active-document-containers.md)
