---
title: IUnknown-Implementierungsklassen (ATL)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IUnknown implementation classes
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
ms.openlocfilehash: 26751c013d65142393377394006a9833e6c8f7bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261890"
---
# <a name="iunknown-implementation-classes"></a>IUnknown-Implementierung-Klassen

Die folgenden Klassen implementieren `IUnknown` und verwandten Methoden:

- [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) verweiszählung für aggregierte und zusammengesetzten Objekte verwaltet. Ermöglicht Ihnen die Angabe ein Threadingmodell.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) verweiszählung für aggregierte und zusammengesetzten Objekte verwaltet. Der Standardhost threading-Modell des Servers verwendet.

- [CComAggObject](../atl/reference/ccomaggobject-class.md) implementiert `IUnknown` für ein zusammengesetztes Objekt.

- [CComObject](../atl/reference/ccomobject-class.md) implementiert `IUnknown` für einen zusammengesetzten Objekt.

- [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementiert `IUnknown` für aggregierte Daten und zusammengesetzten Objekte. Mithilfe von `CComPolyObject` wird vermieden, dass beide `CComAggObject` und `CComObject` innerhalb des Moduls. Ein einzelnes `CComPolyObject` Objekt behandelt, aggregierte und zusammengesetzten Fälle.

- [CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) implementiert `IUnknown` für eines zusammengesetzten Objekts, ohne die Sperrenanzahl des Moduls zu ändern.

- [CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) implementiert `IUnknown` für eine Tearoff Schnittstelle.

- [CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) implementiert `IUnknown` für eine "zwischengespeicherten" abtrennbare-Schnittstelle.

- [CComContainedObject](../atl/reference/ccomcontainedobject-class.md) implementiert `IUnknown` für das inneren Objekt eine Aggregation oder eine Tearoff Schnittstelle.

- [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) verwaltet ein Verweiszähler für das Modul, um sicherzustellen, dass das Objekt wird nicht gelöscht.

- [CComObjectStack](../atl/reference/ccomobjectstack-class.md) erstellt ein temporäre COM-Objekt, mit eine skeletal-Implementierung des `IUnknown`.

## <a name="related-articles"></a>Verwandte Artikel

[Grundlagen von ARL COM-Objekten](../atl/fundamentals-of-atl-com-objects.md)

## <a name="see-also"></a>Siehe auch

[Übersicht über die Klasse](../atl/atl-class-overview.md)<br/>
[Aggregation und Klassenfactory-Makros](../atl/reference/aggregation-and-class-factory-macros.md)<br/>
[COM-Zuordnungs-Makros](../atl/reference/com-map-macros.md)<br/>
[Globale COM-Zuordnungs-Funktionen](../atl/reference/com-map-global-functions.md)
