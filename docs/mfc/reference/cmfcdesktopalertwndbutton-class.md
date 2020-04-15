---
title: CMFCDesktopAlertWndButton-Klasse
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
ms.openlocfilehash: 5b18a15f8bfd98396acae0558d121b32bc4127c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367625"
---
# <a name="cmfcdesktopalertwndbutton-class"></a>CMFCDesktopAlertWndButton-Klasse

Ermöglicht das Hinzufügen von Schaltflächen zu einem Dialogfeld für Desktopwarnungen.

## <a name="syntax"></a>Syntax

```
class CMFCDesktopAlertWndButton : public CMFCButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCDesktopAlertWndButton::CMFCDesktopAlertWndButton`|Der Standardkonstruktor.|
|`CMFCDesktopAlertWndButton::~CMFCDesktopAlertWndButton`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCDesktopAlertWndButton::IsCaptionButton](#iscaptionbutton)|Bestimmt, ob die Schaltfläche im Beschriftungsbereich des Warnungsdialogfelds angezeigt wird.|
|[CMFCDesktopAlertWndButton::IsCloseButton](#isclosebutton)|Bestimmt, ob die Schaltfläche das Dialogfeld "Warnung" schließt.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|Name|BESCHREIBUNG|
|`CMFCDesktopAlertWndButton::m_bIsCaptionButton`|Ein boolescher Wert, der angibt, ob die Schaltfläche im Beschriftungsbereich des Warnungsdialogfelds angezeigt wird.|
|`CMFCDesktopAlertWndButton::m_bIsCloseButton`|Ein boolescher Wert, der angibt, ob die Schaltfläche das Warnungsdialogfeld schließt.|

### <a name="remarks"></a>Bemerkungen

Standardmäßig legt der Konstruktor `m_bIsCaptionButton` `m_bIsCloseButton` die und die Datenmember auf FALSE fest. Das `CMFCDesktopAlertDialog` übergeordnete `m_bIsCaptionButton` Objekt wird auf TRUE festgelegt, wenn die Schaltfläche im Beschriftungsbereich des Warnungsdialogfelds positioniert ist. Die `CMFCDesktopAlertDialog` Klasse `CMFCDesktopAlertWndButton` erstellt ein Objekt, das als Schaltfläche dient, `m_bIsCloseButton` die das Warnungsdialogfeld schließt und auf TRUE setzt.

Fügen `CMFCDesktopAlertWndButton` Sie `CMFCDesktopAlertDialog` einem Objekt Objekte wie eine beliebige Schaltfläche hinzu. Weitere Informationen `CMFCDesktopAlertDialog`zu finden Sie unter [CMFCDesktopAlertDialog Class](../../mfc/reference/cmfcdesktopalertdialog-class.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `SetImage` veranschaulicht, `CMFCDesktopAlertWndButton` wie die Methode in der Klasse verwendet wird. Dieser Codeausschnitt ist Teil des [Desktop alert Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_DesktopAlertDemo#4](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_1.h)]
[!code-cpp[NVC_MFC_DesktopAlertDemo#5](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCDesktopAlertWndButton](../../mfc/reference/cmfcdesktopalertwndbutton-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdesktopalertwnd.h

## <a name="cmfcdesktopalertwndbuttoniscaptionbutton"></a><a name="iscaptionbutton"></a>CMFCDesktopAlertWndButton::IsCaptionButton

Bestimmt, ob die Schaltfläche im Beschriftungsbereich des Warnungsdialogfelds angezeigt wird.

```
BOOL IsCaptionButton() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche im Beschriftungsbereich des Warnungsdialogfelds angezeigt wird. andernfalls 0.

## <a name="cmfcdesktopalertwndbuttonisclosebutton"></a><a name="isclosebutton"></a>CMFCDesktopAlertWndButton::IsCloseButton

Bestimmt, ob die Schaltfläche das Dialogfeld "Warnung" schließt.

```
BOOL IsCloseButton() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Schaltfläche das Dialogfeld "Warnung" schließt. andernfalls 0.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertDialog-Klasse](../../mfc/reference/cmfcdesktopalertdialog-class.md)
