---
title: CComControlBase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComControlBase
- ATLCTL/ATL::CComControlBase
- ATLCTL/ATL::CComControlBase::AppearanceType
- ATLCTL/ATL::CComControlBase::CComControlBase
- ATLCTL/ATL::CComControlBase::ControlQueryInterface
- ATLCTL/ATL::CComControlBase::DoesVerbActivate
- ATLCTL/ATL::CComControlBase::DoesVerbUIActivate
- ATLCTL/ATL::CComControlBase::DoVerbProperties
- ATLCTL/ATL::CComControlBase::FireViewChange
- ATLCTL/ATL::CComControlBase::GetAmbientAppearance
- ATLCTL/ATL::CComControlBase::GetAmbientAutoClip
- ATLCTL/ATL::CComControlBase::GetAmbientBackColor
- ATLCTL/ATL::CComControlBase::GetAmbientCharSet
- ATLCTL/ATL::CComControlBase::GetAmbientCodePage
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayAsDefault
- ATLCTL/ATL::CComControlBase::GetAmbientDisplayName
- ATLCTL/ATL::CComControlBase::GetAmbientFont
- ATLCTL/ATL::CComControlBase::GetAmbientFontDisp
- ATLCTL/ATL::CComControlBase::GetAmbientForeColor
- ATLCTL/ATL::CComControlBase::GetAmbientLocaleID
- ATLCTL/ATL::CComControlBase::GetAmbientMessageReflect
- ATLCTL/ATL::CComControlBase::GetAmbientPalette
- ATLCTL/ATL::CComControlBase::GetAmbientProperty
- ATLCTL/ATL::CComControlBase::GetAmbientRightToLeft
- ATLCTL/ATL::CComControlBase::GetAmbientScaleUnits
- ATLCTL/ATL::CComControlBase::GetAmbientShowGrabHandles
- ATLCTL/ATL::CComControlBase::GetAmbientShowHatching
- ATLCTL/ATL::CComControlBase::GetAmbientSupportsMnemonics
- ATLCTL/ATL::CComControlBase::GetAmbientTextAlign
- ATLCTL/ATL::CComControlBase::GetAmbientTopToBottom
- ATLCTL/ATL::CComControlBase::GetAmbientUIDead
- ATLCTL/ATL::CComControlBase::GetAmbientUserMode
- ATLCTL/ATL::CComControlBase::GetDirty
- ATLCTL/ATL::CComControlBase::GetZoomInfo
- ATLCTL/ATL::CComControlBase::InPlaceActivate
- ATLCTL/ATL::CComControlBase::InternalGetSite
- ATLCTL/ATL::CComControlBase::OnDraw
- ATLCTL/ATL::CComControlBase::OnDrawAdvanced
- ATLCTL/ATL::CComControlBase::OnKillFocus
- ATLCTL/ATL::CComControlBase::OnMouseActivate
- ATLCTL/ATL::CComControlBase::OnPaint
- ATLCTL/ATL::CComControlBase::OnSetFocus
- ATLCTL/ATL::CComControlBase::PreTranslateAccelerator
- ATLCTL/ATL::CComControlBase::SendOnClose
- ATLCTL/ATL::CComControlBase::SendOnDataChange
- ATLCTL/ATL::CComControlBase::SendOnRename
- ATLCTL/ATL::CComControlBase::SendOnSave
- ATLCTL/ATL::CComControlBase::SendOnViewChange
- ATLCTL/ATL::CComControlBase::SetControlFocus
- ATLCTL/ATL::CComControlBase::SetDirty
- ATLCTL/ATL::CComControlBase::m_bAutoSize
- ATLCTL/ATL::CComControlBase::m_bDrawFromNatural
- ATLCTL/ATL::CComControlBase::m_bDrawGetDataInHimetric
- ATLCTL/ATL::CComControlBase::m_bInPlaceActive
- ATLCTL/ATL::CComControlBase::m_bInPlaceSiteEx
- ATLCTL/ATL::CComControlBase::m_bNegotiatedWnd
- ATLCTL/ATL::CComControlBase::m_bRecomposeOnResize
- ATLCTL/ATL::CComControlBase::m_bRequiresSave
- ATLCTL/ATL::CComControlBase::m_bResizeNatural
- ATLCTL/ATL::CComControlBase::m_bUIActive
- ATLCTL/ATL::CComControlBase::m_bUsingWindowRgn
- ATLCTL/ATL::CComControlBase::m_bWasOnceWindowless
- ATLCTL/ATL::CComControlBase::m_bWindowOnly
- ATLCTL/ATL::CComControlBase::m_bWndLess
- ATLCTL/ATL::CComControlBase::m_hWndCD
- ATLCTL/ATL::CComControlBase::m_nFreezeEvents
- ATLCTL/ATL::CComControlBase::m_rcPos
- ATLCTL/ATL::CComControlBase::m_sizeExtent
- ATLCTL/ATL::CComControlBase::m_sizeNatural
- ATLCTL/ATL::CComControlBase::m_spAdviseSink
- ATLCTL/ATL::CComControlBase::m_spAmbientDispatch
- ATLCTL/ATL::CComControlBase::m_spClientSite
- ATLCTL/ATL::CComControlBase::m_spDataAdviseHolder
- ATLCTL/ATL::CComControlBase::m_spInPlaceSite
- ATLCTL/ATL::CComControlBase::m_spOleAdviseHolder
helpviewer_keywords:
- CComControlBase class
ms.assetid: 3d1bf022-acf2-4092-8283-ff8cee6332f3
ms.openlocfilehash: 2420e1643444e6cbbf8edff90bbd3ecb1eac8534
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320772"
---
# <a name="ccomcontrolbase-class"></a>CComControlBase-Klasse

Diese Klasse stellt Methoden zum Erstellen und Verwalten von ATL-Steuerelementen bereit.

> [!IMPORTANT]
> Diese Klasse und ihre Member können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden.

## <a name="syntax"></a>Syntax

```
class ATL_NO_VTABLE CComControlBase
```

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComControlBase::AppearanceType](#appearancetype)|Überschreiben, `m_nAppearance` wenn Ihre Bestandseigenschaft nicht vom Typ **short**ist.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComControlBase::CComControlBase](#ccomcontrolbase)|Der Konstruktor.|
|[CComControlBase::-CComControlBase](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComControlBase::ControlQueryInterface](#controlqueryinterface)|Ruft einen Zeiger auf die angeforderte Schnittstelle ab.|
|[CComControlBase::DoesVerbActivate](#doesverbactivate)|Überprüft, ob der *iVerb-Parameter,* `IOleObjectImpl::DoVerb` der von der Benutzeroberfläche des Steuerelements verwendet wird (*iVerb* entspricht OLEIVERB_UIACTIVATE), die Aktion definiert, die ausgeführt wird, wenn der Benutzer auf das Steuerelement doppelklickt (*iVerb* entspricht OLEIVERB_PRIMARY), das Steuerelement anzeigt (*iVerb* entspricht OLEIVERB_SHOW) oder das Steuerelement aktiviert (*iVerb* entspricht OLEIVERB_INPLACEACTIVATE).|
|[CComControlBase::DoesVerbUIActivate](#doesverbuiactivate)|Überprüft, ob der von `IOleObjectImpl::DoVerb` der Steuerelement-Benutzeroberfläche verwendete *iVerb-Parameter* dazu führt, dass die Benutzeroberfläche des Steuerelements TRUE aktiviert und zurückgegeben wird.|
|[CComControlBase::DoVerbProperties](#doverbproperties)|Zeigt die Eigenschaftenseiten des Steuerelements an.|
|[CComControlBase::FireViewChange](#fireviewchange)|Rufen Sie diese Methode auf, um den Container anzuweisen, das Steuerelement neu zu zeichnen, oder benachrichtigen Sie die registrierten Ratsenken, dass sich die Ansicht des Steuerelements geändert hat.|
|[CComControlBase::GetAmbientAppearance](#getambientappearance)|Ruft DISPID_AMBIENT_APPEARANCE, die aktuelle Darstellungseinstellung für das Steuerelement ab: 0 für flach und 1 für 3D.|
|[CComControlBase::GetAmbientAutoClip](#getambientautoclip)|Ruft DISPID_AMBIENT_AUTOCLIP, ein Flag, das angibt, ob der Container das automatische Zuschneiden des Steuerelementanzeigebereichs unterstützt.|
|[CComControlBase::GetAmbientBackColor](#getambientbackcolor)|Ruft DISPID_AMBIENT_BACKCOLOR, die Umgebungshintergrundfarbe für alle Steuerelemente, die vom Container definiert werden.|
|[CComControlBase::GetAmbientCharSet](#getambientcharset)|Ruft DISPID_AMBIENT_CHARSET ab, den Umgebungszeichensatz für alle Steuerelemente, der vom Container definiert wird.|
|[CComControlBase::GetAmbientCodePage](#getambientcodepage)|Ruft DISPID_AMBIENT_CODEPAGE ab, den Umgebungszeichensatz für alle Steuerelemente, der vom Container definiert wird.|
|[CComControlBase::GetAmbientDisplayAsDefault](#getambientdisplayasdefault)|Ruft DISPID_AMBIENT_DISPLAYASDEFAULT, ein Flag, das TRUE ist, wenn der Container das Steuerelement an dieser Site als Standardschaltfläche markiert hat, und daher sollte sich ein Schaltflächensteuerelement mit einem dickeren Rahmen zeichnen.|
|[CComControlBase::GetAmbientDisplayName](#getambientdisplayname)|Ruft DISPID_AMBIENT_DISPLAYNAME, den Namen, den der Container dem Steuerelement übermittelt hat.|
|[CComControlBase::GetAmbientFont](#getambientfont)|Ruft einen Zeiger auf die Umgebungsschnittstelle `IFont` des Containers ab.|
|[CComControlBase::GetAmbientFontDisp](#getambientfontdisp)|Ruft einen Zeiger auf die Umgebungsdispatchschnittstelle `IFontDisp` des Containers ab.|
|[CComControlBase::GetAmbientForeColor](#getambientforecolor)|Ruft DISPID_AMBIENT_FORECOLOR, die Umgebungsvordergrundfarbe für alle Steuerelemente, die vom Container definiert werden.|
|[CComControlBase::GetAmbientLocaleID](#getambientlocaleid)|Ruft DISPID_AMBIENT_LOCALEID, den Bezeichner der vom Container verwendeten Sprache.|
|[CComControlBase::GetAmbientMessageReflect](#getambientmessagereflect)|Ruft DISPID_AMBIENT_MESSAGEREFLECT, ein Flag ab, das angibt, ob der Container Fensternachrichten (z. B. WM_DRAWITEM) als Ereignisse empfangen möchte.|
|[CComControlBase::GetAmbientPalette](#getambientpalette)|Ruft DISPID_AMBIENT_PALETTE ab, die für den Zugriff auf die HPALETTE des Containers verwendet wird.|
|[CComControlBase::GetAmbientProperty](#getambientproperty)|Ruft die von *id*angegebene Containereigenschaft ab.|
|[CComControlBase::GetAmbientrightToleft](#getambientrighttoleft)|Ruft DISPID_AMBIENT_RIGHTTOLEFT ab, in der der Inhalt vom Container angezeigt wird.|
|[CComControlBase::GetAmbientScaleUnits](#getambientscaleunits)|Ruft DISPID_AMBIENT_SCALEUNITS, die Umgebungseinheiten des Containers (z. B. Zoll oder Zentimeter) für die Beschriftung von Anzeigen ab.|
|[CComControlBase::GetAmbientShowGrabHandles](#getambientshowgrabhandles)|Ruft DISPID_AMBIENT_SHOWGRABHANDLES, ein Flag, das angibt, ob der Container dem Steuerelement erlaubt, Greifgriffe für sich selbst anzuzeigen, wenn es aktiv ist.|
|[CComControlBase::GetAmbientShowHatching](#getambientshowhatching)|Ruft DISPID_AMBIENT_SHOWHATCHING, ein Flag, das angibt, ob der Container es dem Steuerelement ermöglicht, sich selbst mit einem Schraffurmuster anzuzeigen, wenn die Benutzeroberfläche aktiv ist.|
|[CComControlBase::GetAmbientUnterstütztMnemonics](#getambientsupportsmnemonics)|Ruft DISPID_AMBIENT_SUPPORTSMNEMONICS, ein Flag, das angibt, ob der Container Tastatur-Mnemonics unterstützt.|
|[CComControlBase::GetAmbientTextAlign](#getambienttextalign)|Ruft DISPID_AMBIENT_TEXTALIGN, die vom Container bevorzugte Textausrichtung ab: 0 für die allgemeine Ausrichtung (Zahlen rechts, Text links), 1 für die linke Ausrichtung, 2 für die Mittlere Ausrichtung und 3 für die rechte Ausrichtung.|
|[CComControlBase::GetAmbientTopToBottom](#getambienttoptobottom)|Ruft DISPID_AMBIENT_TOPTOBOTTOM ab, in der der Inhalt vom Container angezeigt wird.|
|[CComControlBase::GetAmbientUIDead](#getambientuidead)|Ruft DISPID_AMBIENT_UIDEAD ein Flag ab, das angibt, ob das Steuerelement auf Benutzeroberflächenaktionen reagieren soll.|
|[CComControlBase::GetAmbientUserMode](#getambientusermode)|Ruft DISPID_AMBIENT_USERMODE, ein Flag, das angibt, ob sich der Container im Run-Mode (TRUE) oder design-mode (FALSE) befindet.|
|[CComControlBase::GetDirty](#getdirty)|Gibt den Wert `m_bRequiresSave`des Datenmembers zurück.|
|[CComControlBase::GetZoomInfo](#getzoominfo)|Ruft die x- und y-Werte des Zählers und Nenners des Zoomfaktors für ein Steuerelement ab, das für die ortsspezifische Bearbeitung aktiviert ist.|
|[CComControlBase::InplaceActivate](#inplaceactivate)|Bewirkt, dass das Steuerelement vom inaktiven Zustand in den Zustand wechselt, den das Verb in *iVerb* angibt.|
|[CComControlBase::InternalGetSite](#internalgetsite)|Rufen Sie diese Methode auf, um die Steuerungssite nach einem Zeiger auf die identifizierte Schnittstelle abzufragen.|
|[CComControlBase::OnDraw](#ondraw)|Überschreiben Sie diese Methode, um das Steuerelement zu zeichnen.|
|[CComControlBase::OnDrawAdvanced](#ondrawadvanced)|Der `OnDrawAdvanced` Standard vorbereitet einen normalisierten Gerätekontext für das Zeichnen `OnDraw` und ruft dann die Methode der Steuerelementklasse auf.|
|[CComControlBase::OnKillFocus](#onkillfocus)|Überprüft, ob das Steuerelement aktiv ist und über eine gültige Kontrollsite verfügt, und informiert den Container dann darüber, dass das Steuerelement den Fokus verloren hat.|
|[CComControlBase::OnMouseActivate](#onmouseactivate)|Überprüft, ob sich die Benutzeroberfläche im Benutzermodus befindet, und aktiviert dann das Steuerelement.|
|[CComControlBase::OnPaint](#onpaint)|Bereitet den Container für das Malen vor, ruft den Clientbereich `OnDraw` des Steuerelements ab und ruft dann die Methode der Steuerungsklasse auf.|
|[CComControlBase::OnSetFocus](#onsetfocus)|Überprüft, ob das Steuerelement aktiv ist und über eine gültige Kontrollsite verfügt, und informiert dann den Container, dass das Steuerelement in den Fokus gerückt ist.|
|[CComControlBase::PreTranslateAccelerator](#pretranslateaccelerator)|Überschreiben Sie diese Methode, um eigene Tastaturbeschleunigerhandler bereitzustellen.|
|[CComControlBase::SendOnClose](#sendonclose)|Benachrichtigt alle beim Beratungsinhaber registrierten Beratungssenken, dass die Kontrolle geschlossen wurde.|
|[CComControlBase::SendOnDataChange](#sendondatachange)|Benachrichtigt alle beim Beratungsinhaber registrierten Beratungssenken, dass sich die Kontrolldaten geändert haben.|
|[CComControlBase::SendOnRename](#sendonrename)|Benachrichtigt alle beim Beraterhalter registrierten Beratungssenken, dass das Steuerelement einen neuen Moniker hat.|
|[CComControlBase::SendOnSave](#sendonsave)|Benachrichtigt alle beim Beratungsinhaber registrierten Beratungssenken, dass die Steuerung gespeichert wurde.|
|[CComControlBase::SendOnViewChange](#sendonviewchange)|Benachrichtigt alle registrierten Beratungssenken, dass sich die Ansicht des Steuerelements geändert hat.|
|[CComControlBase::SetControlFocus](#setcontrolfocus)|Legt den Tastaturfokus auf oder aus dem Steuerelement fest oder entfernt ihn.|
|[CComControlBase::SetDirty](#setdirty)|Legt den `m_bRequiresSave` Datenmember auf den Wert in *bDirty*fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComControlBase::m_bAutoSize](#m_bautosize)|Das Flag, das angibt, dass das Steuerelement keine andere Größe haben kann.|
|[CComControlBase::m_bDrawFromNatural](#m_bdrawfromnatural)|Flag, das `IDataObjectImpl::GetData` `CComControlBase::GetZoomInfo` angibt, dass `m_sizeNatural` und sollte `m_sizeExtent`die Steuerelementgröße von anstelle von festlegen.|
|[CComControlBase::m_bDrawGetDataInHimetric](#m_bdrawgetdatainhimetric)|Flag, das `IDataObjectImpl::GetData` angibt, dass HIMETRIC-Einheiten und nicht Pixel beim Zeichnen verwendet werden sollen.|
|[CComControlBase::m_bInPlaceActive](#m_binplaceactive)|Flag, das angibt, dass das Steuerelement aktiv ist.|
|[CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex)|Flag, das den `IOleInPlaceSiteEx` Container angibt, unterstützt die Benutzeroberfläche und OCX96-Steuerungsfunktionen, z. B. fensterlose und flimmerfreie Steuerelemente.|
|[CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd)|Flag, das angibt, ob das Steuerelement mit dem Container über die Unterstützung von OCX96-Steuerelementen (z. B. flimmerfreie und fensterlose Steuerelemente) verhandelt hat und ob das Steuerelement fensterlos oder fensterlos ist.|
|[CComControlBase::m_bRecomposeOnResize](#m_brecomposeonresize)|Flag, das angibt, dass das Steuerelement seine Präsentation neu komponieren möchte, wenn der Container die Anzeigegröße des Steuerelements ändert.|
|[CComControlBase::m_bRequiresSave](#m_brequiressave)|Flag, das angibt, dass das Steuerelement seit dem letzten Speichern geändert wurde.|
|[CComControlBase::m_bResizeNatural](#m_bresizenatural)|Flag, das angibt, dass das Steuerelement die Größe seiner natürlichen Ausdehnung (seine nicht skalierte physische Größe) ändern möchte, wenn der Container die Anzeigegröße des Steuerelements ändert.|
|[CComControlBase::m_bUIActive](#m_buiactive)|Das Flag, das die Benutzeroberfläche des Steuerelements angibt, z. B. Menüs und Symbolleisten, ist aktiv.|
|[CComControlBase::m_bUsingWindowRgn](#m_busingwindowrgn)|Flag, das angibt, dass das Steuerelement den vom Container bereitgestellten Fensterbereich verwendet.|
|[CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)|Flag, das angibt, dass das Steuerelement fensterlos war, aber jetzt möglicherweise fensterlos ist.|
|[CComControlBase::m_bWindowOnly](#m_bwindowonly)|Flag, das das Steuerelement angibt, sollte gefenstert werden, auch wenn der Container fensterlose Steuerelemente unterstützt.|
|[CComControlBase::m_bWndLess](#m_bwndless)|Flag, das angibt, dass das Steuerelement fensterlos ist.|
|[CComControlBase::m_hWndCD](#m_hwndcd)|Enthält einen Verweis auf das Fensterhandle, das dem Steuerelement zugeordnet ist.|
|[CComControlBase::m_nFreezeEvents](#m_nfreezeevents)|Eine Anzahl der Fälle, in denen der Container Ereignisse eingefroren hat (verweigert, Ereignisse zu akzeptieren), ohne dass ein zwischengeschaltetes Tauwetter von Ereignissen (Annahme von Ereignissen) erforderlich ist.|
|[CComControlBase::m_rcPos](#m_rcpos)|Die Position in Pixeln des Steuerelements, ausgedrückt in den Koordinaten des Containers.|
|[CComControlBase::m_sizeExtent](#m_sizeextent)|Die Ausdehnung der Steuerung in HIMETRIC-Einheiten (jede Einheit beträgt 0,01 Millimeter) für ein bestimmtes Display.|
|[CComControlBase::m_sizeNatural](#m_sizenatural)|Die physische Größe des Steuerelements in HIMETRIC-Einheiten (jede Einheit beträgt 0,01 Millimeter).|
|[CComControlBase::m_spAdviseSink](#m_spadvisesink)|Ein direkter Zeiger auf die beratende Verbindung auf dem Container [(IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)des Containers ).|
|[CComControlBase::m_spAmbientDispatch](#m_spambientdispatch)|Ein `CComDispatchDriver` Objekt, mit dem Sie die Eigenschaften `IDispatch` des Containers über einen Zeiger abrufen und festlegen können.|
|[CComControlBase::m_spClientSite](#m_spclientsite)|Ein Zeiger auf die Clientsite des Steuerelements innerhalb des Containers.|
|[CComControlBase::m_spDataAdviseHolder](#m_spdataadviseholder)|Stellt eine Standardmethode bereit, um beratungsgebende Verbindungen zwischen Datenobjekten und Beratungssenken zu halten.|
|[CComControlBase::m_spInPlaceSite](#m_spinplacesite)|Ein Zeiger auf den [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)oder [IOleInPlaceSiteWindowless-Schnittstellenzeiger](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) des Containers.|
|[CComControlBase::m_spOleAdviseHolder](#m_spoleadviseholder)|Stellt eine Standardimplementierung für eine Möglichkeit zum Halten von Beratungsverbindungen bereit.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse stellt Methoden zum Erstellen und Verwalten von ATL-Steuerelementen bereit. [Die CComControl-Klasse](../../atl/reference/ccomcontrol-class.md) `CComControlBase`leitet sich von ab. Wenn Sie ein Standardsteuerelement oder DHTML-Steuerelement mit dem ATL-Steuerelement-Assistenten `CComControlBase`erstellen, leitet der Assistent Ihre Klasse automatisch von ab.

Weitere Informationen zum Erstellen eines Steuerelements finden Sie im [ATL-Tutorial](../../atl/active-template-library-atl-tutorial.md). Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlctl.h

## <a name="ccomcontrolbaseappearancetype"></a><a name="appearancetype"></a>CComControlBase::AppearanceType

Überschreiben, `m_nAppearance` wenn Ihre Bestandseigenschaft nicht vom Typ **short**ist.

```
typedef short AppearanceType;
```

### <a name="remarks"></a>Bemerkungen

Der ATL-Steuerungs-Assistent fügt `m_nAppearance` die Bestandseigenschaft vom Typ short hinzu. Überschreiben, `AppearanceType` wenn Sie einen anderen Datentyp verwenden.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="ccomcontrolbase"></a>CComControlBase::CComControlBase

Der Konstruktor.

```
CComControlBase(HWND& h);
```

### <a name="parameters"></a>Parameter

*H*<br/>
Das Handle für das Fenster, das dem Steuerelement zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Initialisiert die Steuerelementgröße auf 5080X5080 HIMETRIC-Einheiten (2 "X2") und initialisiert die `CComControlBase` Datenmemberwerte auf NULL oder FALSE.

## <a name="ccomcontrolbaseccomcontrolbase"></a><a name="dtor"></a>CComControlBase::-CComControlBase

Der Destruktor.

```
~CComControlBase();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Steuerelement in `~CComControlBase` einem Fenster angezeigt wird, zerstört es, indem [es DestroyWindow aufruft.](/windows/win32/api/winuser/nf-winuser-destroywindow)

## <a name="ccomcontrolbasecontrolqueryinterface"></a><a name="controlqueryinterface"></a>CComControlBase::ControlQueryInterface

Ruft einen Zeiger auf die angeforderte Schnittstelle ab.

```
virtual HRESULT ControlQueryInterface(const IID& iid,
    void** ppv);
```

### <a name="parameters"></a>Parameter

*Iid*<br/>
Die GUID der angeforderten Schnittstelle.

*Ppv*<br/>
Ein Zeiger auf den Schnittstellenzeiger, der von *iid*oder NULL identifiziert wird, wenn die Schnittstelle nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Behandelt nur Schnittstellen in der COM-Map-Tabelle.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#15](../../atl/codesnippet/cpp/ccomcontrolbase-class_1.cpp)]

## <a name="ccomcontrolbasedoesverbactivate"></a><a name="doesverbactivate"></a>CComControlBase::DoesVerbActivate

Überprüft, ob der *iVerb-Parameter,* `IOleObjectImpl::DoVerb` der von der Benutzeroberfläche des Steuerelements verwendet wird (*iVerb* entspricht OLEIVERB_UIACTIVATE), die Aktion definiert, die ausgeführt wird, wenn der Benutzer auf das Steuerelement doppelklickt (*iVerb* entspricht OLEIVERB_PRIMARY), das Steuerelement anzeigt (*iVerb* entspricht OLEIVERB_SHOW) oder das Steuerelement aktiviert (*iVerb* entspricht OLEIVERB_INPLACEACTIVATE).

```
BOOL DoesVerbActivate(LONG iVerb);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Wert, der die Aktion `DoVerb`angibt, die von ausgeführt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn *iVerb* OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW oder OLEIVERB_INPLACEACTIVATE entspricht. Andernfalls wird FALSE zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode überschreiben, um Ein eigenes Aktivierungsverb zu definieren.

## <a name="ccomcontrolbasedoesverbuiactivate"></a><a name="doesverbuiactivate"></a>CComControlBase::DoesVerbUIActivate

Überprüft, ob der von `IOleObjectImpl::DoVerb` der Steuerelement-Benutzeroberfläche verwendete *iVerb-Parameter* dazu führt, dass die Benutzeroberfläche des Steuerelements TRUE aktiviert und zurückgegeben wird.

```
BOOL DoesVerbUIActivate(LONG iVerb);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Wert, der die Aktion `DoVerb`angibt, die von ausgeführt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn *iVerb* OLEIVERB_UIACTIVATE, OLEIVERB_PRIMARY, OLEIVERB_SHOW oder OLEIVERB_INPLACEACTIVATE entspricht. Andernfalls gibt die Methode FALSE zurück.

## <a name="ccomcontrolbasedoverbproperties"></a><a name="doverbproperties"></a>CComControlBase::DoVerbProperties

Zeigt die Eigenschaftenseiten des Steuerelements an.

```
HRESULT DoVerbProperties(LPCRECT /* prcPosRect */, HWND hwndParent);
```

### <a name="parameters"></a>Parameter

*prcPosRec*<br/>
Reserviert.

*hwndParent*<br/>
Handle des Fensters, das das Steuerelement enthält.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#19](../../atl/codesnippet/cpp/ccomcontrolbase-class_2.cpp)]

[!code-cpp[NVC_ATL_COM#20](../../atl/codesnippet/cpp/ccomcontrolbase-class_3.h)]

## <a name="ccomcontrolbasefireviewchange"></a><a name="fireviewchange"></a>CComControlBase::FireViewChange

Rufen Sie diese Methode auf, um den Container anzuweisen, das Steuerelement neu zu zeichnen, oder benachrichtigen Sie die registrierten Ratsenken, dass sich die Ansicht des Steuerelements geändert hat.

```
HRESULT FireViewChange();
```

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Wenn das Steuerelement aktiv ist (der Steuerelementklassendatenmember [CComControlBase::m_bInPlaceActive](#m_binplaceactive) ist TRUE), benachrichtigt der Container, dass Sie das gesamte Steuerelement neu zeichnen möchten. Wenn das Steuerelement inaktiv ist, benachrichtigt die registrierten Ratssenken des Steuerelements (über das Steuerelementklassendatenmember [CComControlBase::m_spAdviseSink](#m_spadvisesink)), dass sich die Ansicht des Steuerelements geändert hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#21](../../atl/codesnippet/cpp/ccomcontrolbase-class_4.cpp)]

## <a name="ccomcontrolbasegetambientappearance"></a><a name="getambientappearance"></a>CComControlBase::GetAmbientAppearance

Ruft DISPID_AMBIENT_APPEARANCE, die aktuelle Darstellungseinstellung für das Steuerelement ab: 0 für flach und 1 für 3D.

```
HRESULT GetAmbientAppearance(short& nAppearance);
```

### <a name="parameters"></a>Parameter

*nErscheinung*<br/>
Die Unterkunft DISPID_AMBIENT_APPEARANCE.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_COM#22](../../atl/codesnippet/cpp/ccomcontrolbase-class_5.h)]

## <a name="ccomcontrolbasegetambientautoclip"></a><a name="getambientautoclip"></a>CComControlBase::GetAmbientAutoClip

Ruft DISPID_AMBIENT_AUTOCLIP, ein Flag, das angibt, ob der Container das automatische Zuschneiden des Steuerelementanzeigebereichs unterstützt.

```
HRESULT GetAmbientAutoClip(BOOL& bAutoClip);
```

### <a name="parameters"></a>Parameter

*bAutoClip*<br/>
Die Unterkunft DISPID_AMBIENT_AUTOCLIP.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientbackcolor"></a><a name="getambientbackcolor"></a>CComControlBase::GetAmbientBackColor

Ruft DISPID_AMBIENT_BACKCOLOR, die Umgebungshintergrundfarbe für alle Steuerelemente, die vom Container definiert werden.

```
HRESULT GetAmbientBackColor(OLE_COLOR& BackColor);
```

### <a name="parameters"></a>Parameter

*Backcolor*<br/>
Die Unterkunft DISPID_AMBIENT_BACKCOLOR.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientcharset"></a><a name="getambientcharset"></a>CComControlBase::GetAmbientCharSet

Ruft DISPID_AMBIENT_CHARSET ab, den Umgebungszeichensatz für alle Steuerelemente, der vom Container definiert wird.

```
HRESULT GetAmbientCharSet(BSTR& bstrCharSet);
```

### <a name="parameters"></a>Parameter

*bstrCharSet*<br/>
Die Unterkunft DISPID_AMBIENT_CHARSET.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="ccomcontrolbasegetambientcodepage"></a><a name="getambientcodepage"></a>CComControlBase::GetAmbientCodePage

Ruft DISPID_AMBIENT_CODEPAGE, die Umgebungscodepage für alle Steuerelemente, die vom Container definiert werden.

```
HRESULT GetAmbientCodePage(ULONG& ulCodePage);
```

### <a name="parameters"></a>Parameter

*ulCodePage*<br/>
Die Unterkunft DISPID_AMBIENT_CODEPAGE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="ccomcontrolbasegetambientdisplayasdefault"></a><a name="getambientdisplayasdefault"></a>CComControlBase::GetAmbientDisplayAsDefault

Ruft DISPID_AMBIENT_DISPLAYASDEFAULT, ein Flag, das TRUE ist, wenn der Container das Steuerelement an dieser Site als Standardschaltfläche markiert hat, und daher sollte sich ein Schaltflächensteuerelement mit einem dickeren Rahmen zeichnen.

```
HRESULT GetAmbientDisplayAsDefault(BOOL& bDisplayAsDefault);
```

### <a name="parameters"></a>Parameter

*bDisplayAsDefault*<br/>
Die Unterkunft DISPID_AMBIENT_DISPLAYASDEFAULT.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientdisplayname"></a><a name="getambientdisplayname"></a>CComControlBase::GetAmbientDisplayName

Ruft DISPID_AMBIENT_DISPLAYNAME, den Namen, den der Container dem Steuerelement übermittelt hat.

```
HRESULT GetAmbientDisplayName(BSTR& bstrDisplayName);
```

### <a name="parameters"></a>Parameter

*bstrDisplayName*<br/>
Die Unterkunft DISPID_AMBIENT_DISPLAYNAME.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientfont"></a><a name="getambientfont"></a>CComControlBase::GetAmbientFont

Ruft einen Zeiger auf die Umgebungsschnittstelle `IFont` des Containers ab.

```
HRESULT GetAmbientFont(IFont** ppFont);
```

### <a name="parameters"></a>Parameter

*ppFont*<br/>
Ein Zeiger auf die [Umgebungs-IFont-Schnittstelle](/windows/win32/api/ocidl/nn-ocidl-ifont) des Containers.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Wenn die Eigenschaft NULL ist, ist der Zeiger NULL. Wenn der Zeiger nicht NULL ist, muss der Aufrufer den Zeiger freigeben.

## <a name="ccomcontrolbasegetambientfontdisp"></a><a name="getambientfontdisp"></a>CComControlBase::GetAmbientFontDisp

Ruft einen Zeiger auf die Umgebungsdispatchschnittstelle `IFontDisp` des Containers ab.

```
HRESULT GetAmbientFontDisp(IFontDisp** ppFont);
```

### <a name="parameters"></a>Parameter

*ppFont*<br/>
Ein Zeiger auf die [Umgebungs-IFontDisp-Dispatchschnittstelle](/windows/win32/api/ocidl/nn-ocidl-ifontdisp) des Containers.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die Eigenschaft NULL ist, ist der Zeiger NULL. Wenn der Zeiger nicht NULL ist, muss der Aufrufer den Zeiger freigeben.

## <a name="ccomcontrolbasegetambientforecolor"></a><a name="getambientforecolor"></a>CComControlBase::GetAmbientForeColor

Ruft DISPID_AMBIENT_FORECOLOR, die Umgebungsvordergrundfarbe für alle Steuerelemente, die vom Container definiert werden.

```
HRESULT GetAmbientForeColor(OLE_COLOR& ForeColor);
```

### <a name="parameters"></a>Parameter

*Forecolor*<br/>
Die Unterkunft DISPID_AMBIENT_FORECOLOR.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientlocaleid"></a><a name="getambientlocaleid"></a>CComControlBase::GetAmbientLocaleID

Ruft DISPID_AMBIENT_LOCALEID, den Bezeichner der vom Container verwendeten Sprache.

```
HRESULT GetAmbientLocaleID(LCID& lcid);
```

### <a name="parameters"></a>Parameter

*lcid*<br/>
Die Unterkunft DISPID_AMBIENT_LOCALEID.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Das Steuerelement kann diesen Bezeichner verwenden, um seine Benutzeroberfläche an verschiedene Sprachen anzupassen.

## <a name="ccomcontrolbasegetambientmessagereflect"></a><a name="getambientmessagereflect"></a>CComControlBase::GetAmbientMessageReflect

Ruft DISPID_AMBIENT_MESSAGEREFLECT, ein Flag, das angibt, ob der `WM_DRAWITEM`Container Fensternachrichten (z. B. ) als Ereignisse empfangen möchte.

```
HRESULT GetAmbientMessageReflect(BOOL& bMessageReflect);
```

### <a name="parameters"></a>Parameter

*bMessageReflect*<br/>
Die Unterkunft DISPID_AMBIENT_MESSAGEREFLECT.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientpalette"></a><a name="getambientpalette"></a>CComControlBase::GetAmbientPalette

Ruft DISPID_AMBIENT_PALETTE ab, die für den Zugriff auf die HPALETTE des Containers verwendet wird.

```
HRESULT GetAmbientPalette(HPALETTE& hPalette);
```

### <a name="parameters"></a>Parameter

*hPalette*<br/>
Die Unterkunft DISPID_AMBIENT_PALETTE.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientproperty"></a><a name="getambientproperty"></a>CComControlBase::GetAmbientProperty

Ruft die container-Eigenschaft ab, die von *dispid*angegeben wurde.

```
HRESULT GetAmbientProperty(DISPID dispid, VARIANT& var);
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Bezeichner der container-Eigenschaft, die abgerufen werden soll.

*var*<br/>
Variable, um die Eigenschaft zu empfangen.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

ATL hat eine Reihe von Hilfsfunktionen bereitgestellt, um bestimmte Eigenschaften abzurufen, z. B. [CComControlBase::GetAmbientBackColor](#getambientbackcolor). Wenn keine geeignete Methode verfügbar `GetAmbientProperty`ist, verwenden Sie .

## <a name="ccomcontrolbasegetambientrighttoleft"></a><a name="getambientrighttoleft"></a>CComControlBase::GetAmbientrightToleft

Ruft DISPID_AMBIENT_RIGHTTOLEFT ab, in der der Inhalt vom Container angezeigt wird.

```
HRESULT GetAmbientRightToLeft(BOOL& bRightToLeft);
```

### <a name="parameters"></a>Parameter

*bRightToLeft*<br/>
Die Unterkunft DISPID_AMBIENT_RIGHTTOLEFT. Legen Sie TRUE fest, wenn Der Inhalt von rechts nach links angezeigt wird, FALSE, wenn er von links nach rechts angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="ccomcontrolbasegetambientscaleunits"></a><a name="getambientscaleunits"></a>CComControlBase::GetAmbientScaleUnits

Ruft DISPID_AMBIENT_SCALEUNITS, die Umgebungseinheiten des Containers (z. B. Zoll oder Zentimeter) für die Beschriftung von Anzeigen ab.

```
HRESULT GetAmbientScaleUnits(BSTR& bstrScaleUnits);
```

### <a name="parameters"></a>Parameter

*bstrScaleUnits*<br/>
Die Unterkunft DISPID_AMBIENT_SCALEUNITS.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientshowgrabhandles"></a><a name="getambientshowgrabhandles"></a>CComControlBase::GetAmbientShowGrabHandles

Ruft DISPID_AMBIENT_SHOWGRABHANDLES, ein Flag, das angibt, ob der Container dem Steuerelement erlaubt, Greifgriffe für sich selbst anzuzeigen, wenn es aktiv ist.

```
HRESULT GetAmbientShowGrabHandles(BOOL& bShowGrabHandles);
```

### <a name="parameters"></a>Parameter

*bShowGrabHandles*<br/>
Die Unterkunft DISPID_AMBIENT_SHOWGRABHANDLES.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientshowhatching"></a><a name="getambientshowhatching"></a>CComControlBase::GetAmbientShowHatching

Ruft DISPID_AMBIENT_SHOWHATCHING, ein Flag, das angibt, ob der Container es dem Steuerelement ermöglicht, sich selbst mit einem Schraffurmuster anzuzeigen, wenn die Benutzeroberfläche des Steuerelements aktiv ist.

```
HRESULT GetAmbientShowHatching(BOOL& bShowHatching);
```

### <a name="parameters"></a>Parameter

*bShowHatching*<br/>
Die Unterkunft DISPID_AMBIENT_SHOWHATCHING.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambientsupportsmnemonics"></a><a name="getambientsupportsmnemonics"></a>CComControlBase::GetAmbientUnterstütztMnemonics

Ruft DISPID_AMBIENT_SUPPORTSMNEMONICS, ein Flag, das angibt, ob der Container Tastatur-Mnemonics unterstützt.

```
HRESULT GetAmbientSupportsMnemonics(BOOL& bSupportsMnemonics);
```

### <a name="parameters"></a>Parameter

*bSupportsMnemonics*<br/>
Die Unterkunft DISPID_AMBIENT_SUPPORTSMNEMONICS.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambienttextalign"></a><a name="getambienttextalign"></a>CComControlBase::GetAmbientTextAlign

Ruft DISPID_AMBIENT_TEXTALIGN, die vom Container bevorzugte Textausrichtung ab: 0 für die allgemeine Ausrichtung (Zahlen rechts, Text links), 1 für die linke Ausrichtung, 2 für die Mittlere Ausrichtung und 3 für die rechte Ausrichtung.

```
HRESULT GetAmbientTextAlign(short& nTextAlign);
```

### <a name="parameters"></a>Parameter

*nTextAlign*<br/>
Die Unterkunft DISPID_AMBIENT_TEXTALIGN.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetambienttoptobottom"></a><a name="getambienttoptobottom"></a>CComControlBase::GetAmbientTopToBottom

Ruft DISPID_AMBIENT_TOPTOBOTTOM ab, in der der Inhalt vom Container angezeigt wird.

```
HRESULT GetAmbientTopToBottom(BOOL& bTopToBottom);
```

### <a name="parameters"></a>Parameter

*bTopToBottom*<br/>
Die Unterkunft DISPID_AMBIENT_TOPTOBOTTOM. Legen Sie TRUE fest, wenn Text von oben nach unten angezeigt wird, FALSE, wenn er von unten nach oben angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="ccomcontrolbasegetambientuidead"></a><a name="getambientuidead"></a>CComControlBase::GetAmbientUIDead

Ruft DISPID_AMBIENT_UIDEAD ein Flag ab, das angibt, ob das Steuerelement auf Benutzeroberflächenaktionen reagieren soll.

```
HRESULT GetAmbientUIDead(BOOL& bUIDead);
```

### <a name="parameters"></a>Parameter

*bUIDead*<br/>
Die Unterkunft DISPID_AMBIENT_UIDEAD.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Wenn TRUE, sollte das Steuerelement nicht reagieren. Dieses Flag gilt unabhängig vom DISPID_AMBIENT_USERMODE-Flag. Siehe [CComControlBase::GetAmbientUserMode](#getambientusermode).

## <a name="ccomcontrolbasegetambientusermode"></a><a name="getambientusermode"></a>CComControlBase::GetAmbientUserMode

Ruft DISPID_AMBIENT_USERMODE, ein Flag, das angibt, ob sich der Container im Run-Mode (TRUE) oder design-mode (FALSE) befindet.

```
HRESULT GetAmbientUserMode(BOOL& bUserMode);
```

### <a name="parameters"></a>Parameter

*bUserMode*<br/>
Die Unterkunft DISPID_AMBIENT_USERMODE.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

## <a name="ccomcontrolbasegetdirty"></a><a name="getdirty"></a>CComControlBase::GetDirty

Gibt den Wert `m_bRequiresSave`des Datenmembers zurück.

```
BOOL GetDirty();
```

### <a name="return-value"></a>Rückgabewert

Gibt den Wert des Datenmembers [m_bRequiresSave](#m_brequiressave)zurück.

### <a name="remarks"></a>Bemerkungen

Dieser Wert wird mit [CComControlBase::SetDirty](#setdirty)festgelegt.

## <a name="ccomcontrolbasegetzoominfo"></a><a name="getzoominfo"></a>CComControlBase::GetZoomInfo

Ruft die x- und y-Werte des Zählers und Nenners des Zoomfaktors für ein Steuerelement ab, das für die ortsspezifische Bearbeitung aktiviert ist.

```
void GetZoomInfo(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parameter

*di*<br/>
Die Struktur, die den Zähler und den Nenner des Zoomfaktors hält. Weitere Informationen finden Sie [unter ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md).

### <a name="remarks"></a>Bemerkungen

Der Zoomfaktor ist der Anteil der natürlichen Größe des Steuerelements an seiner aktuellen Ausdehnung.

## <a name="ccomcontrolbaseinplaceactivate"></a><a name="inplaceactivate"></a>CComControlBase::InplaceActivate

Bewirkt, dass das Steuerelement vom inaktiven Zustand in den Zustand wechselt, den das Verb in *iVerb* angibt.

```
HRESULT InPlaceActivate(LONG iVerb, const RECT* prcPosRect = NULL);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Wert, der die Aktion angibt, die von [IOleObjectImpl::DoVerb](../../atl/reference/ioleobjectimpl-class.md#doverb)ausgeführt werden soll.

*prcPosRect*<br/>
Zeiger auf die Position des In-Place-Steuerelements.

### <a name="return-value"></a>Rückgabewert

Einer der Standard-HRESULT-Werte.

### <a name="remarks"></a>Bemerkungen

Vor der Aktivierung überprüft diese Methode, ob das Steuerelement über eine Clientsite verfügt, überprüft, wie viel des Steuerelements sichtbar ist, und ruft den Speicherort des Steuerelements im übergeordneten Fenster ab. Nachdem das Steuerelement aktiviert wurde, aktiviert diese Methode die Benutzeroberfläche des Steuerelements und weist den Container an, das Steuerelement sichtbar zu machen.

Diese Methode ruft `IOleInPlaceSite`auch `IOleInPlaceSiteEx`einen `IOleInPlaceSiteWindowless` , oder Schnittstellenzeiger für das Steuerelement ab und speichert ihn im Datenmember [CComControlBase::m_spInPlaceSite](#m_spinplacesite)der Steuerklasse. Die Steuerelementklassendatenmember [CComControlBase::m_bInPlaceSiteEx](#m_binplacesiteex), [CComControlBase::m_bWndLess](#m_bwndless), [CComControlBase::m_bWasOnceWindowless](#m_bwasoncewindowless)und [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) sind entsprechend auf true festgelegt.

## <a name="ccomcontrolbaseinternalgetsite"></a><a name="internalgetsite"></a>CComControlBase::InternalGetSite

Rufen Sie diese Methode auf, um die Steuerungssite nach einem Zeiger auf die identifizierte Schnittstelle abzufragen.

```
HRESULT InternalGetSite(REFIID riid, void** ppUnkSite);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Die IID des Schnittstellenzeigers, der in *ppUnkSite*zurückgegeben werden soll.

*ppUnkSite*<br/>
Adresse der Zeigervariablen, die den in *riid*angeforderten Schnittstellenzeiger empfängt.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die Site die in *riid*angeforderte Schnittstelle unterstützt, wird der Zeiger über *ppUnkSite*zurückgegeben. Andernfalls wird *ppUnkSite* auf NULL gesetzt.

## <a name="ccomcontrolbasem_bautosize"></a><a name="m_bautosize"></a>CComControlBase::m_bAutoSize

Das Flag, das angibt, dass das Steuerelement keine andere Größe haben kann.

```
unsigned m_bAutoSize:1;
```

### <a name="remarks"></a>Bemerkungen

Dieses Flag wird `IOleObjectImpl::SetExtent` von überprüft und bewirkt, dass die Funktion E_FAIL zurückgibt, wenn TRUE.

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Wenn Sie die Option **Auto Größe** auf der Registerkarte [Bestandseigenschaften](../../atl/reference/stock-properties-atl-control-wizard.md) des ATL-Steuerelement-Assistenten hinzufügen, erstellt der Assistent automatisch dieses Datenelement in Ihrer Steuerelementklasse, erstellt Put-and-Ab-Methoden für die Eigenschaft und unterstützt [IPropertyNotifySink,](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) um den Container automatisch zu benachrichtigen, wenn sich die Eigenschaft ändert.

## <a name="ccomcontrolbasem_bdrawfromnatural"></a><a name="m_bdrawfromnatural"></a>CComControlBase::m_bDrawFromNatural

Flag, das `IDataObjectImpl::GetData` `CComControlBase::GetZoomInfo` angibt, dass `m_sizeNatural` und sollte `m_sizeExtent`die Steuerelementgröße von anstelle von festlegen.

```
unsigned m_bDrawFromNatural:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_bdrawgetdatainhimetric"></a><a name="m_bdrawgetdatainhimetric"></a>CComControlBase::m_bDrawGetDataInHimetric

Flag, das `IDataObjectImpl::GetData` angibt, dass HIMETRIC-Einheiten und nicht Pixel beim Zeichnen verwendet werden sollen.

```
unsigned m_bDrawGetDataInHimetric:1;
```

### <a name="remarks"></a>Bemerkungen

Jede logische HIMETRIC-Einheit beträgt 0,01 Millimeter.

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_binplaceactive"></a><a name="m_binplaceactive"></a>CComControlBase::m_bInPlaceActive

Flag, das angibt, dass das Steuerelement aktiv ist.

```
unsigned m_bInPlaceActive:1;
```

### <a name="remarks"></a>Bemerkungen

Dies bedeutet, dass das Steuerelement sichtbar ist und sein Fenster, falls vorhanden, sichtbar ist, aber seine Menüs und Symbolleisten sind möglicherweise nicht aktiv. Das `m_bUIActive` Flag gibt an, dass die Benutzeroberfläche des Steuerelements, z. B. Menüs, ebenfalls aktiv ist.

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_binplacesiteex"></a><a name="m_binplacesiteex"></a>CComControlBase::m_bInPlaceSiteEx

Flag, das den `IOleInPlaceSiteEx` Container angibt, unterstützt die Benutzeroberfläche und OCX96-Steuerungsfunktionen, z. B. fensterlose und flimmerfreie Steuerelemente.

```
unsigned m_bInPlaceSiteEx:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Der `m_spInPlaceSite` Datenmember verweist abhängig vom Wert der `m_bWndLess` und-Flags `m_bInPlaceSiteEx` auf eine [IOleInPlaceSite,](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite) [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)oder [IOleInPlaceSiteWindowless-Schnittstelle.](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) (Das Datenmember `m_bNegotiatedWnd` muss TRUE `m_spInPlaceSite` sein, damit der Zeiger gültig ist.)

Wenn `m_bWndLess` FALSE `m_bInPlaceSiteEx` und TRUE `m_spInPlaceSite` ist, ist ein `IOleInPlaceSiteEx` Schnittstellenzeiger. Eine Tabelle mit der Beziehung zwischen diesen drei Datenmembern [finden Sie in m_spInPlaceSite.](#m_spinplacesite)

## <a name="ccomcontrolbasem_bnegotiatedwnd"></a><a name="m_bnegotiatedwnd"></a>CComControlBase::m_bNegotiatedWnd

Flag, das angibt, ob das Steuerelement mit dem Container über die Unterstützung von OCX96-Steuerelementen (z. B. flimmerfreie und fensterlose Steuerelemente) verhandelt hat und ob das Steuerelement fensterlos oder fensterlos ist.

```
unsigned m_bNegotiatedWnd:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Das `m_bNegotiatedWnd` Flag muss TRUE `m_spInPlaceSite` sein, damit der Zeiger gültig ist.

## <a name="ccomcontrolbasem_brecomposeonresize"></a><a name="m_brecomposeonresize"></a>CComControlBase::m_bRecomposeOnResize

Flag, das angibt, dass das Steuerelement seine Präsentation neu komponieren möchte, wenn der Container die Anzeigegröße des Steuerelements ändert.

```
unsigned m_bRecomposeOnResize:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Dieses Flag wird von [IOleObjectImpl::SetExtent](../../atl/reference/ioleobjectimpl-class.md#setextent) aktiviert `SetExtent` und benachrichtigt, falls TRUE, den Container mit Ansichtsänderungen. Wenn dieses Flag gesetzt ist, sollte auch das OLEMISC_RECOMPOSEONRESIZE Bit in der [OLEMISC-Enumeration](/windows/win32/api/oleidl/ne-oleidl-olemisc) festgelegt werden.

## <a name="ccomcontrolbasem_brequiressave"></a><a name="m_brequiressave"></a>CComControlBase::m_bRequiresSave

Flag, das angibt, dass das Steuerelement seit dem letzten Speichern geändert wurde.

```
unsigned m_bRequiresSave:1;
```

### <a name="remarks"></a>Bemerkungen

Der Wert `m_bRequiresSave` von kann mit [CComControlBase::SetDirty](#setdirty) eingestellt und mit [CComControlBase::GetDirty](#getdirty)abgerufen werden.

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_bresizenatural"></a><a name="m_bresizenatural"></a>CComControlBase::m_bResizeNatural

Flag, das angibt, dass das Steuerelement die Größe seiner natürlichen Ausdehnung (seine nicht skalierte physische Größe) ändern möchte, wenn der Container die Anzeigegröße des Steuerelements ändert.

```
unsigned m_bResizeNatural:1;
```

### <a name="remarks"></a>Bemerkungen

Dieses Flag wird `IOleObjectImpl::SetExtent` von überprüft, und wenn `SetExtent` TRUE, `m_sizeNatural`wird die übergebene Größe der zugewiesen.

Die übergebene `SetExtent` Größe wird `m_sizeExtent`immer dem zugewiesen, unabhängig vom Wert von `m_bResizeNatural`.

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_buiactive"></a><a name="m_buiactive"></a>CComControlBase::m_bUIActive

Das Flag, das die Benutzeroberfläche des Steuerelements angibt, z. B. Menüs und Symbolleisten, ist aktiv.

```
unsigned m_bUIActive:1;
```

### <a name="remarks"></a>Bemerkungen

Das `m_bInPlaceActive` Flag gibt an, dass das Steuerelement aktiv ist, nicht jedoch, dass seine Benutzeroberfläche aktiv ist.

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_busingwindowrgn"></a><a name="m_busingwindowrgn"></a>CComControlBase::m_bUsingWindowRgn

Flag, das angibt, dass das Steuerelement den vom Container bereitgestellten Fensterbereich verwendet.

```
unsigned m_bUsingWindowRgn:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_bwasoncewindowless"></a><a name="m_bwasoncewindowless"></a>CComControlBase::m_bWasOnceWindowless

Flag, das angibt, dass das Steuerelement fensterlos war, aber jetzt möglicherweise fensterlos ist.

```
unsigned m_bWasOnceWindowless:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_bwindowonly"></a><a name="m_bwindowonly"></a>CComControlBase::m_bWindowOnly

Flag, das das Steuerelement angibt, sollte gefenstert werden, auch wenn der Container fensterlose Steuerelemente unterstützt.

```
unsigned m_bWindowOnly:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_bwndless"></a><a name="m_bwndless"></a>CComControlBase::m_bWndLess

Flag, das angibt, dass das Steuerelement fensterlos ist.

```
unsigned m_bWndLess:1;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Der Datenmember `m_spInPlaceSite` verweist auf eine [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)- [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)oder [IOleInPlaceSiteWindowless-Schnittstelle,](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) abhängig vom Wert der `m_bWndLess` und [CComControlBase::m_bInPlaceSiteEx-Flags.](#m_binplacesiteex) (Das Datenelement [CComControlBase::m_bNegotiatedWnd](#m_bnegotiatedwnd) muss TRUE sein, damit der [CComControlBase::m_spInPlaceSite](#m_spinplacesite) Zeiger gültig ist.)

Wenn `m_bWndLess` true `m_spInPlaceSite` ist, `IOleInPlaceSiteWindowless` ist ein Schnittstellenzeiger. Eine Tabelle mit der vollständigen Beziehung zwischen diesen Datenmembern finden Sie unter [CComControlBase::m_spInPlaceSite.](#m_spinplacesite)

## <a name="ccomcontrolbasem_hwndcd"></a><a name="m_hwndcd"></a>CComControlBase::m_hWndCD

Enthält einen Verweis auf das Fensterhandle, das dem Steuerelement zugeordnet ist.

```
HWND& m_hWndCD;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_nfreezeevents"></a><a name="m_nfreezeevents"></a>CComControlBase::m_nFreezeEvents

Eine Anzahl der Fälle, in denen der Container Ereignisse eingefroren hat (verweigert, Ereignisse zu akzeptieren), ohne dass ein zwischengeschaltetes Tauwetter von Ereignissen (Annahme von Ereignissen) erforderlich ist.

```
short m_nFreezeEvents;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_rcpos"></a><a name="m_rcpos"></a>CComControlBase::m_rcPos

Die Position in Pixeln des Steuerelements, ausgedrückt in den Koordinaten des Containers.

```
RECT m_rcPos;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_sizeextent"></a><a name="m_sizeextent"></a>CComControlBase::m_sizeExtent

Die Ausdehnung der Steuerung in HIMETRIC-Einheiten (jede Einheit beträgt 0,01 Millimeter) für ein bestimmtes Display.

```
SIZE m_sizeExtent;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Diese Größe wird durch das Display skaliert. Die physische Größe des Steuerelements `m_sizeNatural` wird im Datenmember angegeben und festgelegt.

Sie können die Größe mit der globalen Funktion [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)in Pixel konvertieren.

## <a name="ccomcontrolbasem_sizenatural"></a><a name="m_sizenatural"></a>CComControlBase::m_sizeNatural

Die physische Größe des Steuerelements in HIMETRIC-Einheiten (jede Einheit beträgt 0,01 Millimeter).

```
SIZE m_sizeNatural;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Diese Größe ist festgelegt, `m_sizeExtent` während die Größe in durch die Anzeige skaliert wird.

Sie können die Größe mit der globalen Funktion [AtlHiMetricToPixel](pixel-himetric-conversion-global-functions.md#atlhimetrictopixel)in Pixel konvertieren.

## <a name="ccomcontrolbasem_spadvisesink"></a><a name="m_spadvisesink"></a>CComControlBase::m_spAdviseSink

Ein direkter Zeiger auf die beratende Verbindung auf dem Container [(IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink)des Containers ).

```
CComPtr<IAdviseSink>
    m_spAdviseSink;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_spambientdispatch"></a><a name="m_spambientdispatch"></a>CComControlBase::m_spAmbientDispatch

Ein `CComDispatchDriver` Objekt, mit dem Sie die Eigenschaften `IDispatch` eines Objekts über einen Zeiger abrufen und festlegen können.

```
CComDispatchDriver m_spAmbientDispatch;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_spclientsite"></a><a name="m_spclientsite"></a>CComControlBase::m_spClientSite

Ein Zeiger auf die Clientsite des Steuerelements innerhalb des Containers.

```
CComPtr<IOleClientSite>
    m_spClientSite;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

## <a name="ccomcontrolbasem_spdataadviseholder"></a><a name="m_spdataadviseholder"></a>CComControlBase::m_spDataAdviseHolder

Stellt eine Standardmethode bereit, um beratungsgebende Verbindungen zwischen Datenobjekten und Beratungssenken zu halten.

```
CComPtr<IDataAdviseHolder>
    m_spDataAdviseHolder;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Ein Datenobjekt ist ein Steuerelement, das Daten übertragen kann und [das IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)implementiert, dessen Methoden das Format und das Übertragungsmedium der Daten angeben.

Die `m_spDataAdviseHolder` Schnittstelle implementiert die Methoden [IDataObject::DAdvise](/windows/win32/api/objidl/nf-objidl-idataobject-dadvise) und [IDataObject::DUnadvise,](/windows/win32/api/objidl/nf-objidl-idataobject-dunadvise) um beratungsfreundliche Verbindungen zum Container einzurichten und zu löschen. Der Container des Steuerelements muss eine Beratungssenke implementieren, indem er die [IAdviseSink-Schnittstelle](/windows/win32/api/objidl/nn-objidl-iadvisesink) unterstützt.

## <a name="ccomcontrolbasem_spinplacesite"></a><a name="m_spinplacesite"></a>CComControlBase::m_spInPlaceSite

Ein Zeiger auf den [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite), [IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)oder [IOleInPlaceSiteWindowless-Schnittstellenzeiger](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless) des Containers.

```
CComPtr<IOleInPlaceSiteWindowless>
    m_spInPlaceSite;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Der `m_spInPlaceSite` Zeiger ist nur gültig, wenn das [m_bNegotiatedWnd-Flag](#m_bnegotiatedwnd) TRUE ist.

Die folgende Tabelle `m_spInPlaceSite` zeigt, wie der Zeigertyp von den [m_bWndLess](#m_bwndless) und [m_bInPlaceSiteEx](#m_binplacesiteex) Datenmemberflags abhängt:

|m_spInPlaceSite-Typ|m_bWndLess-Wert|m_bInPlaceSiteEx Wert|
|---------------------------|-----------------------|-----------------------------|
|`IOleInPlaceSiteWindowless`|TRUE|TRUE oder FALSE|
|`IOleInPlaceSiteEx`|FALSE|TRUE|
|`IOleInPlaceSite`|FALSE|FALSE|

## <a name="ccomcontrolbasem_spoleadviseholder"></a><a name="m_spoleadviseholder"></a>CComControlBase::m_spOleAdviseHolder

Stellt eine Standardimplementierung für eine Möglichkeit zum Halten von Beratungsverbindungen bereit.

```
CComPtr<IOleAdviseHolder>
    m_spOleAdviseHolder;
```

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Um diesen Datenmember innerhalb der Steuerelementklasse zu verwenden, müssen Sie ihn als Datenmember in der Steuerelementklasse deklarieren. Ihre Steuerelementklasse erbt diesen Datenmember nicht von der Basisklasse, da er innerhalb einer Union in der Basisklasse deklariert wird.

Die `m_spOleAdviseHolder` Schnittstelle implementiert die [Methoden IOleObject::Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) und [IOleObject::Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) zum Einrichten und Löschen von Beratungsverbindungen zum Container. Der Container des Steuerelements muss eine Beratungssenke implementieren, indem er die [IAdviseSink-Schnittstelle](/windows/win32/api/objidl/nn-objidl-iadvisesink) unterstützt.

## <a name="ccomcontrolbaseondraw"></a><a name="ondraw"></a>CComControlBase::OnDraw

Überschreiben Sie diese Methode, um das Steuerelement zu zeichnen.

```
virtual HRESULT OnDraw(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parameter

*di*<br/>
Ein Verweis auf die [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) Struktur, die Zeichnungsinformationen enthält, z. B. den Zeichnungsaspekt, die Steuerelementgrenzen und ob die Zeichnung optimiert ist oder nicht.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Der `OnDraw` Standardwert löscht oder stellt den Gerätekontext wieder her oder führt nichts aus, abhängig von den in [CComControlBase::OnDrawAdvanced](#ondrawadvanced)festgelegten Flags.

Eine `OnDraw` Methode wird automatisch zu ihrer Steuerelementklasse hinzugefügt, wenn Sie das Steuerelement mit dem ATL-Steuerelement-Assistenten erstellen. Der Standardwert `OnDraw` des Assistenten zeichnet ein Rechteck mit der Bezeichnung "ATL 8.0".

### <a name="example"></a>Beispiel

Siehe Beispiel für [CComControlBase::GetAmbientAppearance](#getambientappearance).

## <a name="ccomcontrolbaseondrawadvanced"></a><a name="ondrawadvanced"></a>CComControlBase::OnDrawAdvanced

Der `OnDrawAdvanced` Standard vorbereitet einen normalisierten Gerätekontext für das Zeichnen `OnDraw` und ruft dann die Methode der Steuerelementklasse auf.

```
virtual HRESULT OnDrawAdvanced(ATL_DRAWINFO& di);
```

### <a name="parameters"></a>Parameter

*di*<br/>
Ein Verweis auf die [ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md) Struktur, die Zeichnungsinformationen enthält, z. B. den Zeichnungsaspekt, die Steuerelementgrenzen und ob die Zeichnung optimiert ist oder nicht.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie den Vom Container übergebenen Gerätekontext akzeptieren möchten, ohne ihn zu normalisieren.

Weitere Informationen finden Sie unter [CComControlBase::OnDraw.](#ondraw)

## <a name="ccomcontrolbaseonkillfocus"></a><a name="onkillfocus"></a>CComControlBase::OnKillFocus

Überprüft, ob das Steuerelement aktiv ist und über eine gültige Kontrollsite verfügt, und informiert den Container dann darüber, dass das Steuerelement den Fokus verloren hat.

```
LRESULT OnKillFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parameter

*nMsg*<br/>
Reserviert.

*wParam*<br/>
Reserviert.

*lParam*<br/>
Reserviert.

*bBehandelt*<br/>
Flag, das angibt, ob die Fensternachricht erfolgreich verarbeitet wurde. Der Standardwert lautet FALSE.

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

## <a name="ccomcontrolbaseonmouseactivate"></a><a name="onmouseactivate"></a>CComControlBase::OnMouseActivate

Überprüft, ob sich die Benutzeroberfläche im Benutzermodus befindet, und aktiviert dann das Steuerelement.

```
LRESULT OnMouseActivate(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parameter

*nMsg*<br/>
Reserviert.

*wParam*<br/>
Reserviert.

*lParam*<br/>
Reserviert.

*bBehandelt*<br/>
Flag, das angibt, ob die Fensternachricht erfolgreich verarbeitet wurde. Der Standardwert lautet FALSE.

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

## <a name="ccomcontrolbaseonpaint"></a><a name="onpaint"></a>CComControlBase::OnPaint

Bereitet den Container für das Malen vor, ruft den Clientbereich `OnDrawAdvanced` des Steuerelements ab und ruft dann die Methode der Steuerungsklasse auf.

```
LRESULT OnPaint(UINT /* nMsg */,
    WPARAM wParam,
    LPARAM /* lParam */,
    BOOL& /* lResult */);
```

### <a name="parameters"></a>Parameter

*nMsg*<br/>
Reserviert.

*wParam*<br/>
Ein vorhandener HDC.

*lParam*<br/>
Reserviert.

*lResult*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Es wird immer NULL zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn *wParam* nicht `OnPaint` NULL ist, geht davon aus, dass es einen gültigen HDC enthält und es anstelle von [CComControlBase::m_hWndCD](#m_hwndcd)verwendet.

## <a name="ccomcontrolbaseonsetfocus"></a><a name="onsetfocus"></a>CComControlBase::OnSetFocus

Überprüft, ob das Steuerelement aktiv ist und über eine gültige Kontrollsite verfügt, und informiert dann den Container, dass das Steuerelement in den Fokus gerückt ist.

```
LRESULT OnSetFocus(UINT /* nMsg */,
    WPARAM /* wParam */,
    LPARAM /* lParam */,
    BOOL& bHandled);
```

### <a name="parameters"></a>Parameter

*nMsg*<br/>
Reserviert.

*wParam*<br/>
Reserviert.

*lParam*<br/>
Reserviert.

*bBehandelt*<br/>
Flag, das angibt, ob die Fensternachricht erfolgreich verarbeitet wurde. Der Standardwert lautet FALSE.

### <a name="return-value"></a>Rückgabewert

Gibt immer 1 zurück.

### <a name="remarks"></a>Bemerkungen

Sendet eine Benachrichtigung an den Container, dass das Steuerelement den Fokus erhalten hat.

## <a name="ccomcontrolbasepretranslateaccelerator"></a><a name="pretranslateaccelerator"></a>CComControlBase::PreTranslateAccelerator

Überschreiben Sie diese Methode, um eigene Tastaturbeschleunigerhandler bereitzustellen.

```
BOOL PreTranslateAccelerator(LPMSG /* pMsg */,
    HRESULT& /* hRet */);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
Reserviert.

*hRet*<br/>
Reserviert.

### <a name="return-value"></a>Rückgabewert

Standardmäßig gibt FALSE zurück.

## <a name="ccomcontrolbasesendonclose"></a><a name="sendonclose"></a>CComControlBase::SendOnClose

Benachrichtigt alle beim Beratungsinhaber registrierten Beratungssenken, dass die Kontrolle geschlossen wurde.

```
HRESULT SendOnClose();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Sendet eine Benachrichtigung, dass das Steuerelement seine Beratungssenken geschlossen hat.

## <a name="ccomcontrolbasesendondatachange"></a><a name="sendondatachange"></a>CComControlBase::SendOnDataChange

Benachrichtigt alle beim Beratungsinhaber registrierten Beratungssenken, dass sich die Kontrolldaten geändert haben.

```
HRESULT SendOnDataChange(DWORD advf = 0);
```

### <a name="parameters"></a>Parameter

*advf*<br/>
Advise-Flags, die angeben, wie der Aufruf von [IAdviseSink::OnDataChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-ondatachange) ausgeführt wird. Die Werte [ADVF](/windows/win32/api/objidl/ne-objidl-advf) stammen aus der ADVF-Enumeration.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="ccomcontrolbasesendonrename"></a><a name="sendonrename"></a>CComControlBase::SendOnRename

Benachrichtigt alle beim Beraterhalter registrierten Beratungssenken, dass das Steuerelement einen neuen Moniker hat.

```
HRESULT SendOnRename(IMoniker* pmk);
```

### <a name="parameters"></a>Parameter

*Pmk*<br/>
Zeiger auf den neuen Moniker des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Sendet eine Benachrichtigung, dass sich der Moniker für das Steuerelement geändert hat.

## <a name="ccomcontrolbasesendonsave"></a><a name="sendonsave"></a>CComControlBase::SendOnSave

Benachrichtigt alle beim Beratungsinhaber registrierten Beratungssenken, dass die Steuerung gespeichert wurde.

```
HRESULT SendOnSave();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Sendet eine Benachrichtigung, dass das Steuerelement gerade seine Daten gespeichert hat.

## <a name="ccomcontrolbasesendonviewchange"></a><a name="sendonviewchange"></a>CComControlBase::SendOnViewChange

Benachrichtigt alle registrierten Beratungssenken, dass sich die Ansicht des Steuerelements geändert hat.

```
HRESULT SendOnViewChange(DWORD dwAspect, LONG lindex = -1);
```

### <a name="parameters"></a>Parameter

*Dwaspect*<br/>
Der Aspekt oder die Ansicht des Steuerelements.

*Lindex*<br/>
Der Teil der Ansicht, die sich geändert hat. Nur -1 ist gültig.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

`SendOnViewChange`[iAdviseSink::OnViewChange](/windows/win32/api/objidl/nf-objidl-iadvisesink-onviewchange)aufruft. Der einzige aktuell unterstützte Wert von *lindex* ist -1, was darauf hinweist, dass die gesamte Ansicht von Interesse ist.

## <a name="ccomcontrolbasesetcontrolfocus"></a><a name="setcontrolfocus"></a>CComControlBase::SetControlFocus

Legt den Tastaturfokus auf oder aus dem Steuerelement fest oder entfernt ihn.

```
BOOL SetControlFocus(BOOL bGrab);
```

### <a name="parameters"></a>Parameter

*bGrab*<br/>
Wenn TRUE, legt der Tastaturfokus auf das aufrufende Steuerelement fest. Wenn FALSE, entfernt den Tastaturfokus aus dem aufrufenden Steuerelement, sofern es den Fokus hat.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Steuerelement erfolgreich den Fokus empfängt. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Für ein Fenstersteuerelement wird die Windows-API-Funktion [SetFocus](/windows/win32/api/winuser/nf-winuser-setfocus) aufgerufen. Für ein fensterloses Steuerelement wird [IOleInPlaceSiteWindowless::SetFocus](/windows/win32/api/ocidl/nf-ocidl-ioleinplacesitewindowless-setfocus) aufgerufen. Durch diesen Aufruf erhält ein fensterloses Steuerelement den Tastaturfokus und kann auf Fensternachrichten reagieren.

## <a name="ccomcontrolbasesetdirty"></a><a name="setdirty"></a>CComControlBase::SetDirty

Legt den `m_bRequiresSave` Datenmember auf den Wert in *bDirty*fest.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parameter

*bDirty*<br/>
Wert des Datenelements [CComControlBase::m_bRequiresSave](#m_brequiressave).

### <a name="remarks"></a>Bemerkungen

`SetDirty(TRUE)`sollte aufgerufen werden, um zu kennzeichnen, dass sich das Steuerelement seit dem letzten Speichern geändert hat. Der Wert `m_bRequiresSave` von wird mit [CComControlBase abgerufen::GetDirty](#getdirty).

## <a name="see-also"></a>Siehe auch

[CComControl-Klasse](../../atl/reference/ccomcontrol-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
