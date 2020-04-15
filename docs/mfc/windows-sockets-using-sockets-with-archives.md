---
title: 'Windows Sockets: Verwenden von Sockets mit Archiven'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], archives
- sockets [MFC], with archives
- archives [MFC], and Windows Sockets
- CSocket class [MFC], programming model
ms.assetid: 17e71a99-a09e-4e1a-9fda-13d62805c824
ms.openlocfilehash: 55b4f9a5412c1447fe2b3bde10cb934b91abf008
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359951"
---
# <a name="windows-sockets-using-sockets-with-archives"></a>Windows Sockets: Verwenden von Sockets mit Archiven

In diesem Artikel wird das [CSocket-Programmiermodell](#_core_the_csocket_programming_model)beschrieben. Die Klasse [CSocket](../mfc/reference/csocket-class.md) bietet Socketunterstützung auf einer höheren Abstraktionsebene als die Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md). `CSocket`verwendet eine Version des MFC-Serialisierungsprotokolls, um Daten an und von einem Socketobjekt über ein MFC [CArchive-Objekt](../mfc/reference/carchive-class.md) zu übergeben. `CSocket`bietet Blockierung (während der Verwaltung der Hintergrundverarbeitung `CArchive`von Windows-Nachrichten) und gibt Ihnen Zugriff auf , die `CAsyncSocket`viele Aspekte der Kommunikation verwaltet, die Sie selbst mit der unformatierten API oder Klasse ausführen müssten.

> [!TIP]
> Sie können `CSocket` die Klasse selbst als eine `CAsyncSocket`bequemere Version von verwenden, `CSocket` aber `CArchive` das einfachste Programmiermodell ist die Verwendung mit einem Objekt.

Weitere Informationen zur Funktionsweise der Implementierung von Sockets mit Archiven finden Sie unter [Windows Sockets: Wie Sockets mit Archiven funktionieren](../mfc/windows-sockets-how-sockets-with-archives-work.md). Beispielcode finden Sie unter [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) and Windows [Sockets: Example of Sockets Using Archives](../mfc/windows-sockets-example-of-sockets-using-archives.md). Informationen zu einigen Funktionen, die Sie durch Ableiten eigener Klassen aus den Socketklassen erhalten können, finden Sie unter [Windows Sockets: Ableiten von Socketklassen](../mfc/windows-sockets-deriving-from-socket-classes.md).

> [!NOTE]
> Wenn Sie ein MFC-Clientprogramm schreiben, um mit etablierten (Nicht-MFC-)Servern zu kommunizieren, senden Sie keine C++-Objekte über das Archiv. Wenn es sich bei dem Server nicht um eine MFC-Anwendung handelt, die die Arten von Objekten versteht, die Sie senden möchten, kann er Ihre Objekte nicht empfangen und deserialisieren. Verwandtes Material zum Thema Kommunikation mit Nicht-MFC-Anwendungen finden Sie auch im Artikel [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md).

## <a name="the-csocket-programming-model"></a><a name="_core_the_csocket_programming_model"></a>Das CSocket-Programmiermodell

Die `CSocket` Verwendung eines Objekts umfasst das Erstellen und Zuordnen mehrerer MFC-Klassenobjekte. Im allgemeinen Verfahren unten wird jeder Schritt sowohl vom Serversocket als auch vom Clientsocket ausgeführt, mit Ausnahme von Schritt 3, in dem jeder Sockettyp eine andere Aktion erfordert.

> [!TIP]
> Zur Laufzeit beginnt die Serveranwendung in der Regel zuerst, bereit zu sein und "zuzuhören", wenn die Clientanwendung eine Verbindung sucht. Wenn der Server nicht bereit ist, wenn der Client versucht, eine Verbindung herzustellen, müssen Sie in der Regel die Benutzeranwendung später erneut versuchen.

#### <a name="to-set-up-communication-between-a-server-socket-and-a-client-socket"></a>So richten Sie die Kommunikation zwischen einem Serversocket und einem Clientsocket ein

1. Erstellen Sie ein [CSocket-Objekt.](../mfc/reference/csocket-class.md)

1. Verwenden Sie das Objekt, um das zugrunde liegende **SOCKET-Handle** zu erstellen.

   Für `CSocket` ein Clientobjekt sollten Sie normalerweise die Standardparameter für [Erstellen](../mfc/reference/casyncsocket-class.md#create)verwenden, es sei denn, Sie benötigen einen Datagrammsocket. Für `CSocket` ein Serverobjekt müssen Sie einen `Create` Port im Aufruf angeben.

    > [!NOTE]
    >  `CArchive`funktioniert nicht mit Datagramm-Sockets. Wenn Sie für `CSocket` einen Datagrammsocket verwenden möchten, müssen Sie `CAsyncSocket`die Klasse wie möglich verwenden, d. h. ohne Archiv. Da Datagramme unzuverlässig sind (nicht garantiert ankommen und wiederholt oder aviniert werden können), sind sie nicht mit der Serialisierung über ein Archiv kompatibel. Sie erwarten, dass ein Serialisierungsvorgang zuverlässig und nacheinander abgeschlossen wird. Wenn Sie versuchen, `CArchive` mit einem Objekt für ein Datagramm zu verwenden, `CSocket` schlägt eine MFC-Assertion fehl.

1. Wenn es sich bei dem Socket um einen Client handelt, rufen Sie [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect) auf, um das Socketobjekt mit einem Serversocket zu verbinden.

     - oder -

   Wenn es sich bei dem Socket um einen Server handelt, rufen Sie [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen) auf, um mit dem Abhören von Verbindungsversuchen von einem Client zu beginnen. Akzeptieren Sie diese beim Empfang einer Verbindungsanforderung, indem Sie [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept)aufrufen.

    > [!NOTE]
    >  Die `Accept` Memberfunktion nimmt einen Verweis `CSocket` auf ein neues, leeres Objekt als Parameter. Sie müssen dieses Objekt `Accept`erstellen, bevor Sie aufrufen. Wenn dieses Socketobjekt den Gültigkeitsbereich verlässt, wird die Verbindung geschlossen. Rufen `Create` Sie dieses neue Socketobjekt nicht auf.

1. Erstellen Sie ein [CSocketFile-Objekt,](../mfc/reference/csocketfile-class.md) das ihm das `CSocket` Objekt zudiesem zuzuordnen.

1. Erstellen Sie ein [CArchive-Objekt](../mfc/reference/carchive-class.md) zum Laden (Empfangen) oder Speichern (Senden) von Daten. Das Archiv ist `CSocketFile` dem Objekt zugeordnet.

   Beachten Sie, `CArchive` dass dies nicht mit Datagrammsockets funktioniert.

1. Verwenden `CArchive` Sie das Objekt, um Daten zwischen dem Client- und dem Serversocket zu übergeben.

   Beachten Sie, dass `CArchive` ein bestimmtes Objekt Daten nur in eine Richtung verschiebt: entweder zum Laden (Empfangen) oder speichern (Senden). In einigen Fällen verwenden `CArchive` Sie zwei Objekte: eines zum Senden von Daten, das andere zum Empfangen von Bestätigungen.

   Nachdem Sie eine Verbindung akzeptiert und das Archiv eingerichtet haben, können Sie Aufgaben wie die Überprüfung von Kennwörtern ausführen.

1. Zerstören Sie das Archiv, die Socketdatei und die Socketobjekte.

    > [!NOTE]
    >  Die `CArchive` Klasse `IsBufferEmpty` liefert die Memberfunktion `CSocket`speziell für die Verwendung mit class . Wenn der Puffer z. B. mehrere Datenmeldungen enthält, müssen Sie eine Schleife durchlaufen, bis alle gelesen und der Puffer gelöscht ist. Andernfalls kann sich Ihre nächste Benachrichtigung, dass Daten empfangen werden sollen, auf unbestimmte Zeit verzögern. Verwenden `IsBufferEmpty` Sie diese Datei, um sicherzustellen, dass Sie alle Daten abrufen.

Der Artikel [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md) veranschaulicht beide Seiten dieses Prozesses mit Beispielcode.

Weitere Informationen finden Sie unter

- [Windows Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CSocket::Erstellen](../mfc/reference/csocket-class.md#create)
