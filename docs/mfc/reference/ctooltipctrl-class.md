---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: bf32671eb3535de1bf072e24bc642145e87c84ee
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426324"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Kapselt die Funktionalität eines ToolTip-Steuerelements. Dabei handelt es sich um ein kleines Popupfenster, das eine einzelne Textzeile anzeigt, die den Zweck eines Tools der Anwendung beschreibt.

## <a name="syntax"></a>Syntax

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CToolTipCtrl:: CToolTipCtrl](#ctooltipctrl)|Erstellt ein `CToolTipCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CToolTipCtrl:: Aktivieren](#activate)|Aktiviert und deaktiviert das QuickInfo-Steuerelement.|
|[CToolTipCtrl:: AddTool](#addtool)|Registriert ein Tool mit dem QuickInfo-Steuerelement.|
|[CToolTipCtrl:: TRL Rect](#adjustrect)|Konvertiert zwischen dem Textanzeige Rechteck eines QuickInfo-Steuer Elements und dem zugehörigen Fenster Rechteck.|
|[CToolTipCtrl:: Create](#create)|Erstellt ein QuickInfo-Steuerelement und fügt es an ein `CToolTipCtrl` Objekt an.|
|[CToolTipCtrl:: kreateex](#createex)|Erstellt ein QuickInfo-Steuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein `CToolTipCtrl` Objekt an.|
|[CToolTipCtrl::D eltool](#deltool)|Entfernt ein Tool aus dem QuickInfo-Steuerelement.|
|[CToolTipCtrl:: getbubblesize](#getbubblesize)|Ruft die Größe der QuickInfo ab.|
|[CToolTipCtrl:: getcurrenttool](#getcurrenttool)|Ruft Informationen (z. b. die Größe, Position und den Text) des QuickInfo-Fensters ab, das im aktuellen QuickInfo-Steuerelement angezeigt wird.|
|[CToolTipCtrl:: getdelta aytime](#getdelaytime)|Ruft die Anfangs-, Popup-und neueinblenden Dauer ab, die derzeit für ein QuickInfo-Steuerelement festgelegt sind.|
|[CToolTipCtrl:: getMargin](#getmargin)|Ruft die oberen, linken, unteren und rechten Ränder ab, die für ein QuickInfo-Fenster festgelegt werden.|
|[CToolTipCtrl:: GetMaxTipWidth](#getmaxtipwidth)|Ruft die maximale Breite für ein QuickInfo-Fenster ab.|
|[CToolTipCtrl:: gettext](#gettext)|Ruft den Text ab, der von einem QuickInfo-Steuerelement für ein Tool verwaltet wird.|
|[CToolTipCtrl:: gettipbkcolor](#gettipbkcolor)|Ruft die Hintergrundfarbe in einem QuickInfo-Fenster ab.|
|[CToolTipCtrl:: gettiptextcolor](#gettiptextcolor)|Ruft die Textfarbe in einem QuickInfo-Fenster ab.|
|[CToolTipCtrl:: getTitle](#gettitle)|Ruft den Titel des aktuellen QuickInfo-Steuer Elements ab.|
|[CToolTipCtrl:: gettoolcount](#gettoolcount)|Ruft die Anzahl der Tools ab, die von einem QuickInfo-Steuerelement verwaltet werden.|
|[CToolTipCtrl:: gettoolinfo](#gettoolinfo)|Ruft die Informationen ab, die ein QuickInfo-Steuerelement zu einem Tool beibehält.|
|[CToolTipCtrl:: HitTest](#hittest)|Testet einen Punkt, um zu bestimmen, ob er sich innerhalb des umgebenden Rechtecks des angegebenen Tools befindet. Wenn dies der Fall ist, ruft Informationen über das Tool ab.|
|[CToolTipCtrl::P op](#pop)|Entfernt ein angezeigtes QuickInfo-Fenster aus der Ansicht.|
|[CToolTipCtrl::P-opup](#popup)|Bewirkt, dass das aktuelle QuickInfo-Steuerelement an den Koordinaten der letzten Maus Meldung angezeigt wird.|
|[CToolTipCtrl:: relayevent](#relayevent)|Übergibt eine Maus Meldung an ein QuickInfo-Steuerelement zur Verarbeitung.|
|[CToolTipCtrl:: setdelta Time](#setdelaytime)|Legt die Anfangs-, Popup-und Wiederholungs Dauer für ein QuickInfo-Steuerelement fest.|
|[CToolTipCtrl:: setMargin](#setmargin)|Legt die oberen, linken, unteren und rechten Ränder für ein QuickInfo-Fenster fest.|
|[CToolTipCtrl:: SetMaxTipWidth](#setmaxtipwidth)|Legt die maximale Breite für ein QuickInfo-Fenster fest.|
|[CToolTipCtrl:: Setup-bkcolor](#settipbkcolor)|Legt die Hintergrundfarbe in einem QuickInfo-Fenster fest.|
|[CToolTipCtrl:: Setup TextColor](#settiptextcolor)|Legt die Textfarbe in einem QuickInfo-Fenster fest.|
|[CToolTipCtrl:: SetTitle](#settitle)|Fügt einer QuickInfo ein Standard Symbol und eine Titel Zeichenfolge hinzu.|
|[CToolTipCtrl:: SetToolInfo](#settoolinfo)|Legt die Informationen fest, die eine QuickInfo für ein Tool beibehält.|
|[CToolTipCtrl:: SetToolRect](#settoolrect)|Legt ein neues Begrenzungs Rechteck für ein Tool fest.|
|[CToolTipCtrl:: SetWindowTheme](#setwindowtheme)|Legt den visuellen Stil des QuickInfo-Fensters fest.|
|[CToolTipCtrl:: Update](#update)|Erzwingt, dass das aktuelle Tool neu gezeichnet wird.|
|[CToolTipCtrl:: updatetiptext](#updatetiptext)|Legt den QuickInfo-Text für ein Tool fest.|

## <a name="remarks"></a>Hinweise

Ein "Tool" ist entweder ein Fenster, z. b. ein untergeordnetes Fenster oder Steuerelement, oder ein Anwendungs definierter rechteckiger Bereich im Client Bereich eines Fensters. Eine QuickInfo wird in den meisten Fällen ausgeblendet. Sie wird nur angezeigt, wenn der Benutzer den Cursor auf ein Tool setzt und ihn für ungefähr eine halbe Sekunde verlässt. Die QuickInfo wird in der Nähe des Cursors angezeigt und verschwindet, wenn der Benutzer auf eine Maustaste klickt oder den Cursor aus dem Tool verschiebt.

`CToolTipCtrl` stellt die Funktionen bereit, um die anfängliche Zeit und Dauer der QuickInfo zu steuern, die Randbreite für den QuickInfo-Text, die Breite des QuickInfo-Fensters selbst und die Hintergrund-und Textfarbe der QuickInfo. Ein einzelnes QuickInfo-Steuerelement kann Informationen für mehr als ein Tool bereitstellen.

Die `CToolTipCtrl`-Klasse stellt die Funktionalität des allgemeinen Windows-QuickInfo-Steuer Elements bereit. Dieses Steuerelement (und damit auch die `CToolTipCtrl`-Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Weitere Informationen zum Aktivieren von Quick Infos finden Sie unter Quick Infos [in Windows, die nicht von CFrameWnd abgeleitet](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)werden.

Weitere Informationen zur Verwendung von `CToolTipCtrl`finden Sie unter Steuer [Elemente](../../mfc/controls-mfc.md) und [Verwenden von CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxcmn.h

##  <a name="activate"></a>CToolTipCtrl:: Aktivieren

Diese Funktion wird aufgerufen, um ein QuickInfo-Steuerelement zu aktivieren oder zu deaktivieren.

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*bactivate*<br/>
Gibt an, ob das QuickInfo-Steuerelement aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Hinweise

Wenn *bactivate* den Wert true hat, wird das Steuerelement aktiviert. der Wert false gibt an, dass er deaktiviert ist.

Wenn ein QuickInfo-Steuerelement aktiv ist, werden die QuickInfo-Informationen angezeigt, wenn sich der Cursor auf einem Tool befindet, das beim Steuerelement registriert ist. Wenn Sie inaktiv ist, werden die QuickInfo-Informationen nicht angezeigt, auch wenn sich der Cursor auf einem Tool befindet.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="addtool"></a>CToolTipCtrl:: AddTool

Registriert ein Tool mit dem QuickInfo-Steuerelement.

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*nidtext*<br/>
ID der Zeichen folgen Ressource, die den Text für das Tool enthält.

*lprecttool*<br/>
Ein Zeiger auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die Koordinaten des umschließenden Rechtecks des Tools enthält. Die Koordinaten sind relativ zur oberen linken Ecke des Client Bereichs des Fensters, das durch *pwnd*identifiziert wird.

*nidtool*<br/>
ID des Tools.

*lpszText*<br/>
Zeiger auf den Text für das Tool. Wenn dieser Parameter den Wert LPSTR_TEXTCALLBACK enthält, werden TTN_NEEDTEXT Benachrichtigungs Meldungen an das übergeordnete Fenster des Fensters gesendet, auf das *pwnd* zeigt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der *lprecttool* -Parameter und der *nidtool* -Parameter müssen gültig sein, oder wenn *lprecttool* NULL ist, muss " *nidtool* " den Wert "0" aufweisen.

Ein QuickInfo-Steuerelement kann mehr als einem Tool zugeordnet werden. Diese Funktion wird aufgerufen, um ein Tool mit dem QuickInfo-Steuerelement zu registrieren, sodass die in der QuickInfo gespeicherten Informationen angezeigt werden, wenn sich der Cursor auf dem Tool befindet.

> [!NOTE]
>  Es ist nicht möglich, eine QuickInfo mit `AddTool`auf ein statisches Steuerelement festzulegen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="adjustrect"></a>CToolTipCtrl:: TRL Rect

Konvertiert zwischen dem Textanzeige Rechteck eines QuickInfo-Steuer Elements und dem zugehörigen Fenster Rechteck.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parameter

*LPRC*<br/>
Ein Zeiger auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die entweder ein QuickInfo-Fenster Rechteck oder ein Textanzeige Rechteck enthält.

*blarger*<br/>
TRUE gibt an, dass *LPRC* zum Angeben eines Textanzeige Rechtecks verwendet wird, und empfängt das entsprechende Fenster Rechteck. FALSE gibt an, dass *LPRC* zum Angeben eines Fenster Rechtecks verwendet wird, und empfängt das entsprechende Textanzeige Rechteck.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Rechteck erfolgreich angepasst wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion berechnet das Textanzeige Rechteck eines QuickInfo-Steuer Elements aus dem Fenster Rechteck oder das QuickInfo-Fenster Rechteck, das zum Anzeigen eines angegebenen Textanzeige Rechtecks erforderlich ist.

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect), wie in der Windows SDK beschrieben.

##  <a name="create"></a>CToolTipCtrl:: Create

Erstellt ein QuickInfo-Steuerelement und fügt es an ein `CToolTipCtrl` Objekt an.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Gibt das übergeordnete Fenster des QuickInfo-Steuer Elements an, in der Regel eine `CDialog`. Er darf nicht NULL sein.

*dwstyle*<br/>
Gibt den Stil des QuickInfo-Steuer Elements an. Weitere Informationen finden Sie im Abschnitt " **Hinweise** ".

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `CToolTipCtrl` Objekt erfolgreich erstellt wurde. andernfalls 0.

### <a name="remarks"></a>Hinweise

Sie erstellen eine `CToolTipCtrl` in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, um das `CToolTipCtrl` Objekt zu erstellen, und rufen Sie dann `Create` auf, um das QuickInfo-Steuerelement zu erstellen und es an das `CToolTipCtrl`-Objekt anzufügen

Der Parameter " *dwstyle* " kann eine beliebige Kombination von [Fenster Stilen](../../mfc/reference/styles-used-by-mfc.md#window-styles)sein. Außerdem verfügt ein QuickInfo-Steuerelement über zwei klassenspezifische Stile: TTS_ALWAYSTIP und TTS_NOPREFIX.

|Stil|Bedeutung|
|-----------|-------------|
|TTS_ALWAYSTIP|Gibt an, dass die QuickInfo angezeigt wird, wenn sich der Cursor auf einem Tool befindet, unabhängig davon, ob das Besitzer Fenster des QuickInfo-Steuer Elements aktiv oder inaktiv ist. Ohne diesen Stil wird das QuickInfo-Steuerelement angezeigt, wenn das Besitzer Fenster des Tools aktiv ist, aber nicht, wenn es inaktiv ist.|
|TTS_NOPREFIX|Dieser Stil hindert das System daran, das kaufmännische und-Zeichen (&) aus einer Zeichenfolge zu entfernen. Wenn ein QuickInfo-Steuerelement nicht den TTS_NOPREFIX Stil hat, entfernt das System automatisch kaufmännische und Zeichen, sodass eine Anwendung dieselbe Zeichenfolge wie ein Menü Element und als Text in einem QuickInfo-Steuerelement verwenden kann.|

Ein QuickInfo-Steuerelement verfügt über die Fenster Stile WS_POPUP und WS_EX_TOOLWINDOW, unabhängig davon, ob Sie Sie beim Erstellen des Steuer Elements angeben.

Um ein QuickInfo-Steuerelement mit erweiterten Windows-Stilen zu erstellen, rufen Sie [CToolTipCtrl::](#createex) up-Ex anstelle von `Create`auf.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="createex"></a>CToolTipCtrl:: kreateex

Erstellt ein-Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CToolTipCtrl`-Objekt zu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Element des Steuer Elements ist.

*dwstyle*<br/>
Gibt den Stil des QuickInfo-Steuer Elements an. Weitere Informationen finden Sie im Abschnitt " **Hinweise** " unter " [Erstellen](#create) ".

*dwstyleex*<br/>
Gibt die erweiterte Art des zu erstellenden Steuer Elements an. Eine Liste erweiterter Windows-Stile finden Sie unter dem *dwExStyle* -Parameter für " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) " in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Verwenden Sie `CreateEx` anstelle von `Create` Erweiterte Windows-Stile, die durch den erweiterten Windows-Stil **WS_EX_** angegeben werden.

##  <a name="ctooltipctrl"></a>CToolTipCtrl:: CToolTipCtrl

Erstellt ein `CToolTipCtrl`-Objekt.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Hinweise

Nach dem Erstellen des-Objekts müssen Sie `Create` abrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>CToolTipCtrl::D eltool

Entfernt das von *pwnd* und *nidtool* angegebene Tool aus der Sammlung von Tools, die von einem QuickInfo-Steuerelement unterstützt werden.

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*nidtool*<br/>
ID des Tools.

##  <a name="getbubblesize"></a>CToolTipCtrl:: getbubblesize

Ruft die Größe der QuickInfo ab.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parameter

*lptoolinfo*<br/>
Ein Zeiger auf die toolinfo-Struktur der [QuickInfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) .

### <a name="return-value"></a>Rückgabewert

Die Größe der QuickInfo.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize), wie in der Windows SDK beschrieben.

##  <a name="getcurrenttool"></a>CToolTipCtrl:: getcurrenttool

Ruft Informationen (z. b. die Größe, Position und den Text) des QuickInfo-Fensters ab, das vom aktuellen QuickInfo-Steuerelement angezeigt wird.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*lptoolinfo*|vorgenommen Ein Zeiger auf eine toolinfo-Struktur, die Informationen über das aktuelle [QuickInfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) -Fenster empfängt.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Informationen erfolgreich abgerufen werden. andernfalls false.

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden Informationen zum aktuellen QuickInfo-Fenster abgerufen.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>CToolTipCtrl:: getdelta aytime

Ruft die Anfangs-, Popup-und neuanschau Dauer ab, die für ein QuickInfo-Steuerelement aktuell festgelegt ist.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parameter

*dwDuration*<br/>
Flag, das angibt, welcher Duration-Wert abgerufen wird. Dieser Parameter kann einen der folgenden Werte aufweisen:

- TTDT_AUTOPOP die Zeitspanne abrufen, die das QuickInfo-Fenster sichtbar bleibt, wenn der Zeiger innerhalb des umgebenden Rechtecks eines Tools stationär ist.

- TTDT_INITIAL abrufen, wie lange der Zeiger innerhalb des umgebenden Rechtecks eines Tools stationär bleiben muss, bevor das QuickInfo-Fenster angezeigt wird.

- TTDT_RESHOW die Zeitspanne abrufen, die benötigt wird, bis nachfolgende QuickInfo-Fenster angezeigt werden, wenn der Zeiger von einem Tool zu einem anderen verschoben wird.

### <a name="return-value"></a>Rückgabewert

Die angegebene Verzögerungszeit in Millisekunden.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime), wie in der Windows SDK beschrieben.

##  <a name="getmargin"></a>CToolTipCtrl:: getMargin

Ruft die oberen, linken, unteren und rechten Ränder für ein QuickInfo-Fenster ab.

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parameter

*LPRC*<br/>
Die Adresse einer `RECT` Struktur, die die Rand Informationen empfängt. Die Elemente der [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur definieren kein Begrenzungs Rechteck. Für den Zweck dieser Nachricht werden die Strukturmember wie folgt interpretiert:

|Member|Representation|
|------------|--------------------|
|`top`|Abstand zwischen dem oberen Rand und dem oberen Rand des QuickInfo-Texts in Pixel.|
|`left`|Abstand zwischen dem linken Rand und dem linken Ende des Tip-Texts in Pixel.|
|`bottom`|Abstand zwischen dem unteren und dem unteren Rand des Tip-Texts in Pixel.|
|`right`|Abstand zwischen dem rechten Rand und dem rechten Ende des Tip-Texts in Pixel.|

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin), wie in der Windows SDK beschrieben.

##  <a name="getmaxtipwidth"></a>CToolTipCtrl:: GetMaxTipWidth

Ruft die maximale Breite für ein QuickInfo-Fenster ab.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Breite für ein QuickInfo-Fenster.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth), wie in der Windows SDK beschrieben.

##  <a name="gettext"></a>CToolTipCtrl:: gettext

Ruft den Text ab, der von einem QuickInfo-Steuerelement für ein Tool verwaltet wird.

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parameter

*str*<br/>
Verweis auf ein `CString` Objekt, das den tooltext empfängt.

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*nidtool*<br/>
ID des Tools.

### <a name="remarks"></a>Hinweise

Das Tool wird mit den Parametern *pwnd* und *nidtool* identifiziert. Wenn das Tool bereits zuvor mit dem QuickInfo-Steuerelement registriert wurde, indem ein vorheriger `CToolTipCtrl::AddTool`aufgerufen wird, wird das Objekt, auf das durch den *Str* -Parameter verwiesen wird, dem tooltext zugewiesen.

##  <a name="gettipbkcolor"></a>CToolTipCtrl:: gettipbkcolor

Ruft die Hintergrundfarbe in einem QuickInfo-Fenster ab.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die Hintergrundfarbe darstellt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor), wie in der Windows SDK beschrieben.

##  <a name="gettiptextcolor"></a>CToolTipCtrl:: gettiptextcolor

Ruft die Textfarbe in einem QuickInfo-Fenster ab.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die Textfarbe darstellt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor), wie in der Windows SDK beschrieben.

##  <a name="gettitle"></a>CToolTipCtrl:: getTitle

Ruft den Titel des aktuellen QuickInfo-Steuer Elements ab.

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*pttgt*|vorgenommen Zeiger auf eine [ttgettitle](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) -Struktur, die Informationen über das QuickInfo-Steuerelement enthält. Wenn diese Methode zurückgegeben wird, zeigt das *psztitle* -Member der [ttgettitle](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) -Struktur auf den Text des Titels.|

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) Nachricht, die in der Windows SDK beschrieben wird.

##  <a name="gettoolcount"></a>CToolTipCtrl:: gettoolcount

Ruft die Anzahl der mit dem QuickInfo-Steuerelement registrierten Tools ab.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der mit dem QuickInfo-Steuerelement registrierten Tools an.

##  <a name="gettoolinfo"></a>CToolTipCtrl:: gettoolinfo

Ruft die Informationen ab, die ein QuickInfo-Steuerelement zu einem Tool beibehält.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parameter

*Toolinfo*<br/>
Verweis auf ein `TOOLINFO` Objekt, das den tooltext empfängt.

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*nidtool*<br/>
ID des Tools.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die `hwnd` und `uId` Member der [toolinfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) -Struktur, auf die von *ctoolinfo* verwiesen wird, identifizieren das Tool. Wenn das Tool mit dem QuickInfo-Steuerelement über einen vorherigen-`AddTool`registriert wurde, wird die `TOOLINFO` Struktur mit Informationen über das Tool gefüllt.

##  <a name="hittest"></a>CToolTipCtrl:: HitTest

Testet einen Punkt, um zu bestimmen, ob er sich innerhalb des umgebenden Rechtecks des angegebenen Tools befindet, und ruft, wenn dies der Fall ist, Informationen über das Tool ab.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*pt*<br/>
Ein Zeiger auf ein `CPoint` Objekt, das die Koordinaten des zu testenden Punkts enthält.

*lptoolinfo*<br/>
Ein Zeiger auf die [toolinfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) -Struktur, die Informationen über das Tool enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn sich der durch die Treffer Test Informationen angegebene Punkt innerhalb des umgebenden Rechtecks des Tools befindet. andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn diese Funktion einen Wert ungleich 0 (null) zurückgibt, wird die Struktur, auf die von *lptoolinfo* verwiesen wird, mit Informationen zu dem Tool gefüllt, in dessen Rechteck der Punkt liegt.

Die `TTHITTESTINFO`-Struktur ist wie folgt definiert:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Gibt das Handle des Tools an.

- `pt`

   Gibt die Koordinaten eines Punkts an, wenn sich der Punkt im umgebenden Rechteck des Tools befindet.

- `ti`

   Informationen zum Tool. Weitere Informationen zur `TOOLINFO` Struktur finden Sie unter [CToolTipCtrl:: gettoolinfo](#gettoolinfo).

##  <a name="pop"></a>CToolTipCtrl::P op

Entfernt ein angezeigtes QuickInfo-Fenster aus der Ansicht.

```
void Pop();
```

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_POP](/windows/win32/Controls/ttm-pop), wie in der Windows SDK beschrieben.

##  <a name="popup"></a>CToolTipCtrl::P-opup

Bewirkt, dass das aktuelle QuickInfo-Steuerelement an den Koordinaten der letzten Maus Meldung angezeigt wird.

```
void Popup();
```

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [TTM_POPUP](/windows/win32/Controls/ttm-popup) Nachricht, die in der Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein QuickInfo-Fenster angezeigt.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>CToolTipCtrl:: relayevent

Übergibt eine Maus Meldung an ein QuickInfo-Steuerelement zur Verarbeitung.

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*lpmsg*<br/>
Zeiger auf eine [msg](/windows/win32/api/winuser/ns-winuser-msg) -Struktur, die die zu relaynachricht enthält.

### <a name="remarks"></a>Hinweise

Ein QuickInfo-Steuerelement verarbeitet nur die folgenden Nachrichten, die durch `RelayEvent`an das Tool gesendet werden:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CPropertySheet:: gettabcontrol](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

##  <a name="setdelaytime"></a>CToolTipCtrl:: setdelta Time

Legt die Verzögerungszeit für ein QuickInfo-Steuerelement fest.

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parameter

*nverzögerung*<br/>
Gibt die neue Verzögerungszeit in Millisekunden an.

*dwDuration*<br/>
Flag, das angibt, welcher Duration-Wert abgerufen wird. Eine Beschreibung der gültigen Werte finden Sie unter [CToolTipCtrl:: getdelta-Time](#getdelaytime) .

*Itime*<br/>
Die angegebene Verzögerungszeit in Millisekunden.

### <a name="remarks"></a>Hinweise

Die Verzögerungszeit ist die Zeitspanne, die der Cursor in einem Tool verbleiben muss, bevor das QuickInfo-Fenster angezeigt wird. Die Standard Verzögerungszeit beträgt 500 Millisekunden.

##  <a name="setmargin"></a>CToolTipCtrl:: setMargin

Legt die oberen, linken, unteren und rechten Ränder für ein QuickInfo-Fenster fest.

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parameter

*LPRC*<br/>
Adresse einer `RECT`-Struktur, die die festzulegenden Rand Informationen enthält. Die Elemente der `RECT` Struktur definieren kein Begrenzungs Rechteck. Eine Beschreibung der Rand Informationen finden Sie unter [CToolTipCtrl:: getMargin](#getmargin) .

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin), wie in der Windows SDK beschrieben.

##  <a name="setmaxtipwidth"></a>CToolTipCtrl:: SetMaxTipWidth

Legt die maximale Breite für ein QuickInfo-Fenster fest.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parameter

*iWidth*<br/>
Die maximale ToolTip-Fensterbreite, die festgelegt werden soll.

### <a name="return-value"></a>Rückgabewert

Die vorherige maximale Tip-Breite.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth), wie in der Windows SDK beschrieben.

##  <a name="settipbkcolor"></a>CToolTipCtrl:: Setup-bkcolor

Legt die Hintergrundfarbe in einem QuickInfo-Fenster fest.

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*CLR*<br/>
Die neue Hintergrundfarbe.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor), wie in der Windows SDK beschrieben.

##  <a name="settiptextcolor"></a>CToolTipCtrl:: Setup TextColor

Legt die Textfarbe in einem QuickInfo-Fenster fest.

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*CLR*<br/>
Die neue Textfarbe.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor), wie in der Windows SDK beschrieben.

##  <a name="settitle"></a>CToolTipCtrl:: SetTitle

Fügt einer QuickInfo ein Standard Symbol und eine Titel Zeichenfolge hinzu.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parameter

*uicon*<br/>
Siehe das *Symbol* in [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) in der Windows SDK.

*lpstrautitle*<br/>
Ein Zeiger auf die Titel Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle), wie in der Windows SDK beschrieben.

##  <a name="settoolinfo"></a>CToolTipCtrl:: SetToolInfo

Legt die Informationen fest, die eine QuickInfo für ein Tool beibehält.

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parameter

*lptoolinfo*<br/>
Ein Zeiger auf eine [toolinfo](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) -Struktur, die die festzulegenden Informationen angibt.

##  <a name="settoolrect"></a>CToolTipCtrl:: SetToolRect

Legt ein neues Begrenzungs Rechteck für ein Tool fest.

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*nidtool*<br/>
ID des Tools.

*lprect*<br/>
Ein Zeiger auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die das neue umschließende Rechteck angibt.

##  <a name="setwindowtheme"></a>CToolTipCtrl:: SetWindowTheme

Legt den visuellen Stil des QuickInfo-Fensters fest.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parameter

*pszSubAppName*<br/>
Ein Zeiger auf eine Unicode-Zeichenfolge, die den festzulegenden visuellen Stil enthält.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert wird nicht verwendet.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion emuliert die Funktionalität der [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) Nachricht, wie in der Windows SDK beschrieben.

##  <a name="update"></a>CToolTipCtrl:: Update

Erzwingt, dass das aktuelle Tool neu gezeichnet wird.

```
void Update();
```

##  <a name="updatetiptext"></a>CToolTipCtrl:: updatetiptext

Aktualisiert den QuickInfo-Text für die Tools dieses Steuer Elements.

```
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Zeiger auf den Text für das Tool.

*folgenden*<br/>
Zeiger auf das Fenster, das das Tool enthält.

*nidtool*<br/>
ID des Tools.

*nidtext*<br/>
ID der Zeichen folgen Ressource, die den Text für das Tool enthält.

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBar-Klasse](../../mfc/reference/ctoolbar-class.md)
