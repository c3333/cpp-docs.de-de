---
title: 'Windows Sockets: Bytereihenfolge'
ms.date: 11/04/2016
helpviewer_keywords:
- byte order issues in sockets programming
- sockets [MFC], byte order issues
- Windows Sockets [MFC], byte order issues
ms.assetid: 8a787a65-f9f4-4002-a02f-ac25a5dace5d
ms.openlocfilehash: 50548202483c4d9d4471ad2c600270c4df4503e7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371070"
---
# <a name="windows-sockets-byte-ordering"></a>Windows Sockets: Bytereihenfolge

In diesem Artikel und zwei Begleitartikeln werden mehrere Probleme in der Windows Sockets-Programmierung erläutert. Dieser Artikel behandelt byte Ordering. Die anderen Probleme werden in den Artikeln behandelt: [Windows Sockets: Blocking](../mfc/windows-sockets-blocking.md) and [Windows Sockets: Converting Strings](../mfc/windows-sockets-converting-strings.md).

Wenn Sie die Klasse [CAsyncSocket](../mfc/reference/casyncsocket-class.md)verwenden oder von ihr ableiten, müssen Sie diese Probleme selbst verwalten. Wenn Sie die Klasse [CSocket](../mfc/reference/csocket-class.md)verwenden oder von ihr ableiten, verwaltet MFC sie für Sie.

## <a name="byte-ordering"></a>Bytereihenfolge

Verschiedene Maschinenarchitekturen speichern manchmal Daten mit unterschiedlichen Byteaufträgen. Beispielsweise speichern Intel-basierte Maschinen Daten in der umgekehrten Reihenfolge von Macintosh-Maschinen (Motorola). Die Intel Byte-Order, genannt "little-Endian", ist auch das Gegenteil der Netzwerkstandard-"Big-Endian"-Reihenfolge. In der folgenden Tabelle werden diese Begriffe erläutert.

### <a name="big--and-little-endian-byte-ordering"></a>Big- und Little-Endian Byte-Bestellung

|Bytereihenfolge|Bedeutung|
|-------------------|-------------|
|Big-Endian|Das bedeutendste Byte befindet sich am linken Ende eines Wortes.|
|Little-Endian|Das bedeutendste Byte befindet sich am rechten Ende eines Wortes.|

In der Regel müssen Sie sich keine Gedanken über die Bytereihenfolgekonvertierung für Daten machen, die Sie über das Netzwerk senden und empfangen, aber es gibt Situationen, in denen Sie Byteaufträge konvertieren müssen.

## <a name="when-you-must-convert-byte-orders"></a>Wenn Sie Byte-Orders konvertieren müssen

Sie müssen Byteaufträge in den folgenden Situationen konvertieren:

- Sie übergeben Informationen, die vom Netzwerk interpretiert werden müssen, im Gegensatz zu den Daten, die Sie an einen anderen Computer senden. Sie können z. B. Ports und Adressen übergeben, die das Netzwerk verstehen muss.

- Die Serveranwendung, mit der Sie kommunizieren, ist keine MFC-Anwendung (und Sie haben keinen Quellcode dafür). Dies erfordert Byteauftragskonvertierungen, wenn die beiden Computer nicht dieselbe Bytereihenfolge verwenden.

## <a name="when-you-do-not-have-to-convert-byte-orders"></a>Wenn Sie Byte-Orders nicht konvertieren müssen

Sie können die Arbeit der Konvertierung von Byteaufträgen in den folgenden Situationen vermeiden:

- Die Computer an beiden Enden können sich darauf einigen, keine Bytes zu tauschen, und beide Computer verwenden die gleiche Bytereihenfolge.

- Der Server, mit dem Sie kommunizieren, ist eine MFC-Anwendung.

- Sie haben Quellcode für den Server, mit dem Sie kommunizieren, sodass Sie explizit feststellen können, ob Sie Byteaufträge konvertieren müssen oder nicht.

- Sie können den Server auf MFC portieren. Dies ist ziemlich einfach zu tun, und das Ergebnis ist in der Regel kleiner, schneller Code.

Wenn Sie mit [CAsyncSocket](../mfc/reference/casyncsocket-class.md)arbeiten, müssen Sie alle erforderlichen Byte-Order-Konvertierungen selbst verwalten. Windows Sockets standardisiert das "big-Endian"-Byte-Order-Modell und bietet Funktionen, die zwischen dieser Order und anderen konvertiert werden können. [CArchive](../mfc/reference/carchive-class.md), das Sie jedoch mit [CSocket](../mfc/reference/csocket-class.md)verwenden, verwendet die entgegengesetzte ("little-Endian") Reihenfolge, kümmert sich aber `CArchive` um die Details der Byte-Order-Konvertierungen für Sie. Durch die Verwendung dieser Standardreihenfolge in Ihren Anwendungen oder die Verwendung von Konvertierungsfunktionen für Windows Sockets byte-order können Sie Ihren Code portabler gestalten.

Das ideale Argument für die Verwendung von MFC-Sockets ist, wenn Sie beide Enden der Kommunikation schreiben und dabei eine MFC-Bibliothek an beiden Enden verwenden. Wenn Sie eine Anwendung schreiben, die mit Nicht-MFC-Anwendungen kommuniziert, z. B. einem FTP-Server, müssen Sie das Byte-Swapping wahrscheinlich selbst verwalten, bevor Sie Daten an das Archivobjekt übergeben, indem Sie die Konvertierungsroutinen **ntohs**, **ntohl**, **htons**und **htonl**verwenden. Ein Beispiel für diese Funktionen, die bei der Kommunikation mit einer Nicht-MFC-Anwendung verwendet werden, wird weiter unten in diesem Artikel angezeigt.

> [!NOTE]
> Wenn das andere Ende der Kommunikation keine MFC-Anwendung ist, müssen Sie `CObject` auch vermeiden, C++-Objekte, die von Ihrem Archiv abgeleitet wurden, zu streamen, da der Empfänger sie nicht verarbeiten kann. Siehe Hinweis in [Windows Sockets: Verwenden von Sockets mit Archiven](../mfc/windows-sockets-using-sockets-with-archives.md).

Weitere Informationen zu Byteaufträgen finden Sie in der Windows Sockets-Spezifikation, die im Windows SDK verfügbar ist.

## <a name="a-byte-order-conversion-example"></a>Ein Byte-Order-Konvertierungsbeispiel

Das folgende Beispiel zeigt eine `CSocket` Serialisierungsfunktion für ein Objekt, das ein Archiv verwendet. Außerdem wird die Verwendung der Konvertierungsfunktionen für Bytereihenfolge in der Windows Sockets-API veranschaulicht.

In diesem Beispiel wird ein Szenario dargestellt, in dem Sie einen Client schreiben, der mit einer Nicht-MFC-Serveranwendung kommuniziert, für die Sie keinen Zugriff auf den Quellcode haben. In diesem Szenario müssen Sie davon ausgehen, dass der Nicht-MFC-Server die Standardmäßige Netzwerkbytereihenfolge verwendet. Im Gegensatz dazu verwendet Ihre `CArchive` MFC-Clientanwendung ein Objekt mit einem `CSocket` Objekt und `CArchive` die "little-Endian"-Bytereihenfolge, das Gegenteil des Netzwerkstandards.

Angenommen, der Nicht-MFC-Server, mit dem Sie kommunizieren möchten, verfügt über ein etabliertes Protokoll für ein Nachrichtenpaket wie das folgende:

[!code-cpp[NVC_MFCSimpleSocket#5](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_1.cpp)]

MFC-Begriffe würden wie folgt ausgedrückt:

[!code-cpp[NVC_MFCSimpleSocket#6](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_2.cpp)]

In C++ ist eine **Struktur** im Wesentlichen dasselbe wie eine Klasse. Die `Message` Struktur kann Memberfunktionen haben, z. B. die `Serialize` oben deklarierte Memberfunktion. Die `Serialize` Memberfunktion könnte wie folgt aussehen:

[!code-cpp[NVC_MFCSimpleSocket#7](../mfc/codesnippet/cpp/windows-sockets-byte-ordering_3.cpp)]

In diesem Beispiel werden Bytereihenfolgekonvertierungen von Daten gefordert, da eine eindeutige Diskrepanz zwischen der Bytereihenfolge `CArchive` der Nicht-MFC-Serveranwendung an einem Ende und der in Ihrer MFC-Clientanwendung am anderen Ende verwendeten Seite besteht. Das Beispiel veranschaulicht mehrere Konvertierungsfunktionen für Bytereihenfolge, die Windows Sockets bereitstellt. In der folgenden Tabelle werden diese Funktionen beschrieben.

### <a name="windows-sockets-byte-order-conversion-functions"></a>Windows Sockets Byte-Order Konvertierungsfunktionen

|Funktion|Zweck|
|--------------|-------------|
|**ntohs**|Konvertieren Sie eine 16-Bit-Menge aus der Netzwerkbytereihenfolge in die Host-Bytereihenfolge (big-Endian in little-Endian).|
|**ntohl**|Konvertieren Sie eine 32-Bit-Menge aus der Netzwerkbytereihenfolge in die Host-Bytereihenfolge (big-Endian in little-Endian).|
|**Htons**|Konvertieren Sie eine 16-Bit-Menge aus hostbyte order in Network Byte Order (little-Endian to big-Endian).|
|**Htonl**|Konvertieren Sie eine 32-Bit-Menge aus hostbyte order in Network Byte Order (little-Endian to big-Endian).|

Ein weiterer Punkt dieses Beispiels ist, dass, wenn die Socketanwendung am anderen Ende der Kommunikation eine Nicht-MFC-Anwendung ist, Sie vermeiden müssen, so etwas wie das folgende zu tun:

`ar << pMsg;`

wobei `pMsg` ein Zeiger auf ein C++-Objekt von der Klasse `CObject`abgeleitet ist. Dadurch werden zusätzliche MFC-Informationen gesendet, die Objekten zugeordnet sind, und der Server versteht sie nicht, wie es bei einer MFC-Anwendung der Fall wäre.

Weitere Informationen finden Sie unter

- [Windows Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows Sockets: Hintergrund](../mfc/windows-sockets-background.md)

- [Windows Sockets: Blockieren](../mfc/windows-sockets-stream-sockets.md)

- [Windows Sockets: Datagrammsockets](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
