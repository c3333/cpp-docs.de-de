---
title: CMFCRibbonStatusBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: f76c2014cd3f6ed6e479fb66436224e675c69569
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368819"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar-Klasse

Die `CMFCRibbonStatusBar` Klasse implementiert ein Statusleistensteuerelement, das Multifunktionsleistenelemente anzeigen kann.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|Fügt der Multifunktionsleistenstatusleiste ein dynamisches Element hinzu.|
|[CMFCRibbonStatusBar::AddElement](#addelement)|Fügt der Multifunktionsleistenstatusleiste ein neues Multifunktionsleistenelement hinzu.|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|Fügt dem erweiterten Bereich der Multifunktionsleistenstatusleiste ein Multifunktionsleistenelement hinzu.|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|Fügt der Multifunktionsleistenstatusleiste ein Trennzeichen hinzu.|
|[CMFCRibbonStatusBar::Erstellen](#create)|Erstellt eine Multifunktionsleistenstatusleiste.|
|[CMFCRibbonStatusBar::CreateEx](#createex)|Erstellt eine Multifunktionsleistenstatusleiste mit einem erweiterten Stil.|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|Gibt einen Zeiger auf das Element zurück, das die angegebene Befehls-ID hat.|
|[CMFCRibbonStatusBar::GetCount](#getcount)|Gibt die Anzahl der Elemente zurück, die sich im Hauptbereich der Multifunktionsleistenstatusleiste befinden.|
|[CMFCRibbonStatusBar::GetElement](#getelement)|Gibt einen Zeiger auf das Element zurück, das sich an einem angegebenen Index befindet.|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|Gibt die Anzahl der Elemente zurück, die sich im erweiterten Bereich der Multifunktionsleistenstatusleiste befinden.|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|Gibt einen Zeiger auf das Element zurück, das sich an einem angegebenen Index im erweiterten Bereich des Status-Menübands befindet.|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomframe](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|Bestimmt, ob der Informationsmodus für die Multifunktionsleistenstatusleiste aktiviert ist.|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(Überschreibt [CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout).)|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|Entfernt alle Elemente aus der Multifunktionsleistenstatusleiste.|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|Entfernt das Element mit einer angegebenen Befehls-ID aus der Multifunktionsleistenstatusleiste.|
|[CMFCRibbonStatusBar::SetInformationen](#setinformation)|Aktiviert oder deaktiviert den Informationsmodus für die Multifunktionsleistenstatusleiste.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCRibbonStatusbar::OnDrawInformation](#ondrawinformation)|Zeigt die Informationszeichenfolge an, die auf der Multifunktionsleistenstatusleiste angezeigt wird, wenn der Informationsmodus aktiviert ist.|

## <a name="remarks"></a>Bemerkungen

Benutzer können die Sichtbarkeit von Multifunktionsleistenelementen in einer Multifunktionsleistenstatusleiste ändern, indem sie das integrierte Kontextmenü für die Menübandstatusleiste verwenden. Sie können Elemente dynamisch hinzufügen oder entfernen.

Eine Multifunktionsleisten-Statusleiste besteht aus zwei Bereichen: einem Hauptbereich und einem erweiterten Bereich. Der erweiterte Bereich wird auf der rechten Seite der Multifunktionsleisten-Statusleiste angezeigt und wird in einer anderen Farbe als der Hauptbereich angezeigt.

In der Regel werden im Hauptbereich der Statusleiste Statusbenachrichtigungen angezeigt, und im erweiterten Bereich werden Ansichtssteuerelemente angezeigt. Der erweiterte Bereich bleibt so lange wie möglich sichtbar, wenn der Benutzer die Größe der Multifunktionsleistenstatusleiste ändert.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung verschiedener Methoden in der `CMFCRibbonStatusBar` -Klasse. Das Beispiel zeigt, wie Sie der Multifunktionsleistenstatusleiste ein neues Multifunktionsleistenelement hinzufügen, dem erweiterten Bereich der Multifunktionsleistenstatusleiste ein Multifunktionsleistenelement hinzufügen, ein Trennzeichen hinzufügen und den regulären Modus für die Multifunktionsleistenstatusleiste aktivieren.

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxribbonstatusbar.h

## <a name="cmfcribbonstatusbaradddynamicelement"></a><a name="adddynamicelement"></a>CMFCRibbonStatusBar::AddDynamicElement

Fügt der Multifunktionsleistenstatusleiste ein dynamisches Element hinzu.

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>Parameter

*pElement*<br/>
[in] Ein Zeiger auf ein dynamisches Element.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zu regulären Elementen können dynamische Elemente nicht angepasst werden, und das Menü "Anpassen" der Statusleiste zeigt sie nicht an.

## <a name="cmfcribbonstatusbaraddelement"></a><a name="addelement"></a>CMFCRibbonStatusBar::AddElement

Fügt der Multifunktionsleistenstatusleiste ein neues Multifunktionsleistenelement hinzu.

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parameter

*pElement*<br/>
[in] Ein Zeiger auf das hinzugefügte Element.

*lpszLabel*<br/>
[in] Eine Textbeschriftung des Elements.

*bIsVisible*<br/>
[in] TRUE, wenn Sie das Element als sichtbar hinzufügen möchten, FALSE, wenn Sie das Element als ausgeblendet hinzufügen möchten.

## <a name="cmfcribbonstatusbaraddextendedelement"></a><a name="addextendedelement"></a>CMFCRibbonStatusBar::AddExtendedElement

Fügt dem erweiterten Bereich der Multifunktionsleistenstatusleiste ein Multifunktionsleistenelement hinzu.

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>Parameter

*pElement*<br/>
[in] Ein Zeiger auf das hinzugefügte Element.

*lpszLabel*<br/>
[in] Die Textbeschriftung des Elements.

*bIsVisible*<br/>
[in] TRUE, wenn Sie das Element als sichtbar hinzufügen möchten, FALSE, wenn Sie das Element als ausgeblendet hinzufügen möchten.

### <a name="remarks"></a>Bemerkungen

Der erweiterte Bereich befindet sich rechts vom Statusleisten-Steuerelement.

## <a name="cmfcribbonstatusbaraddseparator"></a><a name="addseparator"></a>CMFCRibbonStatusBar::AddSeparator

Fügt der Multifunktionsleistenstatusleiste ein Trennzeichen hinzu.

```
void AddSeparator();
```

### <a name="remarks"></a>Bemerkungen

Das Framework fügt ein Trennzeichen nach der Methode [CMFCRibbonStatusBar::AddElement](#addelement)hinzu. fügt das letzte Element ein.

## <a name="cmfcribbonstatusbarcreate"></a><a name="create"></a>CMFCRibbonStatusBar::Erstellen

Erstellt eine Multifunktionsleistenstatusleiste.

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster.

*dwStyle*<br/>
[in] Eine logische ODER-Kombination von Steuerelementstilen.

*nID*<br/>
[in] Die Steuer-ID der Statusleiste.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Statusleiste erfolgreich erstellt wurde, ANDERNFALLS FALSE.

## <a name="cmfcribbonstatusbarcreateex"></a><a name="createex"></a>CMFCRibbonStatusBar::CreateEx

Erstellt eine Multifunktionsleistenstatusleiste mit einem erweiterten Stil.

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster.

*dwCtrlStyle*<br/>
Eine logische ODER-Kombination zusätzlicher Stile zum Erstellen des Statusleistenobjekts.

*dwStyle*<br/>
Der Steuerelementstil der Statusleiste.

*nID*<br/>
Die Steuer-ID der Statusleiste.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Statusleiste erfolgreich erstellt wurde, ANDERNFALLS FALSE.

## <a name="cmfcribbonstatusbarfindbyid"></a><a name="findbyid"></a>CMFCRibbonStatusBar::FindByID

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>Parameter

[in] *uiCmdID*<br/>
[in] *BOOL*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarfindelement"></a><a name="findelement"></a>CMFCRibbonStatusBar::FindElement

Gibt einen Zeiger auf das Element zurück, das die angegebene Befehls-ID hat.

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Die ID des Elements.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Element mit der angegebenen Befehls-ID. NULL, wenn kein solches Element vorhanden ist.

## <a name="cmfcribbonstatusbargetcount"></a><a name="getcount"></a>CMFCRibbonStatusBar::GetCount

Gibt die Anzahl der Elemente zurück, die sich im Hauptbereich der Multifunktionsleistenstatusleiste befinden.

```
int GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die sich im Hauptbereich der Multifunktionsleistenstatusleiste befinden.

## <a name="cmfcribbonstatusbargetelement"></a><a name="getelement"></a>CMFCRibbonStatusBar::GetElement

Gibt einen Zeiger auf das Element zurück, das sich an einem angegebenen Index befindet.

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt einen nullbasierten Index eines Elements an, das sich im Hauptbereich des Statusleistensteuerelements befindet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Element, das sich am angegebenen Index befindet. NULL, wenn der Index negativ ist oder die Anzahl der Elemente in der Statusleiste überschreitet.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbargetexcount"></a><a name="getexcount"></a>CMFCRibbonStatusBar::GetExCount

Gibt die Anzahl der Elemente zurück, die sich im erweiterten Bereich der Multifunktionsleistenstatusleiste befinden.

```
int GetExCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente, die sich im erweiterten Bereich der Multifunktionsleistenstatusleiste befinden.

## <a name="cmfcribbonstatusbargetexelement"></a><a name="getexelement"></a>CMFCRibbonStatusBar::GetExElement

Gibt einen Zeiger auf das Element zurück, das sich an einem angegebenen Index im erweiterten Bereich des Status-Menübands befindet. Der erweiterte Bereich befindet sich rechts vom Statusleisten-Steuerelement.

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
[in] Gibt den nullbasierten Index eines Elements an, das sich im erweiterten Bereich des Statusleistensteuerelements befindet.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Element, das sich an einem angegebenen Index im erweiterten Bereich des Status-Menübands befindet. NULL, wenn *nIndex* negativ ist oder die Anzahl der Elemente im erweiterten Bereich der Multifunktionsleistenstatusleiste überschreitet.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbargetextendedarea"></a><a name="getextendedarea"></a>CMFCRibbonStatusBar::GetExtendedArea

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>Parameter

[in] *rect*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbargetspace"></a><a name="getspace"></a>CMFCRibbonStatusBar::GetSpace

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
int GetSpace() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarisbottomframe"></a><a name="isbottomframe"></a>CMFCRibbonStatusBar::IsBottomframe

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarisextendedelement"></a><a name="isextendedelement"></a>CMFCRibbonStatusBar::IsExtendedElement

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>Parameter

[in] *pElement*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarisinformationmode"></a><a name="isinformationmode"></a>CMFCRibbonStatusBar::IsInformationMode

Bestimmt, ob der Informationsmodus für die Multifunktionsleistenstatusleiste aktiviert ist.

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Statusleiste im Informationsmodus funktionieren kann; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Im Informationsmodus blendet die Statusleiste alle regulären Bereiche aus und zeigt eine Nachrichtenzeichenfolge an.

## <a name="cmfcribbonstatusbarondrawinformation"></a><a name="ondrawinformation"></a>CMFCRibbonStatusbar::OnDrawInformation

Zeigt die Zeichenfolge an, die auf der Multifunktionsleistenstatusleiste angezeigt wird, wenn der Informationsmodus aktiviert ist.

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*strInfo*<br/>
[in] Die Informationszeichenfolge.

*rectInfo*<br/>
[in] Das umgrenzende Rechteck.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, wenn Sie die Darstellung der Informationszeichenfolge in der Statusleiste anpassen möchten. Verwenden Sie die [CMFCRibbonStatusBar::SetInformation-Methode,](#setinformation) um die Statusleiste in den Informationsmodus zu versetzen. In diesem Modus blendet die Statusleiste alle Bereiche aus und zeigt die von *strInfo*angegebene Informationszeichenfolge an.

## <a name="cmfcribbonstatusbarrecalclayout"></a><a name="recalclayout"></a>CMFCRibbonStatusBar::RecalcLayout

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcribbonstatusbarremoveall"></a><a name="removeall"></a>CMFCRibbonStatusBar::RemoveAll

Entfernt alle Elemente aus der Multifunktionsleistenstatusleiste.

```
void RemoveAll();
```

## <a name="cmfcribbonstatusbarremoveelement"></a><a name="removeelement"></a>CMFCRibbonStatusBar::RemoveElement

Entfernt das Element mit einer angegebenen Befehls-ID aus der Multifunktionsleistenstatusleiste.

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>Parameter

*uiID*<br/>
[in] Die ID des Elements, das aus der Statusleiste entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Element mit der angegebenen *uiID* entfernt wird. FALSE sonst.

## <a name="cmfcribbonstatusbarsetinformation"></a><a name="setinformation"></a>CMFCRibbonStatusBar::SetInformationen

Aktiviert oder deaktiviert den Informationsmodus für die Multifunktionsleistenstatusleiste.

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>Parameter

*lpszInfo*<br/>
[in] Die Informationszeichenfolge.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Statusleiste in den Informationsmodus zu versetzen. In diesem Modus blendet die Statusleiste alle Bereiche aus und zeigt die von *lpszInfo*angegebene Informationszeichenfolge an.

Wenn lpszInfo NULL ist, wird die Statusleiste in den regulären Modus zurückversetzt.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement-Klasse](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar-Klasse](../../mfc/reference/cmfcribbonbar-class.md)
