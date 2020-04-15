---
title: CLinkCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CLinkCtrl
- AFXCMN/CLinkCtrl
- AFXCMN/CLinkCtrl::CLinkCtrl
- AFXCMN/CLinkCtrl::Create
- AFXCMN/CLinkCtrl::CreateEx
- AFXCMN/CLinkCtrl::GetIdealHeight
- AFXCMN/CLinkCtrl::GetIdealSize
- AFXCMN/CLinkCtrl::GetItem
- AFXCMN/CLinkCtrl::GetItemID
- AFXCMN/CLinkCtrl::GetItemState
- AFXCMN/CLinkCtrl::GetItemUrl
- AFXCMN/CLinkCtrl::HitTest
- AFXCMN/CLinkCtrl::SetItem
- AFXCMN/CLinkCtrl::SetItemID
- AFXCMN/CLinkCtrl::SetItemState
- AFXCMN/CLinkCtrl::SetItemUrl
helpviewer_keywords:
- CLinkCtrl [MFC], CLinkCtrl
- CLinkCtrl [MFC], Create
- CLinkCtrl [MFC], CreateEx
- CLinkCtrl [MFC], GetIdealHeight
- CLinkCtrl [MFC], GetIdealSize
- CLinkCtrl [MFC], GetItem
- CLinkCtrl [MFC], GetItemID
- CLinkCtrl [MFC], GetItemState
- CLinkCtrl [MFC], GetItemUrl
- CLinkCtrl [MFC], HitTest
- CLinkCtrl [MFC], SetItem
- CLinkCtrl [MFC], SetItemID
- CLinkCtrl [MFC], SetItemState
- CLinkCtrl [MFC], SetItemUrl
ms.assetid: d1cd876a-ecca-42db-8ac4-9cd327df0cd4
ms.openlocfilehash: aa1f630b448c60a0eeb6a905ed6eef6f84a2ff8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372254"
---
# <a name="clinkctrl-class"></a>CLinkCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-SysLink-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CLinkCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CLinkCtrl::CLinkCtrl](#clinkctrl)|Erstellt ein `CLinkCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CLinkCtrl::Erstellen](#create)|Erstellt ein Verknüpfungssteuerelement und `CLinkCtrl` fügt es an ein Objekt an.|
|[CLinkCtrl::CreateEx](#createex)|Erstellt ein Verknüpfungssteuerelement mit erweiterten Stilen und fügt es an ein `CLinkCtrl` Objekt an.|
|[CLinkCtrl::GetIdealHeight](#getidealheight)|Ruft die ideale Höhe des Verbindungssteuerelements ab.|
|[CLinkCtrl::GetIdealSize](#getidealsize)|Berechnet die bevorzugte Höhe des Verknüpfungstexts für das aktuelle Verknüpfungssteuerelement, abhängig von der angegebenen Breite der Verknüpfung.|
|[CLinkCtrl::GetItem](#getitem)|Ruft die Zustände und Attribute eines Verknüpfungssteuerelements ab.|
|[CLinkCtrl::GetItemID](#getitemid)|Ruft die ID eines Verknüpfungssteuerelements ab.|
|[CLinkCtrl::GetItemState](#getitemstate)|Ruft den Status des Verknüpfungssteuerelements ab.|
|[CLinkCtrl::GetItemUrl](#getitemurl)|Ruft die URL ab, die durch das Linksteuerelementelement dargestellt wird.|
|[CLinkCtrl::HitTest](#hittest)|Bestimmt, ob der Benutzer auf den angegebenen Link geklickt hat.|
|[CLinkCtrl::SetItem](#setitem)|Legt die Zustände und Attribute eines Verknüpfungssteuerelements fest.|
|[CLinkCtrl::SetItemID](#setitemid)|Legt die ID eines Verknüpfungssteuerelements fest.|
|[CLinkCtrl::SetItemState](#setitemstate)|Legt den Status des Verknüpfungssteuerelements fest.|
|[CLinkCtrl::SetItemUrl](#setitemurl)|Legt die URL fest, die durch das Verknüpfungssteuerelementelement dargestellt wird.|

## <a name="remarks"></a>Bemerkungen

Ein "Link-Steuerelement" bietet eine bequeme Möglichkeit, Hypertext-Links in ein Fenster einzubetten. Das eigentliche Steuerelement ist ein Fenster, das markierten Text rendert und geeignete Anwendungen startet, wenn der Benutzer auf einen eingebetteten Link klickt. Mehrere Links werden innerhalb eines Steuerelements unterstützt und können über einen nullbasierten Index aufgerufen werden.

Dieses Steuerelement (und `CLinkCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows XP und höher ausgeführt werden.

Weitere Informationen finden Sie unter [SysLink Control](/windows/win32/Controls/syslink-overview) im Windows SDK.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CLinkCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="clinkctrlclinkctrl"></a><a name="clinkctrl"></a>CLinkCtrl::CLinkCtrl

Erstellt ein `CLinkCtrl`-Objekt.

```
CLinkCtrl();
```

## <a name="clinkctrlcreate"></a><a name="create"></a>CLinkCtrl::Erstellen

Erstellt ein Verknüpfungssteuerelement und `CLinkCtrl` fügt es an ein Objekt an.

```
virtual BOOL Create(
    LPCTSTR lpszLinkMarkup,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL Create(DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*lpszLinkMarkup*<br/>
Zeigen Sie mit dem Zeiger auf eine Null-Termin-Zeichenfolge, die den markierten anzuzeigenden Text enthält. Weitere Informationen finden Sie im Abschnitt "Markup und Linkzugriff" im Thema [Übersicht über SysLink-Steuerelemente](/windows/win32/Controls/syslink-overview).

*dwStyle*<br/>
Gibt den Stil des Verknüpfungssteuerelements an. Wenden Sie eine beliebige Kombination von Steuerelementstilen an. Weitere Informationen finden `Windows SDK` Sie unter [Allgemeine Steuerelementstile](/windows/win32/Controls/common-control-styles) im

*Rect*<br/>
Gibt die Größe und Position des Verknüpfungssteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Verknüpfungssteuerelements an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Verknüpfungssteuerelements an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierung erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CLinkCtrl` ein Objekt in zwei Schritten. Rufen Sie zuerst den Konstruktor auf, und rufen Sie dann auf, `Create`das das Verknüpfungssteuerelement erstellt und an das `CLinkCtrl` Objekt anfügt. Wenn Sie erweiterte Fensterstile mit Ihrem Steuerelement verwenden möchten, rufen Sie `Create` [CLinkCtrl::CreateEx](#createex) anstelle von auf.

Die zweite Form `Create` der Methode ist veraltet. Verwenden Sie das erste Formular, das den Parameter *lpszLinkMarkup* angibt.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden zwei `m_Link1` `m_Link2`Variablen definiert, named und , die für den Zugriff auf zwei Verknüpfungssteuerelemente verwendet werden.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#2](../../mfc/reference/codesnippet/cpp/clinkctrl-class_1.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein Verknüpfungssteuerelement basierend auf der Position eines anderen Verknüpfungssteuerelements erstellt. Der Ressourcenlader erstellt das erste Verknüpfungssteuerelement, wenn die Anwendung gestartet wird. Wenn Ihre Anwendung die OnInitDialog-Methode eingibt, erstellen Sie das zweite Verknüpfungssteuerelement relativ zur Position des ersten Linksteuerelements. Anschließend ändern Sie die Größe des zweiten Verknüpfungssteuerelements an den angezeigten Text.

[!code-cpp[NVC_MFC_CLinkCtrl_s1#1](../../mfc/reference/codesnippet/cpp/clinkctrl-class_2.cpp)]

## <a name="clinkctrlcreateex"></a><a name="createex"></a>CLinkCtrl::CreateEx

Erstellt ein Verknüpfungssteuerelement mit erweiterten Stilen und fügt es an ein `CLinkCtrl` Objekt an.

```
virtual BOOL CreateEx(
    LPCTSTR lpszLinkMarkup,
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);

virtual BOOL CreateEx(DWORD  dwExStyle,
    DWORD  dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT  nID);
```

### <a name="parameters"></a>Parameter

*lpszLinkMarkup*<br/>
Zeigen Sie mit dem Zeiger auf eine Null-Termin-Zeichenfolge, die den markierten anzuzeigenden Text enthält. Weitere Informationen finden Sie im Abschnitt "Markup und Linkzugriff" im Thema [Übersicht über SysLink-Steuerelemente](/windows/win32/Controls/syslink-overview).

*dwExStyle*<br/>
Gibt den erweiterten Stil des Verknüpfungssteuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt den Stil des Verknüpfungssteuerelements an. Wenden Sie eine beliebige Kombination von Steuerelementstilen an. Weitere Informationen finden Sie unter [Allgemeine Steuerelementstile](/windows/win32/Controls/common-control-styles) im Windows SDK.

*Rect*<br/>
Gibt die Größe und Position des Verknüpfungssteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Verknüpfungssteuerelements an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Verknüpfungssteuerelements an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Initialisierung erfolgreich war; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Create,](#create) um erweiterte Windows-Stilkonstanten anzuwenden.

Die zweite Form `CreateEx` der Methode ist veraltet. Verwenden Sie das erste Formular, das den Parameter *lpszLinkMarkup* angibt.

## <a name="clinkctrlgetidealheight"></a><a name="getidealheight"></a>CLinkCtrl::GetIdealHeight

Ruft die ideale Höhe des Verbindungssteuerelements ab.

```
int GetIdealHeight() const;
```

### <a name="return-value"></a>Rückgabewert

Die ideale Höhe des Steuerelements in Pixel.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [LM_GETIDEALHEIGHT](/windows/win32/Controls/lm-getidealheight)Win32-LM_GETIDEALHEIGHT , wie im Windows SDK beschrieben.

## <a name="clinkctrlgetidealsize"></a><a name="getidealsize"></a>CLinkCtrl::GetIdealSize

Berechnet die bevorzugte Höhe des Verknüpfungstexts für das aktuelle Verknüpfungssteuerelement, abhängig von der angegebenen Breite der Verknüpfung.

```
int GetIdealSize(
    int cxMaxWidth,
    SIZE* pSize) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*cxMaxWidth*|[in] Die maximale Breite der Verknüpfung in Pixel.|
|[out] \* *pSize*|Ein Zeiger auf [SIZE](/windows/win32/api/windef/ns-windef-size) eine Windows SIZE-Struktur. Wenn diese Methode zurückgegeben wird, `SIZE` enthält das *cy-Element* der Struktur die ideale Linktexthöhe für die Linktextbreite, die von *cxMaxWidth*angegeben wird. Das *cx-Element* der Struktur enthält die tatsächlich benötigte Link-Textbreite.|

### <a name="return-value"></a>Rückgabewert

Die bevorzugte Höhe des Linktexts in Pixel. Der Rückgabewert entspricht dem Wert des *cy-Elements* der `SIZE` Struktur.

### <a name="remarks"></a>Bemerkungen

Ein Beispiel für `GetIdealSize` die Methode finden Sie im Beispiel in [CLinkCtrl::Create](#create).

Diese Methode sendet die [LM_GETIDEALSIZE](/windows/win32/Controls/lm-getidealsize) Nachricht, die im Windows SDK beschrieben wird.

## <a name="clinkctrlgetitem"></a><a name="getitem"></a>CLinkCtrl::GetItem

Ruft die Zustände und Attribute eines Verknüpfungssteuerelements ab.

```
BOOL GetItem(PLITEM pItem) const;
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Ein Zeiger auf eine [LITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-litem) um Elementinformationen zu erhalten.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [LM_GETITEM](/windows/win32/Controls/lm-getitem), wie im Windows SDK beschrieben.

## <a name="clinkctrlgetitemid"></a><a name="getitemid"></a>CLinkCtrl::GetItemID

Ruft die ID eines Verknüpfungssteuerelements ab.

```
BOOL GetItemID(
    int iLink,
    CString& strID) const;

BOOL GetItemID(
    int iLink,
    LPWSTR szID,
    UINT cchID) const;
```

### <a name="parameters"></a>Parameter

*Ilink*<br/>
Der Index eines Verknüpfungssteuerelements.

*strID*<br/>
Ein [CStringT-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das die ID des angegebenen Elements enthält.

*szID*<br/>
Eine null-terminierte Zeichenfolge, die die ID des angegebenen Elements enthält.

*cchID*<br/>
Die Größe in *szID* Zeichen des szID-Puffers.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

> [!NOTE]
> Diese Funktion gibt auch FALSE zurück, wenn der Puffer von *szID oder strID* kleiner als MAX_LINKID_TEXT ist.

### <a name="remarks"></a>Bemerkungen

Ruft die ID eines bestimmten Verknüpfungssteuerelements ab. Weitere Informationen finden Sie in der Win32-Meldung, die im Windows SDK [LM_GETITEM.](/windows/win32/Controls/lm-getitem)

## <a name="clinkctrlgetitemstate"></a><a name="getitemstate"></a>CLinkCtrl::GetItemState

Ruft den Status des Verknüpfungssteuerelements ab.

```
BOOL GetItemState(
    int iLink,
    UINT* pnState,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED) const;
```

### <a name="parameters"></a>Parameter

*Ilink*<br/>
Der Index eines Verknüpfungssteuerelements.

*pnState*<br/>
Der Wert des angegebenen Statuselements.

*stateMask*<br/>
Kombination von Flags, die beschreiben, welches Statuselement abgetreten werden soll. Eine Liste der Werte finden Sie `state` in der Beschreibung des Elements in der [LITEM-Struktur.](/windows/win32/api/commctrl/ns-commctrl-litem) Zulässige Elemente sind identisch `state`mit den in zulässigen .

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Ruft den Wert des angegebenen Statuselements eines bestimmten Verknüpfungssteuerelements ab. Weitere Informationen finden Sie in der Win32-Meldung, die im Windows SDK [LM_GETITEM.](/windows/win32/Controls/lm-getitem)

## <a name="clinkctrlgetitemurl"></a><a name="getitemurl"></a>CLinkCtrl::GetItemUrl

Ruft die URL ab, die durch das Linksteuerelementelement dargestellt wird.

```
BOOL GetItemUrl(
    int iLink,
    CString& strUrl) const;

BOOL GetItemUrl(
    int iLink,
    LPWSTR szUrl,
    UINT cchUrl) const;
```

### <a name="parameters"></a>Parameter

*Ilink*<br/>
Der Index eines Verknüpfungssteuerelements.

*strUrl*<br/>
Ein [CStringT-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das die URL enthält, die durch das angegebene Element dargestellt wird

*szUrl*<br/>
Eine null-terminierte Zeichenfolge, die die URL enthält, die durch das angegebene Element dargestellt wird

*cchUrl*<br/>
Die Größe in Zeichen des *szURL-Puffers.*

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

> [!NOTE]
> Diese Funktion gibt auch FALSE zurück, wenn der Puffer von *szUrl oder strUrl* kleiner als MAX_LINKID_TEXT ist.

### <a name="remarks"></a>Bemerkungen

Ruft die URL ab, die durch das angegebene Linksteuerelementelement dargestellt wird. Weitere Informationen finden Sie in der Win32-Meldung, die im Windows SDK [LM_GETITEM.](/windows/win32/Controls/lm-getitem)

## <a name="clinkctrlhittest"></a><a name="hittest"></a>CLinkCtrl::HitTest

Bestimmt, ob der Benutzer auf den angegebenen Link geklickt hat.

```
BOOL HitTest(PLHITTESTINFO phti) const;
```

### <a name="parameters"></a>Parameter

*phti*<br/>
Zeigen Sie `LHITTESTINFO` auf eine Struktur, die alle Informationen über den Link enthält, auf den der Benutzer geklickt hat.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [LM_HITTEST](/windows/win32/Controls/lm-hittest)Win32-LM_HITTEST , wie im Windows SDK beschrieben.

## <a name="clinkctrlsetitem"></a><a name="setitem"></a>CLinkCtrl::SetItem

Legt die Zustände und Attribute eines Verknüpfungssteuerelements fest.

```
BOOL SetItem(PLITEM pItem);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Ein Zeiger auf eine [LITEM-Struktur,](/windows/win32/api/commctrl/ns-commctrl-litem) die die festzulegenden Informationen enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [LM_SETITEM](/windows/win32/Controls/lm-setitem), wie im Windows SDK beschrieben.

## <a name="clinkctrlsetitemid"></a><a name="setitemid"></a>CLinkCtrl::SetItemID

Ruft die ID eines Verknüpfungssteuerelements ab.

```
BOOL SetItemID(
    int iLink,
    LPCWSTR szID);
```

### <a name="parameters"></a>Parameter

*Ilink*<br/>
Der Index eines Verknüpfungssteuerelements.

*szID*<br/>
Eine null-terminierte Zeichenfolge, die die ID des angegebenen Elements enthält.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Legt die ID eines bestimmten Verknüpfungssteuerelements fest. Weitere Informationen finden Sie in der Win32-Meldung [LM_SETITEM](/windows/win32/Controls/lm-setitem) im Windows SDK.

## <a name="clinkctrlsetitemstate"></a><a name="setitemstate"></a>CLinkCtrl::SetItemState

Ruft den Status des Verknüpfungssteuerelements ab.

```
BOOL SetItemState(
    int iLink,
    UINT state,
    UINT stateMask = LIS_FOCUSED | LIS_ENABLED | LIS_VISITED);
```

### <a name="parameters"></a>Parameter

*Ilink*<br/>
Der Index eines Verknüpfungssteuerelements.

*pnState*<br/>
Der Wert des angegebenen Statuselements, das festgelegt wird.

*stateMask*<br/>
Kombination von Flags, die das festgelegte Statuselement beschreiben. Eine Liste der Werte finden Sie `state` in der Beschreibung des Elements in der [LITEM-Struktur.](/windows/win32/api/commctrl/ns-commctrl-litem) Zulässige Elemente sind identisch `state`mit den in zulässigen .

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Legt den Wert des angegebenen Statuselements eines bestimmten Verknüpfungssteuerelements fest. Weitere Informationen finden Sie in der Win32-Meldung [LM_SETITEM](/windows/win32/Controls/lm-setitem) im Windows SDK.

## <a name="clinkctrlsetitemurl"></a><a name="setitemurl"></a>CLinkCtrl::SetItemUrl

Legt die URL fest, die durch das Verknüpfungssteuerelementelement dargestellt wird.

```
BOOL SetItemUrl(
    int iLink,
    LPCWSTR szUrl);
```

### <a name="parameters"></a>Parameter

*Ilink*<br/>
Der Index eines Verknüpfungssteuerelements.

*szUrl*<br/>
Eine null-terminierte Zeichenfolge, die die URL enthält, die durch das angegebene Element dargestellt wird

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

### <a name="remarks"></a>Bemerkungen

Legt die URL fest, die durch das angegebene Verknüpfungssteuerelementelement dargestellt wird. Weitere Informationen finden Sie in der Win32-Meldung [LM_SETITEM](/windows/win32/Controls/lm-setitem) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)
