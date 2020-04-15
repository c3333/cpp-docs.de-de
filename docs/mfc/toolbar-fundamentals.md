---
title: Grundlegendes über Symbolleisten
ms.date: 11/04/2016
f1_keywords:
- RT_TOOLBAR
helpviewer_keywords:
- embedding toolbar in frame window class [MFC]
- application wizards [MFC], installing default application toolbars
- toolbars [MFC], creating
- resources [MFC], toolbar
- toolbar controls [MFC], toolbars created using Application Wizard
- toolbar controls [MFC], command ID
- RT_TOOLBAR resource [MFC]
- toolbars [MFC], adding default using Application Wizard
- LoadBitmap method [MFC], toolbars
- Toolbar editor [MFC], Application Wizard
- command IDs [MFC], toolbar buttons
- SetButtons method [MFC]
- CToolBar class [MFC], default toolbars in Application Wizard
- frame window classes [MFC], toolbar embedded in
- LoadToolBar method [MFC]
ms.assetid: cc00aaff-8a56-433b-b0c0-b857d76b4ffd
ms.openlocfilehash: d4e8793337beb2eed533fe04daf549ec21efc61d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373476"
---
# <a name="toolbar-fundamentals"></a>Grundlegendes über Symbolleisten

In diesem Artikel wird die grundlegende MFC-Implementierung beschrieben, mit der Sie Ihrer Anwendung eine Standardsymbolleiste hinzufügen können, indem Sie im Anwendungs-Assistenten eine Option auswählen. Folgende Themen werden behandelt:

- [Die Toolbar-Option anwendungsassistent](#_core_the_appwizard_toolbar_option)

- [Die Symbolleiste im Code](#_core_the_toolbar_in_code)

- [Bearbeiten der Symbolleistenressource](#_core_editing_the_toolbar_resource)

- [Mehrere Symbolleisten](#_core_multiple_toolbars)

## <a name="the-application-wizard-toolbar-option"></a><a name="_core_the_appwizard_toolbar_option"></a>Die Toolbar-Option des Anwendungs-Assistenten

Um eine einzelne Symbolleiste mit Standardschaltflächen zu erhalten, wählen Sie die Option Standard-Docking-Symbolleisten auf der Seite mit der Bezeichnung Benutzeroberflächenfeatures aus. Dadurch wird Ihrer Anwendung Code hinzugefügt, der:

- Erstellt das Symbolleistenobjekt.

- Verwaltet die Symbolleiste, einschließlich ihrer Fähigkeit zum Andocken oder Schweben.

## <a name="the-toolbar-in-code"></a><a name="_core_the_toolbar_in_code"></a>Die Symbolleiste im Code

Die Symbolleiste ist ein [CToolBar-Objekt,](../mfc/reference/ctoolbar-class.md) das als `CMainFrame` Datenmember der Anwendungsklasse deklariert ist. Mit anderen Worten, das Symbolleistenobjekt ist in das Hauptrahmenfensterobjekt eingebettet. Dies bedeutet, dass MFC die Symbolleiste erstellt, wenn es das Rahmenfenster erstellt, und die Symbolleiste zerstört, wenn sie das Rahmenfenster zerstört. Die folgende partielle Klassendeklaration für eine MDI-Anwendung (Multiple Document Interface) zeigt Datenmember für eine eingebettete Symbolleiste und eine eingebettete Statusleiste an. Außerdem wird die Außerkraftsetzung der `OnCreate` Memberfunktion angezeigt.

[!code-cpp[NVC_MFCListView#6](../atl/reference/codesnippet/cpp/toolbar-fundamentals_1.h)]

Die Werkzeugleistenerstellung `CMainFrame::OnCreate`erfolgt in . MFC ruft [OnCreate](../mfc/reference/cwnd-class.md#oncreate) auf, nachdem das Fenster für den Rahmen erstellt wurde, aber bevor es sichtbar wird. Die `OnCreate` vom Anwendungs-Assistenten generierte Standardeinstellung führt die folgenden Toolbar-Aufgaben aus:

1. Ruft `CToolBar` die [Memberfunktion Erstellen](../mfc/reference/ctoolbar-class.md#create) des Objekts auf, um das zugrunde liegende [CToolBarCtrl-Objekt](../mfc/reference/ctoolbarctrl-class.md) zu erstellen.

1. Ruft [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) auf, um die Ressourceninformationen der Symbolleiste zu laden.

1. Ruft Funktionen auf, um Docking-, Floating- und Tool-Tipps zu aktivieren. Weitere Informationen zu diesen Anrufen finden Sie im Artikel [Docking and Floating Toolbars](../mfc/docking-and-floating-toolbars.md).

> [!NOTE]
> Das MFC General-Beispiel [DOCKTOOL](../overview/visual-cpp-samples.md) enthält Illustrationen von alten und neuen MFC-Symbolleisten. Die Symbolleisten, `COldToolbar` die verwenden, `LoadBitmap` erfordern Aufrufe `LoadToolBar`in `SetButtons`Schritt 2 an (anstelle) und an . Die neuen Symbolleisten `LoadToolBar`erfordern Aufrufe von .

Die Docking-, Floating- und Tool-Tipps-Aufrufe sind optional. Sie können diese `OnCreate` Zeilen entfernen, wenn Sie es vorziehen. Das Ergebnis ist eine Symbolleiste, die fest bleibt, nicht schweben oder umdocken kann und keine Werkzeugspitzen anzeigen kann.

## <a name="editing-the-toolbar-resource"></a><a name="_core_editing_the_toolbar_resource"></a>Bearbeiten der Symbolleistenressource

Die Standardsymbolleiste, die Sie mit dem Anwendungs-Assistenten erhalten, basiert auf einer **RT_TOOLBAR** benutzerdefinierteressource, die in MFC-Version 4.0 eingeführt wurde. Sie können diese Ressource mit dem [Symbolleisten-Editor](../windows/toolbar-editor.md)bearbeiten. Mit dem Editor können Sie Schaltflächen einfach hinzufügen, löschen und neu anordnen. Es enthält einen grafischen Editor für die Schaltflächen, der dem allgemeinen Grafikeditor in Visual C++ sehr ähnlich ist. Wenn Sie Symbolleisten in früheren Versionen von Visual C++ bearbeitet haben, wird die Aufgabe jetzt viel einfacher.

Um eine Symbolleistenschaltfläche mit einem Befehl zu verbinden, geben `ID_MYCOMMAND`Sie der Schaltfläche eine Befehls-ID, z. B. . Geben Sie die Befehls-ID auf der Eigenschaftenseite der Schaltfläche im Symbolleisten-Editor an. Erstellen Sie dann eine Handlerfunktion für den Befehl (weitere Informationen finden Sie unter [Zuordnen von Nachrichten zu Funktionen).](../mfc/reference/mapping-messages-to-functions.md)

Neue [CToolBar-Memberfunktionen](../mfc/reference/ctoolbar-class.md) arbeiten mit der **RT_TOOLBAR** Ressource. [LoadToolBar](../mfc/reference/ctoolbar-class.md#loadtoolbar) tritt nun an die Stelle von [LoadBitmap,](../mfc/reference/ctoolbar-class.md#loadbitmap) um die Bitmap der Symbolleisten-Schaltflächenbilder zu laden, und SetButtons, um die [Schaltflächenstile](../mfc/reference/ctoolbar-class.md#setbuttons) festzulegen und Schaltflächen mit Bitmap-Bildern zu verbinden.

Weitere Informationen zur Verwendung des Symbolleisten-Editors finden Sie unter [Toolbar-Editor](../windows/toolbar-editor.md).

## <a name="multiple-toolbars"></a><a name="_core_multiple_toolbars"></a>Mehrere Symbolleisten

Der Anwendungs-Assistent stellt Ihnen eine Standardsymbolleiste zur Verfügung. Wenn Sie mehr als eine Symbolleiste in Ihrer Anwendung benötigen, können Sie den Code für zusätzliche Symbolleisten basierend auf dem vom Assistenten generierten Code für die Standardsymbolleiste modellieren.

Wenn Sie eine Symbolleiste als Ergebnis eines Befehls anzeigen möchten, müssen Sie:

- Erstellen Sie eine neue Symbolleistenressource mit dem `OnCreate` Symbolleisten-Editor, und laden Sie sie mit der [LoadToolbar-Memberfunktion](../mfc/reference/ctoolbar-class.md#loadtoolbar) ein.

- Einbetten eines neuen [CToolBar-Objekts](../mfc/reference/ctoolbar-class.md) in ihre Hauptrahmenfensterklasse.

- Machen Sie die `OnCreate` entsprechenden Funktionsaufrufe, um die Symbolleiste anzudocken oder zu schweben, ihre Stile festzulegen usw.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [MFC Toolbar-Implementierung (Übersichtsinformationen zu Symbolleisten)](../mfc/mfc-toolbar-implementation.md)

- [Docking und schwimmende Symbolleisten](../mfc/docking-and-floating-toolbars.md)

- [QuickInfos für die Symbolleiste](../mfc/toolbar-tool-tips.md)

- Die Klassen [CToolBar](../mfc/reference/ctoolbar-class.md) und [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Arbeiten mit der Symbolleistensteuerung](../mfc/working-with-the-toolbar-control.md)

- [Verwenden Ihrer alten Symbolleisten](../mfc/using-your-old-toolbars.md)

## <a name="see-also"></a>Siehe auch

[Implementieren der MFC-Symbolleiste](../mfc/mfc-toolbar-implementation.md)
