---
title: MFC-Anwendungs-Assistent
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351838"
---
# <a name="mfc-application-wizard"></a>MFC-Anwendungs-Assistent

Der MFC-Anwendungs-Assistent erstellt eine Anwendung, die beim Kompilieren die grundlegenden Funktionen einer ausführbaren Windows-Anwendung (.exe) implementiert. Die MFC-Startanwendung umfasst C++-Quelldateien (.cpp), Ressourcendateien (.rc), Headerdateien (.h) sowie eine Projektdatei (.vcxproj). Der in diesen Startdateien generierte Code basiert auf MFC.

> [!NOTE]
> Abhängig von den ausgewählten Optionen kann der Assistent zusätzliche Projektdateien erstellen. Wenn Sie beispielsweise auf der Seite [Erweiterte Funktionen](../../mfc/reference/advanced-features-mfc-application-wizard.md) **kontextabhängige Hilfe** auswählen, erstellt der Assistent die Dateien, die zum Kompilieren der Hilfedateien des Projekts erforderlich sind. Weitere Informationen zu den vom Assistenten erstellten Dateien finden Sie unter [Dateitypen, die für Visual Studio C++-Projekte erstellt](../../build/reference/file-types-created-for-visual-cpp-projects.md)wurden, und in der Datei Readme.txt im Projekt.

## <a name="overview"></a>Übersicht

Auf dieser Seite des Assistenten sind die aktuellen Anwendungseinstellungen für die zu erstellende MFC-Anwendung aufgeführt. Der Assistent erstellt ein Projekt standardmäßig wie folgt:

- [Anwendungstyp, MFC-Anwendungs-Assistent](../../mfc/reference/application-type-mfc-application-wizard.md)

  - Das Projekt wird mit MDI (Multiple Document Interface)-Unterstützung mit Registerkarten erstellt. Weitere Informationen finden Sie unter [SDI und MDI](../../mfc/sdi-and-mdi.md).

  - Das Projekt verwendet die [Dokument-/Ansichtsarchitektur](../../mfc/document-view-architecture.md).

  - Das Projekt verwendet Unicode-Bibliotheken.

  - Das Projekt wird mit dem Visual Studio-Projektformat erstellt und aktiviert visuelle Stilumschaltung.

  - Das Projekt verwendet MFC in einer gemeinsam genutzten DLL. Weitere Informationen finden Sie unter [Erstellen von C/C++-DLLs in Visual Studio](../../build/dlls-in-visual-cpp.md).

- [Verbunddokumentunterstützung, MFC-Anwendungs-Assistent](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - Das Projekt bietet keine Unterstützung für Verbunddokumente.

- [Zeichenfolgen für Dokumentvorlagen, MFC-Anwendungs-Assistent](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - Das Projekt verwendet den Projektnamen als standardmäßige Zeichenfolgen für Dokumentvorlagen.

- [Datenbankunterstützung, MFC-Anwendungs-Assistent](../../mfc/reference/database-support-mfc-application-wizard.md)

  - Das Projekt bietet keine Datenbankunterstützung.

- [Benutzeroberflächen-Features, MFC-Anwendungs-Assistent](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - Das Projekt implementiert standardmäßige Windows-Benutzeroberflächenfeatures wie ein Systemmenü, eine **About** Statusleiste, das Maximieren und Minimieren von Feldern, ein Info-Feld, eine Standardmenüleiste und Docking-Symbolleiste sowie untergeordnete Frames.

- [Erweiterte Funktionen, MFC-Anwendungsassistent](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - Das Projekt unterstützt das Drucken und die Seitenansicht.

  - Das Projekt unterstützt ActiveX-Steuerelemente. Weitere Informationen finden Sie unter [Sequenz von Vorgängen zum Erstellen von ActiveX-Steuerelementen](../../mfc/sequence-of-operations-for-creating-activex-controls.md).

  - Das Projekt bietet keine Unterstützung für [Automation](../../mfc/automation.md), [MAPI](../../mfc/mapi-support-in-mfc.md), [Windows Sockets](../../mfc/windows-sockets-in-mfc.md)oder Active Accessibility.

  - Das Projekt **Explorer** unterstützt einen Explorer-Dockingbereich, einen Ausgabe-Dockingbereich und einen **Output** **Eigenschaften-Dockingbereich.**

- [Erstellte Klassen, MFC-Anwendungs-Assistent](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - Die Ansichtsklasse des Projekts wird von der [CView-Klasse](../../mfc/reference/cview-class.md)abgeleitet.

  - Die Anwendungsklasse des Projekts wird von der [CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)abgeleitet.

  - Die Dokumentklasse des Projekts wird von der [CDocument-Klasse](../../mfc/reference/cdocument-class.md)abgeleitet.

  - Die Hauptrahmenklasse des Projekts wird von der [CMDIFrameWndEx-Klasse](../../mfc/reference/cmdiframewndex-class.md)abgeleitet.

  - Die untergeordnete Rahmenklasse des Projekts wird von der [CMDIChildWndEx-Klasse](../../mfc/reference/cmdichildwndex-class.md)abgeleitet.

Um diese Standardeinstellungen zu ändern, klicken Sie in der linken Spalte des Assistenten auf die Titel der entsprechenden Registerkarten und nehmen auf der angezeigten Seite die Änderungen vor.

Nachdem Sie ein MFC-Anwendungsprojekt erstellt haben, können Sie Dem [code wizards](../../ide/adding-functionality-with-code-wizards-cpp.md)Projekt mithilfe von Visual C++-Codeassistenten Objekte oder Steuerelemente hinzufügen.

## <a name="see-also"></a>Siehe auch

[Erstellen einer MFC-Anwendung](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC-Desktopanwendungen](../../mfc/mfc-desktop-applications.md)<br/>
[Verwenden der Klassen zum Schreiben von Anwendungen für Windows](../../mfc/using-the-classes-to-write-applications-for-windows.md)
