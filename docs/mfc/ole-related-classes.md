---
title: OLE-bezogene Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: 6f6db6ce133b440a5ed86e7c1642396888744540
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621031"
---
# <a name="ole-related-classes"></a>OLE-bezogene Klassen

Diese Klassen stellen eine Reihe von verschiedenen Diensten bereit, von Ausnahmen bis hin zu Datei Eingaben und-Ausgaben.

[COleObjectFactory](reference/coleobjectfactory-class.md)<br/>
Wird zum Erstellen von Elementen verwendet, wenn Sie von anderen Containern angefordert werden. Diese Klasse dient als Basisklasse für spezifischere Arten von Factorys, einschließlich `COleTemplateServer` .

[COleMessageFilter](reference/colemessagefilter-class.md)<br/>
Dient zum Verwalten von Parallelität mit OLE-Lightweight-Remote Prozedur aufrufen (Remote Procedure Calls, LRPC).

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Verwendet die com- `IStream` Schnittstelle, um `CFile` Zugriff auf Verbund Dateien bereitzustellen. Diese Klasse (abgeleitet von `CFile` ) ermöglicht die MFC-Serialisierung die Verwendung von strukturiertem OLE-Speicher.

[CRectTracker](reference/crecttracker-class.md)<br/>
Wird verwendet, um das Verschieben, Ändern der Größe und die Neuausrichtung von direkten Elementen zuzulassen.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
