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
ms.openlocfilehash: e29c30e95116ad68d3498f3f8d3231a63c92c0a7
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353063"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T-Klasse

Diese Klasse stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet, und unterstützt auch das Hosten von lizenzierten ActiveX-Steuerelementen.

> [!IMPORTANT]
> Diese Klasse und ihre Member können in Anwendungen, die im Windows-Runtime ausgeführt werden, nicht verwendet werden.

## <a name="syntax"></a>Syntax

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parameter

*Tbase*<br/>
Die Klasse, von der `CAxWindowT` abgeleitet wird.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Erstellt ein `CAxWindow2T`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CAxWindow2T:: Create](#create)|Erstellt ein Host Fenster.|
|[CAxWindow2T:: kreatecontrollic](#createcontrollic)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es und hostet es im angegebenen Fenster.|
|[CAxWindow2T:: kreatecontrollicex](#createcontrollicex)|Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und Ruft einen Schnittstellen Zeiger (oder Zeiger) aus dem Steuerelement ab.|
|[CAxWindow2T:: getwndclassname](#getwndclassname)|Statische Methode, die den Namen der Fenster Klasse abruft.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAxWindow2T:: Operator =](#operator_eq)|Weist einem vorhandenen-Objekt ein HWND zu `CAxWindow2T` .|

## <a name="remarks"></a>Hinweise

`CAxWindow2T` stellt Methoden zum Bearbeiten eines Fensters bereit, das ein ActiveX-Steuerelement hostet. `CAxWindow2T` bietet auch Unterstützung für das Hosting von lizenzierten ActiveX-Steuerelementen. Das Hosting wird von " **AtlAxWinLic80**" bereitgestellt, das von umschließt wird `CAxWindow2T` .

`CAxWindow2`Die Klasse wird als Spezialisierung der- `CAxWindow2T` Klasse implementiert. Diese Spezialisierung wird wie folgt deklariert:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` Member werden unter [CAxWindow](../../atl/reference/caxwindow-class.md)dokumentiert.

Ein Beispiel, in dem die Member dieser Klasse verwendet werden, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlwin. h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a> CAxWindow2T::CAxWindow2T

Erstellt ein `CAxWindow2T`-Objekt.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle eines vorhandenen Fensters.

## <a name="caxwindow2tcreate"></a><a name="create"></a> CAxWindow2T:: Create

Erstellt ein Host Fenster.

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

### <a name="remarks"></a>Hinweise

`CAxWindow2T::Create` Ruft [CWindow:: Create](../../atl/reference/cwindow-class.md#create) mit dem LPCTSTR *lpstrauwndclass* -Parameter auf, der auf die Fenster Klasse festgelegt ist, die das Hosting von Steuerelementen ermöglicht ( `AtlAxWinLic80` ).

`CWindow::Create`Eine Beschreibung der Parameter und des Rückgabewerts finden Sie unter.

**Hinweis** Wenn 0 als Wert für den *menuorid-* Parameter verwendet wird, muss es als 0U (Standardwert) angegeben werden, um einen Compilerfehler zu vermeiden.

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CAxWindow2T::Create` .

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a> CAxWindow2T:: kreatecontrollic

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

*bstraulickey*<br/>
Der Lizenzschlüssel für das Steuerelement. NULL, wenn ein nicht lizenziertes Steuerelement erstellt wird.

### <a name="remarks"></a>Hinweise

Eine Beschreibung der verbleibenden Parameter und des Rückgabewerts finden Sie unter [CAxWindow:: kreatecontrol](../../atl/reference/caxwindow-class.md#createcontrol) .

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CAxWindow2T::CreateControlLic` .

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a> CAxWindow2T:: kreatecontrollicex

Erstellt ein lizenziertes ActiveX-Steuerelement, initialisiert es, hostet es im angegebenen Fenster und Ruft einen Schnittstellen Zeiger (oder Zeiger) aus dem Steuerelement ab.

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

*bstraulickey*<br/>
Der Lizenzschlüssel für das Steuerelement. NULL, wenn ein nicht lizenziertes Steuerelement erstellt wird.

### <a name="remarks"></a>Hinweise

Weitere Informationen zu den verbleibenden Parametern und Rückgabe Werten finden Sie unter [CAxWindow:: kreatecontrolex](../../atl/reference/caxwindow-class.md#createcontrolex) .

### <a name="example"></a>Beispiel

Ein Beispiel, das verwendet, finden Sie unter Hosting von ActiveX-Steuer [Elementen mithilfe von ATL AxHost](../../atl/atl-control-containment-faq.md#hosting-activex-controls-using-atl-axhost) `CAxWindow2T::CreateControlLicEx` .

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a> CAxWindow2T:: getwndclassname

Ruft den Namen der Fenster Klasse ab.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine Zeichenfolge, die den Namen der Fenster Klasse () enthält, in der `AtlAxWinLic80` lizenzierte und nicht lizenzierte ActiveX-Steuerelemente gehostet werden können.

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a> CAxWindow2T:: Operator =

Weist einem vorhandenen-Objekt ein HWND zu `CAxWindow2T` .

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parameter

*hWnd*<br/>
Ein Handle eines vorhandenen Fensters.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Fragen und Antworten zur Steuerelementkapselung](../../atl/atl-control-containment-faq.md)
