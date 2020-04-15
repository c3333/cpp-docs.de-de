---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Methoden'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], stock methods
- MFC ActiveX controls [MFC], methods
- DoClick method [MFC]
ms.assetid: bc4fad78-cabd-4cc0-a798-464b1a682f0b
ms.openlocfilehash: ec59ccc0cbd48fc3114eb2dc0833dd3dd65691de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364672"
---
# <a name="mfc-activex-controls-adding-stock-methods"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Methoden

Eine Lagermethode unterscheidet sich von einer benutzerdefinierten Methode dadurch, dass sie bereits von der Klasse [COleControl](../mfc/reference/colecontrol-class.md)implementiert wurde. `COleControl` Enthält beispielsweise eine vordefinierte Memberfunktion, die die Refresh-Methode für ihr Steuerelement unterstützt. Der Dispatch-Map-Eintrag für diese Bestandsmethode ist DISP_STOCKFUNC_REFRESH.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

`COleControl`unterstützt zwei Bestandsmethoden: DoClick und Refresh. Die Aktualisierung wird vom Benutzer des Steuerelements aufgerufen, um die Darstellung des Steuerelements sofort zu aktualisieren. DoClick wird aufgerufen, um das Click-Ereignis des Steuerelements zu ausgelöst.

|Methode|Dispatch-Map-Eintrag|Comment|
|------------|------------------------|-------------|
|`DoClick`|**DISP_STOCKPROP_DOCLICK( )**|Löst ein Click-Ereignis aus.|
|`Refresh`|**DISP_STOCKPROP_REFRESH( )**|Aktualisiert sofort das Erscheinungsbild des Steuerelements.|

## <a name="adding-a-stock-method-using-the-add-method-wizard"></a><a name="_core_adding_a_stock_method_using_classwizard"></a>Hinzufügen einer Lagermethode mithilfe des Assistenten zum Hinzufügen von Methoden

Das Hinzufügen einer Lagermethode ist mit dem Assistenten zum Hinzufügen von [Methoden](../ide/add-method-wizard.md)einfach. Das folgende Verfahren veranschaulicht das Hinzufügen der Refresh-Methode zu einem Steuerelement, das mit dem MFC ActiveX Control Wizard erstellt wurde.

#### <a name="to-add-the-stock-refresh-method-using-the-add-method-wizard"></a>So fügen Sie die Bestandsaktualisierungsmethode mithilfe des Assistenten zum Hinzufügen von Methoden hinzu

1. Laden Sie das Steuerelementprojekt.

1. Erweitern Sie in der Klassenansicht den Bibliotheksknoten des Steuerelements.

1. Klicken Sie mit der rechten Maustaste auf den Schnittstellenknoten des Steuerelements (den zweiten Knoten des Bibliotheksknotens), um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Methode hinzufügen**.

   Dadurch wird der Assistenten zum Hinzufügen von Methoden geöffnet.

1. Klicken Sie im Feld **Methodenname** auf **Aktualisieren**.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-method-wizard-changes-for-stock-methods"></a><a name="_core_classwizard_changes_for_stock_methods"></a>Methoden-Assistenten-Änderungen für Aktienmethoden hinzufügen

Da die Stock Refresh-Methode von der Basisklasse des Steuerelements unterstützt wird, ändert der **Add-Methoden-Assistent** die Klassendeklaration des Steuerelements in keiner Weise. Es fügt einen Eintrag für die Methode zur Dispatchzuordnung des Steuerelements und zu seiner hinzu. IDL-Datei. Die folgende Zeile wird der Dispatchzuordnung des Steuerelements hinzugefügt, die sich in ihrer Implementierung (. CPP)-Datei:

[!code-cpp[NVC_MFC_AxUI#16](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_1.cpp)]

Dadurch wird die Refresh-Methode für die Benutzer des Steuerelements verfügbar.

Die folgende Zeile wird der des Steuerelements hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#17](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-methods_2.idl)]

Diese Zeile weist der Refresh-Methode eine bestimmte ID-Nummer zu.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)
