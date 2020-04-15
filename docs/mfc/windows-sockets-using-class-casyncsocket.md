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
ms.openlocfilehash: d3fc32d9da54d9cf8c79e9e5de45b81c2ef64a6e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371966"
---
# <a name="windows-sockets-using-class-casyncsocket"></a>Windows Sockets: Verwenden der Klasse CAsyncSocket

In diesem Artikel wird erläutert, wie die Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)verwendet wird. Beachten Sie, dass diese Klasse die Windows Sockets-API auf einem sehr niedrigen Niveau kapselt. `CAsyncSocket`ist für Programmierer vorgesehen, die die Netzwerkkommunikation im Detail kennen, aber die Bequemlichkeit von Rückrufen für die Benachrichtigung von Netzwerkereignissen wünschen. Basierend auf dieser Annahme enthält dieser Artikel nur grundlegende Anweisungen. Sie sollten wahrscheinlich `CAsyncSocket` in Betracht ziehen, wenn Sie möchten, dass Windows Sockets mit mehreren Netzwerkprotokollen in einer MFC-Anwendung problemlos umgeht, aber keine Flexibilität opfern möchten. Sie könnten auch das Gefühl haben, dass Sie eine bessere Effizienz erzielen können, `CSocket`indem Sie die Kommunikation direkter selbst programmieren, als Sie das allgemeinere alternative Modell der Klasse verwenden könnten.

`CAsyncSocket`wird in der *MFC-Referenz*dokumentiert. Visual C++ stellt auch die Windows Sockets-Spezifikation bereit, die sich im Windows SDK befindet. Die Details werden Ihnen überlassen. Visual C++ stellt keine Beispielanwendung für `CAsyncSocket`zur Verfügung.

Wenn Sie nicht sehr gut über Die Netzwerkkommunikation befetzbar `CArchive` sind und eine einfache Lösung wünschen, verwenden Sie die Klasse [CSocket](../mfc/reference/csocket-class.md) mit einem Objekt. Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven.](../mfc/windows-sockets-using-sockets-with-archives.md)

In diesem Artikel wird Folgendes behandelt:

- Erstellen und `CAsyncSocket` Verwenden eines Objekts.

- [Ihre Aufgaben bei CAsyncSocket](#_core_your_responsibilities_with_casyncsocket).

## <a name="creating-and-using-a-casyncsocket-object"></a><a name="_core_creating_and_using_a_casyncsocket_object"></a>Erstellen und Verwenden eines CAsyncSocket-Objekts

#### <a name="to-use-casyncsocket"></a>So verwenden Sie CAsyncSocket

1. Erstellen Sie ein [CAsyncSocket-Objekt,](../mfc/reference/casyncsocket-class.md) und verwenden Sie das Objekt, um das zugrunde liegende **SOCKET-Handle** zu erstellen.

   Die Erstellung eines Sockels folgt dem MFC-Muster der zweistufigen Konstruktion.

   Beispiel:

   [!code-cpp[NVC_MFCSimpleSocket#3](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_1.cpp)]

     - oder -

   [!code-cpp[NVC_MFCSimpleSocket#4](../mfc/codesnippet/cpp/windows-sockets-using-class-casyncsocket_2.cpp)]

   Der erste Konstruktor `CAsyncSocket` oben erstellt ein Objekt auf dem Stapel. Der zweite Konstruktor `CAsyncSocket` erstellt einen auf dem Heap. Der erste [Create-Aufruf](../mfc/reference/casyncsocket-class.md#create) oben verwendet die Standardparameter, um einen Streamsocket zu erstellen. Der `Create` zweite Aufruf erstellt einen Datagrammsocket mit einem angegebenen Port und einer angegebenen Adresse. (Sie können `Create` beide Versionen mit einer der beiden Konstruktionsmethoden verwenden.)

   Die Parameter `Create` sind:

   - Ein "Port": eine kurze ganze Zahl.

      Für einen Serversocket müssen Sie einen Port angeben. Für einen Clientsocket akzeptieren Sie in der Regel den Standardwert für diesen Parameter, mit dem Windows Sockets einen Port auswählen können.

   - Ein Sockettyp: **SOCK_STREAM** (Standard) oder **SOCK_DGRAM**.

   - Eine Socket-"Adresse" wie "ftp.microsoft.com" oder "128.56.22.8".

      Dies ist Ihre IP-Adresse (Internet Protocol) im Netzwerk. Sie werden sich wahrscheinlich immer auf den Standardwert für diesen Parameter verlassen.

   Die Begriffe "Port" und "Socketadresse" werden in [Windows Sockets: Ports und Socket Addresses](../mfc/windows-sockets-ports-and-socket-addresses.md)erläutert.

1. Wenn es sich bei dem Socket um einen Client handelt, verbinden Sie das Socketobjekt mit einem Serversocket mithilfe von [CAsyncSocket::Connect](../mfc/reference/casyncsocket-class.md#connect).

     - oder -

   Wenn es sich bei dem Socket um einen Server handelt, legen Sie den Socket so fest, dass er (mit [CAsyncSocket::Listen](../mfc/reference/casyncsocket-class.md#listen)) für Verbindungsversuche von einem Client abgehört wird. Akzeptieren Sie diese beim Empfang einer Verbindungsanforderung mit [CAsyncSocket::Accept](../mfc/reference/casyncsocket-class.md#accept).

   Nachdem Sie eine Verbindung akzeptiert haben, können Sie Aufgaben wie das Überprüfen von Kennwörtern ausführen.

    > [!NOTE]
    >  Die `Accept` Memberfunktion nimmt einen Verweis `CSocket` auf ein neues, leeres Objekt als Parameter. Sie müssen dieses Objekt `Accept`erstellen, bevor Sie aufrufen. Wenn dieses Socketobjekt den Gültigkeitsbereich verlässt, wird die Verbindung geschlossen. Rufen `Create` Sie dieses neue Socketobjekt nicht auf. Ein Beispiel finden Sie im Artikel [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

1. Führen Sie die Kommunikation mit `CAsyncSocket` anderen Sockets durch, indem Sie die Memberfunktionen des Objekts aufrufen, die die Windows Sockets-API-Funktionen kapseln.

   Weitere Informationen finden Sie in der Windows Sockets-Spezifikation und der Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md) in der *MFC-Referenz*.

1. Zerstören `CAsyncSocket` Sie das Objekt.

   Wenn Sie das Socketobjekt auf dem Stapel erstellt haben, wird sein Destruktor aufgerufen, wenn die enthaltende Funktion den Gültigkeitsbereich verlässt. Wenn Sie das Socketobjekt auf dem Heap mithilfe des **neuen** Operators erstellt haben, sind Sie dafür verantwortlich, den **Delete-Operator** zum Zerstören des Objekts zu verwenden.

   Der Destruktor ruft [Close](../mfc/reference/casyncsocket-class.md#close) die Close-Memberfunktion des Objekts auf, bevor das Objekt zerstört wird.

Ein Beispiel für diese Sequenz im `CSocket` Code (eigentlich für ein Objekt) finden Sie unter [Windows Sockets: Sequence of Operations](../mfc/windows-sockets-sequence-of-operations.md).

## <a name="your-responsibilities-with-casyncsocket"></a><a name="_core_your_responsibilities_with_casyncsocket"></a>Ihre Aufgaben bei CAsyncSocket

Wenn Sie ein Objekt der Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)erstellen, kapselt das Objekt ein Windows **SOCKET-Handle** und stellt Vorgänge für dieses Handle zur Verfügung. Wenn Sie `CAsyncSocket`verwenden, müssen Sie alle Probleme behandeln, die auftreten können, wenn Sie die API direkt verwenden. Beispiel:

- "Blockieren"-Szenarien.

- Byte-Auftragsunterschiede zwischen den sendenden und empfangenden Maschinen.

- Konvertieren zwischen Unicode- und Multibyte-Zeichensatzzeichenfolgen (MBCS).

Definitionen dieser Begriffe und zusätzliche Informationen finden Sie unter [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md), [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md), Windows [Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Trotz dieser Probleme `CAsycnSocket` kann die Klasse die richtige Wahl für Sie sein, wenn Ihre Anwendung die Flexibilität und Kontrolle erfordert, die Sie erhalten können. Wenn dies nicht der `CSocket` Fall ist, sollten Sie stattdessen die Verwendung von Klasse in Betracht ziehen. `CSocket`versteckt eine Menge Details vor Ihnen: Es pumpt Windows-Nachrichten `CArchive`während der Blockierung von Anrufen und gibt Ihnen Zugriff auf , die Byte Reihenfolge Unterschiede und Zeichenfolgenkonvertierung für Sie verwaltet.

Weitere Informationen finden Sie unter

- [Windows Sockets: Hintergrund](../mfc/windows-sockets-background.md)

- [Windows Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
