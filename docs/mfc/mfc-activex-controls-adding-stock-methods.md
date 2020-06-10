---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Methoden'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: 42d8dfecd32b4aecd0daa4034497ec9abff6d11a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619940"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Methoden

Eine Aktien Methode unterscheidet sich von einer benutzerdefinierten Methode darin, dass Sie bereits durch die Klasse [COleControl](reference/colecontrol-class.md)implementiert ist. `COleControl`Enthält z. b. eine vordefinierte Member-Funktion, die die Aktualisierungs Methode für das Steuerelement unterstützt. Der dispatchzuordnungseintrag für diese Aktien Methode ist DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

`COleControl`unterstützt zwei Aktien Methoden: DoClick und Refresh. Die Aktualisierung wird vom Benutzer des Steuer Elements aufgerufen, um die Darstellung des Steuer Elements sofort zu aktualisieren. DoClick wird aufgerufen, um das Click-Ereignis des Steuer Elements auszulösen.

|Methode|Dispatch-Zuordnungs Eintrag|Kommentar|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK ()**|Löst ein Click-Ereignis aus.|
|`Refresh`|**DISP_STOCKPROP_REFRESH ()**|Aktualisiert sofort die Darstellung des Steuer Elements.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Hinzufügen einer Aktien Methode mithilfe des Assistenten zum Hinzufügen von Methoden

Das Hinzufügen einer Aktien Methode ist einfach mithilfe des [Assistenten zum Hinzufügen von Methoden](../ide/add-method-wizard.md). Das folgende Verfahren veranschaulicht das Hinzufügen der Aktualisierungs Methode zu einem Steuerelement, das mit dem MFC-ActiveX-Steuerelement-Assistenten

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>So fügen Sie die Stock Refresh-Methode mithilfe des Assistenten zum Hinzufügen von Methoden

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Methode hinzufügen**.

   Daraufhin wird der Assistent zum Hinzufügen von Methoden geöffnet.

1. Klicken Sie im Feld **Methoden Name** auf **Aktualisieren**.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Hinzufügen von Methoden-Assistenten Änderungen für Aktien Methoden

Da die Stock Refresh-Methode von der-Basisklasse des Steuer Elements unterstützt wird, ändert der **Assistent zum Hinzufügen von Methoden** die-Klassen Deklaration des Steuer Elements in keiner Weise. Es fügt einen Eintrag für die-Methode zur dispatchmap des Steuer Elements und zum zugehörigen hinzu. IDL-Datei. Die folgende Zeile wird der Dispatchzuordnung des-Steuer Elements hinzugefügt, die sich in der-Implementierung befindet (. Cpp-Datei:

[!code-cpp[NVC_MFC_AxUI#16](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Dadurch ist die Aktualisierungs Methode für die Benutzer des Steuer Elements verfügbar.

Die folgende Zeile wird dem des-Steuer Elements hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#17](codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Diese Zeile weist der Aktualisierungs Methode eine bestimmte ID-Nummer zu.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)
