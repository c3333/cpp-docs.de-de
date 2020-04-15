---
title: Leerlaufschleifen-Verarbeitung
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376014"
---
# <a name="idle-loop-processing"></a>Leerlaufschleifen-Verarbeitung

Viele Anwendungen führen eine langwierige Verarbeitung "im Hintergrund" durch. Manchmal diktieren Leistungsüberlegungen die Verwendung von Multithreading für solche Arbeiten. Threads erfordern zusätzlichen Entwicklungsaufwand, daher werden sie für einfache Aufgaben wie die Leerlaufarbeit, die MFC in der [OnIdle-Funktion](../mfc/reference/cwinthread-class.md#onidle) ausführt, nicht empfohlen. Dieser Artikel konzentriert sich auf die Verarbeitung im Leerlauf. Weitere Informationen zum Multithreading finden Sie unter [Multithreading-Themen](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Einige Arten der Hintergrundverarbeitung werden in Intervallen entsprechend durchgeführt, in denen der Benutzer andernfalls nicht mit der Anwendung interagiert. In einer Anwendung, die für das Microsoft Windows-Betriebssystem entwickelt wurde, kann eine Anwendung die Verarbeitung im Leerlauf durchführen, indem sie einen langwierigen Prozess in viele kleine Fragmente aufteilt. Nach der Verarbeitung jedes Fragments gibt die Anwendung Windows mithilfe einer [PeekMessage-Schleife](/windows/win32/api/winuser/nf-winuser-peekmessagew) eine Ausführungssteuerung.

In diesem Artikel werden zwei Möglichkeiten für die Verarbeitung im Leerlauf in Ihrer Anwendung erläutert:

- Verwenden von **PeekMessage** in der Hauptnachrichtenschleife von MFC.

- Einbetten einer anderen **PeekMessage-Schleife** an einer anderen Stelle in der Anwendung.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>PeekMessage in der MFC-Nachrichtenschleife

In einer Mit MFC entwickelten Anwendung enthält `CWinThread` die Hauptnachrichtenschleife in der Klasse eine Nachrichtenschleife, die die [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32-API aufruft. Diese Schleife ruft `OnIdle` auch `CWinThread` die Memberfunktion zwischen Nachrichten auf. Eine Anwendung kann Nachrichten in dieser Leerlaufzeit verarbeiten, indem sie die `OnIdle` Funktion überschreibt.

> [!NOTE]
> `Run`, `OnIdle`und bestimmte andere Memberfunktionen sind `CWinThread` jetzt Mitglieder `CWinApp`der Klasse und nicht der Klasse . `CWinApp` wird von `CWinThread` abgeleitet.

Weitere Informationen zum Ausführen der Verarbeitung im Leerlauf finden Sie unter [OnIdle](../mfc/reference/cwinthread-class.md#onidle) in der *MFC-Referenz*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>PeekMessage an anderer Stelle in Ihrer Anwendung

Eine weitere Methode zum Ausführen der Verarbeitung im Leerlauf in einer Anwendung besteht darin, eine Nachrichtenschleife in eine Ihrer Funktionen einzubetten. Diese Nachrichtenschleife ist der Hauptnachrichtenschleife von MFC in [CWinThread::Run](../mfc/reference/cwinthread-class.md#run)sehr ähnlich. Das bedeutet, dass eine solche Schleife in einer Anwendung, die mit MFC entwickelt wurde, viele der gleichen Funktionen wie die Hauptnachrichtenschleife ausführen muss. Das folgende Codefragment veranschaulicht das Schreiben einer Nachrichtenschleife, die mit MFC kompatibel ist:

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

Dieser Code, der in eine Funktion eingebettet ist, wird in Schleifen gebracht, solange eine Verarbeitung im Leerlauf erforderlich ist. Innerhalb dieser Schleife ruft eine `PeekMessage`verschachtelte Schleife wiederholt auf. Solange dieser Aufruf einen Wert ungleich Null `CWinThread::PumpMessage` zurückgibt, ruft die Schleife auf, um die normale Nachrichtenübersetzung und -verteilung durchzuführen. Obwohl `PumpMessage` es sich nicht dokumentiert, können Sie dessen Quellcode in der Datei ThrdCore.Cpp im Verzeichnis "atlmfc" Ihrer Visual C++-Installation untersuchen.

Sobald die innere Schleife endet, führt die äußere Schleife `OnIdle`die Leerlaufverarbeitung mit einem oder mehreren Aufrufen von durch. Der erste Aufruf dient mFC- Zwecken. Sie können zusätzliche `OnIdle` Anrufe tätigen, um Ihre eigene Hintergrundarbeit zu erledigen.

Weitere Informationen zum Ausführen der Verarbeitung im Leerlauf finden Sie unter [OnIdle](../mfc/reference/cwinthread-class.md#onidle) in der MFC-Bibliotheksreferenz.

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
