---
title: 'Ausnahmen: OLE-Ausnahmen'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 7bd0b0cb2c9eb6fe49356ae8fd4602676d54fa66
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622789"
---
# <a name="exceptions-ole-exceptions"></a>Ausnahmen: OLE-Ausnahmen

Die Techniken und Funktionen für die Behandlung von Ausnahmen in OLE sind identisch mit denen für andere Ausnahmen. Weitere Informationen zur Ausnahmebehandlung finden Sie im Artikel [modern C++ Best Practices für Ausnahmen und Fehlerbehandlung](../cpp/errors-and-exception-handling-modern-cpp.md).

Alle Ausnahme Objekte werden von der abstrakten Basisklasse abgeleitet `CException` . MFC stellt zwei Klassen für die Behandlung von OLE-Ausnahmen bereit:

- [COleException](reference/coleexception-class.md) Zur Behandlung allgemeiner OLE-Ausnahmen.

- [COleDispatchException](reference/coledispatchexception-class.md) Zum Erstellen und Verarbeiten von OLE Dispatch-Ausnahmen (Automation).

Der Unterschied zwischen diesen beiden Klassen ist die Menge der Informationen, die Sie bereitstellen und wo Sie verwendet werden. `COleException`verfügt über einen öffentlichen Datenmember, der den OLE-Statuscode für die Ausnahme enthält. `COleDispatchException`bietet weitere Informationen, einschließlich der folgenden:

- Ein anwendungsspezifischer Fehlercode

- Eine Fehlerbeschreibung, z. b. "Datenträger voll"

- Ein Hilfe Kontext, den Ihre Anwendung verwenden kann, um zusätzliche Informationen für den Benutzer bereitzustellen.

- Der Name der Hilfedatei Ihrer Anwendung.

- Der Name der Anwendung, die die Ausnahme generiert hat.

`COleDispatchException`bietet weitere Informationen, damit Sie mit Produkten wie Microsoft Visual Basic verwendet werden können. Die Beschreibung des verbalen Fehlers kann in einem Meldungs Feld oder in einer anderen Benachrichtigung verwendet werden. die Hilfe Informationen können verwendet werden, um dem Benutzer zu helfen, auf die Bedingungen zu reagieren, die die Ausnahme verursacht haben.

Zwei globale Funktionen entsprechen den beiden OLE-Ausnahme Klassen: [AfxThrowOleException](reference/exception-processing.md#afxthrowoleexception) und [AfxThrowOleDispatchException](reference/exception-processing.md#afxthrowoledispatchexception). Verwenden Sie diese, um allgemeine OLE-Ausnahmen bzw. OLE Dispatch-Ausnahmen auszulösen.

## <a name="see-also"></a>Siehe auch

[Ausnahmebehandlung](exception-handling-in-mfc.md)
