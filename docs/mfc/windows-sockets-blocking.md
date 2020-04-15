---
title: 'Windows Sockets: Blocking'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], blocking mode
- Windows Sockets [MFC], Windows platforms
- Windows Sockets [MFC], blocking mode
- sockets [MFC], behavior on different Windows platforms
- blocking mode sockets
ms.assetid: 10aca9b1-bfba-41a8-9c55-ea8082181e63
ms.openlocfilehash: 87d4f0eb57f9e26dbf73da06b5d7ca6d61d6c174
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359994"
---
# <a name="windows-sockets-blocking"></a>Windows Sockets: Blocking

In diesem Artikel und zwei Begleitartikeln werden mehrere Probleme in der Windows Sockets-Programmierung erläutert. Dieser Artikel behandelt das Blockieren. Die anderen Probleme werden in den Artikeln behandelt: [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) und [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Wenn Sie die Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)verwenden oder von ihr ableiten, müssen Sie diese Probleme selbst verwalten. Wenn Sie die Klasse [CSocket](../mfc/reference/csocket-class.md)verwenden oder von ihr ableiten, verwaltet MFC sie für Sie.

## <a name="blocking"></a>Blockierung

Ein Socket kann sich im "Blockierungsmodus" oder "Nichtblockierungsmodus" befinden. Die Funktionen von Sockets im Blockierungsmodus (oder synchronen Modus) kehren erst zurück, wenn sie ihre Aktion abschließen können. Dies wird als Blockieren bezeichnet, da der Socket, dessen Funktion aufgerufen wurde, nichts tun kann – blockiert – bis der Aufruf zurückkehrt. Ein Aufruf `Receive` der Memberfunktion kann z. B. beliebig lange dauern, da er auf das Senden der `CSocket`sendenden `CAsyncSocket` Anwendung wartet (dies ist der Fall, wenn Sie verwenden, oder mit blockierender Funktion). Wenn `CAsyncSocket` sich ein Objekt im nicht blockierenden Modus befindet (asynchron arbeitet), wird der Aufruf sofort zurückgegeben, und der aktuelle Fehlercode, der mit der [GetLastError-Memberfunktion](../mfc/reference/casyncsocket-class.md#getlasterror) abgerufen werden kann, ist **WSAEWOULDBLOCK**, was darauf hinweist, dass der Aufruf blockiert worden wäre, wenn er nicht sofort aufgrund des Modus zurückgegeben worden wäre. (`CSocket` gibt niemals **WSAEWOULDBLOCK**zurück . Die Klasse verwaltet das Blockieren für Sie.)

Das Verhalten von Sockets unterscheidet sich unter 32-Bit- und 64-Bit-Betriebssystemen (z. B. Windows 95 oder Windows 98) von 16-Bit-Betriebssystemen (z. B. Windows 3.1). Im Gegensatz zu 16-Bit-Betriebssystemen verwenden die 32-Bit- und 64-Bit-Betriebssysteme präventives Multitasking und bieten Multithreading. Unter den 32-Bit- und 64-Bit-Betriebssystemen können Sie Ihre Sockets in separaten Arbeitsthreads einsetzen. Ein Socket in einem Thread kann blockieren, ohne andere Aktivitäten in der Anwendung zu beeinträchtigen und ohne Rechenzeit für die Blockierung aufzugeben. Informationen zur Multithread-Programmierung finden Sie im Artikel [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).

> [!NOTE]
> In Multithreadanwendungen können Sie die blockierende Natur von `CSocket` verwenden, um den Entwurf Ihres Programms zu vereinfachen, ohne die Reaktionsfähigkeit der Benutzeroberfläche zu beeinträchtigen. Durch die Behandlung von Benutzerinteraktionen im Hauptthread und `CSocket` die Verarbeitung in alternativen Threads können Sie diese logischen Vorgänge trennen. In einer Anwendung, die nicht multithreaded ist, müssen diese beiden Aktivitäten als `CAsyncSocket` ein einzelner Thread kombiniert und behandelt `CSocket::OnMessagePending` werden, was in der Regel bedeutet, dass Sie Kommunikationsanforderungen bei Bedarf verarbeiten oder überschreiben, um Benutzeraktionen während längerer synchroner Aktivitäten zu behandeln.

Der Rest dieser Diskussion richtet sich an Programmierer, die auf 16-Bit-Betriebssysteme abzielen:

Wenn Sie `CAsyncSocket`verwenden, sollten Sie normalerweise die Verwendung von Blockierungsvorgängen vermeiden und stattdessen asynchron arbeiten. Bei asynchronen Vorgängen warten Sie z. B. ab dem `Receive`Punkt, an dem Sie `OnReceive` nach dem Aufruf einen **WSAEWOULDBLOCK-Fehlercode** erhalten, bis Ihre Memberfunktion aufgerufen wird, um Sie darüber zu informieren, dass Sie erneut lesen können. Asynchrone Aufrufe werden durch Rückruf der entsprechenden Rückrufbenachrichtigungsfunktion Ihres Sockets, z. B. [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive), durchgeführt.

Unter Windows gelten blockierende Aufrufe als schlechte Übung. Standardmäßig unterstützt [CAsyncSocket](../mfc/reference/casyncsocket-class.md) asynchrone Aufrufe, und Sie müssen die Blockierung selbst mithilfe von Rückrufbenachrichtigungen verwalten. Die Klasse [CSocket](../mfc/reference/csocket-class.md)hingegen ist synchron. Es pumpt Windows-Nachrichten und verwaltet die Blockierung für Sie.

Weitere Informationen zum Blockieren finden Sie in der Windows Sockets-Spezifikation. Weitere Informationen zu "On"-Funktionen finden Sie unter [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md) and [Windows Sockets: Deriving from Socket Classes](../mfc/windows-sockets-deriving-from-socket-classes.md).

Weitere Informationen finden Sie unter

- [Windows Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Hintergrund](../mfc/windows-sockets-background.md)

- [Windows Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CAsyncSocket::OnSend](../mfc/reference/casyncsocket-class.md#onsend)
