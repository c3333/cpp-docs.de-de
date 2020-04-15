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
ms.openlocfilehash: 929fc1c8166f249fe3babc724b2c0bcd9cb99676
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369682"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton-Klasse

Eine Schaltfläche, die ein Popupmenü anzeigt und die vom Benutzer gewählte Menüoption meldet.

## <a name="syntax"></a>Syntax

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCMenuButton::CMFCMenuButton](#cmfcmenubutton)|Erstellt ein `CMFCMenuButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCMenuButton::PreTranslateMessage](#pretranslatemessage)|Wird vom Framework aufgerufen, um Fensternachrichten zu übersetzen, bevor sie ausgelöst werden. (Überschreibt `CMFCButton::PreTranslateMessage`.)|
|[CMFCMenuButton::SizeToContent](#sizetocontent)|Ändert die Größe der Schaltfläche entsprechend ihrer Text- und Bildgröße.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCMenuButton::m_bOSMenu](#m_bosmenu)|Gibt an, ob das Standard-System-Popupmenü angezeigt oder [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)verwendet werden soll.|
|[CMFCMenuButton::m_bRightArrow](#m_brightarrow)|Gibt an, ob das Popupmenü unter oder rechts neben der Schaltfläche angezeigt wird.|
|[CMFCMenuButton::m_bStayPressed](#m_bstaypressed)|Gibt an, ob die Menüschaltfläche ihren Status ändert, nachdem der Benutzer die Schaltfläche freigegeben hat.|
|[CMFCMenuButton::m_hMenu](#m_hmenu)|Ein Handle für das angefügte Windows-Menü.|
|[CMFCMenuButton::m_nMenuResult](#m_nmenuresult)|Ein Bezeichner, der angibt, welches Element der Benutzer im Popupmenü ausgewählt hat.|
|[CMFCMenuButton::m_bDefaultClick](#m_bdefaultclick)| Erlauben Sie die Standardverarbeitung (auf Schaltflächentext/Bild).|

## <a name="remarks"></a>Bemerkungen

Die `CMFCMenuButton` Klasse wird von der [CMFCButton-Klasse](../../mfc/reference/cmfcbutton-class.md) abgeleitet, die wiederum von der [CButton-Klasse](../../mfc/reference/cbutton-class.md)abgeleitet wird. Daher können Sie `CMFCMenuButton` in Ihrem Code auf `CButton`die gleiche Weise verwenden, wie Sie .

Wenn Sie `CMFCMenuButton`eine erstellen, müssen Sie ein Handle an das zugeordnete Popupmenü übergeben. Rufen Sie als `CMFCMenuButton::SizeToContent`Nächstes die Funktion auf. `CMFCMenuButton::SizeToContent`überprüft, ob die Schaltflächengröße ausreicht, um einen Pfeil einzuschließen, der auf die Position zeigt, an der das Popupfenster angezeigt wird - nämlich unter oder rechts neben der Schaltfläche.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie das Handle des an die Schaltfläche angehängten Menüs festlegen, die Größe der Schaltfläche entsprechend ihrer Text- und Bildgröße ändern und das Popupmenü festlegen, das vom Framework angezeigt wird. Dieser Codeausschnitt ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxmenubutton.h

## <a name="cmfcmenubuttoncmfcmenubutton"></a><a name="cmfcmenubutton"></a>CMFCMenuButton::CMFCMenuButton

Erstellt ein neues [CMFCMenuButton-Objekt.](../../mfc/reference/cmfcmenubutton-class.md)

```
CMFCMenuButton();
```

## <a name="cmfcmenubuttonm_bosmenu"></a><a name="m_bosmenu"></a>CMFCMenuButton::m_bOSMenu

Eine boolesche Membervariable, die angibt, welches Popupmenü das Framework anzeigt.

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Bemerkungen

Wenn `m_bOSMenu` TRUE ist, ruft das `TrackPopupMenu` Framework die geerbte Methode für dieses Objekt auf. Andernfalls ruft das Framework [CContextMenuManager::TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)auf.

## <a name="cmfcmenubuttonm_brightarrow"></a><a name="m_brightarrow"></a>CMFCMenuButton::m_bRightArrow

Eine boolesche Membervariable, die die Position des Popupmenüs angibt.

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer die Menütaste drückt, zeigt die Anwendung ein Popup-Menü an. Das Framework zeigt das Popup-Menü entweder unter der Schaltfläche oder rechts neben der Schaltfläche an. Die Schaltfläche hat auch einen kleinen Pfeil, der angibt, wo das Popup-Menü angezeigt wird. Wenn `m_bRightArrow` TRUE ist, zeigt das Framework das Popup-Menü rechts neben der Schaltfläche an. Andernfalls wird das Popup-Menü unter der Schaltfläche angezeigt.

## <a name="cmfcmenubuttonm_bstaypressed"></a><a name="m_bstaypressed"></a>CMFCMenuButton::m_bStayPressed

Eine boolesche Elementvariable, die angibt, ob die Menüschaltfläche gedrückt angezeigt wird, während der Benutzer eine Auswahl aus dem Popupmenü trifft.

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Bemerkungen

Wenn `m_bStayPressed` das Element FALSE ist, wird die Menüschaltfläche nicht gedrückt, wenn die Verwendung auf die Schaltfläche klickt. In diesem Fall zeigt das Framework nur das Popupmenü an.

Wenn `m_bStayPressed` das Element TRUE ist, wird die Menüschaltfläche gedrückt, wenn der Benutzer auf die Schaltfläche klickt. Es bleibt gedrückt, bis der Benutzer das Popup-Menü schließt, entweder durch Eine Auswahl oder abbrechen.

## <a name="cmfcmenubuttonm_hmenu"></a><a name="m_hmenu"></a>CMFCMenuButton::m_hMenu

Das Handle zum angehängten Menü.

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Bemerkungen

Das Framework zeigt das Menü an, das von dieser Mitgliedsvariablen angezeigt wird, wenn der Benutzer auf die Menüschaltfläche klickt.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Eine ganze Zahl, die angibt, welches Element der Benutzer aus dem Popupmenü auswählt.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Bemerkungen

Der Wert dieser Membervariablen ist Null, wenn der Benutzer das Menü abbricht, ohne eine Auswahl zu treffen, oder wenn ein Fehler auftritt.

## <a name="cmfcmenubuttonm_bdefaultclick"></a><a name="m_bdefaultclick"></a>CMFCMenuButton::m_bDefaultClick

Ermöglicht die Standardverarbeitung von Text oder Bildern auf der Schaltfläche.

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie m_bDefaultClick auf false setzen, wird die Schaltfläche das Menü angezeigt, wenn Sie auf eine beliebige Schaltfläche klicken.

## <a name="cmfcmenubuttonm_nmenuresult"></a><a name="m_nmenuresult"></a>CMFCMenuButton::m_nMenuResult

Eine ganze Zahl, die angibt, welches Element der Benutzer aus dem Popupmenü auswählt.

```
int m_nMenuResult;
```

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubuttonpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCMenuButton::PreTranslateMessage

Wird vom Framework aufgerufen, um Fensternachrichten zu übersetzen, bevor sie ausgelöst werden.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

*pMsg*<br/>
[in] Verweist auf eine [MSG-Struktur,](/windows/win32/api/winuser/ns-winuser-msg) die die zu verarbeitende Nachricht enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht übersetzt wurde und nicht gesendet werden sollte; 0, wenn die Nachricht nicht übersetzt wurde und versendet werden sollte.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcmenubuttonsizetocontent"></a><a name="sizetocontent"></a>CMFCMenuButton::SizeToContent

Ändert die Größe der Schaltfläche entsprechend ihrer Textgröße und Bildgröße.

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>Parameter

*bCalcOnly*<br/>
[in] Ein boolescher Parameter, der angibt, ob diese Methode die Größe der Schaltfläche ändert.

### <a name="return-value"></a>Rückgabewert

Ein [CSize-Objekt,](../../atl-mfc-shared/reference/csize-class.md) das die neue Größe für die Schaltfläche angibt.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion aufrufen und `SizeToContent` *bCalcOnly* TRUE ist, wird nur die neue Größe der Schaltfläche berechnet.

Die neue Größe der Schaltfläche wird berechnet, um den Schaltflächentext, das Bild und den Pfeil anzupassen. Das Framework fügt außerdem vordefinierte Ränder von 10 Pixeln für die horizontale Kante und 5 Pixel für die vertikale Kante hinzu.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton-Klasse](../../mfc/reference/cmfcbutton-class.md)
