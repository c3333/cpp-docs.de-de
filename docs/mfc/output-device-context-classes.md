---
title: Klassen für die Ausgabe (Gerätekontext)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.output
helpviewer_keywords:
- device contexts [MFC], classes
- screen output classes [MFC]
- printing classes [MFC]
- window drawing classes [MFC]
- painting classes [MFC]
- output classes [MFC]
ms.assetid: 35fd6435-a38e-42c6-a3fa-cd6f39370fc3
ms.openlocfilehash: b15f5034604f9d6b67574288140b79b144692478
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615363"
---
# <a name="output-device-context-classes"></a>Klassen für die Ausgabe (Gerätekontext)

Diese Klassen kapseln die verschiedenen Typen von Geräte Kontexten, die in Windows verfügbar sind.

Die meisten der folgenden Klassen Kapseln ein Handle für einen Windows-Gerätekontext. Ein Gerätekontext ist ein Windows-Objekt, das Informationen über die Zeichnungs Attribute eines Geräts (z. b. eine Anzeige oder einen Drucker) enthält. Alle Zeichnungs Aufrufe werden über ein Gerätekontext Objekt durchgeführt. Zusätzliche Klassen, die von abgeleitet `CDC` werden, Kapseln spezialisierte Gerätekontext Funktionen, einschließlich der Unterstützung für Windows-Metadatendateien.

[CDC](reference/cdc-class.md)<br/>
Die Basisklasse für Geräte Kontexte. Wird direkt für den Zugriff auf die gesamte Anzeige und für den Zugriff auf nicht Anzeige Kontexte wie Drucker verwendet.

[CPaintDC](reference/cpaintdc-class.md)<br/>
Ein Anzeige Kontext, der in den Element `OnPaint` Funktionen von Windows verwendet wird. Ruft `BeginPaint` bei der Erstellung und `EndPaint` bei der Zerstörung automatisch auf.

[CClientDC](reference/cclientdc-class.md)<br/>
Ein Anzeige Kontext für Client Fensterbereiche. Wird beispielsweise verwendet, um eine sofortige Reaktion auf Mausereignisse zu zeichnen.

[CWindowDC](reference/cwindowdc-class.md)<br/>
Ein Anzeige Kontext für ganze Fenster, einschließlich des Client-und des nicht-Client Bereichs.

[CMetaFileDC](reference/cmetafiledc-class.md)<br/>
Ein Gerätekontext für Windows-Metadatendateien. Eine Windows-Metadatei enthält eine Sequenz von-GDI-Befehlen (Graphics Device Interface), die zum Erstellen eines Bilds wiedergegeben werden können. Aufrufe, die an die Member-Funktionen eines vorgenommen `CMetaFileDC` werden, werden in einer Metadatei aufgezeichnet.

## <a name="related-classes"></a>Verwandte Klassen

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Enthält Koordinatenpaare (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Enthält eine Entfernung, relative Positionen oder gekoppelte Werte.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Enthält Koordinaten von rechteckigen Bereichen.

[CRgn](reference/crgn-class.md)<br/>
Kapselt einen GDI-Bereich zum Bearbeiten eines elliptischen, polygonalen oder unregelmäßigen Bereichs innerhalb eines Fensters. Wird in Verbindung mit den Clipping-Member-Funktionen in der-Klasse verwendet `CDC` .

[CRectTracker](reference/crecttracker-class.md)<br/>
Zeigt die Benutzeroberfläche zum Ändern der Größe und zum Verschieben von rechteckigen Objekten an und behandelt diese.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Stellt ein Standard Dialogfeld für die Auswahl einer Farbe bereit.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Stellt ein Standard Dialogfeld zum Auswählen einer Schriftart bereit.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Stellt ein Standard Dialogfeld zum Drucken einer Datei bereit.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
