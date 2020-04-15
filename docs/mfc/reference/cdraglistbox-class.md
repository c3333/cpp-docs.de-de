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
ms.openlocfilehash: 0d1ae94948e1143a5bac17985423c4bd1bfbaf65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374029"
---
# <a name="cdraglistbox-class"></a>CDragListBox-Klasse

Zusätzlich zur Bereitstellung der Funktionalität eines Windows-Listenfelds ermöglicht die Klasse dem `CDragListBox` Benutzer, Listenfeldelemente, z. B. Dateinamen, innerhalb des Listenfelds zu verschieben.

## <a name="syntax"></a>Syntax

```
class CDragListBox : public CListBox
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|Erstellt ein `CDragListBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|Wird vom Framework aufgerufen, wenn ein Ziehvorgang gestartet wird.|
|[CDragListBox::CancelDrag](#canceldrag)|Wird vom Framework aufgerufen, wenn ein Ziehvorgang abgebrochen wurde.|
|[CDragListBox::D-Schäppeln](#dragging)|Wird vom Framework während eines Ziehvorgangs aufgerufen.|
|[CDragListBox::DrawInsert](#drawinsert)|Zeichnet die Einfügelinie des Ziehlistenfelds.|
|[CDragListBox::Dropped](#dropped)|Wird vom Framework aufgerufen, nachdem das Element gelöscht wurde.|
|[CDragListBox::ItemFrompt](#itemfrompt)|Gibt die Koordinaten des gezogenen Elements zurück.|

## <a name="remarks"></a>Bemerkungen

Listenfelder mit dieser Funktion ermöglichen es Benutzern, die Elemente in einer Liste auf die für sie am nützlichsten emittorischste Weise zu bestellen. Standardmäßig verschiebt das Listenfeld das Element an den neuen Speicherort in der Liste. Objekte `CDragListBox` können jedoch so angepasst werden, dass Sie Elemente kopieren, anstatt sie zu verschieben.

Das Listenfeldsteuerelement, `CDragListBox` das der Klasse zugeordnet ist, darf nicht über die LBS_SORT oder den LBS_MULTIPLESELECT-Stil verfügen. Eine Beschreibung der Listenfeldstile finden Sie unter [List-Box Styles](../../mfc/reference/styles-used-by-mfc.md#list-box-styles).

Um ein Drag-List-Feld in einem vorhandenen Dialogfeld Ihrer Anwendung zu verwenden, fügen Sie der Dialogfeldvorlage `Control` mithilfe `CDragListBox`des Dialogfeld-Editors ein Listenfeldsteuerelement hinzu, und weisen Sie dann eine Mitgliedsvariable (Kategorie und Variablentyp ) zu, die dem Listenfeldsteuerelement in der Dialogfeldvorlage entspricht.

Weitere Informationen zum Zuweisen von Steuerelementen zu Membervariablen finden Sie unter [Shortcut for Defining Member Variables for Dialog Controls](../../windows/defining-member-variables-for-dialog-controls.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>Anforderungen

**Header:** afxcmn.h

## <a name="cdraglistboxbegindrag"></a><a name="begindrag"></a>CDragListBox::BeginDrag

Wird vom Framework aufgerufen, wenn ein Ereignis auftritt, das einen Ziehvorgang starten könnte, z. B. durch Drücken der linken Maustaste.

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein [CPoint-Objekt,](../../atl-mfc-shared/reference/cpoint-class.md) das die Koordinaten des gezogenen Elements enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Ziehen zulässig ist, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, wenn Sie steuern möchten, was geschieht, wenn ein Ziehvorgang beginnt. Die Standardimplementierung erfasst die Maus und bleibt im Ziehmodus, bis der Benutzer auf die linke oder rechte Maustaste klickt oder ESC drückt, zu dem zeitpunkt der Ziehvorgang abgebrochen wird.

## <a name="cdraglistboxcanceldrag"></a><a name="canceldrag"></a>CDragListBox::CancelDrag

Wird vom Framework aufgerufen, wenn ein Ziehvorgang abgebrochen wurde.

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein [CPoint-Objekt,](../../atl-mfc-shared/reference/cpoint-class.md) das die Koordinaten des gezogenen Elements enthält.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um eine spezielle Verarbeitung für ihr Listenfeldsteuerelement zu verarbeiten.

## <a name="cdraglistboxcdraglistbox"></a><a name="cdraglistbox"></a>CDragListBox::CDragListBox

Erstellt ein `CDragListBox`-Objekt.

```
CDragListBox();
```

## <a name="cdraglistboxdragging"></a><a name="dragging"></a>CDragListBox::D-Schäppeln

Wird vom Framework aufgerufen, wenn ein Listenfeldelement innerhalb des `CDragListBox` Objekts gezogen wird.

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein [CPoint-Objekt,](../../atl-mfc-shared/reference/cpoint-class.md) das die x- und y-Bildschirmkoordinaten des Cursors enthält.

### <a name="return-value"></a>Rückgabewert

Die Ressourcen-ID des anzuzeigenden Cursors. Folgende Werte sind möglich:

- DL_COPYCURSOR Gibt an, dass das Element kopiert wird.

- DL_MOVECURSOR Gibt an, dass das Element verschoben wird.

- DL_STOPCURSOR Gibt an, dass das aktuelle Ablageziel nicht akzeptabel ist.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten gibt DL_MOVECURSOR zurück. Überschreiben Sie diese Funktion, wenn Sie zusätzliche Funktionen bereitstellen möchten.

## <a name="cdraglistboxdrawinsert"></a><a name="drawinsert"></a>CDragListBox::DrawInsert

Wird vom Framework aufgerufen, um die Einfügelinie vor dem Element mit dem angegebenen Index zu zeichnen.

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
Nullbasierter Index der Einfügemarke.

### <a name="remarks"></a>Bemerkungen

Der Wert - 1 löscht die Einfügeanleitung. Überschreiben Sie diese Funktion, um das Erscheinungsbild oder Verhalten der Einfügeanleitung zu ändern.

## <a name="cdraglistboxdropped"></a><a name="dropped"></a>CDragListBox::Dropped

Wird vom Framework aufgerufen, wenn `CDragListBox` ein Element innerhalb eines Objekts abgelegt wird.

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>Parameter

*nSrcIndex*<br/>
Gibt den nullbasierten Index der gelöschten Zeichenfolge an.

*Pt*<br/>
Ein [CPoint-Objekt,](../../atl-mfc-shared/reference/cpoint-class.md) das die Koordinaten der Ablagesite enthält.

### <a name="remarks"></a>Bemerkungen

Das Standardverhalten kopiert das Listenfeldelement und seine Daten an den neuen Speicherort und löscht dann das ursprüngliche Element. Überschreiben Sie diese Funktion, um das Standardverhalten anzupassen, z. B. das Aktivieren von Kopien von Listenfeldelementen, die an andere Speicherorte innerhalb der Liste gezogen werden können.

## <a name="cdraglistboxitemfrompt"></a><a name="itemfrompt"></a>CDragListBox::ItemFrompt

Rufen Sie diese Funktion auf, um den nullbasierten Index des Listenfeldelements abzurufen, das sich unter *pt*befindet.

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Ein [CPoint-Objekt,](../../atl-mfc-shared/reference/cpoint-class.md) das die Koordinaten eines Punktes im Listenfeld enthält.

*bAutoScroll*<br/>
Ein Wert ungleich Null, wenn ein Bildlauf zulässig ist, andernfalls 0.

### <a name="return-value"></a>Rückgabewert

Nullbasierter Index des Drag-Listen-Feldelements.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)
