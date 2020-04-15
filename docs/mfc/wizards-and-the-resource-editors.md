---
title: Assistenten und der Ressourcen-Editor
ms.date: 11/04/2016
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365277"
---
# <a name="wizards-and-the-resource-editors"></a>Assistenten und der Ressourcen-Editor

Visual C++ enthält mehrere Assistenten für die MFC-Programmierung sowie viele integrierte Ressourcen-Editoren. Für die ActiveX-Steuerelementprogrammierung erfüllt der [ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md) einen Ähnlichen wie der MFC-Anwendungs-Assistent. Während Sie MFC-Anwendungen ohne die meisten dieser Tools schreiben können, vereinfachen und beschleunigen die Tools Ihre Arbeit erheblich.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>Verwenden des MFC-Anwendungs-Assistenten zum Erstellen einer MFC-Anwendung

Verwenden Sie den [MFC-Anwendungs-Assistenten,](../mfc/reference/mfc-application-wizard.md) um ein MFC-Projekt in Visual C++ zu erstellen, das OLE und Datenbankunterstützung umfassen kann. Dateien im Projekt enthalten Anwendungs-, Dokument-, Ansichts- und Framefensterklassen. Standardressourcen, einschließlich Menüs und einer optionalen Symbolleiste; andere erforderliche Windows-Dateien; und optionale .rtf-Dateien mit Standard-Windows-Hilfethemen, die Sie überarbeiten und erweitern können, um die Hilfedatei Ihres Programms zu erstellen.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Klassenansicht verwenden, um Klassen und Windows-Nachrichten zu verwalten

Mithilfe der Klassenansicht können Sie Handlerfunktionen für Windows-Nachrichten und -Befehle erstellen, Klassen erstellen und verwalten, Klassenmembervariablen erstellen, Automatisierungsmethoden und -eigenschaften erstellen, Datenbankklassen erstellen und vieles mehr.

> [!NOTE]
> Mit der Klassenansicht können Sie auch virtuelle Funktionen in den MFC-Klassen überschreiben. Wählen Sie die Klasse und die zu überschreibende virtuelle Funktion aus. Der Rest des Prozesses ähnelt der Nachrichtenbehandlung, wie in den folgenden Absätzen beschrieben.

Anwendungen, die unter Windows ausgeführt werden, sind [nachrichtengesteuert.](../mfc/message-handling-and-mapping.md) Benutzeraktionen und andere Ereignisse, die im laufenden Programm auftreten, führen dazu, dass Windows Nachrichten an die Fenster im Programm sendet. Wenn der Benutzer beispielsweise mit der Maus in einem Fenster klickt, sendet Windows eine WM_LBUTTONDOWN Nachricht, wenn die linke Maustaste gedrückt wird, und eine WM_LBUTTONUP Meldung, wenn die Schaltfläche freigegeben wird. Windows sendet auch WM_COMMAND Nachrichten, wenn der Benutzer Befehle aus der Menüleiste auswählt.

Im MFC-Framework können verschiedene Objekte, z. B. Dokumente, Ansichten, Rahmenfenster, Dokumentvorlagen und das Anwendungsobjekt, Nachrichten "behandeln". Ein solches Objekt stellt eine "Handlerfunktion" als eine seiner Memberfunktionen bereit, und das Framework ordnet die eingehende Nachricht seinem Handler zu.

Ein großer Teil der Programmieraufgabe besteht darin, welche Nachrichten welchen Objekten zugeordnet werden sollen, und diese Zuordnung dann zu implementieren. Dazu verwenden Sie die Klassenansicht und den [Klassen-Assistenten](reference/mfc-class-wizard.md).

Der [Klassen-Assistent](reference/mfc-class-wizard.md) erstellt leere Message-Handler-Memberfunktionen, und Sie verwenden den Quellcode-Editor, um den Text des Handlers zu implementieren. Sie können auch Klassen (einschließlich eigener Klassen, die nicht von MFC-Klassen abgeleitet sind) und deren Member mit Klassenansicht erstellen oder bearbeiten. Weitere Informationen zur Verwendung der Klassenansicht und zu Assistenten, die einem Projekt Code hinzufügen, finden Sie unter [Hinzufügen von Funktionen mit Code-Assistenten](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Verwenden der Ressourcen-Editoren zum Erstellen und Bearbeiten von Ressourcen

Verwenden Sie die Visual [C++-Ressourcen-Editoren,](../windows/resource-editors.md) um Menüs, Dialogfelder, benutzerdefinierte Steuerelemente, Beschleunigerschlüssel, Bitmaps, Symbole, Cursor, Zeichenfolgen und Versionsressourcen zu erstellen und zu bearbeiten. Ab Visual C++-Version 4.0 erleichtert ein Symbolleisten-Editor das Erstellen von Symbolleisten erheblich.

Um Ihnen noch weiter zu helfen, stellt die Microsoft Foundation-Klassenbibliothek eine Datei mit dem Namen COMMON bereit. RES, das "Clip Art"-Ressourcen enthält, die Sie aus COMMON kopieren können. RES und fügen Sie in Ihre eigene Ressourcendatei ein. gemeinsam. RES enthält Symbolleistenschaltflächen, allgemeine Cursor, Symbole und mehr. Sie können diese Ressourcen in Ihrer Anwendung verwenden, ändern und weiterverteilen. Weitere Informationen zu COMMON. RES, siehe [Clipart-Beispiel](../overview/visual-cpp-samples.md).

Der MFC-Anwendungs-Assistent, die Visual C++-Assistenten, Ressourcen-Editoren und das MFC-Framework erledigen viel Arbeit für Sie und erleichtern die Verwaltung des Codes erheblich. Der Großteil des anwendungsspezifischen Codes befindet sich in Den Dokument- und Ansichtsklassen.

## <a name="see-also"></a>Siehe auch

[Verwenden der Klassen zum Schreiben von Anwendungen für Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
