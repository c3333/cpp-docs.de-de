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
ms.openlocfilehash: 149af83bd53b7a97fd264bd6b18701fc9f64ea1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364769"
---
# <a name="menus-and-resources-menu-merging"></a>Menüs und Ressourcen: Menüs schachteln

In diesem Artikel werden die Schritte beschrieben, die für OLE-Dokumentanwendungen erforderlich sind, um die visuelle Bearbeitung und die ortsspezifische Aktivierung ordnungsgemäß zu handhaben. Die ortsspezifische Aktivierung stellt sowohl für Container- als auch für Serveranwendungen (Komponenten) eine Herausforderung dar. Der Benutzer verbleibt im gleichen Rahmenfenster (im Kontext des Containerdokuments), führt aber tatsächlich eine andere Anwendung (den Server) aus. Dies erfordert eine Koordination zwischen den Ressourcen der Container- und Serveranwendungen.

Zu den in diesem Artikel behandelten Themen gehören:

- [Menülayouts](#_core_menu_layouts)

- [Symbolleisten und Statusleisten](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a>Menülayouts

Der erste Schritt besteht darin, Menülayouts zu koordinieren. Containeranwendungen sollten ein neues Menü erstellen, das nur verwendet werden kann, wenn eingebettete Elemente aktiviert sind. Zumindest sollte dieses Menü aus der folgenden, in der angegebenen Reihenfolge bestehen:

1. Dateimenü identisch mit dem, das verwendet wird, wenn Dateien geöffnet sind. (Normalerweise werden keine anderen Menüelemente vor dem nächsten Element platziert.)

1. Zwei aufeinander folgende Trennzeichen.

1. Fenstermenü identisch mit dem, das beim Öffnen von Dateien verwendet wird (nur, wenn die Containeranwendung in einer MDI-Anwendung verwendet wird). Einige Anwendungen verfügen möglicherweise über andere Menüs, z. B. ein Optionsmenü, das zu dieser Gruppe gehört und im Menü verbleibt, wenn ein eingebettetes Element aktiviert wird.

    > [!NOTE]
    >  Es können andere Menüs vorhanden sein, die sich auf die Ansicht des Containerdokuments auswirken, z. B. Zoom. Diese Containermenüs werden zwischen den beiden Trennzeichen in dieser Menüressource angezeigt.

Serveranwendungen (Komponentenanwendungen) sollten auch ein neues Menü speziell für die Ortsaktivierung erstellen. Es sollte wie das Menü verwendet werden, wenn Dateien geöffnet sind, aber ohne Menüelemente, wie Datei und Fenster, die das Serverdokument anstelle der Daten bearbeiten. In der Regel besteht dieses Menü aus den folgenden:

1. Bearbeiten Sie das Menü, das mit dem Menü identisch ist, das beim Öffnen von Dateien verwendet wird.

1. Trennzeichen.

1. Objektbearbeitungsmenüs, z. B. das Pen-Menü in der Scribble-Beispielanwendung.

1. Trennzeichen.

1. Hilfemenü.

Sehen Sie sich z. B. das Layout einiger ortsseitigen Beispielmenüs für einen Container und einen Server an. Die Details der einzelnen Menüelemente wurden entfernt, um das Beispiel klarer zu machen. Das ortsbezogene Menü des Containers enthält die folgenden Einträge:

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

Die aufeinander folgenden Trennzeichen geben an, wohin der erste Teil des Servermenüs gehen soll. Sehen Sie sich nun das ortsbezogene Menü des Servers an:

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

Die Trennzeichen hier geben an, wohin die zweite Gruppe von Containermenüelementen gehen soll. Die resultierende Menüstruktur, wenn ein Objekt von diesem Server innerhalb dieses Containers aktiviert wird, sieht wie folgt aus:

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

Wie Sie sehen können, wurden die Trennzeichen durch die verschiedenen Gruppen des Menüs jeder Anwendung ersetzt.

Beschleunigertabellen, die dem ortsseitigen Menü zugeordnet sind, sollten ebenfalls von der Serveranwendung bereitgestellt werden. Der Container wird sie in seine eigenen Beschleunigertabellen integrieren.

Wenn ein eingebettetes Element aktiviert ist, lädt das Framework das In-Place-Menü. Anschließend wird die Serveranwendung nach ihrem Menü zur ortsseitigen Aktivierung gefragt und dort eingefügt, wo sich die Trennzeichen befinden. So kombinieren sich die Menüs. Sie erhalten Menüs aus dem Container für den Betrieb auf der Datei- und Fensterplatzierung, und Sie erhalten Menüs vom Server für den Betrieb des Elements.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a>Symbolleisten und Statusleisten

Serveranwendungen sollten eine neue Symbolleiste erstellen und ihre Bitmap in einer separaten Datei speichern. Die vom Anwendungsassistenten generierten Anwendungen speichern diese Bitmap in einer Datei namens ITOOLBAR. Bmp. Die neue Symbolleiste ersetzt die Symbolleiste der Containeranwendung, wenn das Element des Servers aktiviert ist, und sollte dieselben Elemente wie die normale Symbolleiste enthalten, aber Symbole entfernen, die Elemente in den Menüs Datei und Fenster darstellen.

Diese Symbolleiste wird `COleIPFrameWnd`in Ihre -derived-Klasse geladen, die vom Anwendungsassistenten für Sie erstellt wurde. Die Statusleiste wird von der Containeranwendung behandelt. Weitere Informationen zur Implementierung von ortsseitigen Rahmenfenstern finden Sie unter [Server: Implementieren eines Servers](../mfc/servers-implementing-a-server.md).

## <a name="see-also"></a>Siehe auch

[Menüs und Ressourcen (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Aktivierung](../mfc/activation-cpp.md)<br/>
[Server](../mfc/servers.md)<br/>
[Container](../mfc/containers.md)
