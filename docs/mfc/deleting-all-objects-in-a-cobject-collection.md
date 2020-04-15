---
title: Löschen aller Objekte in einer CObject-Sammlung
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 303b8a566a730c5abd06d51fb7977174e19a6435
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370534"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Löschen aller Objekte in einer CObject-Sammlung

In diesem Artikel wird erläutert, wie Sie alle Objekte in einer Auflistung löschen (ohne das Auflistungsobjekt selbst zu löschen).

Um alle Objekte in einer `CObject`Auflistung von s `CObject`(oder von ) zu löschen, verwenden Sie eine der im Artikel [Zugriff auf alle Mitglieder einer Sammlung](../mfc/accessing-all-members-of-a-collection.md) beschriebenen Iterationstechniken, um jedes Objekt nacheinander zu löschen.

> [!CAUTION]
> Objekte in Auflistungen können freigegeben werden. Das heißt, die Auflistung behält einen Zeiger auf das Objekt, aber andere Teile des Programms können auch Zeiger auf dasselbe Objekt haben. Sie müssen darauf achten, dass Sie ein freigegebenes Objekt nicht löschen, bis alle Teile mit dem Objekt fertig sind.

Dieser Artikel zeigt Ihnen, wie Sie die Objekte in folgenden Beispielen löschen:

- [Eine Liste](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Ein Array](#_core_to_delete_all_elements_in_an_array)

- [Eine Karte](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>So löschen Sie alle Objekte in einer Liste von Zeigern auf CObject

1. Verwenden `GetHeadPosition` `GetNext` und durchlaufen Sie die Liste.

1. Verwenden Sie den **Löschoperator,** um jedes Objekt so zu löschen, wie es in der Iteration auftritt.

1. Rufen `RemoveAll` Sie die Funktion auf, um alle Elemente aus der Liste zu entfernen, nachdem die mit diesen Elementen verknüpften Objekte gelöscht wurden.

Das folgende Beispiel zeigt, wie Sie `CPerson` alle Objekte aus einer Liste von Objekten löschen. Jedes Objekt in der Liste ist `CPerson` ein Zeiger auf ein Objekt, das ursprünglich auf dem Heap zugewiesen wurde.

[!code-cpp[NVC_MFCCollections#17](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Der letzte Funktionsaufruf , ist eine Listenmemberfunktion, `RemoveAll`die alle Elemente aus der Liste entfernt. Die Memberfunktion `RemoveAt` entfernt ein einzelnes Element.

Beachten Sie den Unterschied zwischen dem Löschen des Objekts eines Elements und dem Entfernen des Elements selbst. Wenn Sie ein Element aus der Liste entfernen, wird lediglich der Verweis der Liste auf das Objekt entfernt. Das Objekt ist weiterhin im Speicher vorhanden. Wenn Sie ein Objekt löschen, ist es nicht mehr vorhanden, und sein Speicher wird freigegeben. Daher ist es wichtig, ein Element unmittelbar nach dem Löschen des Elements zu entfernen, damit die Liste nicht versucht, auf Objekte zuzugreifen, die nicht mehr vorhanden sind.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>So löschen Sie alle Elemente in einem Array

1. Verwenden `GetSize` sie und ganzzahlige Indexwerte, um das Array zu durchlaufen.

1. Verwenden Sie den **Löschoperator,** um jedes Element zu löschen, wie es in der Iteration auftritt.

1. Rufen `RemoveAll` Sie die Funktion auf, um alle Elemente aus dem Array zu entfernen, nachdem sie gelöscht wurden.

   Der Code zum Löschen aller Elemente eines Arrays lautet wie folgt:

   [!code-cpp[NVC_MFCCollections#18](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Wie im obigen Listenbeispiel `RemoveAll` können Sie aufrufen, alle `RemoveAt` Elemente in einem Array oder ein einzelnes Element zu entfernen.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>So löschen Sie alle Elemente in einer Karte

1. Verwenden `GetStartPosition` `GetNextAssoc` und durchlaufen Sie das Array.

1. Verwenden Sie den **Löschoperator,** um den Schlüssel und/oder Wert für jedes Kartenelement zu löschen, wie es in der Iteration auftritt.

1. Rufen `RemoveAll` Sie die Funktion auf, um alle Elemente aus der Karte zu entfernen, nachdem sie gelöscht wurden.

   Der Code zum Löschen `CMap` aller Elemente einer Auflistung lautet wie folgt. Jedes Element in der Karte hat eine `CPerson` Zeichenfolge als `CObject`Schlüssel und ein Objekt (abgeleitet von ) als Wert.

   [!code-cpp[NVC_MFCCollections#19](../mfc/codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Sie können `RemoveAll` aufrufen, um alle `RemoveKey` Elemente in einer Karte zu entfernen oder ein einzelnes Element mit dem angegebenen Schlüssel zu entfernen.

## <a name="see-also"></a>Siehe auch

[Zugreifen auf alle Elemente einer Auflistung](../mfc/accessing-all-members-of-a-collection.md)
