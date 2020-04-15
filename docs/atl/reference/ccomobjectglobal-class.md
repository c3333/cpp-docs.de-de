---
title: CComObjectGlobal-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::CComObjectGlobal
- ATLCOM/ATL::CComObjectGlobal::AddRef
- ATLCOM/ATL::CComObjectGlobal::QueryInterface
- ATLCOM/ATL::CComObjectGlobal::Release
- ATLCOM/ATL::CComObjectGlobal::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectGlobal class
ms.assetid: 79bdee55-66e4-4536-b5b3-bdf09f78b9a6
ms.openlocfilehash: 9a784584179186cdf1e63c1ec43cad4d59391ec3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327626"
---
# <a name="ccomobjectglobal-class"></a>CComObjectGlobal-Klasse

Diese Klasse verwaltet eine Verweisanzahl `Base` für das Modul, das Ihr Objekt enthält.

## <a name="syntax"></a>Syntax

```
template<class Base>
class CComObjectGlobal : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von jeder anderen Schnittstelle, die Sie für das Objekt unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectGlobal::CComObjectGlobal](#ccomobjectglobal)|Der Konstruktor.|
|[CComObjectGlobal::'CComObjectGlobal](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectGlobal::AddRef](#addref)|Implementiert eine `AddRef`globale .|
|[CComObjectGlobal::QueryInterface](#queryinterface)|Implementiert eine `QueryInterface`globale .|
|[CComObjectGlobal::Release](#release)|Implementiert eine `Release`globale .|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectGlobal::m_hResFinalConstruct](#m_hresfinalconstruct)|Enthält das HRESULT, das `CComObjectGlobal` während der Konstruktion des Objekts zurückgegeben wurde.|

## <a name="remarks"></a>Bemerkungen

`CComObjectGlobal`verwaltet eine Referenzanzahl für `Base` das Modul, das Ihr Objekt enthält. `CComObjectGlobal`stellt sicher, dass Ihr Objekt nicht gelöscht wird, solange das Modul nicht freigegeben wird. Ihr Objekt wird nur entfernt, wenn die Referenzanzahl für das gesamte Modul auf Null geht.

Beispielsweise kann `CComObjectGlobal`eine Klassenfactory mithilfe von , eine Klassenfactory ein gemeinsames globales Objekt enthalten, das von allen Clients gemeinsam genutzt wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComObjectGlobal`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomobjectglobaladdref"></a><a name="addref"></a>CComObjectGlobal::AddRef

Erhöht die Referenzanzahl des Objekts um 1.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen und Tests nützlich sein kann.

### <a name="remarks"></a>Bemerkungen

Standardmäßig `AddRef` ruft `_Module::Lock`, `_Module` ruft , wobei die globale Instanz von [CComModule](../../atl/reference/ccommodule-class.md) oder eine von ihr abgeleitete Klasse ist.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="ccomobjectglobal"></a>CComObjectGlobal::CComObjectGlobal

Der Konstruktor. Ruft `FinalConstruct` an und legt `HRESULT` dann `FinalConstruct` [m_hResFinalConstruct](#m_hresfinalconstruct) an die zurückgegebene von fest.

```
CComObjectGlobal(void* = NULL));
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie Ihre Basisklasse nicht von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)abgeleitet `FinalConstruct` haben, müssen Sie eine eigene Methode angeben. Der Destruktor ruft `FinalRelease` auf.

## <a name="ccomobjectglobalccomobjectglobal"></a><a name="dtor"></a>CComObjectGlobal::'CComObjectGlobal

Der Destruktor.

```
CComObjectGlobal();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei und ruft [FinalRelease](ccomobjectrootex-class.md#finalrelease)auf.

## <a name="ccomobjectglobalm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectGlobal::m_hResFinalConstruct

Enthält das HRESULT `FinalConstruct` aus aufrufen `CComObjectGlobal` während der Konstruktion des Objekts.

```
HRESULT m_hResFinalConstruct;
```

## <a name="ccomobjectglobalqueryinterface"></a><a name="queryinterface"></a>CComObjectGlobal::QueryInterface

Ruft einen Zeiger auf den angeforderten Schnittstellenzeiger ab.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die GUID der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von iid identifiziert wird, oder NULL, wenn die Schnittstelle nicht gefunden wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

`QueryInterface`verarbeitet nur Schnittstellen in der COM-Map-Tabelle.

## <a name="ccomobjectglobalrelease"></a><a name="release"></a>CComObjectGlobal::Release

Dekrementiert die Referenzanzahl des Objekts um 1.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt in `Release` Debugbuilds einen Wert zurück, der für Diagnosen und Tests nützlich sein kann. Gibt in Nicht-Debug-Builds `Release` immer 0 zurück.

### <a name="remarks"></a>Bemerkungen

Standardmäßig `Release` ruft `_Module::Unlock`, `_Module` ruft , wobei die globale Instanz von [CComModule](../../atl/reference/ccommodule-class.md) oder eine von ihr abgeleitete Klasse ist.

## <a name="see-also"></a>Siehe auch

[CComObjectStack-Klasse](../../atl/reference/ccomobjectstack-class.md)<br/>
[CComAggObject-Klasse](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject-Klasse](../../atl/reference/ccomobject-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
