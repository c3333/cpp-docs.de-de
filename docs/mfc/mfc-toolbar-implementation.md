---
title: Implementieren der MFC-Symbolleiste
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 7876e9403389c19a24e5a482534d0f223eaa4bf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626114"
---
# <a name="mfc-toolbar-implementation"></a>Implementieren der MFC-Symbolleiste

Eine Symbolleiste ist eine [Steuerleiste](control-bars.md) , die die Bitmap-Bilder der Steuerelemente enthält. Diese Bilder können sich wie Druckknöpfe, Kontrollkästchen oder Optionsfelder verhalten. MFC stellt die Klasse [CToolBar](reference/ctoolbar-class.md) zum Verwalten von Symbolleisten bereit.

Wenn Sie sie aktivieren, können Benutzer von MFC-Symbolleisten diese an den Rand eines Fensters andocken, oder an einer beliebigen Stelle im Anwendungsfenster "abdocken". MFC unterstützt keine anpassbaren Symbolleisten wie in der Entwicklungsumgebung.

MFC unterstützt auch QuickInfos: kleine Popupfenster, in denen der Zweck einer Symbolleistenschaltfläche beschrieben wird, wenn Sie die Maus über die Schaltfläche positionieren. Wenn der Benutzer eine Symbolleisten-Schaltfläche drückt, wird standardmäßig eine Statuszeichenfolge in der Statusleiste (falls vorhanden) angezeigt. Sie können die Aktualisierung der "aufleuchtenden" Statusleiste aktivieren, damit die Statuszeichenfolge angezeigt wird, wenn die Maus über die Schaltfläche positioniert wird, ohne dass sie gedrückt wird.

> [!NOTE]
> Ab MFC 4.0 werden Symbolleisten und QuickInfo mit der Funktionalität von Windows 95 und höher anstelle der vorherigen, MFC-spezifischen Implementierung implementiert.

Aus Gründen der Abwärtskompatibilität behält MFC die ältere Symbolleisten Implementierung in der-Klasse bei `COldToolBar` . In der Dokumentation für frühere Versionen von MFC wird `COldToolBar` unter beschrieben `CToolBar` .

Erstellen Sie die erste Symbolleiste im Programm, indem Sie die Symbolleistenoption im Anwendungs-Assistenten auswählen. Sie können auch weitere Symbolleisten erstellen.

Die folgenden werden in diesem Artikel eingeführt:

- [Schaltflächen](#_core_toolbar_buttons)

- [Andockbare und Gleit Komma Symbolleisten](#_core_docking_and_floating_toolbars)

- [Symbolleisten und QuickInfo](#_core_toolbars_and_tool_tips)

- [Die Klassen CToolBar und CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Die Symbolleisten-Bitmap](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>Schaltflächen

Die Schaltflächen in einer Symbolleiste sind den Elementen in einem Menü analog. Beide Arten von Benutzeroberflächen-Objekten generieren Befehle, die das Programm bearbeitet, indem es Handlerfunktionen bereitstellt. Häufig duplizieren Symbolleisten-Schaltflächen die Funktionalität von Menübefehlen und stellen eine alternative Benutzeroberfläche mit derselben Funktionalität bereit. Solche Duplizierung wird einfach angeordnet, indem die Schaltfläche und das Menüelement die gleiche ID erhalten.

Sie können die Schaltflächen in einer Symbolleiste so erstellen, dass sie als Druckknöpfe, Kontrollkästchen oder Optionsfelder angezeigt werden und sich entsprechend verhalten. Weitere Informationen finden Sie unter Class [CToolBar](reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>Andockbare und Gleit Komma Symbolleisten

Eine MFC-Symbolleiste kann:

- fest entlang der Seite des übergeordneten Fensters geöffnet stehen.

- vom Benutzer gezogen und an einer oder mehreren Seiten des von Ihnen angegebenen übergeordneten Fensters "angedockt" oder angefügt werden.

- vom Rahmenfenster "abgedockt" oder gelöst werden und im eigenen kleinen Rahmenfenster angezeigt werden, sodass der Benutzer es an eine beliebige Position verschieben kann.

- im unverankerten Modus in der Größe verändert werden.

Weitere Informationen finden Sie im Artikel [Andocken und](docking-and-floating-toolbars.md)Unverankerte Symbolleisten.

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>Symbolleisten und Quick Infos

MFC-Symbolleisten können als "QuickInfo" angezeigt werden. Hierbei handelt es sich um kleine Fenster, die eine Kurztextbeschreibung mit dem Zweck einer Symbolleisten-Schaltfläche enthalten. Wenn der Benutzer die Maus über eine Symbolleisten-Schaltfläche bewegt, bieten die Popupfenster mit den QuickInfos einen Hinweis an. Weitere Informationen finden Sie im Artikel [Symbol](toolbar-tool-tips.md)leisten Quick Infos.

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Die Klassen CToolBar und CToolBarCtrl

Sie verwalten die Symbolleisten Ihrer Anwendung über die [CToolBar](reference/ctoolbar-class.md)-Klasse. Ab MFC 4.0 ist `CToolBar` erneut implementiert, sodass das allgemeine Steuerelement für Symbolleisten verwendet werden kann, das unter Windows 95 oder höher und Windows NT 3.51 oder höher verfügbar ist.

Diese Neuimplementierung führt zu weniger MFC-Code in Symbolleisten, da MFC die Betriebssystemunterstützung ausnutzt. Das Neuimplementierung verbessert auch die Funktionalität. Sie können Element `CToolBar` Funktionen zum Bearbeiten von Symbolleisten verwenden, oder Sie können einen Verweis auf das zugrunde liegende [CToolBarCtrl](reference/ctoolbarctrl-class.md) -Objekt abrufen und seine Member-Funktionen für die Symbolleisten Anpassung und zusätzliche Funktionen aufzurufen.

> [!TIP]
> Wenn Sie in die ältere MFC-Implementierung von `CToolBar` investiert haben, ist diese Unterstützung weiterhin verfügbar. Weitere Informationen finden Sie im Artikel [Verwenden der alten Symbolleisten](using-your-old-toolbars.md).

Siehe auch das allgemeine MFC-Beispiel [DOCKTOOL](../overview/visual-cpp-samples.md).

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>Die Symbolleisten-Bitmap

Ein erstelltes `CToolBar`-Objekt erstellt das Symbolleistenbild, indem es eine einzelne Bitmap lädt, das ein Bild für jede Schaltfläche enthält. Der Anwendungs-Assistent erstellt eine Standard-Symbolleisten-Bitmap, die Sie mit dem Visual C++ Symbolleisten- [Editor](../windows/toolbar-editor.md)anpassen können.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Grundlagen zu Toolbar](toolbar-fundamentals.md)

- [Andockbare und Gleit Komma Symbolleisten](docking-and-floating-toolbars.md)

- [QuickInfos für die Symbolleiste](toolbar-tool-tips.md)

- [Arbeiten mit dem ToolBar-Steuerelement](working-with-the-toolbar-control.md)

- [Verwenden der bisherigen Symbolleisten](using-your-old-toolbars.md)

- Die Klassen [CToolBar](reference/ctoolbar-class.md) und [CToolBarCtrl](reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Siehe auch

[Symbolleisten](toolbars.md)<br/>
[Symbolleisten-Editor](../windows/toolbar-editor.md)
