---
title: IOleObjectImpl-Klasse
ms.date: 11/04/2016
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: 86d82aea2e92eb99903284abe4ac03478369616c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326524"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl-Klasse

Diese Klasse `IUnknown` implementiert und ist die Hauptschnittstelle, über die ein Container mit einem Steuerelement kommuniziert.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Ihre Klasse, `IOleObjectImpl`abgeleitet von .

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IOleObjectImpl::Beratung](#advise)|Stellt eine beratende Verbindung mit dem Steuerelement her.|
|[IOleObjectImpl::Schließen](#close)|Ändert den Steuerstatus von "Laufen" auf "Geladen".|
|[IOleObjectImpl::DoVerb](#doverb)|Weist das Steuerelement an, eine der aufgezählten Aktionen auszuführen.|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|Weist das Steuerelement an, jeden Rückgängigzustand zu verwerfen, den es aufrechterhält.|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|Weist das Steuerelement an, die Benutzeroberfläche aus der Ansicht zu entfernen.|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|Führt das Steuerelement aus und installiert das Fenster, installiert jedoch nicht die Benutzeroberfläche des Steuerelements.|
|[IOleObjectImpl::DoVerbÖffnen](#doverbopen)|Bewirkt, dass das Steuerelement in einem separaten Fenster geöffnet wird.|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|Führt die angegebene Aktion aus, wenn der Benutzer auf das Steuerelement doppelklickt. Das Steuerelement definiert die Aktion, in der Regel, um das Steuerelement an Ort und Stelle zu aktivieren.|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|Zeigt dem Benutzer ein neu eingefügtes Steuerelement an.|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|Aktiviert das Steuerelement an Ort und Stelle und zeigt die Benutzeroberfläche des Steuerelements an, z. B. Menüs und Symbolleisten.|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|Zählt die Beratungsverbindungen des Steuerelements auf.|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|Zählt Aktionen für das Steuerelement auf.|
|[IOleObjectImpl::GetClientSite](#getclientsite)|Ruft die Clientsite des Steuerelements ab.|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|Ruft Daten aus der Zwischenablage ab. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleObjectImpl::GetExtent](#getextent)|Ruft die Ausdehnung des Anzeigebereichs des Steuerelements ab.|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|Ruft den Status des Steuerelements ab.|
|[IOleObjectImpl::GetMoniker](#getmoniker)|Ruft den Moniker des Steuerelements ab. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|Ruft den Klassenbezeichner des Steuerelements ab.|
|[IOleObjectImpl::GetUserType](#getusertype)|Ruft den Benutzertypnamen des Steuerelements ab.|
|[IOleObjectImpl::InitFromData](#initfromdata)|Initialisiert das Steuerelement aus ausgewählten Daten. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleObjectImpl::IsUptoDate](#isuptodate)|Überprüft, ob das Steuerelement auf dem neuesten Stand ist. Die ATL-Implementierung gibt S_OK zurück.|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|Wird von [DoVerbDiscardUndo](#doverbdiscardundo) aufgerufen, nachdem der Rückgängig-Zustand verworfen wurde.|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|Wird von [DoVerbHide](#doverbhide) aufgerufen, nachdem das Steuerelement ausgeblendet wurde.|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|Wird von [DoVerbInPlaceActivate](#doverbinplaceactivate) aufgerufen, nachdem das Steuerelement aktiviert wurde.|
|[IOleObjectImpl::OnPostVerbÖffnen](#onpostverbopen)|Wird von [DoVerbOpen](#doverbopen) aufgerufen, nachdem das Steuerelement zur Bearbeitung in einem separaten Fenster geöffnet wurde.|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|Wird von [DoVerbShow](#doverbshow) aufgerufen, nachdem das Steuerelement sichtbar gemacht wurde.|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|Wird von [DoVerbUIActivate](#doverbuiactivate) aufgerufen, nachdem die Benutzeroberfläche des Steuerelements aktiviert wurde.|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|Wird von [DoVerbDiscardUndo](#doverbdiscardundo) aufgerufen, bevor der Rückgängig-Zustand verworfen wird.|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|Wird von [DoVerbHide](#doverbhide) aufgerufen, bevor das Steuerelement ausgeblendet wird.|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|Wird von [DoVerbInPlaceActivate](#doverbinplaceactivate) aufgerufen, bevor das Steuerelement aktiviert wird.|
|[IOleObjectImpl::OnPreVerbÖffnen](#onpreverbopen)|Wird von [DoVerbOpen](#doverbopen) aufgerufen, bevor das Steuerelement zur Bearbeitung in einem separaten Fenster geöffnet wurde.|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|Wird von [DoVerbShow](#doverbshow) aufgerufen, bevor das Steuerelement sichtbar gemacht wurde.|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|Wird von [DoVerbUIActivate](#doverbuiactivate) aufgerufen, bevor die Benutzeroberfläche des Steuerelements aktiviert wurde.|
|[IOleObjectImpl::SetClientSite](#setclientsite)|Gibt das Steuerelement über seine Clientsite im Container an.|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|Empfiehlt ein Farbschema für die Anwendung des Steuerelements, falls vorhanden. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleObjectImpl::SetExtent](#setextent)|Legt die Ausdehnung des Anzeigebereichs des Steuerelements fest.|
|[IOleObjectImpl::SetHostNames](#sethostnames)|Gibt das Steuerelement die Namen der Containeranwendung und des Containerdokuments an.|
|[IOleObjectImpl::SetMoniker](#setmoniker)|Sagt dem Steuerelement an, was sein Moniker ist. Die ATL-Implementierung gibt E_NOTIMPL zurück.|
|[IOleObjectImpl::Unadvise](#unadvise)|Löscht eine beratende Verbindung mit dem Steuerelement.|
|[IOleObjectImpl::Update](#update)|Aktualisiert das Steuerelement. Die ATL-Implementierung gibt S_OK zurück.|

## <a name="remarks"></a>Bemerkungen

Die [IOleObject-Schnittstelle](/windows/win32/api/oleidl/nn-oleidl-ioleobject) ist die Hauptschnittstelle, über die ein Container mit einem Steuerelement kommuniziert. Die `IOleObjectImpl` Klasse stellt eine Standardimplementierung `IUnknown` dieser Schnittstelle bereit und implementiert, indem Informationen in Debugbuilds an das Dumpgerät gesendet werden.

**Verwandte Artikel** [ATL Tutorial](../../atl/active-template-library-atl-tutorial.md), Erstellen eines [ATL-Projekts](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ioleobjectimpladvise"></a><a name="advise"></a>IOleObjectImpl::Beratung

Stellt eine beratende Verbindung mit dem Steuerelement her.

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) im Windows SDK.

## <a name="ioleobjectimplclose"></a><a name="close"></a>IOleObjectImpl::Schließen

Ändert den Steuerstatus von "Laufen" auf "Geladen".

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>Bemerkungen

Deaktiviert das Steuerelement und zerstört das Kontrollfenster, falls vorhanden. Wenn der Steuerelementklassendatenmember [CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave) TRUE ist und der Parameter *dwSaveOption* entweder OLECLOSE_SAVEIFDIRTY oder OLECLOSE_PROMPTSAVE ist, werden die Steuerelementeigenschaften vor dem Schließen gespeichert.

Die Zeiger in den Steuerelementklassendatenmembern [CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite) und [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink) werden freigegeben, und die Datenmember [CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)und [CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex) werden auf FALSE festgelegt.

Siehe [IOleObject::Schließen](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) im Windows SDK.

## <a name="ioleobjectimpldoverb"></a><a name="doverb"></a>IOleObjectImpl::DoVerb

Weist das Steuerelement an, eine der aufgezählten Aktionen auszuführen.

```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```

### <a name="remarks"></a>Bemerkungen

Abhängig vom Wert `iVerb`von wird eine `DoVerb` der ATL-Hilfsfunktionen wie folgt aufgerufen:

|*iVerb* Wert|DoVerb-Hilfsfunktion namens|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbinPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

Siehe [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) im Windows SDK.

## <a name="ioleobjectimpldoverbdiscardundo"></a><a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo

Weist das Steuerelement an, jeden Rückgängigzustand zu verwerfen, den es aufrechterhält.

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ioleobjectimpldoverbhide"></a><a name="doverbhide"></a>IOleObjectImpl::DoVerbHide

Deaktiviert und entfernt die Benutzeroberfläche des Steuerelements und blendet das Steuerelement aus.

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält. Wird in der ATL-Implementierung nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ioleobjectimpldoverbinplaceactivate"></a><a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate

Führt das Steuerelement aus und installiert das Fenster, installiert jedoch nicht die Benutzeroberfläche des Steuerelements.

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält. Wird in der ATL-Implementierung nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Aktiviert das Steuerelement an Ort und Stelle, indem [CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)aufgerufen wird. Sofern der Datenmember `m_bWindowOnly` der Steuerelementklasse `DoVerbInPlaceActivate` nicht TRUE ist, wird zunächst versucht, das Steuerelement als fensterloses Steuerelement zu aktivieren (nur möglich, wenn der Container [IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)unterstützt). Wenn dies fehlschlägt, versucht die Funktion, das Steuerelement mit erweiterten Features zu aktivieren (nur möglich, wenn der Container [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)unterstützt). Wenn dies fehlschlägt, versucht die Funktion, das Steuerelement ohne erweiterte Funktionen zu aktivieren (nur möglich, wenn der Container [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)unterstützt). Wenn die Aktivierung erfolgreich ist, benachrichtigt die Funktion den Container, für den das Steuerelement aktiviert wurde.

## <a name="ioleobjectimpldoverbopen"></a><a name="doverbopen"></a>IOleObjectImpl::DoVerbÖffnen

Bewirkt, dass das Steuerelement in einem separaten Fenster geöffnet wird.

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

## <a name="ioleobjectimpldoverbprimary"></a><a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary

Definiert die Aktion, die ausgeführt wird, wenn der Benutzer auf das Steuerelement doppelklickt.

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Legen Sie standardmäßig fest, dass die Eigenschaftenseiten angezeigt werden. Sie können dies in Ihrer Steuerelementklasse überschreiben, um beim Doppelklicken ein anderes Verhalten aufzurufen. spielen Sie z. B. ein Video ab oder gehen Sie aktiv an Ort und Stelle.

## <a name="ioleobjectimpldoverbshow"></a><a name="doverbshow"></a>IOleObjectImpl::DoVerbShow

Weist den Container an, das Steuerelement sichtbar zu machen.

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält. Wird in der ATL-Implementierung nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ioleobjectimpldoverbuiactivate"></a><a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate

Aktiviert die Benutzeroberfläche des Steuerelements und benachrichtigt den Container, dass seine Menüs durch zusammengesetzte Menüs ersetzt werden.

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
[in] Zeiger auf das Rechteck, in das das Steuerelement gezeichnet werden soll.

*hwndParent*<br/>
[in] Handle des Fensters, das das Steuerelement enthält. Wird in der ATL-Implementierung nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ioleobjectimplenumadvise"></a><a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

Liefert eine Aufzählung registrierter Beratungsverbindungen für dieses Steuerelement.

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IOleObject::EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) im Windows SDK.

## <a name="ioleobjectimplenumverbs"></a><a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

Stellt eine Enumeration registrierter Aktionen (Verben) `OleRegEnumVerbs`für dieses Steuerelement durch Aufrufen von an.

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>Bemerkungen

Sie können verbs der .rgs-Datei Ihres Projekts hinzufügen. Siehe z. B. CIRCCTL. RGS in der [CIRC-Probe.](../../overview/visual-cpp-samples.md)

Siehe [IOleObject:EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) im Windows SDK.

## <a name="ioleobjectimplgetclientsite"></a><a name="getclientsite"></a>IOleObjectImpl::GetClientSite

Fügt den Zeiger im Steuerelementklassendatenmember [CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite) in *ppClientSite* ein und erhöht die Verweisanzahl auf dem Zeiger.

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) im Windows SDK.

## <a name="ioleobjectimplgetclipboarddata"></a><a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData

Ruft Daten aus der Zwischenablage ab.

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) im Windows SDK.

## <a name="ioleobjectimplgetextent"></a><a name="getextent"></a>IOleObjectImpl::GetExtent

Ruft die Anzeigegröße eines laufenden Steuerelements in HIMETRIC-Einheiten (0,01 Millimeter pro Einheit) ab.

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Bemerkungen

Die Größe wird im Steuerelementklassendatenmember [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)gespeichert.

Siehe [IOleObject::GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) im Windows SDK.

## <a name="ioleobjectimplgetmiscstatus"></a><a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus

Gibt einen Zeiger auf registrierte Statusinformationen `OleRegGetMiscStatus`für das Steuerelement zurück, indem aufgerufen wird.

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>Bemerkungen

Die Statusinformationen umfassen Verhaltensweisen, die von den Steuerelement- und Präsentationsdaten unterstützt werden. Sie können der .rgs-Datei Ihres Projekts Statusinformationen hinzufügen.

Siehe [IOleObject::GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) im Windows SDK.

## <a name="ioleobjectimplgetmoniker"></a><a name="getmoniker"></a>IOleObjectImpl::GetMoniker

Ruft den Moniker des Steuerelements ab.

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) im Windows SDK.

## <a name="ioleobjectimplgetuserclassid"></a><a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

Gibt den Klassenbezeichner des Steuerelements zurück.

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject:GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) im Windows SDK.

## <a name="ioleobjectimplgetusertype"></a><a name="getusertype"></a>IOleObjectImpl::GetUserType

Gibt den Benutzertypnamen des Steuerelements zurück, indem er aufruft. `OleRegGetUserType`

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>Bemerkungen

Der Benutzertypname wird für die Anzeige in Benutzeroberflächenelementen wie Menüs und Dialogfeldern verwendet. Sie können den Benutzertypnamen in der .rgs-Datei Ihres Projekts ändern.

Siehe [IOleObject::GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) im Windows SDK.

## <a name="ioleobjectimplinitfromdata"></a><a name="initfromdata"></a>IOleObjectImpl::InitFromData

Initialisiert das Steuerelement aus ausgewählten Daten.

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) im Windows SDK.

## <a name="ioleobjectimplisuptodate"></a><a name="isuptodate"></a>IOleObjectImpl::IsUptoDate

Überprüft, ob das Steuerelement auf dem neuesten Stand ist.

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) im Windows SDK.

## <a name="ioleobjectimplonpostverbdiscardundo"></a><a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo

Wird von [DoVerbDiscardUndo](#doverbdiscardundo) aufgerufen, nachdem der Rückgängig-Zustand verworfen wurde.

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode mit Code, der ausgeführt werden soll, nachdem der Rückgängig-Zustand verworfen wurde.

## <a name="ioleobjectimplonpostverbhide"></a><a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide

Wird von [DoVerbHide](#doverbhide) aufgerufen, nachdem das Steuerelement ausgeblendet wurde.

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode mit Code, der ausgeführt werden soll, nachdem das Steuerelement ausgeblendet wurde.

## <a name="ioleobjectimplonpostverbinplaceactivate"></a><a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate

Wird von [DoVerbInPlaceActivate](#doverbinplaceactivate) aufgerufen, nachdem das Steuerelement aktiviert wurde.

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode mit Code, der ausgeführt werden soll, nachdem das Steuerelement aktiviert wurde.

## <a name="ioleobjectimplonpostverbopen"></a><a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbÖffnen

Wird von [DoVerbOpen](#doverbopen) aufgerufen, nachdem das Steuerelement zur Bearbeitung in einem separaten Fenster geöffnet wurde.

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode mit Code, der ausgeführt werden soll, nachdem das Steuerelement zur Bearbeitung in einem separaten Fenster geöffnet wurde.

## <a name="ioleobjectimplonpostverbshow"></a><a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

Wird von [DoVerbShow](#doverbshow) aufgerufen, nachdem das Steuerelement sichtbar gemacht wurde.

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode mit Code, der ausgeführt werden soll, nachdem das Steuerelement sichtbar gemacht wurde.

## <a name="ioleobjectimplonpostverbuiactivate"></a><a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate

Wird von [DoVerbUIActivate](#doverbuiactivate) aufgerufen, nachdem die Benutzeroberfläche des Steuerelements aktiviert wurde.

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode mit Code, der ausgeführt werden soll, nachdem die Benutzeroberfläche des Steuerelements aktiviert wurde.

## <a name="ioleobjectimplonpreverbdiscardundo"></a><a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo

Wird von [DoVerbDiscardUndo](#doverbdiscardundo) aufgerufen, bevor der Rückgängig-Zustand verworfen wird.

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zu verhindern, dass der Rückgängig-Zustand verworfen wird, überschreiben Sie diese Methode, um einen Fehler HRESULT zurückzugeben.

## <a name="ioleobjectimplonpreverbhide"></a><a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide

Wird von [DoVerbHide](#doverbhide) aufgerufen, bevor das Steuerelement ausgeblendet wird.

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zu verhindern, dass das Steuerelement ausgeblendet wird, überschreiben Sie diese Methode, um einen Fehler HRESULT zurückzugeben.

## <a name="ioleobjectimplonpreverbinplaceactivate"></a><a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate

Wird von [DoVerbInPlaceActivate](#doverbinplaceactivate) aufgerufen, bevor das Steuerelement aktiviert wird.

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zu verhindern, dass das Steuerelement aktiviert wird, überschreiben Sie diese Methode, um einen Fehler HRESULT zurückzugeben.

## <a name="ioleobjectimplonpreverbopen"></a><a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbÖffnen

Wird von [DoVerbOpen](#doverbopen) aufgerufen, bevor das Steuerelement zur Bearbeitung in einem separaten Fenster geöffnet wurde.

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zu verhindern, dass das Steuerelement für die Bearbeitung in einem separaten Fenster geöffnet wird, überschreiben Sie diese Methode, um einen Fehler HRESULT zurückzugeben.

## <a name="ioleobjectimplonpreverbshow"></a><a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow

Wird von [DoVerbShow](#doverbshow) aufgerufen, bevor das Steuerelement sichtbar gemacht wurde.

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zu verhindern, dass das Steuerelement sichtbar gemacht wird, überschreiben Sie diese Methode, um einen Fehler HRESULT zurückzugeben.

## <a name="ioleobjectimplonpreverbuiactivate"></a><a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate

Wird von [DoVerbUIActivate](#doverbuiactivate) aufgerufen, bevor die Benutzeroberfläche des Steuerelements aktiviert wurde.

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Um zu verhindern, dass die Benutzeroberfläche des Steuerelements aktiviert wird, überschreiben Sie diese Methode, um einen Fehler HRESULT zurückzugeben.

## <a name="ioleobjectimplsetclientsite"></a><a name="setclientsite"></a>IOleObjectImpl::SetClientSite

Gibt das Steuerelement über seine Clientsite im Container an.

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>Bemerkungen

Die Methode gibt dann S_OK zurück.

Siehe [IOleObject::SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) im Windows SDK.

## <a name="ioleobjectimplsetcolorscheme"></a><a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

Empfiehlt ein Farbschema für die Anwendung des Steuerelements, falls vorhanden.

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) im Windows SDK.

## <a name="ioleobjectimplsetextent"></a><a name="setextent"></a>IOleObjectImpl::SetExtent

Legt die Ausdehnung des Anzeigebereichs des Steuerelements fest.

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>Bemerkungen

Andernfalls `SetExtent` wird der Wert `psizel` gespeichert, auf den im Steuerelementklassendatenmember [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)verwiesen wird. Dieser Wert ist in HIMETRIC-Einheiten (0,01 Millimeter pro Einheit) vorhanden.

Wenn der Steuerelementklassendatenmember [CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural) TRUE ist, `SetExtent` speichert `psizel` auch der Wert, auf den im Steuerelementklassendatenmember [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)verwiesen wird.

Wenn das Steuerelementklassendatenelement [CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize) `SendOnDataChange` TRUE `SendOnViewChange` ist, `SetExtent` ruft und benachrichtigt alle beim Beratungshalter registrierten Beratungssenken, dass sich die Steuerelementgröße geändert hat.

Siehe [IOleObject::SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) im Windows SDK.

## <a name="ioleobjectimplsethostnames"></a><a name="sethostnames"></a>IOleObjectImpl::SetHostNames

Gibt das Steuerelement die Namen der Containeranwendung und des Containerdokuments an.

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) im Windows SDK.

## <a name="ioleobjectimplsetmoniker"></a><a name="setmoniker"></a>IOleObjectImpl::SetMoniker

Sagt dem Steuerelement an, was sein Moniker ist.

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>Rückgabewert

Gibt E_NOTIMPL zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) im Windows SDK.

## <a name="ioleobjectimplunadvise"></a><a name="unadvise"></a>IOleObjectImpl::Unadvise

Löscht die im `m_spOleAdviseHolder` Datenmember der Steuerungsklasse gespeicherte beratungsgebundene Verbindung.

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) im Windows SDK.

## <a name="ioleobjectimplupdate"></a><a name="update"></a>IOleObjectImpl::Update

Aktualisiert das Steuerelement.

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Siehe [IOleObject::Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX-Steuerelementschnittstellen](/windows/win32/com/activex-controls-interfaces)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
