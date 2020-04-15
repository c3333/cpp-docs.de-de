---
title: Aktivierung (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: 9f3fba71002a19a0be0e3429a0faeeefb7c65197
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354169"
---
# <a name="activation-c"></a>Aktivierung (C++)

In diesem Artikel wird die Rolle der Aktivierung bei der visuellen Bearbeitung von OLE-Elementen erläutert. Nachdem ein Benutzer ein OLE-Element in ein Containerdokument eingebettet hat, muss es möglicherweise verwendet werden. Dazu doppelklickt der Benutzer auf das Element, das dieses Element aktiviert. Die häufigste Aktivität für die Aktivierung ist die Bearbeitung. Wenn viele aktuelle OLE-Elemente für die Bearbeitung aktiviert sind, werden die Menüs und Symbolleisten im aktuellen Rahmenfenster geändert, um die Elemente der Serveranwendung widerzuspiegeln, die das Element erstellt hat. Dieses Verhalten, das als in-Place-Aktivierung bezeichnet wird, ermöglicht es dem Benutzer, jedes eingebettete Element in einem zusammengesetzten Dokument zu bearbeiten, ohne das Fenster des Containerdokuments zu verlassen.

Es ist auch möglich, eingebettete OLE-Elemente in einem separaten Fenster zu bearbeiten. Dies geschieht, wenn entweder der Container oder die Serveranwendung die an Ort und Stelle nicht unterstützende Aktivierung unterstützt. Wenn der Benutzer in diesem Fall auf ein eingebettetes Element doppelklickt, wird die Serveranwendung in einem separaten Fenster gestartet, und das eingebettete Element wird als eigenes Dokument angezeigt. Der Benutzer befolgt das Element in diesem Fenster. Wenn die Bearbeitung abgeschlossen ist, schließt der Benutzer die Serveranwendung und kehrt zur Containeranwendung zurück.

Alternativ kann der Benutzer im Menü **Bearbeiten** "Öffnen der Bearbeitung" mit dem ** \<Befehl "Objekt> Öffnen"** wählen. Dadurch wird das Objekt in einem separaten Fenster geöffnet.

> [!NOTE]
> Das Bearbeiten eingebetteter Elemente in einem separaten Fenster war Standardverhalten in Version 1 von OLE, und einige OLE-Anwendungen unterstützen möglicherweise nur diesen Bearbeitungsstil.

Die an Ort und Stelle wird ein dokumentzentrierter Ansatz für die Dokumenterstellung heraufbeauft. Der Benutzer kann ein zusammengesetztes Dokument als eine einzelne Entität behandeln und daran arbeiten, ohne zwischen Anwendungen zu wechseln. Die direkte Aktivierung wird jedoch nur für eingebettete Elemente verwendet, nicht für verknüpfte Elemente: Sie müssen in einem separaten Fenster bearbeitet werden. Dies liegt daran, dass ein verknüpftes Element tatsächlich an einem anderen Ort gespeichert wird. Die Bearbeitung eines verknüpften Elements erfolgt im eigentlichen Kontext der Daten, d.h. dort, wo die Daten gespeichert werden. Das Bearbeiten eines verknüpften Elements in einem separaten Fenster erinnert den Benutzer daran, dass die Daten zu einem anderen Dokument gehören.

MFC unterstützt keine geschachtelte an Ort und Stelle Aktivierung. Wenn Sie eine Container-/Serveranwendung erstellen und dieser Container/Server in einen anderen Container eingebettet und direkt aktiviert ist, kann es keine in ihm eingebetteten Objekte aktivieren.

Was mit einem eingebetteten Element geschieht, wenn der Benutzer darauf doppelklickt, hängt von den für das Element definierten Verben ab. Weitere Informationen finden Sie [unter Aktivierung: Verben](../mfc/activation-verbs.md).

## <a name="see-also"></a>Siehe auch

[OLE](../mfc/ole-in-mfc.md)<br/>
[Container](../mfc/containers.md)<br/>
[Server](../mfc/servers.md)
