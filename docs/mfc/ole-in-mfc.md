---
title: OLE in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, OLE and
- OLE items
- OLE applications [MFC], about OLE
- OLE [MFC]
- OLE containers [MFC], about OLE
- applications [OLE], about OLE
- OLE component object model (COM)
ms.assetid: 5193479d-1239-4697-aea4-e82f92c707ab
ms.openlocfilehash: 529b6d0eaedaee200da547ef9ed980aab51ea233
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622174"
---
# <a name="ole-in-mfc"></a>OLE in MFC

In diesen Artikeln werden die Grundlagen der OLE-Programmierung mit MFC erläutert. MFC bietet die einfachste Möglichkeit, Programme zu schreiben, die OLE verwenden:

- Um die visuelle OLE-Bearbeitung (direkte Aktivierung) zu verwenden.

- Zum Arbeiten als OLE-Container oder-Server.

- Zum Implementieren von Drag & amp; Drop-Funktionen.

- Um mit Datums-und Uhrzeitdaten zu arbeiten.

- Zum Verwalten der Statusdaten von MFC-Modulen, einschließlich der Einstiegspunkte für exportierte DLL-Funktionen, Einstiegspunkte der OLE/COM-Schnittstelle und Einstiegspunkte für Fenster Prozeduren.

Sie können auch [Automation](automation.md)verwenden.

> [!NOTE]
> Der Begriff "OLE" bezeichnet die Technologien, die mit Verknüpfungen und Einbettungen verknüpft sind, darunter OLE-Container, OLE-Server, OLE-Elemente, direkte Aktivierung (oder visuelle Bearbeitung), Tracker, Drag & Drop und Menü Zusammenführung. Der Begriff aktiv gilt für die Component Object Model (com) und com-basierten Objekte, wie z. b. ActiveX-Steuerelemente. OLE-Automatisierung wird jetzt als "Automatisierung" bezeichnet.

## <a name="in-this-section"></a>In diesem Abschnitt

[OLE-Hintergrund](ole-background.md)<br/>
Erläutert OLE und bietet konzeptionelle Informationen zur Funktionsweise.

[Aktivierung](activation-cpp.md)<br/>
Beschreibt die Rolle der Aktivierung bei der Bearbeitung von OLE-Elementen.

[Container](containers.md)<br/>
Stellt Links zur Verwendung von Containern in OLE bereit.

[Datenobjekte und Datenquellen](data-objects-and-data-sources-ole.md)<br/>
Enthält Links zu Themen, in denen die Verwendung der `COleDataObject` Klassen und erläutert wird `COleDataSource` .

[Drag & Drop](drag-and-drop-ole.md)<br/>
Erläutert die Verwendung von kopieren und Einfügen mit OLE.

[OLE-Menüs und-Ressourcen](menus-and-resources-ole.md)<br/>
Erläutert die Verwendung von Menüs und Ressourcen in MFC-OLE-Dokument Anwendungen.

[Registrierung](registration.md)<br/>
Erläutert die Server Installation und-Initialisierung.

[Server](servers.md)<br/>
Beschreibt, wie OLE-Elemente (oder-Komponenten) für die Verwendung durch Container Anwendungen erstellt werden.

[Tracker](trackers.md)<br/>
Bietet Informationen über die- `CRectTracker` Klasse, die eine grafische Benutzeroberfläche bereitstellt, mit der Benutzer mit OLE-Client Elementen interagieren können.

## <a name="related-sections"></a>Verwandte Abschnitte

[Verbindungspunkte](connection-points.md)<br/>
Erläutert, wie Verbindungspunkte (früher als OLE-Verbindungspunkte bezeichnet) mit den MFC-Klassen und implementiert werden `CCmdTarget` `CConnectionPoint` .

[Container/Server-COM-Komponenten](containers-advanced-features.md)<br/>
Beschreibt die Schritte, die erforderlich sind, um optionale erweiterte Funktionen in vorhandene Container Anwendungen einzubinden.

[Das Component Object Model](/windows/win32/com/the-component-object-model)<br/>
Beschreibt die Verwendung von OLE ohne MFC.

## <a name="see-also"></a>Siehe auch

[Konzepte](mfc-concepts.md)
