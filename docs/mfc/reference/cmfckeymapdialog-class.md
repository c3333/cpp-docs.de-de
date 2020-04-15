---
title: CMFCKeyMapDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::CMFCKeyMapDialog
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::DoModal
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::FormatItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::GetCommandKeys
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnInsertItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintHeader
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnPrintItem
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::OnSetColumns
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::PrintKeyMap
- AFXKEYMAPDIALOG/CMFCKeyMapDialog::SetColumnsWidth
helpviewer_keywords:
- CMFCKeyMapDialog [MFC], CMFCKeyMapDialog
- CMFCKeyMapDialog [MFC], DoModal
- CMFCKeyMapDialog [MFC], FormatItem
- CMFCKeyMapDialog [MFC], GetCommandKeys
- CMFCKeyMapDialog [MFC], OnInsertItem
- CMFCKeyMapDialog [MFC], OnPrintHeader
- CMFCKeyMapDialog [MFC], OnPrintItem
- CMFCKeyMapDialog [MFC], OnSetColumns
- CMFCKeyMapDialog [MFC], PrintKeyMap
- CMFCKeyMapDialog [MFC], SetColumnsWidth
ms.assetid: 5feb4942-d636-462d-a162-0104dd320f4e
ms.openlocfilehash: 22aa006ce214ca720192bb761e2ff2b35a64fce3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374415"
---
# <a name="cmfckeymapdialog-class"></a>CMFCKeyMapDialog-Klasse

Die `CMFCKeyMapDialog` Klasse unterstützt ein Steuerelement, das Befehle Tasten auf der Tastatur zuordnet.

## <a name="syntax"></a>Syntax

```
class CMFCKeyMapDialog : public CDialogEx
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCKeyMapDialog::CMFCKeyMapDialog](#cmfckeymapdialog)|Erstellt ein `CMFCKeyMapDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCKeyMapDialog::DoModal](#domodal)|Zeigt ein Dialogfeld für die Tastaturzuordnung an.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCKeyMapDialog::FormatItem](#formatitem)|Wird vom Framework aufgerufen, um eine Zeichenfolge zu erstellen, die eine Schlüsselzuordnung beschreibt. Standardmäßig enthält die Zeichenfolge den Befehlsnamen, die verwendeten Tastenkombinationen und die Beschreibung der Tastenkombination.|
|[CMFCKeyMapDialog::GetCommandKeys](#getcommandkeys)|Ruft eine Zeichenfolge ab, die eine Liste von Tastenkombinationen enthält, die dem angegebenen Befehl zugeordnet sind.|
|[CMFCKeyMapDialog::OnInsertItem](#oninsertitem)|Wird vom Framework aufgerufen, bevor ein neues Element in das interne Listensteuerelement eingefügt wird, das das Tastaturzuordnungssteuerelement unterstützt.|
|[CMFCKeyMapDialog::OnPrintHeader](#onprintheader)|Wird vom Framework aufgerufen, um die Kopfzeile für die Tastaturzuordnung auf einer neuen Seite zu drucken.|
|[CMFCKeyMapDialog::OnPrintItem](#onprintitem)|Wird vom Framework aufgerufen, um ein Tastaturzuordnungselement zu drucken.|
|[CMFCKeyMapDialog::OnSetColumns](#onsetcolumns)|Wird vom Framework aufgerufen, um Beschriftungen für die Spalten im internen Listensteuerelement festzulegen, das das Tastaturzuordnungssteuerelement unterstützt.|
|[CMFCKeyMapDialog::PrintKeyMap](#printkeymap)|Wird vom Framework aufgerufen, wenn ein Benutzer auf die Schaltfläche **Drucken** klickt.|
|[CMFCKeyMapDialog::SetColumnsWidth](#setcolumnswidth)|Wird vom Framework aufgerufen, um die Breite der Spalten im internen Listensteuerelement festzulegen, das das Tastaturzuordnungssteuerelement unterstützt.|

## <a name="remarks"></a>Bemerkungen

Verwenden `CMFCKeyMapDialog` Sie die Klasse, um ein in der Verteilbares Dialogfeld für die Tastaturzuordnung zu implementieren. Das Dialogfeld verwendet ein Listenansichtssteuerelement, um Tastenkombinationen und die zugehörigen Befehle anzuzeigen.

Um die `CMFCKeyMapDialog` Klasse in einer Anwendung zu verwenden, übergeben Sie in `CMFCKeyMapDialog` einem Zeiger auf das Hauptrahmenfenster als Parameter an den Konstruktor. Rufen Sie `DoModal` dann die Methode auf, um ein modales Dialogfeld zu starten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCKeyMapDialog](../../mfc/reference/cmfckeymapdialog-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxkeymapdialog.h

## <a name="cmfckeymapdialogcmfckeymapdialog"></a><a name="cmfckeymapdialog"></a>CMFCKeyMapDialog::CMFCKeyMapDialog

Erstellt ein `CMFCKeyMapDialog`-Objekt.

```
CMFCKeyMapDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bEnablePrint=FALSE);
```

### <a name="parameters"></a>Parameter

*pWndParentFrame*<br/>
[in] Ein Zeiger auf das übergeordnete `CMFCKeyMapDialog` Fenster des Objekts.

*bEnablePrint*<br/>
[in] TRUE, wenn die Liste der Beschleunigerschlüssel gedruckt werden kann; andernfalls FALSE. Der Standardwert lautet FALSE.

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCKeyMapDialog` wie ein Objekt der Klasse erstellt wird. Dieses Beispiel ist Teil des [Visual Studio-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#21](../../mfc/codesnippet/cpp/cmfckeymapdialog-class_1.cpp)]

## <a name="cmfckeymapdialogdomodal"></a><a name="domodal"></a>CMFCKeyMapDialog::DoModal

Zeigt ein Dialogfeld für die Tastaturzuordnung an.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

Eine signierte Ganzzahl, z. B. IDOK oder IDCANCEL, die an die [CDialog::EndDialog-Methode](../../mfc/reference/cdialog-class.md#enddialog) übergeben wird. Die Methode schließt wiederum das Dialogfeld. Weitere Informationen finden Sie unter [CDialog::DoModal](../../mfc/reference/cdialog-class.md#domodal).

### <a name="remarks"></a>Bemerkungen

Im Dialogfeld Tastaturzuordnung können Sie Beschleunigertasten auswählen und verschiedenen Befehlskategorien zuweisen. Darüber hinaus können Sie die ausgewählten Beschleunigertasten und deren Beschreibung in die Zwischenablage kopieren.

## <a name="cmfckeymapdialogformatitem"></a><a name="formatitem"></a>CMFCKeyMapDialog::FormatItem

Wird vom Framework aufgerufen, um eine Zeichenfolge zu erstellen, die eine Schlüsselzuordnung beschreibt. Standardmäßig enthält die Zeichenfolge den Befehlsnamen, die verwendeten Tastenkombinationen und die Beschreibung der Tastenkombination.

```
virtual CString FormatItem(int nItem) const;
```

### <a name="parameters"></a>Parameter

*nItem*<br/>
[in] Der nullbasierte Index eines Elements in der internen Liste der Schlüsselzuordnungen.

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den formatierten Elementtext enthält.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfckeymapdialoggetcommandkeys"></a><a name="getcommandkeys"></a>CMFCKeyMapDialog::GetCommandKeys

Ruft einen Zeichenfolgenwert ab. Die Zeichenfolge enthält eine Liste von Tastenkombinationen, die einem angegebenen Befehl zugeordnet sind.

```
virtual CString GetCommandKeys(UINT uiCmdID) const;
```

### <a name="parameters"></a>Parameter

*uiCmdID*<br/>
[in] Eine Befehls-ID.

### <a name="return-value"></a>Rückgabewert

Eine durch Semikolons getrennte Liste von Tastenkombinationen, die dem angegebenen Befehl zugeordnet sind.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfckeymapdialogoninsertitem"></a><a name="oninsertitem"></a>CMFCKeyMapDialog::OnInsertItem

Wird vom Framework aufgerufen, bevor ein neues Element in ein internes Listensteuerelement eingefügt wird, das das Tastaturzuordnungssteuerelement unterstützt.

```
virtual void OnInsertItem(
    CMFCToolBarButton* pButton,
    int nItem);
```

### <a name="parameters"></a>Parameter

*pButton*<br/>
[in] Ein Zeiger auf eine Symbolleistenschaltfläche, mit der eine Tastenkombination einer Befehlsbezeichnung und -beschreibung zugeordnet wird. Das Schlüsselzuordnungselement wird in einem internen Listensteuerelement gespeichert.

*nItem*<br/>
[in] Ein nullbasierter Index, der angibt, wo das neue Schlüsselzuordnungselement in das interne Listensteuerelement eingefügt werden soll.

### <a name="remarks"></a>Bemerkungen

## <a name="cmfckeymapdialogonprintheader"></a><a name="onprintheader"></a>CMFCKeyMapDialog::OnPrintHeader

Wird vom Framework aufgerufen, um die Kopfzeile für die Tastaturzuordnung auf einer neuen Seite zu drucken.

```
virtual int OnPrintHeader(
    CDC& dc,
    int nPage,
    int cx) const;
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
[in] Der Gerätekontext für den Drucker.

*nPage*<br/>
[in] Die zu druckende Seitenzahl.

*Cx*<br/>
[in] Der horizontale Versatz des Headers in Pixel.

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, die Höhe des gedruckten Textes. Weitere Informationen finden Sie im Abschnitt Rückgabewert von [CDC::DrawText](../../mfc/reference/cdc-class.md#drawtext).

### <a name="remarks"></a>Bemerkungen

Das Framework verwendet diese Methode, um die Tastaturkarte zu drucken. Standardmäßig druckt diese Methode die Seitenzahl, den Anwendungsnamen und den Dialogfeldtitel.

## <a name="cmfckeymapdialogonprintitem"></a><a name="onprintitem"></a>CMFCKeyMapDialog::OnPrintItem

Wird vom Framework aufgerufen, um ein Tastaturzuordnungselement zu drucken.

```
virtual int OnPrintItem(
    CDC& dc,
    int nItem,
    int y,
    int cx,
    BOOL bCalcHeight) const;
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
[in] Der Gerätekontext des Druckers.

*nItem*<br/>
[in] Der nullbasierte Index des zu druckenden Elements.

*y*<br/>
[in] Der vertikale Versatz zwischen dem oberen Rand der Seite und der Position des Elements.

*Cx*<br/>
[in] Der horizontale Versatz zwischen der linken Seite der Seite und der Position des Elements.

*bCalcHeight*<br/>
[in] TRUE, um die beste Höhe für das Druckelement zu berechnen; FALSE, um das Druckelement zu abschneiden, damit es an den Standardbereich passt.

### <a name="return-value"></a>Rückgabewert

Die Höhe des gedruckten Artikels.

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, um ein Schlüsselkartendialogfeldelement zu drucken. Standardmäßig druckt diese Methode den Befehlsnamen, die Tastenkombinationen und die Befehlsbeschreibung des Elements.

## <a name="cmfckeymapdialogonsetcolumns"></a><a name="onsetcolumns"></a>CMFCKeyMapDialog::OnSetColumns

Wird vom Framework aufgerufen, um Beschriftungen für die Spalten im internen Listensteuerelement festzulegen, das das Tastaturzuordnungssteuerelement unterstützt.

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Bemerkungen

Standardmäßig ruft diese Methode die Beschriftungen für die Spalten aus drei Ressourcen ab. Die Befehlsspaltenbeschriftung stammt aus IDS_AFXBARRES_COMMAND, die Schlüsselspaltenbeschriftung aus IDS_AFXBARRES_KEYS und die Beschriftung der Beschreibungsspalte aus IDS_AFXBARRES_DESCRIPTION.

## <a name="cmfckeymapdialogprintkeymap"></a><a name="printkeymap"></a>CMFCKeyMapDialog::PrintKeyMap

Wird vom Framework aufgerufen, wenn ein Benutzer auf die Schaltfläche **Drucken** klickt.

```
virtual void PrintKeyMap();
```

### <a name="remarks"></a>Bemerkungen

Die `PrintKeyMap` Methode druckt die Schlüsselkarte. Es initiiert einen neuen Druckauftrag und ruft dann wiederholt die [CMFCKeyMapDialog::OnPrintHeader-](#onprintheader) und [CMFCKeyMapDialog::OnPrintItem-Methoden](#onprintitem) auf, bis alle Schlüsselzuordnungen gedruckt werden.

## <a name="cmfckeymapdialogsetcolumnswidth"></a><a name="setcolumnswidth"></a>CMFCKeyMapDialog::SetColumnsWidth

Wird vom Framework aufgerufen, um die Breite der Spalten im internen Listensteuerelement festzulegen, das das Tastaturzuordnungssteuerelement unterstützt.

```
virtual void SetColumnsWidth();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode legt die Spalten des internen Listensteuerelements auf Standardbreiten fest. Zunächst wird die Breite der Spalte Mitschnitttasten berechnet. Dann wird ein Drittel der verbleibenden Breite der Befehlsspalte und die restlichen zwei Drittel der Beschreibungsspalte zugeordnet.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager-Klasse](../../mfc/reference/ckeyboardmanager-class.md)
