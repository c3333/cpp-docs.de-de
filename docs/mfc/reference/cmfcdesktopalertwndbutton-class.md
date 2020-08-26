---
title: Cmfcdesktopalertwndbutton-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCaptionButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWndButton::IsCloseButton
helpviewer_keywords:
- CMFCDesktopAlertWndButton [MFC], IsCaptionButton
- CMFCDesktopAlertWndButton [MFC], IsCloseButton
ms.assetid: df39a0c8-0c39-4ab0-8c64-78c5b2c4ecaf
ms.openlocfilehash: 6d296966001dcbc2279a298bdd1d9c21195d61fd
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840778"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>Cmfcdesktopalertwndbutton-Klasse

Ermöglicht das Hinzufügen von Schaltflächen zu einem Desktop Benachrichtigungs Dialogfeld.

## <a name="syntax"></a>Syntax

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Standardkonstruktor|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[Cmfcdesktopalertwndbutton:: iscaptionbutton](#iscaptionbutton)|Bestimmt, ob die Schaltfläche im Beschriftungs Bereich des Dialog Felds Warnung angezeigt wird.|
|[Cmfcdesktopalertwndbutton:: isclosebutton](#isclosebutton)|Bestimmt, ob die Schaltfläche das Warn Dialogfeld schließt.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|-|-|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Ein boolescher Wert, der angibt, ob die Schaltfläche im Beschriftungs Bereich des Dialog Felds Warnung angezeigt wird.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Ein boolescher Wert, der angibt, ob die Schaltfläche das Warn Dialogfeld schließt.|

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt der-Konstruktor die `m_bIsCaptionButton` `m_bIsCloseButton` Datenmember und auf false fest. Das `CMFCDesktopAlertDialog` übergeordnete Objekt `m_bIsCaptionButton` wird auf true festgelegt, wenn die Schaltfläche im Beschriftungs Bereich des Dialog Felds Warnung positioniert ist. Die `CMFCDesktopAlertDialog` -Klasse erstellt ein `CMFCDesktopAlertWndButton` -Objekt, das als Schaltfläche dient, mit der das Dialogfeld Warnung geschlossen und auf true festgelegt wird `m_bIsCloseButton` .

Fügen `CMFCDesktopAlertWndButton` Sie Objekte einem-Objekt hinzu, `CMFCDesktopAlertDialog` wie Sie eine beliebige Schaltfläche hinzufügen würden. Weitere Informationen zu `CMFCDesktopAlertDialog` finden Sie unter [cmfcdesktopalertdialog-Klasse](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie die- `SetImage` Methode in der-Klasse verwendet wird `CMFCDesktopAlertWndButton` . Dieser Code Ausschnitt ist Teil des Beispiels für eine [Desktop Benachrichtigungs Demo](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[Cmfcdesktopalertwndbutton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdesktopalertwnd. h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a> Cmfcdesktopalertwndbutton:: iscaptionbutton

Bestimmt, ob die Schaltfläche im Beschriftungs Bereich des Dialog Felds Warnung angezeigt wird.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Schaltfläche im Beschriftungs Bereich des Dialog Felds Warnung angezeigt wird; andernfalls 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a> Cmfcdesktopalertwndbutton:: isclosebutton

Bestimmt, ob die Schaltfläche das Warn Dialogfeld schließt.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich NULL, wenn die Schaltfläche das Benachrichtigungs Dialogfeld schließt. andernfalls 0.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Cmfcdesktopalertdialog-Klasse](../../mfc/reference/cmfcdesktopalertdialog-class.md)
