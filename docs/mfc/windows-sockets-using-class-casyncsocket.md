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
ms.openlocfilehash: 6a3b3469b908eaf6f8062b8db7fc4287606b7f02
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228504"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Verwenden der Klasse CAsyncSocket

In diesem Artikel wird die Verwendung der [CAsyncSocket](../mfc/reference/casyncsocket-class.md)-Klasse erläutert. Beachten Sie, dass diese Klasse die Windows Sockets-API auf einer sehr niedrigen Ebene kapselt. `CAsyncSocket`dient der Verwendung durch Programmierer, die die Netzwerkkommunikation detailliert kennen, aber die benutzerfreundliche Benachrichtigung über Netzwerkereignisse benötigen. Basierend auf dieser Annahme bietet dieser Artikel nur eine einfache Anweisung. Sie sollten die Verwendung von in Erwägung gezogen haben `CAsyncSocket` , wenn Sie die einfache Handhabung von Windows Sockets mit mehreren Netzwerkprotokollen in einer MFC-Anwendung in Erwägung gezogen haben möchten, aber keine Flexibilität Opfern möchten. Vielleicht haben Sie auch die Meinung, dass Sie eine bessere Effizienz erzielen können, indem Sie die Kommunikation direkter programmieren, als Sie das allgemeinere Alternative Modell der Klasse verwenden können `CSocket` .

`CAsyncSocket`ist in der *MFC-Referenz*dokumentiert. Visual C++ bietet auch die Windows Sockets-Spezifikation, die sich in der Windows SDK befindet. Die Details werden Ihnen angezeigt. Visual C++ stellt keine Beispielanwendung für bereit `CAsyncSocket` .

Wenn Sie die Netzwerkkommunikation nicht kennen und eine einfache Lösung benötigen, verwenden Sie die [CSocket](../mfc/reference/csocket-class.md) -Klasse mit einem- `CArchive` Objekt. Weitere Informationen finden [Sie unter Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md) .

In diesem Artikel wird Folgendes behandelt:

- Erstellen und Verwenden eines- `CAsyncSocket` Objekts.

- [Ihre Zuständigkeiten mit CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Erstellen und Verwenden eines CAsyncSocket-Objekts

#### <a name="to-use-casyncsocket"></a>So verwenden Sie CAsyncSocket

1. Erstellen Sie ein [CAsyncSocket](../mfc/reference/casyncsocket-class.md) -Objekt, und verwenden Sie das-Objekt zum Erstellen des zugrunde liegenden **Sockethandles** .

   Die Erstellung eines Sockets folgt dem MFC-Muster der zweistufigen Konstruktion.

   Zum Beispiel:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     - oder -

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Der erste oben genannte Konstruktor erstellt ein- `CAsyncSocket` Objekt auf dem Stapel. Mit dem zweiten Konstruktor wird ein `CAsyncSocket` auf dem Heap erstellt. Der erste oben genannte [Create](../mfc/reference/casyncsocket-class.md#create) -Befehl verwendet die Standardparameter zum Erstellen eines Stream-Sockets. Der zweite-Befehl `Create` erstellt einen Datagramm-Socket mit einem angegebenen Port und einer angegebenen Adresse. (Sie können beide `Create` Versionen mit einer der beiden Konstruktionsmethoden verwenden.)

   Die Parameter für lauten `Create` :

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
    >  Die `Accept` Member-Funktion nimmt einen Verweis auf ein neues, leeres- `CSocket` Objekt als Parameter auf. Sie müssen dieses Objekt erstellen, bevor Sie aufzurufen `Accept` . Wenn dieses Socketobjekt den Gültigkeitsbereich verlässt, wird die Verbindung geschlossen. `Create`Für dieses neue Socketobjekt nicht aufzurufen. Ein Beispiel finden Sie im Artikel [Windows Sockets: Sequenz von Vorgängen](../mfc/windows-sockets-sequence-of-operations.md).

1. Führen Sie die Kommunikation mit anderen Sockets aus, indem Sie die Element Funktionen des- `CAsyncSocket` Objekts aufrufen, die die Windows Sockets-API-Funktionen kapseln.

   Weitere Informationen finden Sie unter Windows Sockets Specification und Class [CAsyncSocket](../mfc/reference/casyncsocket-class.md) in der *MFC-Referenz*.

1. Zerstört das- `CAsyncSocket` Objekt.

   Wenn Sie das Socket-Objekt auf dem Stapel erstellt haben, wird dessen Dekonstruktor aufgerufen, wenn die enthaltende Funktion den Gültigkeitsbereich verlässt. Wenn Sie das Socketobjekt auf dem Heap mithilfe des- **`new`** Operators erstellt haben, sind Sie dafür verantwortlich, den- **`delete`** Operator zum Zerstören des Objekts zu verwenden.

   Der destrukturtor Ruft die [Close](../mfc/reference/casyncsocket-class.md#close) -Member-Funktion des Objekts auf, bevor das Objekt zerstört wird.

Ein Beispiel für diese Sequenz im Code (tatsächlich für ein- `CSocket` Objekt) finden Sie unter [Windows Sockets: Sequenz von Vorgängen](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Ihre Zuständigkeiten mit CAsyncSocket

Wenn Sie ein Objekt der Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)erstellen, kapselt das-Objekt ein Windows- **Sockethandle** und stellt Vorgänge für dieses Handle bereit. Wenn Sie verwenden `CAsyncSocket` , müssen Sie alle Probleme behandeln, die auftreten können, wenn Sie die API direkt verwenden. Beispiel:

- Blockierende Szenarien.

- Byte Reihen folgen Unterschiede zwischen den sendenden und empfangenden Computern.

- Zwischen Unicode-und MBCS-Zeichen folgen (Multibytezeichen-Zeichensatz).

Definitionen dieser Begriffe und zusätzlichen Informationen finden Sie unter [Windows Sockets: blockieren](../mfc/windows-sockets-blocking.md), [Windows Sockets: Byte Reihen](../mfc/windows-sockets-byte-ordering.md)Folge, [Windows Sockets: Zeichen folgen Umwandlungen](../mfc/windows-sockets-converting-strings.md).

Trotz dieser Probleme ist `CAsycnSocket` die Klasse möglicherweise die richtige Wahl für Sie, wenn Ihre Anwendung die gesamte Flexibilität und Kontrolle erfordert, die Sie erhalten können. Falls nicht, sollten Sie stattdessen die Verwendung der-Klasse in Erwägung gezogen `CSocket` . `CSocket`Blendet eine Menge von Details aus: Sie pumpt Windows-Meldungen während blockierender Aufrufe und ermöglicht Ihnen den Zugriff auf `CArchive` , der die Byte Reihenfolge-Unterschiede und die Zeichen folgen Konvertierung für Sie verwaltet.

Weitere Informationen finden Sie unter

- [Windows-Sockets: Hintergrund](../mfc/windows-sockets-background.md)

- [Windows-Sockets: Streamsockets](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagramm-Sockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
