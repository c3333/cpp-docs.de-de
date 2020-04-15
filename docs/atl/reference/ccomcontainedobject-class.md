---
title: CComContainedObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComContainedObject
- ATLCOM/ATL::CComContainedObject
- ATLCOM/ATL::CComContainedObject::CComContainedObject
- ATLCOM/ATL::CComContainedObject::AddRef
- ATLCOM/ATL::CComContainedObject::GetControllingUnknown
- ATLCOM/ATL::CComContainedObject::QueryInterface
- ATLCOM/ATL::CComContainedObject::Release
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComContainedObject class
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
ms.openlocfilehash: 72ba27c3be6576621995ffb8c98995c6abc9324c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320795"
---
# <a name="ccomcontainedobject-class"></a>CComContainedObject-Klasse

Diese Klasse implementiert [IUnknown,](/windows/win32/api/unknwn/nn-unknwn-iunknown) indem sie an `IUnknown`das Owner-Objekt delegiert.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class Base>
class CComContainedObject : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComcontainedObject::CComcontainedObject](#ccomcontainedobject)|Der Konstruktor. Initialisiert den Memberzeiger auf die des `IUnknown`Besitzerobjekts .|
|[CComcontainedObject::'cComcontainedObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComContainedObject::AddRef](#addref)|Inkrementiert die Referenzanzahl für das Besitzerobjekt.|
|[CComcontainedObject::GetControllingUnbekannt](#getcontrollingunknown)|Ruft die des Besitzerobjekts `IUnknown`ab.|
|[CComcontainedObject::QueryInterface](#queryinterface)|Ruft einen Zeiger auf die Schnittstelle ab, die für das Besitzerobjekt angefordert wurde.|
|[CComContainedObject::Release](#release)|Dekrementiert die Referenzzahl auf das Besitzerobjekt.|

## <a name="remarks"></a>Bemerkungen

ATL `CComContainedObject` verwendet in den Klassen [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md)und [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md). `CComContainedObject`implementiert [IUnknown,](/windows/win32/api/unknwn/nn-unknwn-iunknown) indem es an das `IUnknown`Owner-Objekt delegiert wird. (Der Besitzer ist entweder das äußere Objekt einer Aggregation oder das Objekt, für das eine Abreißschnittstelle erstellt wird.) `CComContainedObject` ruft `CComObjectRootEx` `OuterQueryInterface`'s `OuterAddRef`, `OuterRelease`, und `Base`, alle über geerbt .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComContainedObject`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomcontainedobjectaddref"></a><a name="addref"></a>CComContainedObject::AddRef

Inkrementiert die Referenzanzahl für das Besitzerobjekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="ccomcontainedobject"></a>CComcontainedObject::CComcontainedObject

Der Konstruktor.

```
CComContainedObject(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
[in] Das Besitzerobjekt `IUnknown`.

### <a name="remarks"></a>Bemerkungen

Legt `m_pOuterUnknown` den Memberzeiger (durch `Base` die Klasse geerbt) auf *pv*fest.

## <a name="ccomcontainedobjectccomcontainedobject"></a><a name="dtor"></a>CComcontainedObject::'cComcontainedObject

Der Destruktor.

```
~CComContainedObject();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="ccomcontainedobjectgetcontrollingunknown"></a><a name="getcontrollingunknown"></a>CComcontainedObject::GetControllingUnbekannt

Gibt `m_pOuterUnknown` den Memberzeiger (vererbt durch die *Basisklasse)* `IUnknown`zurück, der die des Besitzerobjekts enthält.

```
IUnknown* GetControllingUnknown();
```

### <a name="return-value"></a>Rückgabewert

Das Besitzerobjekt `IUnknown`.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann `Base` virtuell sein, wenn das [DECLARE_GET_CONTROLLING_UNKNOWN-Makro](aggregation-and-class-factory-macros.md#declare_get_controlling_unknown) deklariert wurde.

## <a name="ccomcontainedobjectqueryinterface"></a><a name="queryinterface"></a>CComcontainedObject::QueryInterface

Ruft einen Zeiger auf die Schnittstelle ab, die für das Besitzerobjekt angefordert wurde.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT STDMETHODCALLTYPE QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Der Bezeichner der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *iid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObject* auf NULL gesetzt.

*Pp*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, `Q`der nach Typ identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *pp* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomcontainedobjectrelease"></a><a name="release"></a>CComContainedObject::Release

Dekrementiert die Referenzzahl auf das Besitzerobjekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt in `Release` Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann. Gibt in Nicht-Debug-Builds `Release` immer 0 zurück.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
