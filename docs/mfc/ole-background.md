---
title: OLE-Hintergrund
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, about OLE
ms.assetid: 5f654eb5-66b1-40c9-9215-bb85356a67f8
ms.openlocfilehash: f7d65f48c1af678f6626ba7d315ceb735d3e960a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364524"
---
# <a name="ole-background"></a>OLE-Hintergrund

OLE ist ein Mechanismus, mit dem Benutzer Dokumente erstellen und bearbeiten können, die Elemente oder "Objekte" enthalten, die von mehreren Anwendungen erstellt wurden.

> [!NOTE]
> OLE war ursprünglich ein Akronym für Object Linking and Embedding. Es wird jetzt jedoch als OLE bezeichnet. Teile von OLE, die sich nicht auf das Verknüpfen und Einbetten beziehen, sind jetzt Teil der Active-Technologie.

OLE-Dokumente, die in der Vergangenheit als zusammengesetzte Dokumente bezeichnet werden, integrieren nahtlos verschiedene Arten von Daten oder Komponenten. Soundclips, Tabellenkalkulationen und Bitmaps sind typische Beispiele für Komponenten in OLE-Dokumenten. Die Unterstützung von OLE in Ihrer Anwendung ermöglicht es Benutzern, OLE-Dokumente zu verwenden, ohne sich Gedanken über den Wechsel zwischen den verschiedenen Anwendungen machen zu müssen. OLE übernimmt die Umschaltung für Sie.

Sie verwenden eine Containeranwendung, um zusammengesetzte Dokumente und eine Serveranwendung oder Komponentenanwendung zu erstellen, um die Elemente innerhalb des Containerdokuments zu erstellen. Jede Anwendung, die Sie schreiben, kann ein Container, ein Server oder beides sein.

OLE enthält viele verschiedene Konzepte, die alle auf das Ziel einer nahtlosen Interaktion zwischen Anwendungen hinarbeiten. Zu diesen Bereichen gehören:

- Verlinken und Einbetten

   Verknüpfen und Einbetten sind die beiden Methoden zum Speichern von Elementen, die in einem OLE-Dokument erstellt wurden und in einer anderen Anwendung erstellt wurden. Allgemeine Informationen zu den Unterschieden zwischen den beiden finden Sie im Artikel [OLE-Hintergrund: Verknüpfen und Einbetten](../mfc/ole-background-linking-and-embedding.md). Ausführlichere Informationen finden Sie in den Artikeln [Container](../mfc/containers.md) und [Server](../mfc/servers.md).

- In-Place-Aktivierung (visuelle Bearbeitung)

   Das Aktivieren eines eingebetteten Elements im Kontext des Containerdokuments wird als in-Place-Aktivierung oder visuelle Bearbeitung bezeichnet. Die Schnittstelle der Containeranwendung ändert sich, um die Features der Komponentenanwendung zu integrieren, die das eingebettete Element erstellt hat. Verknüpfte Elemente werden nie aktiviert, da die tatsächlichen Daten für das Element in einer separaten Datei enthalten sind, aus dem Kontext der Anwendung, die den Link enthält. Weitere Informationen zur in-place-Aktivierung finden Sie im Artikel [Aktivierung](../mfc/activation-cpp.md).

   > [!NOTE]
   > Das Verknüpfen und Einbetten und die direkte Aktivierung bieten die Hauptfunktionen der visuellen OLE-Bearbeitung.

- Mit Automation Automation kann eine Anwendung eine andere Anwendung antreiben. Die treibende Anwendung wird als Automatisierungsclient bezeichnet, und die zu beanstandende Anwendung wird als Automatisierungsserver oder Automatisierungskomponente bezeichnet. Weitere Informationen zur Automatisierung finden Sie in den Artikeln [Automation Clients](../mfc/automation-clients.md) und [Automation Servers](../mfc/automation-servers.md).

   > [!NOTE]
   > Die Automatisierung funktioniert sowohl im OLE- als auch im Active-Technologiekontext. Sie können jedes Objekt basierend auf COM automatisieren.

- Verbunddateien

   Zusammengesetzte Dateien bieten ein Standarddateiformat, das das strukturierte Speichern von zusammengesetzten Dokumenten für OLE-Anwendungen vereinfacht. Innerhalb einer zusammengesetzten Datei haben Speicher viele Funktionen von Verzeichnissen und Streams haben viele Funktionen von Dateien. Diese Technologie wird auch als strukturierter Speicher bezeichnet. Weitere Informationen zu zusammengesetzten Dateien finden Sie im Artikel [Container: Zusammengesetzte Dateien](../mfc/containers-compound-files.md).

- Einheitliche Datenübertragung

   Uniform Data Transfer (UDT) ist ein Satz von Schnittstellen, die das Senden und Empfangen von Daten in Standardform ermöglichen, unabhängig von der tatsächlichen Methode, die für die Übertragung der Daten gewählt wurde. UDT bildet die Grundlage für Datenübertragungen per Drag & Drop. UDT dient nun als Grundlage für die vorhandene Windows-Datenübertragung, wie z. B. die Zwischenablage und den dynamischen Datenaustausch (DDE). Weitere Informationen zu UDT finden Sie im Artikel [Data Objects and Data Sources (OLE)](../mfc/data-objects-and-data-sources-ole.md).

- Drag & Drop

   Drag & Drop ist eine benutzerfreundliche, direkt zu bearbeitende Methode zum Übertragen von Daten zwischen Anwendungen, zwischen Fenstern innerhalb einer Anwendung oder sogar innerhalb eines einzelnen Fensters in einer Anwendung. Die zu übertragenden Daten werden ausgewählt und an das gewünschte Ziel gezogen. Drag & Drop basiert auf einer einheitlichen Datenübertragung. Weitere Informationen zum Ziehen und Ablegen finden Sie im Artikel [Drag and Drop](../mfc/drag-and-drop-ole.md).

- Component Object Model

   Das Component Object Model (COM) stellt die Infrastruktur bereit, die verwendet wird, wenn OLE-Objekte miteinander kommunizieren. Die MFC-OLE-Klassen vereinfachen COM für den Programmierer. COM ist Teil der Active-Technologie, da COM-Objekte sowohl der OLE- als auch der Active-Technologie zugrunde liegen. Weitere Informationen zu COM finden Sie in den Themen [Active Template Library (ATL).](../atl/active-template-library-atl-concepts.md)

Einige der wichtigeren OLE-Themen werden in den folgenden Artikeln behandelt:

- [OLE-Hintergrund: Verlinken und Einbetten](../mfc/ole-background-linking-and-embedding.md)

- [OLE-Hintergrund: Container und Server](../mfc/ole-background-containers-and-servers.md)

- [OLE-Hintergrund: Implementierungsstrategien](../mfc/ole-background-implementation-strategies.md)

- [OLE-Hintergrund: MFC-Implementierung](../mfc/ole-background-mfc-implementation.md)

Suchen Sie in MSDN nach OLE, um allgemeine OLE-Informationen zu erhalten, die in den obigen Artikeln nicht zu finden sind.

## <a name="see-also"></a>Siehe auch

[OLE](../mfc/ole-in-mfc.md)
