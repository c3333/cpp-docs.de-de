---
title: CComClassFactoryAutoThread-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread
- ATLCOM/ATL::CComClassFactoryAutoThread::CreateInstance
- ATLCOM/ATL::CComClassFactoryAutoThread::LockServer
helpviewer_keywords:
- CComClassFactoryAutoThread class
ms.assetid: 22008042-533f-4dd9-bf7e-191ee571f9a1
ms.openlocfilehash: e997d92adfa9df46c82dacbd297db495b037c6e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320907"
---
# <a name="ccomclassfactoryautothread-class"></a>CComClassFactoryAutoThread-Klasse

Diese Klasse implementiert die [IClassFactory-Schnittstelle](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory) und ermöglicht das Erstellen von Objekten in mehreren Apartments.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class CComClassFactoryAutoThread
    : public IClassFactory,
      public CComObjectRootEx<CComGlobalsThreadModel>
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComClassFactoryAutoThread::CreateInstance](#createinstance)|Erstellt ein Objekt der angegebenen CLSID.|
|[CComClassFactoryAutoThread::LockServer](#lockserver)|Sperrt die Klassenfactory im Speicher.|

## <a name="remarks"></a>Bemerkungen

`CComClassFactoryAutoThread`[cComClassFactory](../../atl/reference/ccomclassfactory-class.md)ähnelt, ermöglicht jedoch das Erstellen von Objekten in mehreren Apartments. Um diese Unterstützung nutzen zu können, leiten Sie Ihr EXE-Modul von [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)ab.

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory deklariert. Um `CComClassFactoryAutoThread`sie zu verwenden, geben Sie das [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) Makros in der Klassendefinition des Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#9](../../atl/codesnippet/cpp/ccomclassfactoryautothread-class_1.h)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory`

`CComClassFactoryAutoThread`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomclassfactoryautothreadcreateinstance"></a><a name="createinstance"></a>CComClassFactoryAutoThread::CreateInstance

Erstellt ein Objekt der angegebenen CLSID und ruft einen Schnittstellenzeiger für dieses Objekt ab.

```
STDMETHODIMP CreateInstance(
    LPUNKNOWN pUnkOuter,
    REFIID riid,
    void** ppvObj);
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

### <a name="remarks"></a>Bemerkungen

Wenn Ihr Modul von [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)abstammt, `CreateInstance` wählt zuerst einen Thread aus, um das Objekt in der zugeordneten Wohnung zu erstellen.

## <a name="ccomclassfactoryautothreadlockserver"></a><a name="lockserver"></a>CComClassFactoryAutoThread::LockServer

Inkrementiert und dekrementiert `_Module::Lock` die `_Module::Unlock`Modulsperre durch Aufrufen bzw. Dekrementiert die Modulsperre.

```
STDMETHODIMP LockServer(BOOL fLock);
```

### <a name="parameters"></a>Parameter

*Herde*<br/>
[in] Wenn TRUE, wird die Sperranzahl erhöht. Andernfalls wird die Sperranzahl verringert.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Bei `CComClassFactoryAutoThread`Verwendung `_Module` von , bezieht sich in der Regel auf die globale Instanz von [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).

Durch `LockServer` Aufrufen kann ein Client an einer Klassenfactory festhalten, sodass mehrere Objekte schnell erstellt werden können.

## <a name="see-also"></a>Siehe auch

[IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)<br/>
[CComClassFactory2-Klasse](../../atl/reference/ccomclassfactory2-class.md)<br/>
[CComClassFactorySingleton-Klasse](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
