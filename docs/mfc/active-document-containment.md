---
title: Active Document-Container
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- MFC, COM support
- active document containers [MFC], about active document containers
- MFC COM, active document containment
ms.assetid: b8dfa74b-75ce-47df-b75e-fc87b7f7d687
ms.openlocfilehash: 1c524d6890cd7b86bcae2c40d8c602e7b04e751b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623434"
---
# <a name="active-document-containment"></a>Active Document-Container

Die aktive Dokument Kapselung ist eine Technologie, die einen einzelnen Frame zum Arbeiten mit Dokumenten bereitstellt, anstatt Sie zu zwingen, mehrere Anwendungs Frames für jeden Dokumenttyp zu erstellen und zu verwenden. Dies unterscheidet sich von der grundlegenden OLE-Technologie, da OLE mit eingebetteten Objekten in einem Verbund Dokument funktioniert, in dem nur ein einzelnes Inhalts Element aktiv sein kann. Mit der aktiven Dokument Kapselung aktivieren Sie ein gesamtes Dokument (d. h. eine gesamte Anwendung, einschließlich der zugehörigen Menüs, Symbolleisten usw.) innerhalb des Kontexts eines einzelnen Frames.

Die Active Document Containment-Technologie wurde ursprünglich für die Microsoft Office der Implementierung von Office-Binder entwickelt. Allerdings ist die Technologie flexibel genug, um aktive Dokument Container als Office-Binder zu unterstützen, und kann andere Dokument Server als Office-und Office-kompatible Anwendungen unterstützen.

Die Anwendung, die aktive Dokumente hostet, wird als [aktiver Dokument Container](active-document-containers.md)bezeichnet. Beispiele für derartige Container sind der Microsoft Office Binder oder Microsoft Internet Explorer.

Die aktive Dokument Kapselung wird als Satz von Erweiterungen für OLE-Dokumente implementiert, der Verbund Dokumenten Technologie von OLE. Bei den Erweiterungen handelt es sich um zusätzliche Schnittstellen, die es ermöglichen, dass ein einbettbares, direktes Objekt ein gesamtes Dokument anstelle eines einzelnen eingebetteten Inhalts darstellt. Wie bei OLE-Dokumenten verwendet die aktive Dokument Kapselung einen Container, der den Anzeigebereich für aktive Dokumente und Server bereitstellt, die die Benutzeroberfläche und die Bearbeitungsfunktionen für die aktiven Dokumente selbst bereitstellen.

Ein [aktiver Dokument Server](active-document-servers.md) ist eine Anwendung (z. b. Word, Excel oder PowerPoint), die mindestens eine aktive Dokument Klasse unterstützt, wobei jedes Objekt selbst die Erweiterungs Schnittstellen unterstützt, mit denen das Objekt in einem geeigneten Container aktiviert werden kann.

Ein [aktives Dokument](active-documents.md) (das von einem aktiven Dokument Server wie z. b. Word oder Excel bereitgestellt wird) ist im Grunde ein herkömmliches Dokument, das in einem anderen aktiven Dokument Container als Objekt eingebettet ist. Im Gegensatz zu eingebetteten Objekten haben aktive Dokumente vollständige Kontrolle über Ihre Seiten, und die vollständige Oberfläche der Anwendung (mit allen zugehörigen Befehlen und Tools) ist für den Benutzer zur Bearbeitung verfügbar.

Ein aktives Dokument ist am besten zu verstehen, indem es von einem OLE Embedded-Standard Objekt unterschieden wird. Nach der OLE-Konvention wird ein eingebettetes Objekt in der Seite des Dokuments angezeigt, das es besitzt, und das Dokument wird von einem OLE-Container verwaltet. Der Container speichert die Daten des eingebetteten Objekts mit dem restlichen Dokument. Eingebettete Objekte sind jedoch so eingeschränkt, dass Sie nicht die Seite steuern, auf der Sie angezeigt werden.

Benutzer einer aktiven Dokument Containeranwendung können aktive Dokumente (als Abschnitte in Office-Binder bezeichnet) mit Ihren bevorzugten Anwendungen erstellen (vorausgesetzt, diese Anwendungen sind als aktives Dokument aktiviert), aber die Benutzer können das resultierende Projekt als einzelne Entität verwalten, die eindeutig benannt, gespeichert, gedruckt usw. sein kann. Auf dieselbe Weise kann ein Benutzer eines Internet Browsers sowohl das gesamte Netzwerk als auch lokale Dateisysteme als eine einzelne Dokument Speicher Entität mit der Möglichkeit zum Durchsuchen der Dokumente in diesem Speicher von einem einzigen Speicherort aus behandeln.

## <a name="sample-programs"></a>Beispielprogramme

- Das [MFCBIND](../overview/visual-cpp-samples.md) -Beispiel veranschaulicht die Implementierung einer aktiven Dokument Containeranwendung.

## <a name="see-also"></a>Siehe auch

[MFC COM](mfc-com.md)
