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
ms.openlocfilehash: 47640a59180348bd3513013b65029a775545e211
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619185"
---
# <a name="activation-c"></a>Aktivierung (C++)

In diesem Artikel wird die Rolle der Aktivierung bei der visuellen Bearbeitung von OLE-Elementen erläutert. Nachdem ein Benutzer ein OLE-Element in ein Container Dokument eingebettet hat, muss es möglicherweise verwendet werden. Zu diesem Zweck doppelklickt der Benutzer auf das Element, das das Element aktiviert. Die häufigste Aktivität für die Aktivierung ist die Bearbeitung. Viele aktuelle OLE-Elemente, wenn Sie für die Bearbeitung aktiviert sind, bewirken, dass die Menüs und Symbolleisten im aktuellen Rahmen Fenster geändert werden, um die der Serveranwendung, die das Element erstellt hat, widerzuspiegeln. Dieses Verhalten, das als direkte Aktivierung bezeichnet wird, ermöglicht dem Benutzer, alle eingebetteten Elemente in einem Verbund Dokument zu bearbeiten, ohne das Fenster des Container Dokuments zu überlassen.

Es ist auch möglich, eingebettete OLE-Elemente in einem separaten Fenster zu bearbeiten. Dies geschieht, wenn die Container-oder Serveranwendung keine direkte Aktivierung unterstützt. Wenn der Benutzer in diesem Fall auf ein eingebettetes Element doppelklickt, wird die Serveranwendung in einem separaten Fenster gestartet, und das eingebettete Element wird als eigenes Dokument angezeigt. Der Benutzer bearbeitet das Element in diesem Fenster. Wenn die Bearbeitung abgeschlossen ist, schließt der Benutzer die Serveranwendung und kehrt zur Containeranwendung zurück.

Als Alternative kann der Benutzer mit dem Befehl "Bearbeiten" im Menü " **Bearbeiten** " die Option "Bearbeitung öffnen" auswählen. ** \<object> ** Dadurch wird das Objekt in einem separaten Fenster geöffnet.

> [!NOTE]
> Das Bearbeiten eingebetteter Elemente in einem separaten Fenster war das Standardverhalten in Version 1 von OLE, und einige OLE-Anwendungen unterstützen möglicherweise nur diese Art der Bearbeitung.

Die direkte Aktivierung fördert eine Dokument zentrierte Vorgehensweise für die Dokument Erstellung. Der Benutzer kann ein Verbund Dokument als einzelne Entität behandeln und daran arbeiten, ohne zwischen Anwendungen wechseln zu müssen. Die direkte Aktivierung wird jedoch nur für eingebettete Elemente verwendet, nicht für verknüpfte Elemente: Sie müssen in einem separaten Fenster bearbeitet werden. Dies liegt daran, dass ein verknüpftes Element tatsächlich an einem anderen Speicherort gespeichert wird. Die Bearbeitung eines verknüpften Elements erfolgt im eigentlichen Kontext der Daten, d. h. in dem Speicherort, an dem die Daten gespeichert werden. Wenn Sie ein verknüpftes Element in einem separaten Fenster bearbeiten, wird der Benutzer daran erinnert, dass die Daten zu einem anderen Dokument gehören.

MFC unterstützt keine aktivierte direkte Aktivierung. Wenn Sie eine Container-/Serveranwendung erstellen und dieser Container bzw. Server in einen anderen Container eingebettet und direkt aktiviert ist, kann er die darin eingebetteten Objekte nicht direkt aktivieren.

Was mit einem eingebetteten Element geschieht, wenn der Benutzer darauf doppelklickt, hängt von den Verben ab, die für das Element definiert sind. Weitere Informationen finden Sie unter [Activation: Verbs](activation-verbs.md).

## <a name="see-also"></a>Siehe auch

[OLE](ole-in-mfc.md)<br/>
[Container](containers.md)<br/>
[Server](servers.md)
