---
title: Dialogfelder
ms.date: 11/04/2016
helpviewer_keywords:
- modeless dialog boxes [MFC], MFC dialog boxes
- MFC, dialog boxes
- modal dialog boxes [MFC], MFC dialog boxes
- CDialog class [MFC], MFC dialog boxes
- MFC dialog boxes
ms.assetid: e4feea1a-8360-4ccb-9b84-507f1ccd9ef3
ms.openlocfilehash: da6a2eca7c2366e519b9bf2e809b042dc3ee2e50
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616868"
---
# <a name="dialog-boxes"></a>Dialogfelder

Anwendungen für Windows kommunizieren häufig über Dialogfelder mit dem Benutzer. [CDialog](reference/cdialog-class.md) -Klasse stellt eine Schnittstelle für die Verwaltung von Dialogfeldern bereit. mit dem Dialogfeld-Editor für Visual C++ können Sie problemlos Dialogfelder entwerfen und ihre Dialogfeld Vorlagen Ressourcen erstellen, und Code-Assistenten vereinfachen den Prozess der Initialisierung und Validierung der Steuerelemente in einem Dialogfeld und der Sammlung der vom Benutzer eingegebenen Werte.

Dialog Felder enthalten Steuerelemente, einschließlich:

- Allgemeine Windows-Steuerelemente, wie z. b. Bearbeitungsfelder, Pushbuttons, Listenfelder, Kombinations Felder, Struktur Steuerelemente, Listen Steuerelemente und Status Indikatoren.

- ActiveX-Steuerelemente.

- Vom Besitzer gezeichnete Steuerelemente: Steuerelemente, die für das Zeichnen im Dialogfeld verantwortlich sind.

Die meisten Dialogfelder sind modal, die erfordern, dass der Benutzer das Dialogfeld schließt, bevor ein anderer Teil des Programms verwendet wird. Es ist jedoch möglich, Dialogfelder ohne Modus zu erstellen, mit denen Benutzer mit anderen Fenstern arbeiten können, während das Dialogfeld geöffnet ist. MFC unterstützt beide Arten von Dialogfeldern mit der-Klasse `CDialog` . Die Steuerelemente werden mithilfe einer Dialogfeld Vorlagen-Ressource angeordnet und verwaltet, die mit dem [Dialog-Editor](../windows/dialog-editor.md)erstellt wurde.

[Eigenschaften Blätter](property-sheets-mfc.md), auch als Registerkarten Dialogfelder bezeichnet, sind Dialogfelder, die "Seiten" unterschiedlicher Dialogfeld-Steuerelemente enthalten. Jede Seite enthält den Datei Ordner "Registerkarte" oben. Wenn Sie auf eine Registerkarte klicken, wird diese Seite am Anfang des Dialog Felds angezeigt.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Beispiel: Anzeigen eines Dialogfelds mit einem Menübefehl](example-displaying-a-dialog-box-via-a-menu-command.md)

- [Dialog Feld Komponenten im Framework](dialog-box-components-in-the-framework.md)

- [Modale und nicht modale Dialogfelder](modal-and-modeless-dialog-boxes.md)

- [Eigenschaften Blätter und Eigenschaften Seiten](property-sheets-and-property-pages-mfc.md) in einem Dialogfeld

- [Erstellen der Dialogfeldressource](creating-the-dialog-resource.md)

- [Erstellen einer Dialogfeld Klasse mit Code-Assistenten](creating-a-dialog-class-with-code-wizards.md)

- [Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)

- [Dialog Datenaustausch (DDX) und Validierung (DDV)](dialog-data-exchange-and-validation.md)

- [Typsicherer Zugriff auf Steuerelemente in einem Dialogfeld](type-safe-access-to-controls-in-a-dialog-box.md)

- [Zuordnung von Windows-Meldungen zu ihrer Klasse](mapping-windows-messages-to-your-class.md)

- [Häufig überschreibbare Memberfunktionen](commonly-overridden-member-functions.md)

- [Häufig hinzugefügte Memberfunktionen](commonly-added-member-functions.md)

- [Allgemeine Dialogfeld Klassen](common-dialog-classes.md)

- [Dialog Felder in OLE](dialog-boxes-in-ole.md)

- Erstellen Sie eine Anwendung, deren Benutzeroberfläche ein Dialogfeld ist: siehe [CMNCTRL1](../overview/visual-cpp-samples.md) -oder [CMNCTRL2](../overview/visual-cpp-samples.md) -Beispiel Programme. Der Anwendungs-Assistent bietet auch diese Option.

- [Beispiele](dialog-sample-list.md)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)
