---
title: Bearbeiten des Statussteuerelements
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: 3e3521a82854a85062f9b06bc33eb268d4b9c7a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622437"
---
# <a name="manipulating-the-progress-control"></a>Bearbeiten des Statussteuerelements

Es gibt drei Möglichkeiten, um die aktuelle Position eines Fortschritts Steuer Elements ([CProgressCtrl](reference/cprogressctrl-class.md)) zu ändern.

- Die Position kann durch eine voreingestellte Inkrement-Menge geändert werden.

- Die Position kann um einen beliebigen Betrag geändert werden.

- Die Position kann in einen bestimmten Wert geändert werden.

### <a name="to-change-the-position-by-a-preset-amount"></a>So ändern Sie die Position um einen vordefinierten Betrag

1. Verwenden Sie die Funktion [SetStep](reference/cprogressctrl-class.md#setstep) Member, um den Inkrement-Wert festzulegen. Standardmäßig ist dieser Wert 10. Dieser Wert wird in der Regel als eine der Anfangseinstellungen für das-Steuerelement festgelegt. Der Schrittwert kann negativ sein.

1. Verwenden Sie die [StepIt](reference/cprogressctrl-class.md#stepit) -Member-Funktion, um die Position zu erhöhen. Dies bewirkt, dass das Steuerelement neu gezeichnet wird.

    > [!NOTE]
    >  `StepIt`bewirkt, dass die Position eingebunden wird. Wenn z. b. ein Bereich von 1 -100, ein Schritt von 20 und eine Position 90 ist, `StepIt` wird die Position auf 10 festgelegt.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>So ändern Sie die Position um einen beliebigen Betrag

1. Verwenden Sie die [OffsetPos](reference/cprogressctrl-class.md#offsetpos) -Member-Funktion, um die Position zu ändern. `OffsetPos`akzeptiert negative Werte.

    > [!NOTE]
    >  `OffsetPos`wird im Gegensatz zu `StepIt` nicht in die-Position eingebunden. Die neue Position wird so angepasst, dass Sie im Bereich bleibt.

### <a name="to-change-the-position-to-a-specific-value"></a>So ändern Sie die Position in einen bestimmten Wert

1. Verwenden Sie die Funktion [SetPos](reference/cprogressctrl-class.md#setpos) -Member, um die Position auf einen bestimmten Wert festzulegen. Bei Bedarf wird die neue Position so angepasst, dass Sie innerhalb des Bereichs liegt.

In der Regel wird das Status Steuerelement nur für die Ausgabe verwendet. Verwenden Sie [GetPos](reference/cprogressctrl-class.md#getpos), um die aktuelle Position ohne Angabe eines neuen Werts zu erhalten.

## <a name="see-also"></a>Siehe auch

[Verwenden von CProgressCtrl](using-cprogressctrl.md)<br/>
[Steuerelemente](controls-mfc.md)
