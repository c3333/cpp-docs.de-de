---
title: Erstellen eigener Dialogfeldklassen
ms.date: 09/06/2019
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
ms.openlocfilehash: fab75268e39d75b67db435ebb8d0af6c0b8371fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620502"
---
# <a name="creating-your-dialog-class"></a>Erstellen eigener Dialogfeldklassen

Erstellen Sie für jedes Dialogfeld in Ihrem Programm eine neue Dialogfeld Klasse, um mit der Dialogfeld Ressource zu arbeiten.

Durch das [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md) wird erläutert, wie eine neue Dialogfeld Klasse erstellt wird. Wenn Sie eine Dialogfeld Klasse mit dem [Klassen-Assistenten](reference/mfc-class-wizard.md)erstellen, werden die folgenden Elemente in die von Ihnen angegebenen h-und CPP-Dateien geschrieben:

In der. h-Datei:

- Eine Klassen Deklaration für die Dialogfeld Klasse. Die-Klasse wird von [CDialog](reference/cdialog-class.md)abgeleitet.

In der CPP-Datei:

- Eine Meldungs Zuordnung für die-Klasse.

- Ein Standardkonstruktor für das Dialogfeld.

- Eine außer Kraft setzung der [DoDataExchange](reference/cwnd-class.md#dodataexchange) -Member-Funktion. Bearbeiten Sie diese Funktion. Sie wird für Dialog Datenaustausch und Validierungs Funktionen verwendet, die weiter unten unter [Dialog Datenaustausch und Validierung](dialog-data-exchange-and-validation.md)beschrieben werden.

## <a name="see-also"></a>Siehe auch

[Erstellen einer Dialog Feld Klasse mit Code-Assistenten](creating-a-dialog-class-with-code-wizards.md)<br/>
[Arbeiten mit Dialogfeldern in MFC](life-cycle-of-a-dialog-box.md)
