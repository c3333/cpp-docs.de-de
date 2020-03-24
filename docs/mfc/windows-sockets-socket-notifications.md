---
title: 'Windows Sockets: Socketbenachrichtigungen'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], notifications
- notifications [MFC], socket
- sockets [MFC], notifications
ms.assetid: 87d5bf70-6e77-49a9-9a64-aaadee2ad018
ms.openlocfilehash: 10dbe6c0e1f486257c50efc4acf917cd9d596630
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167770"
---
# <a name="windows-sockets-socket-notifications"></a>Windows Sockets: Socketbenachrichtigungen

In diesem Artikel werden die Benachrichtigungsfunktionen in den Socketklassen beschrieben. Diese Element Funktionen sind Rückruf Funktionen, die vom Framework aufgerufen werden, um das Socketobjekt wichtiger Ereignisse zu benachrichtigen. Die Benachrichtigungsfunktionen lauten:

- [OnReceive](../mfc/reference/casyncsocket-class.md#onreceive): benachrichtigt diesen Socket, dass sich Daten im Puffer befinden, damit er durch Aufrufen von [Receive](../mfc/reference/casyncsocket-class.md#receive)abgerufen werden kann.

- [OnSend](../mfc/reference/casyncsocket-class.md#onsend): benachrichtigt diesen Socket, dass er nun durch Aufrufen von [Send](../mfc/reference/casyncsocket-class.md#send)Daten senden kann.

- [OnAccept](../mfc/reference/casyncsocket-class.md#onaccept): benachrichtigt diesen Abhör Socket, dass er ausstehende Verbindungsanforderungen durch Aufrufen von [Accept](../mfc/reference/casyncsocket-class.md#accept)annehmen kann.

- [OnConnect](../mfc/reference/casyncsocket-class.md#onconnect): benachrichtigt diesen Verbindungs-Socket, dass der Verbindungsversuch abgeschlossen wurde: möglicherweise erfolgreich oder fehlerhaft.

- [OnClose](../mfc/reference/casyncsocket-class.md#onclose): benachrichtigt diesen Socket, dass der Socket, mit dem er verbunden ist, geschlossen wurde.

    > [!NOTE]
    >  Eine zusätzliche Benachrichtigungsfunktion ist [onouto fbanddata](../mfc/reference/casyncsocket-class.md#onoutofbanddata). Diese Benachrichtigung weist den empfangenden Socket an, dass der sendende Socket über "Out-of-Band"-Daten zum Senden verfügt. Out-of-Band-Daten sind logisch unabhängige Kanäle, die den einzelnen verknüpften Streamsockets zugeordnet sind. Der Out-of-Band-Kanal wird normalerweise verwendet, um "dringende" Daten zu senden. MFC unterstützt out-of-Band-Daten. Fortgeschrittene Benutzer, die mit der [CAsyncSocket](../mfc/reference/casyncsocket-class.md) -Klasse arbeiten, müssen möglicherweise den Out-of-Band-Kanal verwenden, aber Benutzer der [CSocket](../mfc/reference/csocket-class.md) -Klasse werden davon abgeraten, Sie zu verwenden. Der einfachere Weg besteht darin, einen zweiten Socket zum Übergeben dieser Daten zu erstellen. Weitere Informationen zu out-of-Band-Daten finden Sie in der Windows Sockets-Spezifikation, die in der Windows SDK verfügbar ist.

Wenn Sie von Class `CAsyncSocket`ableiten, müssen Sie die Benachrichtigungsfunktionen für die für Ihre Anwendung interessanten Netzwerkereignisse überschreiben. Wenn Sie eine Klasse von der Klasse `CSocket`ableiten, sollten Sie die Benachrichtigungsfunktionen überschreiben, die von Interesse sind. Sie können auch `CSocket` selbst verwenden. in diesem Fall werden die Benachrichtigungsfunktionen standardmäßig nicht ausgeführt.

Diese Funktionen sind über schreibbare Rückruf Funktionen. `CAsyncSocket` und `CSocket` Konvertieren von Nachrichten in Benachrichtigungen, aber Sie müssen implementieren, wie die Benachrichtigungsfunktionen reagieren, wenn Sie Sie verwenden möchten. Die Benachrichtigungsfunktionen werden zu dem Zeitpunkt aufgerufen, an dem Ihr Socket über ein interessantes Ereignis benachrichtigt wird, z. b. das vorhanden sein von zu lesenden Daten.

MFC ruft die Benachrichtigungsfunktionen auf, damit Sie das Socketverhalten zum Zeitpunkt der Benachrichtigung anpassen können. Beispielsweise können Sie `Receive` von ihrer `OnReceive` Benachrichtigungsfunktion aus anrufen, d. h., wenn Sie benachrichtigt werden, dass Daten gelesen werden sollen, wird `Receive` aufgerufen, um Sie zu lesen. Dieser Ansatz ist nicht erforderlich, aber es handelt sich um ein gültiges Szenario. Als Alternative können Sie die Benachrichtigungsfunktion verwenden, um den Fortschritt **nachzuverfolgen** , Ablauf Verfolgungs Meldungen zu drucken usw.

Sie können diese Benachrichtigungen nutzen, indem Sie die Benachrichtigungsfunktionen in einer abgeleiteten Socketklasse außer Kraft setzen und eine Implementierung bereitstellen.

Bei einem Vorgang, z. b. beim empfangen oder Senden von Daten, wird ein `CSocket` Objekt synchron. Während des synchronen Zustands werden alle für andere Sockets bezogenen Benachrichtigungen in die Warteschlange eingereiht, während der aktuelle Socket auf die gewünschte Benachrichtigung wartet. (Bei einem `Receive`-Befehl möchte der Socket z. b. eine Benachrichtigung lesen.) Sobald der Socket seinen synchronen Vorgang abgeschlossen hat und wieder asynchron wird, können andere Sockets die Warteschlangen Benachrichtigungen empfangen.

> [!NOTE]
> In `CSocket`wird die `OnConnect` Benachrichtigungsfunktion niemals aufgerufen. Für Verbindungen wird `Connect`aufgerufen, die zurückgegeben wird, wenn die Verbindung abgeschlossen ist (entweder erfolgreich oder fehlerhaft). Wie Verbindungs Benachrichtigungen behandelt werden, ist ein MFC-Implementierungsdetail.

Ausführliche Informationen zu den einzelnen Benachrichtigungsfunktionen finden Sie unter der-Funktion unter Class `CAsyncSocket` in der *MFC-Referenz*. Quellcode und Informationen zu MFC-Beispielen finden Sie unter [MFC-Beispiele](../overview/visual-cpp-samples.md#mfc-samples).

Weitere Informationen finden Sie unter

- [Windows-Sockets: Verwenden der Klasse CAsyncSocket](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows-Sockets: Ableiten von Socket-Klassen](../mfc/windows-sockets-deriving-from-socket-classes.md)

- [Windows-Sockets: Wie Sockets mit Archiven arbeiten](../mfc/windows-sockets-how-sockets-with-archives-work.md)

- [Windows-Sockets: Blocking](../mfc/windows-sockets-blocking.md)

- [Windows-Sockets: Bytereihenfolge](../mfc/windows-sockets-byte-ordering.md)

- [Windows-Sockets: Umwandeln von Zeichenfolgen](../mfc/windows-sockets-converting-strings.md)

## <a name="see-also"></a>Weitere Informationen

[Windows-Sockets in MFC](../mfc/windows-sockets-in-mfc.md)
