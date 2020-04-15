---
title: CMFCStatusBar-Klasse
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
ms.openlocfilehash: 8f262d0139b6dffe54e16748ffda4938ba43fc08
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366057"
---
# <a name="cmfcstatusbar-class"></a>CMFCStatusBar-Klasse

Die `CMFCStatusBar` Klasse implementiert eine Statusleiste `CStatusBar` ähnlich der Klasse. Die `CMFCStatusBar` -Klasse verfügt jedoch über Funktionen, die von der `CStatusBar` -Klasse nicht bereitgestellt werden. Beispielsweise kann die Klasse Bilder, Animationen und Statusanzeigen anzeigen und auf einen Mausdoppelklick reagieren.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCStatusBar : public CPane
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCStatusBar::CalcFixedLayout](#calcfixedlayout)|(Überschreibt [CBasePane::CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout).)|
|[CMFCStatusBar::CommandToIndex](#commandtoindex)||
|[CMFCStatusBar::Erstellen](#create)|Erstellt eine Steuerleiste und fügt sie an das [CPane-Objekt](../../mfc/reference/cpane-class.md) an. (Überschreibt [CPane::Create](../../mfc/reference/cpane-class.md#create).)|
|[CMFCStatusBar::CreateEx](#createex)|Erstellt eine Steuerleiste und fügt sie an das [CPane-Objekt](../../mfc/reference/cpane-class.md) an. (Überschreibt [CPane::CreateEx](../../mfc/reference/cpane-class.md#createex).)|
|[CMFCStatusBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|Legt fest, ob ein anderer Bereich dynamisch zwischen diesem Bereich und dem übergeordneten Rahmen eingefügt werden kann. (Überschreibt [CBasePane::DoesAllowDynInsertBefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore).)|
|[CMFCStatusBar::EnablePaneDoubleClick](#enablepanedoubleclick)|Aktiviert oder deaktiviert die Behandlung von Mausdoppelklicks auf der Statusleiste.|
|[CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar)|Zeigt eine Statusleiste im angegebenen Bereich an.|
|[CMFCStatusBar::GetCount](#getcount)|Gibt die Anzahl der Bereiche in der Statusleiste zurück.|
|[CMFCStatusBar::GetDrawExtendedArea](#getdrawextendedarea)||
|[CMFCStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCStatusBar::GetItemID](#getitemid)||
|[CMFCStatusBar::GetItemRect](#getitemrect)||
|[CMFCStatusBar::GetPaneInfo](#getpaneinfo)||
|[CMFCStatusBar::GetPaneProgress](#getpaneprogress)||
|[CMFCStatusBar::GetPaneStyle](#getpanestyle)|Gibt den Bereichsstil zurück. (Überschreibt [CBasePane::GetPaneStyle](../../mfc/reference/cbasepane-class.md#getpanestyle).)|
|[CMFCStatusBar::GetPaneText](#getpanetext)||
|[CMFCStatusBar::GetPaneWidth](#getpanewidth)|Gibt die Breite des angegebenen Bereichs der Statusleiste in Pixel zurück.|
|[CMFCStatusBar::GetTipText](#gettiptext)|Gibt den QuickInfo-Text für den angegebenen Bereich der Statusleiste zurück.|
|[CMFCStatusBar::InvalidatePaneContent](#invalidatepanecontent)|Macht den angegebenen Bereich ungültig und zeichnet den Inhalt neu.|
|[CMFCStatusBar::PreCreateWindow](#precreatewindow)|Wird vom Framework vor der Erstellung des `CWnd` Windows-Fensters aufgerufen, das an dieses Objekt angefügt ist. (Überschreibt [CWnd::PreCreateWindow](../../mfc/reference/cwnd-class.md#precreatewindow).)|
|[CMFCStatusBar::SetDrawExtendedArea](#setdrawextendedarea)||
|[CMFCStatusBar::SetIndikatoren](#setindicators)||
|[CMFCStatusBar::SetPaneAnimation](#setpaneanimation)|Weist dem angegebenen Bereich eine Animation zu.|
|[CMFCStatusBar::SetPaneBackgroundColor](#setpanebackgroundcolor)|Legt die Hintergrundfarbe für den angegebenen Bereich der Statusleiste fest.|
|[CMFCStatusBar::SetPaneIcon](#setpaneicon)|Legt das Indikatorsymbol für den angegebenen Bereich der Statusleiste fest.|
|[CMFCStatusBar::SetPaneInfo](#setpaneinfo)||
|[CMFCStatusBar::SetPaneProgress](#setpaneprogress)|Legt den aktuellen Fortschritt der Statusleiste für den angegebenen Bereich der Statusleiste fest.|
|[CMFCStatusBar::SetPaneStyle](#setpanestyle)|Legt den Stil des Bereichs fest. (Überschreibt [CBasePane::SetPaneStyle](../../mfc/reference/cbasepane-class.md#setpanestyle).)|
|[CMFCStatusBar::SetPaneText](#setpanetext)||
|[CMFCStatusBar::SetPaneTextColor](#setpanetextcolor)|Legt die Textfarbe für den angegebenen Bereich der Statusleiste fest.|
|[CMFCStatusBar::SetPaneWidth](#setpanewidth)|Legt die Breite in Pixeln des angegebenen Bereichs der Statusleiste fest.|
|[CMFCStatusBar::SetTipText](#settiptext)|Legt den QuickInfo-Text für den angegebenen Bereich der Statusleiste fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCStatusBar::OnDrawPane](#ondrawpane)|Wird vom Framework aufgerufen, wenn es den Bereich der Statusleiste neu zeichnet.|

## <a name="remarks"></a>Bemerkungen

Das folgende Diagramm zeigt eine Abbildung der Statusleiste aus der [Beispielanwendung Statusleiste Demo.](../../overview/visual-cpp-samples.md)

![Beispiel für CMFCStatusBar](../../mfc/reference/media/cmfcstatusbar.png "Beispiel für CMFCStatusBar")

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die lokalen Variablen veranschaulicht, `CMFCStatusBar` die die Anwendung verwendet, um verschiedene Methoden in der Klasse aufzurufen. Diese Variablen werden in StatusBarDemoView.h deklariert. Der Hauptframe wird in MainFrm.h deklariert, das Dokument in StatusBarDemoDoc.h und die Ansicht in StatusBarDemoView.h deklariert. Dieser Codeausschnitt ist Teil des [Beispiels](../../overview/visual-cpp-samples.md)status bar Demo .

[!code-cpp[NVC_MFC_StatusBarDemo#9](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_1.h)]

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCStatusBar` wie Sie `GetStatusBar` einen Verweis auf ein Objekt abrufen, indem `GetStatusBar` Sie die Methode in MainFrm.h einführen und diese Methode dann von der Methode in StatusBarDemoView.h aufrufen. Dieser Codeausschnitt ist Teil des [Beispiels](../../overview/visual-cpp-samples.md)status bar Demo .

[!code-cpp[NVC_MFC_StatusBarDemo#7](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_2.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#8](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_3.h)]

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCStatusBar` wie verschiedene Methoden in der Klasse in StatusBarDemoView.cpp aufzurufen sind. Die Konstanten werden in MainFrm.h deklariert. Das Beispiel zeigt, wie Sie das Symbol festlegen, den QuickInfo-Text des Statusleistenbereichs festlegen, eine Statusleiste im angegebenen Bereich anzeigen, dem angegebenen Bereich eine Animation zuweisen, den Text und die Breite des Statusleistenbereichs festlegen und den aktuellen Fortschrittsindikator der Statusleiste für den Statusleistenbereich festlegen. Dieser Codeausschnitt ist Teil des [Beispiels](../../overview/visual-cpp-samples.md)status bar Demo .

[!code-cpp[NVC_MFC_StatusBarDemo#6](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_4.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#1](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_5.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#2](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_6.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#3](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_7.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#4](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_8.cpp)]
[!code-cpp[NVC_MFC_StatusBarDemo#5](../../mfc/reference/codesnippet/cpp/cmfcstatusbar-class_9.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCStatusBar](../../mfc/reference/cmfcstatusbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxstatusbar.h

## <a name="cmfcstatusbarcalcfixedlayout"></a><a name="calcfixedlayout"></a>CMFCStatusBar::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>Parameter

[in] *bStretch*<br/>
[in] *bHorz*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CMFCStatusBar::CommandToIndex

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parameter

[in] *nIDFind*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarcreate"></a><a name="create"></a>CMFCStatusBar::Erstellen

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

[in] *pParentWnd*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarcreateex"></a><a name="createex"></a>CMFCStatusBar::CreateEx

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

[in] *pParentWnd*<br/>
[in] *dwCtrlStyle*<br/>
[in] *dwStyle*<br/>
[in] *nID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbardoesallowdyninsertbefore"></a><a name="doesallowdyninsertbefore"></a>CMFCStatusBar::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarenablepanedoubleclick"></a><a name="enablepanedoubleclick"></a>CMFCStatusBar::EnablePaneDoubleClick

Aktiviert oder deaktiviert die Behandlung von Mausdoppelklicks auf der Statusleiste.

```
void EnablePaneDoubleClick(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
[in] Wenn TRUE, aktivieren Sie die Verarbeitung des Mausdoppelklicks. Andernfalls deaktivieren Sie die Verarbeitung des Mausdoppelklicks.

### <a name="remarks"></a>Bemerkungen

Wenn die Statusleiste für die Verarbeitung von Doppelklicks aktiviert ist, sendet Windows die WM_COMMAND Benachrichtigung zusammen mit einer Ressourcen-ID an den Besitzer der Statusleiste, wenn der Benutzer auf den Statusleistenbereich doppelklickt.

## <a name="cmfcstatusbarenablepaneprogressbar"></a><a name="enablepaneprogressbar"></a>CMFCStatusBar::EnablePaneProgressBar

Zeigen Sie eine Statusleiste im angegebenen Bereich an.

```
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
[in] Gibt den Index des Bereichs an, dessen Fortschrittsleiste aktiviert werden soll.

*nTotal*<br/>
[in] Gibt den Maximalwert für die Fortschrittsleiste an.

*bDisplayText*<br/>
[in] Gibt an, ob auf dem Fortschrittsbalken der aktuelle Fortschrittswert angezeigt werden soll.

*clrBar*<br/>
[in] Gibt die Hintergrundfarbe der Fortschrittsleiste an.

*clrBarDest*<br/>
[in] Gibt die sekundäre Farbe des Fortschrittsbalkenhintergrunds an. Verwenden Sie einen anderen Wert als *clrBar,* um eine Farbe zu füllen, die in einen Farbverlauf gemischt wird.

*clrProgressText*<br/>
[in] Gibt die Farbe des Textes der Statusleiste an.

### <a name="remarks"></a>Bemerkungen

Wenn Sie den Fortschrittsbalkenaufruf `EnablePaneProgressBar` deaktivieren möchten, wobei *nTotal* auf -1 gesetzt ist. Standardmäßig ist *nTotal* auf 100 festgelegt. Daher benötigen Sie keine zusätzlichen Berechnungen, um den Fortschritt als Prozentsatz anzuzeigen.

Sie sollten unterschiedliche Werte für *clrBar* und *clrBarDest* übergeben, damit die Hintergrundfarbe der Fortschrittsleiste eine Farbe anzeigt, die in einen Farbverlauf gemischt ist. .

Um den aktuellen Fortschritt festzulegen, rufen Sie die [CMFCStatusBar::SetPaneProgress-Methode](#setpaneprogress) auf.

## <a name="cmfcstatusbargetcount"></a><a name="getcount"></a>CMFCStatusBar::GetCount

Ruft die Anzahl der Bereiche in der Statusleiste ab.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bereiche in der Statusleiste.

## <a name="cmfcstatusbargetdrawextendedarea"></a><a name="getdrawextendedarea"></a>CMFCStatusBar::GetDrawExtendedArea

```
BOOL GetDrawExtendedArea() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCStatusBar::GetExtendedArea

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

[in] *rect*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetitemid"></a><a name="getitemid"></a>CMFCStatusBar::GetItemID

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetitemrect"></a><a name="getitemrect"></a>CMFCStatusBar::GetItemRect

```
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>
[in] *lpRect*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CMFCStatusBar::GetPaneInfo

```
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpaneprogress"></a><a name="getpaneprogress"></a>CMFCStatusBar::GetPaneProgress

```
long GetPaneProgress(int nIndex) const;
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpanestyle"></a><a name="getpanestyle"></a>CMFCStatusBar::GetPaneStyle

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpanetext"></a><a name="getpanetext"></a>CMFCStatusBar::GetPaneText

```
void GetPaneText(
    int nIndex,
    CString& s) const;

CString GetPaneText(int nIndex) const;
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>
[in] *s*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbargetpanewidth"></a><a name="getpanewidth"></a>CMFCStatusBar::GetPaneWidth

Ruft die Breite des Bereichs einer Statusleiste ab.

```
int GetPaneWidth(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Statusleistenbereichs an.

### <a name="return-value"></a>Rückgabewert

Die Breite des Statusleistenbereichs, den *nIndex* angibt. Andernfalls Null, wenn kein Statusleistenbereich vorhanden ist.

## <a name="cmfcstatusbargettiptext"></a><a name="gettiptext"></a>CMFCStatusBar::GetTipText

Rufen Sie den QuickInfo-Text des Bereichs einer Statusleiste ab.

```
CString GetTipText(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Bereichs an, für den QuickInfo-Text abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Der QuickInfo-Text des Statusleistenbereichs, den *nIndex* angibt. Andernfalls ist die leere Zeichenfolge, wenn ein Statusleistenbereich für den angegebenen *nIndex* nicht vorhanden ist oder wenn der QuickInfo-Text leer ist.

## <a name="cmfcstatusbarinvalidatepanecontent"></a><a name="invalidatepanecontent"></a>CMFCStatusBar::InvalidatePaneContent

Entkräften Sie den Statusleistenbereich, und zeichnen Sie den Inhalt neu.

```
void InvalidatePaneContent(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Bereichs an, dessen Inhalt ungültig gemacht und neu gezeichnet werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn die Statusleiste ungültig wird, wird sie für die Neuzeichnung markiert. Windows zeichnet es `UpdateWindow` neu, wenn die `OnPaint` Methode eine WM_PAINT Nachricht an die Methode sendet.

## <a name="cmfcstatusbarondrawpane"></a><a name="ondrawpane"></a>CMFCStatusBar::OnDrawPane

Zeichnen Sie den Bereich der Statusleiste neu.

```
virtual void OnDrawPane(
    CDC* pDC,
    CMFCStatusBarPaneInfo* pPane);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext zum Zeichnen.

*pPane*<br/>
[in] Ein Zeiger auf `CMFCStatusBarPaneInfo` eine Struktur, die die Informationen über den neu zu zeichnenden Bereich enthält.

### <a name="remarks"></a>Bemerkungen

Zeichnet den `OnDrawPane` Bereich standardmäßig mithilfe des *Gerätekontexts pDC* entsprechend dem Stil und inhalt des Bereichs neu.

Überschreiben Sie diese `CMFCStatusBar`Methode in einer -derived-Klasse, um die Darstellung eines Bereichs anzupassen.

## <a name="cmfcstatusbarprecreatewindow"></a><a name="precreatewindow"></a>CMFCStatusBar::PreCreateWindow

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>Parameter

[in] *cs*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetdrawextendedarea"></a><a name="setdrawextendedarea"></a>CMFCStatusBar::SetDrawExtendedArea

```
void SetDrawExtendedArea(BOOL bSet = TRUE);
```

### <a name="parameters"></a>Parameter

[in] *bSet*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetindicators"></a><a name="setindicators"></a>CMFCStatusBar::SetIndikatoren

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parameter

[in] *lpIDArray*<br/>
[in] *nIDCount*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpaneanimation"></a><a name="setpaneanimation"></a>CMFCStatusBar::SetPaneAnimation

Weist dem angegebenen Bereich eine Animation zu.

```
void SetPaneAnimation(
    int nIndex,
    HIMAGELIST hImageList,
    UINT nFrameRate=500,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Bereichs an, dem Sie eine Animation zuweisen möchten.

*hImageList*<br/>
[in] Gibt ein Handle für die Bildliste an, die die Animationsrahmen enthält.

*nFrameRate*<br/>
[in] Gibt die Bildrate in Millisekunden für die Animation an.

*bUpdate*<br/>
[in] Wenn TRUE, aktualisieren Sie den Bereichsinhalt sofort. Andernfalls wird der Bereichsinhalt aktualisiert, wenn er ungültig wird.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die aktuelle Animation `SetPaneAnimation` deaktivieren `hImageList` möchten, rufen Sie mit satz gleich null auf.

## <a name="cmfcstatusbarsetpanebackgroundcolor"></a><a name="setpanebackgroundcolor"></a>CMFCStatusBar::SetPaneBackgroundColor

Legt die Hintergrundfarbe des Statusleistenbereichs fest.

```
void SetPaneBackgroundColor(
    int nIndex,
    COLORREF clrBackground=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Bereichs an, für den eine neue Hintergrundfarbe festgelegt werden soll.

*clrBackground*<br/>
[in] Gibt die neue Hintergrundfarbe an.

*bUpdate*<br/>
[in] Wenn TRUE, aktualisieren Sie den Bereichsinhalt sofort. Aktualisieren Sie andernfalls den Bereichsinhalt erst, wenn der Bereich von einer anderen Methode für ungültig erklärt wurde.

## <a name="cmfcstatusbarsetpaneicon"></a><a name="setpaneicon"></a>CMFCStatusBar::SetPaneIcon

Legen Sie das Symbol des Statusleistenbereichs fest.

```
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
[in] Gibt den Index des Bereichs an, für den das Bild festgelegt werden soll.

*hIcon*<br/>
[in] Gibt ein Handle für das Symbol an, das als Bereichsbild festgelegt werden soll.

*bUpdate*<br/>
[in] Gibt an, ob der Bereichsinhalt sofort aktualisiert werden soll.

*hBmp*<br/>
[in] Gibt ein Handle für die Bitmap an, die als Bereichsbild festgelegt werden soll.

*clrTransparent*<br/>
[in] Gibt die transparente Farbe der Bitmap an, die der *hBmp* angibt.

### <a name="remarks"></a>Bemerkungen

Sie können entweder HICON oder HBITMAP zusammen mit der transparenten Farbe übergeben, um das Bild des Bereichs festzulegen. Wenn Sie das Bild nicht mehr anzeigen möchten, übergeben Sie den NULL-Wert als Bildhandle.

Wenn eine ausgeführte Animation vorhanden ist, die [CMFCStatusBar::SetPaneAnimation](#setpaneanimation) festgelegt hat, wird die Animation beendet.

## <a name="cmfcstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CMFCStatusBar::SetPaneInfo

```
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>
[in] *nID*<br/>
[in] *nStyle*<br/>
[in] *cxWidth*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpaneprogress"></a><a name="setpaneprogress"></a>CMFCStatusBar::SetPaneProgress

Legen Sie den aktuellen Fortschrittsindikator der Statusleiste für den angegebenen Bereich fest.

```
void SetPaneProgress(
    int nIndex,
    long nCurr,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Bereichs an, für den der Fortschrittsindikator aktualisiert werden soll.

*nCurr*<br/>
[in] Gibt den aktuellen Wert des Fortschrittsindikators an.

*bUpdate*<br/>
[in] Gibt an, ob der Bereich sofort aktualisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, wenn Sie die Fortschrittsanzeige für die Statusleiste im angegebenen Bereich aktualisieren möchten.

Um diese Funktion für den angegebenen Bereich verwenden zu können, müssen Sie zuerst [CMFCStatusBar::EnablePaneProgressBar](#enablepaneprogressbar) aufrufen.

## <a name="cmfcstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CMFCStatusBar::SetPaneStyle

```
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>
[in] *nStyle*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpanetext"></a><a name="setpanetext"></a>CMFCStatusBar::SetPaneText

```
virtual BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parameter

[in] *nIndex*<br/>
[in] *lpszNewText*<br/>
[in] *bUpdate*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcstatusbarsetpanetextcolor"></a><a name="setpanetextcolor"></a>CMFCStatusBar::SetPaneTextColor

Legt die Textfarbe des angegebenen Bereichs fest.

```
void SetPaneTextColor(
    int nIndex,
    COLORREF clrText=(COLORREF)-1,
    BOOL bUpdate=TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den Index des Bereichs an, dem Sie eine neue Textfarbe zuweisen möchten.

*clrText*<br/>
[in] Gibt die Textfarbe an.

*bUpdate*<br/>
[in] Wenn TRUE, aktualisieren Sie den Bereichsinhalt sofort. Aktualisieren Sie andernfalls den Bereichsinhalt erst, wenn der Bereich von einer anderen Methode für ungültig erklärt wurde.

## <a name="cmfcstatusbarsetpanewidth"></a><a name="setpanewidth"></a>CMFCStatusBar::SetPaneWidth

Legen Sie die Breite des Statusleistenbereichs fest.

```
void SetPaneWidth(
    int nIndex,
    int cx);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Der Index des Statusleistenbereichs, für den eine neue Breite festgelegt werden soll.

*Cx*<br/>
[in] Die neue Breite des Statusleistenbereichs in Pixel.

## <a name="cmfcstatusbarsettiptext"></a><a name="settiptext"></a>CMFCStatusBar::SetTipText

Legen Sie den QuickInfo-Text eines Statusleistenbereichs fest.

```
void SetTipText(
    int nIndex,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Der Index des Bereichs, dem Sie den QuickInfo-Text zuweisen möchten.

*pszTipText*<br/>
[in] Der neue QuickInfo-Text.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)<br/>
[CStatusBar-Klasse](../../mfc/reference/cstatusbar-class.md)
