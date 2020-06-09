---
title: 'Aktivierung: Verben'
ms.date: 11/04/2016
helpviewer_keywords:
- verbs [MFC]
- OLE [MFC], activation
- edit verb [MFC]
- activation [MFC], verbs
- OLE [MFC], editing
- Primary verb [MFC]
- OLE activation {MFC]
ms.assetid: eb56ff23-1de8-43ad-abeb-dc7346ba7b70
ms.openlocfilehash: 03edba0a4336fdc147ef6dd10c7a8154aca19d3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616642"
---
# <a name="activation-verbs"></a>Aktivierung: Verben

In diesem Artikel werden die Rollen primäre und sekundäre Verben bei der OLE- [Aktivierung](activation-cpp.md)erläutert.

Normalerweise ermöglicht das Doppelklicken auf ein eingebettetes Element dem Benutzer, ihn zu bearbeiten. Bestimmte Elemente Verhalten sich jedoch nicht auf diese Weise. Wenn Sie z. b. auf ein Element doppelklicken, das mit der Sound Recorder-Anwendung erstellt wurde, wird der Server nicht in einem separaten Fenster geöffnet. Stattdessen wird der Sound abgespielt.

Der Grund für diesen Verhaltens Unterschied besteht darin, dass Sound Recorder-Elemente ein anderes "primäres Verb" aufweisen. Das primäre Verb ist die Aktion, die ausgeführt wird, wenn der Benutzer auf ein OLE-Element doppelklickt. Bei den meisten OLE-Elementtypen ist das primäre Verb "Edit", mit dem der Server gestartet wird, der das Element erstellt hat. Für einige Arten von Elementen, z. b. Sound Recorder-Elemente, wird das primäre Verb abgespielt.

Viele OLE-Elementtypen unterstützen nur ein Verb, und bearbeiten ist das häufigste. Einige Typen von Elementen unterstützen jedoch mehrere Verben. Beispielsweise unterstützen Sound Recorder-Elemente die Bearbeitung als sekundäres Verb.

Ein anderes Verb verwendetes Verb ist offen. Das geöffnete Verb ist mit der Bearbeitung identisch, mit der Ausnahme, dass die Serveranwendung in einem separaten Fenster gestartet wird. Dieses Verb sollte verwendet werden, wenn entweder die Containeranwendung oder die Serveranwendung die direkte Aktivierung nicht unterstützt.

Alle Verben außer dem primären Verb müssen über einen unter Menübefehl aufgerufen werden, wenn das Element ausgewählt wird. Dieses Untermenü enthält alle Verben, die vom Element unterstützt werden, und wird in der Regel durch den Befehl *Typname* **Object** im Menü **Bearbeiten** erreicht. Weitere Informationen zum *Typname* - **Objekt** Befehl finden Sie in den Artikeln [Menüs und Ressourcen: Container Ergänzungen](menus-and-resources-container-additions.md).

Die von einer Serveranwendung unterstützten Verben sind in der Windows-Registrierungsdatenbank aufgeführt. Wenn die Serveranwendung mit dem Microsoft Foundation Class-Bibliothek geschrieben wird, werden alle Verben automatisch registriert, wenn der Server gestartet wird. Andernfalls sollten Sie diese während der Initialisierungsphase der Serveranwendung registrieren. Weitere Informationen finden Sie im Artikel [Registrierung](registration.md).

## <a name="see-also"></a>Siehe auch

[Aktivierung](activation-cpp.md)<br/>
[Container](containers.md)<br/>
[Server](servers.md)
