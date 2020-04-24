---
title: CDialogEx-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDialogEx
- AFXDIALOGEX/CDialogEx
- AFXDIALOGEX/CDialogEx::CDialogEx
- AFXDIALOGEX/CDialogEx::SetBackgroundColor
- AFXDIALOGEX/CDialogEx::SetBackgroundImage
helpviewer_keywords:
- CDialogEx [MFC], CDialogEx
- CDialogEx [MFC], SetBackgroundColor
- CDialogEx [MFC], SetBackgroundImage
ms.assetid: a6ed3b1f-aef8-4b66-ac78-2160faf63c13
ms.openlocfilehash: 717e560035d42957c16168097577d0c8c589e3c7
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753346"
---
# <a name="cdialogex-class"></a>CDialogEx-Klasse

Die `CDialogEx`-Klasse gibt die Hintergrundfarbe und das Hintergrundbild eines Dialogfelds an.

## <a name="syntax"></a>Syntax

```
class CDialogEx : public CDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialogEx::CDialogEx](#cdialogex)|Erstellt ein `CDialogEx`-Objekt.|
|`CDialogEx::~CDialogEx`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialogEx::SetBackgroundColor](#setbackgroundcolor)|Legt die Hintergrundfarbe des Dialogfelds fest.|
|[CDialogEx::SetBackgroundImage](#setbackgroundimage)|Legt das Hintergrundbild des Dialogfelds fest.|

## <a name="remarks"></a>Bemerkungen

Zum Verwenden der `CDialogEx`-Klasse müssen Sie Ihre Dialogfeldklasse von der `CDialogEx`-Klasse statt der `CDialog`-Klasse ableiten.

Dialogfeldbilder werden in einer Ressourcendatei gespeichert. Das Framework löscht automatisch jedes Bild, das aus der Ressourcendatei geladen wird. Um das aktuelle Hintergrundbild programmgesteuert zu löschen, rufen Sie die [CDialogEx::SetBackgroundImage-Methode](#setbackgroundimage) auf, oder implementieren Sie einen `OnDestroy` Ereignishandler. Wenn Sie die [CDialogEx::SetBackgroundImage-Methode](#setbackgroundimage) `HBITMAP` aufrufen, übergeben Sie einen Parameter als Bildhandle. Das `CDialogEx`-Objekt übernimmt den Besitz des Bilds und löscht es, wenn das `m_bAutoDestroyBmp` -Flag `TRUE` ist.

Ein `CDialogEx` Objekt kann ein übergeordnetes Objekt eines [CMFCPopupMenu-Klassenobjekts](../../mfc/reference/cmfcpopupmenu-class.md) sein. Das [CMFCPopupMenu-Klassenobjekt](../../mfc/reference/cmfcpopupmenu-class.md) ruft die `CDialogEx::SetActiveMenu` Methode auf, wenn das [CMFCPopupMenu-Klassenobjekt](../../mfc/reference/cmfcpopupmenu-class.md) geöffnet wird. Anschließend behandelt `CDialogEx` das Objekt jedes Menüereignis, bis das [CMFCPopupMenu-Klassenobjekt](../../mfc/reference/cmfcpopupmenu-class.md) geschlossen wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopf:** afxdialogex.h

## <a name="cdialogexcdialogex"></a><a name="cdialogex"></a>CDialogEx::CDialogEx

Erstellt ein `CDialogEx`-Objekt.

```
CDialogEx(
    UINT nIDTemplate,
    CWnd* pParent=NULL);

CDialogEx(
    LPCTSTR lpszTemplateName,
    CWnd* pParentWnd=NULL);
```

### <a name="parameters"></a>Parameter

*nIDTemplate*<br/>
[in] Die Ressourcen-ID einer Dialogfeldvorlage.

*lpszTemplateName*<br/>
[in] Der Ressourcenname einer Dialogfeldvorlage.

*pParent*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster. Der Standardwert ist NULL.

*pParentWnd*<br/>
[in] Ein Zeiger auf das übergeordnete Fenster. Der Standardwert ist NULL.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cdialogexsetbackgroundcolor"></a><a name="setbackgroundcolor"></a>CDialogEx::SetBackgroundColor

Legt die Hintergrundfarbe des Dialogfelds fest.

```cpp
void SetBackgroundColor(
    COLORREF color,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
[in] Ein RGB-Farbwert.

*bRepaint*<br/>
[in] TRUE, um den Bildschirm sofort zu aktualisieren; andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

## <a name="cdialogexsetbackgroundimage"></a><a name="setbackgroundimage"></a>CDialogEx::SetBackgroundImage

Legt das Hintergrundbild des Dialogfelds fest.

```cpp
void SetBackgroundImage(
    HBITMAP hBitmap,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bAutoDestroy=TRUE,
    BOOL bRepaint=TRUE);

BOOL SetBackgroundImage(
    UINT uiBmpResId,
    BackgroundLocation location=BACKGR_TILE,
    BOOL bRepaint=TRUE);
```

### <a name="parameters"></a>Parameter

*hBitmap*<br/>
[in] Ein Handle für das Hintergrundbild.

*uiBmpResId*<br/>
[in] Die Ressourcen-ID des Hintergrundbilds.

*location*<br/>
[in] Einer der `CDialogEx::BackgroundLocation` Werte, die die Position des Bildes angeben. Gültige Werte umfassen BACKGR_TILE, BACKGR_TOPLEFT, BACKGR_TOPRIGHT, BACKGR_BOTTOMLEFT und BACKGR_BOTTOMRIGHT. Der Standardwert ist BACKGR_TILE.

*bAutoDestroy*<br/>
[in] TRUE, um das Hintergrundbild automatisch zu zerstören; andernfalls FALSE.

*bRepaint*<br/>
[in] TRUE, um das Dialogfeld sofort neu zu zeichnen; andernfalls FALSE.

### <a name="return-value"></a>Rückgabewert

In der zweiten Methodenüberladungssyntax TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das von Ihnen angegebene Bild wird nicht an den Dialogfeldclientbereich geglast.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPopupMenu-Klasse](../../mfc/reference/cmfcpopupmenu-class.md)<br/>
[CContextMenuManager-Klasse](../../mfc/reference/ccontextmenumanager-class.md)
