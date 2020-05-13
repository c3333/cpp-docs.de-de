---
title: CMFCLinkCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl
- AFXLINKCTRL/CMFCLinkCtrl::SetURL
- AFXLINKCTRL/CMFCLinkCtrl::SetURLPrefix
- AFXLINKCTRL/CMFCLinkCtrl::SizeToContent
- AFXLINKCTRL/CMFCLinkCtrl::OnDrawFocusRect
helpviewer_keywords:
- CMFCLinkCtrl [MFC], SetURL
- CMFCLinkCtrl [MFC], SetURLPrefix
- CMFCLinkCtrl [MFC], SizeToContent
- CMFCLinkCtrl [MFC], OnDrawFocusRect
ms.assetid: 80f3874d-7cc8-410e-9ff1-62a225f5034b
ms.openlocfilehash: 79edff8be6e2c37baa938fc5b624253932609e17
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754250"
---
# <a name="cmfclinkctrl-class"></a>CMFCLinkCtrl-Klasse

Die `CMFCLinkCtrl` Klasse zeigt eine Schaltfläche als Hyperlink an und ruft das Ziel des Links auf, wenn auf die Schaltfläche geklickt wird.

## <a name="syntax"></a>Syntax

```
class CMFCLinkCtrl : public CMFCButton
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCLinkCtrl::SetURL](#seturl)|Zeigt eine angegebene URL als Schaltflächentext an.|
|[CMFCLinkCtrl::SetURLPrefix](#seturlprefix)|Legt das implizite Protokoll (z. B. "http:") der URL fest.|
|[CMFCLinkCtrl::SizeToContent](#sizetocontent)|Ändert die Größe der Schaltfläche so, dass sie den Schaltflächentext oder die Bitmap enthält.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCLinkCtrl::OnDrawFocusRect](#ondrawfocusrect)|Wird vom Framework aufgerufen, bevor das Fokusrechteck der Schaltfläche gezeichnet wird.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie auf eine Schaltfläche `CMFCLinkCtrl` klicken, die von der Klasse abgeleitet wird, `ShellExecute` übergibt das Framework die URL der Schaltfläche als Parameter an die Methode. Dann `ShellExecute` öffnet die Methode das Ziel der URL.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCLinkCtrl` wie die Größe eines Objekts festgelegt wird `CMFCLinkCtrl` und wie eine URL und eine QuickInfo in einem Objekt festgelegt werden. Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#9](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#10](../../mfc/reference/codesnippet/cpp/cmfclinkctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCLinkCtrl](../../mfc/reference/cmfclinkctrl-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxlinkctrl.h

## <a name="cmfclinkctrlondrawfocusrect"></a><a name="ondrawfocusrect"></a>CMFCLinkCtrl::OnDrawFocusRect

Wird vom Framework aufgerufen, bevor das Fokusrechteck der Schaltfläche gezeichnet wird.

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

*rectClient*<br/>
[in] Ein Rechteck, das das Verknüpfungssteuerelement umgrenzt.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode, wenn Sie Ihren eigenen Code verwenden möchten, um das Fokusrechteck der Schaltfläche zu zeichnen.

## <a name="cmfclinkctrlseturl"></a><a name="seturl"></a>CMFCLinkCtrl::SetURL

Zeigt eine angegebene URL als Schaltflächentext an.

```cpp
void SetURL(LPCTSTR lpszURL);
```

### <a name="parameters"></a>Parameter

*lpszURL*<br/>
[in] Der anzuzeigende Schaltflächentext.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfclinkctrlseturlprefix"></a><a name="seturlprefix"></a>CMFCLinkCtrl::SetURLPrefix

Legt das implizite Protokoll (z. B. "http:") der URL fest.

```cpp
void SetURLPrefix(LPCTSTR lpszPrefix);
```

### <a name="parameters"></a>Parameter

*lpszPrefix*<br/>
[in] Das Präfix des URL-Protokolls.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um das URL-Präfix festzulegen. Das Präfix wird nicht auf dem Gesicht der Schaltfläche angezeigt, aber Sie können es verwenden, um zum Ziel der URL zu navigieren.

## <a name="cmfclinkctrlsizetocontent"></a><a name="sizetocontent"></a>CMFCLinkCtrl::SizeToContent

Ändert die Größe der Schaltfläche so, dass sie den Schaltflächentext oder die Bitmap enthält.

```
virtual CSize SizeToContent(
    BOOL bVCenter=FALSE,
    BOOL bHCenter=FALSE);
```

### <a name="parameters"></a>Parameter

*bVCenter*<br/>
[in] TRUE, um den Schaltflächentext zu zentrieren und vertikal zwischen dem oberen und unteren Rand des Linksteuerelements zu bitmap; andernfalls FALSE. Der Standardwert ist FALSE.

*bHCenter*<br/>
[in] TRUE, um den Schaltflächentext zu zentrieren und horizontal zwischen der linken und rechten Seite des Linksteuerelements zu bitmap; andernfalls FALSE. Der Standardwert ist FALSE.

### <a name="return-value"></a>Rückgabewert

Ein [CSize-Objekt,](../../atl-mfc-shared/reference/csize-class.md) das die neue Größe des Verknüpfungssteuerelements enthält.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CLinkCtrl-Klasse](../../mfc/reference/clinkctrl-class.md)<br/>
[CMFCButton-Klasse](../../mfc/reference/cmfcbutton-class.md)
