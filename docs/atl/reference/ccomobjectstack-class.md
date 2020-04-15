---
title: CComObjectStack-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComObjectStack
- ATLCOM/ATL::CComObjectStack
- ATLCOM/ATL::CComObjectStack::CComObjectStack
- ATLCOM/ATL::CComObjectStack::AddRef
- ATLCOM/ATL::CComObjectStack::QueryInterface
- ATLCOM/ATL::CComObjectStack::Release
- ATLCOM/ATL::CComObjectStack::m_hResFinalConstruct
helpviewer_keywords:
- CComObjectStack class
ms.assetid: 3da72c40-c834-45f6-bb76-6ac204028d80
ms.openlocfilehash: 8c3fd56635da8b80c84f6151009586b7bd2b4341
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327571"
---
# <a name="ccomobjectstack-class"></a>CComObjectStack-Klasse

Diese Klasse erstellt ein temporäres COM-Objekt und `IUnknown`stellt ihm eine skelettierte Implementierung von zur Verfügung.

## <a name="syntax"></a>Syntax

```
template <class  Base>
class CComObjectStack : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von jeder anderen Schnittstelle, die Sie für das Objekt unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectStack::CComObjectStack](#ccomobjectstack)|Der Konstruktor.|
|[CComObjectStack::'CComObjectStack](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectStack::AddRef](#addref)|Gibt 0 (null) zurück. Ruft im Debugmodus auf. `_ASSERTE`|
|[CComObjectStack::QueryInterface](#queryinterface)|Gibt E_NOINTERFACE zurück. Ruft im Debugmodus auf. `_ASSERTE`|
|[CComObjectStack::Release](#release)|Gibt 0 (null) zurück. Ruft im Debugmodus auf. `_ASSERTE` ~|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectStack::m_hResFinalConstruct](#m_hresfinalconstruct)|Enthält das HRESULT, das `CComObjectStack` während der Konstruktion des Objekts zurückgegeben wurde.|

## <a name="remarks"></a>Bemerkungen

`CComObjectStack`wird verwendet, um ein temporäres COM-Objekt zu `IUnknown`erstellen und dem Objekt eine skelettierte Implementierung von bereitzustellen. In der Regel wird das Objekt als lokale Variable innerhalb einer Funktion verwendet (d. h. auf den Stapel verschoben). Da das Objekt zerstört wird, wenn die Funktion beendet ist, wird keine Referenzzählung durchgeführt, um die Effizienz zu erhöhen.

Das folgende Beispiel zeigt, wie Sie ein COM-Objekt erstellen, das in einer Funktion verwendet wird:

[!code-cpp[NVC_ATL_COM#42](../../atl/codesnippet/cpp/ccomobjectstack-class_1.cpp)]

Das temporäre `Tempobj` Objekt wird auf den Stapel verschoben und verschwindet automatisch, wenn die Funktion beendet ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComObjectStack`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomobjectstackaddref"></a><a name="addref"></a>CComObjectStack::AddRef

Gibt 0 (null) zurück.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück.

### <a name="remarks"></a>Bemerkungen

Ruft im Debugmodus auf. `_ASSERTE`

## <a name="ccomobjectstackccomobjectstack"></a><a name="ccomobjectstack"></a>CComObjectStack::CComObjectStack

Der Konstruktor.

```
CComObjectStack(void* = NULL);
```

### <a name="remarks"></a>Bemerkungen

Ruft `FinalConstruct` auf und legt dann [m_hResFinalConstruct](#m_hresfinalconstruct) an das Von zurückgegebene `FinalConstruct`HRESULT fest. Wenn Sie Ihre Basisklasse nicht von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)abgeleitet `FinalConstruct` haben, müssen Sie eine eigene Methode angeben. Der Destruktor ruft `FinalRelease` auf.

## <a name="ccomobjectstackccomobjectstack"></a><a name="dtor"></a>CComObjectStack::'CComObjectStack

Der Destruktor.

```
CComObjectStack();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei und ruft [FinalRelease](ccomobjectrootex-class.md#finalrelease)auf.

## <a name="ccomobjectstackm_hresfinalconstruct"></a><a name="m_hresfinalconstruct"></a>CComObjectStack::m_hResFinalConstruct

Enthält das HRESULT, `FinalConstruct` das während `CComObjectStack` der Konstruktion des Objekts vom Aufruf zurückgegeben wurde.

```
HRESULT    m_hResFinalConstruct;
```

## <a name="ccomobjectstackqueryinterface"></a><a name="queryinterface"></a>CComObjectStack::QueryInterface

Gibt E_NOINTERFACE zurück.

```
HRESULT    QueryInterface(REFIID, void**);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOINTERFACE zurück.

### <a name="remarks"></a>Bemerkungen

Ruft im Debugmodus auf. `_ASSERTE`

## <a name="ccomobjectstackrelease"></a><a name="release"></a>CComObjectStack::Release

Gibt 0 (null) zurück.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück.

### <a name="remarks"></a>Bemerkungen

Ruft im Debugmodus auf. `_ASSERTE`

## <a name="see-also"></a>Siehe auch

[CComAggObject-Klasse](../../atl/reference/ccomaggobject-class.md)<br/>
[CComObject-Klasse](../../atl/reference/ccomobject-class.md)<br/>
[CComObjectGlobal-Klasse](../../atl/reference/ccomobjectglobal-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
