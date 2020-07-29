---
title: Schließen des Dialogfelds
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], closing
- dialog boxes [MFC], closing
ms.assetid: 946f5675-c482-46a4-a5dd-34fe138ffae5
ms.openlocfilehash: ef6cdaeb4cb0d7537cda980a1d2c483c53c8dc9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217973"
---
# <a name="closing-the-dialog-box"></a>Schließen des Dialogfelds

Ein modales Dialogfeld wird geschlossen, wenn der Benutzer eine seiner Schaltflächen auswählt, in der Regel die Schaltfläche OK oder die Schaltfläche Abbrechen. Wenn Sie die Schaltfläche OK oder Abbrechen auswählen, sendet Windows das Dialog Objekt eine **BN_CLICKED** -Steuerelement-Benachrichtigungs Meldung mit der ID der Schaltfläche ( **IDOK** oder **IDCANCEL**). `CDialog`stellt standardhandlerfunktionen für diese Nachrichten bereit: `OnOK` und `OnCancel` . Mit den Standard Handlern wird die `EndDialog` Member-Funktion aufgerufen, um das Dialogfenster zu schließen. Sie können auch `EndDialog` von Ihrem eigenen Code aus aufzurufen. Weitere Informationen finden Sie unter der [EndDialog](reference/cdialog-class.md#enddialog) -Member-Funktion der-Klasse `CDialog` in der *MFC-Referenz*.

Um das Schließen und Löschen eines nicht modaldialog Felds anzuordnen, überschreiben Sie `PostNcDestroy` den Operator für den Zeiger, und rufen Sie ihn **`delete`** auf **`this`** . Durch [das zerstören des Dialog](destroying-the-dialog-box.md) Felds wird erläutert, was als nächstes geschieht.

## <a name="see-also"></a>Weitere Informationen

[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
