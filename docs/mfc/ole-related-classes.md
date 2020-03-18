---
title: OLE-bezogene Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE classes [MFC]
- OLE [MFC], classes
ms.assetid: 2135cf54-1d9d-4e0e-91b4-943b3440effa
ms.openlocfilehash: dfcc07b3fbd0c5badce8e397f4d52bc7d8d3028c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447604"
---
# <a name="ole-related-classes"></a>OLE-bezogene Klassen

Diese Klassen stellen eine Reihe von verschiedenen Diensten bereit, von Ausnahmen bis hin zu Datei Eingaben und-Ausgaben.

[COleObjectFactory](../mfc/reference/coleobjectfactory-class.md)<br/>
Wird zum Erstellen von Elementen verwendet, wenn Sie von anderen Containern angefordert werden. Diese Klasse dient als Basisklasse für spezifischere Arten von Factorys, einschließlich `COleTemplateServer`.

[Colemessagefilter](../mfc/reference/colemessagefilter-class.md)<br/>
Dient zum Verwalten von Parallelität mit OLE-Lightweight-Remote Prozedur aufrufen (Remote Procedure Calls, LRPC).

[Colestreamfile](../mfc/reference/colestreamfile-class.md)<br/>
Verwendet die com-`IStream` Schnittstelle, um `CFile` Zugriff auf Verbund Dateien bereitzustellen. Diese Klasse (abgeleitet von `CFile`) ermöglicht die MFC-Serialisierung die Verwendung von strukturiertem OLE-Speicher.

[CRectTracker](../mfc/reference/crecttracker-class.md)<br/>
Wird verwendet, um das Verschieben, Ändern der Größe und die Neuausrichtung von direkten Elementen zuzulassen.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)
