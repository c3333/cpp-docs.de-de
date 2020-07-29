---
title: Verbindungspunkte
ms.date: 11/19/2018
f1_keywords:
- IConnectionPoint
helpviewer_keywords:
- IConnectionPoint interface
- connections, connection points
- OLE COM connection points
- MFC COM, connection points
- COM, connection points
- interfaces, IConnectionPoint
- MFC, COM support
- connection points [MFC]
- CCmdTarget class [MFC], and connection points
- sinks, connection points
ms.assetid: bc9fd7c7-8df6-4752-ac8c-0b177442c88d
ms.openlocfilehash: c14d8247be2abdf828b88e728bd930691ec6571f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214151"
---
# <a name="connection-points"></a>Verbindungspunkte

In diesem Artikel wird erläutert, wie Verbindungspunkte (früher als OLE-Verbindungspunkte bezeichnet) mit den MFC-Klassen und implementiert werden `CCmdTarget` `CConnectionPoint` .

In der Vergangenheit hat der Component Object Model (com) einen allgemeinen Mechanismus ( `IUnknown::QueryInterface` *) definiert, der es Objekten gestattet hat, Funktionen in Schnittstellen zu implementieren und verfügbar zu machen. Es wurde jedoch kein entsprechender Mechanismus definiert, der es-Objekten ermöglichte, bestimmte Schnittstellen aufzurufen. Das heißt, com definiert, wie eingehende Zeiger auf Objekte (Zeiger auf die Schnittstellen dieses Objekts) behandelt wurden, aber kein explizites Modell für ausgehende Schnittstellen (Zeiger, das das Objekt auf die Schnittstellen anderer Objekte hält). COM verfügt jetzt über ein Modell, das als Verbindungspunkte bezeichnet wird, das diese Funktionalität unterstützt.

Eine Verbindung besteht aus zwei Teilen: dem Objekt, das die-Schnittstelle aufruft, die als Quelle bezeichnet wird, und dem Objekt, das die-Schnittstelle implementiert. Ein Verbindungspunkt ist die Schnittstelle, die von der Quelle verfügbar gemacht wird. Durch die Bereitstellung eines Verbindungs Punkts ermöglicht eine Quelle senken, Verbindungen mit sich selbst (der Quelle) herzustellen. Über den Verbindungspunkt Mechanismus (die- `IConnectionPoint` Schnittstelle) wird ein Zeiger auf die Sink-Schnittstelle an das Quell Objekt übermittelt. Dieser Zeiger stellt der Quelle den Zugriff auf die Implementierung einer Senke eines Satzes von Element Funktionen bereit. Um z. b. ein von der Senke implementiertes Ereignis auszulösen, kann die Quelle die entsprechende Methode der Senke-Implementierung aufzurufen. In der folgenden Abbildung wird der soeben beschriebene Verbindungspunkt veranschaulicht.

![Implementierter Verbindungspunkt](../mfc/media/vc37lh1.gif "Implementierter Verbindungspunkt") <br/>
Implementierter Verbindungspunkt

MFC implementiert dieses Modell in den Klassen [CConnectionPoint](reference/cconnectionpoint-class.md) und [CCmdTarget](reference/ccmdtarget-class.md) . Von abgeleitete Klassen `CConnectionPoint` implementieren die- `IConnectionPoint` Schnittstelle, mit der Verbindungspunkte für andere Objekte verfügbar gemacht werden. Von abgeleitete Klassen `CCmdTarget` implementieren die `IConnectionPointContainer` -Schnittstelle, die alle verfügbaren Verbindungspunkte eines Objekts aufzählen oder einen bestimmten Verbindungspunkt finden kann.

Für jeden Verbindungspunkt, der in der Klasse implementiert ist, müssen Sie einen Verbindungsteil deklarieren, der den Verbindungspunkt implementiert. Wenn Sie einen oder mehrere Verbindungspunkte implementieren, müssen Sie auch eine einzelne Verbindungs Zuordnung in der Klasse deklarieren. Eine Verbindungs Zuordnung ist eine Tabelle mit Verbindungs Punkten, die vom ActiveX-Steuerelement unterstützt werden.

Die folgenden Beispiele veranschaulichen eine einfache Verbindungs Zuordnung und einen Verbindungspunkt. Im ersten Beispiel werden die Verbindungs Zuordnung und der Punkt deklariert. im zweiten Beispiel werden die Karte und der Punkt implementiert. Beachten Sie, dass `CMyClass` eine von `CCmdTarget` abgeleitete Klasse sein muss. Im ersten Beispiel wird Code in der Klassen Deklaration im **`protected`** Abschnitt eingefügt:

[!code-cpp[NVC_MFCConnectionPoints#1](codesnippet/cpp/connection-points_1.h)]

Die Makros **BEGIN_CONNECTION_PART** und **END_CONNECTION_PART** deklarieren eine eingebettete Klasse `XSampleConnPt` (abgeleitet `CConnectionPoint` von), die diesen speziellen Verbindungspunkt implementiert. Wenn Sie Element `CConnectionPoint` Funktionen überschreiben oder eigene Element Funktionen hinzufügen möchten, deklarieren Sie Sie zwischen diesen beiden Makros. Das- `CONNECTION_IID` Makro überschreibt z. b. die-Element `CConnectionPoint::GetIID` Funktion, wenn diese zwischen diesen beiden Makros platziert wird.

Im zweiten Beispiel wird Code in die Implementierungs Datei des Steuer Elements (CPP-Datei) eingefügt. Dieser Code implementiert die Verbindungs Zuordnung, die den Verbindungspunkt umfasst `SampleConnPt` :

[!code-cpp[NVC_MFCConnectionPoints#2](codesnippet/cpp/connection-points_2.cpp)]

Wenn die Klasse über mehr als einen Verbindungspunkt verfügt, fügen Sie zusätzliche **CONNECTION_PART** Makros zwischen den **BEGIN_CONNECTION_MAP** -und **END_CONNECTION_MAP** -Makros ein.

Fügen Sie abschließend `EnableConnections` im Konstruktor der Klasse einen-Rückruf hinzu. Beispiel:

[!code-cpp[NVC_MFCConnectionPoints#3](codesnippet/cpp/connection-points_3.cpp)]

Nachdem dieser Code eingefügt wurde, macht `CCmdTarget` die von abgeleitete Klasse einen Verbindungspunkt für die- `ISampleSink` Schnittstelle verfügbar. In der folgenden Abbildung wird dieses Beispiel veranschaulicht.

![Mithilfe von MFC implementierter Verbindungspunkt](../mfc/media/vc37lh2.gif "Mithilfe von MFC implementierter Verbindungspunkt") <br/>
Ein mit MFC implementierter Verbindungspunkt

Verbindungspunkte unterstützen in der Regel "Multicasting" – die Möglichkeit, an mehrere senken zu übertragen, die mit derselben Schnittstelle verbunden sind. Im folgenden Beispiel Fragment wird veranschaulicht, wie Multicast durch durchlaufen jeder Senke an einem Verbindungspunkt veranschaulicht wird:

[!code-cpp[NVC_MFCConnectionPoints#4](codesnippet/cpp/connection-points_4.cpp)]

In diesem Beispiel wird der aktuelle Satz von Verbindungen auf dem `SampleConnPt` Verbindungspunkt mit einem-Befehl abgerufen `CConnectionPoint::GetConnections` . Anschließend durchläuft Sie die Verbindungen und ruft `ISampleSink::SinkFunc` für jede aktive Verbindung auf.

## <a name="see-also"></a>Weitere Informationen

[MFC COM](mfc-com.md)
