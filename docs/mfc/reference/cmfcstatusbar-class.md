---
title: Cmfcstatusbar-Klasse
ms.date: 11/19/2018
f1_keywords:
- CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar
- AFXSTATUSBAR/CMFCStatusBar::CalcFixedLayout
- AFXSTATUSBAR/CMFCStatusBar::CommandToIndex
- AFXSTATUSBAR/CMFCStatusBar::Create
- AFXSTATUSBAR/CMFCStatusBar::CreateEx
- AFXSTATUSBAR/CMFCStatusBar::DoesAllowDynInsertBefore
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneDoubleClick
- AFXSTATUSBAR/CMFCStatusBar::EnablePaneProgressBar
- AFXSTATUSBAR/CMFCStatusBar::GetCount
- AFXSTATUSBAR/CMFCStatusBar::GetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::GetItemID
- AFXSTATUSBAR/CMFCStatusBar::GetItemRect
- AFXSTATUSBAR/CMFCStatusBar::GetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::GetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::GetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::GetPaneText
- AFXSTATUSBAR/CMFCStatusBar::GetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::GetTipText
- AFXSTATUSBAR/CMFCStatusBar::InvalidatePaneContent
- AFXSTATUSBAR/CMFCStatusBar::PreCreateWindow
- AFXSTATUSBAR/CMFCStatusBar::SetDrawExtendedArea
- AFXSTATUSBAR/CMFCStatusBar::SetIndicators
- AFXSTATUSBAR/CMFCStatusBar::SetPaneAnimation
- AFXSTATUSBAR/CMFCStatusBar::SetPaneBackgroundColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneIcon
- AFXSTATUSBAR/CMFCStatusBar::SetPaneInfo
- AFXSTATUSBAR/CMFCStatusBar::SetPaneProgress
- AFXSTATUSBAR/CMFCStatusBar::SetPaneStyle
- AFXSTATUSBAR/CMFCStatusBar::SetPaneText
- AFXSTATUSBAR/CMFCStatusBar::SetPaneTextColor
- AFXSTATUSBAR/CMFCStatusBar::SetPaneWidth
- AFXSTATUSBAR/CMFCStatusBar::SetTipText
- AFXSTATUSBAR/CMFCStatusBar::OnDrawPane
helpviewer_keywords:
- CMFCStatusBar [MFC], CalcFixedLayout
- CMFCStatusBar [MFC], CommandToIndex
- CMFCStatusBar [MFC], Create
- CMFCStatusBar [MFC], CreateEx
- CMFCStatusBar [MFC], DoesAllowDynInsertBefore
- CMFCStatusBar [MFC], EnablePaneDoubleClick
- CMFCStatusBar [MFC], EnablePaneProgressBar
- CMFCStatusBar [MFC], GetCount
- CMFCStatusBar [MFC], GetDrawExtendedArea
- CMFCStatusBar [MFC], GetExtendedArea
- CMFCStatusBar [MFC], GetItemID
- CMFCStatusBar [MFC], GetItemRect
- CMFCStatusBar [MFC], GetPaneInfo
- CMFCStatusBar [MFC], GetPaneProgress
- CMFCStatusBar [MFC], GetPaneStyle
- CMFCStatusBar [MFC], GetPaneText
- CMFCStatusBar [MFC], GetPaneWidth
- CMFCStatusBar [MFC], GetTipText
- CMFCStatusBar [MFC], InvalidatePaneContent
- CMFCStatusBar [MFC], PreCreateWindow
- CMFCStatusBar [MFC], SetDrawExtendedArea
- CMFCStatusBar [MFC], SetIndicators
- CMFCStatusBar [MFC], SetPaneAnimation
- CMFCStatusBar [MFC], SetPaneBackgroundColor
- CMFCStatusBar [MFC], SetPaneIcon
- CMFCStatusBar [MFC], SetPaneInfo
- CMFCStatusBar [MFC], SetPaneProgress
- CMFCStatusBar [MFC], SetPaneStyle
- CMFCStatusBar [MFC], SetPaneText
- CMFCStatusBar [MFC], SetPaneTextColor
- CMFCStatusBar [MFC], SetPaneWidth
- CMFCStatusBar [MFC], SetTipText
- CMFCStatusBar [MFC], OnDrawPane
ms.assetid: f2960d1d-f4ed-41e8-bd99-0382b2f8d88e
ms.openlocfilehash: 004873ef2696eb9504cdd4df77e700c4a145e886
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686573"
---
# <a name="cmfcstatusbar-class"></a>Cmfcstatusbar-Klasse

Die- `CMFCStatusBar` Klasse implementiert eine Statusleiste, die der- `CStatusBar` Klasse ähnelt. Die `CMFCStatusBar` -Klasse verfügt jedoch über Funktionen, die von der `CStatusBar` -Klasse nicht bereitgestellt werden. Beispielsweise kann die Klasse Bilder, Animationen und Statusanzeigen anzeigen und auf einen Mausdoppelklick reagieren.

Weitere Informationen finden Sie im Quellcode, der sich im Ordner **VC \\ atlmfc \\ src \\ MFC** Ihrer Visual Studio-Installation befindet.

## <a name="syntax"></a>Syntax

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cmfcstatusbar:: calcfixedlayout](#calcfixedlayout)|(Überschreibt [cbasepane:: calcfixedlayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[Cmfcstatusbar:: commandto Index](#commandtoindex)||
|[Cmfcstatusbar:: Create](#create)|Erstellt eine Steuerleiste und fügt Sie an das [CPANE](../../mfc/reference/cpane-class.md) -Objekt an. (Überschreibt [CPANE:: Create](../../mfc/reference/cpane-class.md#create).)|
|[Cmfcstatusbar:: kreateex](#createex)|Erstellt eine Steuerleiste und fügt Sie an das [CPANE](../../mfc/reference/cpane-class.md) -Objekt an. (Überschreibt [CPANE:: kreateex](../../mfc/reference/cpane-class.md#createex).)|
|[Cmfcstatusbar::D oesallowdyninsertbefore](#doesallowdyninsertbefore)|Bestimmt, ob ein anderer Bereich dynamisch zwischen diesem Bereich und dem übergeordneten Frame eingefügt werden kann. (Überschreibt [cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[Cmfcstatusbar:: enablepanedoubleclick](#enablepanedoubleclick)|Aktiviert oder deaktiviert die Handhabung von Maus Doppelklicks auf der Statusleiste.|
|[Cmfcstatusbar:: enablepaneprogressbar](#enablepaneprogressbar)|Zeigt eine Statusanzeige im angegebenen Bereich an.|
|[Cmfcstatusbar:: GetCount](#getcount)|Gibt die Anzahl der Bereiche auf der Statusleiste zurück.|
|[Cmfcstatusbar:: getdrawextendedarea](#getdrawextendedarea)||
|[Cmfcstatusbar:: getextendedarea](#getextendedarea)||
|[Cmfcstatusbar:: getItemID](#getitemid)||
|[Cmfcstatusbar:: GetItemRect](#getitemrect)||
|[Cmfcstatusbar:: getpaneinfo](#getpaneinfo)||
|[Cmfcstatusbar:: getpaneprogress](#getpaneprogress)||
|[Cmfcstatusbar:: getpanestyle](#getpanestyle)|Gibt den Bereich des Bereichs zurück. (Überschreibt [cbasepane:: getpanestyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[Cmfcstatusbar:: getpanetext](#getpanetext)||
|[Cmfcstatusbar:: getpanewidth](#getpanewidth)|Gibt die Breite des angegebenen Bereichs der Statusleiste in Pixel zurück.|
|[Cmfcstatusbar:: GetTipText](#gettiptext)|Gibt den QuickInfo-Text für den angegebenen Bereich der Statusleiste zurück.|
|[Cmfcstatusbar:: invalidatepanecontent](#invalidatepanecontent)|Erklärt den angegebenen Bereich für ungültig und zeichnet seinen Inhalt neu.|
|[Cmfcstatusbar::P neu erstellten atewindow](#precreatewindow)|Wird von Framework vor der Erstellung des Windows-Fensters, das an dieses Objekt angefügt ist, aufgerufen `CWnd` . (Überschreibt [CWnd::P neu erstellte atewindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[Cmfcstatusbar:: setdrawextendedarea](#setdrawextendedarea)||
|[Cmfcstatusbar:: setindicator](#setindicators)||
|[Cmfcstatusbar:: setpaneanimation](#setpaneanimation)|Weist eine Animation dem angegebenen Bereich zu.|
|[Cmfcstatusbar:: setpanebackgroundcolor](#setpanebackgroundcolor)|Legt die Hintergrundfarbe für den angegebenen Bereich der Statusleiste fest.|
|[Cmfcstatusbar:: setpaneicon](#setpaneicon)|Legt das Indikator Symbol für den angegebenen Bereich der Statusleiste fest.|
|[Cmfcstatusbar:: setpaneinfo](#setpaneinfo)||
|[Cmfcstatusbar:: setpaneprogress](#setpaneprogress)|Legt den aktuellen Status der Statusleiste für den angegebenen Bereich der Statusleiste fest.|
|[Cmfcstatusbar:: setpanestyle](#setpanestyle)|Legt den Stil des Bereichs fest. (Überschreibt [cbasepane:: setpanestyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[Cmfcstatusbar:: SetPaneText](#setpanetext)||
|[Cmfcstatusbar:: setpanetextcolor](#setpanetextcolor)|Legt die Textfarbe für den angegebenen Bereich der Statusleiste fest.|
|[Cmfcstatusbar:: setpanewidth](#setpanewidth)|Legt die Breite des angegebenen Bereichs der Statusleiste in Pixel fest.|
|[Cmfcstatusbar:: Setup Text](#settiptext)|Legt den QuickInfo-Text für den angegebenen Bereich der Statusleiste fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|name|Beschreibung|
|----------|-----------------|
|[Cmfcstatusbar:: ondrawpane](#ondrawpane)|Wird von Framework aufgerufen, wenn es den Bereich der Statusleiste neu zeichnet.|

## <a name="remarks"></a>Bemerkungen

Das folgende Diagramm zeigt eine Abbildung der Statusleiste aus der Beispielanwendung für die [Statusleiste-Demo](../../overview/visual-cpp-samples.md) .

![Beispiel für CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Beispiel für CMFCStatusBar")

## <a name="examples"></a>Beispiele

Im folgenden Beispiel werden die lokalen Variablen veranschaulicht, die von der Anwendung verwendet werden, um verschiedene Methoden in der-Klasse aufzurufen `CMFCStatusBar` . Diese Variablen werden in "Status Name. h" deklariert. Der Hauptframe wird in "mainfrm. h" deklariert, das Dokument wird in "Status-bardemodoc. h" deklariert, und die Sicht wird in "Status Name. h" deklariert. Dieser Code Ausschnitt ist Teil des Status leisten- [Demo](../../overview/visual-cpp-samples.md)Beispiels.

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

Im folgenden Beispiel wird veranschaulicht, wie Sie einen Verweis auf `CMFCStatusBar` das-Objekt abrufen, indem Sie die `GetStatusBar` -Methode in "mainfrm. h" einführen und dann diese Methode von der- `GetStatusBar` Methode in "Status Name. h" aufrufen. Dieser Code Ausschnitt ist Teil des Status leisten- [Demo](../../overview/visual-cpp-samples.md)Beispiels.

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

Im folgenden Beispiel wird veranschaulicht, wie verschiedene Methoden in der- `CMFCStatusBar` Klasse in "Status Name. cpp" aufgerufen werden. Die Konstanten werden in "mainfrm. h" deklariert. Das Beispiel zeigt, wie Sie das Symbol festlegen, den QuickInfo-Text des Status leisten Bereichs festlegen, eine Statusanzeige im angegebenen Bereich anzeigen, eine Animation zum angegebenen Bereich zuweisen, den Text und die Breite des Bereichs der Statusleiste festlegen und die aktuelle Statusanzeige der Statusleiste für den Bereich Statusleiste festlegen. Dieser Code Ausschnitt ist Teil des Status leisten- [Demo](../../overview/visual-cpp-samples.md)Beispiels.

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxstatusbar. h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a> Cmfcstatusbar:: calcfixedlayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

in *bstretch*<br/>
in *bhorz*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a> Cmfcstatusbar:: commandto Index

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parameter

in *nidfind*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarcreate"></a><a name="create"></a> Cmfcstatusbar:: Create

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

in *pparser*<br/>
in *dwstyle*<br/>
in *NID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a> Cmfcstatusbar:: kreateex

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

in *pparser*<br/>
in *dwctrlstyle*<br/>
in *dwstyle*<br/>
in *NID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a> Cmfcstatusbar::D oesallowdyninsertbefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a> Cmfcstatusbar:: enablepanedoubleclick

Aktiviert oder deaktiviert die Handhabung von Maus Doppelklicks auf der Statusleiste.

```cpp
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*benabel*<br/>
in Wenn true, aktivieren Sie die Verarbeitung des Mauszeigers. Andernfalls deaktivieren Sie die Verarbeitung des Mauszeigers.

### <a name="remarks"></a>Bemerkungen

Wenn die Statusleiste für die Verarbeitung von doppelten Klicks aktiviert ist, sendet Windows die WM_COMMAND Benachrichtigung in Verbindung mit einer Ressourcen-ID an den Besitzer der Statusleiste, wenn der Benutzer auf den Bereich Statusleiste doppelklickt.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a> Cmfcstatusbar:: enablepaneprogressbar

Zeigt eine Statusanzeige im angegebenen Bereich an.

```cpp
void EnablePaneProgressBar(
    int nIndex,
    long nTotal=100,
    BOOL bDisplayText=FALSE,
    COLORREF clrBar=-1,
    COLORREF clrBarDest=-1,
    COLORREF clrProgressText=-1);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, dessen Statusanzeige aktiviert werden soll.

*nsumme*<br/>
in Gibt den maximalen Wert für die Statusanzeige an.

*bdisplaytext*<br/>
in Gibt an, ob die Statusanzeige den aktuellen Fortschritts Wert anzeigen soll.

*clrbar*<br/>
in Gibt die Hintergrundfarbe der Statusanzeige an.

*clrbardest*<br/>
in Gibt die sekundäre Farbe des Fortschrittsanzeige Hintergrunds an. Verwenden Sie einen anderen Wert als *clrbar* , um eine Farbe auszufüllen, die in einen Farbverlauf gemischt ist.

*clrProgressText*<br/>
in Gibt die Textfarbe der Statusanzeige an.

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Statusanzeige Vorgang deaktivieren möchten `EnablePaneProgressBar` , wobei *ntotal* auf-1 festgelegt ist. Standardmäßig ist *ntotal* auf 100 festgelegt. Daher benötigen Sie keine weiteren Berechnungen, um den Status als Prozentwert anzuzeigen.

Sie sollten verschiedene Werte für *clrbar* und *clrbardest* übergeben, damit die Hintergrundfarbe der Statusanzeige eine in einen Farbverlauf umgemischte Farbe anzeigt. .

Um den aktuellen Status festzulegen, müssen Sie die [cmfcstatusbar:: setpaneprogress](#setpaneprogress) -Methode aufrufen.

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a> Cmfcstatusbar:: GetCount

Ruft die Anzahl der Bereiche in der Statusleiste ab.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bereiche in der Statusleiste.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a> Cmfcstatusbar:: getdrawextendedarea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a> Cmfcstatusbar:: getextendedarea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

in *Rect*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a> Cmfcstatusbar:: getItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a> Cmfcstatusbar:: GetItemRect

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>
in *lprect*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a> Cmfcstatusbar:: getpaneinfo

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>
in *NID*<br/>
in *nstyle*<br/>
in *cxwidth*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a> Cmfcstatusbar:: getpaneprogress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a> Cmfcstatusbar:: getpanestyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a> Cmfcstatusbar:: getpanetext

```cpp
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>
in *s*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a> Cmfcstatusbar:: getpanewidth

Ruft die Breite des Bereichs einer Statusleiste ab.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs der Statusleiste an.

### <a name="return-value"></a>Rückgabewert

Die Breite des Status leisten Bereichs, der von *nIndex* angegeben wird. andernfalls 0 (null), wenn kein Status Leistenbereich vorhanden ist.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a> Cmfcstatusbar:: GetTipText

Ruft den QuickInfo-Text für den Bereich einer Statusleiste ab.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, für den QuickInfo-Text abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Der QuickInfo-Text des Status leisten Bereichs, der von *nIndex* angegeben wird. Andernfalls die leere Zeichenfolge, wenn für den angegebenen *nIndex* kein Status Leistenbereich vorhanden ist oder wenn der QuickInfo-Text leer ist.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a> Cmfcstatusbar:: invalidatepanecontent

Der Status Leistenbereich für ungültig erklärt und der Inhalt neu gezeichnet wird.

```cpp
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, dessen Inhalt für ungültig erklärt und neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn die Statusleiste ungültig ist, wird Sie für das erneute zeichnen markiert. Windows zeichnet es neu, wenn die- `UpdateWindow` Methode eine WM_PAINT Meldung an die- `OnPaint` Methode sendet.

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a> Cmfcstatusbar:: ondrawpane

Zeichnen Sie den Bereich der Statusleiste neu.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parameter

*PDC*<br/>
in Ein Zeiger auf einen Gerätekontext zum Zeichnen.

*ppane*<br/>
in Ein Zeiger auf eine- `CMFCStatusBarPaneInfo` Struktur, die die Informationen über den Bereich enthält, der neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Standardmäßig `OnDrawPane` zeichnet den Bereich mithilfe des Geräte Kontexts *PDC* nach dem Stil und Inhalt des Bereichs.

Überschreiben Sie diese Methode in einer `CMFCStatusBar` von abgeleiteten Klasse, um die Darstellung eines Bereichs anzupassen.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a> Cmfcstatusbar::P neu erstellten atewindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parameter

in *CS*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a> Cmfcstatusbar:: setdrawextendedarea

```cpp
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parameter

in *BSET*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a> Cmfcstatusbar:: setindicator

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parameter

in *lpidarray*<br/>
in *transicount*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a> Cmfcstatusbar:: setpaneanimation

Weist eine Animation dem angegebenen Bereich zu.

```cpp
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, dem Sie eine Animation zuweisen möchten.

*hImageList*<br/>
in Gibt ein Handle für die Bildliste an, die die Animations Frames enthält.

*nframerate*<br/>
in Gibt die Framerate in Millisekunden für die Animation an.

*bUpdate*<br/>
in Wenn true, aktualisieren Sie den Bereichs Inhalt sofort. Andernfalls wird der Bereichs Inhalt aktualisiert, wenn er für ungültig erklärt wird.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die aktuelle Animation deaktivieren möchten, wird aufgerufen, `SetPaneAnimation` wobei `hImageList` auf NULL festgelegt ist.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a> Cmfcstatusbar:: setpanebackgroundcolor

Legt die Hintergrundfarbe des Status leisten Bereichs fest.

```cpp
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, für den eine neue Hintergrundfarbe festgelegt werden soll.

*clrBackground*<br/>
in Gibt die neue Hintergrundfarbe an.

*bUpdate*<br/>
in Wenn true, aktualisieren Sie den Bereichs Inhalt sofort. Aktualisieren Sie den Bereichs Inhalt andernfalls erst, wenn der Bereich durch eine andere Methode ungültig gemacht wird.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a> Cmfcstatusbar:: setpaneicon

Legen Sie das Symbol für den Bereich Statusleiste fest.

```cpp
void SetPaneIcon(
    int nIndex,
    HICON hIcon,
    BOOL bUpdate=TRUE);

void SetPaneIcon(
    int nIndex,
    HBITMAP hBmp,
    COLORREF clrTransparent=RGB(255, 0, 255),
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, für den das Bild festgelegt werden soll.

*hIcon*<br/>
in Gibt ein Handle für das Symbol an, das als Bereichs Bild festgelegt werden soll.

*bUpdate*<br/>
in Gibt an, ob der Bereichs Inhalt sofort aktualisiert werden soll.

*hbmp*<br/>
in Gibt ein Handle für die Bitmap an, das als Bereichs Bild festgelegt werden soll.

*clrtransparent*<br/>
in Gibt die transparente Farbe der Bitmap an, die das *hbmp* anzeigt.

### <a name="remarks"></a>Bemerkungen

Sie können entweder HICON oder HBITMAP mit der transparenten Farbe übergeben, um das Bild des Bereichs festzulegen. Wenn Sie das Bild nicht mehr anzeigen möchten, übergeben Sie den NULL-Wert als Bild handle.

Wenn eine laufende Animation vorhanden ist, die [cmfcstatusbar:: setpaneanimation](#setpaneanimation) festgelegt hat, wird die Animation angehalten.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a> Cmfcstatusbar:: setpaneinfo

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>
in *NID*<br/>
in *nstyle*<br/>
in *cxwidth*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a> Cmfcstatusbar:: setpaneprogress

Legen Sie den aktuellen Status Indikator der Statusanzeige für den angegebenen Bereich fest.

```cpp
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, für den die Statusanzeige aktualisiert werden soll.

*ncurrr*<br/>
in Gibt den aktuellen Wert der Statusanzeige an.

*bUpdate*<br/>
in Gibt an, ob der Bereich sofort aktualisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Ruft diese Methode auf, wenn Sie die Statusanzeige für die Statusanzeige im angegebenen Bereich aktualisieren möchten.

Um diese Funktion für den angegebenen Bereich zu verwenden, müssen Sie zuerst [cmfcstatusbar:: enablepaneprogressbar](#enablepaneprogressbar) aufrufen.

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a> Cmfcstatusbar:: setpanestyle

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>
in *nstyle*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a> Cmfcstatusbar:: SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parameter

in *nIndex*<br/>
in *lpsznewtext*<br/>
in *bUpdate*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a> Cmfcstatusbar:: setpanetextcolor

Legt die Textfarbe des angegebenen Bereichs fest.

```cpp
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Gibt den Index des Bereichs an, dem Sie eine neue Textfarbe zuweisen möchten.

*clrText*<br/>
in Gibt die Textfarbe an.

*bUpdate*<br/>
in Wenn true, aktualisieren Sie den Bereichs Inhalt sofort. Aktualisieren Sie den Bereichs Inhalt andernfalls erst, wenn der Bereich durch eine andere Methode ungültig gemacht wird.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a> Cmfcstatusbar:: setpanewidth

Legen Sie die Breite des Bereichs der Statusleiste fest.

```cpp
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Der Index des Status leisten Bereichs, für den eine neue Breite festgelegt werden soll.

*verschoben*<br/>
in Die neue Breite des Status leisten Bereichs in Pixel.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a> Cmfcstatusbar:: Setup Text

Legen Sie den QuickInfo-Text eines Status leisten Bereichs fest.

```cpp
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
in Der Index des Bereichs, dem der QuickInfo-Text zugewiesen werden soll.

*psztiptext*<br/>
in Der neue QuickInfo-Text.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CPANE-Klasse](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar-Klasse](../../mfc/reference/cstatusbar-class.md)
