---
title: CFontDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFontDialog
- AFXDLGS/CFontDialog
- AFXDLGS/CFontDialog::CFontDialog
- AFXDLGS/CFontDialog::DoModal
- AFXDLGS/CFontDialog::GetCharFormat
- AFXDLGS/CFontDialog::GetColor
- AFXDLGS/CFontDialog::GetCurrentFont
- AFXDLGS/CFontDialog::GetFaceName
- AFXDLGS/CFontDialog::GetSize
- AFXDLGS/CFontDialog::GetStyleName
- AFXDLGS/CFontDialog::GetWeight
- AFXDLGS/CFontDialog::IsBold
- AFXDLGS/CFontDialog::IsItalic
- AFXDLGS/CFontDialog::IsStrikeOut
- AFXDLGS/CFontDialog::IsUnderline
- AFXDLGS/CFontDialog::m_cf
helpviewer_keywords:
- CFontDialog [MFC], CFontDialog
- CFontDialog [MFC], DoModal
- CFontDialog [MFC], GetCharFormat
- CFontDialog [MFC], GetColor
- CFontDialog [MFC], GetCurrentFont
- CFontDialog [MFC], GetFaceName
- CFontDialog [MFC], GetSize
- CFontDialog [MFC], GetStyleName
- CFontDialog [MFC], GetWeight
- CFontDialog [MFC], IsBold
- CFontDialog [MFC], IsItalic
- CFontDialog [MFC], IsStrikeOut
- CFontDialog [MFC], IsUnderline
- CFontDialog [MFC], m_cf
ms.assetid: 6228d500-ed0f-4156-81e5-ab0d57d1dcf4
ms.openlocfilehash: 6ece239496def9fd65a95a622ac3c475fe5becea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373827"
---
# <a name="cfontdialog-class"></a>CFontDialog-Klasse

Ermöglicht es Ihnen, ein Dialogfeld für die Schriftartauswahl in Ihre Anwendung zu integrieren.

## <a name="syntax"></a>Syntax

```
class CFontDialog : public CCommonDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFontDialog::CFontDialog](#cfontdialog)|Erstellt ein `CFontDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFontDialog::DoModal](#domodal)|Zeigt das Dialogfeld an und ermöglicht es dem Benutzer, eine Auswahl zu treffen.|
|[CFontDialog::GetCharFormat](#getcharformat)|Ruft die Zeichenformatierung der ausgewählten Schriftart ab.|
|[CFontDialog::GetColor](#getcolor)|Gibt die Farbe der ausgewählten Schriftart zurück.|
|[CFontDialog::GetCurrentFont](#getcurrentfont)|Weist die Merkmale der aktuell ausgewählten `LOGFONT` Schriftart einer Struktur zu.|
|[CFontDialog::GetFaceName](#getfacename)|Gibt den Flächennamen der ausgewählten Schriftart zurück.|
|[CFontDialog::GetSize](#getsize)|Gibt die Punktgröße der ausgewählten Schriftart zurück.|
|[CFontDialog::GetStyleName](#getstylename)|Gibt den Stilnamen der ausgewählten Schriftart zurück.|
|[CFontDialog::GetWeight](#getweight)|Gibt die Gewichtung der ausgewählten Schriftart zurück.|
|[CfontDialog::IsBold](#isbold)|Bestimmt, ob die Schriftart fett formatiert ist.|
|[CFontDialog::IsItalic](#isitalic)|Bestimmt, ob die Schriftart kursiv ist.|
|[CfontDialog::IsStrikeOut](#isstrikeout)|Bestimmt, ob die Schriftart mit Strikeout angezeigt wird.|
|[CFontDialog::IsUnderline](#isunderline)|Bestimmt, ob die Schriftart unterstrichen ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFontDialog::m_cf](#m_cf)|Eine Struktur, die `CFontDialog` zum Anpassen eines Objekts verwendet wird.|

## <a name="remarks"></a>Bemerkungen

Ein `CFontDialog` Objekt ist ein Dialogfeld mit einer Liste von Schriftarten, die derzeit im System installiert sind. Der Benutzer kann eine bestimmte Schriftart aus der Liste auswählen, und diese Auswahl wird dann an die Anwendung zurückgemeldet.

Um ein `CFontDialog` Objekt zu erstellen, verwenden Sie den bereitgestellten Konstruktor oder leiten Sie eine neue Unterklasse ab, und verwenden Sie einen eigenen benutzerdefinierten Konstruktor.

Nachdem `CFontDialog` ein Objekt erstellt wurde, `m_cf` können Sie die Struktur verwenden, um die Werte oder Zustände von Steuerelementen im Dialogfeld zu initialisieren. Die [m_cf](#m_cf) Struktur vom Typ [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw). Weitere Informationen zu dieser Struktur finden Sie im Windows SDK.

Rufen Sie nach dem Initialisieren der `DoModal` Steuerelemente des Dialogobjekts die Memberfunktion auf, um das Dialogfeld anzuzeigen, und ermöglichen Sie dem Benutzer, eine Schriftart auszuwählen. `DoModal`gibt an, ob der Benutzer die Schaltfläche OK (IDOK) oder Abbrechen (IDCANCEL) ausgewählt hat.

Wenn `DoModal` IDOK zurückgegeben wird, `CFontDialog`können Sie eine der Memberfunktionen von verwenden, um die vom Benutzer eingegebenen Informationen abzurufen.

Sie können die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) verwenden, um zu ermitteln, ob während der Initialisierung des Dialogfelds ein Fehler aufgetreten ist, und um mehr über den Fehler zu erfahren. Weitere Informationen zu dieser Funktion finden Sie im Windows SDK.

`CFontDialog`sich auf das COMMDLG verlässt. DLL-Datei, die mit Windows-Versionen 3.1 und höher ausgeliefert wird.

Um das Dialogfeld anzupassen, leiten `CFontDialog`Sie eine Klasse von ab, stellen Sie eine benutzerdefinierte Dialogfeldvorlage bereit, und fügen Sie eine Meldungszuordnung hinzu, um die Benachrichtigungen aus den erweiterten Steuerelementen zu verarbeiten. Alle nicht verarbeiteten Nachrichten sollten an die Basisklasse übergeben werden.

Das Anpassen der Hook-Funktion ist nicht erforderlich.

Weitere Informationen zur `CFontDialog`Verwendung finden Sie unter [Allgemeine Dialogklassen](../../mfc/common-dialog-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CCommonDialog](../../mfc/reference/ccommondialog-class.md)

`CFontDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdlgs.h

## <a name="cfontdialogcfontdialog"></a><a name="cfontdialog"></a>CFontDialog::CFontDialog

Erstellt ein `CFontDialog`-Objekt.

```
CFontDialog(
    LPLOGFONT lplfInitial = NULL,
    DWORD dwFlags = CF_EFFECTS | CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);

CFontDialog(
    const CHARFORMAT& charformat,
    DWORD dwFlags = CF_SCREENFONTS,
    CDC* pdcPrinter = NULL,
    CWnd* pParentWnd = NULL);
```

### <a name="parameters"></a>Parameter

*plfInitial*<br/>
Ein Zeiger auf eine [LOGFONT-Datenstruktur,](/windows/win32/api/wingdi/ns-wingdi-logfontw) mit der Sie einige Der Schriftartenfestlegen festlegen können.

*charFormat*<br/>
Ein Zeiger auf eine [CHARFORMAT-Datenstruktur,](/windows/win32/api/richedit/ns-richedit-charformata) mit der Sie einige der Schriftzüge in einem umfangreichen Bearbeitungssteuerelement festlegen können.

*dwFlags*<br/>
Bestimmt eine oder mehrere Schriftart-wählen-Flags. Ein oder mehrere Vorgabewerte können mit dem bitweisen OR-Operator kombiniert werden. Wenn Sie den `m_cf.Flag`s-Strukturmember ändern, stellen Sie sicher, dass Sie einen bitweisen OR-Operator bei Ihren Änderungen verwenden, um das Standardverhalten unverändert zu lassen. Weitere Informationen zu jedem dieser Flags finden Sie in der Beschreibung der [CHOOSEFONT-Struktur](/windows/win32/api/commdlg/ns-commdlg-choosefontw) im Windows SDK.

*pdcPrinter*<br/>
Ein Zeiger auf einen Druckgerätekontext. Sofern bereitgestellt, verweist dieser Parameter auf einen Druckgerätekontext für den Drucker, auf dem die Schriftarten ausgewählt werden sollen.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete Fenster oder das Besitzerfenster des Schriftartdialogfelds.

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass der Konstruktor automatisch die Member der `CHOOSEFONT`-Struktur ausfüllt. Sie sollten diese nur ändern, wenn Sie ein anderes Schriftartdialogfeld als das standardmäßige verwenden möchten.

> [!NOTE]
> Die erste Version dieser Funktion existiert nur, wenn es keine Unterstützung für das Rich-Edit-Steuerelement gibt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#78](../../mfc/codesnippet/cpp/cfontdialog-class_1.cpp)]

## <a name="cfontdialogdomodal"></a><a name="domodal"></a>CFontDialog::DoModal

Rufen Sie diese Funktion auf, um das Dialogfeld allgemeine Windows-Schriftart anzuzeigen und dem Benutzer die Auswahl einer Schriftart zu ermöglichen.

```
virtual INT_PTR DoModal();
```

### <a name="return-value"></a>Rückgabewert

IDOK oder IDCANCEL. Wenn IDCANCEL zurückgegeben wird, rufen Sie die Windows [CommDlgExtendedError-Funktion](/windows/win32/api/commdlg/nf-commdlg-commdlgextendederror) auf, um zu ermitteln, ob ein Fehler aufgetreten ist.

IDOK und IDCANCEL sind Konstanten, die angeben, ob der Benutzer die Schaltfläche OK oder Abbrechen ausgewählt hat.

### <a name="remarks"></a>Bemerkungen

Wenn Sie die verschiedenen Schriftdialogsteuerelemente initialisieren [m_cf](#m_cf) möchten, indem Sie Elemente `DoModal`der m_cf Struktur festlegen, sollten Sie dies vor dem Aufruf tun, jedoch nachdem das Dialogobjekt erstellt wurde.

Wenn `DoModal` IDOK zurückgegeben wird, können Sie andere Memberfunktionen aufrufen, um die Einstellungen oder Informationen, die der Benutzer eingibt, in das Dialogfeld abzurufen.

### <a name="example"></a>Beispiel

  Siehe die Beispiele für [CFontDialog::CFontDialog](#cfontdialog) und [CFontDialog::GetColor](#getcolor).

## <a name="cfontdialoggetcharformat"></a><a name="getcharformat"></a>CFontDialog::GetCharFormat

Ruft die Zeichenformatierung der ausgewählten Schriftart ab.

```
void GetCharFormat(CHARFORMAT& cf) const;
```

### <a name="parameters"></a>Parameter

*Cf*<br/>
Eine [CHARFORMAT-Struktur,](/windows/win32/api/richedit/ns-richedit-charformata) die Informationen über die Zeichenformatierung der ausgewählten Schriftart enthält.

## <a name="cfontdialoggetcolor"></a><a name="getcolor"></a>CFontDialog::GetColor

Rufen Sie diese Funktion auf, um die ausgewählte Schriftfarbe abzurufen.

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>Rückgabewert

Die Farbe der ausgewählten Schriftart.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#79](../../mfc/codesnippet/cpp/cfontdialog-class_2.cpp)]

## <a name="cfontdialoggetcurrentfont"></a><a name="getcurrentfont"></a>CFontDialog::GetCurrentFont

Rufen Sie diese Funktion auf, um den Membern einer [LOGFONT-Struktur](/windows/win32/api/wingdi/ns-wingdi-logfontw) die Merkmale der aktuell ausgewählten Schriftart zuzuweisen.

```
void GetCurrentFont(LPLOGFONT lplf);
```

### <a name="parameters"></a>Parameter

*lplf*<br/>
Ein Zeiger auf `LOGFONT` eine Struktur.

### <a name="remarks"></a>Bemerkungen

Weitere `CFontDialog` Memberfunktionen werden bereitgestellt, um auf einzelne Merkmale der aktuellen Schriftart zuzugreifen.

Wenn diese Funktion während eines Aufrufs von [DoModal](#domodal)aufgerufen wird, gibt sie die aktuelle Auswahl zu diesem Zeitpunkt zurück (was der Benutzer im Dialogfeld sieht oder geändert hat). Wenn diese Funktion nach einem `DoModal` Aufruf `DoModal` von aufgerufen wird (nur wenn IDOK zurückgegeben wird), gibt sie zurück, was der Benutzer tatsächlich ausgewählt hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#80](../../mfc/codesnippet/cpp/cfontdialog-class_3.cpp)]

## <a name="cfontdialoggetfacename"></a><a name="getfacename"></a>CFontDialog::GetFaceName

Rufen Sie diese Funktion auf, um den Flächennamen der ausgewählten Schriftart abzurufen.

```
CString GetFaceName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Flächenname der im `CFontDialog` Dialogfeld ausgewählten Schriftart.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#81](../../mfc/codesnippet/cpp/cfontdialog-class_4.cpp)]

## <a name="cfontdialoggetsize"></a><a name="getsize"></a>CFontDialog::GetSize

Rufen Sie diese Funktion auf, um die Größe der ausgewählten Schriftart abzurufen.

```
int GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Die Schriftgröße in Zehntel eines Punktes.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#82](../../mfc/codesnippet/cpp/cfontdialog-class_5.cpp)]

## <a name="cfontdialoggetstylename"></a><a name="getstylename"></a>CFontDialog::GetStyleName

Rufen Sie diese Funktion auf, um den Stilnamen der ausgewählten Schriftart abzurufen.

```
CString GetStyleName() const;
```

### <a name="return-value"></a>Rückgabewert

Der Stilname der Schriftart.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#83](../../mfc/codesnippet/cpp/cfontdialog-class_6.cpp)]

## <a name="cfontdialoggetweight"></a><a name="getweight"></a>CFontDialog::GetWeight

Rufen Sie diese Funktion auf, um die Gewichtung der ausgewählten Schriftart abzurufen.

```
int GetWeight() const;
```

### <a name="return-value"></a>Rückgabewert

Die Gewichtung der ausgewählten Schriftart.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zur Gewichtung einer Schriftart finden Sie unter [CFont::CreateFont](../../mfc/reference/cfont-class.md#createfont).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#84](../../mfc/codesnippet/cpp/cfontdialog-class_7.cpp)]

## <a name="cfontdialogisbold"></a><a name="isbold"></a>CfontDialog::IsBold

Rufen Sie diese Funktion auf, um zu ermitteln, ob die ausgewählte Schriftart fett formatiert ist.

```
BOOL IsBold() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn in der ausgewählten Schriftart das Bold-Merkmal aktiviert ist. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#85](../../mfc/codesnippet/cpp/cfontdialog-class_8.cpp)]

## <a name="cfontdialogisitalic"></a><a name="isitalic"></a>CFontDialog::IsItalic

Rufen Sie diese Funktion auf, um zu ermitteln, ob die ausgewählte Schriftart kursiv ist.

```
BOOL IsItalic() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn in der ausgewählten Schriftart das Italic-Merkmal aktiviert ist. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#86](../../mfc/codesnippet/cpp/cfontdialog-class_9.cpp)]

## <a name="cfontdialogisstrikeout"></a><a name="isstrikeout"></a>CfontDialog::IsStrikeOut

Rufen Sie diese Funktion auf, um zu bestimmen, ob die ausgewählte Schriftart mit Strikeout angezeigt wird.

```
BOOL IsStrikeOut() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn in der ausgewählten Schriftart das Strikeout-Merkmal aktiviert ist. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#87](../../mfc/codesnippet/cpp/cfontdialog-class_10.cpp)]

## <a name="cfontdialogisunderline"></a><a name="isunderline"></a>CFontDialog::IsUnderline

Rufen Sie diese Funktion auf, um zu bestimmen, ob die ausgewählte Schriftart unterstrichen ist.

```
BOOL IsUnderline() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn in der ausgewählten Schriftart das Merkmal Unterstreichung aktiviert ist. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#88](../../mfc/codesnippet/cpp/cfontdialog-class_11.cpp)]

## <a name="cfontdialogm_cf"></a><a name="m_cf"></a>CFontDialog::m_cf

Eine Struktur, deren Member die Eigenschaften des Dialogobjekts speichern.

```
CHOOSEFONT m_cf;
```

### <a name="remarks"></a>Bemerkungen

Nach dem `CFontDialog` Erstellen eines `m_cf` Objekts können Sie verschiedene Aspekte `DoModal` des Dialogfelds ändern, bevor Sie die Memberfunktion aufrufen. Weitere Informationen zu dieser Struktur finden Sie unter [CHOOSEFONT](/windows/win32/api/commdlg/ns-commdlg-choosefontw) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#89](../../mfc/codesnippet/cpp/cfontdialog-class_12.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CCommonDialog-Klasse](../../mfc/reference/ccommondialog-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)
