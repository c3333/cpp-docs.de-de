---
title: Grundlagen von ATL COM-Objekten
ms.date: 11/19/2018
helpviewer_keywords:
- COM, and ATL
- ATL, COM
- ATL COM objects
- COM objects, ATL
ms.assetid: 0f9c9d98-cc28-45da-89ac-dc94cee422fe
ms.openlocfilehash: 651413534ed44143e2a0fdaf00bdabd6e5d57010
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319557"
---
# <a name="fundamentals-of-atl-com-objects"></a>Grundlagen von ATL COM-Objekten

Die folgende Abbildung zeigt die Beziehung zwischen den Klassen und Schnittstellen, die zum Definieren eines ATL COM-Objekts verwendet werden.

![ATL-Struktur](../atl/media/vc307y1.gif "ATL-Struktur")

> [!NOTE]
> Dieses Diagramm `CComObject` zeigt, `CYourClass` dass `CComAggObject` `CComPolyObject` von `CYourClass` der Whereas abgeleitet und als Membervariable enthalten.

Es gibt drei Möglichkeiten, ein ATL COM-Objekt zu definieren. Die Standardoption besteht `CComObject` darin, die `CYourClass`Klasse zu verwenden, die von abgeleitet wird. Die zweite Option besteht darin, ein `CComAggObject` aggregiertes Objekt mithilfe der Klasse zu erstellen. Die dritte Option ist `CComPolyObject` die Verwendung der Klasse. `CComPolyObject`fungiert als Hybrid: Sie kann `CComObject` als Klasse `CComAggObject` oder als Klasse fungieren, je nachdem, wie sie zuerst erstellt wird. Weitere Informationen zur Verwendung `CComPolyObject` der Klasse finden Sie unter [CComPolyObject Class](../atl/reference/ccompolyobject-class.md).

Wenn Sie Standard-ATL-COM verwenden, verwenden Sie zwei Objekte: ein äußeres Objekt und ein inneres Objekt. Externe Clients greifen über die Wrapperfunktionen, die im äußeren Objekt definiert sind, auf die Funktionalität des inneren Objekts zu. Das äußere Objekt `CComObject`ist vom Typ .

Wenn Sie ein aggregiertes Objekt verwenden, stellt das äußere Objekt keine Wrapper für die Funktionalität des inneren Objekts bereit. Stattdessen stellt das äußere Objekt einen Zeiger bereit, auf den externe Clients direkt zugreifen. In diesem Szenario ist das `CComAggObject`äußere Objekt vom Typ . Das innere Objekt ist eine Membervariable des äußeren `CYourClass`Objekts und hat vom Typ .

Da der Client nicht durch das äußere Objekt gehen muss, um mit dem inneren Objekt zu interagieren, sind aggregierte Objekte in der Regel effizienter. Außerdem muss das äußere Objekt die Funktionalität des aggregierten Objekts nicht kennen, da die Schnittstelle des aggregierten Objekts direkt für den Client verfügbar ist. Allerdings können nicht alle Objekte aggregiert werden. Damit ein Objekt aggregiert werden kann, muss es unter Berücksichtigung der Aggregation entworfen werden.

ATL implementiert [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) in zwei Phasen:

- [CComObject](../atl/reference/ccomobject-class.md), [CComAggObject](../atl/reference/ccomaggobject-class.md)oder [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementiert die `IUnknown` Methoden.

- [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) verwaltet die Verweisanzahl `IUnknown`und die äußeren Zeiger von .

Andere Aspekte Ihres ATL COM-Objekts werden von anderen Klassen behandelt:

- [CComCoClass](../atl/reference/ccomcoclass-class.md) definiert die Standardklassenfactory und das Aggregationsmodell des Objekts.

- [IDispatchImpl](../atl/reference/idispatchimpl-class.md) stellt eine Standardimplementierung des `IDispatch Interface` Teils aller dualen Schnittstellen für das Objekt bereit.

- [ISupportErrorInfoImpl](../atl/reference/isupporterrorinfoimpl-class.md) implementiert `ISupportErrorInfo` die Schnittstelle, die sicherstellt, dass Fehlerinformationen in der Aufrufkette korrekt weitergegeben werden können.

## <a name="in-this-section"></a>In diesem Abschnitt

[Implementieren von CComObjectRootEx](../atl/implementing-ccomobjectrootex.md)<br/>
Beispiel-COM-Zuordnungseinträge `CComObjectRootEx`zum Implementieren von anzeigen.

[Implementieren von CComObject, CComAggObject und CComPolyObject](../atl/implementing-ccomobject-ccomaggobject-and-ccompolyobject.md)<br/>
Erläutert, wie sich die **DECLARE_\*_AGGREGATABLE** `CComAggObject`Makros `CComPolyObject`auf die Verwendung von `CComObject`auswirken, und .

[Unterstützen von IDispatch und IErrorInfo](../atl/supporting-idispatch-and-ierrorinfo.md)<br/>
Listet die ATL-Implementierungsklassen `IDispatch` auf, die zum Unterstützen der und `IErrorInfo` Schnittstellen verwendet werden sollen.

[Unterstützen von IDispEventImpl](../atl/supporting-idispeventimpl.md)<br/>
Erläutert die Schritte zum Implementieren eines Verbindungspunkts für Ihre Klasse.

[Ändern der Standardklassenfactory und des Aggregationsmodells](../atl/changing-the-default-class-factory-and-aggregation-model.md)<br/>
Zeigen Sie an, welche Makros zum Ändern der Standardklassenfactory und des Aggregationsmodells verwendet werden sollen.

[Erstellen eines aggregierten Objekts](../atl/creating-an-aggregated-object.md)<br/>
Listet die Schritte zum Erstellen eines aggregierten Objekts auf.

## <a name="related-sections"></a>Verwandte Abschnitte

[Erstellen eines ATL-Projekts](../atl/reference/creating-an-atl-project.md)<br/>
Enthält Informationen zum Erstellen eines ATL COM-Objekts.

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Enthält Links zu konzeptionellen Themen über die Programmierung mit der Active Template Library.

## <a name="see-also"></a>Siehe auch

[Konzepte](../atl/active-template-library-atl-concepts.md)
