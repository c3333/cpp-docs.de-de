---
title: 'Windows Sockets: Verwenden der Klasse CAsyncSocket'
ms.date: 11/04/2016
helpviewer_keywords:
- CAsyncSocket class [MFC], programming model
- Windows Sockets [MFC], asynchronous
- sockets [MFC], converting between Unicode and MBCS strings
- SOCKET handle
- sockets [MFC], asynchronous operation
- Windows Sockets [MFC], converting Unicode and MBCS strings
ms.assetid: 825dae17-7c1b-4b86-8d6c-da7f1afb5d8d
ms.openlocfilehash: 3977308776c4ec6fed844038c4453ad03d065f98
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445943"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Verwenden der Klasse CAsyncSocket

In diesem Artikel wird die Verwendung der [CAsyncSocket](../mfc/reference/casyncsocket-class.md)-Klasse erläutert. Beachten Sie, dass diese Klasse die Windows Sockets-API auf einer sehr niedrigen Ebene kapselt. `CAsyncSocket` ist zur Verwendung durch Programmierer gedacht, die die Netzwerkkommunikation detailliert kennen, aber die benutzerfreundliche Benachrichtigung über Netzwerkereignisse benötigen. Basierend auf dieser Annahme bietet dieser Artikel nur eine einfache Anweisung. Sie sollten die Verwendung von `CAsyncSocket` in Erwägung gezogen haben, wenn Sie die einfache Handhabung von Windows Sockets mit mehreren Netzwerkprotokollen in einer MFC-Anwendung in Erwägung gezogen möchten, aber keine Flexibilität Opfern möchten. Vielleicht haben Sie auch die Meinung, dass Sie eine bessere Effizienz erzielen können, indem Sie die Kommunikation direkter programmieren, als Sie das allgemeinere Alternative Modell der Klasse `CSocket`verwenden können.

`CAsyncSocket` ist in der *MFC-Referenz*dokumentiert. Visual C++ liefert auch die Windows Sockets-Spezifikation, die sich im Windows SDK befindet. Die Details werden Ihnen angezeigt. Visual C++ stellt keine Beispielanwendung für `CAsyncSocket`bereit.

Wenn Sie die Netzwerkkommunikation nicht kennen und eine einfache Lösung benötigen, verwenden Sie die [CSocket](../mfc/reference/csocket-class.md) -Klasse mit einem `CArchive`-Objekt. Weitere Informationen finden [Sie unter Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md) .

In diesem Artikel wird Folgendes behandelt:

- Erstellen und Verwenden eines `CAsyncSocket` Objekts.

- [Ihre Zuständigkeiten mit CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

##  <a name="_core_creating_and_using_a_casyncsocket_object"></a>Erstellen und Verwenden eines CAsyncSocket-Objekts

#### <a name="to-use-casyncsocket"></a>So verwenden Sie CAsyncSocket

1. Erstellen Sie ein [CAsyncSocket](../mfc/reference/casyncsocket-class.md) -Objekt, und verwenden Sie das-Objekt zum Erstellen des zugrunde liegenden **Sockethandles** .

   Die Erstellung eines Sockets folgt dem MFC-Muster der zweistufigen Konstruktion.

   Beispiel:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     Oder

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Der erste oben genannte Konstruktor erstellt ein `CAsyncSocket` Objekt auf dem Stapel. Der zweite Konstruktor erstellt eine `CAsyncSocket` auf dem Heap. Der erste oben genannte [Create](../mfc/reference/casyncsocket-class.md#create) -Befehl verwendet die Standardparameter zum Erstellen eines Stream-Sockets. Der zweite `Create`-aufrufsvorgang erstellt einen Datagrammsocket mit einem angegebenen Port und einer angegebenen Adresse. (Sie können entweder `Create`-Version mit einer der beiden Konstruktionsmethoden verwenden.)

   Die zu `Create` Parameter lauten wie folgt:

   - Ein "Port": eine kurze Ganzzahl.

      Für einen Serversocket müssen Sie einen Port angeben. Bei einem Clientsocket akzeptieren Sie in der Regel den Standardwert für diesen Parameter, mit dem Windows Sockets einen Port auswählen kann.

   - Ein socketyp: **SOCK_STREAM** (Standard) oder **SOCK_DGRAM**.

   - Eine Socketadresse, z. b. "FTP.Microsoft.com" oder "128.56.22.8".

      Dies ist die IP-Adresse (Internet Protocol) im Netzwerk. Wahrscheinlich verlassen Sie sich immer auf den Standardwert für diesen Parameter.

   Die Begriffe "Port" und "Socketadresse" werden in [Windows Sockets: Ports und Socketadressen](../mfc/windows-sockets-ports-and-socket-addresses.md)erläutert.

1. Wenn der Socket ein Client ist, verbinden Sie das Socketobjekt mit einem Serversocket mithilfe von [CAsyncSocket:: Connect](../mfc/reference/casyncsocket-class.md#connect).

     Oder

   Wenn der Socket ein Server ist, legen Sie den Socket so fest, dass er mit dem lauschen (mit [CAsyncSocket:: lauschen](../mfc/reference/casyncsocket-class.md#listen)) für Verbindungsversuche von einem Client beginnt. Wenn Sie eine Verbindungsanforderung empfangen, akzeptieren Sie Sie mit [CAsyncSocket:: Accept](../mfc/reference/casyncsocket-class.md#accept).

   Nachdem Sie eine Verbindung akzeptiert haben, können Sie Aufgaben wie das Überprüfen von Kenn Wörtern ausführen.

    > [!NOTE]
    >  Die `Accept` Member-Funktion nimmt einen Verweis auf ein neues, leeres `CSocket`-Objekt als Parameter auf. Sie müssen dieses Objekt erstellen, bevor Sie `Accept`abrufen. Wenn dieses Socketobjekt den Gültigkeitsbereich verlässt, wird die Verbindung geschlossen. `Create` für dieses neue Socketobjekt nicht aufzurufen. Ein Beispiel finden Sie im Artikel [Windows Sockets: Sequenz von Vorgängen](../mfc/windows-sockets-sequence-of-operations.md).

1. Führen Sie die Kommunikation mit anderen Sockets aus, indem Sie die Element Funktionen des `CAsyncSocket` Objekts aufrufen, die die Windows Sockets-API-Funktionen kapseln.

   Weitere Informationen finden Sie unter Windows Sockets Specification und Class [CAsyncSocket](../mfc/reference/casyncsocket-class.md) in der *MFC-Referenz*.

1. Zerstören Sie das `CAsyncSocket`-Objekt.

   Wenn Sie das Socket-Objekt auf dem Stapel erstellt haben, wird dessen Dekonstruktor aufgerufen, wenn die enthaltende Funktion den Gültigkeitsbereich verlässt. Wenn Sie das Socket-Objekt auf dem Heap mit dem **New** -Operator erstellt haben, sind Sie dafür verantwortlich, den **Delete** -Operator zu verwenden, um das Objekt zu zerstören.

   Der destrukturtor Ruft die [Close](../mfc/reference/casyncsocket-class.md#close) -Member-Funktion des Objekts auf, bevor das Objekt zerstört wird.

Ein Beispiel für diese Sequenz im Code (tatsächlich für ein `CSocket` Objekt) finden Sie unter [Windows Sockets: Sequenz von Vorgängen](../mfc/windows-sockets-sequence-of-operations.md).

##  <a name="_core_your_responsibilities_with_casyncsocket"></a>Ihre Zuständigkeiten mit CAsyncSocket

Wenn Sie ein Objekt der Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)erstellen, kapselt das-Objekt ein Windows- **Sockethandle** und stellt Vorgänge für dieses Handle bereit. Wenn Sie `CAsyncSocket`verwenden, müssen Sie alle Probleme behandeln, die auftreten können, wenn Sie die API direkt verwenden. Beispiel:

- Blockierende Szenarien.

- Byte Reihen folgen Unterschiede zwischen den sendenden und empfangenden Computern.

- Zwischen Unicode-und MBCS-Zeichen folgen (Multibytezeichen-Zeichensatz).

Definitionen dieser Begriffe und zusätzlichen Informationen finden Sie unter [Windows Sockets: blockieren](../mfc/windows-sockets-blocking.md), [Windows Sockets: Byte Reihen](../mfc/windows-sockets-byte-ordering.md)Folge, [Windows Sockets: Zeichen folgen Umwandlungen](../mfc/windows-sockets-converting-strings.md).

Trotz dieser Probleme ist die Klasse `CAsycnSocket` möglicherweise die richtige Wahl für Sie, wenn Ihre Anwendung die gesamte Flexibilität und Kontrolle erfordert, die Sie erhalten können. Falls nicht, sollten Sie stattdessen die Verwendung von Klassen `CSocket` in Erwägung gezogen. `CSocket` blendet eine Menge von Details aus: Sie pumpt Windows-Meldungen während Blockierungs aufrufen und ermöglicht Ihnen den Zugriff auf `CArchive`, das die Unterschiede bei der Byte Reihenfolge und die Zeichen folgen Konvertierung für Sie verwaltet.

Weitere Informationen finden Sie unter

- [Windows-Sockets: Hintergrund](../mfc/windows-sockets-background.md)

- [Windows-Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows-Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Weitere Informationen

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
