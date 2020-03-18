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
ms.openlocfilehash: 8c33aa4d77eeeeca69e50dc63982ff4d7e8bd505
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426354"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl-Klasse

Stellt die Funktionalität des allgemeinen Windows-Statusleisten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[Cstatus-Barcode STRG:: cstatus-barstrg](#cstatusbarctrl)|Erstellt ein `CStatusBarCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[Cstatus-Barcode STRG:: Create](#create)|Erstellt ein StatusBar-Steuerelement und fügt es an ein `CStatusBarCtrl` Objekt an.|
|[Cstatus-Barcode STRG:: up-Ex](#createex)|Erstellt ein StatusBar-Steuerelement mit den angegebenen erweiterten Windows-Stilen und fügt es an ein `CStatusBarCtrl` Objekt an.|
|[Cstatus-STRG::D rawitem](#drawitem)|Wird aufgerufen, wenn sich ein visueller Aspekt eines Besitzers-Status leisten-Steuer Elements ändert.|
|[Cstatus-barstrg:: getrahmens](#getborders)|Ruft die aktuelle Breite der horizontalen und vertikalen Rahmen eines StatusBar-Steuer Elements ab.|
|[Cstatus-barstrg:: getIcon](#geticon)|Ruft das Symbol für einen Teil (auch als Bereich bezeichnet) im aktuellen StatusBar-Steuerelement ab.|
|[Cstatus-barstrg:: GetParts](#getparts)|Ruft die Anzahl der Teile in einem StatusBar-Steuerelement ab.|
|[Cstatus-Barcode STRG:: GetRect](#getrect)|Ruft das umgebende Rechteck eines Teils in einem StatusBar-Steuerelement ab.|
|[Cstatus-barstrg:: gettext](#gettext)|Ruft den Text aus dem angegebenen Teil eines StatusBar-Steuer Elements ab.|
|[Cstatus-barstrg:: getTextLength](#gettextlength)|Ruft die Länge des Texts aus dem angegebenen Teil eines StatusBar-Steuer Elements in Zeichen ab.|
|[Cstatus-barstrg:: GetTipText](#gettiptext)|Ruft den QuickInfo-Text für einen Bereich in einer Statusleiste ab.|
|[CStatusBarCtrl:: IsSimple](#issimple)|Überprüft ein Statusfenster-Steuerelement, um zu bestimmen, ob es sich im einfachen Modus befindet.|
|[Cstatu\barctrl:: SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe in einer Statusleiste fest.|
|[Cstatus-barctrl:: abticon](#seticon)|Legt das Symbol für einen Bereich in einer Statusleiste fest.|
|[Cstatuin barctrl:: setMinHeight](#setminheight)|Legt die Mindesthöhe des Zeichnungs Bereichs eines Status leisten Steuer Elements fest.|
|[Cstatus-barctrl:: SetParts](#setparts)|Legt die Anzahl der Teile in einem StatusBar-Steuerelement und die Koordinate des rechten Rands der einzelnen Teile fest.|
|[Cstatus-barctrl:: SetSimple](#setsimple)|Gibt an, ob ein Status leisten-Steuerelement einfachen Text anzeigt oder alle Steuerelement Teile anzeigt, die durch einen vorherigen `SetParts`aufgerufen wurden.|
|[Cstatus-barctrl:: SetText](#settext)|Legt den Text im bestimmten Teil eines Statusleisten-Steuerelements fest.|
|[Cstatulaufbarctrl:: Setup Text](#settiptext)|Legt den QuickInfo-Text für einen Bereich in einer Statusleiste fest.|

## <a name="remarks"></a>Hinweise

Ein "StatusBar-Steuerelement" ist ein horizontales Fenster, das normalerweise am unteren Rand eines übergeordneten Fensters angezeigt wird, in dem eine Anwendung verschiedene Arten von Statusinformationen anzeigen kann. Das StatusBar-Steuerelement kann in Teile aufgeteilt werden, um mehr als eine Art von Informationen anzuzeigen.

Dieses Steuerelement (und damit auch die `CStatusBarCtrl`-Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Weitere Informationen zur Verwendung von `CStatusBarCtrl`finden Sie unter Steuer [Elemente](../../mfc/controls-mfc.md) und [Verwenden von cstatus-barctrl](../../mfc/using-cstatusbarctrl.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxcmn.h

##  <a name="create"></a>Cstatus-Barcode STRG:: Create

Erstellt ein StatusBar-Steuerelement und fügt es an ein `CStatusBarCtrl` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*<br/>
Gibt den Stil des StatusBar-Steuer Elements an. Wenden Sie eine beliebige Kombination von Status leisten-Steuerelement Formaten an, die in [allgemeinen Steuer](/windows/win32/Controls/common-control-styles) Element Formaten in der Windows SDK Dieser Parameter muss den WS_CHILD Stil enthalten. Sie sollte auch den WS_VISIBLE Stil enthalten.

*Rect*<br/>
Gibt die Größe und Position des StatusBar-Steuer Elements an. Dabei kann es sich entweder um ein [CRect](../../atl-mfc-shared/reference/crect-class.md) -Objekt oder um eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur handeln.

*pparser*<br/>
Gibt das übergeordnete Fenster des Status leisten Steuer Elements an, in der Regel eine `CDialog`. Er darf nicht NULL sein.

*NID*<br/>
Gibt die ID des StatusBar-Steuer Elements an.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Sie erstellen eine `CStatusBarCtrl` in zwei Schritten. Zuerst wird der Konstruktor aufgerufen und dann `Create`aufgerufen, der das StatusBar-Steuerelement erstellt und an das `CStatusBarCtrl` Objekt anfügt.

Die Standardposition eines Status Fensters befindet sich am unteren Rand des übergeordneten Fensters, Sie können jedoch den CCS_TOP Stil angeben, damit er am oberen Rand des Client Bereichs des übergeordneten Fensters angezeigt wird. Sie können den SBARS_SIZEGRIP Stil angeben, um einen Größen Zieh Punkt am rechten Ende des Status Fensters einzuschließen. Das Kombinieren der CCS_TOP-und SBARS_SIZEGRIP Stile wird nicht empfohlen, da der resultierende Größen Zieh Punkt nicht funktionsfähig ist, auch wenn das System ihn im Statusfenster zeichnet.

Rufen Sie zum Erstellen einer Statusleiste mit erweiterten Fenster Stilen [CStatusBarCtrl::](#createex) up-Ex anstelle von `Create`auf.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

##  <a name="createex"></a>Cstatus-Barcode STRG:: up-Ex

Erstellt ein-Steuerelement (ein untergeordnetes Fenster) und ordnet es dem `CStatusBarCtrl`-Objekt zu.

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
Gibt die erweiterte Art des zu erstellenden Steuer Elements an. Eine Liste erweiterter Windows-Stile finden Sie unter dem *dwExStyle* -Parameter für " [kreatewindowex](/windows/win32/api/winuser/nf-winuser-createwindowexw) " in der Windows SDK.

*dwstyle*<br/>
Gibt den Stil des StatusBar-Steuer Elements an. Wenden Sie eine beliebige Kombination von Status leisten-Steuerelement Formaten an, die in [allgemeinen Steuer](/windows/win32/Controls/common-control-styles) Element Formaten in der Windows SDK Dieser Parameter muss den WS_CHILD Stil enthalten. Sie sollte auch den WS_VISIBLE Stil enthalten.

*Rect*<br/>
Ein Verweis auf eine [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die die Größe und Position des zu erstellenden Fensters in Client Koordinaten von *pparser*beschreibt.

*pparser*<br/>
Ein Zeiger auf das Fenster, das das übergeordnete Element des Steuer Elements ist.

*NID*<br/>
Die ID des untergeordneten Fensters des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Verwenden Sie `CreateEx` anstelle von [Create](#create) , um erweiterte Windows-Stile anzuwenden, die durch den erweiterten Windows-Stil **WS_EX_** angegeben werden.

##  <a name="cstatusbarctrl"></a>Cstatus-Barcode STRG:: cstatus-barstrg

Erstellt ein `CStatusBarCtrl`-Objekt.

```
CStatusBarCtrl();
```

##  <a name="drawitem"></a>Cstatus-STRG::D rawitem

Wird von Framework aufgerufen, wenn sich ein visueller Aspekt eines Besitzers-Status leisten-Steuer Elements ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpdrawitemstruct*<br/>
Ein langer Zeiger auf eine [drawitemstruct](/windows/win32/api/winuser/ns-winuser-drawitemstruct) -Struktur, die Informationen über den erforderlichen Zeichentyp enthält.

### <a name="remarks"></a>Hinweise

Der `itemAction` Member der `DRAWITEMSTRUCT` Struktur definiert die auszuführende Zeichnungs Aktion.

Standardmäßig führt diese Member-Funktion keine Aktion aus. Überschreiben Sie diese Member-Funktion, um das Zeichnen für einen Besitzer `CStatusBarCtrl` Objekt zu implementieren.

Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface), die für den in *lpdrawitemstruct* angegebenen Anzeige Kontext ausgewählt sind, wiederherstellen, bevor diese Element Funktion beendet wird.

##  <a name="getborders"></a>Cstatus-barstrg:: getrahmens

Ruft die aktuelle Breite der horizontalen und vertikalen Rahmen des StatusBar-Steuer Elements und des Leerraums zwischen Rechtecke ab.

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>Parameter

*prahmens*<br/>
Die Adresse eines ganzzahligen Arrays mit drei Elementen. Das erste Element empfängt die Breite des horizontalen Rahmens, das zweite empfängt die Breite des vertikalen Rahmens, und das dritte empfängt die Breite des Rahmens zwischen Rechtecke.

*nhorz*<br/>
Verweis auf eine Ganzzahl, die die Breite des horizontalen Rahmens empfängt.

*vertieren*<br/>
Verweis auf eine Ganzzahl, die die Breite des vertikalen Rahmens empfängt.

*nabstände*<br/>
Verweis auf eine Ganzzahl, die die Breite des Rahmens zwischen Rechtecke empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Rahmen bestimmen den Abstand zwischen dem äußeren Rand des Steuer Elements und den Rechtecke innerhalb des Steuer Elements, die Text enthalten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

##  <a name="geticon"></a>Cstatus-barstrg:: getIcon

Ruft das Symbol für einen Teil (auch als Bereich bezeichnet) im aktuellen StatusBar-Steuerelement ab.

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*ipart*|in Der null basierte Index des Teils, der das abzurufende Symbol enthält. Wenn dieser Parameter-1 ist, wird angenommen, dass es sich bei der Statusleiste um eine Statusleiste im einfachen Modus handelt.|

### <a name="return-value"></a>Rückgabewert

Das Handle für das Symbol, wenn die Methode erfolgreich war. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Diese Methode sendet die [SB_GETICON](/windows/win32/Controls/sb-geticon) Nachricht, die in der Windows SDK beschrieben wird.

Ein StatusBar-Steuerelement besteht aus einer Zeile mit Textausgabe Bereichen, die auch als Teile bezeichnet werden. Weitere Informationen zur Statusleiste finden Sie unter [Status leisten Implementierung in MFC](../../mfc/status-bar-implementation-in-mfc.md) und [Festlegen des Modus für ein CStatusBarCtrl-Objekt](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md).

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird eine Variable definiert, `m_statusBar`, die für den Zugriff auf das aktuelle StatusBar-Steuerelement verwendet wird. Diese Variable wird im nächsten Beispiel verwendet.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird ein Symbol in zwei Bereiche des aktuellen StatusBar-Steuer Elements kopiert. In einem früheren Abschnitt des Code Beispiels haben wir ein StatusBar-Steuerelement mit drei Bereichen erstellt und dann dem ersten Bereich ein Symbol hinzugefügt. In diesem Beispiel wird das Symbol aus dem ersten Bereich abgerufen und dann dem zweiten und dritten Bereich hinzugefügt.

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

##  <a name="getparts"></a>Cstatus-barstrg:: GetParts

Ruft die Anzahl der Teile in einem StatusBar-Steuerelement ab.

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>Parameter

*nparts*<br/>
Anzahl der Teile, für die Koordinaten abgerufen werden sollen. Wenn dieser Parameter größer als die Anzahl der Teile im Steuerelement ist, ruft die Nachricht nur die Koordinaten für vorhandene Teile ab.

*pparts*<br/>
Die Adresse eines ganzzahligen Arrays, das über die gleiche Anzahl von Elementen wie die Anzahl der von *nparts*angegebenen Teile verfügt. Jedes Element im Array empfängt die Client Koordinate des rechten Rands des entsprechenden Teils. Wenn ein Element auf-1 festgelegt ist, wird die Position des rechten Rands für diesen Teil auf den rechten Rand der Statusleiste erweitert.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Teile im-Steuerelement, wenn erfolgreich, andernfalls 0 (null).

### <a name="remarks"></a>Hinweise

Diese Member-Funktion ruft auch die Koordinate des rechten Rands der angegebenen Anzahl von Teilen ab.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

##  <a name="getrect"></a>Cstatus-Barcode STRG:: GetRect

Ruft das umgebende Rechteck eines Teils in einem StatusBar-Steuerelement ab.

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*npane*<br/>
NULL basierter Index des Teils, dessen Begrenzungs Rechteck abgerufen werden soll.

*lprect*<br/>
Adresse einer [Rect](/previous-versions/dd162897\(v=vs.85\)) -Struktur, die das Begrenzungs Rechteck empfängt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

##  <a name="gettext"></a>Cstatus-barstrg:: gettext

Ruft den Text aus dem angegebenen Teil eines StatusBar-Steuer Elements ab.

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
Adresse des Puffers, der den Text empfängt. Dieser Parameter ist eine NULL-terminierte Zeichenfolge.

*npane*<br/>
Der null basierte Index des Teils, von dem Text abgerufen werden soll.

*pType*<br/>
Zeiger auf eine Ganzzahl, die die Typinformationen empfängt. Der Typ kann einen der folgenden Werte aufweisen:

- **0** der Text wird mit einem Rahmen gezeichnet, der unterhalb der Ebene der Statusleiste angezeigt wird.

- SBT_NOBORDERS der Text ohne Rahmen gezeichnet wird.

- SBT_POPOUT der Text mit einem Rahmen gezeichnet wird, der höher als die Ebene der Statusleiste ist.

- SBT_OWNERDRAW wenn der Text über den SBT_OWNERDRAW Zeichentyp verfügt, empfängt *pType* diese Nachricht und gibt den 32-Bit-Wert zurück, der dem Text statt der Länge und dem Vorgangstyp zugeordnet ist.

### <a name="return-value"></a>Rückgabewert

Die Länge (in Zeichen) des Texts oder ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Wert, der den aktuellen Text enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

##  <a name="gettextlength"></a>Cstatus-barstrg:: getTextLength

Ruft die Länge des Texts aus dem angegebenen Teil eines StatusBar-Steuer Elements in Zeichen ab.

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>Parameter

*npane*<br/>
Der null basierte Index des Teils, von dem Text abgerufen werden soll.

*pType*<br/>
Zeiger auf eine Ganzzahl, die die Typinformationen empfängt. Der Typ kann einen der folgenden Werte aufweisen:

- **0** der Text wird mit einem Rahmen gezeichnet, der unterhalb der Ebene der Statusleiste angezeigt wird.

- SBT_NOBORDERS der Text ohne Rahmen gezeichnet wird.

- SBT_OWNERDRAW wird der Text vom übergeordneten Fenster gezeichnet.

- SBT_POPOUT der Text mit einem Rahmen gezeichnet wird, der höher als die Ebene der Statusleiste ist.

### <a name="return-value"></a>Rückgabewert

Die Länge des Texts in Zeichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

##  <a name="gettiptext"></a>Cstatus-barstrg:: GetTipText

Ruft den QuickInfo-Text für einen Bereich in einer Statusleiste ab.

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>Parameter

*npane*<br/>
Der null basierte Index des Status leisten Bereichs, um den QuickInfo-Text zu empfangen.

### <a name="return-value"></a>Rückgabewert

Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt, das den Text enthält, der in der QuickInfo verwendet werden soll.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

##  <a name="issimple"></a>CStatusBarCtrl:: IsSimple

Überprüft ein Statusfenster-Steuerelement, um zu bestimmen, ob es sich im einfachen Modus befindet.

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn sich das Statusfenster-Steuerelement im einfachen Modus befindet andernfalls NULL.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple), wie in der Windows SDK beschrieben.

##  <a name="setbkcolor"></a>Cstatu\barctrl:: SetBkColor

Legt die Hintergrundfarbe in einer Statusleiste fest.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parameter

*programmiert*<br/>
COLORREF-Wert, der die neue Hintergrundfarbe angibt. Geben Sie den CLR_DEFAULT Wert an, der bewirkt, dass die Statusleiste die Standard Hintergrundfarbe verwendet.

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der die vorherige Standard Hintergrundfarbe darstellt.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

##  <a name="seticon"></a>Cstatus-barctrl:: abticon

Legt das Symbol für einen Bereich in einer Statusleiste fest.

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>Parameter

*npane*<br/>
Der null basierte Index des Bereichs, der das Symbol empfängt. Wenn dieser Parameter-1 ist, wird angenommen, dass es sich bei der Statusleiste um eine einfache Statusleiste handelt.

*hIcon*<br/>
Handle für das Symbol, das festgelegt werden soll. Wenn dieser Wert NULL ist, wird das Symbol aus dem Teil entfernt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [SB_SETICON](/windows/win32/Controls/sb-seticon), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [cstatuus barctrl:: SetBkColor](#setbkcolor).

##  <a name="setminheight"></a>Cstatuin barctrl:: setMinHeight

Legt die Mindesthöhe des Zeichnungs Bereichs eines Status leisten Steuer Elements fest.

```
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>Parameter

*nmin.*<br/>
Die minimale Höhe des Steuer Elements in Pixel.

### <a name="remarks"></a>Hinweise

Die Mindesthöhe ist die Summe aus *nmin* und der doppelten Breite des vertikalen Rahmens des StatusBar-Steuer Elements in Pixel.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

##  <a name="setparts"></a>Cstatus-barctrl:: SetParts

Legt die Anzahl der Teile in einem StatusBar-Steuerelement und die Koordinate des rechten Rands der einzelnen Teile fest.

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>Parameter

*nparts*<br/>
Anzahl der festzulegenden Teile. Die Anzahl der Teile darf nicht größer als 255 sein.

*pbreiten*<br/>
Die Adresse eines ganzzahligen Arrays, das über die gleiche Anzahl von Elementen wie von *nparts*angegebene Teile verfügt. Jedes Element im Array gibt die Position (in Client Koordinaten) des rechten Rands des entsprechenden Teils an. Wenn ein Element-1 ist, wird die Position des rechten Rands für diesen Teil auf den rechten Rand des Steuer Elements ausgedehnt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

##  <a name="setsimple"></a>Cstatus-barctrl:: SetSimple

Gibt an, ob ein Status leisten-Steuerelement einfachen Text anzeigt oder alle Steuerelement Teile anzeigt, die durch einen vorherigen Aufrufen von [SetParts](#setparts)festgelegt wurden.

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>Parameter

*bsimple*<br/>
in Flag zum Anzeigen des Typs. Wenn dieser Parameter true ist, zeigt das Steuerelement einfachen Text an. Wenn der Wert false ist, werden mehrere Teile angezeigt.

### <a name="return-value"></a>Rückgabewert

Gibt immer 0 zurück.

### <a name="remarks"></a>Hinweise

Wenn die Anwendung das StatusBar-Steuerelement von "nicht einfach" in "einfach" oder umgekehrt ändert, zeichnet das System sofort das Steuerelement neu.

##  <a name="settext"></a>Cstatus-barctrl:: SetText

Legt den Text im bestimmten Teil eines Statusleisten-Steuerelements fest.

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Adresse einer mit NULL endenden Zeichenfolge, die den festzulegenden Text angibt. Wenn *nType* SBT_OWNERDRAW ist, stellt *lpszText* 32 Bits von Daten dar.

*npane*<br/>
Der nullbasierte Index des festzulegenden Teils. Wenn dieser Wert 255 ist, wird angenommen, dass das Statusleisten-Steuerelement ein einfaches Steuerelement mit nur einem Teil ist.

*nType*<br/>
Der Typ des Zeichenvorgangs. Eine Liste möglicher Werte finden Sie unter [SB_SETTEXT Meldung](/windows/win32/Controls/sb-settext) .

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Die Meldung erklärt den Teil des Steuer Elements für ungültig, der geändert wurde, sodass der neue Text angezeigt wird, wenn das Steuerelement das nächste Mal die WM_PAINT Nachricht empfängt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

##  <a name="settiptext"></a>Cstatulaufbarctrl:: Setup Text

Legt den QuickInfo-Text für einen Bereich in einer Statusleiste fest.

```
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parameter

*npane*<br/>
Der null basierte Index des Status leisten Bereichs, um den QuickInfo-Text zu empfangen.

*psztiptext*<br/>
Ein Zeiger auf eine Zeichenfolge, die den QuickInfo-Text enthält.

### <a name="remarks"></a>Hinweise

Diese Member-Funktion implementiert das Verhalten der Win32-Nachricht [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext), wie in der Windows SDK beschrieben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl-Klasse](../../mfc/reference/ctoolbarctrl-class.md)
