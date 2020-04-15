---
title: CBindStatusCallback-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 6cdac444836574dd4d398571b71bb25363af5d3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321239"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback-Klasse

Diese Klasse implementiert die `IBindStatusCallback`-Schnittstelle.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, die die Funktion enthält, die aufgerufen wird, wenn die Daten empfangen werden.

*nBindFlags*<br/>
Gibt die Bindungsflags an, die von [GetBindInfo](#getbindinfo)zurückgegeben werden. Die Standardimplementierung legt fest, dass die Bindung asynchron ist, ruft die neueste Version des Datens/Objekts ab und speichert keine abgerufenen Daten im Datenträgercache.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|Der Konstruktor.|
|[CBindStatusCallback::'CBindStatusCallback](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBindStatusCallback::Download](#download)|Statische Methode, die den Downloadprozess startet, ein `CBindStatusCallback` Objekt erstellt und aufruft. `StartAsyncDownload`|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|Wird vom asynchronen Moniker aufgerufen, um Informationen über den Typ der zu erstellenden Bindung anzufordern.|
|[CBindStatusCallback::GetPriority](#getpriority)|Wird vom asynchronen Moniker aufgerufen, um die Priorität des Bindungsvorgangs abzubekommen. Die ATL-Implementierung gibt zurück. `E_NOTIMPL`|
|[CBindStatusCallback::OnDataVerfügbar](#ondataavailable)|Wird aufgerufen, um Daten für Ihre Anwendung bereitzustellen, sobald sie verfügbar sind. Liest die Daten und ruft dann die an sie übergebene Funktion auf, um die Daten zu verwenden.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|Wird aufgerufen, wenn die Ressourcen niedrig sind. Die ATL-Implementierung gibt S_OK zurück.|
|[CBindStatusCallback::OnObjectVerfügbar](#onobjectavailable)|Wird vom asynchronen Moniker aufgerufen, um einen Objektschnittstellenzeiger an ihre Anwendung zu übergeben. Die ATL-Implementierung gibt S_OK zurück.|
|[CBindStatusCallback::OnFortschritt](#onprogress)|Wird aufgerufen, um den Fortschritt eines Datendownloadvorgangs anzuzeigen. Die ATL-Implementierung gibt S_OK zurück.|
|[CBindStatusCallback::OnStartBinding](#onstartbinding)|Wird aufgerufen, wenn die Bindung gestartet wird.|
|[CBindStatusCallback::OnStopBinding](#onstopbinding)|Wird aufgerufen, wenn die asynchrone Datenübertragung beendet wird.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|Initialisiert die verfügbaren Bytes und die gelesenen Bytes auf Null, erstellt `OnDataAvailable` ein Push-Typ-Streamobjekt aus einer URL und ruft jedes Mal auf, wenn Daten verfügbar sind.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|Anzahl der zum Lesen verfügbaren Bytes.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|Gesamtanzahl der gelesenen Bytes.|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|Zeiger auf die Funktion, die aufgerufen wird, wenn Daten verfügbar sind.|
|[CBindStatusCallback::m_pT](#m_pt)|Zeiger auf das Objekt, das die asynchrone Datenübertragung anfordert.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|Zeiger auf die [IBindCtx-Schnittstelle](/windows/win32/api/objidl/nn-objidl-ibindctx) für den aktuellen Bindungsvorgang.|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|Zeiger auf `IBinding` die Schnittstelle für den aktuellen Bindungsvorgang.|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|Zeiger auf die [IMoniker-Schnittstelle](/windows/win32/api/objidl/nn-objidl-imoniker) für die zu verwendende URL.|
|[CBindStatusCallback::m_spStream](#m_spstream)|Zeiger auf die [IStream-Schnittstelle](/windows/win32/api/objidl/nn-objidl-istream) für die Datenübertragung.|

## <a name="remarks"></a>Bemerkungen

Die `CBindStatusCallback`-Klasse implementiert die `IBindStatusCallback`-Schnittstelle. `IBindStatusCallback`muss von Ihrer Anwendung implementiert werden, damit sie Benachrichtigungen von einer asynchronen Datenübertragung erhalten kann. Der vom System bereitgestellte asynchrone Moniker verwendet `IBindStatusCallback` Methoden zum Senden und Empfangen von Informationen über die asynchrone Datenübertragung an und von Ihrem Objekt.

In der `CBindStatusCallback` Regel ist das Objekt einem bestimmten Bindungsvorgang zugeordnet. Im [ASYNC-Beispiel](../../overview/visual-cpp-samples.md) wird beispielsweise beim Festlegen der URL-Eigenschaft ein `CBindStatusCallback` Objekt `Download`im Aufruf von:

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

Der asynchrone Moniker verwendet `OnData` die Rückruffunktion, um Ihre Anwendung aufzurufen, wenn sie über Daten verfügt. Der asynchrone Moniker wird vom System bereitgestellt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CComObjectRootBase`

`IBindStatusCallback`

[Ccomobjectrootex](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

Der Konstruktor.

```
CBindStatusCallback();
```

### <a name="remarks"></a>Bemerkungen

Erstellt ein Objekt, um Benachrichtigungen über die asynchrone Datenübertragung zu erhalten. In der Regel wird für jeden Bindungsvorgang ein Objekt erstellt.

Der Konstruktor initialisiert auch [m_pT](#m_pt) und [m_pFunc](#m_pfunc) zu NULL.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a>CBindStatusCallback::'CBindStatusCallback

Der Destruktor.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a>CBindStatusCallback::Download

Erstellt `CBindStatusCallback` ein Objekt `StartAsyncDownload` und ruft auf, um mit dem herunterladen von Daten asynchron von der angegebenen URL zu beginnen.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
[in] Ein Zeiger auf das Objekt, das die asynchrone Datenübertragung anfordert. Das `CBindStatusCallback` Objekt wird für die Klasse dieses Objekts templatiert.

*pFunc*<br/>
[in] Ein Zeiger auf die Funktion, die die gelesenen Daten empfängt. Die Funktion ist ein Member der Klasse `T`des Typs Ihres Objekts . Siehe [StartAsyncDownload](#startasyncdownload) für Syntax und ein Beispiel.

*bstrURL*<br/>
[in] Die URL, von der Daten abzurufen sind. Kann ein gültiger URL oder Dateiname sein. Lässt keine NULL-Werte zu. Beispiel:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] Die `IUnknown` des Containers. NULL standardmäßig.

*bRelativ*<br/>
[in] Ein Flag, das angibt, ob die URL relativ oder absolut ist. FALSE standardmäßig, was bedeutet, dass die URL absolut ist.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Jedes Mal, wenn Daten verfügbar sind, werden sie über `OnDataAvailable`an das Objekt gesendet. `OnDataAvailable`liest die Daten und ruft die Funktion auf, auf die *pFunc* zeigt (z. B. um die Daten zu speichern oder auf dem Bildschirm zu drucken).

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a>CBindStatusCallback::GetBindInfo

Wird aufgerufen, um dem Moniker zu sagen, wie er binden soll.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>Parameter

*pgrfBSCF*<br/>
[out] Ein Zeiger auf BINDF-Enumerationswerte, der angibt, wie der Bindungsvorgang ausgeführt werden soll. Standardmäßig mit den folgenden Enumerationswerten festgelegt:

BINDF_ASYNCHRONOUS Asynchroner Download.

BINDF_ASYNCSTORAGE `OnDataAvailable` gibt E_PENDING zurück, wenn Daten noch nicht verfügbar sind, anstatt zu blockieren, bis Daten verfügbar sind.

BINDF_GETNEWESTVERSION Der Bindungsvorgang sollte die neueste Version der Daten abrufen.

BINDF_NOWRITECACHE Der Bindungsvorgang sollte keine abgerufenen Daten im Datenträgercache speichern.

*pbindinfo*<br/>
[in, out] Ein Zeiger auf `BINDINFO` die Struktur, der weitere Informationen darüber enthält, wie die Bindung des Objekts erfolgen soll.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung legt fest, dass die Bindung asynchron ist und das Datenpushmodell verwendet wird. Im Data-Push-Modell steuert der Moniker den asynchronen Bindungsvorgang und benachrichtigt den Client kontinuierlich, wenn neue Daten verfügbar sind.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a>CBindStatusCallback::GetPriority

Wird vom asynchronen Moniker aufgerufen, um die Priorität des Bindungsvorgangs abzubekommen.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>Parameter

*pnPriorität*<br/>
[out] Adresse der **LONG** LONG-Variablen, die bei Erfolg die Priorität erhält.

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

Kann verwendet werden, um die Anzahl der zum Lesen verfügbaren Bytes zu speichern.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Bemerkungen

Initialisiert auf `StartAsyncDownload`Null in .

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a>CBindStatusCallback::m_dwTotalRead

Die kumulative Summe der in der asynchronen Datenübertragung gelesenen Bytes.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Bemerkungen

Inkrementiert `OnDataAvailable` jedes Mal wird durch die Anzahl der Bytes tatsächlich gelesen aufgerufen. Initialisiert auf `StartAsyncDownload`Null in .

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

Die Funktion, `m_pFunc` auf die `OnDataAvailable` verwiesen wird, wird aufgerufen, nachdem sie die verfügbaren Daten gelesen hat (z. B. um die Daten zu speichern oder auf dem Bildschirm zu drucken).

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Bemerkungen

Die Funktion, `m_pFunc` auf die von verwiesen wird, ist ein Member der Objektklasse und hat die folgende Syntax:

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a>CBindStatusCallback::m_pT

Ein Zeiger auf das Objekt, das die asynchrone Datenübertragung anfordert.

```
T* m_pT;
```

### <a name="remarks"></a>Bemerkungen

Das `CBindStatusCallback` Objekt wird für die Klasse dieses Objekts templatiert.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a>CBindStatusCallback::m_spBindCtx

Ein Zeiger auf eine [IBindCtx-Schnittstelle,](/windows/win32/api/objidl/nn-objidl-ibindctx) die Zugriff auf den Bindungskontext bietet (ein Objekt, das Informationen zu einem bestimmten Monikerbindungsvorgang speichert).

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Bemerkungen

Initialisiert `StartAsyncDownload`in .

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a>CBindStatusCallback::m_spBinding

Ein Zeiger auf `IBinding` die Schnittstelle des aktuellen Bindungsvorgangs.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Bemerkungen

Initialisiert `OnStartBinding` in und `OnStopBinding`veröffentlicht in .

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

Ein Zeiger auf die [IMoniker-Schnittstelle](/windows/win32/api/objidl/nn-objidl-imoniker) für die url, die verwendet werden soll.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Bemerkungen

Initialisiert `StartAsyncDownload`in .

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a>CBindStatusCallback::m_spStream

Ein Zeiger auf die [IStream-Schnittstelle](/windows/win32/api/objidl/nn-objidl-istream) des aktuellen Bindungsvorgangs.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Bemerkungen

Initialisiert `OnDataAvailable` aus `STGMEDIUM` der Struktur, wenn das BCSF-Flag BCSF_FIRSTDATANOTIFICATION wird und freigegeben wird, wenn das BCSF-Flag BCSF_LASTDATANOTIFICATION wird.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a>CBindStatusCallback::OnDataVerfügbar

Die vom System bereitgestellten asynchronen Monikeraufrufe, `OnDataAvailable` um dem Objekt Daten bereitzustellen, sobald es verfügbar ist.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>Parameter

*grfBSCF*<br/>
[in] Ein BSCF-Enumerationswert. Eine oder mehrere der folgenden Optionen: BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION oder BSCF_LASTDATANOTIFICATION.

*dwSize*<br/>
[in] Der kumulative Betrag (in Bytes) der seit Beginn der Bindung verfügbaren Daten. Kann Null sein, was darauf hinweist, dass die Datenmenge nicht relevant ist oder dass kein bestimmter Betrag verfügbar wurde.

*pformatetc*<br/>
[in] Zeiger auf die [FORMATETC-Struktur,](/windows/win32/com/the-formatetc-structure) die das Format der verfügbaren Daten enthält. Wenn kein Format vorhanden ist, kann CF_NULL werden.

*pstgmed*<br/>
[in] Zeiger auf die [STGMEDIUM-Struktur,](/windows/win32/com/the-stgmedium-structure) die die tatsächlichen Daten jetzt verfügbar hält.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

`OnDataAvailable`liest die Daten und ruft dann eine Methode der Objektklasse auf (z. B. um die Daten zu speichern oder auf dem Bildschirm zu drucken). Weitere Informationen finden Sie unter [CBindStatusCallback::StartAsyncDownload.](#startasyncdownload)

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a>CBindStatusCallback::OnLowResource

Wird aufgerufen, wenn die Ressourcen niedrig sind.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>Parameter

*dwReserved*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a>CBindStatusCallback::OnObjectVerfügbar

Wird vom asynchronen Moniker aufgerufen, um einen Objektschnittstellenzeiger an ihre Anwendung zu übergeben.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Schnittstellenbezeichner der angeforderten Schnittstelle. Nicht verwendet.

*Punk*<br/>
Adresse der IUnknown-Schnittstelle. Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a>CBindStatusCallback::OnFortschritt

Wird aufgerufen, um den Fortschritt eines Datendownloadvorgangs anzuzeigen.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>Parameter

*ulProgress*<br/>
Unsignierte lange ganze Zahl. Nicht verwendet.

*ulProgressMax*<br/>
Nicht signierte lange ganzzahlige Nicht verwendete.

*ulStatusCode*<br/>
Unsignierte lange ganze Zahl. Nicht verwendet.

*szStatusText*<br/>
Adresse eines Zeichenfolgenwerts. Nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a>CBindStatusCallback::OnStartBinding

Legt das [m_spBinding](#m_spbinding) Datenelement `IBinding` m_spBinding auf den Zeiger in *pBinding*fest.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>Parameter

*dwReserved*<br/>
Für die zukünftige Verwendung reserviert.

*pBinding*<br/>
[in] Adresse der IBinding-Schnittstelle des aktuellen Bindungsvorgangs. Dies kann nicht NULL sein. Der Client sollte AddRef auf diesem Zeiger aufrufen, um einen Verweis auf das Bindungsobjekt beizubehalten.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a>CBindStatusCallback::OnStopBinding

Gibt `IBinding` den Zeiger im Datenmember [m_spBinding](#m_spbinding).

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>Parameter

*Hresult*<br/>
Statuscode, der vom Bindungsvorgang zurückgegeben wird.

*szError*<br/>
Adresse eines Zeichenfolgenwerts. Nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Wird vom vom System bereitgestellten asynchronen Moniker aufgerufen, um das Ende des Bindungsvorgangs anzugeben.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

Startet das herunterladen von Daten asynchron von der angegebenen URL.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
[in] Ein Zeiger auf das Objekt, das die asynchrone Datenübertragung anfordert. Das `CBindStatusCallback` Objekt wird für die Klasse dieses Objekts templatiert.

*pFunc*<br/>
[in] Ein Zeiger auf die Funktion, die die gelesenen Daten empfängt. Die Funktion ist ein Member der Klasse `T`des Typs Ihres Objekts . Siehe **Hinweise** für Syntax und ein Beispiel.

*bstrURL*<br/>
[in] Die URL, von der Daten abzurufen sind. Kann ein gültiger URL oder Dateiname sein. Lässt keine NULL-Werte zu. Beispiel:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
[in] Die `IUnknown` des Containers. NULL standardmäßig.

*bRelativ*<br/>
[in] Ein Flag, das angibt, ob die URL relativ oder absolut ist. FALSE standardmäßig, was bedeutet, dass die URL absolut ist.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Jedes Mal, wenn Daten verfügbar sind, werden sie über `OnDataAvailable`an das Objekt gesendet. `OnDataAvailable`liest die Daten und ruft die Funktion auf, auf die *pFunc* zeigt (z. B. um die Daten zu speichern oder auf dem Bildschirm zu drucken).

Die Funktion, auf die *pFunc* zeigt, ist ein Member der Klasse Ihres Objekts und hat die folgende Syntax:

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

Im folgenden Beispiel (aus dem [ASYNC-Beispiel)](../../overview/visual-cpp-samples.md) schreibt die Funktion `OnData` die empfangenen Daten in ein Textfeld.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
