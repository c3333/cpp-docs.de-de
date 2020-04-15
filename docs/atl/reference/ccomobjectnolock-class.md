---
title: CComObjectNoLock-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::CComObjectNoLock
- ATLCOM/ATL::CComObjectNoLock::AddRef
- ATLCOM/ATL::CComObjectNoLock::QueryInterface
- ATLCOM/ATL::CComObjectNoLock::Release
helpviewer_keywords:
- CComObjectNoLock class
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
ms.openlocfilehash: c190f495e284e98b27a6c6dc2099a8dfc4b1693d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327618"
---
# <a name="ccomobjectnolock-class"></a>CComObjectNoLock-Klasse

Diese Klasse `IUnknown` implementiert für ein nicht aggregiertes Objekt, erhöht jedoch nicht die Modulsperranzahl im Konstruktor.

## <a name="syntax"></a>Syntax

```
template<class Base>
class CComObjectNoLock : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von jeder anderen Schnittstelle, die Sie für das Objekt unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CcomObjectnoLock::CComObjectNoLock](#ccomobjectnolock)|Konstruktor.|
|[CcomObjectnoLock::'CcomObjectnoLock](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObjectNoLock::AddRef](#addref)|Inkrementiert die Referenzanzahl für das Objekt.|
|[CComObjectNoLock::QueryInterface](#queryinterface)|Gibt einen Zeiger auf die angeforderte Schnittstelle zurück.|
|[CComObjectNoLock::Release](#release)|Dekrementiert die Referenzanzahl auf das Objekt.|

## <a name="remarks"></a>Bemerkungen

`CComObjectNoLock`ist [cComObject](../../atl/reference/ccomobject-class.md) ähnlich, da [Es IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) für ein nicht aggregiertes Objekt implementiert. `CComObjectNoLock` erhöht jedoch nicht die Modulsperranzahl im Konstruktor.

ATL `CComObjectNoLock` wird intern für Klassenfabriken verwendet. Im Allgemeinen verwenden Sie diese Klasse nicht direkt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComObjectNoLock`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomobjectnolockaddref"></a><a name="addref"></a>CComObjectNoLock::AddRef

Inkrementiert die Referenzanzahl für das Objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen oder Tests nützlich sein kann.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="ccomobjectnolock"></a>CcomObjectnoLock::CComObjectNoLock

Der Konstruktor. Im Gegensatz zu [CComObject](../../atl/reference/ccomobject-class.md)erhöht die Modulsperranzahl nicht.

```
CComObjectNoLock(void* = NULL);
```

### <a name="parameters"></a>Parameter

<em>void\*</em><br/>
[in] Dieser unbenannte Parameter wird nicht verwendet. Sie ist für die `CComXXXObjectXXX` Symmetrie mit anderen Konstruktoren vorhanden.

## <a name="ccomobjectnolockccomobjectnolock"></a><a name="dtor"></a>CcomObjectnoLock::'CcomObjectnoLock

Der Destruktor.

```
~CComObjectNoLock();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei und ruft [FinalRelease](ccomobjectrootex-class.md#finalrelease)auf.

## <a name="ccomobjectnolockqueryinterface"></a><a name="queryinterface"></a>CComObjectNoLock::QueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Der Bezeichner der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *iid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObject* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomobjectnolockrelease"></a><a name="release"></a>CComObjectNoLock::Release

Dekrementiert die Referenzanzahl auf das Objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Gibt in `Release` Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann. Gibt in Nicht-Debug-Builds `Release` immer 0 zurück.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
