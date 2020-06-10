---
title: Erstellen des Steuerelements für Datum und Uhrzeit
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: 5d753b166454b795932ec8f47b0897829fab9b8e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620471"
---
# <a name="creating-the-date-and-time-picker-control"></a>Erstellen des Steuerelements für Datum und Uhrzeit

Wie das Steuerelement für die Datums-und Uhrzeit Auswahl erstellt wird, hängt davon ab, ob Sie das Steuerelement in einem Dialogfeld verwenden oder es in einem nicht Dialogfeld erstellen.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>So verwenden Sie CDateTimeCtrl direkt in einem Dialogfeld

1. Fügen Sie im Dialog-Editor der Dialogfeld Vorlagen-Ressource ein Steuerelement für die Datums-und Uhrzeit Auswahl hinzu. Gibt die Steuerelement-ID an.

1. Geben Sie im Dialogfeld "Eigenschaften" des Steuer Elements für die Datums-und Uhrzeit Auswahl alle benötigten Stile an.

1. Verwenden Sie den [Assistenten zum Hinzufügen](../ide/adding-a-member-variable-visual-cpp.md) von Element Variablen, um eine Member-Variable vom Typ [CDateTimeCtrl](reference/cdatetimectrl-class.md) mit der Control-Eigenschaft hinzuzufügen. Sie können diesen Member verwenden, um `CDateTimeCtrl` Member-Funktionen aufzurufen.

1. Verwenden Sie den [Klassen-Assistenten](reference/mfc-class-wizard.md) , um Handlerfunktionen in der Dialogfeld Klasse für beliebige [Benachrichtigungs](processing-notification-messages-in-date-and-time-picker-controls.md) Meldungen für Datums-und Zeitauswahl Steuerelemente zuzuordnen, die Sie behandeln müssen (siehe zuordnen [von Meldungen zu Funktionen](reference/mapping-messages-to-functions.md))

1. Legen Sie in [OnInitDialog](reference/cdialog-class.md#oninitdialog)alle zusätzlichen Stile für das- `CDateTimeCtrl` Objekt fest.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>So verwenden Sie CDateTimeCtrl in einem nicht-Dialogfenster

1. Deklarieren Sie das Steuerelement in der Ansicht oder in der Fenster Klasse.

1. Rufen Sie die [Create](reference/ctabctrl-class.md#create) Member-Funktion des Steuer Elements (möglicherweise in [OnInitialUpdate](reference/cview-class.md#oninitialupdate)) auf, möglicherweise so früh wie die [OnCreate](reference/cwnd-class.md#oncreate) -Handlerfunktion des übergeordneten Fensters (wenn Sie das Steuerelement Unterklassen). Legen Sie die Stile für das-Steuerelement fest.

## <a name="see-also"></a>Siehe auch

[Verwenden von CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Steuerelemente](controls-mfc.md)
