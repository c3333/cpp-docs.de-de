---
title: CComObjectRoot-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComObjectRoot
- atlcom/ATL::CComObjectRoot
helpviewer_keywords:
- CComObjectRoot class
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
ms.openlocfilehash: 98868e67fd14899a75f86837034ba540d22039e3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224239"
---
# <a name="ccomobjectroot-class"></a>CComObjectRoot-Klasse

Diese Typdefinition von [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) ist im Standard Threading Modell des Servers Vorlagen basiert.

## <a name="syntax"></a>Syntax

```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```

## <a name="remarks"></a>Bemerkungen

`CComObjectRoot`ist ein **`typedef`** von [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md) , das auf dem Standard Threading Modell des Servers basiert. Daher verweist [ccomobjectthreadmodel](atl-typedefs.md#ccomobjectthreadmodel) entweder auf [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) oder [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md).

`CComObjectRootEx`behandelt die Verwaltung von Objekt Verweis zählungs Punkten für nicht aggregierte und aggregierte Objekte. Sie enthält den Objekt Verweis Zähler, wenn das Objekt nicht aggregiert wird, und enthält den Zeiger auf das äußere unbekannte, wenn das Objekt aggregiert wird. Bei aggregierten Objekten `CComObjectRootEx` können Methoden verwendet werden, um den Fehler des inneren Objekts zu verarbeiten und das äußere Objekt vor dem Löschen zu schützen, wenn innere Schnittstellen freigegeben oder das innere Objekt gelöscht wird.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

## <a name="see-also"></a>Siehe auch

[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComAggObject-Klasse](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject-Klasse](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject-Klasse](../../atl/reference/ccompolyobject-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
