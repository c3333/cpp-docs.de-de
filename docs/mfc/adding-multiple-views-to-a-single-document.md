---
title: Hinzufügen mehrerer Ansichten zu einem Dokument
ms.date: 11/04/2016
helpviewer_keywords:
- multiple views [MFC], SDI applications
- documents [MFC], multiple views
- single document interface (SDI), adding views
- views [MFC], SDI applications
ms.assetid: 86d0c134-01d5-429c-b672-36cfb956dc01
ms.openlocfilehash: 95de3a582c3d45db858e2b4bce0268e1dab63931
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215971"
---
# <a name="adding-multiple-views-to-a-single-document"></a>Hinzufügen mehrerer Ansichten zu einem Dokument

In einer SDI-Anwendung (Single-Document Interface), die mit der MFC-Bibliothek (Microsoft Foundation Class) erstellt wurde, wird jeder Dokumenttyp einem einzelnen Ansichtstyp zugeordnet. In einigen Fällen ist es wünschenswert, dass Sie die aktuelle Ansicht eines Dokuments mit einer neuen Ansicht wechseln können.

> [!TIP]
> Weitere Verfahren zum Implementieren mehrerer Sichten für ein einzelnes Dokument finden Sie unter [CDocument:: AddView](reference/cdocument-class.md#addview) und MFC-Beispiel [sammeln](../overview/visual-cpp-samples.md) .

Sie können diese Funktionalität implementieren, indem Sie eine neue `CView` abgeleitete Klasse und zusätzlichen Code zum dynamischen wechseln der Sichten in eine vorhandene MFC-Anwendung hinzufügen.

Die Schritte lauten wie folgt:

- [Vorhandene Anwendungsklasse ändern](#vcconmodifyexistingapplicationa1)

- [Erstellen und Ändern der neuen Ansichts Klasse](#vcconnewviewclassa2)

- [Erstellen und Anfügen der neuen Ansicht](#vcconattachnewviewa3)

- [Implementieren der Wechselfunktion](#vcconswitchingfunctiona4)

- [Unterstützung für das Wechseln der Ansicht hinzufügen](#vcconswitchingtheviewa5)

Im restlichen Teil dieses Themas wird Folgendes vorausgesetzt:

- Der Name des von `CWinApp` abgeleiteten Objekts ist `CMyWinApp` , und `CMyWinApp` wird in *MYWINAPP deklariert und definiert. H* und *MYWINAPP. Cpp*.

- `CNewView`der Name des neuen, von `CView` abgeleiteten Objekts, und `CNewView` wird in NEWVIEW deklariert und definiert *. H* und *NEWVIEW. Cpp*.

## <a name="modify-the-existing-application-class"></a><a name="vcconmodifyexistingapplicationa1"></a>Vorhandene Anwendungsklasse ändern

Damit die Anwendung zwischen Sichten wechseln kann, müssen Sie die Anwendungsklasse ändern, indem Sie Element Variablen zum Speichern der Sichten und eine Methode zum wechseln hinzufügen.

Fügen Sie der Deklaration von `CMyWinApp` in MYWINAPP den folgenden Code hinzu *. H*:

[!code-cpp[NVC_MFCDocViewSDI#1](codesnippet/cpp/adding-multiple-views-to-a-single-document_1.h)]

Die neuen Element Variablen, `m_pOldView` und `m_pNewView` , zeigen auf die aktuelle Ansicht und die neu erstellte. Die neue-Methode ( `SwitchView` ) schaltet die Ansichten ein, wenn Sie vom Benutzer angefordert werden. Der Text der-Methode wird weiter unten in diesem Thema unter [Implementieren der Wechselfunktion](#vcconswitchingfunctiona4)erläutert.

Die letzte Änderung der Anwendungsklasse erfordert das Einschließen einer neuen Header Datei, die eine in der Wechselfunktion verwendete Windows-Meldung (**WM_INITIALUPDATE**) definiert.

Fügen Sie die folgende Zeile in den Abschnitt include von *MYWINAPP ein. Cpp*:

[!code-cpp[NVC_MFCDocViewSDI#2](codesnippet/cpp/adding-multiple-views-to-a-single-document_2.cpp)]

Speichern Sie die Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="create-and-modify-the-new-view-class"></a><a name="vcconnewviewclassa2"></a>Erstellen und Ändern der neuen Ansichts Klasse

Das Erstellen der neuen Ansichts Klasse wird mithilfe des Befehls **neue Klasse** , der in Klassenansicht verfügbar ist, vereinfacht. Die einzige Voraussetzung für diese Klasse ist, dass Sie von abgeleitet wird `CView` . Fügen Sie der Anwendung diese neue Klasse hinzu. Spezifische Informationen zum Hinzufügen einer neuen Klasse zum Projekt finden Sie unter [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md).

Nachdem Sie dem Projekt die Klasse hinzugefügt haben, müssen Sie die Barrierefreiheit einiger Ansichts Klassenmember ändern.

Ändern Sie *NEWVIEW. H* , indem der Zugriffsspezifizierer von **`protected`** in **`public`** für den Konstruktor und den debugtor geändert wird. Dadurch kann die Klasse dynamisch erstellt und zerstört und die Darstellung der Ansicht geändert werden, bevor Sie sichtbar ist.

Speichern Sie die Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="create-and-attach-the-new-view"></a><a name="vcconattachnewviewa3"></a>Erstellen und Anfügen der neuen Ansicht

Um die neue Ansicht zu erstellen und anzufügen, müssen Sie die `InitInstance` Funktion Ihrer Anwendungsklasse ändern. Die Änderung fügt neuen Code hinzu, der ein neues Ansichts Objekt erstellt und dann sowohl `m_pOldView` als auch `m_pNewView` mit den beiden vorhandenen Ansichts Objekten initialisiert.

Da die neue Sicht innerhalb der-Funktion erstellt wird `InitInstance` , werden die neuen und vorhandenen Sichten für die Lebensdauer der Anwendung beibehalten. Die Anwendung könnte die neue Ansicht jedoch genauso einfach dynamisch erstellen.

Fügen Sie diesen Code nach dem-Befehl ein `ProcessShellCommand` :

[!code-cpp[NVC_MFCDocViewSDI#3](codesnippet/cpp/adding-multiple-views-to-a-single-document_3.cpp)]

Speichern Sie die Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="implement-the-switching-function"></a><a name="vcconswitchingfunctiona4"></a>Implementieren der Wechselfunktion

Im vorherigen Schritt haben Sie Code hinzugefügt, der ein neues Ansichts Objekt erstellt und initialisiert hat. Der letzte Hauptabschnitt ist die Implementierung der Wechsel Methode, `SwitchView` .

Am Ende der Implementierungs Datei für Ihre Anwendungsklasse (*MYWINAPP). Cpp*): Fügen Sie die folgende Methoden Definition hinzu:

[!code-cpp[NVC_MFCDocViewSDI#4](codesnippet/cpp/adding-multiple-views-to-a-single-document_4.cpp)]

Speichern Sie die Änderungen, und fahren Sie mit dem nächsten Schritt fort.

## <a name="add-support-for-switching-the-view"></a><a name="vcconswitchingtheviewa5"></a>Unterstützung für das Wechseln der Ansicht hinzufügen

Der letzte Schritt umfasst das Hinzufügen von Code, der die-Methode aufruft, `SwitchView` Wenn die Anwendung zwischen Sichten wechseln muss. Dies kann auf verschiedene Arten erfolgen: durch Hinzufügen eines neuen Menü Elements für den Benutzer, um die Ansichten intern auszuwählen oder zu wechseln, wenn bestimmte Bedingungen erfüllt sind.

Weitere Informationen zum Hinzufügen neuer Menü Elemente und Befehls Handlerfunktionen finden Sie unter [Handler für Befehle und Steuerelement Benachrichtigungen](handlers-for-commands-and-control-notifications.md).

## <a name="see-also"></a>Weitere Informationen

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
