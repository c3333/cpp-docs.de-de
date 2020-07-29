---
title: 'Windows Sockets: Beispiel für Sockets mithilfe der Archive'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 275a6c274648225fedcec9d42c280f77af68158e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226775"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Beispiel für Sockets mithilfe der Archive

Dieser Artikel enthält ein Beispiel für die Verwendung von Class [CSocket](../mfc/reference/csocket-class.md). Im Beispiel werden- `CArchive` Objekte verwendet, um Daten über einen Socket zu serialisieren. Beachten Sie, dass dies keine Dokumentserialisierung in eine oder aus einer Datei ist.

Im folgenden Beispiel wird veranschaulicht, wie Sie das Archiv verwenden, um Daten über-Objekte zu senden und zu empfangen `CSocket` . Das Beispiel ist so konzipiert, dass zwei Instanzen der Anwendung (auf demselben Computer oder auf verschiedenen Computern im Netzwerk) Daten austauschen. Eine Instanz sendet Daten, die von der anderen Instanz empfangen und bestätigt werden. Beide Anwendungen können einen Austausch initiieren und können als Server oder als Client für die andere Anwendung fungieren. Die folgende Funktion ist in der Ansichts Klasse der Anwendung definiert:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Der wichtigste Aspekt dieses Beispiels ist, dass die Struktur mit der einer MFC-Funktion vergleichbar ist `Serialize` . Die `PacketSerialize` Member-Funktion besteht aus einer- **`if`** Anweisung mit einer- **`else`** Klausel. Die Funktion empfängt zwei [kardinale](../mfc/reference/carchive-class.md) Verweise als Parameter: *arData* und *arAck*. Wenn das *arData* -Archiv Objekt zum Speichern (senden) festgelegt ist, wird die **`if`** Verzweigung ausgeführt; andernfalls, wenn *arData* für das Laden (empfangen) festgelegt ist, übernimmt die Funktion die **`else`** Verzweigung. Weitere Informationen zur Serialisierung in MFC finden Sie unter [Serialisierung](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> Es wird davon ausgegangen, dass das *arAck* -Archiv Objekt das Gegenteil von *arData*ist. Wenn *' arData '* zum Senden dient, wird *arAck* empfangen, und umgekehrt ist ' true '.

Zum Senden wird die Beispiel Funktion für eine angegebene Anzahl von Wiederholungen durchlaufen, wobei jedes Mal einige Zufallsdaten zu Demonstrationszwecken generiert werden. Die Anwendung würde echte Daten aus einer Quelle, z. b. einer Datei, abrufen. Der einfügeoperator von *arData* Archive ( **<<** ) wird verwendet, um einen Stream von drei aufeinander folgenden Datenblöcken zu senden:

- Ein "Header", der die Art der Daten angibt (in diesem Fall der Wert der *bvalue* -Variablen und die Anzahl der zu sendenden Kopien).

   Beide Elemente werden für dieses Beispiel nach dem Zufallsprinzip generiert.

- Die angegebene Anzahl von Kopien der Daten.

   Die innere **`for`** Schleife sendet *bvalue* so oft wie angegeben.

- Eine Zeichenfolge namens " *strautext* ", die der Empfänger für seinen Benutzer anzeigt.

Für den Empfang funktioniert die-Funktion ähnlich, mit der Ausnahme, dass der Extraktions Operator () des Archivs verwendet wird, **>>** um Daten aus dem Archiv zu erhalten. Die empfangende Anwendung überprüft die empfangenen Daten, zeigt die endgültige Meldung "empfangen" an und sendet dann eine Nachricht zurück, die besagt, dass die sendende Anwendung angezeigt werden soll.

In diesem Kommunikationsmodell ist das Wort "empfangen", die in der Variable " *strintext* " gesendete Nachricht, für die Anzeige am anderen Ende der Kommunikation, sodass es dem empfangenden Benutzer angibt, dass eine bestimmte Anzahl von Datenpaketen empfangen wurde. Der Empfänger antwortet mit einer ähnlichen Zeichenfolge, die "sent" heißt, um auf dem Bildschirm des ursprünglichen Absenders angezeigt zu werden. Der Empfang beider Zeichen folgen gibt an, dass eine erfolgreiche Kommunikation stattgefunden hat.

> [!CAUTION]
> Wenn Sie ein MFC-Client Programm schreiben, um mit festgelegten (nicht-MFC-Servern) zu kommunizieren, senden Sie keine C++-Objekte über das Archiv. Es ist nicht möglich, Objekte zu empfangen und zu deserialisieren, es sei denn, der Server ist eine MFC-Anwendung, die die Arten von Objekten versteht, die Sie senden möchten. Ein Beispiel im Artikel [Windows Sockets: Byte-Reihen](../mfc/windows-sockets-byte-ordering.md) Folge zeigt eine Kommunikation dieses Typs.

Weitere Informationen finden Sie unter Windows Sockets Specification: **htonl**, **htons**, **ndehl**, **NUM**. Weitere Informationen finden Sie unter:

- [Windows Sockets: Ableiten von Socketklassen](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: wie Sockets mit Archiven funktionieren](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows-Sockets: Hintergrund](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive:: isspeichernde](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive:: Operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive:: Operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive:: Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)
