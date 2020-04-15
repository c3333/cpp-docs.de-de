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
ms.openlocfilehash: 2594531df63bcd62cdaec44fbc3668ea68990922
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366898"
---
# <a name="ole-in-mfc"></a>OLE in MFC

In diesen Artikeln werden die Grundlagen der OLE-Programmierung mit MFC erläutert. MFC bietet die einfachste Möglichkeit, Programme zu schreiben, die OLE verwenden:

- So verwenden Sie die visuelle OLE-Bearbeitung (ortsnahe Aktivierung).

- So arbeiten Sie als OLE-Container oder -Server.

- So implementieren Sie Drag-and-Drop-Funktionen.

- So arbeiten Sie mit Datums- und Uhrzeitdaten.

- Verwalten der Statusdaten von MFC-Modulen, einschließlich exportierter DLL-Funktionseinstiegspunkte, OLE/COM-Schnittstelleneinstiegspunkte und Fensterprozedur-Einstiegspunkte.

Sie können auch [Automation](../mfc/automation.md)verwenden.

> [!NOTE]
> Der Begriff OLE bezeichnet die Technologien, die mit dem Verknüpfen und Einbetten verbunden sind, einschließlich OLE-Containern, OLE-Servern, OLE-Elementen, direkte Aktivierung (oder visuelle Bearbeitung), Trackern, Drag & Drop und Menüzusammenführen. Der Begriff Aktiv gilt für das Component Object Model (COM) und COM-basierte Objekte wie ActiveX-Steuerelemente. OLE Automation heißt jetzt Automation.

## <a name="in-this-section"></a>In diesem Abschnitt

[OLE-Hintergrund](../mfc/ole-background.md)<br/>
Erläutert OLE und stellt konzeptionelle Informationen zur Funktionsweise bereit.

[Aktivierung](../mfc/activation-cpp.md)<br/>
Beschreibt die Rolle der Aktivierung beim Bearbeiten von OLE-Elementen.

[Container](../mfc/containers.md)<br/>
Stellt Links zur Verwendung von Containern in OLE bereit.

[Datenobjekte und Datenquellen](../mfc/data-objects-and-data-sources-ole.md)<br/>
Enthält Links zu Themen, `COleDataObject` in `COleDataSource` denen die Verwendung von und Klassen erläutert wird.

[Drag & Drop](../mfc/drag-and-drop-ole.md)<br/>
Erläutert das Kopieren und Einfügen mit OLE.

[OLE-Menüs und Ressourcen](../mfc/menus-and-resources-ole.md)<br/>
Erläutert die Verwendung von Menüs und Ressourcen in MFC-OLE-Dokumentanwendungen.

[Registrierung](../mfc/registration.md)<br/>
Erläutert die Serverinstallation und -initialisierung.

[Server](../mfc/servers.md)<br/>
Beschreibt das Erstellen von OLE-Elementen (oder -Komponenten) für die Verwendung durch Containeranwendungen.

[Tracker](../mfc/trackers.md)<br/>
Stellt Informationen `CRectTracker` zur Klasse bereit, die eine grafische Benutzeroberfläche bereitstellt, mit der Benutzer mit OLE-Clientelementen interagieren können.

## <a name="related-sections"></a>Verwandte Abschnitte

[Verbindungspunkte](../mfc/connection-points.md)<br/>
Erläutert das Implementieren von Verbindungspunkten (früher als OLE-Verbindungspunkte bezeichnet) mithilfe der MFC-Klassen `CCmdTarget` und `CConnectionPoint`.

[Container-/Server-COM-Komponenten](../mfc/containers-advanced-features.md)<br/>
Beschreibt die Schritte, die erforderlich sind, um optionale erweiterte Features in vorhandene Containeranwendungen zu integrieren.

[Das Component Object Model](/windows/win32/com/the-component-object-model)<br/>
Beschreibt die Verwendung von OLE ohne MFC.

## <a name="see-also"></a>Siehe auch

[Konzepte](../mfc/mfc-concepts.md)
