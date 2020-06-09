---
title: Sammlungen
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
ms.openlocfilehash: f2cd03afbb09dff38298454658c3d3dc2dfa6a8a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619345"
---
# <a name="collections"></a>Sammlungen

Der Microsoft Foundation Class-Bibliothek stellt Auflistungs Klassen zum Verwalten von Gruppen von Objekten bereit. Diese Klassen sind von zwei Typen:

- [Aus C++-Vorlagen erstellte Auflistungs Klassen](#_core_the_template_based_collection_classes)

- [Sammlungs Klassen, die nicht aus Vorlagen erstellt wurden](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
> Wenn Ihr Code bereits nicht Vorlagen Auflistungs Klassen verwendet, können Sie diese weiterhin verwenden. Wenn Sie neue typsichere Auflistungs Klassen für Ihre eigenen Datentypen schreiben, empfiehlt es sich, die neueren Vorlagen basierten Klassen zu verwenden.

## <a name="collection-shapes"></a><a name="_core_collection_shapes"></a>Sammlungs Formen

Eine Auflistungs Klasse ist durch die Form "Form" und durch die Typen ihrer Elemente gekennzeichnet. Die Form bezieht sich auf die Art und Weise, in der die Objekte von der Auflistung organisiert und gespeichert werden. MFC bietet drei grundlegende Sammlungs Formen: Listen, Arrays und Karten (auch als Wörterbücher bezeichnet). Sie können die Form Sammlung auswählen, die sich am besten für ihr bestimmtes Programmierproblem eignet.

Jede der drei bereitgestellten Auflistungs Formen wird kurz später in diesem Thema beschrieben. Informationen zum Vergleichen der Features der Formen, damit Sie entscheiden können, welches für Ihr Programm am besten geeignet ist, finden Sie unter [Empfehlungen für die Auswahl einer Sammlungsklasse](recommendations-for-choosing-a-collection-class.md).

- List

   Die List-Klasse stellt eine geordnete, nicht indizierte Liste von Elementen bereit, die als doppelt verknüpfte Liste implementiert ist. Eine Liste weist einen "Head" und ein "tail" auf, und das Hinzufügen oder Entfernen von Elementen aus dem Head-oder tail-Element oder das Einfügen oder Löschen von Elementen in der Mitte ist sehr schnell.

- Array

   Die Array-Klasse stellt ein dynamisch formatierstelltes, geordnetes und ganz Zahl indiziertes Array von-Objekten bereit.

- Map (auch als Wörterbuch bezeichnet)

   Eine Zuordnung ist eine Auflistung, die ein Schlüsselobjekt einem Wertobjekt zuordnet.

## <a name="the-template-based-collection-classes"></a><a name="_core_the_template_based_collection_classes"></a>Vorlagenbasierte Auflistungs Klassen

Die einfachste Möglichkeit, eine typsichere Auflistung zu implementieren, die Objekte eines beliebigen Typs enthält, besteht darin, eine der auf MFC-Vorlagen basierenden Klassen zu verwenden. Beispiele für diese Klassen finden Sie unter MFC-Beispiel [Sammlung](../overview/visual-cpp-samples.md).

In der folgenden Tabelle sind die auf MFC-Vorlagen basierenden Sammlungs Klassen aufgeführt.

### <a name="collection-template-classes"></a>Sammlungsvorlagen Klassen

|Sammlungs Inhalt|Arrays|Listen|Maps|
|-------------------------|------------|-----------|----------|
|Sammlungen von Objekten eines beliebigen Typs|`CArray`|`CList`|`CMap`|
|Auflistungen von Zeigern auf Objekte eines beliebigen Typs|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

## <a name="the-collection-classes-not-based-on-templates"></a><a name="_core_the_collection_classes_not_based_on_templates"></a>Die Auflistungs Klassen, die nicht auf Vorlagen basieren

Wenn Ihre Anwendung bereits MFC-Auflistungs-Klassen verwendet, können Sie Sie weiterhin verwenden. Für neue Sammlungen empfiehlt es sich jedoch, die Vorlagen basierten Klassen zu verwenden. In der folgenden Tabelle werden die MFC-Auflistungs Klassen aufgelistet, die nicht auf Vorlagen basieren.

### <a name="nontemplate-collection-classes"></a>Nontemplate-Auflistungs Klassen

|Arrays|Listen|Maps|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

Die Eigenschaften der MFC-Auflistungs Klassen Tabelle in [Empfehlungen für die Auswahl einer Sammlungsklasse](recommendations-for-choosing-a-collection-class.md) beschreiben die MFC-Auflistungs Klassen in Bezug auf diese Merkmale (mit Ausnahme von Form):

- ob die Klasse C++-Vorlagen verwendet

- ob die in der Auflistung gespeicherten Elemente serialisiert werden können

- ob die in der Auflistung gespeicherten Elemente zur Diagnose gesichert werden können

- ob die Auflistung typsicher ist

### <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

#### <a name="general-collection-class-tasks"></a>Allgemeine Auflistungs Klassenaufgaben

- [Empfehlungen für die Auswahl einer Sammlungsklasse](recommendations-for-choosing-a-collection-class.md)

- [Vorgehensweise: Erstellen einer typsicheren Auflistung](how-to-make-a-type-safe-collection.md)

- [Erstellen von Stack- und Warteschlangenauflistungen](creating-stack-and-queue-collections.md)

- [CArray:: Add](reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>Vorlagenbasierte Auflistungs Klassen Tasks

- [Vorlagenbasierte Klassen](template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>Zugreifen auf die Member einer Auflistung (Vorlagen basiert oder nicht)

- [Zugreifen auf alle Elemente einer Auflistung](accessing-all-members-of-a-collection.md)

- [Löschen aller Objekte in einer CObject-Sammlung](deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>Siehe auch

[Konzepte](mfc-concepts.md)<br/>
[Allgemeine MFC-Themen](general-mfc-topics.md)
