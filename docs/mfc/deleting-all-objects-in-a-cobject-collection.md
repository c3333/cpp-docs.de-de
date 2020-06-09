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
ms.openlocfilehash: 2921fe4e4f10c96a096d30d8f842eecdfd644ca6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615912"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Löschen aller Objekte in einer CObject-Sammlung

In diesem Artikel wird erläutert, wie alle Objekte in einer Auflistung gelöscht werden (ohne das Sammlungsobjekt selbst zu löschen).

Zum Löschen aller Objekte in einer Auflistung von `CObject` s (oder von Objekten `CObject` , die von abgeleitet werden) verwenden Sie eine der Iterations Techniken, die im Artikel [zugreifen auf alle Member einer](accessing-all-members-of-a-collection.md) Auflistung beschrieben werden, um jedes Objekt seinerseits zu löschen.

> [!CAUTION]
> Objekte in Auflistungen können freigegeben werden. Das heißt, die-Auflistung behält einen Zeiger auf das-Objekt bei, aber andere Teile des Programms haben möglicherweise auch Zeiger auf das gleiche Objekt. Sie müssen darauf achten, dass Sie ein Objekt, das freigegeben wird, erst löschen, wenn alle Teile die Verwendung des-Objekts abgeschlossen haben.

In diesem Artikel wird erläutert, wie die Objekte in gelöscht werden:

- [Eine Liste](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Ein Array](#_core_to_delete_all_elements_in_an_array)

- [Eine Karte](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>So löschen Sie alle Objekte in einer Liste von Zeigern auf CObject

1. Verwenden `GetHeadPosition` `GetNext` Sie und, um die Liste zu durchlaufen.

1. Verwenden Sie den **Delete** -Operator, um alle Objekte zu löschen, wie Sie in der Iterationen gefunden werden.

1. Ruft die- `RemoveAll` Funktion auf, um alle Elemente aus der Liste zu entfernen, nachdem die-Objekte, die diesen Elementen zugeordnet sind, gelöscht wurden.

Im folgenden Beispiel wird gezeigt, wie alle-Objekte aus einer Liste von-Objekten gelöscht werden `CPerson` . Jedes Objekt in der Liste ist ein Zeiger auf ein- `CPerson` Objekt, das ursprünglich auf dem Heap zugeordnet wurde.

[!code-cpp[NVC_MFCCollections#17](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Der letzte Funktions Aufrufwert, `RemoveAll` , ist eine List-Member-Funktion, die alle Elemente aus der Liste entfernt. Die Member-Funktion `RemoveAt` entfernt ein einzelnes Element.

Beachten Sie den Unterschied zwischen dem Löschen eines Element Objekts und dem Entfernen des Elements selbst. Durch das Entfernen eines Elements aus der Liste wird lediglich der Verweis der Liste auf das-Objekt entfernt. Das Objekt ist weiterhin im Arbeitsspeicher vorhanden. Wenn Sie ein Objekt löschen, ist es nicht mehr vorhanden, und sein Speicher wird freigegeben. Daher ist es wichtig, ein Element unmittelbar nach dem Löschen des-Objekts zu entfernen, sodass die Liste nicht mehr auf nicht mehr vorhandene Objekte zugreift.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>So löschen Sie alle Elemente in einem Array

1. Verwenden `GetSize` Sie und ganzzahlige Indexwerte, um das Array zu durchlaufen.

1. Verwenden Sie den **Delete** -Operator, um jedes Element zu löschen, das in der Iterations-gefunden wurde.

1. Ruft die- `RemoveAll` Funktion auf, um alle Elemente aus dem Array zu entfernen, nachdem Sie gelöscht wurden.

   Der Code zum Löschen aller Elemente eines Arrays lautet wie folgt:

   [!code-cpp[NVC_MFCCollections#18](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Wie im obigen Listen Beispiel können Sie auch `RemoveAll` zum Entfernen aller Elemente in einem Array oder `RemoveAt` zum Entfernen eines einzelnen Elements aufruft.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>So löschen Sie alle Elemente in einer Zuordnung

1. Verwenden `GetStartPosition` `GetNextAssoc` Sie und, um das Array zu durchlaufen.

1. Verwenden Sie den **Delete** -Operator, um den Schlüssel und/oder den Wert für jedes Kartenelement zu löschen, das in der Iterations-gefunden wurde.

1. Ruft die- `RemoveAll` Funktion auf, um alle Elemente aus der Zuordnung zu entfernen, nachdem Sie gelöscht wurden.

   Der Code zum Löschen aller Elemente einer Auflistung `CMap` lautet wie folgt. Jedes Element in der Zuordnung hat eine Zeichenfolge als Schlüssel und ein- `CPerson` Objekt (abgeleitet von `CObject` ) als-Wert.

   [!code-cpp[NVC_MFCCollections#19](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Sie können aufzurufen `RemoveAll` , um alle Elemente in einer Zuordnung `RemoveKey` zu entfernen oder ein einzelnes Element mit dem angegebenen Schlüssel zu entfernen.

## <a name="see-also"></a>Siehe auch

[Zugreifen auf alle Elemente einer Auflistung](accessing-all-members-of-a-collection.md)
