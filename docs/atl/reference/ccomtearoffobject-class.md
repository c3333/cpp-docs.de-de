---
title: CComTearOffObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComTearOffObject
- ATLCOM/ATL::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::CComTearOffObject
- ATLCOM/ATL::CComTearOffObject::AddRef
- ATLCOM/ATL::CComTearOffObject::QueryInterface
- ATLCOM/ATL::CComTearOffObject::Release
- ATLCOM/ATL::CComTearOffObjectBase
- ATLCOM/ATL::m_pOwner
helpviewer_keywords:
- tear-off interfaces, ATL
- tear-off interfaces
- CComTearOffObject class
ms.assetid: d974b598-c6b2-42b1-8360-9190d9d0fbf3
ms.openlocfilehash: de7528d3972991c233ee4b9037f609b89d0f7434
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327319"
---
# <a name="ccomtearoffobject-class"></a>CComTearOffObject-Klasse

Diese Klasse implementiert eine Abreißschnittstelle.

## <a name="syntax"></a>Syntax

```
template<class Base>
class CComTearOffObject : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ihre Abreißklasse, abgeleitet `CComTearOffObjectBase` von und den Schnittstellen, die Ihr Abreißobjekt unterstützen soll.

ATL implementiert seine Abreißschnittstellen in zwei Phasen `CComTearOffObjectBase` : Die Methoden `QueryInterface`behandeln `CComTearOffObject` die Verweisanzahl und implementieren [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComtearOffObject::CComtearOffObject](#ccomtearoffobject)|Der Konstruktor.|
|[CComtearOffObject::'cComtearOffObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComTearOffObject::AddRef](#addref)|Inkrementiert die `CComTearOffObject` Verweisanzahl für ein Objekt.|
|[CComTearOffObject::QueryInterface](#queryinterface)|Gibt einen Zeiger auf die angeforderte Schnittstelle für Ihre Abreißklasse oder die Besitzerklasse zurück.|
|[CComTearOffObject::Release](#release)|Dekrementiert die Referenzanzahl für ein `CComTearOffObject` Objekt und zerstört es.|

### <a name="ccomtearoffobjectbase-methods"></a>CComTearOffObjectBase-Methoden

|||
|-|-|
|[CComTearOffObjectBase](#ccomtearoffobjectbase)|Konstruktor.|

### <a name="ccomtearoffobjectbase-data-members"></a>CComTearOffObjectBase-Datenmember

|||
|-|-|
|[m_pOwner](#m_powner)|Ein Zeiger auf `CComObject` eine von der Besitzerklasse abgeleitete.|

## <a name="remarks"></a>Bemerkungen

`CComTearOffObject`implementiert eine Abreißschnittstelle als separates Objekt, das nur instanziiert wird, wenn diese Schnittstelle abgefragt wird. Der Abreißer wird gelöscht, wenn die Referenzanzahl Null wird. In der Regel erstellen Sie eine Abreißschnittstelle für eine Schnittstelle, die selten verwendet wird, da die Verwendung eines Abreißers einen vtable-Zeiger in allen Instanzen des Hauptobjekts speichert.

Sie sollten die Klasse ableiten, `CComTearOffObjectBase` die den Abreißer implementiert, und von den Schnittstellen, die Das Abreißobjekt unterstützen soll. `CComTearOffObjectBase`wird für die Besitzerklasse und das Threadmodell templatiert. Die Besitzerklasse ist die Klasse des Objekts, für das ein Abreißer implementiert wird. Wenn Sie kein Gewindemodell angeben, wird das Standardthreadmodell verwendet.

Sie sollten eine COM-Karte für Ihre Abreißklasse erstellen. Wenn ATL den Abriss instanziiert, wird `CComTearOffObject<CYourTearOffClass>` `CComCachedTearOffObject<CYourTearOffClass>`es erstellt oder .

Im BEEPER-Beispiel ist die `CBeeper2` Klasse z. B. `CBeeper` die Tear-off-Klasse und die Klasse die Besitzerklasse:

[!code-cpp[NVC_ATL_COM#43](../../atl/codesnippet/cpp/ccomtearoffobject-class_1.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComTearOffObject`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomtearoffobjectaddref"></a><a name="addref"></a>CComTearOffObject::AddRef

Erhöht die Referenzanzahl `CComTearOffObject` des Objekts um eins.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der für Diagnosen und Tests nützlich sein kann.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="ccomtearoffobject"></a>CComtearOffObject::CComtearOffObject

Der Konstruktor.

```
CComTearOffObject(void* pv);
```

### <a name="parameters"></a>Parameter

*Pv*<br/>
[in] Zeiger, der in einen Zeiger auf `CComObject<Owner>` ein Objekt konvertiert wird.

### <a name="remarks"></a>Bemerkungen

Erhöht die Referenzanzahl des Besitzers um eins.

## <a name="ccomtearoffobjectccomtearoffobject"></a><a name="dtor"></a>CComtearOffObject::'cComtearOffObject

Der Destruktor.

```
~CComTearOffObject();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei, ruft FinalRelease auf und dekrementiert die Modulsperranzahl.

## <a name="ccomtearoffobjectccomtearoffobjectbase"></a><a name="ccomtearoffobjectbase"></a>CComtearOffObject::CComtearOffObjectBase

Der Konstruktor.

```
CComTearOffObjectBase();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das [m_pOwner-Member](#m_powner) auf NULL.

## <a name="ccomtearoffobjectm_powner"></a><a name="m_powner"></a>CComTearOffObject::m_pOwner

Ein Zeiger auf ein [CComObject-Objekt,](../../atl/reference/ccomobject-class.md) das von *Owner*abgeleitet wurde.

```
CComObject<Owner>* m_pOwner;
```

### <a name="parameters"></a>Parameter

*Besitzer*<br/>
[in] Die Klasse, für die ein Abriss implementiert wird.

### <a name="remarks"></a>Bemerkungen

Der Zeiger wird während der Konstruktion auf NULL initialisiert.

## <a name="ccomtearoffobjectqueryinterface"></a><a name="queryinterface"></a>CComTearOffObject::QueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
STDMETHOD(QueryInterface)(REFIID iid, void** ppvObject);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
[in] Die IID der angeforderten Schnittstelle.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *iid*oder NULL identifiziert wird, wenn die Schnittstelle nicht gefunden wird.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Fragt zuerst nach Schnittstellen für Ihre Abreißklasse ab. Wenn die Schnittstelle nicht vorhanden ist, werden Abfragen für die Schnittstelle für das Besitzerobjekt angezeigt. Wenn die angeforderte Schnittstelle ist `IUnknown`, gibt den `IUnknown` Besitzer zurück.

## <a name="ccomtearoffobjectrelease"></a><a name="release"></a>CComTearOffObject::Release

Dekrementiert die Referenzanzahl um eins, und wenn `CComTearOffObject`die Referenzanzahl Null ist, löscht die .

```
STDMETHOD_ULONG Release();
```

### <a name="return-value"></a>Rückgabewert

In Nicht-Debug-Builds wird immer Null zurückgegeben. Gibt in Debugbuilds einen Wert zurück, der für Diagnosen oder Tests nützlich sein kann.

## <a name="see-also"></a>Siehe auch

[CComCachedTearOffObject-Klasse](../../atl/reference/ccomcachedtearoffobject-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
