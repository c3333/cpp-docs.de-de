---
title: Erstellen und Anzeigen von Dialogfeldern
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
ms.openlocfilehash: 649d64f8e8b894027b9d6850b62d357d79c1dafa
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616271"
---
# <a name="creating-and-displaying-dialog-boxes"></a>Erstellen und Anzeigen von Dialogfeldern

Das Erstellen eines Dialog Objekts ist ein zweistufiges Vorgang. Erstellen Sie zuerst das Dialogfeld Objekt, und erstellen Sie dann das Dialogfeld. Modale und nicht modale Dialogfelder unterscheiden sich etwas in dem Prozess, der zum Erstellen und Anzeigen verwendet wurde. In der folgenden Tabelle ist aufgelistet, wie modale und nicht modale Dialogfelder normalerweise erstellt und angezeigt werden.

### <a name="dialog-creation"></a>Dialog Erstellung

|Dialogtyp|Erstellen|
|-----------------|----------------------|
|[Modeless](creating-modeless-dialog-boxes.md)|Erstellen `CDialog` und dann Member-Funktion aufzurufen `Create` .|
|[Aufkommen](creating-modal-dialog-boxes.md)|Erstellen `CDialog` und dann Member-Funktion aufzurufen `DoModal` .|

Wenn Sie möchten, können Sie das Dialogfeld über eine [in-Memory-Dialogfeld Vorlage](using-a-dialog-template-in-memory.md) erstellen, die Sie erstellt haben, anstatt aus einer Dialogfeld Vorlagen Ressource. Dies ist jedoch ein erweitertes Thema.

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
