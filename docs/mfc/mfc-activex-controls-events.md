---
title: 'MFC-ActiveX-Steuerelemente: Ereignisse'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
ms.openlocfilehash: 129b805379fa68cb4f50ee1f8e3ac7d1b725d9ec
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622324"
---
# <a name="mfc-activex-controls-events"></a>MFC-ActiveX-Steuerelemente: Ereignisse

ActiveX-Steuerelemente verwenden Ereignisse, um einen Container zu benachrichtigen, dass etwas mit dem Steuerelement geschehen ist. Häufige Beispiele für Ereignisse sind u. a. Klicks auf das Steuerelement, mit der Tastatur eingegebene Daten und Änderungen am Zustand des Steuer Elements. Wenn diese Aktionen auftreten, löst das Steuerelement ein Ereignis aus, um den Container zu benachrichtigen.

Ereignisse werden auch als Meldungen bezeichnet.

MFC unterstützt zwei Arten von Ereignissen: Stock und Custom. Aktien Ereignisse sind Ereignisse, die von der Klasse [COleControl](reference/colecontrol-class.md) automatisch verarbeitet werden. Eine komplette Liste der Aktien Ereignisse finden Sie im Artikel [MFC-ActiveX-Steuerelemente: Hinzufügen von Aktien Ereignissen](mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Mit benutzerdefinierten Ereignissen kann ein Steuerelement den Container Benachrichtigen, wenn eine für dieses Steuerelement spezifische Aktion auftritt. Einige Beispiele wären eine Änderung des internen Zustands eines Steuer Elements oder des Empfangs einer bestimmten Fenster Meldung.

Damit das Steuerelement Ereignisse ordnungsgemäß auslösen kann, muss die Steuerelement Klasse jedes Ereignis des Steuer Elements einer Element Funktion zuordnen, die aufgerufen werden soll, wenn das zugehörige Ereignis auftritt. Dieser Zuordnungs Mechanismus (als Ereignis Zuordnung bezeichnet) zentralisiert Informationen über das Ereignis und ermöglicht es Visual Studio, auf einfache Weise auf die Ereignisse des Steuer Elements zuzugreifen und diese zu bearbeiten. Diese Ereignis Zuordnung wird durch das folgende Makro deklariert, das sich im-Header (befindet. H) der Deklaration der Steuerelement Klasse:

[!code-cpp[NVC_MFC_AxUI#2](codesnippet/cpp/mfc-activex-controls-events_1.h)]

Nachdem die Ereignis Zuordnung deklariert wurde, muss Sie in der-Implementierung des-Steuer Elements () definiert werden. Cpp-Datei. Die folgenden Codezeilen definieren die Ereignis Zuordnung, sodass Ihr Steuerelement bestimmte Ereignisse auslösen kann:

[!code-cpp[NVC_MFC_AxUI#3](codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

Wenn Sie den MFC-ActiveX-Steuerelement-Assistenten verwenden, um das Projekt zu erstellen, werden diese Zeilen automatisch hinzugefügt. Wenn Sie den MFC-ActiveX-Steuerelement-Assistenten nicht verwenden, müssen Sie diese Zeilen manuell hinzufügen.

Mit Klassenansicht können Sie `COleControl` die von Ihnen definierten Klassen-oder benutzerdefinierten Ereignisse hinzufügen, die von Ihnen definiert werden. Bei jedem neuen Ereignis fügt Klassenansicht automatisch den richtigen Eintrag der Ereignis Zuordnung des-Steuer Elements und der-Steuerelemente des-Steuer Elements hinzu. IDL-Datei.

In zwei anderen Artikeln werden die Ereignisse ausführlich erläutert:

- [MFC-ActiveX-Steuerelemente: Hinzufügen von Aktien](mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC-ActiveX-Steuerelemente: Hinzufügen von benutzerdefinierten Ereignissen](mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)<br/>
[MFC-ActiveX-Steuerelemente: Methoden](mfc-activex-controls-methods.md)<br/>
[COleControl-Klasse](reference/colecontrol-class.md)
