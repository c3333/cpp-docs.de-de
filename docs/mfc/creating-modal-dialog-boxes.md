---
title: Erstellen von modalen Dialogfeldern
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed7cc94982a46e542a5174d4d46b8013cc84ffa4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622980"
---
# <a name="creating-modal-dialog-boxes"></a>Erstellen von modalen Dialogfeldern

Um ein modales Dialogfeld zu erstellen, rufen Sie einen der beiden öffentlichen Konstruktoren auf, die in [CDialog](reference/cdialog-class.md)deklariert wurden. Rufen Sie als nächstes die [DoModal](reference/cdialog-class.md#domodal) -Member-Funktion des Dialog Felds auf, um das Dialogfeld anzuzeigen, und verwalten Sie die Interaktion damit, bis der Benutzer OK oder Abbrechen auswählt. Durch diese Verwaltung von `DoModal` wird das Dialogfeld modal. Für modale Dialogfelder `DoModal` lädt die Dialogfeld Ressource.

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
