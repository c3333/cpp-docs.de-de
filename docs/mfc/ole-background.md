---
title: OLE-Hintergrund
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: 96ece9a2a5be6ea29c95e17e81f6ce4adbfd4c0b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624164"
---
# <a name="ole-background"></a>OLE-Hintergrund

OLE ist ein Mechanismus, mit dem Benutzer Dokumente erstellen und bearbeiten können, die Elemente enthalten, die von mehreren Anwendungen erstellt wurden.

> [!NOTE]
> OLE war ursprünglich ein Akronym für das Verknüpfen und Einbetten von Objekten. Es wird jedoch jetzt als OLE bezeichnet. Teile von OLE, die nicht mit Verknüpfungen und Einbettungen verwandt sind, sind jetzt Bestandteil der aktiven Technologie.

OLE-Dokumente, die in der Vergangenheit als Verbund Dokumente bezeichnet wurden, integrieren verschiedene Datentypen oder Komponenten nahtlos. Sound Ausschnitte, Kalkulations Tabellen und Bitmaps sind typische Beispiele für Komponenten, die in OLE-Dokumenten gefunden werden. Die Unterstützung von OLE in Ihrer Anwendung ermöglicht Ihren Benutzern die Verwendung von OLE-Dokumenten, ohne sich Gedanken über den Wechsel zwischen den verschiedenen Anwendungen OLE führt den Wechsel für Sie durch.

Zum Erstellen von Verbund Dokumenten und einer Serveranwendung oder einer Komponenten Anwendung verwenden Sie eine Containeranwendung, um die Elemente im Container Dokument zu erstellen. Jede Anwendung, die Sie schreiben, kann ein Container, ein Server oder beides sein.

OLE beinhaltet viele verschiedene Konzepte, die alle für das Ziel der nahtlosen Interaktion zwischen Anwendungen funktionieren. Diese Bereiche umfassen Folgendes:

- Verlinken und Einbetten

   Verknüpfungen und Einbettungen sind die zwei Methoden zum Speichern von Elementen, die in einem in einer anderen Anwendung erstellten OLE-Dokument erstellt wurden. Allgemeine Informationen zu den Unterschieden zwischen den beiden finden Sie im Artikel [OLE-Hintergrund: verknüpfen und Einbetten](ole-background-linking-and-embedding.md). Ausführlichere Informationen finden Sie in den Artikeln [Container](containers.md) und [Server](servers.md).

- Direkte Aktivierung (visuelle Bearbeitung)

   Das Aktivieren eines eingebetteten Elements im Kontext des Container Dokuments wird als direkte Aktivierung oder visuelle Bearbeitung bezeichnet. Die-Schnittstelle der Containeranwendung ändert sich, um die Funktionen der Komponenten Anwendung zu integrieren, die das eingebettete Element erstellt hat. Verknüpfte Elemente werden niemals an Ort und Stelle aktiviert, da die eigentlichen Daten für das Element in einer separaten Datei enthalten sind, aus dem Kontext der Anwendung, die den Link enthält. Weitere Informationen zur direkten Aktivierung finden Sie im Artikel [Activation (Aktivierung](activation-cpp.md)).

   > [!NOTE]
   > Das Verknüpfen und Einbetten und die direkte Aktivierung stellen die wichtigsten Funktionen der visuellen OLE-Bearbeitung dar.

- Automation Automation ermöglicht einer Anwendung, eine andere Anwendung zu steuern. Die treibende Anwendung wird als Automatisierungs Client bezeichnet, und die Anwendung, die gesteuert wird, wird als Automatisierungsserver oder Automatisierungskomponente bezeichnet. Weitere Informationen zur Automatisierung finden Sie in den Artikeln [Automation Clients](automation-clients.md) and [Automation Servers](automation-servers.md).

   > [!NOTE]
   > Automation funktioniert sowohl in OLE-als auch in aktiven Technologie Kontexten. Sie können ein beliebiges Objekt auf der Grundlage von com automatisieren.

- Verbunddateien

   Verbund Dateien stellen ein Standarddatei Format bereit, das die strukturierte Speicherung von Verbund Dokumenten für OLE-Anwendungen vereinfacht. In einer Verbund Datei verfügen Speicher über viele Funktionen von Verzeichnissen und Streams über zahlreiche Funktionen von Dateien. Diese Technologie wird auch als strukturierter Speicher bezeichnet. Weitere Informationen zu Verbund Dateien finden Sie im Artikel [Container: Verbund Dateien](containers-compound-files.md).

- Uniform Data Transfer

   Uniform Data Transfer (UDT) ist ein Satz von Schnittstellen, mit denen Datenstandard mäßig gesendet und empfangen werden können, unabhängig von der eigentlichen Methode, die zum Übertragen der Daten gewählt wurde. UDT bildet die Grundlage für Datenübertragungen per Drag & Drop. UDT dient nun als Grundlage für die vorhandene Windows-Datenübertragung, z. b. die Zwischenablage und der dynamische Datenaustausch (DDE). Weitere Informationen zu UDT finden Sie im Artikel [Datenobjekte und Datenquellen (OLE)](data-objects-and-data-sources-ole.md).

- Drag & Drop

   Drag & Drop ist eine einfach zu verwendende, direkt Bearbeitungsmethode zum Übertragen von Daten zwischen Anwendungen, zwischen Fenstern innerhalb einer Anwendung oder sogar innerhalb eines einzelnen Fensters in einer Anwendung. Die zu übertragenden Daten werden ausgewählt und auf das gewünschte Ziel gezogen. Drag & Drop basiert auf einheitlicher Datenübertragung. Weitere Informationen zum Ziehen und ablegen finden Sie im Artikel [Drag & Drop](drag-and-drop-ole.md).

- Component Object Model

   Der Component Object Model (com) stellt die Infrastruktur bereit, die verwendet wird, wenn OLE-Objekte miteinander kommunizieren. Die MFC-OLE-Klassen vereinfachen com für den Programmierer. Com ist Teil der aktiven Technologie, weil COM-Objekte sowohl OLE als auch aktive Technologie zugrunde liegen. Weitere Informationen zu com finden Sie in den Themen [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md) .

Einige der wichtigeren OLE-Themen werden in den folgenden Artikeln behandelt:

- [OLE-Hintergrund: Verlinken und Einbetten](ole-background-linking-and-embedding.md)

- [OLE-Hintergrund: Container und Server](ole-background-containers-and-servers.md)

- [OLE-Hintergrund: Implementierungsstrategien](ole-background-implementation-strategies.md)

- [OLE-Hintergrund: MFC-Implementierung](ole-background-mfc-implementation.md)

Allgemeine OLE-Informationen, die in den obigen Artikeln nicht gefunden wurden, finden Sie unter OLE in MSDN.

## <a name="see-also"></a>Siehe auch

[OLE](ole-in-mfc.md)
