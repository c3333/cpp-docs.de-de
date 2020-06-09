---
title: Modale und nicht modale Dialogfelder
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 857bb3ea9e66ca0be155413faea23c0aba2abc9e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622206"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modale und nicht modale Dialogfelder

Sie können [CDialog](reference/cdialog-class.md) -Klasse verwenden, um zwei Arten von Dialogfeldern zu verwalten:

- *Modale Dialogfelder*, die erfordern, dass der Benutzer antwortet, bevor das Programm fortgesetzt wird

- Nicht *modante Dialogfelder*, die auf dem Bildschirm bleiben und jederzeit zur Verwendung verfügbar sind, aber andere Benutzeraktivitäten zulassen

Die Ressourcen Bearbeitung und die Prozeduren zum Erstellen einer Dialogfeld Vorlage sind für modale und nicht modale Dialogfelder identisch.

Zum Erstellen eines Dialog Felds für das Programm sind die folgenden Schritte erforderlich:

1. Verwenden Sie den [Dialog-Editor](../windows/dialog-editor.md) , um das Dialogfeld zu entwerfen und seine Dialogfeld Vorlagen-Ressource zu erstellen.

1. Erstellen Sie eine Dialogfeld Klasse.

1. Verbinden Sie die Steuer [Elemente der Dialogfeld Ressource mit Nachrichten Handlern](../windows/adding-event-handlers-for-dialog-box-controls.md) in der Dialogfeld Klasse.

1. Fügen Sie Datenelemente hinzu, die den Steuerelementen des Dialog Felds zugeordnet sind, und, um die Überprüfungen des [Dialog](dialog-data-exchange.md) Feld-und [Dialog Daten](dialog-data-validation.md) für die Steuerelemente anzugeben

## <a name="see-also"></a>Siehe auch

[Dialog Felder](dialog-boxes.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
