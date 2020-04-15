---
title: COlePropertiesDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::COlePropertiesDialog
- AFXODLGS/COlePropertiesDialog::DoModal
- AFXODLGS/COlePropertiesDialog::OnApplyScale
- AFXODLGS/COlePropertiesDialog::m_gp
- AFXODLGS/COlePropertiesDialog::m_lp
- AFXODLGS/COlePropertiesDialog::m_op
- AFXODLGS/COlePropertiesDialog::m_psh
- AFXODLGS/COlePropertiesDialog::m_vp
helpviewer_keywords:
- COlePropertiesDialog [MFC], COlePropertiesDialog
- COlePropertiesDialog [MFC], DoModal
- COlePropertiesDialog [MFC], OnApplyScale
- COlePropertiesDialog [MFC], m_gp
- COlePropertiesDialog [MFC], m_lp
- COlePropertiesDialog [MFC], m_op
- COlePropertiesDialog [MFC], m_psh
- COlePropertiesDialog [MFC], m_vp
ms.assetid: a54dbc89-1447-4329-bd01-00e98ec9e935
ms.openlocfilehash: f065894ff49af755ab4020f71b0213b19db49054
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374897"
---
# <a name="colepropertiesdialog-class"></a>COlePropertiesDialog-Klasse

Kapselt das allgemeine Windows-OLE-Dialogfeld "Objekteigenschaften".

## <a name="syntax"></a>Syntax

```
class COlePropertiesDialog : public COleDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePropertiesDialog::COlePropertiesDialog](#colepropertiesdialog)|Erstellt ein `COlePropertiesDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePropertiesDialog::DoModal](#domodal)|Zeigt das Dialogfeld an und ermöglicht es dem Benutzer, eine Auswahl zu treffen.|
|[COlePropertiesDialog::OnApplyScale](#onapplyscale)|Wird vom Framework aufgerufen, wenn sich die Skalierung des Dokumentelements geändert hat.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COlePropertiesDialog::m_gp](#m_gp)|Eine Struktur, die zum Initialisieren der `COlePropertiesDialog` Seite "Allgemein" eines Objekts verwendet wird.|
|[COlePropertiesDialog::m_lp](#m_lp)|Eine Struktur, die zum Initialisieren der `COlePropertiesDialog` Seite "Link" eines Objekts verwendet wird.|
|[COlePropertiesDialog::m_op](#m_op)|Eine Struktur, die `COlePropertiesDialog` zum Initialisieren des Objekts verwendet wird.|
|[COlePropertiesDialog::m_psh](#m_psh)|Eine Struktur, die zum Hinzufügen zusätzlicher benutzerdefinierter Eigenschaftenseiten verwendet wird.|
|[COlePropertiesDialog::m_vp](#m_vp)|Eine Struktur, die zum Anpassen der `COlePropertiesDialog` Seite "Ansicht" eines Objekts verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Die allgemeinen Dialogfelder zu den OLE-Objekteigenschaften bieten eine einfache Möglichkeit, die Eigenschaften eines OLE-Dokumentelements in einer Weise anzuzeigen und zu ändern, die mit den Windows-Standards konsistent ist. Zu diesen Eigenschaften gehören unter anderem Informationen über die Datei, die durch das Dokumentelement dargestellt wird, Optionen zum Anzeigen des Symbols und der Bildskalierung sowie Informationen über den Link des Elements (wenn das Element verknüpft ist).

Um ein `COlePropertiesDialog` Objekt zu verwenden, `COlePropertiesDialog` erstellen Sie das Objekt zuerst mit dem Konstruktor. Nachdem das Dialogfeld erstellt wurde, rufen Sie die `DoModal` Memberfunktion auf, um das Dialogfeld anzuzeigen, und ermöglichen Sie dem Benutzer, alle Eigenschaften des Elements zu ändern. `DoModal`gibt an, ob der Benutzer die Schaltfläche OK (IDOK) oder Abbrechen (IDCANCEL) ausgewählt hat. Zusätzlich zu den Schaltflächen OK und Abbrechen gibt es eine Schaltfläche Anwenden. Wenn der Benutzer Übernehmen auswählt, werden alle an den Eigenschaften des Dokumentelements vorgenommenen Änderungen auf das Element angewendet, und sein Bild wird automatisch aktualisiert, bleibt jedoch aktiv.

Der [m_psh](#m_psh) Datenmember ist ein `PROPSHEETHEADER` Zeiger auf eine Struktur, und in den meisten Fällen müssen Sie nicht explizit darauf zugreifen. Eine Ausnahme ist, wenn Sie zusätzliche Eigenschaftenseiten benötigen, die über die Standardseiten "Allgemein", "Ansicht" und "Verknüpfen" hinausgehen. In diesem Fall können `m_psh` Sie das Datenelement so ändern, dass es Ihre benutzerdefinierten Seiten einschließt, bevor Sie die `DoModal` Memberfunktion aufrufen.

Weitere Informationen zu OLE-Dialogfeldern finden Sie im Artikel [Dialogfelder in OLE](../../mfc/dialog-boxes-in-ole.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

[COleDialog](../../mfc/reference/coledialog-class.md)

`COlePropertiesDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxodlgs.h

## <a name="colepropertiesdialogcolepropertiesdialog"></a><a name="colepropertiesdialog"></a>COlePropertiesDialog::COlePropertiesDialog

Erstellt ein `COlePropertiesDialog` -Objekt.

```
COlePropertiesDialog(
    COleClientItem* pItem,
    UINT nScaleMin = 10,
    UINT nScaleMax = 500,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigen Sie auf das Dokumentelement, auf dessen Eigenschaften zugegriffen wird.

*nScaleMin*<br/>
Minimaler Skalierungsprozentsatz für das Dokumentelementbild.

*nScaleMax*<br/>
Maximaler Skalierungsprozentsatz für das Dokumentelementbild.

*pParentWnd*<br/>
Zeigen Sie mit dem Zeiger auf das übergeordnete elementge oder den Besitzer des Dialogfelds.

### <a name="remarks"></a>Bemerkungen

Leiten Sie die allgemeine DIALOGklasse `COlePropertiesDialog` ole Objekteigenschaften ab, um die Skalierung für Ihre Dokumentelemente zu implementieren. Dialogfelder, die von einer Instanz dieser Klasse implementiert werden, unterstützen die Skalierung des Dokumentelements nicht.

Standardmäßig verfügt das allgemeine Dialogfeld OLE-Objekteigenschaften über drei Standardseiten:

- Allgemein

   Diese Seite enthält Systeminformationen für die Datei, die durch das ausgewählte Dokumentelement dargestellt wird. Auf dieser Seite kann der Benutzer das ausgewählte Element in einen anderen Typ konvertieren.

- Sicht

   Diese Seite enthält Optionen zum Anzeigen des Elements, Zum Ändern des Symbols und zum Ändern der Skalierung des Bildes.

- Link

   Diese Seite enthält Optionen zum Ändern des Speicherorts des verknüpften Elements und zum Aktualisieren des verknüpften Elements. Auf dieser Seite kann der Benutzer den Link des ausgewählten Elements unterbrechen.

Um Seiten hinzuzufügen, die über [m_psh](#m_psh) die standardmäßig bereitgestellten seiten hinausgehen, `COlePropertiesDialog`ändern Sie die m_psh Membervariable, bevor Sie den Konstruktor Ihrer -derived-Klasse beenden. Dies ist eine `COlePropertiesDialog` erweiterte Implementierung des Konstruktors.

## <a name="colepropertiesdialogdomodal"></a><a name="domodal"></a>COlePropertiesDialog::DoModal

Rufen Sie diese Memberfunktion auf, um das Dialogfeld allgemeine OLE-Objekteigenschaften von Windows anzuzeigen und dem Benutzer zu ermöglichen, die verschiedenen Eigenschaften des Dokumentelements anzuzeigen und/oder zu ändern.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL, wenn erfolgreich; andernfalls 0. IDOK und IDCANCEL sind Konstanten, die angeben, ob der Benutzer die Schaltfläche OK oder Abbrechen ausgewählt hat.

Wenn IDCANCEL zurückgegeben wird, können Sie die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) aufrufen, um zu ermitteln, ob ein Fehler aufgetreten ist.

## <a name="colepropertiesdialogm_gp"></a><a name="m_gp"></a>COlePropertiesDialog::m_gp

Eine Struktur vom Typ [OLEUIGNRLPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuignrlpropsw), die zum Initialisieren der Seite Allgemein des Dialogfelds OLE-Objekteigenschaften verwendet wird.

```
OLEUIGNRLPROPS m_gp;
```

### <a name="remarks"></a>Bemerkungen

Diese Seite zeigt den Typ und die Größe einer Einbettung und ermöglicht dem Benutzer den Zugriff auf das Dialogfeld Konvertieren. Auf dieser Seite wird auch das Linkziel angezeigt, wenn es sich bei dem Objekt um einen Link handelt.

Weitere Informationen zur `OLEUIGNRLPROPS` Struktur finden Sie im Windows SDK.

## <a name="colepropertiesdialogm_lp"></a><a name="m_lp"></a>COlePropertiesDialog::m_lp

Eine Struktur vom Typ [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw), die zum Initialisieren der Seite Verknüpfen des Dialogfelds OLE-Objekteigenschaften verwendet wird.

```
OLEUILINKPROPS m_lp;
```

### <a name="remarks"></a>Bemerkungen

Diese Seite zeigt den Speicherort des verknüpften Elements an und ermöglicht es dem Benutzer, den Link zum Element zu aktualisieren oder zu unterbrechen.

Weitere Informationen zur `OLEUILINKPROPS` Struktur finden Sie im Windows SDK.

## <a name="colepropertiesdialogm_op"></a><a name="m_op"></a>COlePropertiesDialog::m_op

Eine Struktur vom Typ [OLEUIOBJECTPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiobjectpropsw), die zum Initialisieren des allgemeinen Dialogfelds OLE-Objekteigenschaften verwendet wird.

```
OLEUIOBJECTPROPS m_op;
```

### <a name="remarks"></a>Bemerkungen

Diese Struktur enthält Elemente, die zum Initialisieren der Seiten Allgemein, Verknüpfung und Anzeigen verwendet werden.

Weitere Informationen finden Sie in den Strukturen OLEUIOBJECTPROPS und [OLEUILINKPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuilinkpropsw) im Windows SDK.

## <a name="colepropertiesdialogm_psh"></a><a name="m_psh"></a>COlePropertiesDialog::m_psh

Eine Struktur vom Typ [PROPSHEETHEADER](/windows/win32/api/prsht/ns-prsht-propsheetheadera_v2), deren Member die Eigenschaften des Dialogobjekts speichern.

```
PROPSHEETHEADER m_psh;
```

### <a name="remarks"></a>Bemerkungen

Nach dem `COlePropertiesDialog` Erstellen eines `m_psh` Objekts können Sie verschiedene Aspekte `DoModal` des Dialogfelds festlegen, bevor Sie die Memberfunktion aufrufen.

Wenn Sie `m_psh` das Datenelement direkt ändern, überschreiben Sie jedes Standardverhalten.

Weitere Informationen zur `PROPSHEETHEADER` Struktur finden Sie im Windows SDK.

## <a name="colepropertiesdialogm_vp"></a><a name="m_vp"></a>COlePropertiesDialog::m_vp

Eine Struktur vom Typ [OLEUIVIEWPROPS](/windows/win32/api/oledlg/ns-oledlg-oleuiviewpropsw), die zum Initialisieren der Seite Ansicht des Dialogfelds OLE-Objekteigenschaften verwendet wird.

```
OLEUIVIEWPROPS m_vp;
```

### <a name="remarks"></a>Bemerkungen

Auf dieser Seite kann der Benutzer zwischen "Inhalt"- und "iconic"-Ansichten des Objekts wechseln und seine Skalierung innerhalb des Containers ändern. Es ermöglicht dem Benutzer auch den Zugriff auf das Dialogfeld Symbol ändern, wenn das Objekt als Symbol angezeigt wird.

Weitere Informationen zur `OLEUIVIEWPROPS` Struktur finden Sie im Windows SDK.

## <a name="colepropertiesdialogonapplyscale"></a><a name="onapplyscale"></a>COlePropertiesDialog::OnApplyScale

Wird vom Framework aufgerufen, wenn sich der Skalierungswert geändert hat und entweder OK oder Apply ausgewählt wurde.

```
virtual BOOL OnApplyScale(
    COleClientItem* pItem,
    int nCurrentScale,
    BOOL bRelativeToOrig);
```

### <a name="parameters"></a>Parameter

*pItem*<br/>
Zeigen Sie auf das Dokumentelement, auf dessen Eigenschaften zugegriffen wird.

*nCurrentScale*<br/>
Numerischer Wert der Dialogskala.

*bRelativeToOrig*<br/>
Gibt an, ob die Skalierung auf die ursprüngliche Größe des Dokumentelements zutrifft.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn behandelt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt. Sie müssen diese Funktion überschreiben, um die Skalierungssteuerelemente zu aktivieren.

> [!NOTE]
> Bevor das allgemeine Dialogfeld OLE-Objekteigenschaften angezeigt wird, ruft das Framework diese Funktion mit einem NULL für *pItem* und einem - 1 für *nCurrentScale*auf. Dadurch wird ermittelt, ob die Skalierungssteuerelemente aktiviert werden sollen.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel CIRC](../../overview/visual-cpp-samples.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleDialog-Klasse](../../mfc/reference/coledialog-class.md)<br/>
[CPropertyPage-Klasse](../../mfc/reference/cpropertypage-class.md)
