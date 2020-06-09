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
ms.openlocfilehash: 70b0e08bc638b5f630d423ec0db8a169a0119175
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619950"
---
# <a name="mfc-activex-controls-adding-custom-events"></a>MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Ereignissen

Benutzerdefinierte Ereignisse unterscheiden sich von Aktien Ereignissen darin, dass Sie nicht automatisch von der-Klasse ausgelöst werden `COleControl` . Ein benutzerdefiniertes Ereignis erkennt eine bestimmte Aktion, die vom Steuerelement Entwickler als Ereignis festgelegt wird. Die Ereignis Zuordnungs Einträge für benutzerdefinierte Ereignisse werden durch das EVENT_CUSTOM-Makro dargestellt. Der folgende Abschnitt implementiert ein benutzerdefiniertes Ereignis für ein ActiveX-Steuerelement Projekt, das mit dem ActiveX-Steuerelement-Assistenten erstellt wurde.

## <a name="adding-a-custom-event-with-the-add-event-wizard"></a><a name="_core_adding_a_custom_event_with_classwizard"></a>Hinzufügen eines benutzerdefinierten Ereignisses mit dem Assistenten zum Hinzufügen von Ereignissen

Im folgenden Verfahren wird ein bestimmtes benutzerdefiniertes Ereignis, ClickIn, hinzugefügt. Mit diesem Verfahren können Sie weitere benutzerdefinierte Ereignisse hinzufügen. Ersetzen Sie den benutzerdefinierten Ereignis Namen und die zugehörigen Parameter für den Namen und die Parameter des ClickIn-Ereignisses.

#### <a name="to-add-the-clickin-custom-event-using-the-add-event-wizard"></a>So fügen Sie das benutzerdefinierte ClickIn-Ereignis mithilfe des Assistenten zum Hinzufügen von Ereignissen

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie in **Klassenansicht**mit der rechten Maustaste auf Ihre ActiveX-Steuerelement Klasse, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Ereignis hinzufügen**.

   Daraufhin wird der Assistent zum Hinzufügen von Ereignissen geöffnet.

1. Wählen Sie im Feld **Ereignis Name** zunächst ein vorhandenes Ereignis aus, klicken Sie dann auf das Optionsfeld **Benutzer** definiert, und geben Sie dann *ClickIn*ein.

1. Geben Sie im Feld **interner Name** den Namen der auslösenden Funktion des Ereignisses ein. Verwenden Sie für dieses Beispiel den Standardwert, der vom Assistenten zum Hinzufügen von Ereignissen () bereitgestellt wird `FireClickIn` .

1. Fügen Sie einen Parameter mit dem Namen *xcoord* (Type *OLE_XPOS_PIXELS*) hinzu, indem Sie die **Parameter Name** und **Parametertyp** verwenden.

1. Fügen Sie einen zweiten Parameter namens *yCoord* (Type *OLE_YPOS_PIXELS*) hinzu.

1. Klicken Sie auf **Fertig** stellen, um das Ereignis zu erstellen.

## <a name="add-event-wizard-changes-for-custom-events"></a><a name="_core_classwizard_changes_for_custom_events"></a>Hinzufügen von Ereignis-Assistenten Änderungen für benutzerdefinierte Ereignisse

Wenn Sie ein benutzerdefiniertes Ereignis hinzufügen, nimmt der Assistent zum Hinzufügen von Ereignissen Änderungen an der Steuerelement Klasse vor H,. Cpp und. IDL-Dateien. Die folgenden Codebeispiele sind spezifisch für das ClickIn-Ereignis.

Die folgenden Zeilen werden dem-Header hinzugefügt (. H) der Steuerelement Klasse:

[!code-cpp[NVC_MFC_AxUI#7](codesnippet/cpp/mfc-activex-controls-adding-custom-events_1.h)]

Dieser Code deklariert eine Inline Funktion `FireClickIn` mit dem Namen, die [COleControl:: FireEvent](reference/colecontrol-class.md#fireevent) mit dem ClickIn-Ereignis und Parametern aufruft, die Sie mithilfe des Assistenten zum Hinzufügen von Ereignissen definiert haben.

Außerdem wird die folgende Zeile der Ereignis Zuordnung für das-Steuerelement hinzugefügt, das sich in der-Implementierung befindet (. Cpp-Datei Ihrer Steuerelement Klasse:

[!code-cpp[NVC_MFC_AxUI#8](codesnippet/cpp/mfc-activex-controls-adding-custom-events_2.cpp)]

Mit diesem Code wird das Ereignis mit der Funktion "Inline" versehen `FireClickIn` und die Parameter übergeben, die Sie mithilfe des Assistenten zum Hinzufügen von Ereignissen definiert haben.

Zum Schluss wird die folgende Zeile zum-Steuerelement hinzugefügt. IDL-Datei:

[!code-cpp[NVC_MFC_AxUI#9](codesnippet/cpp/mfc-activex-controls-adding-custom-events_3.idl)]

Diese Zeile weist das ClickIn-Ereignis einer bestimmten ID-Nummer zu, die aus der Position des Ereignisses in der Ereignisliste Ereignis-Assistent hinzufügen entnommen wurde. Der Eintrag in der Ereignisliste ermöglicht einem Container das Vorhersagen des Ereignisses. Beispielsweise kann er Handlercode bereitstellen, der ausgeführt werden soll, wenn das Ereignis ausgelöst wird.

## <a name="calling-fireclickin"></a><a name="_core_calling_fireclickin"></a>Aufrufen von "freclickin"

Nachdem Sie das benutzerdefinierte ClickIn-Ereignis mithilfe des Assistenten zum Hinzufügen von Ereignissen hinzugefügt haben, müssen Sie entscheiden, wann dieses Ereignis ausgelöst werden soll. Dies erfolgt durch Aufrufen von, `FireClickIn` Wenn die entsprechende Aktion ausgeführt wird. Für diese Erörterung verwendet das-Steuerelement die- `InCircle` Funktion innerhalb eines `WM_LBUTTONDOWN` Meldungs Handlers, um das ClickIn-Ereignis auszulösen, wenn ein Benutzer in einem kreisförmigen oder elliptischen Bereich klickt. Mit dem folgenden Verfahren wird der-Handler hinzugefügt `WM_LBUTTONDOWN` .

#### <a name="to-add-a-message-handler-with-the-add-event-wizard"></a>So fügen Sie mit dem Assistenten zum Hinzufügen von Ereignissen einen Nachrichten Handler hinzu

1. Laden Sie das Steuerelementprojekt.

1. Wählen Sie in **Klassenansicht**ihre ActiveX-Steuerelement Klasse aus.

1. Im Fenster **Eigenschaften** sehen Sie eine Liste der Meldungen, die vom ActiveX-Steuerelement verarbeitet werden können. Jeder in Fett gezeigten Meldung wird bereits eine Handlerfunktion zugewiesen.

1. Wählen Sie die Nachricht aus, die Sie behandeln möchten. Wählen Sie in diesem Beispiel aus `WM_LBUTTONDOWN` .

1. Wählen Sie im Dropdown-Listenfeld auf der rechten Seite ** \<Add> OnLButtonDown**aus.

1. Doppelklicken Sie in **Klassenansicht** auf die neue Handlerfunktion, um zum Meldungshandlercode in der-Implementierung zu springen (. Cpp-Datei des ActiveX-Steuer Elements.

Im folgenden Codebeispiel wird die- `InCircle` Funktion jedes Mal aufgerufen, wenn im Steuerelement Fenster auf die linke Maustaste geklickt wird. Dieses Beispiel finden Sie in der `WM_LBUTTONDOWN` Handlerfunktion `OnLButtonDown` in der [CIRC-Beispiel](../overview/visual-cpp-samples.md) Abstraktion.

[!code-cpp[NVC_MFC_AxUI#10](codesnippet/cpp/mfc-activex-controls-adding-custom-events_4.cpp)]

> [!NOTE]
> Wenn der Assistent zum Hinzufügen von Ereignissen Meldungs Handler für Maustasten Aktionen erstellt, wird automatisch ein aufzurufende Nachrichten Handler der Basisklasse hinzugefügt. Entfernen Sie diesen-Befehl nicht. Wenn das Steuerelement eine der Stock Maus Nachrichten verwendet, müssen die Meldungs Handler in der Basisklasse aufgerufen werden, um sicherzustellen, dass die Maus Aufzeichnung ordnungsgemäß verarbeitet wird.

Im folgenden Beispiel wird das-Ereignis nur ausgelöst, wenn der Klick innerhalb eines Zirkel förmigen oder elliptischen Bereichs innerhalb des-Steuer Elements auftritt. Um dieses Verhalten zu erreichen, können Sie die `InCircle` -Funktion in der Implementierung des-Steuer Elements platzieren (. Cpp-Datei:

[!code-cpp[NVC_MFC_AxUI#11](codesnippet/cpp/mfc-activex-controls-adding-custom-events_5.cpp)]

Sie müssen auch die folgende Deklaration der `InCircle` -Funktion zum-Header Ihres Steuer Elements hinzufügen (. H):

[!code-cpp[NVC_MFC_AxUI#12](codesnippet/cpp/mfc-activex-controls-adding-custom-events_6.h)]

## <a name="custom-events-with-stock-names"></a><a name="_core_custom_events_with_stock_names"></a>Benutzerdefinierte Ereignisse mit Aktien Namen

Sie können benutzerdefinierte Ereignisse mit dem gleichen Namen wie Aktien Ereignisse erstellen, aber Sie können nicht beide Elemente im selben Steuerelement implementieren. Beispielsweise können Sie ein benutzerdefiniertes Ereignis mit dem Namen Click erstellen, das nicht ausgelöst wird, wenn beim Klicken auf das Kurs Ereignis normalerweise ein Trigger ausgelöst wird. Sie können das Click-Ereignis dann jederzeit auslösen, indem Sie die auslösende Funktion aufrufen.

Im folgenden Verfahren wird ein benutzerdefiniertes Click-Ereignis hinzugefügt.

#### <a name="to-add-a-custom-event-that-uses-a-stock-event-name"></a>So fügen Sie ein benutzerdefiniertes Ereignis hinzu, das einen Aktien Ereignis Namen verwendet

1. Laden Sie das Steuerelementprojekt.

1. Klicken Sie in **Klassenansicht**mit der rechten Maustaste auf Ihre ActiveX-Steuerelement Klasse, um das Kontextmenü zu öffnen.

1. Klicken Sie im Kontextmenü auf **Hinzufügen** , und klicken Sie dann auf **Ereignis hinzufügen**.

   Daraufhin wird der Assistent zum Hinzufügen von Ereignissen geöffnet.

1. Wählen Sie in der Dropdown Liste **Ereignis Name** den Namen eines Aktien Ereignisses aus. Wählen Sie für dieses Beispiel die Option **Klicken**aus.

1. Wählen Sie für **Ereignistyp**die Option **Benutzer**definiert aus.

1. Klicken Sie auf **Fertig** stellen, um das Ereignis zu erstellen.

1. `FireClick`An den entsprechenden Stellen im Code aufzurufen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)
