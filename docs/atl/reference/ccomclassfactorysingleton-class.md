---
title: CComClassFactorySingleton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton
- ATLCOM/ATL::CComClassFactorySingleton::CreateInstance
- ATLCOM/ATL::CComClassFactorySingleton::m_spObj
helpviewer_keywords:
- CComClassFactorySingleton class
ms.assetid: debb983c-382b-487b-8d42-7ea26dc158b8
ms.openlocfilehash: ec860f7ef59b7d3289bf2e18fea0f0e064a7c8f9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320822"
---
# <a name="ccomclassfactorysingleton-class"></a>CComClassFactorySingleton-Klasse

Diese Klasse leitet sich von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ab und verwendet [CComObjectGlobal,](../../atl/reference/ccomobjectglobal-class.md) um ein einzelnes Objekt zu erstellen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class CComClassFactorySingleton : public CComClassFactory
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse.

`CComClassFactorySingleton`von [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) ableitet und [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md) verwendet, um ein einzelnes Objekt zu erstellen. Jeder Aufruf `CreateInstance` der Methode fragt dieses Objekt einfach nach einem Schnittstellenzeiger ab.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComClassFactorySingleton::CreateInstance](#createinstance)|Abfragen `m_spObj` für einen Schnittstellenzeiger.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComClassFactorySingleton::m_spObj](#m_spobj)|Das [CComObjectGlobal-Objekt,](../../atl/reference/ccomobjectglobal-class.md) das von `CComClassFactorySingleton`erstellt wurde.|

## <a name="remarks"></a>Bemerkungen

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)das Makro `CComClassFactory` DECLARE_CLASSFACTORY , das als Standardklassenfactory deklariert wird. Um `CComClassFactorySingleton`sie zu verwenden, geben Sie das [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Makros in der Klassendefinition des Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#10](../../atl/codesnippet/cpp/ccomclassfactorysingleton-class_1.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)

`CComClassFactorySingleton`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomclassfactorysingletoncreateinstance"></a><a name="createinstance"></a>CComClassFactorySingleton::CreateInstance

Ruft `QueryInterface` [über m_spObj](#m_spobj) aufrufen, um einen Schnittstellenzeiger abzurufen.

```
STDMETHOD(CreateInstance)(LPUNKNOWN pUnkOuter, REFIID riid, void** ppvObj);
```

### <a name="parameters"></a>Parameter

*pUnkOuter*<br/>
[in] Wenn das Objekt als Teil eines Aggregats erstellt wird, muss *pUnkOuter* das äußere Unbekannte sein. Andernfalls muss *pUnkOuter* NULL sein.

*riid*<br/>
[in] Die IID der angeforderten Schnittstelle. Wenn *pUnkOuter* nicht NULL ist, `IID_IUnknown`muss *riid* sein.

*ppvObj*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *riid*identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObj* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="ccomclassfactorysingletonm_spobj"></a><a name="m_spobj"></a>CComClassFactorySingleton::m_spObj

Das [CComObjectGlobal-Objekt,](../../atl/reference/ccomobjectglobal-class.md) das von `CComClassFactorySingleton`erstellt wurde.

```
CComPtr<IUnknown> m_spObj;
```

### <a name="remarks"></a>Bemerkungen

Jeder Aufruf der [CreateInstance-Methode](#createinstance) fragt dieses Objekt einfach nach einem Schnittstellenzeiger ab.

Beachten Sie, dass `m_spObj` die aktuelle Form von `CComClassFactorySingleton` stellt eine brechende Änderung gegenüber der Art und Weise, die in früheren Versionen von ATL funktioniert. In früheren `CComClassFactorySingleton` Versionen wurde das Objekt während der Serverinitialisierung gleichzeitig mit der Klassenfactory erstellt. In Visual C++.NET 2003 und höher wird das Objekt bei der ersten Anforderung verzögert erstellt. Diese Änderung kann zu Fehlern in Programmen führen, die auf einer frühen Initialisierung basieren.

## <a name="see-also"></a>Siehe auch

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2-Klasse](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactoryAutoThread-Klasse](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
