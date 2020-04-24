---
title: CStatusBarCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 57d040a7efd87d384e0aaa6275593bc91f38cc86
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753035"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Statusleisten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStatusBarCtrl::CStatusBarCtrl](#cstatusbarctrl)|Erstellt ein `CStatusBarCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStatusBarCtrl::Erstellen](#create)|Erstellt ein Statusleistensteuerelement und fügt `CStatusBarCtrl` es an ein Objekt an.|
|[CStatusBarCtrl::CreateEx](#createex)|Erstellt ein Statusleistensteuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein `CStatusBarCtrl` Objekt an.|
|[CStatusBarCtrl::DrawItem](#drawitem)|Wird aufgerufen, wenn sich ein visueller Aspekt eines Besitzerzeichnungsstatusleistensteuerelements ändert.|
|[CStatusBarCtrl::GetBorders](#getborders)|Ruft die aktuellen Breiten der horizontalen und vertikalen Ränder eines Statusleistensteuerelements ab.|
|[CStatusBarCtrl::GetIcon](#geticon)|Ruft das Symbol für ein Teil (auch als Bereich bezeichnet) im aktuellen Statusleistensteuerelement ab.|
|[CStatusBarCtrl::GetParts](#getparts)|Ruft eine Anzahl der Teile in einem Statusleistensteuerelement ab.|
|[CStatusBarCtrl::GetRect](#getrect)|Ruft das umgrenzende Rechteck eines Teils in einem Statusleistensteuerelement ab.|
|[CStatusBarCtrl::GetText](#gettext)|Ruft den Text aus dem angegebenen Teil eines Statusleistensteuerelements ab.|
|[CStatusBarCtrl::GetTextLength](#gettextlength)|Rufen Sie die Länge des Texts in Zeichen aus dem angegebenen Teil eines Statusleistensteuerelements ab.|
|[CStatusBarCtrl::GetTipText](#gettiptext)|Ruft den QuickInfo-Text für einen Bereich in einer Statusleiste ab.|
|[CStatusBarCtrl::IsSimple](#issimple)|Überprüft ein Statusfenstersteuerelement, um festzustellen, ob es sich im einfachen Modus befindet.|
|[CStatusBarCtrl::SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe in einer Statusleiste fest.|
|[CStatusBarCtrl::SetIcon](#seticon)|Legt das Symbol für einen Bereich in einer Statusleiste fest.|
|[CStatusBarCtrl::SetMinHeight](#setminheight)|Legt die Minimale Höhe des Zeichenbereichs eines Statusleistensteuerelements fest.|
|[CStatusBarCtrl::SetParts](#setparts)|Legt die Anzahl der Teile in einem Statusleistensteuerelement und die Koordinate des rechten Rands jedes Teils fest.|
|[CStatusBarCtrl::SetSimple](#setsimple)|Gibt an, ob ein Statusleistensteuerelement einfachen Text oder alle `SetParts`Steuerelementteile anzeigt, die durch einen vorherigen Aufruf von festgelegt wurden.|
|[CStatusBarCtrl::SetText](#settext)|Legt den Text im bestimmten Teil eines Statusleisten-Steuerelements fest.|
|[CStatusBarCtrl::SetTipText](#settiptext)|Legt den QuickInfo-Text für einen Bereich in einer Statusleiste fest.|

## <a name="remarks"></a>Bemerkungen

Ein "Statusleistensteuerelement" ist ein horizontales Fenster, das normalerweise am unteren Rand eines übergeordneten Fensters angezeigt wird, in dem eine Anwendung verschiedene Arten von Statusinformationen anzeigen kann. Das Statusleistensteuerelement kann in Teile unterteilt werden, um mehr als einen Informationstyp anzuzeigen.

Dieses Steuerelement (und `CStatusBarCtrl` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Weitere Informationen zur `CStatusBarCtrl`Verwendung von finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl::Erstellen

Erstellt ein Statusleistensteuerelement und fügt `CStatusBarCtrl` es an ein Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Statusleistensteuerelements an. Wenden Sie eine beliebige Kombination von Statusleistensteuerungsstilen an, die in [allgemeinen Steuerelementstilen](/windows/win32/Controls/common-control-styles) im Windows SDK aufgeführt sind. Dieser Parameter muss den stilWS_CHILD enthalten. Es sollte auch den WS_VISIBLE Stil enthalten.

*Rect*<br/>
Gibt die Größe und Position des Statusleistensteuerelements an. Dabei kann es sich entweder um ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) handelt.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Statusleistensteuerelements an, in der Regel eine `CDialog`. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Statusleistensteuerelements an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CStatusBarCtrl` eine in zwei Schritten. Rufen Sie zuerst den Konstruktor `Create`auf, und rufen Sie dann auf, das das Statusleistensteuerelement erstellt und an das `CStatusBarCtrl` Objekt anfügt.

Die Standardposition eines Statusfensters befindet sich am unteren Rand des übergeordneten Fensters, Sie können jedoch die CCS_TOP-Format angeben, damit sie oben im Clientbereich des übergeordneten Fensters angezeigt wird. Sie können den SBARS_SIZEGRIP Stil angeben, der einen Größengriff am rechten Ende des Statusfensters einschließen soll. Das Kombinieren der CCS_TOP- und SBARS_SIZEGRIP-Stile wird nicht empfohlen, da der resultierende Größengriff nicht funktionsfähig ist, obwohl das System ihn im Statusfenster zeichnet.

Um eine Statusleiste mit erweiterten Fensterstilen zu erstellen, rufen `Create`Sie [CStatusBarCtrl::CreateEx](#createex) anstelle von auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::CreateEx

Erstellt ein Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CStatusBarCtrl` Objekt zu.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwExStyle*<br/>
Gibt den erweiterten Stil des zu erstellenden Steuerelements an. Eine Liste der erweiterten Windows-Stile finden Sie im *dwExStyle-Parameter* für [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) im Windows SDK.

*dwStyle*<br/>
Gibt den Stil des Statusleistensteuerelements an. Wenden Sie eine beliebige Kombination von Statusleistensteuerungsstilen an, die in [allgemeinen Steuerelementstilen](/windows/win32/Controls/common-control-styles) im Windows SDK aufgeführt sind. Dieser Parameter muss den stilWS_CHILD enthalten. Es sollte auch den WS_VISIBLE Stil enthalten.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des zu erstellenden Fensters in den Clientkoordinaten von *pParentWnd*beschreibt.

*pParentWnd*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Steuerelement ist.

*nID*<br/>
Die untergeordnete Fenster-ID des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Verwenden `CreateEx` Sie anstelle von [Erstellen,](#create) um erweiterte Windows-Formatvorlagen anzuwenden, die durch das Erweiterte Windows-Stilvorwort **WS_EX_** angegeben werden.

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl::CStatusBarCtrl

Erstellt ein `CStatusBarCtrl`-Objekt.

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Besitzerzeichnungsstatusleistensteuerelements ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein langer Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die Informationen über den erforderlichen Zeichnungstyp enthält.

### <a name="remarks"></a>Bemerkungen

Das `itemAction` Element `DRAWITEMSTRUCT` der Struktur definiert die Zeichnungsaktion, die ausgeführt werden soll.

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, um `CStatusBarCtrl` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren.

Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den in *lpDrawItemStruct* bereitgestellten Anzeigekontext ausgewählt wurden, bevor diese Memberfunktion beendet wird.

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarCtrl::GetBorders

Ruft die aktuellen Breiten des Statusleistensteuerelements des horizontalen und vertikalen Rahmens sowie des Abstands zwischen Rechtecken ab.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parameter

*pGrenzen*<br/>
Adresse eines ganzzahligen Arrays mit drei Elementen. Das erste Element erhält die Breite des horizontalen Rahmens, das zweite die Breite des vertikalen Rahmens und das dritte die Breite des Rahmens zwischen den Rechtecken.

*nHorz*<br/>
Verweis auf eine ganze Zahl, die die Breite des horizontalen Rahmens empfängt.

*nVert*<br/>
Verweis auf eine ganze Zahl, die die Breite des vertikalen Rahmens empfängt.

*nSpacing*<br/>
Verweis auf eine ganze Zahl, die die Breite des Rahmens zwischen Rechtecken empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Rahmen bestimmen den Abstand zwischen dem äußeren Rand des Steuerelements und den Rechtecken innerhalb des Steuerelements, die Text enthalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarCtrl::GetIcon

Ruft das Symbol für ein Teil (auch als Bereich bezeichnet) im aktuellen Statusleistensteuerelement ab.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parameter

|Parameter|BESCHREIBUNG|
|---------------|-----------------|
|*Ipart*|[in] Der nullbasierte Index des Teils, das das abzudann ausgehende Symbol enthält. Wenn dieser Parameter -1 ist, wird davon ausgegangen, dass die Statusleiste eine einfache Modusstatusleiste ist.|

### <a name="return-value"></a>Rückgabewert

Das Handle zum Symbol, wenn die Methode erfolgreich war; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode sendet die [SB_GETICON](/windows/win32/Controls/sb-geticon) Nachricht, die im Windows SDK beschrieben wird.

Ein Statusleistensteuerelement besteht aus einer Zeile von Textausgabebereichen, die auch als Teile bezeichnet werden. Weitere Informationen zur Statusleiste finden Sie unter [Statusleistenimplementierung in MFC](../../mfc/status-bar-implementation-in-mfc.md) und [Festlegen des Modus eines CStatusBarCtrl-Objekts](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird `m_statusBar`eine Variable definiert, , die für den Zugriff auf das aktuelle Statusleistensteuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein Symbol in zwei Bereiche des aktuellen Statusleistensteuerelements kopiert. In einem früheren Abschnitt des Codebeispiels haben wir ein Statusleistensteuerelement mit drei Bereichen erstellt und dann dem ersten Bereich ein Symbol hinzugefügt. In diesem Beispiel wird das Symbol aus dem ersten Bereich abgerufen und dann dem zweiten und dritten Bereich hinzugefügt.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarCtrl::GetParts

Ruft eine Anzahl der Teile in einem Statusleistensteuerelement ab.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parameter

*nParts*<br/>
Anzahl der Teile, für die Koordinaten abgerufen werden sollen. Wenn dieser Parameter größer als die Anzahl der Teile im Steuerelement ist, ruft die Nachricht Koordinaten nur für vorhandene Teile ab.

*pParts*<br/>
Adresse eines ganzzahligen Arrays mit der gleichen Anzahl von Elementen wie die Anzahl der von *nParts*angegebenen Teile . Jedes Element im Array empfängt die Client-Koordinate des rechten Rands des entsprechenden Teils. Wenn ein Element auf - 1 gesetzt ist, erstreckt sich die Position des rechten Rands für dieses Teil bis zum rechten Rand der Statusleiste.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Teile im Steuerelement, wenn sie erfolgreich sind, oder Null andernfalls.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion ruft auch die Koordinate der rechten Kante der angegebenen Anzahl von Teilen ab.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarCtrl::GetRect

Ruft das umgrenzende Rechteck eines Teils in einem Statusleistensteuerelement ab.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nPane*<br/>
Nullbasierter Index des Teils, dessen umgrenztes Rechteck abgerufen werden soll.

*lpRect*<br/>
Adresse einer [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die das umgrenzende Rechteck empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarCtrl::GetText

Ruft den Text aus dem angegebenen Teil eines Statusleistensteuerelements ab.

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Adresse des Puffers, der den Text empfängt. Dieser Parameter ist eine null-terminierte Zeichenfolge.

*nPane*<br/>
Nullbasierter Index des Teils, aus dem Text abgerufen werden soll.

*pType*<br/>
Zeiger auf eine ganze Zahl, die die Typinformationen empfängt. Der Typ kann einer der folgenden Werte sein:

- **0** Der Text wird mit einem Rahmen gezeichnet, der niedriger als die Ebene der Statusleiste angezeigt wird.

- SBT_NOBORDERS Der Text wird ohne Grenzen gezeichnet.

- SBT_POPOUT Der Text wird mit einem Rahmen gezeichnet, der höher als die Ebene der Statusleiste angezeigt wird.

- SBT_OWNERDRAW Wenn der Text den SBT_OWNERDRAW Zeichnungstyp s. hat, empfängt *pType* diese Meldung und gibt den 32-Bit-Wert zurück, der dem Text zugeordnet ist, anstatt der Länge und dem Vorgangstyp.

### <a name="return-value"></a>Rückgabewert

Die Länge des Textes oder eines [CStrings,](../../atl-mfc-shared/reference/cstringt-class.md) der den aktuellen Text enthält, in Zeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarCtrl::GetTextLength

Ruft die Länge des Textes aus dem angegebenen Teil eines Statusleistensteuerelements in Zeichen ab.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parameter

*nPane*<br/>
Nullbasierter Index des Teils, aus dem Text abgerufen werden soll.

*pType*<br/>
Zeiger auf eine ganze Zahl, die die Typinformationen empfängt. Der Typ kann einer der folgenden Werte sein:

- **0** Der Text wird mit einem Rahmen gezeichnet, der niedriger als die Ebene der Statusleiste angezeigt wird.

- SBT_NOBORDERS Der Text wird ohne Grenzen gezeichnet.

- SBT_OWNERDRAW Der Text wird vom übergeordneten Fenster gezeichnet.

- SBT_POPOUT Der Text wird mit einem Rahmen gezeichnet, der höher als die Ebene der Statusleiste angezeigt wird.

### <a name="return-value"></a>Rückgabewert

Die Länge des Textes in Zeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarCtrl::GetTipText

Ruft den QuickInfo-Text für einen Bereich in einer Statusleiste ab.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parameter

*nPane*<br/>
Der nullbasierte Index des Statusleistenbereichs, um den QuickInfo-Text zu empfangen.

### <a name="return-value"></a>Rückgabewert

Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den Text enthält, der in der QuickInfo verwendet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)Win32-SB_GETTIPTEXT , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarCtrl::IsSimple

Überprüft ein Statusfenstersteuerelement, um festzustellen, ob es sich im einfachen Modus befindet.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn sich das Statusfenstersteuerelement im einfachen Modus befindet; andernfalls Null.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)Win32-SB_ISSIMPLE , wie im Windows SDK beschrieben.

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarCtrl::SetBkColor

Legt die Hintergrundfarbe in einer Statusleiste fest.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parameter

*Cr*<br/>
COLORREF-Wert, der die neue Hintergrundfarbe angibt. Geben Sie den wert CLR_DEFAULT an, der bewirkt, dass die Statusleiste die Standardhintergrundfarbe verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die vorherige Standardhintergrundfarbe darstellt.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der Win32-Meldung [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor), wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarCtrl::SetIcon

Legt das Symbol für einen Bereich in einer Statusleiste fest.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parameter

*nPane*<br/>
Der nullbasierte Index des Bereichs, der das Symbol empfängt. Wenn dieser Parameter -1 ist, wird davon ausgegangen, dass die Statusleiste eine einfache Statusleiste ist.

*hIcon*<br/>
Behandeln Sie das zu setzende Symbol. Wenn dieser Wert NULL ist, wird das Symbol aus dem Teil entfernt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [SB_SETICON](/windows/win32/Controls/sb-seticon)Win32-SB_SETICON , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CStatusBarCtrl::SetBkColor](#setbkcolor).

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarCtrl::SetMinHeight

Legt die Minimale Höhe des Zeichenbereichs eines Statusleistensteuerelements fest.

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parameter

*Nmin*<br/>
Minimale Höhe (in Pixel) des Steuerelements.

### <a name="remarks"></a>Bemerkungen

Die minimale Höhe ist die Summe von *nMin* und die doppelte Breite (in Pixel) des vertikalen Rahmens des Statusleistensteuerelements.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarCtrl::SetParts

Legt die Anzahl der Teile in einem Statusleistensteuerelement und die Koordinate des rechten Rands jedes Teils fest.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parameter

*nParts*<br/>
Anzahl der festzulegenden Teile. Die Anzahl der Teile darf nicht größer als 255 sein.

*pWidths*<br/>
Adresse eines ganzzahligen Arrays mit der gleichen Anzahl von Elementen wie Teile, die von *nParts*angegeben werden. Jedes Element im Array gibt die Position in Clientkoordinaten des rechten Rands des entsprechenden Teils an. Wenn ein Element - 1 ist, erstreckt sich die Position der rechten Kante für dieses Teil bis zum rechten Rand des Steuerelements.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarCtrl::SetSimple

Gibt an, ob ein Statusleistensteuerelement einfachen Text oder alle Steuerelementteile anzeigt, die durch einen vorherigen Aufruf von [SetParts](#setparts)festgelegt wurden.

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parameter

*bEinfach*<br/>
[in] Display-Typ-Flag. Wenn dieser Parameter TRUE ist, zeigt das Steuerelement einfachen Text an. Wenn es FALSE ist, werden mehrere Teile angezeigt.

### <a name="return-value"></a>Rückgabewert

Es wird immer 0 zurückgegeben.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung das Statusleistensteuerelement von nicht einfach auf einfach oder umgekehrt ändert, zeichnet das System das Steuerelement sofort neu.

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarCtrl::SetText

Legt den Text im bestimmten Teil eines Statusleisten-Steuerelements fest.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Adresse einer mit NULL endenden Zeichenfolge, die den festzulegenden Text angibt. Wenn *nType* SBT_OWNERDRAW ist, stellt *lpszText* 32 Bit Daten dar.

*nPane*<br/>
Der nullbasierte Index des festzulegenden Teils. Wenn dieser Wert 255 ist, wird angenommen, dass das Statusleisten-Steuerelement ein einfaches Steuerelement mit nur einem Teil ist.

*nType*<br/>
Der Typ des Zeichenvorgangs. Eine Liste der möglichen Werte [finden Sie in SB_SETTEXT Meldung.](/windows/win32/Controls/sb-settext)

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Nachricht macht den geänderten Teil des Steuerelements ungültig, sodass der neue Text angezeigt wird, wenn das Steuerelement das nächste WM_PAINT Nachricht empfängt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarCtrl::SetTipText

Legt den QuickInfo-Text für einen Bereich in einer Statusleiste fest.

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parameter

*nPane*<br/>
Der nullbasierte Index des Statusleistenbereichs, um den QuickInfo-Text zu empfangen.

*pszTipText*<br/>
Ein Zeiger auf eine Zeichenfolge, die den QuickInfo-Text enthält.

### <a name="remarks"></a>Bemerkungen

Diese Memberfunktion implementiert das Verhalten der [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)Win32-SB_SETTIPTEXT , wie im Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl-Klasse](../../mfc/reference/ctoolbarctrl-class.md)
