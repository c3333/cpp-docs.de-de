---
title: Initialisieren des Dialogfelds
ms.date: 11/04/2016
helpviewer_keywords:
- initializing dialog boxes [MFC]
- OnInitDialog method [MFC]
- modal dialog boxes [MFC], initializing
- modeless dialog boxes [MFC], initializing
- MFC dialog boxes [MFC], initializing
ms.assetid: 968142f5-19f9-4b34-a1d4-8e6412d4379b
ms.openlocfilehash: 1f8f8f7e40b1c873c4428542c628d02e250f14b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626337"
---
# <a name="initializing-the-dialog-box"></a>Initialisieren des Dialogfelds

Nachdem das Dialogfeld und alle zugehörigen Steuerelemente erstellt wurden, aber kurz bevor das Dialogfeld (eines der beiden Typen) auf dem Bildschirm angezeigt wird, wird die [OnInitDialog](reference/cdialog-class.md#oninitdialog) -Member-Funktion des Dialog Objekts aufgerufen. Bei einem modalen Dialogfeld erfolgt dies während des `DoModal` Aufrufes. Bei einem nicht modalem Dialogfeld `OnInitDialog` wird aufgerufen, wenn `Create` aufgerufen wird. Normalerweise überschreiben Sie `OnInitDialog` , um die Steuerelemente des Dialog Felds zu initialisieren, z. b. das Festlegen des Anfangs Texts eines Bearbeitungs Felds. Sie müssen die `OnInitDialog` Member-Funktion der Basisklasse `CDialog` von ihrer außer Kraft Setzung aus abrufen `OnInitDialog` .

Wenn Sie die Hintergrundfarbe des Dialog Felds (und die aller anderen Dialogfelder in der Anwendung) festlegen möchten, finden Sie weitere Informationen unter [Festlegen der Hintergrundfarbe für das Dialogfeld](setting-the-dialog-boxs-background-color.md).

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
