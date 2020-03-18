---
title: Verwenden von CSpinButtonCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: 775668426cd11e20a4c863f07a964935d0d5420f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447184"
---
# <a name="using-cspinbuttonctrl"></a>Verwenden von CSpinButtonCtrl

Das *Drehfeld* -Steuerelement (auch als *auf-ab-* Steuerelement bezeichnet) stellt ein paar von Pfeilen bereit, auf die ein Benutzer klicken kann, um einen Wert anzupassen. Dieser Wert wird als *aktuelle Position*bezeichnet. Die Position bleibt im Bereich der Drehfeld Schaltfläche. Wenn der Benutzer auf den Pfeil nach oben klickt, wird die Position nach oben verschoben. Wenn der Benutzer auf den Pfeil nach unten klickt, wird die Position auf den Minimalpunkt verschoben.

Das Drehfeld-Steuerelement wird in MFC durch die [CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md) -Klasse dargestellt.

> [!NOTE]
>  Standardmäßig ist für den Bereich für die Dreh Schaltfläche der Höchstwert auf NULL (0) und der Minimalwert auf 100 festgelegt. Da der Höchstwert kleiner als der minimale Wert ist, wird durch Klicken auf den Pfeil nach oben die Position verringert, und durch Klicken auf den Pfeil nach unten wird er vergrößert. Verwenden Sie [CSpinButtonCtrl:: ctrange](../mfc/reference/cspinbuttonctrl-class.md#setrange) , um diese Werte anzupassen.

In der Regel wird die aktuelle Position in einem Begleit Steuerelement angezeigt. Das Begleit Steuerelement wird als *Buddy-Fenster*bezeichnet. Eine Abbildung eines Drehfeld-Steuer Elements finden [Sie unter Informationen zu auf-ab-Steuerelementen](/windows/win32/Controls/up-down-controls) in der Windows SDK.

Um ein Drehfeld-Steuerelement und ein Bearbeitungs Steuerelement-Buddy-Fenster zu erstellen, ziehen Sie in Visual Studio zuerst ein Bearbeitungs Steuerelement in das Dialogfeld oder Fenster, und ziehen Sie dann ein Drehfeld. Wählen Sie das Drehfeld-Steuerelement **aus, und**legen Sie dessen **autobuddy** fest, und **legen** Sie die Eigenschaften der Legen Sie außerdem die **Alignment** -Eigenschaft fest. **Rechts** bündig ist am häufigsten. Mit diesen Einstellungen wird das Bearbeitungs Steuerelement als Buddy-Fenster festgelegt, da es direkt vor dem Bearbeitungs Steuerelement in der Aktivier Reihenfolge steht. Das Bearbeitungs Steuerelement zeigt ganze Zahlen an, und das Drehfeld-Steuerelement wird auf der rechten Seite des Bearbeitungs Steuer Elements eingebettet. Optional können Sie den gültigen Bereich des Drehfeld-Steuer Elements mithilfe der [CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) -Methode festlegen. Es sind keine Ereignishandler erforderlich, um zwischen dem Drehfeld-Steuerelement und dem Buddy-Fenster zu kommunizieren, da Sie Daten direkt austauschen. Wenn Sie ein Drehfeld-Steuerelement für einen anderen Zweck verwenden, z. b. um eine Sequenz von Fenstern oder Dialogfeldern zu durchsuchen, fügen Sie einen Handler für die UDN_DELTAPOS Nachricht hinzu, und führen Sie dort Ihre benutzerdefinierte Aktion aus.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Drehfeld-Schaltflächenstile](../mfc/spin-button-styles.md)

- [Memberfunktionen für das Drehfeldsteuerelement](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>Weitere Informationen

[Kontrollen](../mfc/controls-mfc.md)
