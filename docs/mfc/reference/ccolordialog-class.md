---
title: CColorDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CColorDialog
- AFXDLGS/CColorDialog
- AFXDLGS/CColorDialog::CColorDialog
- AFXDLGS/CColorDialog::DoModal
- AFXDLGS/CColorDialog::GetColor
- AFXDLGS/CColorDialog::GetSavedCustomColors
- AFXDLGS/CColorDialog::SetCurrentColor
- AFXDLGS/CColorDialog::OnColorOK
- AFXDLGS/CColorDialog::m_cc
helpviewer_keywords:
- CColorDialog [MFC], CColorDialog
- CColorDialog [MFC], DoModal
- CColorDialog [MFC], GetColor
- CColorDialog [MFC], GetSavedCustomColors
- CColorDialog [MFC], SetCurrentColor
- CColorDialog [MFC], OnColorOK
- CColorDialog [MFC], m_cc
ms.assetid: d013dc25-9290-4b5d-a97e-95ad7208e13b
ms.openlocfilehash: ab8d934ca0c40c7073f2fc6d88549eb8db595b3f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352239"
---
# <a name="ccolordialog-class"></a>CColorDialog-Klasse

Ermöglicht es Ihnen, ein Dialogfeld für die Farbauswahl in Ihre Anwendung zu integrieren.

## <a name="syntax"></a>Syntax

```
class CColorDialog : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CColorDialog::CColorDialog](#ccolordialog)|Erstellt ein `CColorDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CColorDialog::DoModal](#domodal)|Zeigt ein Farbdialogfeld an und ermöglicht es dem Benutzer, eine Auswahl zu treffen.|
|[CColorDialog::GetColor](#getcolor)|Gibt `COLORREF` eine Struktur zurück, die die Werte der ausgewählten Farbe enthält.|
|[CColorDialog::GetSavedCustomColors](#getsavedcustomcolors)|Ruft benutzerdefinierte Farben ab, die vom Benutzer erstellt wurden.|
|[CColorDialog::SetCurrentColor](#setcurrentcolor)|Erzwingt die aktuelle Farbauswahl auf die angegebene Farbe.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CColorDialog::OnColorOK](#oncolorok)|Überschreiben, um die in das Dialogfeld eingegebene Farbe zu überprüfen.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CColorDialog::m_cc](#m_cc)|Eine Struktur, die zum Anpassen der Einstellungen des Dialogfelds verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Ein `CColorDialog` Objekt ist ein Dialogfeld mit einer Liste von Farben, die für das Anzeigesystem definiert sind. Der Benutzer kann eine bestimmte Farbe aus der Liste auswählen oder erstellen, die dann nach Demenkfeld an die Anwendung zurückgemeldet wird.

Um ein `CColorDialog` Objekt zu erstellen, verwenden Sie den bereitgestellten Konstruktor oder leiten Sie eine neue Klasse ab, und verwenden Sie einen eigenen benutzerdefinierten Konstruktor.

Nachdem das Dialogfeld erstellt wurde, können Sie beliebige Werte in der [m_cc](#m_cc) Struktur festlegen oder ändern, um die Werte der Steuerelemente des Dialogfelds zu initialisieren. Die *m_cc* Struktur vom Typ [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1).

Rufen Sie nach dem Initialisieren der `DoModal` Steuerelemente des Dialogfelds die Memberfunktion auf, um das Dialogfeld anzuzeigen, und ermöglichen Sie dem Benutzer, eine Farbe auszuwählen. `DoModal`gibt die Auswahl des Benutzers entweder der Schaltfläche OK (IDOK) oder Abbrechen (IDCANCEL) des Benutzers zurück.

Wenn `DoModal` IDOK zurückgegeben wird, `CColorDialog`können Sie eine der Memberfunktionen von verwenden, um die vom Benutzer eingegebenen Informationen abzurufen.

Sie können die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) verwenden, um zu ermitteln, ob während der Initialisierung des Dialogfelds ein Fehler aufgetreten ist, und um mehr über den Fehler zu erfahren.

`CColorDialog`sich auf das COMMDLG verlässt. DLL-Datei, die mit Windows-Versionen 3.1 und höher ausgeliefert wird.

Um das Dialogfeld anzupassen, leiten `CColorDialog`Sie eine Klasse von ab, stellen Sie eine benutzerdefinierte Dialogfeldvorlage bereit, und fügen Sie eine Meldungszuordnung hinzu, um die Benachrichtigungen aus den erweiterten Steuerelementen zu verarbeiten. Alle nicht verarbeiteten Nachrichten sollten an die Basisklasse übergeben werden.

Das Anpassen der Hook-Funktion ist nicht erforderlich.

> [!NOTE]
> Bei einigen `CColorDialog` Installationen wird das Objekt nicht mit einem grauen `CDialog` Hintergrund angezeigt, wenn Sie das Framework verwendet haben, um andere Objekte grau zu machen.

Weitere Informationen zur `CColorDialog`Verwendung finden Sie unter [Allgemeine Dialogklassen](../../mfc/common-dialog-classes.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CColorDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="ccolordialogccolordialog"></a><a name="ccolordialog"></a>CColorDialog::CColorDialog

Erstellt ein `CColorDialog`-Objekt.

```
CColorDialog(
    COLORREF clrInit = 0,
    DWORD dwFlags = 0,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*clrInit*<br/>
Die Standardfarbauswahl. Wenn kein Wert angegeben ist, ist der Standardwert RGB(0,0,0) (schwarz).

*dwFlags*<br/>
Ein Satz von Flags, die die Funktion und Darstellung des Dialogfelds anpassen. Weitere Informationen finden Sie in der [CHOOSECOLOR-Struktur](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1) im Windows SDK.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete oder Besitzerfenster des Dialogfelds.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#49](../../mfc/codesnippet/cpp/ccolordialog-class_1.cpp)]

## <a name="ccolordialogdomodal"></a><a name="domodal"></a>CColorDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld allgemeine Farbe von Windows anzuzeigen und dem Benutzer die Auswahl einer Farbe zu ermöglichen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL. Wenn IDCANCEL zurückgegeben wird, rufen Sie die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) auf, um zu ermitteln, ob ein Fehler aufgetreten ist.

IDOK und IDCANCEL sind Konstanten, die angeben, ob der Benutzer die Schaltfläche OK oder Abbrechen ausgewählt hat.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Farbdialogfeldoptionen initialisieren möchten, [m_cc](#m_cc) indem Sie Elemente der `DoModal` m_cc Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogfeldobjekt erstellt wurde.

Nach `DoModal`dem Aufruf können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen, die der Benutzer in das Dialogfeld eingibt, abzurufen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CColorDialog::CColorDialog](#ccolordialog).

## <a name="ccolordialoggetcolor"></a><a name="getcolor"></a>CColorDialog::GetColor

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um die Informationen über die Vom Benutzer ausgewählte Farbe abzurufen.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der die RGB-Informationen für die im Farbdialogfeld ausgewählte Farbe enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#50](../../mfc/codesnippet/cpp/ccolordialog-class_2.cpp)]

## <a name="ccolordialoggetsavedcustomcolors"></a><a name="getsavedcustomcolors"></a>CColorDialog::GetSavedCustomColors

`CColorDialog`Objekte ermöglichen es dem Benutzer, neben der Auswahl von Farben bis zu 16 benutzerdefinierte Farben zu definieren.

```
static COLORREF* PASCAL GetSavedCustomColors();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Array von 16 RGB-Farbwerten, in dem vom Benutzer erstellte benutzerdefinierte Farben gespeichert werden.

### <a name="remarks"></a>Bemerkungen

Die `GetSavedCustomColors` Memberfunktion ermöglicht den Zugriff auf diese Farben. Diese Farben können abgerufen werden, nachdem [DoModal](#domodal) IDOK zurückgegeben hat.

Jeder der 16 RGB-Werte im zurückgegebenen Array wird in RGB (255,255,255) (weiß) initialisiert. Die vom Benutzer ausgewählten benutzerdefinierten Farben werden nur zwischen Dialogfeldaufrufen innerhalb der Anwendung gespeichert. Wenn Sie diese Farben zwischen Aufrufen der Anwendung speichern möchten, müssen Sie sie auf andere Weise speichern, z. B. in einer Initialisierung (. INI)-Datei.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#51](../../mfc/codesnippet/cpp/ccolordialog-class_3.cpp)]

## <a name="ccolordialogm_cc"></a><a name="m_cc"></a>CColorDialog::m_cc

Eine Struktur vom Typ [CHOOSECOLOR](/windows/win32/api/commdlg/ns-commdlg-choosecolora~r1), deren Elemente die Merkmale und Werte des Dialogfelds speichern.

```
CHOOSECOLOR m_cc;
```

### <a name="remarks"></a>Bemerkungen

Nach dem `CColorDialog` Erstellen eines Objekts können Sie *m_cc* verwenden, um verschiedene Aspekte des Dialogfelds festzulegen, bevor Sie die [DoModal-Memberfunktion](#domodal) aufrufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#53](../../mfc/codesnippet/cpp/ccolordialog-class_4.cpp)]

## <a name="ccolordialogoncolorok"></a><a name="oncolorok"></a>CColorDialog::OnColorOK

Überschreiben, um die in das Dialogfeld eingegebene Farbe zu überprüfen.

```
virtual BOOL OnColorOK();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Dialogfeld nicht verworfen werden soll. andernfalls 0, um die eingegebene Farbe zu akzeptieren.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion nur, wenn Sie eine benutzerdefinierte Überprüfung der Farbe bereitstellen möchten, die der Benutzer im Farbdialogfeld auswählt.

Der Benutzer kann eine Farbe nach einer der folgenden beiden Methoden auswählen:

- Klicken Sie auf eine Farbe in der Farbpalette. Die RGB-Werte der ausgewählten Farbe werden dann in den entsprechenden RGB-Bearbeitungsfeldern widergespiegelt.

- Eingeben von Werten in den RGB-Bearbeitungsfeldern

Durch `OnColorOK` Das Überschreiben können Sie eine Farbe ablehnen, die der Benutzer aus anwendungsspezifischen Gründen in ein allgemeines Farbdialogfeld eingibt.

Normalerweise müssen Sie diese Funktion nicht verwenden, da das Framework eine Standardüberprüfung von Farben bereitstellt und ein Meldungsfeld anzeigt, wenn eine ungültige Farbe eingegeben wird.

Sie können [SetCurrentColor](#setcurrentcolor) `OnColorOK` von innen aufrufen, um eine Farbauswahl zu erzwingen. Nachdem `OnColorOK` Sie ausgelöst wurden (d. h., der Benutzer klickt auf **OK,** um die Farbänderung zu akzeptieren), können Sie [GetColor](#getcolor) aufrufen, um den RGB-Wert der neuen Farbe abzurufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#52](../../mfc/codesnippet/cpp/ccolordialog-class_5.cpp)]

## <a name="ccolordialogsetcurrentcolor"></a><a name="setcurrentcolor"></a>CColorDialog::SetCurrentColor

Rufen Sie diese `DoModal` Funktion nach dem Aufruf auf, um die aktuelle Farbauswahl auf den in *clr*angegebenen Farbwert zu erzwingen.

```
void SetCurrentColor(COLORREF clr);
```

### <a name="parameters"></a>Parameter

*Clr*<br/>
Ein RGB-Farbwert.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird innerhalb eines `OnColorOK`Nachrichtenhandlers oder aufgerufen. Das Dialogfeld aktualisiert automatisch die Auswahl des Benutzers basierend auf dem Wert des *parameters clr.*

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CColorDialog::OnColorOK](#oncolorok).

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[MFC-Beispiel DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
