---
title: CMFCSpinButtonCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl
- AFXSPINBUTTONCTRL/CMFCSpinButtonCtrl::OnDraw
helpviewer_keywords:
- CMFCSpinButtonCtrl [MFC], OnDraw
ms.assetid: 8773f259-4d3f-4bca-a71c-09e0c71bc843
ms.openlocfilehash: 445b857400d8c82109ca7220b84bac692a2abf89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376177"
---
# <a name="cmfcspinbuttonctrl-class"></a>CMFCSpinButtonCtrl-Klasse

Die `CMFCSpinButtonCtrl` Klasse unterstützt einen visuellen Manager, der ein Drehtastensteuerelement zeichnet.

## <a name="syntax"></a>Syntax

```
class CMFCSpinButtonCtrl : public CSpinButtonCtrl
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCSpinButtonCtrl::CMFCSpinButtonCtrl`|Der Standardkonstruktor.|
|`CMFCSpinButtonCtrl::~CMFCSpinButtonCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCSpinButtonCtrl::OnDraw](#ondraw)|Malt das aktuelle Drehtastensteuerelement neu.|

## <a name="remarks"></a>Bemerkungen

Um einen visuellen Manager zum Zeichnen eines Drehtastensteuerelements `CSpinButtonCtrl` in der `CMFCSpinButtonCtrl` Anwendung zu verwenden, ersetzen Sie alle Instanzen der Klasse durch die Klasse.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCSpinButtonCtrl` wie Sie `Create` ein Objekt der Klasse erstellen und dessen Methode verwenden.

[!code-cpp[NVC_MFC_RibbonApp#25](../../mfc/reference/codesnippet/cpp/cmfcspinbuttonctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CSpinButtonCtrl](../../mfc/reference/cspinbuttonctrl-class.md)

[CMFCSpinButtonCtrl](../../mfc/reference/cmfcspinbuttonctrl-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxspinbuttonctrl.h

## <a name="cmfcspinbuttonctrlondraw"></a><a name="ondraw"></a>CMFCSpinButtonCtrl::OnDraw

Malt das aktuelle Drehtastensteuerelement neu.

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
[in] Ein Zeiger auf einen Gerätekontext.

### <a name="remarks"></a>Bemerkungen

Das Framework `CMFCSpinButtonCtrl::OnPaint` ruft die Methode auf, die [CWnd::OnPaint-Nachricht](../../mfc/reference/cwnd-class.md#onpaint) zu behandeln, und diese Methode ruft diese `CMFCSpinButtonCtrl::OnDraw` Methode wiederum auf. Überschreiben Sie diese Methode, um die Art und Weise anzupassen, wie das Framework das Drehtastensteuerelement zeichnet.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCVisualManager-Klasse](../../mfc/reference/cmfcvisualmanager-class.md)
