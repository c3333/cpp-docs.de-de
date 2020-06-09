---
title: Verwenden der Schaltfläche „Anwenden“
ms.date: 11/04/2016
helpviewer_keywords:
- Apply button in property sheet
- property sheets, Apply button
ms.assetid: 7e977015-59b8-406f-b545-aad0bfd8d55b
ms.openlocfilehash: cd1254a31491e713513f0db0d4cf87baddd9bb23
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618612"
---
# <a name="handling-the-apply-button"></a>Verwenden der Schaltfläche „Anwenden“

Eigenschaften Blätter verfügen über eine Funktion, die Standard Dialogfelder nicht enthalten: Sie ermöglichen es dem Benutzer, Änderungen anzuwenden, die Sie vor dem Schließen des Eigenschaften Blatts vorgenommen haben. Dies erfolgt mithilfe der Schaltfläche anwenden. In diesem Artikel werden Methoden erläutert, die Sie zum ordnungsgemäßen implementieren dieses Features verwenden können.

Modale Dialogfelder wenden die Einstellungen in der Regel auf ein externes Objekt an, wenn der Benutzer auf OK klickt, um das Dialogfeld zu schließen. Das gleiche gilt für ein Eigenschaften Blatt: Wenn der Benutzer auf OK klickt, werden die neuen Einstellungen im Eigenschaften Blatt wirksam.

Möglicherweise möchten Sie jedoch dem Benutzer gestatten, Einstellungen zu speichern, ohne das Dialogfeld Eigenschaften Blatt schließen zu müssen. Dies ist die Funktion der Schaltfläche anwenden. Die Schaltfläche anwenden wendet die aktuellen Einstellungen auf allen Eigenschaften Seiten auf das externe Objekt an, anstatt nur die aktuellen Einstellungen der aktuell aktiven Seite anzuwenden.

Standardmäßig ist die Schaltfläche Anwenden immer deaktiviert. Sie müssen Code schreiben, um die Schaltfläche anwenden zu den entsprechenden Zeiten zu aktivieren, und Sie müssen Code schreiben, um die Auswirkung von Apply zu implementieren, wie unten erläutert.

Wenn Sie dem Benutzer nicht die Apply-Funktionalität anbieten möchten, ist es nicht erforderlich, die Schaltfläche anwenden zu entfernen. Sie können Sie deaktiviert lassen, wie es bei Anwendungen der Fall ist, die in zukünftigen Versionen von Windows eine standardmäßige Unterstützung für Eigenschaften Blätter verwenden.

Um eine Seite als geändert zu melden und die Schaltfläche anwenden zu aktivieren, geben Sie an `CPropertyPage::SetModified( TRUE )` . Wenn einer der Seiten geändert wird, bleibt die Schaltfläche anwenden aktiviert, unabhängig davon, ob die derzeit aktive Seite geändert wurde.

Sie sollten [CPropertyPage:: SetModified](reference/cpropertypage-class.md#setmodified) aufrufen, wenn der Benutzereinstellungen auf der Seite ändert. Eine Möglichkeit, zu erkennen, wenn ein Benutzer eine Einstellung auf der Seite ändert, ist die Implementierung von Änderungs Benachrichtigungs Handlern für jedes der Steuerelemente auf der Eigenschaften Seite, z. b. **EN_CHANGE** oder **BN_CLICKED**.

Zum Implementieren der Auswirkung der Schaltfläche anwenden muss das Eigenschaften Blatt seinen Besitzer oder ein anderes externes Objekt in der Anwendung anweisen, die aktuellen Einstellungen auf den Eigenschaften Seiten anzuwenden. Gleichzeitig sollte auf dem Eigenschaften Blatt die Schaltfläche anwenden deaktiviert werden, indem `CPropertyPage::SetModified( FALSE )` für alle Seiten aufgerufen wird, die Ihre Änderungen auf das externe Objekt angewendet haben.

Ein Beispiel für diesen Prozess finden Sie in der MFC-Beispiel [PROPDLG](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Siehe auch

[Eigenschaften Blätter](property-sheets-mfc.md)
