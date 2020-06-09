---
title: Formularansichten (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 94d8b7d026ee3aaf1bac9dee2226de6dd9382599
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615684"
---
# <a name="form-views-mfc"></a>Formularansichten (MFC)

Sie können jeder Visual C++ Anwendung, die die MFC-Bibliotheken unterstützt, Formulare hinzufügen, einschließlich einer [Formular basierten Anwendung](reference/creating-a-forms-based-mfc-application.md) (eine, deren Ansichts Klasse von abgeleitet ist `CFormView` ). Wenn Sie Ihre Anwendung nicht erstmalig für die Unterstützung von Formularen erstellt haben, wird Visual C++ diese Unterstützung für Sie hinzufügen, wenn Sie ein neues Formular einfügen. In einer SDI-oder MDI-Anwendung, die die standardmäßige [Dokument-/Ansichtarchitektur](document-view-architecture.md)implementiert, wird der Benutzer von Visual C++ aufgefordert, aus den verfügbaren Formularen auszuwählen, wenn der Benutzer den **neuen** Befehl auswählt (standardmäßig im Menü **Datei** ).

Wenn der Benutzer bei einer SDI-Anwendung den **neuen** Befehl auswählt, wird die aktuelle Instanz des Formulars weiterhin ausgeführt, aber es wird eine neue Instanz der Anwendung mit dem ausgewählten Formular erstellt, wenn eine solche nicht gefunden wurde. In einer MDI-Anwendung wird die aktuelle Instanz des Formulars weiterhin ausgeführt, wenn der Benutzer den **neuen** Befehl auswählt.

> [!NOTE]
> Sie können ein Formular in eine Dialogfeld basierte Anwendung einfügen (eine, deren Dialogfeld Klasse auf basiert `CDialog` und eine, in der keine Ansichts Klasse implementiert ist). Ohne die Dokument-/Ansichtsarchitektur implementiert Visual C++ die **Datei** jedoch nicht automatisch&#124;**neue** Funktionalität. Sie müssen eine Möglichkeit für den Benutzer zum Anzeigen zusätzlicher Formulare erstellen, z. b. durch Implementieren eines Dialog Felds mit Registerkarten im Registerkarten Format mit verschiedenen Eigenschaften Seiten.

Wenn Sie ein neues Formular in Ihre Anwendung einfügen, führt Visual C++ folgende Schritte aus:

- Erstellt eine-Klasse auf Grundlage einer der Formular Formatklassen, die Sie auswählen ( `CFormView` , `CRecordView` , `CDaoRecordView` oder `CDialog` ).

- Erstellt eine Dialogfeld Ressource mit entsprechenden Stilen (oder Sie können eine vorhandene Dialog Ressource verwenden, die noch keiner Klasse zugeordnet ist).

   Wenn Sie eine vorhandene Dialogfeld Ressource auswählen, müssen Sie diese Stile möglicherweise über die Seite Eigenschaften für das Dialogfeld festlegen. Stile für ein Dialogfeld müssen Folgendes umfassen:

     **WS_CHILD**= on

     **WS_BORDER**= aus

     **WS_VISIBLE**= aus

     **WS_CAPTION**= aus

Für Anwendungen, die auf der Dokument-/Ansichtsarchitektur basieren, wird der **neue Formular** Befehl (mit der rechten Maustaste in Klassenansicht) angezeigt:

- Erstellt eine `CDocument` -basierte-Klasse.

   Anstatt eine neue Klasse erstellen zu müssen, können Sie eine beliebige vorhandene `CDocument` -basierte-Klasse im Projekt verwenden.

- Generiert eine Dokument Vorlage (abgeleitet von `CDocument` ) mit Zeichen folgen-, Menü-und Symbol Ressourcen.

   Sie können auch eine neue Klasse erstellen, auf der die Vorlage basieren soll.

- Fügt `AddDocumentTemplate` im Code der Anwendung einen-Rückruf hinzu `InitInstance` .

   Visual C++ fügt diesen Code für jedes neue Formular hinzu, das Sie erstellen, wodurch das Formular der Liste der verfügbaren Formulare hinzugefügt wird, wenn der Benutzer den **neuen** Befehl auswählt. Dieser Code enthält die zugeordnete Ressourcen-ID des Formulars und die Namen der zugeordneten Dokument-, Ansichts-und Frame Klassen, die zusammen das neue Formular Objekt bilden.

   Dokumentvorlagen dienen als Verbindung zwischen Dokumenten, Rahmen Fenstern und Ansichten. Für ein einzelnes Dokument können Sie viele Vorlagen erstellen.

Weitere Informationen finden Sie unter

- [Erstellen einer Formular basierten Anwendung](reference/creating-a-forms-based-mfc-application.md)

- [Einfügen eines Formulars in ein Projekt](inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Siehe auch

[Elemente der Benutzeroberfläche](user-interface-elements-mfc.md)
