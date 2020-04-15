---
title: Ereignisbehandlungsprinzipien (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, implementing
- event handling, advising event sources
- interfaces, event and event sink
- dual interfaces, event interfaces
- event handling, dual event interfaces
ms.assetid: d17ca7cb-54f2-4658-ab8b-b721ac56801d
ms.openlocfilehash: 2e810853e7c81f279039e0b3dfda5199d38deee2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319567"
---
# <a name="event-handling-principles"></a>Prinzipien für die Ereignisbehandlung

Es gibt drei Schritte, die für die gesamte Ereignisbehandlung gemeinsam sind. Folgendes ist erforderlich:

- Implementieren Sie die Ereignisschnittstelle für Ihr Objekt.

- Weisen Sie die Ereignisquelle an, dass Ihr Objekt Ereignisse empfangen möchte.

- Bedecken Sie die Ereignisquelle, wenn Ihr Objekt keine Ereignisse mehr empfangen muss.

Die Art und Weise, wie Sie die Ereignisschnittstelle implementieren, hängt vom Typ ab. Eine Ereignisschnittstelle kann vtable, dual oder eine Dispinterface sein. Es liegt am Designer der Ereignisquelle, die Schnittstelle zu definieren. es liegt an Ihnen, diese Schnittstelle zu implementieren.

> [!NOTE]
> Obwohl es keine technischen Gründe dafür gibt, dass eine Ereignisschnittstelle nicht dual sein kann, gibt es eine Reihe von guten Designgründen, um die Verwendung von Duals zu vermeiden. Dies ist jedoch eine Entscheidung, die vom Designer/Implementierer der *Ereignisquelle*getroffen wurde. Da Sie aus der Perspektive des `sink`Ereignisses arbeiten, müssen Sie die Möglichkeit zulassen, dass Sie möglicherweise keine andere Wahl haben, als eine duale Ereignisschnittstelle zu implementieren. Weitere Informationen zu dualen Schnittstellen finden Sie unter [Dual Interfaces und ATL](../atl/dual-interfaces-and-atl.md).

Die Beratung der Ereignisquelle kann in drei Schritte unterteilt werden:

- Abfragen des Quellobjekts nach [IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer).

- Rufen Sie [IConnectionPointContainer::FindConnectionPoint](/windows/win32/api/ocidl/nf-ocidl-iconnectionpointcontainer-findconnectionpoint) auf, der die IID der Ereignisschnittstelle übergibt, die Sie interessiert. Wenn dies erfolgreich ist, wird die [IConnectionPoint-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) für ein Verbindungspunktobjekt zurückgegeben.

- Rufen Sie [IConnectionPoint::Advise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-advise) das Übergeben der `IUnknown` Ereignissenke. Wenn dies erfolgreich `DWORD` ist, wird ein Cookie zurückgegeben, das die Verbindung darstellt.

Sobald Sie Ihr Interesse am Empfangen von Ereignissen erfolgreich registriert haben, werden Methoden auf der Ereignisschnittstelle Ihres Objekts entsprechend den vom Quellobjekt ausgelösten Ereignissen aufgerufen. Wenn Sie keine Ereignisse mehr empfangen müssen, können Sie das Cookie über [IConnectionPoint::Unadvise](/windows/win32/api/ocidl/nf-ocidl-iconnectionpoint-unadvise)an den Verbindungspunkt zurückgeben. Dadurch wird die Verbindung zwischen Quelle und Senke aufgebrochen.

Achten Sie darauf, Referenzzyklen bei der Behandlung von Ereignissen zu vermeiden.

## <a name="see-also"></a>Siehe auch

[Ereignisbehandlung](../atl/event-handling-and-atl.md)
