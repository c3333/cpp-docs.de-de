---
title: Vom Anwendungs-Assistenten erstellte Rahmenfensterklassen
ms.date: 11/04/2016
f1_keywords:
- CMainFrame
helpviewer_keywords:
- application wizards [MFC], frame window classes created by
- window classes [MFC]
- classes [MFC], frame-window
- CMDIFrameWnd class [MFC], frame windows
- window classes [MFC], frame
- CFrameWnd class [MFC], frame windows
- CMDIChildWnd class [MFC], frame windows
- frame window classes [MFC], created by application wizards
- CMainFrame class [MFC]
ms.assetid: 9947df73-4470-49a0-ac61-7b6ee401a74e
ms.openlocfilehash: c17ba2b6dd79e8e62baa29bba403c136d16a0d95
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077539"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Vom Anwendungs-Assistenten erstellte Rahmenfensterklassen

Wenn Sie ein neues MFC-Projekt aus dem Dialogfeld " **Neues Projekt** ", zusätzlich zu den Anwendungs-, Dokument-und Ansichts Klassen, erstellen, erstellt der Anwendungs-Assistent eine abgeleitete Rahmen Fenster Klasse für das Hauptrahmen Fenster Ihrer Anwendung. Die-Klasse wird standardmäßig `CMainFrame` aufgerufen, und die darin enthaltenen Dateien heißen mainfrm. H und mainfrm. CPP.

Wenn Ihre Anwendung SDI ist, wird die `CMainFrame` Klasse von der Klasse [CFrameWnd](../mfc/reference/cframewnd-class.md)abgeleitet.

Wenn die Anwendung MDI ist, wird `CMainFrame` von der Klasse [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)abgeleitet. In diesem Fall `CMainFrame` den Hauptframe implementiert, der das Menü, die Symbolleiste und Status leisten enthält. Der Anwendungs-Assistent leitet keine neue Dokument Rahmen-Fenster Klasse für Sie ab. Stattdessen wird die Standard Implementierung in der [CMDIChildWnd-Klasse](../mfc/reference/cmdichildwnd-class.md)verwendet. Das MFC-Framework erstellt ein untergeordnetes Fenster, das jede Ansicht enthält (die vom Typ `CScrollView`, `CEditView`, `CTreeView`, `CListView`usw. sein kann), die für die Anwendung erforderlich ist. Wenn Sie Ihr Dokument Rahmen Fenster anpassen müssen, können Sie eine neue Dokument Rahmen Fenster-Klasse erstellen (siehe [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md)).

Wenn Sie sich dafür entscheiden, eine Symbolleiste zu unterstützen, verfügt die Klasse auch über Element Variablen vom Typ " [CToolBar](../mfc/reference/ctoolbar-class.md) " und " [CStatusBar](../mfc/reference/cstatusbar-class.md) " sowie über eine `OnCreate` nachrichtenhandlerfunktion zum Initialisieren der beiden [Steuer leisten](../mfc/control-bars.md).

Diese Rahmen Fenster Klassen funktionieren wie erstellt, aber um ihre Funktionalität zu verbessern, müssen Sie Element Variablen und Element Funktionen hinzufügen. Möglicherweise möchten Sie auch, dass die Fenster Klassen andere Windows-Meldungen verarbeiten. Weitere Informationen finden Sie unter [Ändern der Stile eines Fensters, das von MFC erstellt wurde](../mfc/changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Weitere Informationen

[Rahmenfensterklassen](../mfc/frame-window-classes.md)<br/>
[MFC-Programm oder Steuern von Quell- und Headerdateien](../build/reference/mfc-program-or-control-source-and-header-files.md)
