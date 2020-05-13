---
title: CComCachedTearOffObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::CComCachedTearOffObject
- ATLCOM/ATL::CComCachedTearOffObject::AddRef
- ATLCOM/ATL::CComCachedTearOffObject::FinalConstruct
- ATLCOM/ATL::CComCachedTearOffObject::FinalRelease
- ATLCOM/ATL::CComCachedTearOffObject::QueryInterface
- ATLCOM/ATL::CComCachedTearOffObject::Release
- ATLCOM/ATL::CComCachedTearOffObject::m_contained
helpviewer_keywords:
- cache, ATL cached tear-off objects
- CComCachedTearOffObject class
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
ms.openlocfilehash: 019b90c932de144d05fbf05f3ca339f4e5d6edd1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748103"
---
# <a name="ccomcachedtearoffobject-class"></a>CComCachedTearOffObject-Klasse

Diese Klasse implementiert [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) für eine Abreißschnittstelle.

## <a name="syntax"></a>Syntax

```
template
<class contained>
class CComCachedTearOffObject : public
    IUnknown,
public CComObjectRootEx<contained
::_ThreadModel::ThreadModelNoCS>
```

#### <a name="parameters"></a>Parameter

*Enthalten*<br/>
Ihre Abreißklasse, abgeleitet `CComTearOffObjectBase` von und den Schnittstellen, die Ihr Abreißobjekt unterstützen soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCachedTearOffObject::CComCachedTearOffObject](#ccomcachedtearoffobject)|Der Konstruktor.|
|[CComCachedTearOffObject::'CComCachedTearOffObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCachedTearOffObject::AddRef](#addref)|Inkrementiert die `CComCachedTearOffObject` Verweisanzahl für ein Objekt.|
|[CComCachedTearOffObject::FinalConstruct](#finalconstruct)|Ruft `m_contained::FinalConstruct` die Methode (die Abreißklasse) auf.|
|[CComCachedTearOffObject::FinalRelease](#finalrelease)|Ruft `m_contained::FinalRelease` die Methode (die Abreißklasse) auf.|
|[CComCachedTearOffObject::QueryInterface](#queryinterface)|Gibt einen Zeiger `IUnknown` auf `CComCachedTearOffObject` die des Objekts oder auf die angeforderte `contained`Schnittstelle in der Abreißklasse (die Klasse ) zurück.|
|[CComCachedTearOffObject::Release](#release)|Dekrementiert die Referenzanzahl für ein `CComCachedTearOffObject` Objekt und zerstört sie, wenn die Referenzanzahl 0 ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComCachedTearOffObject::m_contained](#m_contained)|Ein `CComContainedObject` Objekt, das von Ihrer Abreißklasse (der Klasse `contained`) abgeleitet wurde.|

## <a name="remarks"></a>Bemerkungen

`CComCachedTearOffObject`implementiert [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) für eine Abreißschnittstelle. Diese Klasse unterscheidet `CComTearOffObject` sich `CComCachedTearOffObject` von `IUnknown`der eigenen , getrennt `IUnknown` vom Owner-Objekt (der Besitzer ist das Objekt, für das der Abriss erstellt wird). `CComCachedTearOffObject`behält seine eigene Referenzanzahl auf seiner `IUnknown` und löscht sich selbst, sobald seine Referenzanzahl Null ist. Wenn Sie jedoch eine der Abreißschnittstellen abfragen, wird die Referenzanzahl `IUnknown` der des Besitzerobjekts erhöht.

Wenn `CComCachedTearOffObject` das Objekt, das das Abreißvorgang implementiert, bereits instanziiert ist und die `CComCachedTearOffObject` Abreißschnittstelle erneut abgefragt wird, wird dasselbe Objekt wiederverwendet. Wenn dagegen eine von einem `CComTearOffObject` implementierte Abreißschnittstelle erneut über das `CComTearOffObject` Besitzerobjekt abgefragt wird, wird eine andere instanziiert.

Die Owner-Klasse `FinalRelease` muss `Release` die `IUnknown` zwischengespeicherte `CComCachedTearOffObject`für die implementieren und aufrufen, die ihre Verweisanzahl dekrementiert. Dies `CComCachedTearOffObject`führt `FinalRelease` dazu, dass aufgerufen wird und der Abriss gelöscht wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IUnknown`

`CComCachedTearOffObject`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlcom.h

## <a name="ccomcachedtearoffobjectaddref"></a><a name="addref"></a>CComCachedTearOffObject::AddRef

Erhöht die Referenzanzahl `CComCachedTearOffObject` des Objekts um 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen und Tests nützlich sein kann.

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="ccomcachedtearoffobject"></a>CComCachedTearOffObject::CComCachedTearOffObject

Der Konstruktor.

```
CComCachedTearOffObject(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
[in] Zeiger auf `IUnknown` die `CComCachedTearOffObject`der .

### <a name="remarks"></a>Bemerkungen

Initialisiert das `CComContainedObject` [Member, m_contained](#m_contained).

## <a name="ccomcachedtearoffobjectccomcachedtearoffobject"></a><a name="dtor"></a>CComCachedTearOffObject::'CComCachedTearOffObject

Der Destruktor.

```
~CComCachedTearOffObject();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei und ruft [FinalRelease](#finalrelease)auf.

## <a name="ccomcachedtearoffobjectfinalconstruct"></a><a name="finalconstruct"></a>CComCachedTearOffObject::FinalConstruct

Aufrufe `m_contained::FinalConstruct` zum `m_contained`Erstellen `CComContainedObject` <  `contained` von , das> Objekt, das für den Zugriff auf die von Ihrer Abreißklasse implementierte Schnittstelle verwendet wird.

```
HRESULT FinalConstruct();
```

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomcachedtearoffobjectfinalrelease"></a><a name="finalrelease"></a>CComCachedTearOffObject::FinalRelease

Ruft `m_contained::FinalRelease` die `m_contained`Freigabe `CComContainedObject` <  `contained` von , das> Objekt auf.

```cpp
void FinalRelease();
```

## <a name="ccomcachedtearoffobjectm_contained"></a><a name="m_contained"></a>CComCachedTearOffObject::m_contained

Ein [CComContainedObject-Objekt,](../../atl/reference/ccomcontainedobject-class.md) das von Ihrer Abreißklasse abgeleitet wurde.

```
CcomContainedObject <contained> m_contained;
```

### <a name="parameters"></a>Parameter

*Enthalten*<br/>
[in] Ihre Abreißklasse, abgeleitet `CComTearOffObjectBase` von und den Schnittstellen, die Ihr Abreißobjekt unterstützen soll.

### <a name="remarks"></a>Bemerkungen

Die `m_contained` Erben werden verwendet, um über die abzugehörigen Objekte `QueryInterface`, `FinalConstruct`und `FinalRelease`auf die Abreißschnittstelle in ihrer Abreißklasse zuzugreifen.

## <a name="ccomcachedtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComCachedTearOffObject::QueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *iid*oder NULL identifiziert wird, wenn die Schnittstelle nicht gefunden wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Wenn die angeforderte Schnittstelle ist `IUnknown`, `CComCachedTearOffObject`gibt `IUnknown` einen Zeiger auf die eigene zurück und erhöht die Referenzanzahl. Andernfalls werden Abfragen für die Schnittstelle in Ihrer Abreißklasse mithilfe `CComObjectRootEx`der [InternalQueryInterface-Methode,](ccomobjectrootex-class.md#internalqueryinterface) die von geerbt wurde, abgefragt.

## <a name="ccomcachedtearoffobjectrelease"></a><a name="release"></a>CComCachedTearOffObject::Release

Dekrementiert die Referenzanzahl um 1 und löscht das `CComCachedTearOffObject` Objekt, wenn die Referenzanzahl 0 ist.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt in Nicht-Debug-Builds immer 0 zurück. Gibt in Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann.

## <a name="see-also"></a>Weitere Informationen

[CComTearOffObject-Klasse](../../atl/reference/ccomtearoffobject-class.md)<br/>
[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
