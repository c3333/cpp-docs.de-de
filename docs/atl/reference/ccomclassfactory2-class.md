---
title: CComClassFactory2-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComClassFactory2
- ATLCOM/ATL::CComClassFactory2
- ATLCOM/ATL::CComClassFactory2::CreateInstance
- ATLCOM/ATL::CComClassFactory2::CreateInstanceLic
- ATLCOM/ATL::CComClassFactory2::GetLicInfo
- ATLCOM/ATL::CComClassFactory2::LockServer
- ATLCOM/ATL::CComClassFactory2::RequestLicKey
helpviewer_keywords:
- CComClassFactory2 class
ms.assetid: 19b66fd6-b9ed-47a0-822c-8132184f5a3e
ms.openlocfilehash: 0cb2064cfaea6317c4522ff917f3963fca2219b8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321017"
---
# <a name="ccomclassfactory2-class"></a>CComClassFactory2-Klasse

Diese Klasse implementiert die [IClassFactory2-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)

## <a name="syntax"></a>Syntax

```
template <class license>
class CComClassFactory2 : public IClassFactory2,
    public CComObjectRootEx<CComGlobalsThreadModel>,
    public license
```

#### <a name="parameters"></a>Parameter

*Lizenz*<br/>
Eine Klasse, die die folgenden statischen Funktionen implementiert:

- `static BOOL VerifyLicenseKey( BSTR bstr );`

- `static BOOL GetLicenseKey( DWORD dwReserved, BSTR * pBstr );`

- `static BOOL IsLicenseValid( );`

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComClassFactory2::CreateInstance](#createinstance)|Erstellt ein Objekt der angegebenen CLSID.|
|[CComClassFactory2::CreateInstancelic](#createinstancelic)|Erstellt bei einem Lizenzschlüssel ein Objekt der angegebenen CLSID.|
|[CComClassFactory2::GetLicInfo](#getlicinfo)|Ruft Informationen ab, die die Lizenzierungsfunktionen der Klassenfactory beschreiben.|
|[CComClassFactory2::LockServer](#lockserver)|Sperrt die Klassenfactory im Speicher.|
|[CComClassFactory2::RequestLicKey](#requestlickey)|Erstellt und gibt einen Lizenzschlüssel zurück.|

## <a name="remarks"></a>Bemerkungen

`CComClassFactory2`implementiert die [IClassFactory2-Schnittstelle,](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2) die eine Erweiterung von [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)ist. `IClassFactory2`steuert die Objekterstellung über eine Lizenz. Eine Klassenfactory, die auf einem lizenzierten Computer ausgeführt wird, kann einen Laufzeitlizenzschlüssel bereitstellen. Mit diesem Lizenzschlüssel kann eine Anwendung Objekte instanziieren, wenn keine vollständige Computerlizenz vorhanden ist.

ATL-Objekte erwerben normalerweise eine Klassenfactory, indem sie von [CComCoClass](../../atl/reference/ccomcoclass-class.md)ableiten. Diese Klasse enthält das Makro [DECLARE_CLASSFACTORY](aggregation-and-class-factory-macros.md#declare_classfactory), das [CComClassFactory](../../atl/reference/ccomclassfactory-class.md) als Standardklassenfactory deklariert. Um `CComClassFactory2`sie zu verwenden, geben Sie das [DECLARE_CLASSFACTORY2](aggregation-and-class-factory-macros.md#declare_classfactory2) Makros in der Klassendefinition des Objekts an. Beispiel:

[!code-cpp[NVC_ATL_COM#2](../../atl/codesnippet/cpp/ccomclassfactory2-class_1.h)]

`CMyLicense`muss `CComClassFactory2`der Vorlagenparameter für , `VerifyLicenseKey`die `GetLicenseKey`statischen Funktionen , und `IsLicenseValid`implementieren. Im Folgenden finden Sie ein Beispiel für eine einfache Lizenzklasse:

[!code-cpp[NVC_ATL_COM#3](../../atl/codesnippet/cpp/ccomclassfactory2-class_2.h)]

`CComClassFactory2`leitet sich von `CComClassFactory2Base` beiden und *Lizenz*. `CComClassFactory2Base`, wiederum leitet sich `IClassFactory2` von `CComObjectRootEx< CComGlobalsThreadModel >`und ab.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

`license`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`IClassFactory2`

`CComClassFactory2`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="ccomclassfactory2createinstance"></a><a name="createinstance"></a>CComClassFactory2::CreateInstance

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

### <a name="remarks"></a>Bemerkungen

Erfordert, dass der Computer vollständig lizenziert ist. Wenn keine vollständige Computerlizenz vorhanden ist, rufen Sie [CreateInstanceLic](#createinstancelic)auf.

## <a name="ccomclassfactory2createinstancelic"></a><a name="createinstancelic"></a>CComClassFactory2::CreateInstancelic

Ähnlich wie [CreateInstance](#createinstance) `CreateInstanceLic` , mit der Ausnahme, dass ein Lizenzschlüssel erforderlich ist.

```
STDMETHOD(CreateInstanceLic)(
    IUnknown* pUnkOuter,
    IUnknown* /* pUnkReserved
*/,
    REFIID riid,
    BSTR bstrKey,
    void** ppvObject);
```

### <a name="parameters"></a>Parameter

*pUnkOuter*<br/>
[in] Wenn das Objekt als Teil eines Aggregats erstellt wird, muss *pUnkOuter* das äußere Unbekannte sein. Andernfalls muss *pUnkOuter* NULL sein.

*pUnkReserved*<br/>
[in] Wird nicht verwendet. Muss NULL sein.

*riid*<br/>
[in] Die IID der angeforderten Schnittstelle. Wenn *pUnkOuter* nicht NULL ist, `IID_IUnknown`muss *riid* sein.

*bstrKey*<br/>
[in] Der Laufzeitlizenzschlüssel, der zuvor von `RequestLicKey`einem Aufruf an abgerufen wurde. Dieser Schlüssel ist erforderlich, um das Objekt zu erstellen.

*ppvObject*<br/>
[out] Ein Zeiger auf den Schnittstellenzeiger, der von *riid*angegeben wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, wird *ppvObject* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Sie können einen Lizenzschlüssel mit [RequestLicKey](#requestlickey)erhalten. Um ein Objekt auf einem nicht lizenzierten `CreateInstanceLic`Computer zu erstellen, müssen Sie anrufen.

## <a name="ccomclassfactory2getlicinfo"></a><a name="getlicinfo"></a>CComClassFactory2::GetLicInfo

Füllt eine [LICINFO-Struktur](/windows/win32/api/ocidl/ns-ocidl-licinfo) mit Informationen, die die Lizenzierungsfunktionen der Klassenfactory beschreiben.

```
STDMETHOD(GetLicInfo)(LICINFO* pLicInfo);
```

### <a name="parameters"></a>Parameter

*pLicInfo*<br/>
[out] Zeiger auf `LICINFO` eine Struktur.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Der `fRuntimeKeyAvail` Member dieser Struktur gibt an, ob die Klassenfactory bei einem Lizenzschlüssel das Erstellen von Objekten auf einem nicht lizenzierten Computer zulässt. Das *fLicVerified-Mitglied* gibt an, ob eine vollständige Computerlizenz vorhanden ist.

## <a name="ccomclassfactory2lockserver"></a><a name="lockserver"></a>CComClassFactory2::LockServer

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

## <a name="ccomclassfactory2requestlickey"></a><a name="requestlickey"></a>CComClassFactory2::RequestLicKey

Erstellt und gibt einen Lizenzschlüssel `fRuntimeKeyAvail` zurück, vorausgesetzt, das Element der [LICINFO-Struktur](/windows/win32/api/ocidl/ns-ocidl-licinfo) ist TRUE.

```
STDMETHOD(RequestLicKey)(DWORD dwReserved, BSTR* pbstrKey);
```

### <a name="parameters"></a>Parameter

*dwReserved*<br/>
[in] Wird nicht verwendet. Muss Null sein.

*pbstrKey*<br/>
[out] Zeiger auf den Lizenzschlüssel.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Für den Aufruf von [CreateInstanceLic](#createinstancelic) ist ein Lizenzschlüssel erforderlich, um ein Objekt auf einem nicht lizenzierten Computer zu erstellen. Wenn `fRuntimeKeyAvail` FALSE ist, können Objekte nur auf einem vollständig lizenzierten Computer erstellt werden.

Rufen Sie [GetLicInfo](#getlicinfo) auf, um den Wert von `fRuntimeKeyAvail`abzurufen.

## <a name="see-also"></a>Siehe auch

[CComClassFactoryAutoThread-Klasse](../../atl/reference/ccomclassfactoryautothread-class.md)<br/>
[CComClassFactorySingleton-Klasse](../../atl/reference/ccomclassfactorysingleton-class.md)<br/>
[CComObjectRootEx-Klasse](../../atl/reference/ccomobjectrootex-class.md)<br/>
[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
