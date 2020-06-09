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
ms.openlocfilehash: 74ca89d91cf4e60b09a063551b526f177caed161
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624514"
---
# <a name="idle-loop-processing"></a>Leerlaufschleifen-Verarbeitung

Viele Anwendungen führen eine lange Verarbeitung im Hintergrund aus. Manchmal wird die Verwendung von Multithreading für diese Arbeit durch Leistungsaspekte vorgegeben. Threads verursachen zusätzlichen Entwicklungsaufwand, sodass Sie nicht für einfache Aufgaben wie die Leerlaufzeit, die MFC in der [OnIdle](reference/cwinthread-class.md#onidle) -Funktion durchführt, empfohlen werden. Dieser Artikel konzentriert sich auf die Leerlauf Verarbeitung. Weitere Informationen zum Multithreading finden Sie unter [Multithreading-Themen](../parallel/multithreading-support-for-older-code-visual-cpp.md).

Einige Arten der Hintergrundverarbeitung werden in Intervallen ordnungsgemäß durchgeführt, in denen der Benutzer nicht anderweitig mit der Anwendung interagiert. In einer Anwendung, die für das Betriebssystem Microsoft Windows entwickelt wurde, kann eine Anwendung die Leerlaufzeit Verarbeitung durchführen, indem ein langwieriger Prozess in viele kleine Fragmente aufgeteilt wird. Nach der Verarbeitung der einzelnen Fragmente gibt die Anwendung mithilfe einer " [Peer Message](/windows/win32/api/winuser/nf-winuser-peekmessagew) "-Schleife die Ausführungs Steuerung an Windows aus.

In diesem Artikel werden zwei Möglichkeiten für die Leerlauf Verarbeitung in Ihrer Anwendung erläutert:

- Verwenden von " **Peer Message** " in der Hauptnachrichten Schleife von MFC.

- Das Einbetten einer anderen **Peer Message** -Schleife an einer anderen Stelle in der Anwendung.

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>"Peer Message" in der MFC-Nachrichten Schleife

In einer mit MFC entwickelten Anwendung enthält die Hauptnachrichten Schleife in der- `CWinThread` Klasse eine Nachrichten Schleife, die die Win32-API von [Peer Message](/windows/win32/api/winuser/nf-winuser-peekmessagew) aufruft. Diese Schleife ruft auch die `OnIdle` Member-Funktion von `CWinThread` zwischen Nachrichten auf. Eine Anwendung kann Nachrichten in dieser Leerlaufzeit verarbeiten, indem Sie die-Funktion überschreibt `OnIdle` .

> [!NOTE]
> `Run`, `OnIdle` und bestimmte andere Element Funktionen sind nun Member der-Klasse und `CWinThread` nicht der-Klasse `CWinApp` . `CWinApp` wird von `CWinThread` abgeleitet.

Weitere Informationen zum Ausführen der Leerlauf Verarbeitung finden Sie unter " [OnIdle](reference/cwinthread-class.md#onidle) " in der *MFC-Referenz*.

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>"Peer Message" an einer anderen Stelle in der Anwendung

Eine andere Methode zum Ausführen der Leerlauf Verarbeitung in einer Anwendung besteht darin, eine Nachrichten Schleife in eine ihrer Funktionen einzubetten. Diese Nachrichten Schleife ähnelt der MFC-Hauptnachrichten Schleife, die in [CWinThread:: Run](reference/cwinthread-class.md#run)gefunden wurde. Dies bedeutet, dass eine solche Schleife in einer mit MFC entwickelten Anwendung viele der gleichen Funktionen wie die Hauptnachrichten Schleife ausführen muss. Das folgende Code Fragment veranschaulicht das Schreiben einer Nachrichten Schleife, die mit MFC kompatibel ist:

[!code-cpp[NVC_MFCDocView#8](codesnippet/cpp/idle-loop-processing_1.cpp)]

Dieser Code, der in eine Funktion eingebettet ist, wird so lange Schleifen, wie es eine Leerlauf Verarbeitung gibt. Innerhalb dieser Schleife ruft eine geschachtelte Schleife wiederholt auf `PeekMessage` . Solange dieser Aufruf einen Wert ungleich 0 (null) zurückgibt, ruft die Schleife `CWinThread::PumpMessage` auf, um eine normale Nachrichten Übersetzung und-Verteilung auszuführen. Obwohl `PumpMessage` nicht dokumentiert ist, können Sie den Quellcode in der Datei "thrdcore. cpp" im Verzeichnis "\atlmfc\src\mfc" Ihrer Visual C++-Installation überprüfen.

Sobald die innere Schleife beendet ist, führt die äußere Schleife eine Leerlauf Verarbeitung mit einem oder mehreren Aufrufen von durch `OnIdle` . Der erste-Befehl wird für MFC-Zwecke verwendet. Sie können zusätzliche Aufrufe von durchführen `OnIdle` , um Ihre eigenen Hintergrundaufgaben durchzuführen.

Weitere Informationen zum Ausführen der Leerlauf Verarbeitung finden Sie unter " [OnIdle](reference/cwinthread-class.md#onidle) " in der MFC-Bibliotheks Referenz.

## <a name="see-also"></a>Siehe auch

[Allgemeine MFC-Themen](general-mfc-topics.md)
