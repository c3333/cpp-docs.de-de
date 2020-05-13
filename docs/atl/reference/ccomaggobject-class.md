---
title: CComAggObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComAggObject
- ATLCOM/ATL::CComAggObject
- ATLCOM/ATL::CComAggObject::CComAggObject
- ATLCOM/ATL::CComAggObject::AddRef
- ATLCOM/ATL::CComAggObject::CreateInstance
- ATLCOM/ATL::CComAggObject::FinalConstruct
- ATLCOM/ATL::CComAggObject::FinalRelease
- ATLCOM/ATL::CComAggObject::QueryInterface
- ATLCOM/ATL::CComAggObject::Release
- ATLCOM/ATL::CComAggObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComAggObject class
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
ms.openlocfilehash: b9200c9c396fc16b6df3f4c2f4c66fb7976316d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748164"
---
# <a name="ccomaggobject-class"></a>CComAggObject-Klasse

Diese Klasse implementiert die [IUnknown-Schnittstelle](/windows/win32/api/unknwn/nn-unknwn-iunknown) für ein aggregiertes Objekt. Definitionsgemäß ist ein aggregiertes Objekt in einem äußeren Objekt enthalten. Die `CComAggObject` Klasse ähnelt der [CComObject-Klasse](../../atl/reference/ccomobject-class.md), mit der Ausnahme, dass sie eine Schnittstelle verfügbar macht, auf die externe Clients direkt zugreifen können.

## <a name="syntax"></a>Syntax

```
template<class contained>
class CComAggObject : public IUnknown,
   public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parameter

*Enthalten*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von allen anderen Schnittstellen, die Sie für das Objekt unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComAggObject::CComAggObject](#ccomaggobject)|Der Konstruktor.|
|[CComAggObject::'CComAggObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComAggObject::AddRef](#addref)|Inkrementiert die Referenzanzahl für das aggregierte Objekt.|
|[CComAggObject::CreateInstance](#createinstance)|Mit dieser statischen Funktion können Sie ein neues **CComAggObject-<-Objekt** `contained` **>** ohne den Overhead von [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)erstellen.|
|[CComAggObject::FinalConstruct](#finalconstruct)|Führt die endgültige `m_contained`Initialisierung von durch.|
|[CComAggObject::FinalRelease](#finalrelease)|Führt die `m_contained`endgültige Zerstörung von durch.|
|[CComAggObject::QueryInterface](#queryinterface)|Ruft einen Zeiger auf die angeforderte Schnittstelle ab.|
|[CComAggObject::Release](#release)|Dekrementiert die Referenzanzahl auf das aggregierte Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComAggObject::m_contained](#m_contained)|Delegierte `IUnknown` ruft den äußeren Unbekannten auf.|

## <a name="remarks"></a>Bemerkungen

`CComAggObject`implementiert [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) für ein aggregiertes Objekt. `CComAggObject`hat eine `IUnknown` eigene Schnittstelle, die von `IUnknown` der Schnittstelle des äußeren Objekts getrennt ist, und behält seine eigene Referenzanzahl bei.

Weitere Informationen zur Aggregation finden Sie im Artikel [Grundlagen von ATL COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComAggObject`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcom.h

## <a name="ccomaggobjectaddref"></a><a name="addref"></a>CComAggObject::AddRef

Inkrementiert die Referenzanzahl für das aggregierte Objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

## <a name="ccomaggobjectccomaggobject"></a><a name="ccomaggobject"></a>CComAggObject::CComAggObject

Der Konstruktor.

```
CComAggObject(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
[in] Das äußere Unbekannte.

### <a name="remarks"></a>Bemerkungen

Initialisiert das `CComContainedObject` Member, [m_contained](#m_contained)und erhöht die Modulsperranzahl.

Der Destruktor dekrementiert die Modulsperranzahl.

## <a name="ccomaggobjectccomaggobject"></a><a name="dtor"></a>CComAggObject::'CComAggObject

Der Destruktor.

```
~CComAggObject();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei, ruft [FinalRelease](#finalrelease)auf und dekrementiert die Modulsperranzahl.

## <a name="ccomaggobjectcreateinstance"></a><a name="createinstance"></a>CComAggObject::CreateInstance

Mit dieser statischen Funktion können Sie ein neues **CComAggObject-<-Objekt** `contained` **>** ohne den Overhead von [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)erstellen.

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComAggObject<contained>** pp);
```

### <a name="parameters"></a>Parameter

*Pp*<br/>
[out] Ein Zeiger auf ein **\<CComAggObject**<em>enthielt</em> **>** zeiger. Wenn `CreateInstance` kein *Erfolg* besteht, wird pp auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das zurückgegebene Objekt hat eine Referenzanzahl von Null, also rufen Sie sofort an, `AddRef` und verwenden `Release` Sie dann, um den Verweis auf dem Objektzeiger freizugeben, wenn Sie fertig sind.

Wenn Sie keinen direkten Zugriff auf das Objekt benötigen, aber dennoch `CoCreateInstance`ein neues Objekt ohne den Overhead von erstellen möchten, verwenden Sie stattdessen [CComCoClass::CreateInstance.](../../atl/reference/ccomcoclass-class.md#createinstance)

## <a name="ccomaggobjectfinalconstruct"></a><a name="finalconstruct"></a>CComAggObject::FinalConstruct

Diese Methode wird in den letzten Phasen der Objektkonstruktion aufgerufen und führt eine endgültige Initialisierung für das [m_contained-Member](#m_contained) durch.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomaggobjectfinalrelease"></a><a name="finalrelease"></a>CComAggObject::FinalRelease

Diese Methode wird während der Objektzerstörung aufgerufen und gibt den [m_contained-Member](#m_contained) frei.

```cpp
void FinalRelease();
```

## <a name="ccomaggobjectm_contained"></a><a name="m_contained"></a>CComAggObject::m_contained

Ein [CComContainedObject-Objekt,](../../atl/reference/ccomcontainedobject-class.md) das von Ihrer Klasse abgeleitet wurde.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parameter

*Enthalten*<br/>
[in] Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von allen anderen Schnittstellen, die Sie für das Objekt unterstützen möchten.

### <a name="remarks"></a>Bemerkungen

Alle `IUnknown` durchgehenden Anrufe `m_contained` werden an das äußere Unbekannte delegiert.

## <a name="ccomaggobjectqueryinterface"></a><a name="queryinterface"></a>CComAggObject::QueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

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

### <a name="remarks"></a>Bemerkungen

Wenn die angeforderte Schnittstelle ist `IUnknown`, `QueryInterface` gibt einen Zeiger `IUnknown` auf die eigene des aggregierten Objekts zurück und erhöht die Referenzanzahl. Andernfalls fragt diese Methode für `CComContainedObject` die Schnittstelle über den Member [m_contained](#m_contained)ab.

## <a name="ccomaggobjectrelease"></a><a name="release"></a>CComAggObject::Release

Dekrementiert die Referenzanzahl auf das aggregierte Objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt in `Release` Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann. Gibt in Nicht-Debug-Builds `Release` immer 0 zurück.

## <a name="see-also"></a>Weitere Informationen

[CComObject-Klasse](../../atl/reference/ccomobject-class.md)<br/>
[CComPolyObject-Klasse](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_ONLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_only_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
