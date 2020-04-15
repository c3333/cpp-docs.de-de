---
title: CAxWindow2T-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: 14080b624132979df533135bc1eef108dc793398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318698"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T-Klasse

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet, und unterstützt auch das Hosten lizenzierter ActiveX-Steuerelemente.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parameter

*TBase*<br/>
Die Klasse, `CAxWindowT` aus der sich ableitet.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Erstellt ein `CAxWindow2T`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAxWindow2T::Erstellen](#create)|Erstellt ein Hostfenster.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.|
|[CAxWindow2T::CreateControllicex](#createcontrollicex)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und ruft einen Schnittstellenzeiger (oder Zeiger) aus dem Steuerelement ab.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Statische Methode, die den Namen der Fensterklasse abruft.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAxWindow2T::Operator =](#operator_eq)|Weist einem vorhandenen `CAxWindow2T` Objekt eine HWND zu.|

## <a name="remarks"></a>Bemerkungen

`CAxWindow2T`stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet. `CAxWindow2T`unterstützt auch das Hosting lizenzierter ActiveX-Steuerelemente. Das Hosting wird von " **AtlAxWinLic80** `CAxWindow2T`", die von umwickelt wird bereitgestellt.

Die `CAxWindow2` Klasse wird als Spezialisierung `CAxWindow2T` der Klasse implementiert. Diese Spezialisierung wird wie:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT`Mitglieder werden unter [CAxWindow](../../atl/reference/caxwindow-class.md)dokumentiert.

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen mithilfe von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das die Member dieser Klasse verwendet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Erstellt ein `CAxWindow2T`-Objekt.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle eines vorhandenen Fensters.

## <a name="caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T::Erstellen

Erstellt ein Hostfenster.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>Bemerkungen

`CAxWindow2T::Create`ruft [CWindow::Create](../../atl/reference/cwindow-class.md#create) auf, wenn der Parameter LPCTSTR *lpstrWndClass* `AtlAxWinLic80`auf die Fensterklasse festgelegt ist, die das Steuerelementhosting ( bereitstellt).

Eine `CWindow::Create` Beschreibung der Parameter und des Rückgabewerts finden Sie unter .

**Hinweis** Wenn 0 als Wert für den *Parameter MenuOrID* verwendet wird, muss es als 0U (der Standardwert) angegeben werden, um einen Compilerfehler zu vermeiden.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `CAxWindow2T::Create`verwendet.

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parameter

*bstrLicKey*<br/>
Der Lizenzschlüssel für das Steuerelement; NULL, wenn sie ein nicht lizenziertes Steuerelement erstellen.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [CAxWindow::CreateControl.](../../atl/reference/caxwindow-class.md#createcontrol)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `CAxWindow2T::CreateControlLic`verwendet.

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T::CreateControllicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und ruft einen Schnittstellenzeiger (oder Zeiger) aus dem Steuerelement ab.

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>Parameter

*bstrLicKey*<br/>
Der Lizenzschlüssel für das Steuerelement; NULL, wenn sie ein nicht lizenziertes Steuerelement erstellen.

### <a name="remarks"></a>Bemerkungen

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [CAxWindow::CreateControlEx.](../../atl/reference/caxwindow-class.md#createcontrolex)

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [Hostieren von ActiveX-Steuerelementen unter Verwendung von ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) für ein Beispiel, das `CAxWindow2T::CreateControlLicEx`verwendet.

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Ruft den Namen der Fensterklasse ab.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den`AtlAxWinLic80`Namen der Fensterklasse ( ) enthält, die lizenzierte und nicht lizenzierte ActiveX-Steuerelemente hosten kann.

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T::Operator =

Weist einem vorhandenen `CAxWindow2T` Objekt eine HWND zu.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle eines vorhandenen Fensters.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Fragen und Antworten zur Steuerelementkapselung](../../atl/atl-control-containment-faq.md)
