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
ms.openlocfilehash: e63e63b914b9db64139b9b81a2c749a78ac4a58f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503854"
---
# <a name="mfc-activex-controls-adding-stock-events-to-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von vordefinierten Ereignissen zu einem ActiveX-Steuerelement

Aktien Ereignisse unterscheiden sich von benutzerdefinierten Ereignissen darin, dass Sie automatisch von der Klasse [COleControl](reference/colecontrol-class.md)ausgelöst werden. `COleControl` enthält vordefinierte Element Funktionen, die Ereignisse auslösen, die sich aus häufigen Aktionen ergeben. Einige häufige Aktionen, die durch implementiert werden `COleControl` , umfassen ein-und Doppelklicks auf das Steuerelement, Tastatur Ereignisse und Änderungen im Zustand der Maustasten. Ereignis Zuordnungs Einträge für Aktien Ereignisse sind immer das EVENT_STOCK Präfix vorangestellt.

## <a name="stock-events-supported-by-the-add-event-wizard"></a><a name="_core_stock_events_supported_by_classwizard"></a> Vom Assistenten zum Hinzufügen von Ereignissen unterstützte Aktien Ereignisse

Die- `COleControl` Klasse stellt zehn Aktien Ereignisse bereit, die in der folgenden Tabelle aufgeführt sind. Mithilfe des [Assistenten zum Hinzufügen](../ide/adding-an-event-visual-cpp.md#add-event-wizard)von Ereignissen können Sie die gewünschten Ereignisse in Ihrem Steuerelement angeben.

### <a name="stock-events"></a>Aktien Ereignisse

|Ereignis|Auslösen der Funktion|Kommentare|
|-----------|---------------------|--------------|
|Klicken Sie auf|**void-"freclick ()"**|Wird ausgelöst, wenn das Steuerelement die Maus erfasst, eine beliebige **BUTTONUP** -Meldung (Links, zentriert oder rechts) empfangen wird und die Schaltfläche über dem Steuerelement losgelassen wird. Die Kurs-mousidown-und mousiup-Ereignisse treten vor diesem Ereignis auf.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_CLICK ()**|
|DblClick|**void firedblclick ()**|Vergleichbar mit Click, aber ausgelöst, wenn eine **BUTTONDBLCLK** -Nachricht empfangen wird.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_DBLCLICK ()**|
|Fehler|**void FireError (SCODE***SCODE* **, LPCSTR** `lpszDescription` **, uint** `nHelpID` **= 0)**        |Wird ausgelöst, wenn ein Fehler innerhalb des ActiveX-Steuer Elements außerhalb des Gültigkeits Bereichs eines Methoden Aufrufes oder Eigenschaften Zugriffs auftritt.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_ERROREVENT ()**|
|KeyDown|**Feuer KeyDown (kurz** `nChar` **, kurz** `nShiftState` **)** leeren      |Wird ausgelöst, wenn eine- `WM_SYSKEYDOWN` oder- `WM_KEYDOWN` Meldung empfangen wird.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_KEYDOWN ()**|
|KeyPress|**void Feuer KeyPress (Kurzform)** <strong>\*</strong> `pnChar` **)**    |Wird ausgelöst, wenn eine `WM_CHAR` Nachricht empfangen wird.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_KEYPRESS ()**|
|KeyUp|**void Feuer KeyUp (Short** `nChar` **, Short** `nShiftState` **)**      |Wird ausgelöst, wenn eine- `WM_SYSKEYUP` oder- `WM_KEYUP` Meldung empfangen wird.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_KEYUP ()**|
|MouseDown|**void firemouledown (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Wird ausgelöst, wenn ein **buttondown** (Links, zentriert oder rechts) empfangen wird. Die Maus wird unmittelbar vor dem Auslösen dieses Ereignisses aufgezeichnet.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_MOUSEDOWN ()**|
|MouseMove|**void firemoulemove (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Wird ausgelöst, wenn eine WM_MOUSEMOVE Meldung empfangen wird.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_MOUSEMOVE ()**|
|MouseUp|**void firemouberup (Short** `nButton` **, Short** `nShiftState` **, float***x* **, float***y***)**          |Wird ausgelöst, **Wenn eine beliebige** Schaltfläche (Links, zentriert oder rechts) empfangen wird. Die Maus Aufzeichnung wird freigegeben, bevor dieses Ereignis ausgelöst wird.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_MOUSEUP ()**|
|"Leserystatechange"|**void firereadystatechange ()**|Wird ausgelöst, wenn ein Steuerelement aufgrund der empfangenen Datenmenge in den nächsten Status übergeht.<br /><br /> Ereignis Zuordnungs Eintrag: **EVENT_STOCK_READYSTATECHANGE ()**|

## <a name="adding-a-stock-event-using-the-add-event-wizard"></a><a name="_core_adding_a_stock_event_using_classwizard"></a> Hinzufügen eines Aktien Ereignisses mithilfe des Assistenten zum Hinzufügen von Ereignissen

Das Hinzufügen von Aktien Ereignissen erfordert weniger Arbeit als das Hinzufügen von benutzerdefinierten Ereignissen, da das Auslösen des eigentlichen Ereignisses automatisch von der Basisklasse behandelt wird `COleControl` . Das folgende Verfahren fügt einem Steuerelement, das mit dem [MFC-ActiveX-Steuer](reference/mfc-activex-control-wizard.md)Element-Assistenten entwickelt wurde, ein Lager Ereignis hinzu. Das Ereignis, das als KeyPress bezeichnet wird, wird ausgelöst, wenn eine Taste gedrückt wird und das Steuerelement aktiv ist. Dieses Verfahren kann auch verwendet werden, um andere Aktien Ereignisse hinzuzufügen. Ersetzen Sie den Namen des ausgewählten Aktien Ereignisses durch KeyPress.

#### <a name="to-add-the-keypress-stock-event-using-the-add-event-wizard"></a>So fügen Sie das KeyPress-Aktien Ereignis mithilfe des Assistenten zum Hinzufügen von Ereignissen hinzu

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie in Klassenansicht mit der rechten Maustaste auf Ihre ActiveX-Steuerelement Klasse, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Ereignis hinzufügen**.

   Daraufhin wird der Assistent zum Hinzufügen von Ereignissen geöffnet.

1. Wählen Sie in der Dropdown Liste **Ereignis Name den Namen** aus `KeyPress` .

1. Klicken Sie auf **Fertig stellen**.

## <a name="add-event-wizard-changes-for-stock-events"></a><a name="_core_classwizard_changes_for_stock_events"></a> Hinzufügen von Änderungen des Ereignis-Assistenten für Bestands Ereignisse

Da Bestands Ereignisse von der Basisklasse des Steuer Elements behandelt werden, ändert der Assistent zum Hinzufügen von Ereignissen Ihre Klassen Deklaration in keiner Weise. Das Ereignis wird der Ereignis Zuordnung des-Steuer Elements hinzugefügt, und es wird ein Eintrag in der erstellt. IDL-Datei. Die folgende Zeile wird der Ereignis Zuordnung des-Steuer Elements hinzugefügt, die sich in der Implementierung der Steuerelement Klasse befindet. Cpp-Datei:

[!code-cpp[NVC_MFC_AxUI#5](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_1.cpp)]

Durch das Hinzufügen dieses Codes wird ein KeyPress-Ereignis ausgelöst, wenn eine WM_CHAR Nachricht empfangen wird und das Steuerelement aktiv ist. Das KeyPress-Ereignis kann zu anderen Zeitpunkten durch Aufrufen der auslösenden Funktion (z `FireKeyPress` . b.) aus dem Steuercode ausgelöst werden.

Der Assistent zum Hinzufügen von Ereignissen fügt dem des-Steuer Elements die folgende Codezeile hinzu. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#6](codesnippet/cpp/mfc-activex-controls-adding-stock-events-to-an-activex-control_2.idl)]

Diese Zeile verknüpft das KeyPress-Ereignis mit der Standard-Dispatch-ID und ermöglicht dem Container, das KeyPress-Ereignis zu erwarten.

## <a name="see-also"></a>Weitere Informationen

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)
