---
title: CCheckListBox-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
ms.openlocfilehash: 8ca8d3b2cb4ce3c5b070d883e0a418ebec3665b1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352379"
---
# <a name="cchecklistbox-class"></a>CCheckListBox-Klasse

Stellt die Funktionalität eines Windows-Kontrolllistenfelds bereit.

## <a name="syntax"></a>Syntax

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|Erstellt ein `CCheckListBox`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCheckListBox::Erstellen](#create)|Erstellt das Windows-Checklistenfeld und `CCheckListBox` fügt es an das Objekt an.|
|[CCheckListBox::DrawItem](#drawitem)|Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines Listenfelds für die Besitzerzeichnung ändert.|
|[CCheckListBox::Aktivieren](#enable)|Aktiviert oder deaktiviert ein Checklistenfeldelement.|
|[CCheckListBox::GetCheck](#getcheck)|Ruft das Kontrollkästchen des Elements ab.|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|Ruft den Stil der Kontrollkästchen des Steuerelements ab.|
|[CCheckListBox::IsEnabled](#isenabled)|Bestimmt, ob ein Element aktiviert ist.|
|[CCheckListBox::MeasureItem](#measureitem)|Wird vom Framework aufgerufen, wenn ein Listenfeld mit einem Besitzerzeichnungsstil erstellt wird.|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|Wird vom Framework aufgerufen, um die Position des Kontrollkästchens eines Elements abzusehen.|
|[CCheckListBox::SetCheck](#setcheck)|Legt das Kontrollkästchen für den Status eines Elements fest.|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|Legt den Stil der Kontrollkästchen des Steuerelements fest.|

## <a name="remarks"></a>Bemerkungen

Ein "Checklistenfeld" zeigt eine Liste von Elementen an, z. B. Dateinamen. Jedes Element in der Liste verfügt über ein Kontrollkästchen, das der Benutzer aktivieren oder löschen kann.

`CCheckListBox`ist nur für besitzergezeichnete Steuerelemente vorgesehen, da die Liste mehr als Textzeichenfolgen enthält. Im einfachsten Fall enthält ein Checklistenfeld Textzeichenfolgen und Kontrollkästchen, aber Sie benötigen überhaupt keinen Text. Sie können z. B. eine Liste kleiner Bitmaps mit einem Kontrollkästchen neben jedem Element haben.

Um ein eigenes Checklistenfeld zu erstellen, `CCheckListBox`müssen Sie eine eigene Klasse von ableiten. Um eine eigene Klasse abzuleiten, schreiben Sie einen `Create`Konstruktor für die abgeleitete Klasse, und rufen Sie dann auf.

Wenn Sie Windows-Benachrichtigungen verarbeiten möchten, die von einem Listenfeld an das übergeordnete Element gesendet werden (normalerweise eine von [CDialog](../../mfc/reference/cdialog-class.md)abgeleitete Klasse), fügen Sie der übergeordneten Klasse für jede Nachricht einen Nachrichtenzuordnungseintrag und eine Message-Handler-Memberfunktion hinzu.

Jeder Nachrichtenzuordnungseintrag hat die folgende Form:

**\_ON-Benachrichtigung**_Notification_ **(** _id_, _memberFxn_ **)**

wobei `id` die untergeordnete Fenster-ID des Steuerelements `memberFxn` angegeben wird, das die Benachrichtigung sendet, und der Name der übergeordneten Memberfunktion ist, die Sie geschrieben haben, um die Benachrichtigung zu behandeln.

Der Funktionsprototyp des Übergeordneten ist wie folgt:

`afx_msg void memberFxn();`

Es gibt nur einen Message-Map-Eintrag, `CCheckListBox` der sich speziell auf CListBox bezieht (siehe aber auch die Message-Map-Einträge für [CListBox):](../../mfc/reference/clistbox-class.md)

- ON_CLBN_CHKCHANGE Der Benutzer hat das Kontrollkästchen eines Elements geändert.

Wenn es sich bei Ihrem Checklistenfeld um ein Standardprüffeld handelt (eine Liste von Zeichenfolgen mit den Kontrollkästchen in Standardgröße links neben jedem), können Sie das Kontrollkästchen [CCheckListBox::DrawItem](#drawitem) verwenden. Andernfalls müssen Sie die [Funktion CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem) und die Funktionen [CCheckListBox::DrawItem](#drawitem) und [CCheckListBox::MeasureItem](#measureitem) überschreiben.

Sie können ein Checklistenfeld entweder aus einer Dialogfeldvorlage oder direkt im Code erstellen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

Erstellt ein `CCheckListBox`-Objekt.

```
CCheckListBox();
```

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CCheckListBox` ein Objekt in zwei Schritten. Definieren Sie zuerst `CCheckListBox`eine von `Create`abgeleitete Klasse und rufen Sie dann auf, wodurch das Windows-Checklistenfeld initialisiert und an das `CCheckListBox` Objekt angefügt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>CCheckListBox::Erstellen

Erstellt das Windows-Checklistenfeld und `CCheckListBox` fügt es an das Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwStyle*<br/>
Gibt den Stil des Checklistenfelds an. Der Stil muss LBS_HASSTRINGS und entweder LBS_OWNERDRAWFIXED (alle Elemente in der Liste haben die gleiche Höhe) oder LBS_OWNERDRAWVARIABLE (Elemente in der Liste sind unterschiedlich hoch). Dieser Stil kann mit anderen [Listenfeldstilen](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) außer LBS_USETABSTOPS kombiniert werden.

*Rect*<br/>
Gibt die Größe und Position des Checklistenfelds an. Kann entweder ein [CRect-Objekt](../../atl-mfc-shared/reference/crect-class.md) oder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) sein.

*pParentWnd*<br/>
Gibt das übergeordnete Fenster des Prüffelds (in der Regel ein Objekt) `CDialog` an. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Kontrollfeld-ID des Prüffelds an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CCheckListBox` ein Objekt in zwei Schritten. Definieren Sie zunächst eine `CcheckListBox` von `Create`der Klasse abgeleitete Klasse, und rufen Sie `CCheckListBox`dann auf, die das Windows-Checklistenfeld initialisiert und an die anfügt. Siehe [CCheckListBox::CCheckListBox](#cchecklistbox) für ein Beispiel.

Bei `Create` der Ausführung sendet Windows die [Nachrichten WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate) [, WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate), [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)und [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) Nachrichten an das Prüffeldsteuerelement.

Diese Nachrichten werden standardmäßig von den Memberfunktionen [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate), [OnCreate](../../mfc/reference/cwnd-class.md#oncreate), [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)und `CWnd` [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) in der Basisklasse verarbeitet. Um die Standardnachrichtenbehandlung zu erweitern, fügen Sie der abgeleiteten Klasse eine Nachrichtenzuordnung hinzu, und überschreiben Sie die vorherigen Nachrichtenhandlermemberfunktionen. Überschreiben `OnCreate`Sie z. B., um die erforderliche Initialisierung für eine neue Klasse durchzuführen.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein Checklistenfeldsteuerelement an:

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

- WS_VSCROLL So fügen Sie eine vertikale Bildlaufleiste hinzu

- WS_HSCROLL So fügen Sie eine horizontale Bildlaufleiste hinzu

- WS_GROUP Zu Gruppensteuerelementen

- WS_TABSTOP So lassen Sie das Tabing auf dieses Steuerelement zu

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox::DrawItem

Wird vom Framework aufgerufen, wenn sich ein visueller Aspekt eines vom Besitzer gezeichneten Checklistenfelds ändert.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein langer Zeiger auf eine [DRAWITEMSTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-drawitemstruct) die Informationen über den erforderlichen Zeichnungstyp enthält.

### <a name="remarks"></a>Bemerkungen

Die `itemAction` `itemState` und die `DRAWITEMSTRUCT` Elemente der Struktur definieren die Zeichnungsaktion, die ausgeführt werden soll.

Standardmäßig zeichnet diese Funktion eine Standard-Kontrollkästchenliste, die aus einer Liste von Zeichenfolgen besteht, die jeweils ein Kontrollkästchen in Standardgröße auf der linken Seite enthalten. Die Kontrollkästchenliste ist die unter [Erstellen](#create)angegebene .

Überschreiben Sie diese Memberfunktion, um das Zeichnen von Prüflistenfeldern für Besitzerzeichnen zu implementieren, die nicht standardmäßig aufgeführt sind, z. B. Checklistenfelder mit Listen, die keine Zeichenfolgen sind, mit Elementen mit variabler Höhe oder mit Kontrollkästchen, die sich nicht auf der linken Seite befinden. Die Anwendung sollte alle GDI-Objekte (Graphics Device Interface) wiederherstellen, die für den anzeigekontext ausgewählt wurden, der in *lpDrawItemStruct* vor dem Beenden dieser Memberfunktion angegeben wurde.

Wenn Checklistenfeldelemente nicht alle die gleiche Höhe aufweisen, muss der Checklistenfeldstil (in `Create`angegeben) **LBS_OWNERVARIABLE**sein, und Sie müssen die [MeasureItem-Funktion](#measureitem) überschreiben.

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox::Aktivieren

Rufen Sie diese Funktion auf, um ein Checklistenfeldelement zu aktivieren oder zu deaktivieren.

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des zu aktivierenden Checklistenfeldelements.

*bAktiviert*<br/>
Gibt an, ob das Element aktiviert oder deaktiviert ist.

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox::GetCheck

Ruft den Status des angegebenen Kontrollkästchens ab.

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Nullbasierter Index eines Kontrollkästchens, das im Listenfeld enthalten ist.

### <a name="return-value"></a>Rückgabewert

Der Status des angegebenen Kontrollkästchens. In der folgenden Tabelle sind mögliche Werte aufgeführt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|Bst_checked|Das Kontrollkästchen ist aktiviert.|
|BST_UNCHECKED|Das Kontrollkästchen ist nicht aktiviert.|
|BST_INDETERMINATE|Der Kontrollkästchenstatus ist unbestimmt.|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

Rufen Sie diese Funktion auf, um den Stil des Checklistenfelds abzurufen.

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>Rückgabewert

Der Stil der Kontrollkästchen des Steuerelements.

### <a name="remarks"></a>Bemerkungen

Informationen zu möglichen Stilen finden Sie unter [SetCheckStyle](#setcheckstyle).

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox::IsEnabled

Rufen Sie diese Funktion auf, um zu bestimmen, ob ein Element aktiviert ist.

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index des Artikels.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element aktiviert ist; andernfalls 0.

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox::MeasureItem

Wird vom Framework aufgerufen, wenn ein Checklistenfeld mit einem nicht standardmäßigen Stil erstellt wird.

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>Parameter

*lpMeasureItemStruct*<br/>
Ein langer Zeiger auf eine [MEASUREITEMSTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-measureitemstruct)

### <a name="remarks"></a>Bemerkungen

Standardmäßig führt diese Memberfunktion nichts aus. Überschreiben Sie diese Memberfunktion, und füllen Sie die `MEASUREITEMSTRUCT` Struktur aus, um Windows über die Dimensionen von Checklisten-Box-Elementen zu informieren. Wenn das Checklistenfeld mit dem [Stil LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) erstellt wird, ruft das Framework diese Memberfunktion für jedes Element im Listenfeld auf. Andernfalls wird dieses Element nur einmal aufgerufen.

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

Das Framework ruft diese Funktion auf, um die Position und Größe des Kontrollkästchens in einem Element abzubekommen.

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>Parameter

*rectItem*<br/>
Die Position und Größe des Listenelements.

*rectCheckBox*<br/>
Das Kontrollkästchen Standardposition und -größe eines Elements.

### <a name="return-value"></a>Rückgabewert

Die Position und Größe des Kontrollkästchens eines Artikels.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung gibt nur die Standardposition und`rectCheckBox`-größe des Kontrollkästchens ( zurück. Standardmäßig wird ein Kontrollkästchen in der oberen linken Ecke eines Elements ausgerichtet und ist die Standard-Kontrollkästchengröße. Es kann Fälle geben, in denen Sie die Kontrollkästchen auf der rechten Seite oder ein größeres oder kleineres Kontrollkästchen wünschen. In diesen Fällen `OnGetCheckPosition` überschreiben Sie, um die Position und Größe des Kontrollkästchens innerhalb des Elements zu ändern.

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox::SetCheck

Legt den Status des angegebenen Kontrollkästchens fest.

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Nullbasierter Index eines Kontrollkästchens, das im Listenfeld enthalten ist.

*nCheck*<br/>
Der Schaltflächenstatus für das angegebene Kontrollkästchen. Weitere Informationen zu möglichen Werten finden Sie im Abschnitt "Bemerkungen".

### <a name="remarks"></a>Bemerkungen

In der folgenden Tabelle sind mögliche Werte für den Parameter *nCheck* aufgeführt.

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|Bst_checked|Aktivieren Sie das angegebene Kontrollkästchen.|
|BST_UNCHECKED|Deaktivieren Sie das angegebene Kontrollkästchen.|
|BST_INDETERMINATE|Legen Sie den angegebenen Kontrollkästchenstatus auf unbestimmt fest.<br /><br /> Dieser Status ist nur verfügbar, wenn der Kontrollkästchenstil BS_AUTO3STATE oder BS_3STATE ist. Weitere Informationen finden Sie unter [Schaltflächenstile](../../mfc/reference/styles-used-by-mfc.md#button-styles).|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

Rufen Sie diese Funktion auf, um den Stil der Kontrollkästchen im Checklistenfeld festzulegen.

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>Parameter

*nStyle*<br/>
Bestimmt den Stil der Kontrollkästchen im Checklistenfeld.

### <a name="remarks"></a>Bemerkungen

Gültige Stile sind:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

Weitere Informationen zu diesen Stilen finden Sie unter [Schaltflächenstile](../../mfc/reference/styles-used-by-mfc.md#button-styles).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)
