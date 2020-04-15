---
title: Verwenden von CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 6f72601d3813f36e4a99b9ab04f2e9383c58df94
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366486"
---
# <a name="using-cspinbuttonctrl"></a>Verwenden von CSpinButtonCtrl

Das *Drehtastensteuerelement* (auch als *Up-Down-Steuerelement* bezeichnet) stellt ein Paar von Pfeilen bereit, auf die ein Benutzer klicken kann, um einen Wert anzupassen. Dieser Wert wird als *aktuelle Position*bezeichnet. Die Position bleibt im Bereich der Drehtaste. Wenn der Benutzer auf den Pfeil nach oben klickt, bewegt sich die Position in Richtung des Maximums. und wenn der Benutzer auf den Abwärtspfeil klickt, bewegt sich die Position in Richtung des Minimums.

Das Drehtastensteuerelement wird in MFC durch die [CSpinButtonCtrl-Klasse](../mfc/reference/cspinbuttonctrl-class.md) dargestellt.

> [!NOTE]
> Standardmäßig ist der Bereich für die Drehschaltfläche auf Null (0) und das Minimum auf 100 festgelegt. Da der Maximalwert kleiner als der Mindestwert ist, verringert das Klicken auf den Pfeil nach oben die Position, und durch Klicken auf den Abwärtspfeil wird sie erhöht. Verwenden Sie [CSpinButtonCtrl::SetRange,](../mfc/reference/cspinbuttonctrl-class.md#setrange) um diese Werte anzupassen.

In der Regel wird die aktuelle Position in einem Begleitsteuerelement angezeigt. Das Begleitsteuerelement wird als *Buddy-Fenster*bezeichnet. Eine Abbildung eines Drehschaltflächensteuerelements finden Sie [unter Informationen zu Up-Down-Steuerelementen](/windows/win32/Controls/up-down-controls) im Windows SDK.

Um ein Drehsteuerelement und ein Bearbeitungssteuerelement-Buddy-Fenster zu erstellen, ziehen Sie in Visual Studio zunächst ein Bearbeitungssteuerelement in das Dialogfeld oder Fenster, und ziehen Sie dann ein Drehsteuerelement. Wählen Sie das Spin-Steuerelement aus, und legen Sie die **Eigenschaften "Auto Buddy"** und **"Buddy Integer"** auf **True**fest. Legen Sie auch die **Alignment-Eigenschaft** fest. **Right Align** ist typisch. Mit diesen Einstellungen wird das Bearbeitungssteuerelement als Buddy-Fenster festgelegt, da es direkt dem Bearbeitungssteuerelement in der Registerkartenreihenfolge vorangeht. Das Bearbeitungssteuerelement zeigt ganze Zahlen an, und das Spin-Steuerelement ist in der rechten Seite des Bearbeitungssteuerelements eingebettet. Optional können Sie den gültigen Bereich des Spin-Steuerelements mithilfe der [CSpinButtonCtrl::SetRange-Methode](../mfc/reference/cspinbuttonctrl-class.md#setrange) festlegen. Es sind keine Ereignishandler erforderlich, um zwischen dem Spin-Steuerelement und dem Buddy-Fenster zu kommunizieren, da sie Daten direkt austauschen. Wenn Sie ein Spin-Steuerelement für einen anderen Zweck verwenden, z. B. um eine Sequenz von Fenstern oder Dialogfeldern zu durchblättern, fügen Sie einen Handler für die UDN_DELTAPOS Nachricht hinzu, und führen Sie dort Die benutzerdefinierte Aktion aus.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Drehfeld-Schaltflächenstile](../mfc/spin-button-styles.md)

- [Memberfunktionen für das Drehfeldsteuerelement](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Siehe auch

[Steuerelemente](../mfc/controls-mfc.md)
