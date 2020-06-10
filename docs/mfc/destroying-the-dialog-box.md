---
title: Zerstören des Dialogfelds
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: 9b1244b03dc3f6f418730dd782050448f3bf8934
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621914"
---
# <a name="destroying-the-dialog-box"></a>Zerstören des Dialogfelds

Modale Dialogfelder werden normalerweise auf dem Stapel Rahmen erstellt und zerstört, wenn die Funktion, die Sie erstellt hat, endet. Der Dekonstruktor des Dialog Objekts wird aufgerufen, wenn das Objekt den Gültigkeitsbereich verlässt.

Dialogfelder ohne Modus werden normalerweise erstellt und im Besitz einer übergeordneten Ansicht oder eines Rahmen Fensters, – das Hauptrahmen Fenster der Anwendung oder ein Dokument Rahmen Fenster. Der standardmäßige [OnClose](reference/cwnd-class.md#onclose) -Handler ruft [DestroyWindow](reference/cwnd-class.md#destroywindow)auf, wodurch das Dialogfeld Fenster zerstört wird. Wenn das Dialogfeld eigenständig und ohne Zeiger darauf oder eine andere besondere Besitz Semantik steht, sollten Sie [PostNcDestroy](reference/cwnd-class.md#postncdestroy) überschreiben, um das C++ Dialog Objekt zu zerstören. Sie sollten [OnCancel](reference/cdialog-class.md#oncancel) auch überschreiben und `DestroyWindow` innerhalb dieses Aufrufes abrufen. Wenn dies nicht der Fall ist, sollte der Besitzer des Dialog Felds das C++-Objekt zerstören, wenn es nicht mehr benötigt wird.

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
