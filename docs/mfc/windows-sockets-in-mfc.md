---
title: Windows-Sockets in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- WINSOCK.DLL
- sockets [MFC], programming models
- MFC, Windows Sockets
- Windows Sockets [MFC], MFC support
- Windows Sockets [MFC], programming models
- WSOCK32.DLL
- sockets [MFC], MFC
ms.assetid: 1f3c476a-9c68-49fe-9a25-d22971a334d0
ms.openlocfilehash: 8e5562b028d3d9b7cba4b47716b63fd1392c514f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371093"
---
# <a name="windows-sockets-in-mfc"></a>Windows-Sockets in MFC

> [!NOTE]
> MFC unterstützt Windows Sockets 1, unterstützt jedoch Windows [Sockets 2](/windows/win32/WinSock/windows-sockets-start-page-2)nicht . Windows Sockets 2 wurde zuerst mit Windows 98 ausgeliefert und ist die in Windows 2000 enthaltene Version.

MFC stellt zwei Modelle zum Schreiben von Netzwerkkommunikationsprogrammen mit Windows Sockets zur Verfügung, die in zwei MFC-Klassen enthalten sind. In diesem Artikel werden diese Modelle und weitere Details beschrieben, die MFC-Sockets unterstützen. Ein "Socket" ist ein Endpunkt der Kommunikation: ein Objekt, über das Ihre Anwendung mit anderen Windows Sockets-Anwendungen über ein Netzwerk kommuniziert.

Informationen zu Windows Sockets, einschließlich einer Erläuterung des Socketkonzepts, finden Sie unter [Windows Sockets: Background](../mfc/windows-sockets-background.md).

## <a name="sockets-programming-models"></a><a name="_core_sockets_programming_models"></a>Sockets-Programmiermodelle

Die beiden MFC Windows Sockets-Programmiermodelle werden von den folgenden Klassen unterstützt:

- `CAsyncSocket`

   Diese Klasse kapselt die Windows Sockets-API. [CAsyncSocket](../mfc/reference/casyncsocket-class.md) ist für Programmierer, die Netzwerkprogrammierung kennen und die Flexibilität der Programmierung direkt auf die Socket-API wollen, aber auch die Bequemlichkeit von Rückruffunktionen für die Benachrichtigung von Netzwerkereignissen wollen. Abgesehen von dem Verpacken von Sockets in objektorientierter Form für die Verwendung in C++ ist die einzige zusätzliche Abstraktion, die diese Klasse bereitstellt, das Konvertieren bestimmter Socket-bezogener Windows-Nachrichten in Rückrufe. Weitere Informationen finden Sie unter [Windows Sockets: Socket Notifications](../mfc/windows-sockets-socket-notifications.md).

- `CSocket`

   Diese von `CAsyncSocket`abgeleitete Klasse stellt eine Abstraktion auf höherer Ebene für die Arbeit mit Sockets über ein MFC-CArchive-Objekt zur Verfügung. [CArchive](../mfc/reference/carchive-class.md) Die Verwendung eines Sockets mit einem Archiv ähnelt stark der Verwendung des MFC-Dateiserialisierungsprotokolls. Dies macht die Verwendung `CAsyncSocket` einfacher als das Modell. [CSocket](../mfc/reference/csocket-class.md) erbt viele Memberfunktionen, die `CAsyncSocket` Windows Sockets-APIs kapseln. Sie müssen einige dieser Funktionen verwenden und Sockets im Allgemeinen programmieren. Verwaltet `CSocket` jedoch viele Aspekte der Kommunikation, die Sie selbst mit `CAsyncSocket`der rohen API oder der Klasse erledigen müssten. Am wichtigsten `CSocket` ist, bietet Blockierung (mit Hintergrundverarbeitung von Windows-Nachrichten), die für den synchronen Betrieb von `CArchive`ist.

Erstellen und `CSocket` `CAsyncSocket` Verwenden von Objekten wird in [Windows Sockets beschrieben: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md) und [Windows Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md).

## <a name="windows-sockets-dlls"></a><a name="_core_mfc_socket_samples_and_windows_sockets_dlls"></a>Windows Sockets-DLLs

Die Microsoft Windows-Betriebssysteme stellen die Windows Sockets Dynamic-Link-Bibliotheken (DLL) bereit. Visual C++ stellt die entsprechenden Headerdateien und Bibliotheken sowie die Windows Sockets-Spezifikation zur Verfügung.

Weitere Informationen zu Windows Sockets finden Sie unter:

- [Windows Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

- [Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Reihenfolge der Operationen](../mfc/windows-sockets-sequence-of-operations.md)

- [Windows Sockets: Beispiel für Sockets mithilfe der Archive](../mfc/windows-sockets-example-of-sockets-using-archives.md)

- [Windows Sockets: Wie Sockets mit Archiven arbeiten](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Ableiten von Socket-Classen](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Socketbenachrichtigungen](../mfc/windows-sockets-socket-notifications.md)

- [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md)

- [Windows Sockets: Bytereihenfolge](../mfc/windows-sockets-byte-ordering.md)

- [Windows Sockets: Umwandeln von Zeichenfolgen](../mfc/windows-sockets-converting-strings.md)

- [Windows Sockets: Ports und Socketadressen](../mfc/windows-sockets-ports-and-socket-addresses.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets](../mfc/windows-sockets.md)
