---
title: 'Zwischenablage: Verwenden der Windows-Zwischenablage'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
ms.openlocfilehash: 1b11bfe18443858de0dd7032f72fecadb1d6ebdd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626034"
---
# <a name="clipboard-using-the-windows-clipboard"></a>Zwischenablage: Verwenden der Windows-Zwischenablage

In diesem Thema wird beschrieben, wie Sie die standardmäßige Windows-Zwischenablage-API in ihrer MFC-Anwendung verwenden

Die meisten Anwendungen für Windows unterstützen das Ausschnitten oder Kopieren von Daten in die Windows-Zwischenablage und das Einfügen von Daten aus der Zwischenablage Die Zwischenablage Datenformate unterscheiden sich je nach Anwendung. Das Framework unterstützt für eine begrenzte Anzahl von Klassen nur eine begrenzte Anzahl von Zwischenablage Formaten. Normalerweise implementieren Sie die in der Zwischenablage bezogenen Befehle – Ausschneiden, kopieren und Einfügen – im Menü Bearbeiten für die Ansicht. Die Klassenbibliothek definiert die Befehls-IDs für diese Befehle: **ID_EDIT_CUT**, **ID_EDIT_COPY**und **ID_EDIT_PASTE**. Ihre Meldungs zeiligen Eingabe Aufforderungen werden ebenfalls definiert.

[Nachrichten und Befehle im Framework](messages-and-commands-in-the-framework.md) wird erläutert, wie Menübefehle in der Anwendung behandelt werden, indem der Menübefehl einer Handlerfunktion zuordnet wird. Solange Ihre Anwendung keine Handlerfunktionen für die Zwischenablage Befehle im Menü Bearbeiten definiert, bleiben Sie deaktiviert. Um Handlerfunktionen für die Befehle zum Ausschneiden und kopieren zu schreiben, implementieren Sie die Auswahl in Ihrer Anwendung. Zum Schreiben einer Handlerfunktion für den Befehl Einfügen Fragen Sie die Zwischenablage ab, um festzustellen, ob Sie Daten in einem Format enthält, das Ihre Anwendung akzeptieren kann. Wenn Sie z. b. den Befehl kopieren aktivieren möchten, können Sie einen Handler schreiben, der etwa wie folgt aussieht:

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

Die Befehle zum Ausschneiden, kopieren und Einfügen sind nur in bestimmten Kontexten sinnvoll. Die Befehle zum Ausschneiden und kopieren sollten nur aktiviert werden, wenn etwas ausgewählt ist, und der Befehl Einfügen nur, wenn sich etwas in der Zwischenablage befindet. Sie können dieses Verhalten bereitstellen, indem Sie updatehandlerfunktionen definieren, die diese Befehle abhängig vom Kontext aktivieren oder deaktivieren. Weitere Informationen finden Sie unter [Aktualisieren von Benutzeroberflächen Objekten](how-to-update-user-interface-objects.md).

Der Microsoft Foundation Class-Bibliothek stellt die Unterstützung der Zwischenablage für die Textbearbeitung mit den `CEdit` Klassen und bereit `CEditView` . Die OLE-Klassen vereinfachen auch das Implementieren von Zwischenablage Operationen, die OLE-Elemente einschließen. Weitere Informationen zu den OLE-Klassen finden [Sie unter Zwischenablage: Verwenden des OLE-Zwischenablage Mechanismus](clipboard-using-the-ole-clipboard-mechanism.md).

Das Implementieren anderer Befehle zum Bearbeiten von Menüs, wie z. b. rückgängig (**ID_EDIT_UNDO**) und wiederholen (**ID_EDIT_REDO**), wird Ihnen ebenfalls überlassen. Wenn Ihre Anwendung diese Befehle nicht unterstützt, können Sie Sie mithilfe der Visual C++ Ressourcen-Editoren problemlos aus ihrer Ressourcen Datei löschen.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Kopieren und Einfügen von Daten](clipboard-copying-and-pasting-data.md)

- [Verwenden des OLE-Zwischenablage Mechanismus](clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>Siehe auch

[Zwischenablage](clipboard.md)
