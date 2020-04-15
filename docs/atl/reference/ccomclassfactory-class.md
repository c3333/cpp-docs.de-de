---
title: CComClassFactory-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory
- ATLCOM/ATL::CComClassFactory
- ATLCOM/ATL::CComClassFactory::CreateInstance
- ATLCOM/ATL::CComClassFactory::LockServer
helpviewer_keywords:
- CComClassFactory class
ms.assetid: e56dacf7-d5c4-4c42-aef4-a86d91981a1b
ms.openlocfilehash: 041575339906b83488697f1db5a7f8b08b53070e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321023"
---
# <a name="ccomclassfactory-class"></a>CComClassFactory-Klasse

Diese Klasse implementiert die [IClassFactory-Schnittstelle.](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)

## <a name="syntax"></a>Syntax

```
class CComClassFactory
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComClassFactory::CreateInstance](#createinstance)|Erstellt ein Objekt der angegebenen CLSID.|
|[CComClassFactory::LockServer](#lockserver)|Sperrt die Klassenfactory im Speicher.|

## <a name="remarks"></a>Bemerkungen

`CComClassFactory`implementiert die [IClassFactory-Schnittstelle,](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) die Methoden zum Erstellen eines Objekts einer bestimmten CLSID sowie zum Sperren der Klassenfactory im Arbeitsspeicher enthält, damit neue Objekte schneller erstellt werden können. `IClassFactory`muss für jede Klasse implementiert werden, die Sie in der Systemregistrierung registrieren und der Sie eine CLSID zuweisen.

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory)das Makro `CComClassFactory` DECLARE_CLASSFACTORY , das als Standardklassenfactory deklariert wird. Um diese Standardeinstellung zu überschreiben, geben Sie eines der `DECLARE_CLASSFACTORY` *XXX-Makros* in Ihrer Klassendefinition an. Das [DECLARE_CLASSFACTORY_EX-Makro](aggregation-and-class-factory-macros.md#declare_classfactory_ex) verwendet z. B. die angegebene Klasse für die Klassenfactory:

[!code-cpp[NVC_ATL_COM#8](../../atl/codesnippet/cpp/ccomclassfactory-class_1.h)]

Die obige Klassendefinition `CMyClassFactory` gibt an, dass sie als Standardklassenfactory des Objekts verwendet wird. `CMyClassFactory`muss von `CComClassFactory` ableiten `CreateInstance`und überschreiben .

ATL stellt drei weitere Makros bereit, die eine Klassenfactory deklarieren:

- [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Verwendet [CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md), das die Erstellung über eine Lizenz steuert.

- [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Verwendet [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md), das Objekte in mehreren Apartments erstellt.

- [DECLARE_CLASSFACTORY_SINGLETON](aggregation-and-class-factory-macros.md#declare_classfactory_singleton) Verwendet [CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md), das ein einzelnes [CComObjectGlobal-Objekt](../../atl/reference/ccomobjectglobal-class.md) erstellt.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomclassfactorycreateinstance"></a><a name="createinstance"></a>CComClassFactory::CreateInstance

Erstellt ein Objekt der angegebenen CLSID und ruft einen Schnittstellenzeiger für dieses Objekt ab.

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

## <a name="ccomclassfactorylockserver"></a><a name="lockserver"></a>CComClassFactory::LockServer

Inkrementiert und dekrementiert `_Module::Lock` die `_Module::Unlock`Modulsperre durch Aufrufen bzw. Dekrementiert die Modulsperre.

```
STDMETHOD(LockServer)(BOOL fLock);
```

### <a name="parameters"></a>Parameter

*Herde*<br/>
[in] Wenn TRUE, wird die Sperranzahl erhöht. Andernfalls wird die Sperranzahl verringert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

`_Module`bezieht sich auf die globale Instanz von [CComModule](../../atl/reference/ccommodule-class.md) oder eine von ihr abgeleitete Klasse.

Durch `LockServer` Aufrufen kann ein Client an einer Klassenfactory festhalten, sodass mehrere Objekte schnell erstellt werden können.

## <a name="see-also"></a>Siehe auch

[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
