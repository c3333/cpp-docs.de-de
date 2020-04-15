---
title: CReBar-Klasse
ms.date: 11/19/2018
f1_keywords:
- CReBar
- AFXEXT/CReBar
- AFXEXT/CReBar::AddBar
- AFXEXT/CReBar::Create
- AFXEXT/CReBar::GetReBarCtrl
helpviewer_keywords:
- CReBar [MFC], AddBar
- CReBar [MFC], Create
- CReBar [MFC], GetReBarCtrl
ms.assetid: c1ad2720-1d33-4106-8e4e-80aa84f93559
ms.openlocfilehash: c1379d1ef8effea0df564da1b43769bb9a11435d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363932"
---
# <a name="crebar-class"></a>CReBar-Klasse

Eine Steuerleiste, die Layout-, Persistenz- und Zustandsinformationen für Grundleisten-Steuerelemente bereitstellt.

## <a name="syntax"></a>Syntax

```
class CReBar : public CControlBar
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CReBar::AddBar](#addbar)|Fügt einer Bewehrung ein Band hinzu.|
|[CReBar::Erstellen](#create)|Erstellt das Bewehrungssteuerelement und `CReBar` fügt es an das Objekt an.|
|[CReBar::GetReBarCtrl](#getrebarctrl)|Ermöglicht den direkten Zugriff auf das zugrunde liegende gemeinsame Steuerelement.|

## <a name="remarks"></a>Bemerkungen

Ein Bewehrungsobjekt kann eine Vielzahl von untergeordneten Fenstern enthalten, in der Regel andere Steuerelemente, einschließlich Bearbeitungsfelder, Symbolleisten und Listenfelder. Ein Bewehrungsobjekt kann seine untergeordneten Fenster über einer angegebenen Bitmap anzeigen. Ihre Anwendung kann die Größe der Bewehrung automatisch ändern, oder der Benutzer kann die Größe der Bewehrung manuell ändern, indem er auf die Greiferleiste klickt oder sie zieht.

![Beispiel eines Grundleistenmenüs](../../mfc/reference/media/vc4sc61.gif "Beispiel eines Grundleistenmenüs")

## <a name="rebar-control"></a>Bewehrungssteuerung

Ein Bewehrungsobjekt verhält sich ähnlich wie ein Symbolleistenobjekt. Eine Bewehrung verwendet den Click-and-Drag-Mechanismus, um die Größe ihrer Bänder zu ändern. Ein Bewehrungssteuerelement kann ein oder mehrere Bänder enthalten, wobei jedes Band eine beliebige Kombination aus einer Greiferleiste, einer Bitmap, einer Textbeschriftung und einem untergeordneten Fenster enthält. Bänder dürfen jedoch nicht mehr als ein untergeordnetes Fenster enthalten.

`CReBar`verwendet die [CReBarCtrl-Klasse,](../../mfc/reference/crebarctrl-class.md) um seine Implementierung bereitzustellen. Sie können über [GetReBarCtrl](#getrebarctrl) auf das Bewehrungssteuerelement zugreifen, um die Anpassungsoptionen des Steuerelements zu nutzen. Weitere Informationen zu Bewehrungssteuerelementen finden Sie unter `CReBarCtrl`. Weitere Informationen zur Verwendung von Bewehrungssteuerelementen finden Sie unter [Verwenden von CReBarCtrl](../../mfc/using-crebarctrl.md).

> [!CAUTION]
> Bewehrungs- und Bewehrungssteuerungsobjekte unterstützen das MFC-Steuerleistenandocken nicht. Wenn `CRebar::EnableDocking` aufgerufen wird, wird Ihre Anwendung bestätigen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CReBar`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="crebaraddbar"></a><a name="addbar"></a>CReBar::AddBar

Rufen Sie diese Memberfunktion auf, um der Bewehrung ein Band hinzuzufügen.

```
BOOL AddBar(
    CWnd* pBar,
    LPCTSTR pszText = NULL,
    CBitmap* pbmp = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS | RBBS_FIXEDBMP);

BOOL AddBar(
    CWnd* pBar,
    COLORREF clrFore,
    COLORREF clrBack,
    LPCTSTR pszText = NULL,
    DWORD dwStyle = RBBS_GRIPPERALWAYS);
```

### <a name="parameters"></a>Parameter

*Pbar*<br/>
Ein Zeiger auf `CWnd` ein Objekt, das das untergeordnete Fenster ist, das in die Bewehrung eingefügt werden soll. Das referenzierte Objekt muss über eine WS_CHILD verfügen.

*lpszText*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Text enthält, der auf der Bewehrung angezeigt werden soll. NULL standardmäßig. Der in *lpszText* enthaltene Text ist nicht Teil des untergeordneten Fensters. es ist auf der Bewehrung selbst.

*pbmp*<br/>
Ein Zeiger auf `CBitmap` ein Objekt, das auf dem Bewehrungshintergrund angezeigt werden soll. NULL standardmäßig.

*dwStyle*<br/>
Ein DWORD, das den Stil enthält, der auf die Bewehrung angewendet werden soll. Eine `fStyle` vollständige Liste der Bandstile finden Sie in der Funktionsbeschreibung in der Win32-Struktur [REBARBANDINFO.](/windows/win32/api/commctrl/ns-commctrl-rebarbandinfow)

*clrFore*<br/>
Ein COLORREF-Wert, der die Vordergrundfarbe der Bewehrung darstellt.

*clrBack*<br/>
Ein COLORREF-Wert, der die Hintergrundfarbe der Bewehrung darstellt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#1](../../mfc/reference/codesnippet/cpp/crebar-class_1.cpp)]

## <a name="crebarcreate"></a><a name="create"></a>CReBar::Erstellen

Rufen Sie diese Memberfunktion auf, um eine Bewehrung zu erstellen.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = RBS_BANDBORDERS,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_CLIPSIBLINGS | WS_CLIPCHILDREN | CBRS_TOP,
    UINT nID = AFX_IDW_REBAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigen Sie `CWnd` auf das Objekt, dessen Windows-Fenster das übergeordnete Element der Statusleiste ist. Normalerweise Ihr Rahmenfenster.

*dwCtrlStyle*<br/>
Der Bewehrungssteuerungsstil. Standardmäßig RBS_BANDBORDERS, die schmale Linien anzeigt, um benachbarte Bänder innerhalb des Bewehrungssteuerelements zu trennen. Eine Liste der Formatvorlagen finden Sie unter [Bewehrungssteuerungsstile](/windows/win32/Controls/rebar-control-styles) im Windows SDK.

*dwStyle*<br/>
Die Bewehrungsfensterstile.

*nID*<br/>
Die untergeordnete Fenster-ID der Bewehrung.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CReBar::AddBar](#addbar).

## <a name="crebargetrebarctrl"></a><a name="getrebarctrl"></a>CReBar::GetReBarCtrl

Diese Memberfunktion ermöglicht den direkten Zugriff auf das zugrunde liegende gemeinsame Steuerelement.

```
CReBarCtrl& GetReBarCtrl() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf ein [CReBarCtrl-Objekt.](../../mfc/reference/crebarctrl-class.md)

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, um die Funktionalität der allgemeinen Windows-Bewehrungssteuerung beim Anpassen der Bewehrung zu nutzen. Wenn Sie `GetReBarCtrl`aufrufen, wird ein `CReBarCtrl` Referenzobjekt an das Objekt zurückgegeben, sodass Sie beide Elementfunktionen verwenden können.

Weitere Informationen `CReBarCtrl` zum Anpassen der Bewehrung finden Sie unter Verwenden von [CReBarCtrl](../../mfc/using-crebarctrl.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CReBarCtrl#2](../../mfc/reference/codesnippet/cpp/crebar-class_2.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel-MFCIE](../../overview/visual-cpp-samples.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
