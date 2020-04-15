---
title: 'Windows Sockets: Beispiel für Sockets mithilfe der Archive'
ms.date: 11/04/2016
helpviewer_keywords:
- sockets [MFC], with archives
- examples [MFC], Windows Sockets
- Windows Sockets [MFC], with archives
ms.assetid: 2e3c9bb2-7e7b-4f28-8dc5-6cb7a484edac
ms.openlocfilehash: 253a65430ae230fbc4deeb9bd5288f28237310d2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371087"
---
# <a name="windows-sockets-example-of-sockets-using-archives"></a>Windows Sockets: Beispiel für Sockets mithilfe der Archive

Dieser Artikel stellt ein Beispiel für die Verwendung der Klasse [CSocket](../mfc/reference/csocket-class.md)vor. Im Beispiel `CArchive` werden Objekte verwendet, um Daten über einen Socket zu serialisieren. Beachten Sie, dass dies keine Dokumentserialisierung zu oder aus einer Datei ist.

Das folgende Beispiel veranschaulicht, wie Sie das Archiv `CSocket` zum Senden und Empfangen von Daten über Objekte verwenden. Das Beispiel ist so konzipiert, dass zwei Instanzen der Anwendung (auf demselben Computer oder auf verschiedenen Computern im Netzwerk) Daten austauschen. Eine Instanz sendet Daten, die die andere Instanz empfängt und anerkennt. Jede Anwendung kann einen Austausch initiieren und entweder als Server oder als Client für die andere Anwendung fungieren. Die folgende Funktion ist in der Ansichtsklasse der Anwendung definiert:

[!code-cpp[NVC_MFCSimpleSocket#1](../mfc/codesnippet/cpp/windows-sockets-example-of-sockets-using-archives_1.cpp)]

Das Wichtigste an diesem Beispiel ist, dass seine Struktur `Serialize` mit der einer MFC-Funktion vergleichbar ist. Die `PacketSerialize` Memberfunktion besteht aus einer **if-Anweisung** mit einer **else-Klausel.** Die Funktion erhält zwei [CArchive-Referenzen](../mfc/reference/carchive-class.md) als Parameter: *arData* und *arAck*. Wenn das *arData-Archivobjekt* zum Speichern (Senden) festgelegt ist, wird der **if-Zweig** ausgeführt. Andernfalls, wenn *arData* zum Laden (Empfangen) festgelegt ist, übernimmt die Funktion den **anderen** Zweig. Weitere Informationen zur Serialisierung in MFC finden Sie unter [Serialisierung](../mfc/how-to-make-a-type-safe-collection.md).

> [!NOTE]
> Das *arAck-Archivobjekt* wird als das Gegenteil von *arData*angenommen. Wenn *arData* zum Senden dient, empfängt *arAck,* und das Umgekehrte ist wahr.

Zum Senden wird die Beispielfunktion für eine bestimmte Anzahl von Schleifen ausgeführt, wobei jedes Mal zufällige Daten zu Demonstrationszwecken generiert werden. Ihre Anwendung würde echte Daten aus einer Quelle abrufen, z. B. aus einer Datei. Der Einfügeoperator des *arData-Archivs* (**<<**) wird verwendet, um einen Stream mit drei aufeinanderfolgenden Datenblöcken zu senden:

- Ein "Header", der die Art der Daten angibt (in diesem Fall den Wert der *variable bValue* und wie viele Kopien gesendet werden).

   Beide Elemente werden für dieses Beispiel nach dem Zufallsprinzip generiert.

- Die angegebene Anzahl von Kopien der Daten.

   Die innere **for-Schleife** sendet *bValue* die angegebene Anzahl von Malen.

- Eine Zeichenfolge namens *strText,* die der Empfänger seinem Benutzer anzeigt.

Für den Empfang funktioniert die Funktion ähnlich, mit der**>>** Ausnahme, dass sie den Extraktionsoperator des Archivs ( ) verwendet, um Daten aus dem Archiv abzubekommen. Die empfangende Anwendung überprüft die empfangenen Daten, zeigt die endgültige Meldung "Empfangen" an und sendet dann eine Meldung zurück, die "Gesendet" für die sendende Anwendung anzeigt.

In diesem Kommunikationsmodell ist das Wort "Empfangen", die in der *strText-Variablen* gesendete Nachricht, für die Anzeige am anderen Ende der Kommunikation vorgesehen, sodass es dem empfangenden Benutzer angibt, dass eine bestimmte Anzahl von Datenpaketen empfangen wurde. Der Empfänger antwortet mit einer ähnlichen Zeichenfolge, die "Gesendet" sagt, für die Anzeige auf dem Bildschirm des ursprünglichen Absenders. Der Empfang beider Zeichenfolgen zeigt an, dass eine erfolgreiche Kommunikation stattgefunden hat.

> [!CAUTION]
> Wenn Sie ein MFC-Clientprogramm schreiben, um mit etablierten (Nicht-MFC-)Servern zu kommunizieren, senden Sie keine C++-Objekte über das Archiv. Wenn es sich bei dem Server nicht um eine MFC-Anwendung handelt, die die Arten von Objekten versteht, die Sie senden möchten, kann er Ihre Objekte nicht empfangen und deserialisieren. Ein Beispiel im Artikel [Windows Sockets: Byte Ordering](../mfc/windows-sockets-byte-ordering.md) zeigt eine Kommunikation dieses Typs.

Weitere Informationen finden Sie unter Windows Sockets Specification: **htonl**, **htons**, **ntohl**, **ntohs**. Weitere Informationen finden Sie unter:

- [Windows Sockets: Ableiten von Socket-Classen](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows Sockets: Wie Sockets mit Archiven arbeiten](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows Sockets: Hintergrund](../mfc/windows-sockets-background.md)

## <a name="see-also"></a>Siehe auch

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)<br/>
[CArchive::IsStoring](../mfc/reference/carchive-class.md#isstoring)<br/>
[CArchive::operator <<](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::operator >>](../mfc/reference/carchive-class.md#operator_lt_lt)<br/>
[CArchive::Flush](../mfc/reference/carchive-class.md#flush)<br/>
[CObject::Serialisieren](../mfc/reference/cobject-class.md#serialize)
