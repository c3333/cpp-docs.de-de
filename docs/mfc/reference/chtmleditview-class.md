---
title: CHtmlEditView-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 20d4586c1ae45e5f3f56c0adbb1ecb1757084fd7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752319"
---
# <a name="chtmleditview-class"></a>CHtmlEditView-Klasse

Stellt die Funktionalität der WebBrowser-Bearbeitungsplattform im Kontext der MFC-Dokument-/Ansichtarchitektur bereit.

## <a name="syntax"></a>Syntax

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|Erstellt ein `CHtmlEditView`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHtmlEditView::Erstellen](#create)|Erstellt ein neues Fensterobjekt.|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|Gibt `IHTMLDocument2` die Schnittstelle für das aktuelle Dokument zurück.|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|Ruft den Namen des Standarddokuments für diese Ansicht ab.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[Chtmlview](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxhtml.h

## <a name="chtmleditviewchtmleditview"></a><a name="chtmleditview"></a>CHtmlEditView::CHtmlEditView

Erstellt ein `CHtmlEditView`-Objekt.

```
CHtmlEditView();
```

## <a name="chtmleditviewcreate"></a><a name="create"></a>CHtmlEditView::Erstellen

Erstellt ein neues Fensterobjekt.

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Verweist auf eine null-beendete Zeichenfolge, die die Windows-Klasse benennt. Der Klassenname kann ein beliebiger Name sein, der `RegisterClass` mit der globalen Funktion [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass) oder der Windows-Funktion registriert ist. Wenn NULL, verwendet die vordefinierten [CFrameWnd-Standardattribute.](../../mfc/reference/cframewnd-class.md)

*lpszWindowName*<br/>
Zeigt auf eine null-terminierte Zeichenfolge, die den Fensternamen darstellt.

*dwStyle*<br/>
Gibt die Fensterstilattribute an. Standardmäßig werden die WS_VISIBLE- und WS_CHILD Windows-Stile festgelegt.

*Rect*<br/>
Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Größe und Position des Fensters angibt. Mit *dem rectDefault-Wert* kann Windows die Größe und Position des neuen Fensters angeben.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster des Steuerelements.

*nID*<br/>
Die ID-Nummer der Ansicht. Legen Sie standardmäßig AFX_IDW_PANE_FIRST fest.

*pContext*<br/>
Ein Zeiger auf einen [CCreateContext](../../mfc/reference/ccreatecontext-structure.md). NULL standardmäßig.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft auch die enthaltene WebBrowser-Methode zum Laden eines Standarddokuments `Navigate` auf (siehe [CHtmlEditView::GetStartDocument](#getstartdocument)).

## <a name="chtmleditviewgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditView::GetDHtmlDocument

Gibt `IHTMLDocument2` die Schnittstelle für das aktuelle Dokument zurück.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parameter

*ppDocument*<br/>
Die [IHTMLDocument2-Schnittstelle.](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))

## <a name="chtmleditviewgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditView::GetStartDocument

Ruft den Namen des Standarddokuments für diese Ansicht ab.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Weitere Informationen

[HTMLEdit-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
