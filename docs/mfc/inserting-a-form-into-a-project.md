---
title: Einfügen eines Formulars in ein Projekt
ms.date: 11/04/2016
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
ms.openlocfilehash: 8e3162ac3917781920130bcbed23864eb90afa59
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618428"
---
# <a name="inserting-a-form-into-a-project"></a>Einfügen eines Formulars in ein Projekt

Formulare stellen einen praktischen Container für Steuerelemente bereit. Sie können ein MFC-basiertes Formular problemlos in Ihre Anwendung einfügen, sofern die Anwendung die MFC-Bibliotheken unterstützt.

### <a name="to-insert-a-form-into-your-project"></a>So fügen Sie ein Formular in das Projekt ein

1. Wählen Sie in Klassenansicht das Projekt aus, dem Sie das Formular hinzufügen möchten, und klicken Sie dann auf die Rechte Maustaste.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Klasse hinzufügen**.

   Wenn der Befehl **New Form** nicht verfügbar ist, kann das Projekt auf dem Active Template Library (ATL) basieren. Wenn Sie einem ATL-Projekt ein Formular hinzufügen möchten, müssen Sie beim ersten Erstellen des Projekts [bestimmte Einstellungen angeben](../atl/reference/application-settings-atl-project-wizard.md) .

1. Klicken Sie im **MFC** -Ordner auf **MFC-Klasse**.

1. Stellen Sie mithilfe des MFC-Klassen-Assistenten die neue Klasse von [CFormView](reference/cformview-class.md)ableiten.

Visual C++ fügt der Anwendung das Formular hinzu, indem es in den Dialog-Editor geöffnet wird, sodass Sie mit dem Hinzufügen von Steuerelementen beginnen und am Gesamtentwurf arbeiten können.

Möglicherweise möchten Sie die folgenden zusätzlichen Schritte ausführen (nicht zutreffend für Dialogfeld basierte Anwendungen):

1. Überschreiben Sie die `OnUpdate` Member-Funktion.

1. Implementieren Sie eine Member-Funktion, um Daten aus ihrer Ansicht in das Dokument zu verschieben.

1. Erstellen Sie eine `OnPrint` Member-Funktion.

## <a name="see-also"></a>Siehe auch

[Formularansichten](form-views-mfc.md)
