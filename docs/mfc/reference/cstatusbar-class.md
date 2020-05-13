---
title: CStatusBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStatusBar
- AFXEXT/CStatusBar
- AFXEXT/CStatusBar::CStatusBar
- AFXEXT/CStatusBar::CommandToIndex
- AFXEXT/CStatusBar::Create
- AFXEXT/CStatusBar::CreateEx
- AFXEXT/CStatusBar::DrawItem
- AFXEXT/CStatusBar::GetItemID
- AFXEXT/CStatusBar::GetItemRect
- AFXEXT/CStatusBar::GetPaneInfo
- AFXEXT/CStatusBar::GetPaneStyle
- AFXEXT/CStatusBar::GetPaneText
- AFXEXT/CStatusBar::GetStatusBarCtrl
- AFXEXT/CStatusBar::SetIndicators
- AFXEXT/CStatusBar::SetPaneInfo
- AFXEXT/CStatusBar::SetPaneStyle
- AFXEXT/CStatusBar::SetPaneText
helpviewer_keywords:
- CStatusBar [MFC], CStatusBar
- CStatusBar [MFC], CommandToIndex
- CStatusBar [MFC], Create
- CStatusBar [MFC], CreateEx
- CStatusBar [MFC], DrawItem
- CStatusBar [MFC], GetItemID
- CStatusBar [MFC], GetItemRect
- CStatusBar [MFC], GetPaneInfo
- CStatusBar [MFC], GetPaneStyle
- CStatusBar [MFC], GetPaneText
- CStatusBar [MFC], GetStatusBarCtrl
- CStatusBar [MFC], SetIndicators
- CStatusBar [MFC], SetPaneInfo
- CStatusBar [MFC], SetPaneStyle
- CStatusBar [MFC], SetPaneText
ms.assetid: a3bde3db-e71c-4881-a3ca-1d5481c345ba
ms.openlocfilehash: 969edb3b1c87da851d83d390ab9d4e707bd2eb1e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753056"
---
# <a name="cstatusbar-class"></a>CStatusBar-Klasse

Eine Steuerleiste mit einer Zeile von Textausgabebereichen ("Indikatoren" genannt).

## <a name="syntax"></a>Syntax

```
class CStatusBar : public CControlBar
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStatusBar::CStatusBar](#cstatusbar)|Erstellt ein `CStatusBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStatusBar::CommandToIndex](#commandtoindex)|Ruft den Index für eine bestimmte Indikator-ID ab.|
|[CStatusBar::Erstellen](#create)|Erstellt die Statusleiste, fügt `CStatusBar` sie an das Objekt an und legt die ursprüngliche Schriftart und Balkenhöhe fest.|
|[CStatusBar::CreateEx](#createex)|Erstellt `CStatusBar` ein Objekt mit zusätzlichen `CStatusBarCtrl` Stilen für das eingebettete Objekt.|
|[CStatusBar::DrawItem](#drawitem)|Wird aufgerufen, wenn sich ein visueller Aspekt eines Besitzerzeichnungsstatusleistensteuerelements ändert.|
|[CStatusBar::GetItemID](#getitemid)|Ruft die Indikator-ID für einen bestimmten Index ab.|
|[CStatusBar::GetItemRect](#getitemrect)|Ruft das Anzeigerechteck für einen bestimmten Index ab.|
|[CStatusBar::GetPaneInfo](#getpaneinfo)|Ruft Indikator-ID, Stil und Breite für einen bestimmten Index ab.|
|[CStatusBar::GetPaneStyle](#getpanestyle)|Ruft den Indikatorstil für einen bestimmten Index ab.|
|[CStatusBar::GetPaneText](#getpanetext)|Ruft Indikatortext für einen bestimmten Index ab.|
|[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl)|Ermöglicht den direkten Zugriff auf das zugrunde liegende gemeinsame Steuerelement.|
|[CStatusBar::SetIndicators](#setindicators)|Legt Indikator-IDs fest.|
|[CStatusBar::SetPaneInfo](#setpaneinfo)|Legt Indikator-ID, Stil und Breite für einen bestimmten Index fest.|
|[CStatusBar::SetPaneStyle](#setpanestyle)|Legt den Indikatorstil für einen bestimmten Index fest.|
|[CStatusBar::SetPaneText](#setpanetext)|Legt Indikatortext für einen bestimmten Index fest.|

## <a name="remarks"></a>Bemerkungen

Die Ausgabebereiche werden häufig als Nachrichtenlinien und als Statusindikatoren verwendet. Beispiele hierfür sind die Menü-Hilfe-Meldungszeilen, die den ausgewählten Menübefehl kurz erläutern, sowie die Indikatoren, die den Status der SCROLL LOCK, NUM LOCK und anderer Tasten anzeigen.

[CStatusBar::GetStatusBarCtrl](#getstatusbarctrl), eine Memberfunktion, die neu in MFC 4.0 ist, ermöglicht es Ihnen, die Unterstützung des gemeinsamen Windows-Steuerelements für die Anpassung der Statusleiste und zusätzliche Funktionen zu nutzen. `CStatusBar`Memberfunktionen bieten Ihnen die meisten Funktionen der allgemeinen Windows-Steuerelemente. Wenn Sie jedoch `GetStatusBarCtrl`anrufen, können Sie Ihren Statusleisten noch mehr eigenschaften einer Windows 95/98-Statusleiste geben. Wenn Sie `GetStatusBarCtrl`aufrufen, wird ein `CStatusBarCtrl` Verweis auf ein Objekt zurückgegeben. Weitere Informationen zum Entwerfen von Symbolleisten mit allgemeinen Windows-Steuerelementen finden Sie unter [CStatusBarCtrl.](../../mfc/reference/cstatusbarctrl-class.md) Allgemeinere Informationen zu allgemeinen Steuerelementen finden Sie unter [Allgemeine Steuerelemente](/windows/win32/Controls/common-controls-intro) im Windows SDK.

Das Framework speichert Indikatorinformationen in einem Array mit dem linken Indikator an Position 0. Wenn Sie eine Statusleiste erstellen, verwenden Sie ein Array von Zeichenfolgen-IDs, die das Framework den entsprechenden Indikatoren zuordnet. Sie können dann entweder eine Zeichenfolgen-ID oder einen Index verwenden, um auf einen Indikator zuzugreifen.

Standardmäßig ist der erste Indikator "elastisch": Er nimmt die Statusleistenlänge auf, die von den anderen Indikatorbereichen nicht verwendet wird, sodass die anderen Bereiche rechtsbündig ausgerichtet sind.

Führen Sie die folgenden Schritte aus, um eine Statusleiste zu erstellen:

1. Erstellen `CStatusBar` Sie das Objekt.

1. Rufen Sie die Funktion [Erstellen](#create) (oder [CreateEx](#createex)) auf, `CStatusBar` um das Statusleistenfenster zu erstellen und es an das Objekt anzuhängen.

1. Rufen Sie [SetIndicators](#setindicators) auf, um jedem Indikator eine Zeichenfolgen-ID zuzuordnen.

Es gibt drei Möglichkeiten, den Text in einem Statusleistenbereich zu aktualisieren:

1. Rufen Sie [CWnd::SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext) auf, um den Text nur im Bereich 0 zu aktualisieren.

1. Rufen Sie [CCmdUI::SetText](../../mfc/reference/ccmdui-class.md#settext) im ON_UPDATE_COMMAND_UI-Handler der Statusleiste auf.

1. Rufen Sie [SetPaneText](#setpanetext) auf, um den Text für jeden Bereich zu aktualisieren.

Rufen Sie [SetPaneStyle](#setpanestyle) auf, um den Stil eines Statusleistenbereichs zu aktualisieren.

Weitere Informationen zur `CStatusBar`Verwendung finden Sie im Artikel [Statusleistenimplementierung in MFC](../../mfc/status-bar-implementation-in-mfc.md) und [Technical Note 31 : Control Bars](../../mfc/tn031-control-bars.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CStatusBar`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxext.h

## <a name="cstatusbarcommandtoindex"></a><a name="commandtoindex"></a>CStatusBar::CommandToIndex

Ruft den Indikatorindex für eine bestimmte ID ab.

```
int CommandToIndex(UINT nIDFind) const;
```

### <a name="parameters"></a>Parameter

*nIDFind*<br/>
Zeichenfolgen-ID des Indikators, dessen Index abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des Indikators, wenn erfolgreich; -1 wenn nicht erfolgreich.

### <a name="remarks"></a>Bemerkungen

Der Index des ersten Indikators ist 0.

## <a name="cstatusbarcreate"></a><a name="create"></a>CStatusBar::Erstellen

Erstellt eine Statusleiste (ein untergeordnetes Fenster) und ordnet sie dem `CStatusBar` Objekt zu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeiger auf das [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) dessen Windows-Fenster das übergeordnete Element der Statusleiste ist.

*dwStyle*<br/>
Der Statusleistenstil. Zusätzlich zu den Standardmäßigen [Windows-Stilen](../../mfc/reference/styles-used-by-mfc.md#window-styles)werden diese Stile unterstützt.

- CBRS_TOP Steuerleiste befindet sich oben im Rahmenfenster.

- CBRS_BOTTOM Steuerleiste befindet sich am unteren Rand des Rahmenfensters.

- CBRS_NOALIGN Steuerleiste wird nicht neu positioniert, wenn die Größe des übergeordneten Elements geändert wird.

*nID*<br/>
Die untergeordnete Fenster-ID der Symbolleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Legt außerdem die anfangsschriftart und die Höhe der Statusleiste auf einen Standardwert fest.

## <a name="cstatusbarcreateex"></a><a name="createex"></a>CStatusBar::CreateEx

Rufen Sie diese Funktion auf, um eine Statusleiste `CStatusBar` (ein untergeordnetes Fenster) zu erstellen und sie dem Objekt zuzuordnen.

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = 0,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | CBRS_BOTTOM,
    UINT nID = AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeiger auf das [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) dessen Windows-Fenster das übergeordnete Element der Statusleiste ist.

*dwCtrlStyle*<br/>
Zusätzliche Stile für die Erstellung des eingebetteten [CStatusBarCtrl-Objekts.](../../mfc/reference/cstatusbarctrl-class.md) Der Standardwert gibt eine Statusleiste ohne Größengriff oder QuickInfo-Unterstützung an. Unterstützt werden Statusleistenstile:

- SBARS_SIZEGRIP Die Statusleistensteuerung enthält einen Größengriff am rechten Ende der Statusleiste. Ein Größengriff ähnelt einem Größenrahmen. Es handelt sich um einen rechteckigen Bereich, auf den der Benutzer klicken und ziehen kann, um die Größe des übergeordneten Fensters zu ändern.

- SBT_TOOLTIPS Die Statusleiste unterstützt QuickInfos.

Weitere Informationen zu diesen Stilen finden Sie unter [Einstellungen für die CStatusBarCtrl](../../mfc/settings-for-the-cstatusbarctrl.md).

*dwStyle*<br/>
Der Statusleistenstil. Der Standardwert gibt an, dass eine sichtbare Statusleiste am unteren Rand des Rahmenfensters erstellt wird. Wenden Sie eine beliebige Kombination von Statusleistensteuerelementstilen an, die in [Fensterstilen](../../mfc/reference/styles-used-by-mfc.md#window-styles) und [CDialogBar::Create](../../mfc/reference/cdialogbar-class.md#create)aufgeführt sind. Dieser Parameter sollte jedoch immer die WS_CHILD- und WS_VISIBLE-Stile enthalten.

*nID*<br/>
Die untergeordnete Fenster-ID der Statusleiste.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Funktion legt auch die anfangse Schriftart fest und legt die Höhe der Statusleiste auf einen Standardwert fest.

Verwenden `CreateEx`Sie anstelle von [Create](#create), wenn bestimmte Stile während der Erstellung des eingebetteten Statusleistensteuerelements vorhanden sein müssen. Legen Sie beispielsweise *dwCtrlStyle* auf SBT_TOOLTIPS, um QuickInfos in einem Statusleistenobjekt anzuzeigen.

## <a name="cstatusbarcstatusbar"></a><a name="cstatusbar"></a>CStatusBar::CStatusBar

Erstellt ein `CStatusBar` Objekt, erstellt bei Bedarf eine Standardschriftleiste und legt die Schriftartaufwerte auf Standardwerte fest.

```
CStatusBar();
```

## <a name="cstatusbardrawitem"></a><a name="drawitem"></a>CStatusBar::DrawItem

Diese Memberfunktion wird vom Framework aufgerufen, wenn sich ein visueller Aspekt einer vom Besitzer gezeichneten Statusleiste ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die Informationen über den erforderlichen Zeichnungstyp enthält.

### <a name="remarks"></a>Bemerkungen

Das `itemAction` Element `DRAWITEMSTRUCT` der Struktur definiert die Zeichnungsaktion, die ausgeführt werden soll. Überschreiben Sie diese Memberfunktion, um `CStatusBar` die Zeichnung für ein Besitzerzeichnungsobjekt zu implementieren. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den anzeigekontext ausgewählt wurden, der in *lpDrawItemStruct* vor dem Beenden dieser Memberfunktion angegeben wurde.

## <a name="cstatusbargetitemid"></a><a name="getitemid"></a>CStatusBar::GetItemID

Gibt die ID des von *nIndex*angegebenen Indikators zurück.

```
UINT GetItemID(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Indikators, dessen ID abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Die ID des Indikators, der von *nIndex*angegeben wird.

## <a name="cstatusbargetitemrect"></a><a name="getitemrect"></a>CStatusBar::GetItemRect

Kopiert die Koordinaten des von *nIndex* angegebenen Indikators in die Struktur, auf die *lpRect*zeigt.

```cpp
void GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Indikators, dessen Rechteckkoordinaten abgerufen werden sollen.

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt,](../../atl-mfc-shared/reference/crect-class.md) das die Koordinaten des von *nIndex*angegebenen Indikators empfängt.

### <a name="remarks"></a>Bemerkungen

Koordinaten sind in Pixel relativ zur oberen linken Ecke der Statusleiste.

## <a name="cstatusbargetpaneinfo"></a><a name="getpaneinfo"></a>CStatusBar::GetPaneInfo

Legt *nID*, *nStyle*und *cxWidth* auf die ID, den Stil und die Breite des Indikatorbereichs an der von *nIndex*angegebenen Position fest.

```cpp
void GetPaneInfo(
    int nIndex,
    UINT& nID,
    UINT& nStyle,
    int& cxWidth) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Bereichs, dessen Informationen abgerufen werden sollen.

*nID*<br/>
Verweis auf ein UINT, das auf die ID des Bereichs festgelegt ist.

*nStyle*<br/>
Verweis auf ein UINT, das auf den Stil des Bereichs festgelegt ist.

*cxWidth*<br/>
Verweis auf eine ganze Zahl, die auf die Breite des Bereichs festgelegt ist.

## <a name="cstatusbargetpanestyle"></a><a name="getpanestyle"></a>CStatusBar::GetPaneStyle

Rufen Sie diese Memberfunktion auf, um den Stil des Bereichs einer Statusleiste abzurufen.

```
UINT GetPaneStyle(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Bereichs, dessen Stil abgerufen werden soll.

### <a name="return-value"></a>Rückgabewert

Der Stil des status-bar-Bereichs, der von *nIndex*angegeben wird.

### <a name="remarks"></a>Bemerkungen

Der Stil eines Bereichs bestimmt, wie der Bereich angezeigt wird.

Eine Liste der Stile, die für Statusleisten verfügbar sind, finden Sie unter [Erstellen](#create)von .

## <a name="cstatusbargetpanetext"></a><a name="getpanetext"></a>CStatusBar::GetPaneText

Rufen Sie diese Memberfunktion auf, um den Text abzurufen, der in einem Statusleistenbereich angezeigt wird.

```
CString GetPaneText(int nIndex) const;  void GetPaneText(int nIndex, CString& rString) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Bereichs, dessen Text abgerufen werden soll.

*rString*<br/>
Ein Verweis auf ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das den abzuholenden Text enthält.

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den Text des Bereichs enthält.

### <a name="remarks"></a>Bemerkungen

Die zweite Form dieser Memberfunktion `CString` füllt ein Objekt mit dem Zeichenfolgentext.

## <a name="cstatusbargetstatusbarctrl"></a><a name="getstatusbarctrl"></a>CStatusBar::GetStatusBarCtrl

Diese Memberfunktion ermöglicht den direkten Zugriff auf das zugrunde liegende gemeinsame Steuerelement.

```
CStatusBarCtrl& GetStatusBarCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Enthält einen Verweis auf ein [CStatusBarCtrl-Objekt.](../../mfc/reference/cstatusbarctrl-class.md)

### <a name="remarks"></a>Bemerkungen

Verwenden `GetStatusBarCtrl` Sie diese Möglichkeit, um die Funktionalität des allgemeinen Windows-Statusleistensteuerelements zu nutzen und die Unterstützung zu nutzen, die [CStatusBarCtrl](../../mfc/reference/cstatusbarctrl-class.md) für die Anpassung der Statusleiste bereitstellt. Mithilfe des allgemeinen Steuerelements können Sie beispielsweise einen Stil angeben, der einen Größengriff auf der Statusleiste enthält, oder Sie können einen Stil angeben, der die Statusleiste oben im Clientbereich des übergeordneten Fensters anzeigen soll.

Allgemeinere Informationen zu allgemeinen Steuerelementen finden Sie unter [Allgemeine Steuerelemente](/windows/win32/Controls/common-controls-intro) im Windows SDK.

## <a name="cstatusbarsetindicators"></a><a name="setindicators"></a>CStatusBar::SetIndicators

Legt die ID jedes Indikators auf den Wert fest, der durch das entsprechende Element des *Arrays lpIDArray*angegeben wird, die zeichenfolgenRessource lädt, die von jeder ID angegeben wird, und legt den Text des Indikators auf die Zeichenfolge fest.

```
BOOL SetIndicators(
    const UINT* lpIDArray,
    int nIDCount);
```

### <a name="parameters"></a>Parameter

*lpIDArray*<br/>
Zeiger auf ein Array von IDs.

*nIDCount*<br/>
Anzahl der Elemente im Array, auf die von *lpIDArray*verwiesen wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

## <a name="cstatusbarsetpaneinfo"></a><a name="setpaneinfo"></a>CStatusBar::SetPaneInfo

Legt den angegebenen Indikatorbereich auf eine neue ID, Einen neuen Stil und eine neue Breite fest.

```cpp
void SetPaneInfo(
    int nIndex,
    UINT nID,
    UINT nStyle,
    int cxWidth);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Indikatorbereichs, dessen Stil festgelegt werden soll.

*nID*<br/>
Neue ID für den Indikatorbereich.

*nStyle*<br/>
Neuer Stil für den Indikatorbereich.

*cxWidth*<br/>
Neue Breite für den Indikatorbereich.

### <a name="remarks"></a>Bemerkungen

Die folgenden Indikatorstile werden unterstützt:

- SBPS_NOBORDERS Kein 3D-Rahmen um die Scheibe.

- SBPS_POPOUT Umkehrendes Rand, sodass der Text "herausspringt".

- SBPS_DISABLED Zeichnen Sie keinen Text.

- SBPS_STRETCH Stretch-Bereich, um nicht genutzten Speicherplatz zu füllen. Nur ein Bereich pro Statusleiste kann diesen Stil haben.

- SBPS_NORMAL Keine Dehnung, Keine Grenzen oder Pop-out.

## <a name="cstatusbarsetpanestyle"></a><a name="setpanestyle"></a>CStatusBar::SetPaneStyle

Rufen Sie diese Memberfunktion auf, um den Stil des Bereichs einer Statusleiste festzulegen.

```cpp
void SetPaneStyle(
    int nIndex,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Bereichs, dessen Stil festgelegt werden soll.

*nStyle*<br/>
Stil des Bereichs, dessen Stil festgelegt werden soll.

### <a name="remarks"></a>Bemerkungen

Der Stil eines Bereichs bestimmt, wie der Bereich angezeigt wird.

Eine Liste der Stile, die für Statusleisten verfügbar sind, finden Sie unter [SetPaneInfo](#setpaneinfo).

## <a name="cstatusbarsetpanetext"></a><a name="setpanetext"></a>CStatusBar::SetPaneText

Rufen Sie diese Memberfunktion auf, um den Bereichstext auf die Zeichenfolge festzulegen, auf die von *lpszNewText*verwiesen wird.

```
BOOL SetPaneText(
    int nIndex,
    LPCTSTR lpszNewText,
    BOOL bUpdate = TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Bereichs, dessen Text festgelegt werden soll.

*lpszNewText*<br/>
Zeigen Sie auf den neuen Bereichstext.

*bUpdate*<br/>
Wenn TRUE, wird der Bereich ungültig, nachdem der Text festgelegt wurde.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Nach dem `SetPaneText`Aufruf müssen Sie einen UI-Aktualisierungshandler hinzufügen, um den neuen Text in der Statusleiste anzuzeigen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#176](../../mfc/codesnippet/cpp/cstatusbar-class_1.cpp)]

[!code-cpp[NVC_MFCDocView#177](../../mfc/codesnippet/cpp/cstatusbar-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#178](../../mfc/codesnippet/cpp/cstatusbar-class_3.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel STRGBARS](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DLGCBR32](../../overview/visual-cpp-samples.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CStatusBarCtrl-Klasse](../../mfc/reference/cstatusbarctrl-class.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)
