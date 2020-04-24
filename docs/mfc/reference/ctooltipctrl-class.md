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
ms.openlocfilehash: 53a5a5b6871680f9758d140174dcceae6c53f568
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752198"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

Kapselt die Funktionalität eines ToolTip-Steuerelements. Dabei handelt es sich um ein kleines Popupfenster, das eine einzelne Textzeile anzeigt, die den Zweck eines Tools der Anwendung beschreibt.

## <a name="syntax"></a>Syntax

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|Erstellt ein `CToolTipCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CToolTipCtrl::Aktivieren](#activate)|Aktiviert und deaktiviert die Werkzeugspitzensteuerung.|
|[CToolTipCtrl::AddTool](#addtool)|Registriert ein Werkzeug mit der Werkzeugspitzensteuerung.|
|[CToolTipCtrl::AdjustRect](#adjustrect)|Konvertiert zwischen dem Textanzeigerechteck eines Werkzeugspitzensteuerelements und dem Fensterrechteck.|
|[CToolTipCtrl::Erstellen](#create)|Erstellt ein Werkzeugspitzensteuerelement und fügt `CToolTipCtrl` es an ein Objekt an.|
|[CToolTipCtrl::CreateEx](#createex)|Erstellt ein QuickInfo-Steuerelement mit den angegebenen erweiterten `CToolTipCtrl` Windows-Stilen und fügt es an ein Objekt an.|
|[CToolTipCtrl::DelTool](#deltool)|Entfernt ein Werkzeug aus dem Werkzeugspitzensteuerelement.|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|Ruft die Größe der Werkzeugspitze ab.|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|Ruft Informationen wie Größe, Position und Text des QuickInfo-Fensters ab, das im aktuellen QuickInfo-Steuerelement angezeigt wird.|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|Ruft die Anfangs-, Popup- und Neuanzeigedauern ab, die derzeit für ein QuickInfo-Steuerelement festgelegt sind.|
|[CToolTipCtrl::GetMargin](#getmargin)|Ruft den oberen, linken, unteren und rechten Rand ab, die für ein QuickInfo-Fenster festgelegt sind.|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|Ruft die maximale Breite für ein QuickInfofenster ab.|
|[CToolTipCtrl::GetText](#gettext)|Ruft den Text ab, den ein QuickInfo-Steuerelement für ein Werkzeug verwaltet.|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|Ruft die Hintergrundfarbe in einem QuickInfofenster ab.|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|Ruft die Textfarbe in einem QuickInfofenster ab.|
|[CToolTipCtrl::GetTitle](#gettitle)|Ruft den Titel des aktuellen QuickInfo-Steuerelements ab.|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|Ruft eine Anzahl der Werkzeuge ab, die von einem QuickInfo-Steuerelement verwaltet werden.|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|Ruft die Informationen ab, die ein QuickInfo-Steuerelement über ein Werkzeug verwaltet.|
|[CToolTipCtrl::HitTest](#hittest)|Testet einen Punkt, um festzustellen, ob er sich innerhalb des umgrenzenden Rechtecks des angegebenen Werkzeugs befindet. Wenn dies der Zutun hat, werden Informationen zum Tool abgerufen.|
|[CToolTipCtrl::Pop](#pop)|Entfernt ein angezeigtes QuickInfo-Fenster aus der Ansicht.|
|[CToolTipCtrl::Popup](#popup)|Bewirkt, dass das aktuelle ToolTip-Steuerelement an den Koordinaten der letzten Mausnachricht angezeigt wird.|
|[CToolTipCtrl::RelayEvent](#relayevent)|Übergibt eine Mausnachricht zur Verarbeitung an ein QuickInfo-Steuerelement.|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|Legt das Initial-, Pop-up- und Reshow-Dauern für ein QuickInfo-Steuerelement fest.|
|[CToolTipCtrl::SetMargin](#setmargin)|Legt den oberen, linken, unteren und rechten Rand für ein QuickInfo-Fenster fest.|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|Legt die maximale Breite für ein QuickInfofenster fest.|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|Legt die Hintergrundfarbe in einem QuickInfo-Fenster fest.|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|Legt die Textfarbe in einem QuickInfofenster fest.|
|[CToolTipCtrl::SetTitle](#settitle)|Fügt einem QuickInfo ein Standardsymbol und eine Titelzeichenfolge hinzu.|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|Legt die Informationen fest, die eine QuickInfo für ein Werkzeug verwaltet.|
|[CToolTipCtrl::SetToolRect](#settoolrect)|Legt ein neues umgrenzendes Rechteck für ein Werkzeug fest.|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|Legt den visuellen Stil des Werkzeugspitzenfensters fest.|
|[CToolTipCtrl::Update](#update)|Erzwingt, dass das aktuelle Werkzeug neu gezeichnet wird.|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|Legt den QuickInfo-Text für ein Werkzeug fest.|

## <a name="remarks"></a>Bemerkungen

Ein "Werkzeug" ist entweder ein Fenster, z. B. ein untergeordnetes Fenster oder Steuerelement, oder ein anwendungsdefinierter rechteckiger Bereich innerhalb des Clientbereichs eines Fensters. Eine QuickInfo wird die meiste Zeit ausgeblendet und erscheint nur, wenn der Benutzer den Cursor auf ein Werkzeug setzt und ihn dort für etwa eine halbe Sekunde belässt. Die QuickInfo wird in der Nähe des Cursors angezeigt und verschwindet, wenn der Benutzer mit der Maus tasten oder den Cursor vom Werkzeug entfernt.

`CToolTipCtrl`bietet die Funktionalität zur Steuerung der Anfangszeit und -dauer der Werkzeugspitze, der Randbreiten, die den Werkzeugspitzentext umgeben, der Breite des Werkzeugspitzenfensters selbst sowie der Hintergrund- und Textfarbe der QuickInfo. Ein einzelnes QuickInfo-Steuerelement kann Informationen für mehr als ein Werkzeug bereitstellen.

Die `CToolTipCtrl` Klasse stellt die Funktionalität des allgemeinen Windows-Tooltippsteuerelements bereit. Dieses Steuerelement (und `CToolTipCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Versionen 3.51 und höher ausgeführt werden.

Weitere Informationen zum Aktivieren von Tooltipps finden Sie unter [Tooltipps in Windows, nicht abgeleitet von CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md).

Weitere Informationen zur `CToolTipCtrl`Verwendung finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CToolTipCtrl](../../mfc/using-ctooltipctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl::Aktivieren

Rufen Sie diese Funktion auf, um ein QuickInfo-Steuerelement zu aktivieren oder zu deaktivieren.

```cpp
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>Parameter

*bAktivieren*<br/>
Gibt an, ob das QuickInfo-Steuerelement aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn *bActivate* TRUE ist, wird das Steuerelement aktiviert. wenn FALSE, ist es deaktiviert.

Wenn ein QuickInfo-Steuerelement aktiv ist, werden die Informationen zum QuickInfo angezeigt, wenn sich der Cursor auf einem Werkzeug befindet, das mit dem Steuerelement registriert ist. Wenn sie inaktiv ist, werden die Informationen zum QuickInfo nicht angezeigt, auch wenn sich der Cursor auf einem Werkzeug befindet.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipCtrl::AddTool

Registriert ein Werkzeug mit der Werkzeugspitzensteuerung.

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

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*nIDText*<br/>
ID der Zeichenfolgenressource, die den Text für das Werkzeug enthält.

*lpRectTool*<br/>
Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die Koordinaten des umgrenzenden Rechtecks des Werkzeugs enthält. Die Koordinaten sind relativ zur oberen linken Ecke des Clientbereichs des Fensters, das von *pWnd*identifiziert wird.

*nIDTool*<br/>
ID des Werkzeugs.

*lpszText*<br/>
Zeiger auf den Text für das Werkzeug. Wenn dieser Parameter den Wert LPSTR_TEXTCALLBACK enthält, gehen TTN_NEEDTEXT Benachrichtigungen an das übergeordnete Fenster, auf das *pWnd* zeigt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Parameter *lpRectTool* und *nIDTool* müssen beide gültig sein, oder wenn *lpRectTool* NULL ist, muss *nIDTool* 0 sein.

Ein QuickInfo-Steuerelement kann mehr als einem Werkzeug zugeordnet werden. Rufen Sie diese Funktion auf, um ein Werkzeug mit dem Werkzeugspitzensteuerelement zu registrieren, sodass die in der QuickInfo gespeicherten Informationen angezeigt werden, wenn sich der Cursor auf dem Werkzeug befindet.

> [!NOTE]
> Sie können eine QuickInfo mit `AddTool`nicht auf ein statisches Steuerelement festlegen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipCtrl::AdjustRect

Konvertiert zwischen dem Textanzeigerechteck eines QuickInfo-Steuerelements und dem Fensterrechteck.

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>Parameter

*lprc*<br/>
Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die entweder ein Werkzeugspitzenfensterrechteck oder ein Textanzeigerechteck enthält.

*bLarger*<br/>
Wenn TRUE, wird *lprc* verwendet, um ein Textanzeigerechteck anzugeben, und es empfängt das entsprechende Fensterrechteck. Wenn FALSE, wird *lprc* verwendet, um ein Fensterrechteck anzugeben, und es erhält das entsprechende Textanzeigerechteck.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Rechteck erfolgreich angepasst wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Elementfunktion berechnet das Textanzeigerechteck eines Werkzeugspitzensteuerelements aus dem Fensterrechteck oder das Rechteck im Werkzeugspitzenfenster, das zum Anzeigen eines angegebenen Textanzeigerechtecks erforderlich ist.

Diese Memberfunktion implementiert das Verhalten der [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)Win32-TTM_ADJUSTRECT , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl::Erstellen

Erstellt ein Werkzeugspitzensteuerelement und fügt `CToolTipCtrl` es an ein Objekt an.

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Werkzeugspitzensteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*dwStyle*<br/>
Gibt den Stil des Werkzeugspitzensteuerelements an. Weitere Informationen finden Sie im Abschnitt **"Bemerkungen".**

### <a name="return-value"></a>Rückgabewert

Ein Wert `CToolTipCtrl` ungleich Null, wenn das Objekt erfolgreich erstellt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CToolTipCtrl` eine in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, um das `CToolTipCtrl` Objekt zu erstellen, und rufen Sie dann auf, `Create` um das Werkzeugspitzensteuerelement zu erstellen und es an das `CToolTipCtrl` Objekt anzuhängen.

Der *dwStyle-Parameter* kann eine beliebige Kombination von [Window Styles](../../mfc/reference/styles-used-by-mfc.md#window-styles)sein. Darüber hinaus verfügt ein QuickInfo-Steuerelement über zwei klassenspezifische Stile: TTS_ALWAYSTIP und TTS_NOPREFIX.

|Style|Bedeutung|
|-----------|-------------|
|TTS_ALWAYSTIP|Gibt an, dass die QuickInfo angezeigt wird, wenn sich der Cursor auf einem Werkzeug befindet, unabhängig davon, ob das Besitzerfenster des Werkzeugspitzensteuerelements aktiv oder inaktiv ist. Ohne diesen Stil wird das Werkzeugspitzensteuerelement angezeigt, wenn das Besitzerfenster des Werkzeugs aktiv ist, jedoch nicht, wenn es inaktiv ist.|
|TTS_NOPREFIX|Dieser Stil verhindert, dass das System das zeichenund (&) von einer Zeichenfolge entfernt. Wenn ein QuickInfo-Steuerelement nicht über den TTS_NOPREFIX-Stil verfügt, entfernt das System automatisch vom Format, sodass eine Anwendung dieselbe Zeichenfolge wie ein Menüelement und als Text in einem QuickInfo-Steuerelement verwenden kann.|

Ein QuickInfo-Steuerelement verfügt über die WS_POPUP und WS_EX_TOOLWINDOW Fensterstile, unabhängig davon, ob Sie sie beim Erstellen des Steuerelements angeben.

Um ein QuickInfo-Steuerelement mit erweiterten Fensterstilen zu erstellen, rufen `Create`Sie [CToolTipCtrl::CreateEx](#createex) anstelle von auf.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnen es dem `CToolTipCtrl` Objekt zu.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*dwStyle*<br/>
Gibt den Stil des Werkzeugspitzensteuerelements an. Weitere Informationen finden Sie im Abschnitt **"Anmerkungen"** unter [Erstellen.](#create)

*dwStyleEx*<br/>
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn andernfalls 0 erfolgreich ist.

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie, anstatt `Create` erweiterte Windows-Formatvorlagen anzuwenden, die durch das Windows-Vorwort für erweiterte Stile **WS_EX_** angegeben werden.

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipCtrl::CToolTipCtrl

Erstellt ein `CToolTipCtrl`-Objekt.

```
CToolTipCtrl();
```

### <a name="remarks"></a>Bemerkungen

Sie müssen `Create` nach dem Erstellen des Objekts aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl::DelTool

Entfernt das von *pWnd* und *nIDTool* angegebene Werkzeug aus der Sammlung von Werkzeugen, die von einem QuickInfo-Steuerelement unterstützt werden.

```cpp
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*nIDTool*<br/>
ID des Werkzeugs.

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipCtrl::GetBubbleSize

Ruft die Größe der Werkzeugspitze ab.

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parameter

*lpToolInfo*<br/>
Ein Zeiger auf die [TOOLINFO-Struktur](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) des Tooltips.

### <a name="return-value"></a>Rückgabewert

Die Größe der Werkzeugspitze.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)Win32-TTM_GETBUBBLESIZE , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl::GetCurrentTool

Ruft Informationen wie Größe, Position und Text des QuickInfo-Fensters ab, das vom aktuellen QuickInfo-Steuerelement angezeigt wird.

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*lpToolInfo*|[out] Zeiger auf eine [TOOLINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) die Informationen über das aktuelle QuickInfo-Fenster empfängt.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Informationen erfolgreich abgerufen werden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel werden Informationen zum aktuellen QuickInfo-Fenster abgerufen.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl::GetDelayTime

Ruft die Anfangs-, Popup- und Neuanzeigedauern ab, die derzeit für ein QuickInfo-Steuerelement festgelegt sind.

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>Parameter

*dwDuration*<br/>
Flag, das angibt, welcher Dauerwert abgerufen wird. Dieser Parameter kann einer der folgenden Werte sein:

- TTDT_AUTOPOP Abrufen der Zeitdauer, für die das Werkzeugspitzenfenster sichtbar bleibt, wenn der Zeiger im umgrenzenden Rechteck eines Werkzeugs stationär ist.

- TTDT_INITIAL Abrufen der Zeitdauer, für die der Zeiger innerhalb des umgrenzten Rechtecks eines Werkzeugs stationär bleiben muss, bevor das Werkzeugspitzenfenster angezeigt wird.

- TTDT_RESHOW Abrufen der Zeit, die für nachfolgende QuickInfofenster benötigt wird, um anzuzeigen, wenn der Zeiger von einem Werkzeug zu einem anderen bewegt wird.

### <a name="return-value"></a>Rückgabewert

Die angegebene Verzögerungszeit in Millisekunden

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime), wie im Windows SDK beschrieben.

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipCtrl::GetMargin

Ruft den oberen, linken, unteren und rechten Rand ab, der für ein QuickInfo-Fenster festgelegt wurde.

```cpp
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>Parameter

*lprc*<br/>
Adresse einer `RECT` Struktur, die die Margin-Informationen erhält. Die Elemente der [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) definieren kein umgrenzendes Rechteck. Für die Zwecke dieser Meldung werden die Strukturmember wie folgt interpretiert:

|Member|Darstellung|
|------------|--------------------|
|`top`|Abstand zwischen dem oberen Rand und dem oberen Rand des QuickInfotexts in Pixel.|
|`left`|Abstand zwischen dem linken Rand und dem linken Ende des Spitzentextes in Pixel.|
|`bottom`|Abstand zwischen dem unteren Rand und dem unteren Rand des Spitzentextes in Pixel.|
|`right`|Abstand zwischen dem rechten Rand und dem rechten Ende des Spitzentextes in Pixeln.|

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)Win32-TTM_GETMARGIN , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipCtrl::GetMaxTipWidth

Ruft die maximale Breite für ein QuickInfofenster ab.

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>Rückgabewert

Die maximale Breite für ein Werkzeugspitzenfenster.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)Win32-TTM_GETMAXTIPWIDTH , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipCtrl::GetText

Ruft den Text ab, den ein QuickInfo-Steuerelement für ein Werkzeug verwaltet.

```cpp
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Verweis auf `CString` ein Objekt, das den Text des Werkzeugs empfängt.

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*nIDTool*<br/>
ID des Werkzeugs.

### <a name="remarks"></a>Bemerkungen

Die Parameter *pWnd* und *nIDTool* identifizieren das Werkzeug. Wenn dieses Werkzeug zuvor über einen vorherigen Aufruf von `CToolTipCtrl::AddTool`beim Werkzeugspitzensteuerelement registriert wurde, wird dem Objekt, auf das der Parameter *str* verweist, der Text des Werkzeugs zugewiesen.

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl::GetTipBkColor

Ruft die Hintergrundfarbe in einem QuickInfofenster ab.

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die Hintergrundfarbe darstellt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor), wie im Windows SDK beschrieben.

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl::GetTipTextColor

Ruft die Textfarbe in einem QuickInfofenster ab.

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die Textfarbe darstellt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)Win32-TTM_GETTIPTEXTCOLOR , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl::GetTitle

Ruft den Titel des aktuellen QuickInfo-Steuerelements ab.

```cpp
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*pttgt*|[out] Zeiger auf eine [TTGETTITLE-Struktur,](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) die Informationen zum ToolTip-Steuerelement enthält. Wenn diese Methode zurückgegeben wird, zeigt das *pszTitle-Element* der [TTGETTITLE-Struktur](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) auf den Text des Titels.|

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) Nachricht, die im Windows SDK beschrieben wird.

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl::GetToolCount

Ruft eine Anzahl der Werkzeuge ab, die mit dem Werkzeugspitzensteuerelement registriert sind.

```
int GetToolCount() const;
```

### <a name="return-value"></a>Rückgabewert

Eine Anzahl von Werkzeugen, die bei der Werkzeugspitzensteuerung registriert sind.

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipCtrl::GetToolInfo

Ruft die Informationen ab, die ein QuickInfo-Steuerelement über ein Werkzeug verwaltet.

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>Parameter

*ToolInfo*<br/>
Verweis auf `TOOLINFO` ein Objekt, das den Text des Werkzeugs empfängt.

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*nIDTool*<br/>
ID des Werkzeugs.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die `hwnd` `uId` und Mitglieder der [TOOLINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) auf die von *CToolInfo* verwiesen wird, identifizieren das Tool. Wenn dieses Werkzeug durch einen vorherigen Aufruf von `AddTool`beim `TOOLINFO` Werkzeugspitzensteuerelement registriert wurde, wird die Struktur mit Informationen über das Werkzeug gefüllt.

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipCtrl::HitTest

Testet einen Punkt, um zu ermitteln, ob er sich innerhalb des umgrenzenden Rechtecks des angegebenen Werkzeugs befindet, und ruft, falls ja, Informationen über das Werkzeug ab.

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*Pt*<br/>
Zeiger auf `CPoint` ein Objekt, das die Koordinaten des zu testenden Punktes enthält.

*lpToolInfo*<br/>
Zeiger auf [die TOOLINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) die Informationen über das Werkzeug enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn sich der durch die Treffertestinformationen angegebene Punkt innerhalb des umgebenden Rechtecks des Werkzeugs befindet. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn diese Funktion einen Wert ungleich Null zurückgibt, wird die Struktur, auf die *lpToolInfo* zeigt, mit Informationen über das Werkzeug gefüllt, in dessen Rechteck der Punkt liegt.

Die `TTHITTESTINFO` Struktur ist wie folgt definiert:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   Gibt den Ziehpunkt des Werkzeugs an.

- `pt`

   Gibt die Koordinaten eines Punktes an, wenn sich der Punkt im umgrenzenden Rechteck des Werkzeugs befindet.

- `ti`

   Informationen zum Tool. Weitere Informationen zur `TOOLINFO` Struktur finden Sie unter [CToolTipCtrl::GetToolInfo](#gettoolinfo).

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl::Pop

Entfernt ein angezeigtes QuickInfo-Fenster aus der Ansicht.

```cpp
void Pop();
```

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_POP](/windows/win32/Controls/ttm-pop)Win32-TTM_POP , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl::Popup

Bewirkt, dass das aktuelle QuickInfo-Steuerelement an den Koordinaten der letzten Mausnachricht angezeigt wird.

```cpp
void Popup();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [TTM_POPUP](/windows/win32/Controls/ttm-popup) Nachricht, die im Windows SDK beschrieben wird.

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein QuickInfo-Fenster angezeigt.

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl::RelayEvent

Übergibt eine Mausnachricht zur Verarbeitung an ein QuickInfo-Steuerelement.

```cpp
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>Parameter

*lpMsg*<br/>
Zeiger auf eine [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die die zu relaysende Nachricht enthält.

### <a name="remarks"></a>Bemerkungen

Eine QuickInfo-Steuerung verarbeitet nur die folgenden Meldungen, die an sie gesendet werden: `RelayEvent`

|WM_LBUTTONDOWN|Wm_mousemove|
|---------------------|-------------------|
|Wm_lbuttonup|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol).

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipCtrl::SetDelayTime

Legt die Verzögerungszeit für ein QuickInfo-Steuerelement fest.

```cpp
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>Parameter

*nDelay*<br/>
Gibt die neue Verzögerungszeit in Millisekunden an.

*dwDuration*<br/>
Flag, das angibt, welcher Dauerwert abgerufen wird. Eine Beschreibung der gültigen Werte finden Sie unter [CToolTipCtrl::GetDelayTime.](#getdelaytime)

*iTime*<br/>
Die angegebene Verzögerungszeit in Millisekunden.

### <a name="remarks"></a>Bemerkungen

Die Verzögerungszeit ist die Zeitdauer, die der Cursor auf einem Werkzeug verbleiben muss, bevor das Werkzeugspitzenfenster angezeigt wird. Die Standardverzögerungszeit beträgt 500 Millisekunden.

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipCtrl::SetMargin

Legt den oberen, linken, unteren und rechten Rand für ein QuickInfo-Fenster fest.

```cpp
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>Parameter

*lprc*<br/>
Adresse einer `RECT` Struktur, die die festzulegenden Margin-Informationen enthält. Die Elemente `RECT` der Struktur definieren kein umgrenzendes Rechteck. Eine Beschreibung der Margin-Informationen finden Sie unter [CToolTipCtrl::GetMargin.](#getmargin)

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)Win32-TTM_SETMARGIN , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipCtrl::SetMaxTipWidth

Legt die maximale Breite für ein QuickInfofenster fest.

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>Parameter

*iWidth*<br/>
Die maximale Zusendefensterbreite des Werkzeugspitzenfensters.

### <a name="return-value"></a>Rückgabewert

Die vorherige maximale Spitzenbreite.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)Win32-TTM_SETMAXTIPWIDTH , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipCtrl::SetTipBkColor

Legt die Hintergrundfarbe in einem QuickInfo-Fenster fest.

```cpp
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*Clr*<br/>
Die neue Hintergrundfarbe.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor), wie im Windows SDK beschrieben.

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipCtrl::SetTipTextColor

Legt die Textfarbe in einem QuickInfofenster fest.

```cpp
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*Clr*<br/>
Die neue Textfarbe.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor), wie im Windows SDK beschrieben.

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipCtrl::SetTitle

Fügt einem QuickInfo ein Standardsymbol und eine Titelzeichenfolge hinzu.

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>Parameter

*uIcon*<br/>
Siehe *Symbol* in [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle) im Windows SDK.

*lpstrTitle*<br/>
Zeiger auf die Titelzeichenfolge.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)Win32-TTM_SETTITLE , wie im Windows SDK beschrieben.

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipCtrl::SetToolInfo

Legt die Informationen fest, die eine QuickInfo für ein Werkzeug verwaltet.

```cpp
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>Parameter

*lpToolInfo*<br/>
Ein Zeiger auf eine [TOOLINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) die die festzulegenden Informationen angibt.

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipCtrl::SetToolRect

Legt ein neues umgrenzendes Rechteck für ein Werkzeug fest.

```cpp
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*nIDTool*<br/>
ID des Werkzeugs.

*lpRect*<br/>
Zeiger auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die das neue umgrenzte Rechteck angibt.

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipCtrl::SetWindowTheme

Legt den visuellen Stil des Werkzeugspitzenfensters fest.

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>Parameter

*pszSubAppName*<br/>
Ein Zeiger auf eine Unicode-Zeichenfolge, die den festzulegenden visuellen Stil enthält.

### <a name="return-value"></a>Rückgabewert

Der Rückgabewert wird nicht verwendet.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion emuliert die Funktionalität der [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) Nachricht, wie im Windows SDK beschrieben.

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl::Update

Erzwingt, dass das aktuelle Werkzeug neu gezeichnet wird.

```cpp
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipCtrl::UpdateTipText

Aktualisiert den Tooltipptext für die Werkzeuge dieses Steuerelements.

```cpp
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
Zeiger auf den Text für das Werkzeug.

*pWnd*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Werkzeug enthält.

*nIDTool*<br/>
ID des Werkzeugs.

*nIDText*<br/>
ID der Zeichenfolgenressource, die den Text für das Werkzeug enthält.

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBar-Klasse](../../mfc/reference/ctoolbar-class.md)
