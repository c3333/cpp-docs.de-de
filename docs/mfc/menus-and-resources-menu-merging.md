---
title: 'Menüs und Ressourcen: Menüs schachteln'
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: 03d27443f90634b5d787eee25acc951d24178f42
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626222"
---
# <a name="menus-and-resources-menu-merging"></a>Menüs und Ressourcen: Menüs schachteln

In diesem Artikel werden die Schritte erläutert, die für OLE-Dokument Anwendungen erforderlich sind, um die visuelle Bearbeitung und die direkte Aktivierung ordnungsgemäß auszuführen. Die direkte Aktivierung stellt eine Herausforderung für Container-und Server Anwendungen (Component) dar. Der Benutzer verbleibt im gleichen Rahmen Fenster (im Kontext des Container Dokuments), führt aber tatsächlich eine andere Anwendung (der Server) aus. Dies erfordert eine Koordination zwischen den Ressourcen der Container-und Server Anwendungen.

Zu den in diesem Artikel behandelten Themen gehören:

- [Menü Layouts](#_core_menu_layouts)

- [Symbolleisten und Status leisten](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Menü Layouts

Der erste Schritt besteht darin, Menü Layouts zu koordinieren. Container Anwendungen sollten ein neues Menü erstellen, das nur verwendet wird, wenn eingebettete Elemente an Ort und Stelle aktiviert werden. Dieses Menü sollte mindestens aus folgendem in der aufgeführten Reihenfolge bestehen:

1. Das Dateimenü ist identisch mit dem Menü, das beim Öffnen von Dateien verwendet wird. (In der Regel werden keine anderen Menü Elemente vor dem nächsten Element platziert.)

1. Zwei aufeinander folgende Trennzeichen.

1. Fenstermenü, das mit dem beim Öffnen von Dateien verwendeten identisch ist (nur bei der Containeranwendung in einer MDI-Anwendung). Einige Anwendungen haben möglicherweise andere Menüs, z. b. ein Options Menü, das zu dieser Gruppe gehört, die im Menü bleibt, wenn ein eingebettetes Element an Ort und Stelle aktiviert wird.

    > [!NOTE]
    >  Möglicherweise gibt es andere Menüs, die sich auf die Ansicht des Container Dokuments auswirken, z. b. Zoom. Diese Container Menüs werden zwischen den beiden Trennzeichen in dieser Menü Ressource angezeigt.

Server-(Komponenten-) Anwendungen sollten auch ein neues Menü speziell für die direkte Aktivierung erstellen. Dies sollte dem Menü entsprechen, das verwendet wird, wenn Dateien geöffnet sind, jedoch ohne Menü Elemente, wie z. b. Datei und Fenster, die das Server Dokument anstelle der Daten bearbeiten. In der Regel besteht dieses Menü aus folgendem:

1. Menü Bearbeiten, das mit dem Menü identisch ist, das beim Öffnen von Dateien verwendet wird.

1. Trennzeichen.

1. Objekt Bearbeitungs Menüs, z. b. das Stift Menü in der Scribble-Beispielanwendung.

1. Trennzeichen.

1. Hilfemenü.

Ein Beispiel finden Sie im Layout einiger Beispiele für direkte Menüs für einen Container und einen Server. Die Details der einzelnen Menü Elemente wurden entfernt, um das Beispiel übersichtlicher zu machen. Das direkte Menü des Containers enthält die folgenden Einträge:

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

Die aufeinander folgenden Trennzeichen geben an, wo der erste Teil des Server Menüs angezeigt werden soll. Sehen Sie sich jetzt das direkte Menü des Servers an:

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

Die Trennzeichen geben hier an, wo die zweite Gruppe von Container Menü Elementen wechseln soll. Die resultierende Menüstruktur, wenn ein Objekt von diesem Server innerhalb dieses Containers aktiviert ist, sieht wie folgt aus:

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

Wie Sie sehen können, wurden die Trennzeichen durch die verschiedenen Gruppen der einzelnen Anwendungs Menüs ersetzt.

Zugriffstasten Tabellen, die dem direkten Menü zugeordnet sind, sollten auch von der Serveranwendung bereitgestellt werden. Der Container integriert Sie in seine eigenen Zugriffstasten Tabellen.

Wenn ein eingebettetes Element an Ort und Stelle aktiviert wird, lädt das Framework das direkte Menü. Anschließend wird die Serveranwendung nach dem Menü für die direkte Aktivierung aufgefordert, und die Trennzeichen werden eingefügt. Auf diese Weise werden die Menüs kombiniert. Sie erhalten Menüs aus dem Container für die Betriebssystem-und Fensterplatzierung, und Sie erhalten Menüs vom Server für den Betrieb auf dem Element.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Symbolleisten und Status leisten

Server Anwendungen sollten eine neue Symbolleiste erstellen und die Bitmap in einer separaten Datei speichern. Die von dem Anwendungs-Assistenten generierten Anwendungen speichern diese Bitmap in einer Datei namens "IToolbar". BMP. Die neue Symbolleiste ersetzt die Symbolleiste der Containeranwendung, wenn das Element des Servers an Ort und Stelle aktiviert ist, und sollte dieselben Elemente wie die normale Symbolleiste enthalten, aber Symbole entfernen, die Elemente in den Menüs "Datei" und "Fenster" darstellen.

Diese Symbolleiste wird in `COleIPFrameWnd` der von abgeleiteten Klasse geladen, die Sie vom Anwendungs-Assistenten für Sie erstellt haben. Die Statusleiste wird von der Containeranwendung behandelt. Weitere Informationen zur Implementierung von direkten Rahmen Fenstern finden Sie unter [Server: Implementieren eines Servers](servers-implementing-a-server.md).

## <a name="see-also"></a>Siehe auch

[Menüs und Ressourcen (OLE)](menus-and-resources-ole.md)<br/>
[Aktivierung](activation-cpp.md)<br/>
[Server](servers.md)<br/>
[Container](containers.md)
