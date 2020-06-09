---
title: Speicherverwaltung
ms.date: 11/04/2016
helpviewer_keywords:
- memory [MFC]
- MFC, memory management
- memory allocation [MFC]
- memory [MFC], managing
- memory allocation [MFC], MFC
ms.assetid: 934ac81b-d630-4232-88e5-ea74f7187987
ms.openlocfilehash: 464a31491f2c3017453bdd5bbdc8b059d348eb3c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626263"
---
# <a name="memory-management"></a>Speicherverwaltung

In dieser Gruppe von Artikeln wird beschrieben, wie Sie die allgemeinen Dienste der Microsoft Foundation Class-Bibliothek (MFC) in Bezug auf die Speicherverwaltung nutzen. Die Speicher Belegung kann in zwei Hauptkategorien unterteilt werden: Frame Zuweisungen und Heap Zuweisungen.

Ein Hauptunterschied zwischen den beiden Zuweisungs Techniken besteht darin, dass Sie mit der Rahmen Zuordnung in der Regel mit dem eigentlichen Speicherblock selbst arbeiten. bei der Heap Zuordnung erhalten Sie immer einen Zeiger auf den Speicherblock. Ein weiterer wichtiger Unterschied zwischen den beiden Schemas besteht darin, dass Frame Objekte automatisch gelöscht werden, während Heap Objekte explizit vom Programmierer gelöscht werden müssen.

Informationen zu nicht-MFC-Informationen zur Speicherverwaltung Unterprogramme für Windows finden Sie unter [Speicherverwaltung](/windows/win32/memory/memory-management) in der Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Frame Zuordnung](memory-management-frame-allocation.md)

- [Heap Zuordnung](memory-management-heap-allocation.md)

- [Belegen von Speicher für ein Array](memory-management-examples.md)

- [Aufheben der Zuordnung von Arbeitsspeicher für ein Array aus dem Heap](memory-management-examples.md)

- [Belegen von Speicher für eine Datenstruktur](memory-management-examples.md)

- [Belegen von Speicher für ein Objekt](memory-management-examples.md)

- [Größe von Speicherblöcken mit Größenänderung](memory-management-resizable-memory-blocks.md)

## <a name="see-also"></a>Siehe auch

[Konzepte](mfc-concepts.md)<br/>
[Allgemeine MFC-Themen](general-mfc-topics.md)
