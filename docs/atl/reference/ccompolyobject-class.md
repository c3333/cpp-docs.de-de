---
title: CComPolyObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComPolyObject
- ATLCOM/ATL::CComPolyObject
- ATLCOM/ATL::CComPolyObject::CComPolyObject
- ATLCOM/ATL::CComPolyObject::AddRef
- ATLCOM/ATL::CComPolyObject::CreateInstance
- ATLCOM/ATL::CComPolyObject::FinalConstruct
- ATLCOM/ATL::CComPolyObject::FinalRelease
- ATLCOM/ATL::CComPolyObject::QueryInterface
- ATLCOM/ATL::CComPolyObject::Release
- ATLCOM/ATL::CComPolyObject::m_contained
helpviewer_keywords:
- aggregate objects [C++], in ATL
- aggregation [C++], ATL objects
- CComPolyObject class
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
ms.openlocfilehash: c880d170a03196d0e15ea8741c786e560d90ddc4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747769"
---
# <a name="ccompolyobject-class"></a>CComPolyObject-Klasse

Diese Klasse `IUnknown` implementiert für ein aggregiertes oder nicht aggregiertes Objekt.

## <a name="syntax"></a>Syntax

```
template<class contained>
class CComPolyObject : public IUnknown,
      public CComObjectRootEx<contained::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parameter

*Enthalten*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von allen anderen Schnittstellen, die Sie für das Objekt unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPolyObject::CComPolyObject](#ccompolyobject)|Der Konstruktor.|
|[CComPolyObject::-CComPolyObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPolyObject::AddRef](#addref)|Inkrementiert die Referenzanzahl des Objekts.|
|[CComPolyObject::CreateInstance](#createinstance)|(Statisch) Ermöglicht das Erstellen eines neuen **CComPolyObject-<-Objekts** `contained` **>** ohne den Overhead von [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).|
|[CComPolyObject::FinalConstruct](#finalconstruct)|Führt die endgültige `m_contained`Initialisierung von durch.|
|[CComPolyObject::FinalRelease](#finalrelease)|Führt die `m_contained`endgültige Zerstörung von durch.|
|[CComPolyObject::QueryInterface](#queryinterface)|Ruft einen Zeiger auf die angeforderte Schnittstelle ab.|
|[CComPolyObject::Release](#release)|Dekrementiert die Referenzanzahl des Objekts.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComPolyObject::m_contained](#m_contained)|Delegiert `IUnknown` Aufrufe an das äußere Unbekannte, `IUnknown` wenn das Objekt aggregiert ist, oder an das Objekt, wenn das Objekt nicht aggregiert ist.|

## <a name="remarks"></a>Bemerkungen

`CComPolyObject`implementiert [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) für ein aggregiertes oder nicht aggregiertes Objekt.

Wenn eine `CComPolyObject` Instanz von erstellt wird, wird der Wert des äußeren Unbekannten überprüft. Wenn es NULL `IUnknown` ist, wird für ein nicht aggregiertes Objekt implementiert. Wenn der äußere Unbekannte `IUnknown` nicht NULL ist, wird für ein aggregiertes Objekt implementiert.

Der Vorteil `CComPolyObject` der Verwendung besteht darin, dass Sie vermeiden, dass sowohl [CComAggObject](../../atl/reference/ccomaggobject-class.md) als auch [CComObject](../../atl/reference/ccomobject-class.md) in Ihrem Modul verwendet werden, um die aggregierten und nicht aggregierten Anfragen zu behandeln. Ein `CComPolyObject` einzelnes Objekt behandelt beide Fälle. Dies bedeutet, dass nur eine Kopie des vtable und eine Kopie der Funktionen in Ihrem Modul vorhanden sind. Wenn Ihr vtable groß ist, kann dies die Modulgröße erheblich verringern. Wenn Ihr vtable jedoch klein `CComPolyObject` ist, kann die Verwendung zu einer etwas größeren Modulgröße führen, da `CComAggObject` `CComObject`sie nicht für ein aggregiertes oder nicht aggregiertes Objekt optimiert ist, wie es sich in und befindet.

Wenn das DECLARE_POLY_AGGREGATABLE Makro in der Klassendefinition `CComPolyObject` Des Objekts angegeben ist, wird das Objekt erstellt. DECLARE_POLY_AGGREGATABLE werden automatisch deklariert, wenn Sie den ATL-Projekt-Assistenten verwenden, um ein vollständiges Steuerelement oder Internet Explorer-Steuerelement zu erstellen.

Wenn aggregiert, `CComPolyObject` verfügt das `IUnknown`Objekt über eine eigene `IUnknown`, getrennt vom äußeren Objekt und behält seine eigene Verweisanzahl bei. `CComPolyObject`verwendet [CComContainedObject,](../../atl/reference/ccomcontainedobject-class.md) um an das äußere Unbekannte zu delegieren.

Weitere Informationen zur Aggregation finden Sie im Artikel [Grundlagen von ATL COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComPolyObject`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcom.h

## <a name="ccompolyobjectaddref"></a><a name="addref"></a>CComPolyObject::AddRef

Inkrementiert die Referenzanzahl für das Objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

## <a name="ccompolyobjectccompolyobject"></a><a name="ccompolyobject"></a>CComPolyObject::CComPolyObject

Der Konstruktor.

```
CComPolyObject(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
[in] Ein Zeiger auf das äußere Unbekannte, wenn das Objekt aggregiert werden soll, oder NULL, wenn das Objekt nicht aggregiert wird.

### <a name="remarks"></a>Bemerkungen

Initialisiert das `CComContainedObject` Datenelement, [m_contained](#m_contained)und erhöht die Modulsperranzahl.

Der Destruktor dekrementiert die Modulsperranzahl.

## <a name="ccompolyobjectccompolyobject"></a><a name="dtor"></a>CComPolyObject::-CComPolyObject

Der Destruktor.

```
~CComPolyObject();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei, ruft [FinalRelease](#finalrelease)auf und dekrementiert die Modulsperranzahl.

## <a name="ccompolyobjectcreateinstance"></a><a name="createinstance"></a>CComPolyObject::CreateInstance

Ermöglicht das Erstellen eines neuen **CComPolyObject-<-Objekts** `contained` **>** ohne den Overhead von [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

```
static HRESULT WINAPI CreateInstance(
    LPUNKNOWN pUnkOuter,
    CComPolyObject<contained>** pp);
```

### <a name="parameters"></a>Parameter

*Pp*<br/>
[out] Ein Zeiger auf einen **CComPolyObject-<** `contained` **>** Zeiger. Wenn `CreateInstance` kein *Erfolg* besteht, wird pp auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das zurückgegebene Objekt hat eine Referenzanzahl von Null, also rufen Sie sofort an, `AddRef` und verwenden `Release` Sie dann, um den Verweis auf dem Objektzeiger freizugeben, wenn Sie fertig sind.

Wenn Sie keinen direkten Zugriff auf das Objekt benötigen, aber dennoch ein `CoCreateInstance`neues Objekt ohne den Overhead von erstellen möchten, verwenden Sie stattdessen [CComCoClass::CreateInstance.](../../atl/reference/ccomcoclass-class.md#createinstance)

## <a name="ccompolyobjectfinalconstruct"></a><a name="finalconstruct"></a>CComPolyObject::FinalConstruct

Diese Methode wird in den letzten Phasen der Objekterstellung aufgerufen und führt eine endgültige Initialisierung für das [m_contained](#m_contained) Data-Member durch.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccompolyobjectfinalrelease"></a><a name="finalrelease"></a>CComPolyObject::FinalRelease

Diese Methode wird während der Objektzerstörung aufgerufen und gibt den [m_contained](#m_contained) Datenmember frei.

```cpp
void FinalRelease();
```

## <a name="ccompolyobjectm_contained"></a><a name="m_contained"></a>CComPolyObject::m_contained

Ein [CComContainedObject-Objekt,](../../atl/reference/ccomcontainedobject-class.md) das von Ihrer Klasse abgeleitet wurde.

```
CComContainedObject<contained> m_contained;
```

### <a name="parameters"></a>Parameter

*Enthalten*<br/>
[in] Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von allen anderen Schnittstellen, die Sie für das Objekt unterstützen möchten.

### <a name="remarks"></a>Bemerkungen

`IUnknown`Aufrufe `m_contained` durch werden an das äußere Unbekannte delegiert, `IUnknown` wenn das Objekt aggregiert ist, oder an das objekt, wenn das Objekt nicht aggregiert wird.

## <a name="ccompolyobjectqueryinterface"></a><a name="queryinterface"></a>CComPolyObject::QueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
template <class Q>
HRESULT QueryInterface(Q** pp);
```

### <a name="parameters"></a>Parameter

*Q*<br/>
Die COM-Schnittstelle.

*Iid*<br/>
[in] Der Bezeichner der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *iid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObject* auf NULL gesetzt.

*Pp*<br/>
[out] Ein Zeiger auf die `__uuidof(Q)`Schnittstelle, die durch identifiziert wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wenn die angeforderte Schnittstelle für `IUnknown`ein `QueryInterface` aggregiertes Objekt ist, wird ein `IUnknown` Zeiger auf die eigene Desatonur des aggregierten Objekts zurückgegeben und die Verweisanzahl erhöht. Andernfalls fragt diese Methode für `CComContainedObject` die Schnittstelle über das Datenmember [m_contained ab.](#m_contained)

## <a name="ccompolyobjectrelease"></a><a name="release"></a>CComPolyObject::Release

Dekrementiert die Referenzanzahl auf das Objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt in `Release` Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann. Gibt in Nichtdebug-Builds `Release` immer 0 zurück.

## <a name="see-also"></a>Weitere Informationen

[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[DECLARE_POLY_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_poly_aggregatable)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
