---
title: 'ActiveX-Steuerelementcontainer: Behandeln von Ereignissen eines ActiveX-Steuerelements'
ms.date: 09/12/2018
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
ms.openlocfilehash: 4b7bc78a2937c010a4d2f1fb000ae0fe8ca2416c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625122"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX-Steuerelementcontainer: Behandeln von Ereignissen eines ActiveX-Steuerelements

In diesem Artikel wird die Verwendung des Fensters **Eigenschaften** (in **Klassenansicht**) zum Installieren von Ereignis Handlern für ActiveX-Steuerelemente in einem ActiveX-Steuerelement Container erläutert. Die Ereignishandler werden verwendet, um Benachrichtigungen (von der Steuerung) bestimmter Ereignisse zu empfangen und eine Aktion als Reaktion auszuführen. Diese Benachrichtigung wird als "auslösen" des Ereignisses bezeichnet.

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

> [!NOTE]
> In diesem Artikel wird ein Dialogfeld basiertes ActiveX-Steuerelement Container Projekt mit dem Namen Container und ein eingebettetes Steuerelement namens CIRC als Beispiele in den Prozeduren und Codes verwendet.

Mithilfe der Schaltfläche Ereignisse im **Eigenschaften** Fenster (in **Klassenansicht**) können Sie eine Zuordnung von Ereignissen erstellen, die in der Containeranwendung des ActiveX-Steuer Elements auftreten können. Diese Zuordnung, die als "Ereignissenkenzuordnung" bezeichnet wird, wird von Visual C++ erstellt und verwaltet, wenn Sie der Steuerelement Container Klasse Ereignishandler hinzufügen. Jeder Ereignishandler, der mit einem Ereignis Zuordnungs Eintrag implementiert wird, ordnet einem containerereignishandlermember ein bestimmtes Ereignis zu. Diese Ereignishandlerfunktion wird aufgerufen, wenn das angegebene Ereignis vom ActiveX-Steuerelement Objekt ausgelöst wird.

Weitere Informationen zu ereignissenkenmaps finden Sie unter [ereignissenkenzuordnungen](reference/event-sink-maps.md) in der *Klassen Bibliotheks Referenz*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Ereignishandleränderungen am Projekt

Wenn Sie das **Eigenschaften** Fenster verwenden, um Ereignishandler hinzuzufügen, wird eine Ereignissenkenzuordnung deklariert und im Projekt definiert. Die folgenden-Anweisungen werden dem-Steuerelement hinzugefügt. Cpp-Datei beim ersten Hinzufügen eines Ereignis Handlers. Dieser Code deklariert eine Ereignis Senke-Zuordnung für die Dialogfeld Klasse (in diesem Fall `CContainerDlg` ):

[!code-cpp[NVC_MFC_AxCont#8](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Wenn Sie das **Eigenschaften** Fenster verwenden, um Ereignisse hinzuzufügen, `ON_EVENT` wird der Ereignis Senk Karte ein Ereignis Zuordnungs Eintrag () hinzugefügt, und der Implementierung des Containers wird eine Ereignishandlerfunktion hinzugefügt. Cpp-Datei.

Im folgenden Beispiel wird ein Ereignishandler mit `OnClickInCircCtrl` dem Namen für das-Ereignis des Circ-Steuer Elements deklariert `ClickIn` :

[!code-cpp[NVC_MFC_AxCont#10](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Außerdem wird die folgende Vorlage der `CContainerDlg` Klassen Implementierung () hinzugefügt. Cpp-Datei für die ereignishandlermember-Funktion:

[!code-cpp[NVC_MFC_AxCont#11](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Weitere Informationen zu ereignissenkenmakros finden Sie unter [ereignissenkenzuordnungen](reference/event-sink-maps.md) in der *Klassen Bibliotheks Referenz*.

#### <a name="to-create-an-event-handler-function"></a>So erstellen Sie eine Ereignishandlerfunktion

1. Wählen Sie in Klassenansicht die Dialogfeld Klasse aus, die das ActiveX-Steuerelement enthält. Verwenden Sie für dieses Beispiel `CContainerDlg` .

1. Klicken Sie im Fenster **Eigenschaften** auf die Schaltfläche **Ereignisse**.

1. Wählen Sie im Fenster **Eigenschaften** die Steuerelement-ID des eingebetteten ActiveX-Steuer Elements aus. Verwenden Sie für dieses Beispiel `IDC_CIRCCTRL1` .

   Das **Eigenschaften** Fenster zeigt eine Liste von Ereignissen an, die vom eingebetteten ActiveX-Steuerelement ausgelöst werden können. Jeder Member-Funktion, die in Fett Schrift angezeigt wird, sind Handlerfunktionen zugewiesen.

1. Wählen Sie das Ereignis aus, das von der Dialogfeld Klasse behandelt werden soll. Wählen Sie für dieses Beispiel die Option **Klicken**aus.

1. Wählen Sie im Dropdown-Listenfeld auf der rechten Seite die Option ** \<Add> ClickCircctrl1**aus.

1. Doppelklicken Sie in Klassenansicht auf die neue Handlerfunktion, um zum Ereignishandlercode in der-Implementierung zu springen (. Cpp-Datei von `CContainerDlg` .

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](activex-control-containers.md)
