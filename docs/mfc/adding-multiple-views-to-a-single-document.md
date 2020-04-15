---
title: Hinzufügen mehrerer Ansichten zu einem Dokument
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 4fa39a4d9369c84d2cffdaeff28dc9cb2f966b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370865"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Hinzufügen mehrerer Ansichten zu einem Dokument

In einer SDI-Anwendung (Single Document Interface) mit der Microsoft Foundation Class (MFC)-Bibliothek ist jeder Dokumenttyp einem einzelnen Ansichtstyp zugeordnet. In einigen Fällen ist es wünschenswert, die aktuelle Ansicht eines Dokuments mit einer neuen Ansicht wechseln zu können.

> [!TIP]
> Weitere Verfahren zum Implementieren mehrerer Ansichten für ein einzelnes Dokument finden Sie unter [CDocument::AddView](../mfc/reference/cdocument-class.md#addview) und das [COLLECT](../overview/visual-cpp-samples.md) MFC-Beispiel.

Sie können diese Funktionalität implementieren, indem Sie eine neue `CView`-abgeleitete Klasse und zusätzlichen Code hinzufügen, um die Ansichten dynamisch zu einer vorhandenen MFC-Anwendung zu wechseln.

Die Schritte lauten wie folgt:

- [Ändern der vorhandenen Anwendungsklasse](#vcconmodifyexistingapplicationa1)

- [Erstellen und Ändern der neuen Ansichtsklasse](#vcconnewviewclassa2)

- [Erstellen und Anfügen der neuen Ansicht](#vcconattachnewviewa3)

- [Implementieren der Switching-Funktion](#vcconswitchingfunctiona4)

- [Unterstützung für das Wechseln der Ansicht hinzufügen](#vcconswitchingtheviewa5)

Im weiteren Verlauf dieses Themas wird Folgendes vorausgesetzt:

- Der Name `CWinApp`des -derived-Objekts ist `CMyWinApp`, und `CMyWinApp` wird in *MYWINAPP deklariert und definiert. H* und *MYWINAPP. CPP*.

- `CNewView`ist der Name `CView`des neuen -derived-Objekts und `CNewView` wird in NEWVIEW deklariert und *definiert. H* und *NEWVIEW. CPP*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Ändern der vorhandenen Anwendungsklasse

Damit die Anwendung zwischen Ansichten wechseln kann, müssen Sie die Anwendungsklasse ändern, indem Sie Membervariablen zum Speichern der Ansichten und eine Methode zum Wechseln dieser Ansichten hinzufügen.

Fügen Sie der Deklaration von `CMyWinApp` in *MYWINAPP den folgenden Code hinzu. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Die neuen `m_pOldView` Membervariablen `m_pNewView`und zeigen auf die aktuelle Ansicht und die neu erstellte Ansicht. Die neue`SwitchView`Methode ( ) wechselt die Ansichten, wenn sie vom Benutzer angefordert wird. Der Text der Methode wird weiter unten in diesem Thema unter [Implementieren der Switching-Funktion](#vcconswitchingfunctiona4)erläutert.

Die letzte Änderung an der Anwendungsklasse erfordert das Einschließen einer neuen Headerdatei, die eine Windows-Nachricht (**WM_INITIALUPDATE**definiert), die in der Switching-Funktion verwendet wird.

Fügen Sie die folgende Zeile in den Include-Abschnitt von *MYWINAPP ein. CPP*:

[!code-cpp[NVC_MFCDocViewSDI#2](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Speichern Sie Ihre Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Erstellen und Ändern der neuen Ansichtsklasse

Das Erstellen der neuen Ansichtsklasse wird mithilfe des **Befehls Neue Klasse,** der in der Klassenansicht verfügbar ist, erleichtert. Die einzige Voraussetzung für diese Klasse ist, dass sie von ableitet. `CView` Fügen Sie diese neue Klasse zur Anwendung hinzu. Weitere Informationen zum Hinzufügen einer neuen Klasse zum Projekt finden Sie unter [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md).

Nachdem Sie die Klasse dem Projekt hinzugefügt haben, müssen Sie die Zugänglichkeit einiger Ansichtsklassenmember ändern.

Ändern Sie *NEWVIEW. H,* indem der Zugriffsbezeichner für den Konstruktor und Destruktor von **"geschützt"** auf **"öffentlich"** geändert wird. Dadurch kann die Klasse dynamisch erstellt und zerstört werden und die Ansichtsdarstellung ändern, bevor sie sichtbar ist.

Speichern Sie Ihre Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Erstellen und Anfügen der neuen Ansicht

Um die neue Ansicht zu erstellen und `InitInstance` anzufügen, müssen Sie die Funktion Ihrer Anwendungsklasse ändern. Die Änderung fügt neuen Code hinzu, der ein `m_pOldView` neues `m_pNewView` Ansichtsobjekt erstellt und dann sowohl und mit den beiden vorhandenen Ansichtsobjekten initialisiert.

Da die neue Ansicht `InitInstance` innerhalb der Funktion erstellt wird, bleiben sowohl die neue als auch die vorhandene Ansicht während der Lebensdauer der Anwendung erhalten. Die Anwendung könnte die neue Ansicht jedoch genauso einfach dynamisch erstellen.

Fügen Sie diesen Code `ProcessShellCommand`nach dem Aufruf von:

[!code-cpp[NVC_MFCDocViewSDI#3](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Speichern Sie Ihre Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Implementieren der Switching-Funktion

Im vorherigen Schritt haben Sie Code hinzugefügt, der ein neues Ansichtsobjekt erstellt und initialisiert hat. Das letzte große Stück ist die `SwitchView`Implementierung der Switching-Methode, .

Am Ende der Implementierungsdatei für Ihre Anwendungsklasse (*MYWINAPP. CPP*), fügen Sie die folgende Methodendefinition hinzu:

[!code-cpp[NVC_MFCDocViewSDI#4](../mfc/codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Speichern Sie Ihre Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Unterstützung für das Wechseln der Ansicht hinzufügen

Der letzte Schritt umfasst das `SwitchView` Hinzufügen von Code, der die Methode aufruft, wenn die Anwendung zwischen Ansichten wechseln muss. Dies kann auf verschiedene Weise erfolgen: indem entweder ein neues Menüelement hinzugefügt wird, das der Benutzer auswählen kann, oder die Ansichten intern wechselt, wenn bestimmte Bedingungen erfüllt sind.

Weitere Informationen zum Hinzufügen neuer Menüelemente und Befehlshandlerfunktionen finden Sie unter [Handler für Befehle und Steuerbenachrichtigungen](../mfc/handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtsarchitektur](../mfc/document-view-architecture.md)
