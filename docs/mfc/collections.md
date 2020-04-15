---
title: Auflistungen
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
ms.openlocfilehash: 3fba3a3c6cd3fecbda7f46575b1d72c450c44019
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361870"
---
# <a name="collections"></a>Auflistungen

Die Microsoft Foundation-Klassenbibliothek stellt Auflistungsklassen zum Verwalten von Objektgruppen bereit. Diese Klassen haben zwei Typen:

- [Sammlungsklassen, die aus C++-Vorlagen erstellt wurden](#_core_the_template_based_collection_classes)

- [Auflistungsklassen, die nicht aus Vorlagen erstellt wurden](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Wenn Ihr Code bereits Nichtvorlagenauflistungsklassen verwendet, können Sie sie weiterhin verwenden. Wenn Sie neue typsichere Auflistungsklassen für Ihre eigenen Datentypen schreiben, wird empfohlen, die neueren vorlagenbasierten Klassen zu verwenden.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Sammlungsformen

Eine Auflistungsklasse zeichnet sich durch ihre "Form" und die Typen ihrer Elemente aus. Die Form bezieht sich auf die Art und Weise, wie die Objekte von der Auflistung organisiert und gespeichert werden. MFC stellt drei grundlegende Auflistungs-Shapes bereit: Listen, Arrays und Karten (auch als Wörterbücher bezeichnet). Sie können die Sammlungsform auswählen, die für Ihr spezielles Programmierproblem am besten geeignet ist.

Jedes der drei bereitgestellten Auflistungs-Shapes wird später in diesem Thema kurz beschrieben. Informationen zum Vergleichen der Features der Shapes, mit denen Sie entscheiden können, welche für Ihr Programm am besten ist, finden Sie unter [Empfehlungen zum Auswählen einer Sammlungsklasse](../mfc/recommendations-for-choosing-a-collection-class.md).

- List

   Die Listenklasse stellt eine geordnete, nicht indizierte Liste von Elementen bereit, die als doppelt verknüpfte Liste implementiert ist. Eine Liste hat einen "Kopf" und einen "Schwanz", und das Hinzufügen oder Entfernen von Elementen aus dem Kopf oder Schwanz oder das Einfügen oder Löschen von Elementen in der Mitte ist sehr schnell.

- Array

   Die Arrayklasse stellt ein Array mit dynamischer Größe, geordneter und ganzzahliger Indizierter Array von Objekten bereit.

- Karte (auch als Wörterbuch bekannt)

   Eine Zuordnung ist eine Auflistung, die einem Wertobjekt ein Schlüsselobjekt zuordnet.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Die vorlagenbasierten Auflistungsklassen

Die einfachste Möglichkeit zum Implementieren einer typsicheren Auflistung, die Objekte eines beliebigen Typs enthält, besteht darin, eine der Aufderader-basierten MFC-Vorlagenklassen zu verwenden. Beispiele für diese Klassen finden Sie im MFC-Beispiel [COLLECT](../overview/visual-cpp-samples.md).

In der folgenden Tabelle sind die auf MFC-Vorlagen basierenden Auflistungsklassen aufgeführt.

### <a name="collection-template-classes"></a>Sammlungsvorlagenklassen

|Sammlungsinhalt|Arrays|Listen|Karten|
|-------------------------|------------|-----------|----------|
|Auflistungen von Objekten eines beliebigen Typs|`CArray`|`CList`|`CMap`|
|Auflistungen von Zeigern auf Objekte eines beliebigen Typs|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Die Auflistungsklassen, die nicht auf Vorlagen basieren

Wenn Ihre Anwendung bereits MFC-Nichtvorlagenklassen verwendet, können Sie sie weiterhin verwenden. Für neue Sammlungen wird jedoch empfohlen, die vorlagenbasierten Klassen zu verwenden. In der folgenden Tabelle sind die MFC-Auflistungsklassen aufgeführt, die nicht auf Vorlagen basieren.

### <a name="nontemplate-collection-classes"></a>Nontemplate-Auflistungsklassen

|Arrays|Listen|Karten|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Die Tabelle Merkmale von MFC-Auflistungsklassen in den Empfehlungen für die [Auswahl einer Auflistungsklasse](../mfc/recommendations-for-choosing-a-collection-class.md) beschreibt die MFC-Auflistungsklassen in Bezug auf diese Eigenschaften (außer Shape):

- ob die Klasse C++-Vorlagen verwendet

- ob die in der Auflistung gespeicherten Elemente serialisiert werden können

- ob die in der Auflistung gespeicherten Elemente zur Diagnose gesichert werden können

- ob die Auflistung typsicher ist

### <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

#### <a name="general-collection-class-tasks"></a>Allgemeine Aufgaben der Sammlungsklasse

- [Empfehlungen für die Auswahl einer Sammlungsklasse](../mfc/recommendations-for-choosing-a-collection-class.md)

- [Vorgehensweise: Erstellen einer typsicheren Auflistung](../mfc/how-to-make-a-type-safe-collection.md)

- [Erstellen von Stack- und Warteschlangenauflistungen](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Hinzufügen](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Vorlagenbasierte Aufgaben der Sammlungsklasse

- [Vorlagenbasierte Klassen](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Zugriff auf die Mitglieder einer Sammlung (Vorlagenbasiert oder nicht)

- [Zugreifen auf alle Elemente einer Auflistung](../mfc/accessing-all-members-of-a-collection.md)

- [Löschen aller Objekte in einer CObject-Sammlung](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Siehe auch

[Konzepte](../mfc/mfc-concepts.md)<br/>
[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)
