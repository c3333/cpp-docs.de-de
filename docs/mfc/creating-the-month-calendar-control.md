---
title: Erstellen des Monatskalender-Steuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 49d21bd4ce5aae23d5fc4c74567bc1c1d5a43570
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616235"
---
# <a name="creating-the-month-calendar-control"></a>Erstellen des Monatskalender-Steuerelements

Wie das Monatskalender-Steuerelement erstellt wird, hängt davon ab, ob Sie das Steuerelement in einem Dialogfeld verwenden oder es in einem nicht Dialogfeld erstellen.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>So verwenden Sie CMonthCalCtrl direkt in einem Dialogfeld

1. Fügen Sie im Dialog-Editor der Dialogfeld Vorlagen-Ressource ein Monatskalender-Steuerelement hinzu. Gibt die Steuerelement-ID an.

1. Geben Sie alle Stile an, die im Dialogfeld "Eigenschaften" des Monatskalender-Steuer Elements erforderlich sind.

1. Verwenden Sie den [Assistenten zum Hinzufügen](../ide/adding-a-member-variable-visual-cpp.md) von Element Variablen, um eine Member-Variable vom Typ [CMonthCalCtrl](reference/cmonthcalctrl-class.md) mit der Control-Eigenschaft hinzuzufügen. Sie können diesen Member verwenden, um `CMonthCalCtrl` Member-Funktionen aufzurufen.

1. Verwenden Sie den [Klassen-Assistenten](reference/mfc-class-wizard.md) , um Handlerfunktionen in der Dialogfeld Klasse für beliebige Monats-Kalender Steuerelement-Benachrichtigungs Meldungen zuzuordnen, die Sie behandeln müssen. [Mapping Messages to Functions](reference/mapping-messages-to-functions.md)

1. Legen Sie in [OnInitDialog](reference/cdialog-class.md#oninitdialog)alle zusätzlichen Stile für das- `CMonthCalCtrl` Objekt fest.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>So verwenden Sie CMonthCalCtrl in einem nicht Dialogfeld Fenster

1. Definieren Sie das Steuerelement in der Ansicht oder in der Fenster Klasse.

1. Rufen Sie die [Create](reference/cmonthcalctrl-class.md#create) Member-Funktion des Steuer Elements (möglicherweise in [OnInitialUpdate](reference/cview-class.md#oninitialupdate)) auf, möglicherweise so früh wie die [OnCreate](reference/cwnd-class.md#oncreate) -Handlerfunktion des übergeordneten Fensters (wenn Sie das Steuerelement Unterklassen). Legen Sie die Stile für das-Steuerelement fest.

## <a name="see-also"></a>Siehe auch

[Verwenden von CMonthCalCtrl](using-cmonthcalctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
