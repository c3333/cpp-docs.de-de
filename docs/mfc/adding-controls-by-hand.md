---
title: Manuelles Hinzufügen von Steuerelementen
ms.date: 11/04/2016
helpviewer_keywords:
- Windows common controls [MFC], adding
- dialog box controls [MFC], adding to dialog boxes
- controlling input focus
- input focus control
- focus, controlling input [MFC]
- controls [MFC], adding to dialog boxes
- common controls [MFC], adding
ms.assetid: bc843e59-0c51-4b5b-8bf2-343f716469d2
ms.openlocfilehash: 4efd1c23c7e4d6f7d8e6fa9fe046f8de11c825a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626539"
---
# <a name="adding-controls-by-hand"></a>Manuelles Hinzufügen von Steuerelementen

Sie können [einem Dialogfeld mit dem Dialog-Editor Steuerelemente hinzufügen](using-the-dialog-editor-to-add-controls.md) oder Sie selbst mit Code hinzufügen.

Wenn Sie selbst ein Steuerelement Objekt erstellen möchten, Betten Sie in der Regel das C++-Steuerelement Objekt in ein C++-Dialogfeld oder Rahmen Fenster Objekt ein. Wie viele andere Objekte im Framework erfordern Steuerelemente zweistufige Konstruktion. Sie sollten die **Create** Member-Funktion des Steuer Elements als Teil der Erstellung des übergeordneten Dialog Felds oder des Rahmen Fensters aufzurufen. In Dialogfeldern wird dies normalerweise in [OnInitDialog](reference/cdialog-class.md#oninitdialog)und für Rahmen Fenster in [OnCreate](reference/cwnd-class.md#oncreate)vorgenommen.

Im folgenden Beispiel wird gezeigt, wie Sie ein `CEdit` -Objekt in der Klassen Deklaration einer abgeleiteten Dialog Klasse deklarieren und dann die `Create` Member-Funktion in aufzurufen `OnInitDialog` . Da das- `CEdit` Objekt als eingebettetes Objekt deklariert ist, wird es automatisch erstellt, wenn das Dialog Objekt erstellt wird, aber es muss dennoch mit seiner eigenen Member-Funktion initialisiert werden `Create` .

[!code-cpp[NVC_MFCControlLadenDialog#1](codesnippet/cpp/adding-controls-by-hand_1.h)]

Die folgende `OnInitDialog` Funktion richtet ein Rechteck ein und ruft dann `Create` auf, um das Windows-Bearbeitungs Steuerelement zu erstellen und es an das nicht initialisierte Objekt anzufügen `CEdit` .

[!code-cpp[NVC_MFCControlLadenDialog#2](codesnippet/cpp/adding-controls-by-hand_2.cpp)]

Nachdem Sie das Edit-Objekt erstellt haben, können Sie den Eingabefokus auch auf das-Steuerelement festlegen, indem Sie die-Element `SetFocus` Funktion aufrufen. Schließlich wird 0 von zurückgegeben, `OnInitDialog` um anzuzeigen, dass Sie den Fokus festgelegt haben. Wenn Sie einen Wert ungleich 0 (null) zurückgeben, legt der Dialog-Manager den Fokus auf das erste Steuerelement in der Liste der Dialogfeld Elemente fest. In den meisten Fällen empfiehlt es sich, den Dialogfeldern mit dem Dialog-Editor Steuerelemente hinzuzufügen.

## <a name="see-also"></a>Siehe auch

[Erstellen und Verwenden von Steuerelementen](making-and-using-controls.md)<br/>
[Steuerelemente](controls-mfc.md)<br/>
[CDialog:: OnInitDialog](reference/cdialog-class.md#oninitdialog)
