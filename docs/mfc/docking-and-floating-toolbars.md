---
title: Andockbare und unverankerte Symbolleisten
ms.date: 11/04/2016
f1_keywords:
- CBRS_SIZE_DYNAMIC
- CBRS_SIZE_FIXED
helpviewer_keywords:
- size [MFC], toolbars
- size
- frame windows [MFC], toolbar docking
- CBRS_ALIGN_ANY constant [MFC]
- palettes, floating
- toolbars [MFC], docking
- CBRS_SIZE_DYNAMIC constant [MFC]
- floating toolbars
- toolbars [MFC], size
- toolbars [MFC], floating
- fixed-size toolbars
- CBRS_SIZE_FIXED constant [MFC]
- toolbar controls [MFC], wrapping
- toolbars [MFC], wrapping
- floating palettes
ms.assetid: b7f9f9d4-f629-47d2-a3c4-2b33fa6b51e4
ms.openlocfilehash: f40d8860f2e514bf3c9e9364a664326250c9627a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615839"
---
# <a name="docking-and-floating-toolbars"></a>Andockbare und unverankerte Symbolleisten

Der Microsoft Foundation Class-Bibliothek unterstützt andockbare Symbolleisten. Eine andockbare Symbolleiste kann an eine beliebige Seite ihres übergeordneten Fensters angefügt oder angedockt werden, oder Sie kann in einem eigenen Mini Rahmen Fenster getrennt bzw. in einem anderen Fenster angezeigt werden. In diesem Artikel wird erläutert, wie Sie andockbare Symbolleisten in Ihren Anwendungen verwenden.

Wenn Sie den Anwendungs-Assistenten verwenden, um das Gerüst Ihrer Anwendung zu generieren, werden Sie aufgefordert, auszuwählen, ob Sie andockbare Symbolleisten verwenden möchten. Standardmäßig generiert der Anwendungs-Assistent den Code, der die drei Aktionen ausführt, die erforderlich sind, um eine andockbare Symbolleiste in Ihrer Anwendung zu platzieren:

- [Andocken in einem Rahmen Fenster aktivieren](#_core_enabling_docking_in_a_frame_window).

- [Andocken für eine Symbolleiste aktivieren](#_core_enabling_docking_for_a_toolbar).

- [Andocken der Symbolleiste (im Rahmen Fenster)](#_core_docking_the_toolbar).

Wenn einer dieser Schritte fehlt, wird in der Anwendung eine Standard Symbolleiste angezeigt. Die letzten beiden Schritte müssen für jede andockbare Symbolleiste in Ihrer Anwendung ausgeführt werden.

Weitere Themen, die in diesem Artikel behandelt werden, sind:

- [Unverankerte Symbolleiste](#_core_floating_the_toolbar)

- [Dynamisches Ändern der Größe der Symbolleiste](#_core_dynamically_resizing_the_toolbar)

- [Festlegen der Umbruch Positionen für eine Symbolleiste im festgelegten Stil](#_core_setting_wrap_positions_for_a_fixed_style_toolbar)

Beispiele hierzu finden Sie unter MFC-Beispiel für allgemeine [DOCKTOOL](../overview/visual-cpp-samples.md) .

## <a name="enabling-docking-in-a-frame-window"></a><a name="_core_enabling_docking_in_a_frame_window"></a>Aktivieren von Docking in einem Rahmen Fenster

Zum Andocken von Symbolleisten in einem Rahmen Fenster muss das Rahmen Fenster (oder das Ziel) aktiviert sein, damit das Andocken zugelassen wird. Dies erfolgt mithilfe der [CFrameWnd:: EnableDocking](reference/cframewnd-class.md#enabledocking) -Funktion, die einen *DWORD* -Parameter annimmt, bei dem es sich um einen Satz von stilbits handelt, der angibt, welche Seite des Rahmen Fensters andocken akzeptiert. Wenn eine Symbolleiste angedockt wird und mehrere Seiten angedockt werden können, werden die Seiten, die in dem an übergebenen Parameter angegeben sind, `EnableDocking` in der folgenden Reihenfolge verwendet: oben, unten, Links, rechts. Wenn Sie Steuerungs leisten an einem beliebigen Ort andocken möchten, übergeben Sie **CBRS_ALIGN_ANY** an `EnableDocking` .

## <a name="enabling-docking-for-a-toolbar"></a><a name="_core_enabling_docking_for_a_toolbar"></a>Aktivieren von Docking für eine Symbolleiste

Nachdem Sie das Ziel für das Andocken vorbereitet haben, müssen Sie die Symbolleiste (oder Quelle) auf ähnliche Weise vorbereiten. [CControlBar:: EnableDocking](reference/ccontrolbar-class.md#enabledocking) für jede Symbolleiste, die Sie andocken möchten, und die Zielseiten angeben, an denen die Symbolleiste Andocken soll. Wenn keine der im-Befehl angegebenen Seiten `CControlBar::EnableDocking` den Seiten entspricht, die für das Andocken im Rahmen Fenster aktiviert sind, kann die Symbolleiste nicht Andocken – Sie wird float. Nachdem der Vorgang abgeschlossen wurde, bleibt er eine unverankerte Symbolleiste, die nicht an das Rahmen Fenster angedockt werden kann.

Wenn der gewünschte Effekt eine dauerhaft unverankerte Symbolleiste ist, können Sie `EnableDocking` mit dem Parameter 0 aufrufen. Anschließend wird [CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar)aufgerufen. Die Symbolleiste bleibt unverankert, Sie kann dauerhaft nicht andocken.

## <a name="docking-the-toolbar"></a><a name="_core_docking_the_toolbar"></a>Andocken der Toolbar

Das Framework ruft [CFrameWnd::D ockcontrolbar](reference/cframewnd-class.md#dockcontrolbar) auf, wenn der Benutzer versucht, die Symbolleiste auf einer Seite des Rahmen Fensters abzulegen, das Andocken zulässt.

Außerdem können Sie diese Funktion jederzeit zum Andocken von Steuer leisten an das Rahmen Fenster aufzurufen. Dies erfolgt normalerweise während der Initialisierung. Mehr als eine Symbolleiste kann an eine bestimmte Seite des Rahmen Fensters angedockt werden.

## <a name="floating-the-toolbar"></a><a name="_core_floating_the_toolbar"></a>Unverankerte Symbolleiste

Das Trennen einer andockbaren Symbolleiste über das Rahmen Fenster wird als unverankert der Symbolleiste bezeichnet. Nennen Sie hierfür [CFrameWnd:: FloatControlBar](reference/cframewnd-class.md#floatcontrolbar) . Geben Sie die zu verwendende Symbolleiste, den Punkt, an dem Sie platziert werden soll, und einen Ausrichtungs Stil an, der bestimmt, ob die Gleit Komma Symbolleiste horizontal oder vertikal ist.

Das Framework ruft diese Funktion auf, wenn ein Benutzer eine Symbolleiste von der angedockten Position zieht und Sie an einer Position ablegt, an der das Andocken nicht aktiviert ist. Dies kann sich innerhalb oder außerhalb des Rahmen Fensters befinden. Wie bei `DockControlBar` können Sie diese Funktion auch während der Initialisierung aufzurufen.

Die MFC-Implementierung von andockbaren Symbolleisten bietet nicht einige der erweiterten Features, die in einigen Anwendungen gefunden werden, die andockbare Symbolleisten unterstützen. Funktionen wie z. b. anpassbare Symbolleisten werden nicht bereitgestellt.

## <a name="dynamically-resizing-the-toolbar"></a><a name="_core_dynamically_resizing_the_toolbar"></a>Dynamisches Ändern der Größe der Symbolleiste

Ab Visual C++ Version 4,0 können Sie es Benutzern Ihrer Anwendung ermöglichen, die Größe von Gleit Komma Symbolleisten dynamisch zu ändern. In der Regel hat eine Symbolleiste eine lange, lineare Form, die horizontal angezeigt wird. Sie können jedoch die Ausrichtung der Symbolleiste und ihre Form ändern. Wenn der Benutzer z. b. eine Symbolleiste gegen eine vertikale Seite des Rahmen Fensters andockt, wird die Form in ein vertikales Layout geändert. Es ist auch möglich, die Symbolleiste in ein Rechteck mit mehreren Zeilen von Schaltflächen zu Formen.

Sie können:

- Legen Sie die dynamische Größe als Symbolleisten Merkmal fest.

- Legen Sie die festgelegte Größe als Symbolleisten Merkmal fest.

Um diese Unterstützung zu bieten, gibt es zwei neue Symbolleisten Stile für die Verwendung in den Aufrufen der [CToolBar:: Create](reference/ctoolbar-class.md#create) Member-Funktion. Sie lauten wie folgt:

- **CBRS_SIZE_DYNAMIC** Die Steuerleiste ist dynamisch.

- **CBRS_SIZE_FIXED** Die Steuerleiste ist korrigiert.

Der dynamische Stil der Größe ermöglicht dem Benutzer, die Größe der Symbolleiste zu ändern, während Sie unverankert ist, während Sie angedockt ist. Die Symbolleiste "umschließt", wo die Form geändert werden muss, wenn der Benutzer seine Ränder zieht.

Der festgelegte Stil der Größe behält die Umbruch Zustände einer Symbolleiste bei und korrigiert die Position der Schaltflächen in den einzelnen Spalten. Der Benutzer der Anwendung kann die Form der Symbolleiste nicht ändern. Die Symbolleiste wird an festgelegten Stellen umschlossen, z. b. die Positionen der Trennzeichen zwischen den Schaltflächen. Diese Form wird beibehalten, unabhängig davon, ob die Symbolleiste angedockt ist oder nicht. Der Effekt ist eine fixierte Palette mit mehreren Spalten von Schaltflächen.

Sie können auch [CToolBar:: GetButtonStyle](reference/ctoolbar-class.md#getbuttonstyle) verwenden, um einen Zustand und Stil für Schaltflächen auf den Symbolleisten zurückzugeben. Der Stil einer Schaltfläche bestimmt, wie die Schaltfläche angezeigt wird und wie Sie auf Benutzereingaben reagiert. der Status gibt an, ob sich die Schaltfläche in einem umschpackten Zustand befindet.

## <a name="setting-wrap-positions-for-a-fixed-style-toolbar"></a><a name="_core_setting_wrap_positions_for_a_fixed_style_toolbar"></a>Festlegen der Umbruch Positionen für eine Symbolleiste im festgelegten Stil

Legen Sie für eine Symbolleiste mit fester Stil Größe Symbolleisten-Schaltflächen Indizes fest, an denen die Symbolleiste eingebunden wird. Der folgende Code zeigt, wie Sie dies in der außer Kraft setzung des Hauptrahmen Fensters durchführen können `OnCreate` :

[!code-cpp[NVC_MFCDocViewSDI#10](codesnippet/cpp/docking-and-floating-toolbars_1.cpp)]

Das allgemeine MFC- [beispieldocktool](../overview/visual-cpp-samples.md) zeigt, wie Sie mithilfe der Member-Funktionen der Klassen [CControlBar](reference/ccontrolbar-class.md) und [CToolBar](reference/ctoolbar-class.md) das dynamische Layout einer Symbolleiste verwalten. Weitere Informationen finden Sie in der Datei EDITBAR. Cpp in DOCKTOOL.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Grundlagen zu Toolbar](toolbar-fundamentals.md)

- [QuickInfos für die Symbolleiste](toolbar-tool-tips.md)

- [Verwenden der alten Symbolleisten](using-your-old-toolbars.md)

## <a name="see-also"></a>Siehe auch

[Implementieren der MFC-Symbolleiste](mfc-toolbar-implementation.md)
