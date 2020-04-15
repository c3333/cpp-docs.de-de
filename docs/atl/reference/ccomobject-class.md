---
title: CComObject-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComObject
- ATLCOM/ATL::CComObject
- ATLCOM/ATL::CComObject::CComObject
- ATLCOM/ATL::CComObject::AddRef
- ATLCOM/ATL::CComObject::CreateInstance
- ATLCOM/ATL::CComObject::QueryInterface
- ATLCOM/ATL::CComObject::Release
helpviewer_keywords:
- CComObject class
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
ms.openlocfilehash: de6ffb45fe5c6f73ab656d5c6185b70d9f5edd38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327645"
---
# <a name="ccomobject-class"></a>CComObject-Klasse

Diese Klasse `IUnknown` implementiert für ein nicht aggregiertes Objekt.

## <a name="syntax"></a>Syntax

```
template<class Base>
class CComObject : public Base
```

#### <a name="parameters"></a>Parameter

*Basis*<br/>
Ihre Klasse, abgeleitet von [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) oder [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), sowie von allen anderen Schnittstellen, die Sie für das Objekt unterstützen möchten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObject::CComObject](#ccomobject)|Der Konstruktor.|
|[CComObject::-CComObject](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComObject::AddRef](#addref)|Inkrementiert die Referenzanzahl für das Objekt.|
|[CComObject::CreateInstance](#createinstance)|(Statisch) Erstellt ein `CComObject` neues Objekt.|
|[CComObject::QueryInterface](#queryinterface)|Ruft einen Zeiger auf die angeforderte Schnittstelle ab.|
|[CComObject::Release](#release)|Dekrementiert die Referenzanzahl auf das Objekt.|

## <a name="remarks"></a>Bemerkungen

`CComObject`implementiert [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) für ein nicht aggregiertes Objekt. Ruft jedoch `QueryInterface`an `AddRef`, `Release` auf und `CComObjectRootEx`wird an delegiert.

Weitere Informationen zur `CComObject`Verwendung finden Sie im Artikel [Grundlagen von ATL COM-Objekten](../../atl/fundamentals-of-atl-com-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`Base`

`CComObject`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomobjectaddref"></a><a name="addref"></a>CComObject::AddRef

Inkrementiert die Referenzanzahl für das Objekt.

```
STDMETHOD_(ULONG, AddRef)();
```

### <a name="return-value"></a>Rückgabewert

Diese Funktion gibt die neue inkrementierte Referenzanzahl für das Objekt zurück. Dieser Wert kann für Diagnosen oder Tests nützlich sein.

## <a name="ccomobjectccomobject"></a><a name="ccomobject"></a>CComObject::CComObject

Der Konstruktor erhöht die Modulsperranzahl.

```
CComObject(void* = NULL);
```

### <a name="parameters"></a>Parameter

<em>void\*</em><br/>
[in] Dieser unbenannte Parameter wird nicht verwendet. Sie ist für die `CComXXXObjectXXX` Symmetrie mit anderen Konstruktoren vorhanden.

### <a name="remarks"></a>Bemerkungen

Der Zerstörer deziert ihn.

Wenn `CComObject`ein -derived-Objekt erfolgreich mit dem **neuen** Operator erstellt wurde, ist die anfängliche Referenzanzahl 0. Um die Verweisanzahl auf den richtigen Wert (1) festzulegen, rufen Sie die [AddRef-Funktion](#addref) auf.

## <a name="ccomobjectccomobject"></a><a name="dtor"></a>CComObject::-CComObject

Der Destruktor.

```
CComObject();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugeordneten Ressourcen frei, ruft [FinalRelease](ccomobjectrootex-class.md#finalrelease)auf und dekrementiert die Modulsperranzahl.

## <a name="ccomobjectcreateinstance"></a><a name="createinstance"></a>CComObject::CreateInstance

Mit dieser statischen Funktion können Sie ein neues **CComObject-<-Objekt** `Base` **>** ohne den Overhead von [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)erstellen.

```
static HRESULT WINAPI CreateInstance(CComObject<Base>** pp);
```

### <a name="parameters"></a>Parameter

*Pp*<br/>
[out] Ein Zeiger auf einen **CComObject-<** `Base` **>** Zeiger. Wenn `CreateInstance` kein *Erfolg* besteht, wird pp auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Das zurückgegebene Objekt hat eine Referenzanzahl von Null, also rufen Sie sofort an, `AddRef` und verwenden `Release` Sie dann, um den Verweis auf dem Objektzeiger freizugeben, wenn Sie fertig sind.

Wenn Sie keinen direkten Zugriff auf das Objekt benötigen, aber dennoch `CoCreateInstance`ein neues Objekt ohne den Overhead von erstellen möchten, verwenden Sie stattdessen [CComCoClass::CreateInstance.](../../atl/reference/ccomcoclass-class.md#createinstance)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#38](../../atl/codesnippet/cpp/ccomobject-class_1.h)]

[!code-cpp[NVC_ATL_COM#39](../../atl/codesnippet/cpp/ccomobject-class_2.cpp)]

## <a name="ccomobjectqueryinterface"></a><a name="queryinterface"></a>CComObject::QueryInterface

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

## <a name="ccomobjectrelease"></a><a name="release"></a>CComObject::Release

Dekrementiert die Referenzanzahl auf das Objekt.

```
STDMETHOD_(ULONG, Release)();
```

### <a name="return-value"></a>Rückgabewert

Diese Funktion gibt die neue dekrementierte Verweisanzahl für das Objekt zurück. In Debugbuilds kann der Rückgabewert für Diagnosen oder Tests nützlich sein. Gibt in Nicht-Debug-Builds `Release` immer 0 zurück.

## <a name="see-also"></a>Siehe auch

[CComAggObject-Klasse](../../atl/reference/ccomaggobject-class.md)<br/>
[CComPolyObject-Klasse](../../atl/reference/ccompolyobject-class.md)<br/>
[DECLARE_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_aggregatable)<br/>
[DECLARE_NOT_AGGREGATABLE](aggregation-and-class-factory-macros.md#declare_not_aggregatable)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
