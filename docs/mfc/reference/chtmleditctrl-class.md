---
title: CHtmlEditCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::CHtmlEditCtrl
- AFXHTML/CHtmlEditCtrl::Create
- AFXHTML/CHtmlEditCtrl::GetDHtmlDocument
- AFXHTML/CHtmlEditCtrl::GetStartDocument
helpviewer_keywords:
- CHtmlEditCtrl [MFC], CHtmlEditCtrl
- CHtmlEditCtrl [MFC], Create
- CHtmlEditCtrl [MFC], GetDHtmlDocument
- CHtmlEditCtrl [MFC], GetStartDocument
ms.assetid: 0fc4a238-b05f-4874-9edc-6a6701f064d9
ms.openlocfilehash: 05063c62e9f7a5d88d3fecde842f979725200f98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366843"
---
# <a name="chtmleditctrl-class"></a>CHtmlEditCtrl-Klasse

Stellt die Funktionalität des WebBrowser-ActiveX-Steuerelements in einem MFC-Fenster bereit.

## <a name="syntax"></a>Syntax

```
class CHtmlEditCtrl: public CWnd,
    public CHtmlEditCtrlBase<CHtmlEditCtrl>
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHtmlEditCtrl::CHtmlEditCtrl](#chtmleditctrl)|Erstellt ein `CHtmlEditCtrl`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CHtmlEditCtrl::Erstellen](#create)|Erstellt ein WebBrowser ActiveX-Steuerelement und `CHtmlEditCtrl` fügt es an das Objekt an. Diese Funktion versetzt das WebBrowser ActiveX-Steuerelement automatisch in den Bearbeitungsmodus.|
|[CHtmlEditCtrl::GetDHtmlDocument](#getdhtmldocument)|Ruft die [IHTMLDocument2-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) für das Dokument ab, das derzeit im enthaltenen WebBrowser-Steuerelement geladen ist.|
|[CHtmlEditCtrl::GetStartDocument](#getstartdocument)|Ruft die URL in ein Standarddokument ab, das in das enthaltene WebBrowser-Steuerelement geladen werden soll.|

## <a name="remarks"></a>Bemerkungen

Das gehostete WebBrowser-Steuerelement wird nach der Erstellung automatisch in den Bearbeitungsmodus versetzt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHtmlEditCtrl`

## <a name="requirements"></a>Anforderungen

**Header:** afxhtml.h

## <a name="chtmleditctrlchtmleditctrl"></a><a name="chtmleditctrl"></a>CHtmlEditCtrl::CHtmlEditCtrl

Erstellt ein `CHtmlEditCtrl`-Objekt.

```
CHtmlEditCtrl();
```

## <a name="chtmleditctrlcreate"></a><a name="create"></a>CHtmlEditCtrl::Erstellen

Erstellt ein WebBrowser ActiveX-Steuerelement und `CHtmlEditCtrl` fügt es an das Objekt an. Das WebBrowser ActiveX-Steuerelement navigiert automatisch zu einem Standarddokument und wird dann von dieser Funktion in den Bearbeitungsmodus versetzt.

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    int nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>Parameter

*lpszWindowName*<br/>
Dieser Parameter wird nicht verwendet.

*dwStyle*<br/>
Dieser Parameter wird nicht verwendet.

*Rect*<br/>
Gibt die Größe und Position des Steuerelements an.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Steuerelements an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die ID des Steuerelements an.

*pContext*<br/>
Dieser Parameter wird nicht verwendet.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg zurück, FALSE bei Fehler.

## <a name="chtmleditctrlgetdhtmldocument"></a><a name="getdhtmldocument"></a>CHtmlEditCtrl::GetDHtmlDocument

Ruft die [IHTMLDocument2-Schnittstelle](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\)) für das Dokument ab, das derzeit im enthaltenen WebBrowser-Steuerelement geladen ist.

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>Parameter

*ppDocument*<br/>
Die Dokumentschnittstelle.

## <a name="chtmleditctrlgetstartdocument"></a><a name="getstartdocument"></a>CHtmlEditCtrl::GetStartDocument

Ruft die URL in ein Standarddokument ab, das in das enthaltene WebBrowser-Steuerelement geladen werden soll.

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
