---
title: 'Windows Sockets: Ports und Socketadressen'
ms.date: 11/04/2016
helpviewer_keywords:
- ports [MFC], definition
- Windows Sockets [MFC], ports
- Windows Sockets [MFC], addresses
- ports [MFC]
- addresses [MFC], socket
- sockets [MFC], addresses
- sockets [MFC], ports
ms.assetid: e050261a-9285-4f31-a1c5-6c8033af5b4a
ms.openlocfilehash: 791bf07c927e80e65e0fda79fae8a50235bc2def
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371050"
---
# <a name="windows-sockets-ports-and-socket-addresses"></a>Windows Sockets: Ports und Socketadressen

In diesem Artikel werden die Begriffe "Port" und "Adresse" erläutert, wie sie bei Windows Sockets verwendet werden.

## <a name="port"></a><a name="_core_port"></a>Hafen

Ein Port identifiziert einen eindeutigen Prozess, für den ein Dienst bereitgestellt werden kann. Im vorliegenden Kontext ist ein Port einer Anwendung zugeordnet, die Windows Sockets unterstützt. Die Idee ist, jede Windows Sockets-Anwendung eindeutig zu identifizieren, sodass mehr als eine Windows Sockets-Anwendung gleichzeitig auf einem Computer ausgeführt werden kann.

Bestimmte Ports sind für allgemeine Dienste wie FTP reserviert. Sie sollten die Verwendung dieser Ports vermeiden, es sei denn, Sie bieten diese Art von Dienst an. In der Windows Sockets-Spezifikation werden diese reservierten Ports aufgeführt. Die Datei WINSOCK. H listet sie auch auf.

Damit die Windows Sockets-DLL einen verwendbaren Port für Sie auswählen kann, übergeben Sie 0 als Portwert. MFC wählt einen Portwert größer als 1.024 Dezimalstellen aus. Sie können den von MFC ausgewählten Portwert abrufen, indem Sie die [A-Zip-Funktion CAsyncSocket::GetSockName](../mfc/reference/casyncsocket-class.md#getsockname) aufrufen.

## <a name="socket-address"></a><a name="_core_socket_address"></a>Socketadresse

Jedes Socketobjekt ist einer IP-Adresse (Internet Protocol) im Netzwerk zugeordnet. In der Regel ist die Adresse ein Computername, z. B. "ftp.microsoft.com", oder eine gepunktete Zahl, z. B. "128.56.22.8".

Wenn Sie einen Socket erstellen möchten, müssen Sie in der Regel keine eigene Adresse angeben.

> [!NOTE]
> Es ist möglich, dass Ihr Computer über mehrere Netzwerkkarten verfügt (oder Ihre Anwendung eines Tages auf einem solchen Computer ausgeführt werden kann), die jeweils ein anderes Netzwerk darstellen. In diesem Fall müssen Sie möglicherweise eine Adresse angeben, um anzugeben, welche Netzwerkkarte der Socket verwenden soll. Dies ist sicher, eine erweiterte Nutzung und ein mögliches Portabilitätsproblem zu sein.

Weitere Informationen finden Sie unter

- [Windows Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows Sockets: Wie Sockets mit Archiven arbeiten](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
