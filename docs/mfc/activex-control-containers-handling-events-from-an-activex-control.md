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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367953"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>ActiveX-Steuerelementcontainer: Behandeln von Ereignissen eines ActiveX-Steuerelements

In diesem Artikel wird die Verwendung des **Eigenschaftenfensters** (in **der Klassenansicht**) zum Installieren von Ereignishandlern für ActiveX-Steuerelemente in einem ActiveX-Steuerelementcontainer erläutert. Die Ereignishandler werden verwendet, um Benachrichtigungen (vom Steuerelement) bestimmter Ereignisse zu empfangen und als Reaktion eine Aktion auszuführen. Diese Benachrichtigung wird als "Auslösen" des Ereignisses bezeichnet.

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

> [!NOTE]
> In diesem Artikel wird ein dialogbasiertes ActiveX-Steuerelementcontainerprojekt mit dem Namen Container und ein eingebettetes Steuerelement mit dem Namen Circ als Beispiele in den Prozeduren und dem Code verwendet.

Mit der Schaltfläche Ereignisse im **Eigenschaftenfenster** (in der **Klassenansicht**) können Sie eine Zuordnung von Ereignissen erstellen, die in Ihrer ActiveX-Steuerelementcontaineranwendung auftreten können. Diese Karte, die als "Ereignissenkenzuordnung" bezeichnet wird, wird von Visual C++ erstellt und verwaltet, wenn Sie der Steuerelementcontainerklasse Ereignishandler hinzufügen. Jeder Ereignishandler, der mit einem Ereigniszuordnungseintrag implementiert ist, ordnet ein bestimmtes Ereignis einer Containerereignishandlermemberfunktion zu. Diese Ereignishandlerfunktion wird aufgerufen, wenn das angegebene Ereignis vom ActiveX-Steuerelementobjekt ausgelöst wird.

Weitere Informationen zu Ereignissenkenzuordnungen finden Sie unter [Ereignissenkenzuordnungen](../mfc/reference/event-sink-maps.md) in der *Klassenbibliotheksreferenz*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Ereignishandleränderungen am Projekt

Wenn Sie das **Eigenschaftenfenster** zum Hinzufügen von Ereignishandlern verwenden, wird eine Ereignissenkenzuordnung deklariert und in Ihrem Projekt definiert. Die folgenden Anweisungen werden dem Steuerelement hinzugefügt. CPP-Datei beim ersten Hinzulegen eines Ereignishandlers. Dieser Code deklariert eine Ereignissenkenzuordnung für die Dialogfeldklasse (in diesem `CContainerDlg`Fall):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Wenn Sie das **Eigenschaftenfenster** zum Hinzufügen von`ON_EVENT`Ereignissen verwenden, wird der Ereignissenkenzuordnung ein Ereigniszuordnungseintrag ( ) hinzugefügt, und der Implementierung des Containers wird eine Ereignishandlerfunktion hinzugefügt (. CPP)-Datei.

Im folgenden Beispiel wird ein `OnClickInCircCtrl`Ereignishandler mit dem `ClickIn` Namen , für das Ereignis des Circ-Steuerelements deklariert:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Darüber hinaus wird die folgende `CContainerDlg` Vorlage zur Klassenimplementierung hinzugefügt (. CPP)-Datei für die Ereignishandlermemberfunktion:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Weitere Informationen zu Ereignissenkenmakros finden Sie unter [Ereignissenkenzuordnungen](../mfc/reference/event-sink-maps.md) in der *Klassenbibliotheksreferenz*.

#### <a name="to-create-an-event-handler-function"></a>So erstellen Sie eine Ereignishandlerfunktion

1. Wählen Sie in der Klassenansicht die Dialogklasse aus, die das ActiveX-Steuerelement enthält. Verwenden Sie in `CContainerDlg`diesem Beispiel .

1. Klicken Sie im Fenster **Eigenschaften** auf die Schaltfläche **Ereignisse**.

1. Wählen Sie im **Fenster Eigenschaften** die Steuerungs-ID des eingebetteten ActiveX-Steuerelements aus. Verwenden Sie in `IDC_CIRCCTRL1`diesem Beispiel .

   Im **Fenster Eigenschaften** wird eine Liste der Ereignisse angezeigt, die vom eingebetteten ActiveX-Steuerelement ausgelöst werden können. Jeder Elementfunktion, die in fett dargestellt wird, sind bereits Handlerfunktionen zugewiesen.

1. Wählen Sie das Ereignis aus, das die Dialogklasse verarbeiten soll. Wählen Sie in diesem Beispiel **Klicken**aus.

1. Wählen Sie ** \<** im Dropdown-Listenfeld auf der rechten Seite> ClickCircctrl1 .

1. Doppelklicken Sie auf die neue Handlerfunktion aus der Klassenansicht, um zum Ereignishandlercode in der Implementierung zu springen (. CPP)-Datei `CContainerDlg`von .

## <a name="see-also"></a>Siehe auch

[ActiveX-Steuerelementcontainer](../mfc/activex-control-containers.md)
