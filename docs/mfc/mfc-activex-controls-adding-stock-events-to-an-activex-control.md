---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Ereignissen zu einem ActiveX-Steuerelement'
ms.date: 11/04/2016
f1_keywords:
- EVENT__STOCK_ERROR
- EVENT__STOCK_READYSTATECHANGE
- ReadyStateChange
- EVENT__STOCK_MOUSEMOVE
- EVENT__STOCK_MOUSEUP
- EVENT__STOCK_DBLCLICK
- KeyPress
- EVENT__STOCK_KEYDOWN
- EVENT__STOCK
- EVENT__STOCK_MOUSEDOWN
- EVENT__STOCK_KEYPRESS
- EVENT__STOCK_CLICK
- EVENT__STOCK_KEYUP
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- KeyPress event
- FireDblClick event
- FireMouseDown event
- events [MFC], stock
- FireKeyPress event
- EVENT_STOCK_MOUSEMOVE event
- EVENT_STOCK_CLICK event
- FireClick event
- FireKeyUp event
- FireMouseUp event
- EVENT_STOCK_ERROREVENT event
- EVENT_STOCK_KEYDOWN event
- EVENT_STOCK_MOUSEDOWN event
- EVENT_STOCK_KEYPRESS macro [MFC]
- EVENT_STOCK_KEYUP event
- EVENT_STOCK_DBLCLICK event
- FireError event
- FireKeyDown event
- ReadyStateChange event
- EVENT_STOCK_MOUSEUP event
- FireMouseMove event
- EVENT_STOCK prefix
- EVENT_STOCK_READYSTATECHANGE event
- EVENT_STOCK_KEYPRESS event
ms.assetid: 3eeadc67-4b3d-4444-8caa-53054073988a
ms.openlocfilehash: 79cd4fc572e55c67cc5a2cfe3a00e04f2a4a7850
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364686"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Ereignissen zu einem ActiveX-Steuerelement

Bestandsereignisse unterscheiden sich von benutzerdefinierten Ereignissen dadurch, dass sie automatisch von der Klasse [COleControl](../mfc/reference/colecontrol-class.md)ausgelöst werden. `COleControl`enthält vordefinierte Memberfunktionen, die Ereignisse aus allgemeinen Aktionen ausfeuern. Einige häufige Aktionen, die von `COleControl` implementiert werden, umfassen Ein- und Doppelklicks auf das Steuerelement, Tastaturereignisse und Änderungen im Zustand der Maustasten. Ereigniskarteneinträgen für Bestandsereignisse wird immer das Präfix EVENT_STOCK vorangestellt.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a>Vom Add-Event-Assistenten unterstützte Bestandsereignisse

Die `COleControl` Klasse bietet zehn Bestandsereignisse, die in der folgenden Tabelle aufgeführt sind. Sie können die gewünschten Ereignisse in Ihrem Steuerelement mithilfe des [Assistenten zum Hinzufügen](../ide/add-event-wizard.md)von Ereignissen angeben.

### <a name="stock-events"></a>Stock Events

|Ereignis|Brennfunktion|Kommentare|
|-----------|---------------------|--------------|
|Klicken Sie auf |**void FireClick( )**|Wird ausgelöst, wenn das Steuerelement die Maus erfasst, wird eine **beliebige BUTTONUP-Nachricht** (links, mitte oder rechts) empfangen, und die Schaltfläche wird über das Steuerelement freigegeben. Die Stock MouseDown- und MouseUp-Ereignisse treten vor diesem Ereignis auf.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_CLICK( )**|
|Dblclick|**void FireDblClick( )**|Ähnlich wie Click, aber ausgelöst, wenn eine **BUTTONDBLCLK-Nachricht** empfangen wird.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_DBLCLICK( )**|
|Fehler|**void FireError( SCODE***scode* **, LPCSTR** `lpszDescription` , **UINT**`nHelpID`**= 0 )**        |Wird ausgelöst, wenn ein Fehler innerhalb des ActiveX-Steuerelements außerhalb des Bereichs eines Methodenaufrufs oder Eigenschaftenzugriffs auftritt.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_ERROREVENT( )**|
|KeyDown|**void FireKeyDown( kurz** `nChar` **, kurz**`nShiftState`**)**      |Wird ausgelöst, wenn eine `WM_SYSKEYDOWN` oder `WM_KEYDOWN` eine Nachricht empfangen wird.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_KEYDOWN( )**|
|Keypress|**void FireKeyPress( kurz** <strong>\*</strong> `pnChar` **)**    |Wird ausgelöst, wenn eine `WM_CHAR` Nachricht empfangen wird.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_KEYPRESS( )**|
|KeyUp|**void FireKeyUp( kurz** `nChar` **, kurz**`nShiftState`**)**      |Wird ausgelöst, wenn eine `WM_SYSKEYUP` oder `WM_KEYUP` eine Nachricht empfangen wird.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_KEYUP( )**|
|Mousedown|**void FireMouseDown( kurz** `nButton` **, kurz** `nShiftState` **, float***x* **, float***y***)**          |Wird ausgelöst, wenn **BUTTONDOWN** (links, mitte oder rechts) empfangen wird. Die Maus wird unmittelbar vor dem Ausfeuern dieses Ereignisses erfasst.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_MOUSEDOWN( )**|
|Mousemove|**void FireMouseMove( kurz** `nButton` **, kurz** `nShiftState` **, float***x* **, float***y***)**          |Wird ausgelöst, wenn eine WM_MOUSEMOVE Nachricht empfangen wird.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_MOUSEMOVE( )**|
|Mouseup|**void FireMouseUp( kurz** `nButton` **, kurz** `nShiftState` **, float***x* **, float***y***)**          |Wird ausgelöst, wenn **BUTTONUP** (links, mitte oder rechts) empfangen wird. Die Mausaufnahme wird veröffentlicht, bevor dieses Ereignis ausgelöst wird.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_MOUSEUP( )**|
|ReadyStateChange|**void FireReadyStateChange( )**|Wird ausgelöst, wenn ein Steuerelement aufgrund der empfangenen Datenmenge in den nächsten bereiten Zustand wechselt.<br /><br /> Ereigniskarteneintrag: **EVENT_STOCK_READYSTATECHANGE( )**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a>Hinzufügen eines Stock-Ereignisses mithilfe des Assistenten zum Hinzufügen von Ereignis

Das Hinzufügen von Bestandsereignissen erfordert weniger Arbeit als das Hinzufügen benutzerdefinierter `COleControl`Ereignisse, da das Auslösen des tatsächlichen Ereignisses automatisch von der Basisklasse behandelt wird. Mit dem folgenden Verfahren wird einem Steuerelement, das mit dem [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md)entwickelt wurde, ein Bestandsereignis hinzugefügt. Das Ereignis, das als KeyPress bezeichnet wird, wird ausgelöst, wenn eine Taste gedrückt wird und das Steuerelement aktiv ist. Dieses Verfahren kann auch verwendet werden, um andere Bestandsereignisse hinzuzufügen. Ersetzen Sie den ausgewählten Bestandsereignisnamen für KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>So fügen Sie das KeyPress-Aktienereignis mithilfe des Add-Ereignis-Assistenten hinzu

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie in der Klassenansicht mit der rechten Maustaste auf Ihre ActiveX-Steuerelementklasse, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Ereignis hinzufügen**.

   Dadurch wird der Assistenten zum Hinzufügen von Ereignisen geöffnet.

1. Wählen Sie `KeyPress`in der Dropdown-Liste **Ereignisname** aus.

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a>Hinzufügen von Ereignis-Assistenten-Änderungen für Aktienereignisse

Da Bestandsereignisse von der Basisklasse des Steuerelements verarbeitet werden, ändert der Add-Ereignis-Assistent Ihre Klassendeklaration in keiner Weise. Das Ereignis wird der Ereigniszuordnung des Steuerelements hinzugefügt und ein Eintrag in seiner erstellt. IDL-Datei. Die folgende Zeile wird der Ereigniszuordnung des Steuerelements hinzugefügt, die sich in der Implementierung der Steuerelementklasse befindet (. CPP)-Datei:

[!code-cpp[NVC_MFC_AxUI#5](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Durch Hinzufügen dieses Codes wird ein KeyPress-Ereignis ausgelöst, wenn eine WM_CHAR Nachricht empfangen wird und das Steuerelement aktiv ist. Das KeyPress-Ereignis kann zu anderen Zeiten ausgelöst werden, `FireKeyPress`indem seine Löschfunktion (z. B. ) innerhalb des Steuercodes aufgerufen wird.

Der Assistent zum Hinzufügen von Ereignis fügt die folgende Codezeile zum Steuerelement hinzu. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#6](../mfc/codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Diese Zeile ordnet das KeyPress-Ereignis seiner Standard-Dispatch-ID zu und ermöglicht es dem Container, das KeyPress-Ereignis zu antizipieren.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](../mfc/reference/colecontrol-class.md)
