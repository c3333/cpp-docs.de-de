---
title: 'Windows Sockets: Bytereihenfolge'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: f00936f3de07df8c1e4d9df1c678b2cfd5f3e3ad
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226801"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Bytereihenfolge

In diesem Artikel und in zwei begleitenden Artikeln werden verschiedene Probleme bei der Windows Sockets-Programmierung erläutert. Dieser Artikel behandelt die Byte-Reihenfolge. Die anderen Probleme werden in den folgenden Artikeln behandelt: [Windows Sockets: Blockierung](../mfc/windows-sockets-blocking.md) und [Windows Sockets: umstellen](../mfc/windows-sockets-converting-strings.md)von Zeichen folgen.

Wenn Sie die Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)verwenden oder davon ableiten, müssen Sie diese Probleme selbst verwalten. Wenn Sie die [CSocket](../mfc/reference/csocket-class.md)-Klasse verwenden oder davon ableiten, werden Sie von MFC für Sie verwaltet.

## <a name="byte-ordering"></a>Bytereihenfolge

Unterschiedliche Computerarchitekturen speichern manchmal Daten mit unterschiedlichen Byte Aufträgen. Beispielsweise speichern Intel-basierte Computer Daten in umgekehrter Reihenfolge von Macintosh-Computern (Motorola). Die Intel-Byte-Reihenfolge, die als "Little-Endian" bezeichnet wird, ist auch die umgekehrte Reihenfolge des Netzwerkstandards "Big-Endian". In der folgenden Tabelle werden diese Begriffe erläutert.

### <a name="big--and-little-endian-byte-ordering"></a>Big-und Little-Endian-Byte Reihenfolge

|Bytereihenfolge|Bedeutung|
|-------------------|-------------|
|Big-tedian|Das signifikanteste Byte befindet sich am linken Ende eines Worts.|
|Little-d|Das signifikanteste Byte befindet sich am rechten Ende eines Worts.|

In der Regel müssen Sie sich keine Gedanken über die Byte Reihenfolge für Daten machen, die Sie über das Netzwerk senden und empfangen. es gibt jedoch Situationen, in denen Sie Byte Bestellungen konvertieren müssen.

## <a name="when-you-must-convert-byte-orders"></a>Wenn Sie Byte Bestellungen konvertieren müssen

Sie müssen Byte Bestellungen in den folgenden Situationen konvertieren:

- Sie übergeben Informationen, die vom Netzwerk interpretiert werden müssen, im Gegensatz zu den Daten, die Sie an einen anderen Computer senden. Beispielsweise können Sie Ports und Adressen übergeben, die das Netzwerk verstehen muss.

- Die Serveranwendung, mit der Sie kommunizieren, ist keine MFC-Anwendung (und Sie haben keinen Quellcode dafür). Dadurch wird die Konvertierung von Byte Reihenfolgen aufgerufen, wenn die beiden Computer nicht die gleiche Byte Reihenfolge aufweisen.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Wenn Sie keine Byte Bestellungen konvertieren müssen

In den folgenden Situationen können Sie die Verarbeitung von Byte Bestellungen vermeiden:

- Die Computer an beiden Enden können zustimmen, dass Sie keine Bytes austauschen, und beide Computer verwenden dieselbe Byte Reihenfolge.

- Der Server, mit dem Sie kommunizieren, ist eine MFC-Anwendung.

- Sie verfügen über Quellcode für den Server, mit dem Sie kommunizieren, sodass Sie explizit feststellen können, ob Sie Byte Bestellungen konvertieren müssen oder nicht.

- Sie können den Server auf MFC portieren. Dies ist recht einfach, und das Ergebnis ist normalerweise kleiner, schnellerer Code.

Bei der Arbeit mit [CAsyncSocket](../mfc/reference/casyncsocket-class.md)müssen Sie ggf. alle notwendigen Konvertierungen der Byte Reihenfolge verwalten. Windows Sockets vereinheitlicht das byteorder-Modell "Big-Endian" und stellt Funktionen bereit, um zwischen dieser Bestellung und anderen zu konvertieren. Wenn Sie jedoch mit [CSocket](../mfc/reference/csocket-class.md) [verwenden, wird](../mfc/reference/carchive-class.md)die umgekehrte Reihenfolge ("Little-Endian") verwendet, aber `CArchive` die Details der Byte Reihenfolge-Konvertierungen werden für Sie übernommen. Wenn Sie diese Standardsortierung in Ihren Anwendungen verwenden oder Windows Sockets Byte-Order-Konvertierungs Funktionen verwenden, können Sie Ihren Code portabler gestalten.

Das ideale Argument für die Verwendung von MFC-Sockets ist, wenn Sie beide Enden der Kommunikation schreiben und dabei eine MFC-Bibliothek an beiden Enden verwenden. Wenn Sie eine Anwendung schreiben, die mit nicht-MFC-Anwendungen, wie z. b. einem FTP-Server, kommunizieren soll, müssen Sie das Byte-austauschen wahrscheinlich selbst verwalten, bevor Sie Daten an das Archive-Objekt übergeben. verwenden Sie dazu die Windows Sockets-Konvertierungs Routinen **NUM HS**, **nbyhl**, **htons**und **htonl**. Ein Beispiel für diese Funktionen, die für die Kommunikation mit einer nicht-MFC-Anwendung verwendet werden, wird weiter unten in diesem Artikel angezeigt.

> [!NOTE]
> Wenn das andere Ende der Kommunikation keine MFC-Anwendung ist, müssen Sie auch das Streaming von C++-Objekten, die von abgeleitet werden, `CObject` in Ihr Archiv vermeiden, da der Empfänger Sie nicht verarbeiten kann. Weitere Informationen finden Sie unter [Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md).

Weitere Informationen zu Byte Bestellungen finden Sie in der Windows Sockets-Spezifikation, die in der Windows SDK verfügbar ist.

## <a name="a-byte-order-conversion-example"></a>Beispiel für eine Konvertierung in Byte Reihenfolge

Das folgende Beispiel zeigt eine Serialisierungsfunktion für ein- `CSocket` Objekt, das ein-Archiv verwendet. Außerdem wird die Verwendung der Byte Reihenfolge-Konvertierungs Funktionen in der Windows Sockets-API veranschaulicht.

Dieses Beispiel zeigt ein Szenario, in dem Sie einen Client schreiben, der mit einer nicht-MFC-Serveranwendung kommuniziert, für die Sie keinen Zugriff auf den Quellcode haben. In diesem Szenario müssen Sie davon ausgehen, dass der nicht-MFC-Server die Standard-Netzwerk-Byte Reihenfolge verwendet. Im Gegensatz dazu verwendet die MFC-Client Anwendung ein `CArchive` -Objekt mit einem `CSocket` -Objekt und `CArchive` verwendet die Byte Reihenfolge "Little-Endian", das Gegenteil des Netzwerkstandards.

Angenommen, der nicht-MFC-Server, mit dem Sie kommunizieren möchten, verfügt über ein Erfassungs Protokoll für ein Nachrichten Paket wie den folgenden:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

In MFC-begriffen würde dies wie folgt ausgedrückt werden:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

In C++ ist ein im **`struct`** Grunde das gleiche wie eine Klasse. Die- `Message` Struktur kann über Member-Funktionen verfügen, z `Serialize` . b. die oben deklarierte Element Funktion. Die `Serialize` Member-Funktion könnte wie folgt aussehen:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

In diesem Beispiel wird die Konvertierung von Daten in Byte Reihenfolge aufgerufen, da es einen eindeutigen Konflikt zwischen der Byte Reihenfolge der nicht-MFC-Serveranwendung an einem Ende und dem, das `CArchive` in der MFC-Client Anwendung am anderen Ende verwendet wird, gibt. Das Beispiel veranschaulicht einige der von Windows Sockets bereitgestellten Byte Reihen folgen Konvertierungs Funktionen. In der folgenden Tabelle werden diese Funktionen beschrieben.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Umwandlungs Funktionen für die Byte Reihenfolge von Windows Sockets

|Funktion|Zweck|
|--------------|-------------|
|**NUM**|Konvertieren einer 16-Bit-Menge aus der Netzwerk-Byte-Reihenfolge in die Host-Byte Reihenfolge (Big-Endian in Little-Endian).|
|**nzu HLS**|Konvertieren einer 32-Bit-Menge von der Netzwerk-Byte-Reihenfolge in die Host-Byte Reihenfolge (Big-Endian in Little-Endian).|
|**Htonnen**|Konvertiert eine 16-Bit-Menge von der Host-Byte-Reihenfolge in die Netzwerk-Byte Reihenfolge (Little-Endian in Big-Endian).|
|**Htonl**|Konvertieren einer 32-Bit-Menge von der Host-Byte Reihenfolge in die Netzwerk-Byte Reihenfolge (Little-Endian in Big-Endian).|

Ein weiterer Punkt dieses Beispiels ist, dass die socketanwendung am anderen Ende der Kommunikation eine nicht-MFC-Anwendung ist. Sie müssen beispielsweise Folgendes vermeiden:

`ar << pMsg;`

dabei `pMsg` ist ein Zeiger auf ein C++-Objekt, das von der-Klasse abgeleitet ist `CObject` . Dadurch werden zusätzliche MFC-Informationen gesendet, die Objekten zugeordnet sind, und der Server versteht dies nicht, wie es bei einer MFC-Anwendung der Fall wäre.

Weitere Informationen finden Sie unter

- [Windows Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows-Sockets: Hintergrund](../mfc/windows-sockets-background.md)

- [Windows-Sockets: Streamsockets](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagramm-Sockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
