---
title: 'MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Ereignissen'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events [MFC]
- EVENT_CUSTOM prefix [MFC]
- custom events [MFC], adding to ActiveX controls
- EVENT_CUSTOM macro [MFC]
- InCircle method [MFC]
- ClickIn event
- FireClickIn event
- COleControl class [MFC], custom events [MFC]
- Click event, custom events [MFC]
- events [MFC], ActiveX controls
- custom events [MFC]
- FireEvent method, adding custom events
ms.assetid: c584d053-1e34-47aa-958e-37d3e9b85892
ms.openlocfilehash: 8d464e5d7c9731e158e44d66d569fd1555401e17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364729"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Ereignissen

Benutzerdefinierte Ereignisse unterscheiden sich von Bestandsereignissen `COleControl`dadurch, dass sie nicht automatisch von der Klasse ausgelöst werden. Ein benutzerdefiniertes Ereignis erkennt eine bestimmte Aktion, die vom Steuerelemententwickler bestimmt wird, als Ereignis. Die Ereigniszuordnungseinträge für benutzerdefinierte Ereignisse werden durch das EVENT_CUSTOM Makro dargestellt. Im folgenden Abschnitt wird ein benutzerdefiniertes Ereignis für ein ActiveX-Steuerelementprojekt implementiert, das mit dem ActiveX Control Wizard erstellt wurde.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Hinzufügen eines benutzerdefinierten Ereignisses mit dem Assistenten zum Hinzufügen von Ereignis

Mit dem folgenden Verfahren wird ein bestimmtes benutzerdefiniertes Ereignis, ClickIn, hinzugefügt. Mit diesem Verfahren können Sie weitere benutzerdefinierte Ereignisse hinzufügen. Ersetzen Sie Ihren benutzerdefinierten Ereignisnamen und seine Parameter durch den ClickIn-Ereignisnamen und die Parameter.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>So fügen Sie das benutzerdefinierte ClickIn-Ereignis mithilfe des Assistenten zum Hinzufügen von Ereignis hinzu

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie in der **Klassenansicht**mit der rechten Maustaste auf Ihre ActiveX-Steuerelementklasse, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Ereignis hinzufügen**.

   Dadurch wird der Assistenten zum Hinzufügen von Ereignisen geöffnet.

1. Wählen Sie im Feld **Ereignisname** zuerst ein beliebiges vorhandenes Ereignis aus, klicken Sie dann auf das **benutzerdefinierte** Optionsfeld, und geben Sie dann *ClickIn ein.*

1. Geben Sie im Feld **Interner Name** den Namen der Löschfunktion des Ereignisses ein. Verwenden Sie in diesem Beispiel den Standardwert,`FireClickIn`der vom Assistenten zum Hinzufügen von Ereignis ( bereitgestellt wird.

1. Fügen Sie einen Parameter namens *xCoord* (Typ *OLE_XPOS_PIXELS*) mithilfe der Steuerelemente **Parametername** und **Parametertyp** hinzu.

1. Fügen Sie einen zweiten Parameter namens *yCoord* (Typ *OLE_YPOS_PIXELS*) hinzu.

1. Klicken Sie auf **Fertig stellen,** um das Ereignis zu erstellen.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Hinzufügen von Ereignis-Assistenten-Änderungen für benutzerdefinierte Ereignisse

Wenn Sie ein benutzerdefiniertes Ereignis hinzufügen, nimmt der Assistent zum Hinzufügen von Ereignis Änderungen an der Steuerelementklasse vor. H. CPP und . IDL-Dateien. Die folgenden Codebeispiele sind spezifisch für das ClickIn-Ereignis.

Die folgenden Zeilen werden dem Kopf (. H) Datei Ihrer Kontrollklasse:

[!code-cpp[NVC_MFC_AxUI#7](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Dieser Code deklariert eine `FireClickIn` Inlinefunktion namens [COleControl::FireEvent](../mfc/reference/colecontrol-class.md#fireevent) mit dem ClickIn-Ereignis und Parametern, die Sie mit dem Add-Ereignis-Assistenten definiert haben.

Darüber hinaus wird die folgende Zeile zur Ereigniszuordnung für das Steuerelement hinzugefügt, die sich in der Implementierung (. CPP)-Datei Ihrer Kontrollklasse:

[!code-cpp[NVC_MFC_AxUI#8](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Dieser Code ordnet das Ereignis ClickIn `FireClickIn`der Inline-Funktion zu und übergibt die Parameter, die Sie mit dem Assistenten zum Hinzufügen von Ereignis definiert haben.

Schließlich wird die folgende Zeile zu der des Steuerelements hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#9](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Diese Zeile weist dem ClickIn-Ereignis eine bestimmte ID-Nummer zu, die von der Position des Ereignisses in der Ereignisliste Desereignis-Assistent hinzufügen entnommen wird. Der Eintrag in der Ereignisliste ermöglicht es einem Container, das Ereignis zu antizipieren. Beispielsweise kann es Handlercode bereitstellen, der ausgeführt werden soll, wenn das Ereignis ausgelöst wird.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Aufrufen von FireClickIn

Nachdem Sie das benutzerdefinierte ClickIn-Ereignis mithilfe des Assistenten zum Hinzufügen von Ereignis hinzugefügt haben, müssen Sie entscheiden, wann dieses Ereignis ausgelöst werden soll. Dazu rufen Sie `FireClickIn` auf, wenn die entsprechende Aktion ausgeführt wird. Für diese Diskussion verwendet `InCircle` das Steuerelement `WM_LBUTTONDOWN` die Funktion innerhalb eines Nachrichtenhandlers, um das ClickIn-Ereignis zu ausgelöst, wenn ein Benutzer innerhalb eines kreisförmigen oder elliptischen Bereichs klickt. Mit dem folgenden `WM_LBUTTONDOWN` Verfahren wird der Handler hinzugefügt.

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>So fügen Sie einen Nachrichtenhandler mit dem Assistenten zum Hinzufügen von Ereignis hinzu

1. Laden Sie das Steuerelementprojekt.

1. Wählen Sie in der **Klassenansicht**Ihre ActiveX-Steuerelementklasse aus.

1. Im **Eigenschaftenfenster** wird eine Liste der Nachrichten angezeigt, die vom ActiveX-Steuerelement verarbeitet werden können. Für jede Nachricht, die fett angezeigt wird, ist bereits eine Handlerfunktion zugewiesen.

1. Wählen Sie die Nachricht aus, die Sie behandeln möchten. Wählen Sie in `WM_LBUTTONDOWN`diesem Beispiel die Option aus.

1. Wählen Sie ** \<** im Dropdown-Listenfeld auf der rechten Seite> OnLButtonDown hinzufügen aus.

1. Doppelklicken Sie in der **Klassenansicht** auf die neue Handlerfunktion, um zum Nachrichtenhandlercode in der Implementierung zu springen (. CPP)-Datei Ihres ActiveX-Steuerelements.

Das folgende Codebeispiel `InCircle` ruft die Funktion jedes Mal auf, wenn die linke Maustaste im Kontrollfenster angeklickt wird. Dieses Beispiel finden Sie `WM_LBUTTONDOWN` in `OnLButtonDown`der Handlerfunktion , in der [Circ-Beispielabstrakt.](../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_AxUI#10](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Wenn der Assistenten zum Hinzufügen von Ereignis nachrichtenhandler für Mausschaltflächenaktionen erstellt, wird automatisch ein Aufruf an denselben Nachrichtenhandler der Basisklasse hinzugefügt. Entfernen Sie diesen Aufruf nicht. Wenn das Steuerelement eine der Stock-Maus-Nachrichten verwendet, müssen die Nachrichtenhandler in der Basisklasse aufgerufen werden, um sicherzustellen, dass die Mauserfassung ordnungsgemäß behandelt wird.

Im folgenden Beispiel wird das Ereignis nur ausgelöst, wenn der Klick innerhalb eines kreisförmigen oder elliptischen Bereichs innerhalb des Steuerelements auftritt. Um dieses Verhalten zu erreichen, können Sie die Funktion in der `InCircle` Implementierung Ihres Steuerelements (. CPP)-Datei:

[!code-cpp[NVC_MFC_AxUI#11](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Sie müssen auch die folgende Deklaration der `InCircle` Funktion zum Header des Steuerelements hinzufügen (. H) Datei:

[!code-cpp[NVC_MFC_AxUI#12](../mfc/codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Benutzerdefinierte Ereignisse mit Aktiennamen

Sie können benutzerdefinierte Ereignisse mit demselben Namen wie Bestandsereignisse erstellen, jedoch können Sie nicht beide in demselben Steuerelement implementieren. Sie können z. B. ein benutzerdefiniertes Ereignis namens Click erstellen, das nicht ausgelöst wird, wenn das Aktienereignis Click normalerweise ausgelöst wird. Sie können dann das Click-Ereignis jederzeit auslösen, indem Sie seine Löschfunktion aufrufen.

Mit dem folgenden Verfahren wird ein benutzerdefiniertes Click-Ereignis hinzugefügt.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>So fügen Sie ein benutzerdefiniertes Ereignis hinzu, das einen Bestandsereignisnamen verwendet

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie in der **Klassenansicht**mit der rechten Maustaste auf Ihre ActiveX-Steuerelementklasse, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** und dann auf **Ereignis hinzufügen**.

   Dadurch wird der Assistenten zum Hinzufügen von Ereignisen geöffnet.

1. Wählen Sie in der Dropdown-Liste **Ereignisname** einen Bestandsereignisnamen aus. Wählen Sie in diesem Beispiel **Klicken**aus.

1. Wählen Sie für **Ereignistyp**die Option **Benutzerdefiniert**aus.

1. Klicken Sie auf **Fertig stellen,** um das Ereignis zu erstellen.

1. Rufen `FireClick` Sie an geeigneten Stellen in Ihrem Code an.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](../mfc/reference/colecontrol-class.md)
