---
title: Klassen für Rahmenfenster (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 1c0a1e1e93433e0fbe07c11eb350216173e74d84
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625851"
---
# <a name="frame-window-classes-windows"></a>Klassen für Rahmenfenster (Windows)

Rahmen Fenster sind Fenster, die eine Anwendung oder einen Teil einer Anwendung umgestalten. Rahmen Fenster enthalten in der Regel weitere Fenster, z. b. Ansichten, Symbolleisten und Status leisten. Im Fall von `CMDIFrameWnd` können Sie `CMDIChildWnd` Objekte indirekt enthalten.

[CFrameWnd](reference/cframewnd-class.md)<br/>
Die Basisklasse für das Hauptrahmen Fenster einer SDI-Anwendung. Auch die Basisklasse für alle anderen Frame Fenster Klassen.

[CMDIFrameWnd](reference/cmdiframewnd-class.md)<br/>
Die Basisklasse für das Hauptrahmen Fenster einer MDI-Anwendung.

[CMDIChildWnd](reference/cmdichildwnd-class.md)<br/>
Die Basisklasse für die Dokument Rahmen Fenster einer MDI-Anwendung.

[CMiniFrameWnd](reference/cminiframewnd-class.md)<br/>
Ein halbheight-Rahmen Fenster, das in der Regel um unverankerte Symbolleisten geht.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Stellt das Rahmen Fenster für eine Ansicht bereit, wenn ein Server Dokument an Ort und Stelle bearbeitet wird.

## <a name="related-class"></a>Verwandte Klasse

`CMenu`Die Klasse stellt eine Schnittstelle bereit, über die auf die Menüs der Anwendung zugegriffen werden soll. Dies ist nützlich, um Menüs zur Laufzeit dynamisch zu bearbeiten. beispielsweise beim Hinzufügen oder Löschen von Menü Elementen gemäß Kontext. Obwohl Menüs am häufigsten mit Frame Fenstern verwendet werden, können Sie auch mit Dialogfeldern und anderen nicht untergeordneten Fenstern verwendet werden.

[CMenu](reference/cmenu-class.md)<br/>
Kapselt ein `HMENU` Handle für die Menüleiste der Anwendung und Popup Menüs.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
