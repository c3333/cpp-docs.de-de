---
title: CMFCMenuButton-Klasse
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: 2f8ef341d7f460ed6b0ec23cb8a490842eb67cbc
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743268"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton-Klasse

Eine Schaltfläche, die ein Popupmenü anzeigt und die vom Benutzer gewählte Menüoption meldet.

## <a name="syntax"></a>Syntax

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[Cmfcmenubutton:: cmfcmenubutton](#cmfcmenubutton)|Erstellt ein `CMFCMenuButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Wird von Framework aufgerufen, um Fenster Meldungen zu übersetzen, bevor Sie gesendet werden. (Überschreibt `CMFCButton::PreTranslateMessage`.)|
|[Cmfcmenubutton:: sizeto Content](#sizetocontent)|Ändert die Größe der Schaltfläche entsprechend der Text-und Bildgröße.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[Cmfcmenubutton:: m_bOSMenu](#m_bosmenu)|Gibt an, ob das Standard-Popup Menü des Systems oder [ccontextmenumanager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)angezeigt werden soll.|
|[Cmfcmenubutton:: m_bRightArrow](#m_brightarrow)|Gibt an, ob das Popup Menü unterhalb oder rechts von der Schaltfläche angezeigt wird.|
|[Cmfcmenubutton:: m_bStayPressed](#m_bstaypressed)|Gibt an, ob die Menü Schaltfläche ihren Zustand ändert, nachdem der Benutzer die Schaltfläche losgelassen hat.|
|[Cmfcmenubutton:: m_hMenu](#m_hmenu)|Ein Handle für das angefügte Windows-Menü.|
|[Cmfcmenubutton:: m_nMenuResult](#m_nmenuresult)|Ein Bezeichner, der angibt, welches Element der Benutzer aus dem Popupmenü ausgewählt hat.|
|[Cmfcmenubutton:: m_bDefaultClick](#m_bdefaultclick)| Standard Verarbeitung (bei Schaltflächen Text/Bild) zulassen.|

## <a name="remarks"></a>Bemerkungen

Die `CMFCMenuButton` Klasse wird von der [cmfcbutton-Klasse](../../mfc/reference/cmfcbutton-class.md) abgeleitet, die wiederum von der [CButton-Klasse](../../mfc/reference/cbutton-class.md)abgeleitet ist. Daher können Sie `CMFCMenuButton` in Ihrem Code wie gewohnt verwenden `CButton` .

Wenn Sie ein erstellen `CMFCMenuButton` , müssen Sie ein Handle an das zugehörige Popup Menü übergeben. Anschließend wird die-Funktion aufgerufen `CMFCMenuButton::SizeToContent` . `CMFCMenuButton::SizeToContent` prüft, ob die Schaltflächen Größe ausreichend ist, um einen Pfeil einzuschließen, der auf den Speicherort zeigt, an dem das Popup Fenster angezeigt wird, nämlich unterhalb oder rechts neben der Schaltfläche.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie das Handle des Menüs festgelegt wird, das an die Schaltfläche angefügt ist, die Größe der Schaltfläche entsprechend der Text-und Bildgröße angepasst und das Popup Menü festgelegt wird, das vom Framework angezeigt wird. Dieser Code Ausschnitt ist Teil des Beispiels " [neue Steuerelemente](../../overview/visual-cpp-samples.md)".

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxmenubutton. h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a> Cmfcmenubutton:: cmfcmenubutton

Erstellt ein neues [cmfcmenubutton](../../mfc/reference/cmfcmenubutton-class.md) -Objekt.

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a> Cmfcmenubutton:: m_bOSMenu

Eine boolesche Member-Variable, die angibt, welches Popup Menü im Framework angezeigt wird.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Bemerkungen

Wenn `m_bOSMenu` den Wert true hat, ruft das Framework die geerbte `TrackPopupMenu` Methode für dieses Objekt auf. Andernfalls ruft das Framework [ccontextmenumanager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)auf.

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a> Cmfcmenubutton:: m_bRightArrow

Eine boolesche Element Variable, die den Speicherort des Popup Menüs angibt.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer die Menü Schaltfläche drückt, zeigt die Anwendung ein Popup Menü an. Das Framework zeigt das Popup Menü entweder unter der Schaltfläche oder rechts neben der Schaltfläche an. Die Schaltfläche verfügt auch über einen kleinen Pfeil, der angibt, wo das Popup Menü angezeigt wird. Wenn `m_bRightArrow` true ist, zeigt das Framework das Popup Menü rechts neben der Schaltfläche an. Andernfalls wird das Popup Menü unter der Schaltfläche angezeigt.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a> Cmfcmenubutton:: m_bStayPressed

Eine boolesche Element Variable, die angibt, ob die Menü Schaltfläche gedrückt erscheint, während der Benutzer eine Auswahl aus dem Popupmenü trifft.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Bemerkungen

Wenn der `m_bStayPressed` Member false ist, wird die Menü Schaltfläche nicht gedrückt, wenn die Verwendung auf die Schaltfläche klickt. In diesem Fall zeigt das Framework nur das Popup Menü an.

Wenn der `m_bStayPressed` Member true ist, wird die Menü Schaltfläche gedrückt, wenn der Benutzer auf die Schaltfläche klickt. Es bleibt so lange gedrückt, bis der Benutzer das Popup Menü schließt, indem er entweder eine Auswahl oder einen Abbruch vornimmt.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a> Cmfcmenubutton:: m_hMenu

Das Handle für das angefügte Menü.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Bemerkungen

Das Framework zeigt das Menü an, das durch diese Element Variable angegeben wird, wenn der Benutzer auf die Menü Schaltfläche klickt

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a> Cmfcmenubutton:: m_nMenuResult

Eine ganze Zahl, die angibt, welches Element der Benutzer aus dem Popupmenü auswählt.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Bemerkungen

Der Wert dieser Element Variablen ist 0 (null), wenn der Benutzer das Menü abbricht, ohne eine Auswahl vorzunehmen, oder wenn ein Fehler auftritt.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a> Cmfcmenubutton:: m_bDefaultClick

Ermöglicht die Standard Verarbeitung von Text oder Bildern auf der Schaltfläche.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie m_bDefaultClick auf false festlegen, wird die Schaltfläche angezeigt, wenn Sie auf eine beliebige Stelle auf der Schaltfläche klicken.

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a> Cmfcmenubutton::P retranslatemess Age

Wird von Framework aufgerufen, um Fenster Meldungen zu übersetzen, bevor Sie gesendet werden.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pmsg*<br/>
in Verweist auf eine [msg](/windows/win32/api/winuser/ns-winuser-msg) -Struktur, die die zu verarbeitende Meldung enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Nachricht übersetzt wurde und nicht gesendet werden sollte. 0, wenn die Meldung nicht übersetzt wurde und gesendet werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a> Cmfcmenubutton:: sizeto Content

Ändert die Größe der Schaltfläche entsprechend der Textgröße und Bildgröße.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parameter

*bcally*<br/>
in Ein boolescher Parameter, der angibt, ob diese Methode die Größe der Schaltfläche ändert.

### <a name="return-value"></a>Rückgabewert

Ein [CSize](../../atl-mfc-shared/reference/csize-class.md) -Objekt, das die neue Größe für die Schaltfläche angibt.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion aufzurufen und *bcalenly* true ist, `SizeToContent` berechnet nur die neue Größe der Schaltfläche.

Die neue Größe der Schaltfläche wird für den Schaltflächen Text, das Bild und den Pfeil angepasst. Das Framework fügt auch vordefinierte Ränder von 10 Pixeln für den horizontalen Rand und 5 Pixel für den vertikalen Rand hinzu.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcbutton-Klasse](../../mfc/reference/cmfcbutton-class.md)
