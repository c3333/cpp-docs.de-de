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
ms.openlocfilehash: 00254bdf49015f26ac257789a15afd1e7f5cc31f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621708"
---
# <a name="frame-window-classes-created-by-the-application-wizard"></a>Vom Anwendungs-Assistenten erstellte Rahmenfensterklassen

Wenn Sie ein neues MFC-Projekt aus dem Dialogfeld " **Neues Projekt** ", zusätzlich zu den Anwendungs-, Dokument-und Ansichts Klassen, erstellen, erstellt der Anwendungs-Assistent eine abgeleitete Rahmen Fenster Klasse für das Hauptrahmen Fenster Ihrer Anwendung. Die-Klasse wird `CMainFrame` standardmäßig aufgerufen, und die darin enthaltenen Dateien heißen mainfrm. H und mainfrm. CPP.

Wenn es sich bei Ihrer Anwendung um einen SDI handelt, `CMainFrame` wird die Klasse von der [CFrameWnd](reference/cframewnd-class.md)-Klasse abgeleitet.

Wenn die Anwendung MDI ist, `CMainFrame` wird von der Klasse [CMDIFrameWnd](reference/cmdiframewnd-class.md)abgeleitet. In diesem Fall `CMainFrame` wird der Hauptframe implementiert, der das Menü, die Symbolleiste und Status leisten enthält. Der Anwendungs-Assistent leitet keine neue Dokument Rahmen-Fenster Klasse für Sie ab. Stattdessen wird die Standard Implementierung in der [CMDIChildWnd-Klasse](reference/cmdichildwnd-class.md)verwendet. Das MFC-Framework erstellt ein untergeordnetes Fenster, das jede Ansicht enthält (die vom Typ,,, usw. sein kann), die für `CScrollView` `CEditView` `CTreeView` `CListView` die Anwendung erforderlich ist. Wenn Sie Ihr Dokument Rahmen Fenster anpassen müssen, können Sie eine neue Dokument Rahmen Fenster-Klasse erstellen (siehe [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md)).

Wenn Sie sich dafür entscheiden, eine Symbolleiste zu unterstützen, verfügt die Klasse auch über Element Variablen vom Typ " [CToolBar](reference/ctoolbar-class.md) " und " [CStatusBar](reference/cstatusbar-class.md) " sowie `OnCreate` über eine nachrichtenhandlerfunktion zum Initialisieren der beiden [Steuer leisten](control-bars.md).

Diese Rahmen Fenster Klassen funktionieren wie erstellt, aber um ihre Funktionalität zu verbessern, müssen Sie Element Variablen und Element Funktionen hinzufügen. Möglicherweise möchten Sie auch, dass die Fenster Klassen andere Windows-Meldungen verarbeiten. Weitere Informationen finden Sie unter [Ändern der Stile eines Fensters, das von MFC erstellt wurde](changing-the-styles-of-a-window-created-by-mfc.md).

## <a name="see-also"></a>Siehe auch

[Rahmenfensterklassen](frame-window-classes.md)<br/>
[MFC-Programm oder Steuern von Quell-und Header Dateien](../build/reference/mfc-program-or-control-source-and-header-files.md)
