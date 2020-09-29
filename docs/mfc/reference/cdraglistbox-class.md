---
title: CDragListBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: b260d3a88fc8c3f2d341005c1e47cfd9ab668e1e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500363"
---
# <a name="cdraglistbox-class"></a>CDragListBox-Klasse

Zusätzlich zur Bereitstellung der Funktionalität eines Windows-Listen Felds ermöglicht die- `CDragListBox` Klasse dem Benutzer das Verschieben von Listenfeld Elementen, z. b. Dateinamen, innerhalb des Listen Felds.

## <a name="syntax"></a>Syntax

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CDragListBox:: CDragListBox](#cdraglistbox)|Erstellt ein `CDragListBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CDragListBox:: BeginDrag](#begindrag)|Wird von Framework aufgerufen, wenn ein Zieh Vorgang gestartet wird.|
|[CDragListBox:: CancelDrag](#canceldrag)|Wird von Framework aufgerufen, wenn ein Zieh Vorgang abgebrochen wurde.|
|[CDragListBox::D ragging](#dragging)|Wird von Framework während eines Zieh Vorgangs aufgerufen.|
|[CDragListBox::D rawinsert](#drawinsert)|Zeichnet die einfügeanleitung des Zieh Listen Felds.|
|[CDragListBox::D ropped](#dropped)|Wird von Framework aufgerufen, nachdem das Element gelöscht wurde.|
|[CDragListBox:: itemfrompt](#itemfrompt)|Gibt die Koordinaten des Elements zurück, das gezogen wird.|

## <a name="remarks"></a>Bemerkungen

Listenfelder mit dieser Funktion ermöglichen es Benutzern, die Elemente in einer Liste in einer beliebigen Weise zu sortieren, die für Sie am nützlichsten ist. Standardmäßig wird das Element im Listenfeld an die neue Position in der Liste verschoben. `CDragListBox`Objekte können jedoch angepasst werden, um Elemente zu kopieren, anstatt Sie zu verschieben.

Das Listenfeld-Steuerelement, das der-Klasse zugeordnet ist, `CDragListBox` darf nicht über die LBS_SORT oder den LBS_MULTIPLESELECT Stil verfügen. Eine Beschreibung der Listenfeld Stile finden Sie unter [List-Box-Stile](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Um ein Listenfeld mit Drag & amp; Drop in ein vorhandenes Dialogfeld der Anwendung zu verwenden, fügen Sie der Dialogfeld Vorlage mithilfe des Dialog-Editors ein Listenfeld-Steuerelement hinzu, und weisen Sie dann eine Element Variable (von Kategorie `Control` und Variablentyp) zu, `CDragListBox` die dem Listenfeld-Steuerelement in der

Weitere Informationen zum Zuweisen von Steuerelementen zu Element Variablen finden Sie unter [Verknüpfung zum Definieren von Element Variablen für Dialog](../../windows/adding-editing-or-deleting-controls.md)Feld Steuerelemente.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a> CDragListBox:: BeginDrag

Wird von Framework aufgerufen, wenn ein Ereignis auftritt, das einen Zieh Vorgang, z. b. das Drücken der linken Maustaste, einleiten könnte.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parameter

*pt*<br/>
Ein [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) -Objekt, das die Koordinaten des Elements enthält, das gezogen wird.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das ziehen zulässig ist, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie steuern möchten, was geschieht, wenn ein Zieh Vorgang beginnt. Die Standard Implementierung erfasst die Maus und verbleibt im Zieh Modus, bis der Benutzer mit der linken oder rechten Maustaste klickt oder ESC drückt. zu diesem Zeitpunkt wird der Zieh Vorgang abgebrochen.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a> CDragListBox:: CancelDrag

Wird von Framework aufgerufen, wenn ein Zieh Vorgang abgebrochen wurde.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parameter

*pt*<br/>
Ein [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) -Objekt, das die Koordinaten des Elements enthält, das gezogen wird.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine spezielle Verarbeitung für das Listenfeld-Steuerelement zu verarbeiten.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a> CDragListBox:: CDragListBox

Erstellt ein `CDragListBox`-Objekt.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a> CDragListBox::D ragging

Wird von Framework aufgerufen, wenn ein Listenfeld Element innerhalb des Objekts gezogen wird `CDragListBox` .

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parameter

*pt*<br/>
Ein [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) -Objekt, das die x-und y-Bildschirm Koordinaten des Cursors enthält.

### <a name="return-value"></a>Rückgabewert

Die Ressourcen-ID des Cursors, der angezeigt werden soll. Folgende Werte sind möglich:

- DL_COPYCURSOR gibt an, dass das Element kopiert wird.

- DL_MOVECURSOR gibt an, dass das Element verschoben wird.

- DL_STOPCURSOR gibt an, dass das aktuelle Ablage Ziel nicht zulässig ist.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten gibt DL_MOVECURSOR zurück. Überschreiben Sie diese Funktion, wenn Sie zusätzliche Funktionen bereitstellen möchten.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a> CDragListBox::D rawinsert

Wird von Framework aufgerufen, um die einfügeanleitung vor dem Element mit dem angegeben Index zu zeichnen.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parameter

*nitem*<br/>
NULL basierter Index der Einfügemarke.

### <a name="remarks"></a>Bemerkungen

Mit dem Wert-1 wird die einfügeanleitung gelöscht. Überschreiben Sie diese Funktion, um die Darstellung oder das Verhalten der einfügeanleitung zu ändern.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a> CDragListBox::D ropped

Wird von Framework aufgerufen, wenn ein Element innerhalb eines- `CDragListBox` Objekts gelöscht wird.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parameter

*nsrcindex*<br/>
Gibt den NULL basierten Index der gelöschten Zeichenfolge an.

*pt*<br/>
Ein [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) -Objekt, das die Koordinaten der Ablage Site enthält.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten kopiert das Listenfeld Element und die zugehörigen Daten an den neuen Speicherort und löscht dann das ursprüngliche Element. Überschreiben Sie diese Funktion, um das Standardverhalten anzupassen, z. b. das Aktivieren von Kopien von Listenfeld Elementen, die an andere Positionen in der Liste gezogen werden sollen.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a> CDragListBox:: itemfrompt

Rufen Sie diese Funktion auf, um den NULL basierten Index des Listenfeld Elements abzurufen, das sich unter *PT*befindet.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parameter

*pt*<br/>
Ein [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) -Objekt, das die Koordinaten eines Punkts im Listenfeld enthält.

*bauherum Scroll*<br/>
Ungleich 0 (null), wenn Bildläufe zulässig sind, andernfalls 0.

### <a name="return-value"></a>Rückgabewert

NULL basierter Index des Zieh Listenfeld Elements.

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)
