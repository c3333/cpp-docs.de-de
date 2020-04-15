---
title: CMFCEditBrowseCtrl-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFileBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::EnableFolderBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::GetMode
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnAfterUpdate
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnBrowse
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnChangeLayout
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnDrawBrowseButton
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::OnIllegalFileName
- AFXEDITBROWSECTRL/CMFCEditBrowseCtrl::SetBrowseButtonImage
helpviewer_keywords:
- CMFCEditBrowseCtrl [MFC], EnableBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFileBrowseButton
- CMFCEditBrowseCtrl [MFC], EnableFolderBrowseButton
- CMFCEditBrowseCtrl [MFC], GetMode
- CMFCEditBrowseCtrl [MFC], OnAfterUpdate
- CMFCEditBrowseCtrl [MFC], OnBrowse
- CMFCEditBrowseCtrl [MFC], OnChangeLayout
- CMFCEditBrowseCtrl [MFC], OnDrawBrowseButton
- CMFCEditBrowseCtrl [MFC], OnIllegalFileName
- CMFCEditBrowseCtrl [MFC], SetBrowseButtonImage
ms.assetid: 69cfd886-3d35-4bee-8901-7c88fcf9520f
ms.openlocfilehash: 6c611297353f82e4ec90365cbe33db763d9c9838
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367538"
---
# <a name="cmfceditbrowsectrl-class"></a>CMFCEditBrowseCtrl-Klasse

Die `CMFCEditBrowseCtrl` Klasse unterstützt das Bearbeitungs-Browse-Steuerelement, bei dem es sich um ein bearbeitbares Textfeld handelt, das optional eine Schaltfläche zum Durchsuchen enthält. Wenn der Benutzer auf die Schaltfläche zum Durchsuchen klicken, führt das Steuerelement eine benutzerdefinierte Aktion aus oder zeigt ein Standarddialogfeld an, das einen Dateibrowser oder einen Ordnerbrowser enthält.

## <a name="syntax"></a>Syntax

```
class CMFCEditBrowseCtrl : public CEdit
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCEditBrowseCtrl::CMFCEditBrowseCtrl`|Der Standardkonstruktor.|
|`CMFCEditBrowseCtrl::~CMFCEditBrowseCtrl`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton)|Aktiviert oder deaktiviert die Schaltfläche "Durchsuchen".|
|[CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)|Aktiviert die Schaltfläche "Durchsuchen" und versetzt das Bearbeitungs-Suchsteuerelement in den *Dateisuchmodus.*|
|[CMFCEditBrowseCtrl::EnableFolderBrowseButton](#enablefolderbrowsebutton)|Aktiviert die Schaltfläche "Durchsuchen" und versetzt das Bearbeitungs-Suchsteuerelement in den *Ordner-Suchmodus.*|
|[CMFCEditBrowseCtrl::GetMode](#getmode)|Gibt den aktuellen Suchmodus zurück.|
|[CMFCEditBrowseCtrl::OnAfterUpdate](#onafterupdate)|Wird vom Framework aufgerufen, nachdem das Bearbeitungs-Browse-Steuerelement mit dem Ergebnis einer Suchaktion aktualisiert wurde.|
|[CMFCEditBrowseCtrl::OnBrowse](#onbrowse)|Wird vom Framework aufgerufen, nachdem der Benutzer auf die Schaltfläche "Durchsuchen" geklickt hat.|
|[CMFCEditBrowseCtrl::OnChangeLayout](#onchangelayout)|Zeichnet das aktuelle Bearbeitungs-Suchsteuerelement neu.|
|[CMFCEditBrowseCtrl::OnDrawBrowseButton](#ondrawbrowsebutton)|Wird vom Framework aufgerufen, um die Schaltfläche "Durchsuchen" zu zeichnen.|
|[CMFCEditBrowseCtrl::OnIllegalFileName](#onillegalfilename)|Wird vom Framework aufgerufen, wenn ein ungültiger Dateiname in das Bearbeitungssteuerelement eingegeben wurde.|
|`CMFCEditBrowseCtrl::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. Syntax und weitere Informationen finden Sie unter [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).|
|[CMFCEditBrowseCtrl::SetBrowseButtonImage](#setbrowsebuttonimage)|Legt ein benutzerdefiniertes Bild für die Schaltfläche "Durchsuchen" fest.|

## <a name="remarks"></a>Bemerkungen

Verwenden Sie ein Bearbeitungs-Suchsteuerelement, um einen Datei- oder Ordnernamen auszuwählen. Optional können Sie das Steuerelement verwenden, um eine benutzerdefinierte Aktion auszuführen, z. B. um ein Dialogfeld anzuzeigen. Sie können die Schaltfläche "Durchsuchen" anzeigen oder nicht anzeigen, und Sie können eine benutzerdefinierte Beschriftung oder ein benutzerdefiniertes Bild auf die Schaltfläche anwenden.

Der *Suchmodus* des Bearbeitungs-Suchsteuerelements bestimmt, ob eine Schaltfläche zum Durchsuchen angezeigt wird und welche Aktion auftritt, wenn auf die Schaltfläche geklickt wird. Weitere Informationen finden Sie unter [GetMode-Methode.](#getmode)

Die `CMFCEditBrowseCtrl` Klasse unterstützt die folgenden Modi.

- **Benutzerdefinierter Modus**

   Eine benutzerdefinierte Aktion wird ausgeführt, wenn der Benutzer auf die Schaltfläche "Durchsuchen" klickt. Sie können z. B. ein anwendungsspezifisches Dialogfeld anzeigen.

- **Dateimodus**

   Ein Standardmäßiges Dialogfeld für die Dateiauswahl wird angezeigt, wenn der Benutzer auf die Schaltfläche "Durchsuchen" klickt.

- **Ordnermodus**

   Ein Dialogfeld für die Standardordnerauswahl wird angezeigt, wenn der Benutzer auf die Schaltfläche "Durchsuchen" klickt.

## <a name="how-to-specify-an-edit-browse-control"></a>How-How: Geben Sie ein Bearbeitungs-Browse-Steuerelement an

Führen Sie die folgenden Schritte aus, um ein Bearbeitungs-Browse-Steuerelement in Ihre Anwendung zu integrieren:

1. Wenn Sie einen benutzerdefinierten Suchmodus implementieren möchten, `CMFCEditBrowseCtrl` leiten Sie Ihre eigene Klasse von der Klasse ab, und überschreiben Sie dann die [CMFCEditBrowseCtrl::OnBrowse-Methode.](#onbrowse) Führen Sie in der überschriebenen Methode eine benutzerdefinierte Suchaktion aus, und aktualisieren Sie das Bearbeitungs-Browse-Steuerelement mit dem Ergebnis.

1. Betten Sie `CMFCEditBrowseCtrl` entweder das Objekt oder das abgeleitete Bearbeitungs-Such-Steuerelementobjekt in das übergeordnete Fensterobjekt ein.

1. Wenn Sie den **Klassen-Assistenten** zum Erstellen eines Dialogfelds verwenden, fügen Sie dem Dialogfeldformular ein Bearbeitungssteuerelement ( `CEdit`) hinzu. Fügen Sie außerdem eine Variable hinzu, um auf das Steuerelement in der Headerdatei zuzugreifen. Ändern Sie in der Headerdatei den `CEdit` `CMFCEditBrowseCtrl`Typ der Variablen von in . Das Bearbeitungs-Browse-Steuerelement wird automatisch erstellt. Wenn Sie den **Klassen-Assistenten**nicht `CMFCEditBrowseCtrl` verwenden, fügen Sie der `Create` Headerdatei eine Variable hinzu, und rufen Sie dann ihre Methode auf.

1. Wenn Sie einem Dialogfeld ein Bearbeitungs-Suchsteuerelement hinzufügen, verwenden Sie das **Tool ClassWizard,** um den Datenaustausch einzurichten.

1. Rufen Sie die [EnableFolderBrowseButton](#enablefolderbrowsebutton), [EnableFileBrowseButton](#enablefilebrowsebutton)oder [EnableBrowseButton-Methode](#enablebrowsebutton) auf, um den Suchmodus festzulegen und die Schaltfläche "Durchsuchen" anzuzeigen. Rufen Sie die [GetMode-Methode](#getmode) auf, um den aktuellen Suchmodus abzurufen.

1. Um ein benutzerdefiniertes Bild für die Schaltfläche "Durchsuchen" bereitzustellen, rufen Sie die [SetBrowseButtonImage-Methode](#setbrowsebuttonimage) auf, oder überschreiben Sie die [OnDrawBrowseButton-Methode.](#ondrawbrowsebutton)

1. Um die Schaltfläche "Durchsuchen" aus dem Steuerelement "Durchsuchen bearbeiten" zu entfernen, rufen Sie die [EnableBrowseButton-Methode](#enablebrowsebutton) auf, wobei der Parameter *bEnable* auf FALSE festgelegt ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCEditBrowseCtrl](../../mfc/reference/cmfceditbrowsectrl-class.md)

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCEditBrowseCtrl` wie `EnableFolderBrowseButton` zwei `EnableFileBrowseButton`Methoden in der Klasse verwendet werden: und . Dieses Beispiel ist Teil des [Beispiels "Neue Steuerelemente "Neue Steuerelemente ".](../../overview/visual-cpp-samples.md)

[!code-cpp[NVC_MFC_NewControls#6](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#7](../../mfc/reference/codesnippet/cpp/cmfceditbrowsectrl-class_2.cpp)]

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxeditbrowsectrl.h

## <a name="cmfceditbrowsectrlenablebrowsebutton"></a><a name="enablebrowsebutton"></a>CMFCEditBrowseCtrl::EnableBrowseButton

Zeigt die Schaltfläche "Durchsuchen" im aktuellen Bearbeitungs-Suchsteuerelement an oder zeigt sie nicht an.

```
void EnableBrowseButton(
    BOOL bEnable=TRUE,
    LPCTSTR szLabel=_T("..."));
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
TRUE, um die Schaltfläche "Durchsuchen" anzuzeigen; FALSE, um die Schaltfläche "Durchsuchen" nicht anzuzeigen. Der Standardwert ist TRUE.

*szLabel*<br/>
Die Beschriftung, die auf der Schaltfläche "Durchsuchen" angezeigt wird. Der Standardwert ist " **...**".

### <a name="remarks"></a>Bemerkungen

Wenn der *Parameter bEnable* TRUE ist, implementieren Sie eine benutzerdefinierte Aktion, die ausgeführt werden soll, wenn auf die Schaltfläche "Durchsuchen" geklickt wird. Um eine benutzerdefinierte Aktion zu implementieren, leiten Sie eine Klasse von der `CMFCEditBrowseCtrl` Klasse ab, und überschreiben Sie dann die [OnBrowse-Methode.](#onbrowse)

Wenn der *Parameter bEnable* TRUE ist, ist `BrowseMode_Default`der Suchmodus des Steuerelements ; Andernfalls ist `BrowseMode_None`der Suchmodus . Weitere Informationen zu Suchmodi finden Sie unter [GetMode-Methode.](#getmode)

## <a name="cmfceditbrowsectrlenablefilebrowsebutton"></a><a name="enablefilebrowsebutton"></a>CMFCEditBrowseCtrl::EnableFileBrowseButton

Zeigt die Schaltfläche "Durchsuchen" im aktuellen Bearbeitungs-Suchsteuerelement an und versetzt das Steuerelement in den *Dateisuchmodus.*

```
void EnableFileBrowseButton(
    LPCTSTR lpszDefExt=NULL,
    LPCTSTR lpszFilter=NULL,
    DWORD dwFlags = OFN_HIDEREADONLY | OFN_OVERWRITEPROMPT);
```

### <a name="parameters"></a>Parameter

*lpszDefExt*<br/>
Gibt die Standard-Dateinamenerweiterung an, die im Dialogfeld zur Dateiauswahl verwendet wird. Der Standardwert ist NULL.

*lpszFilter*<br/>
Gibt die Standardfilterzeichenfolge an, die im Dialogfeld zur Dateiauswahl verwendet wird. Der Standardwert ist NULL.

*dwFlags*<br/>
Dialogfeldflags. Der Standardwert ist eine bitweise Kombination (OR) von OFN_HIDEREADONLY und OFN_OVERWRITEPROMPT.

### <a name="remarks"></a>Bemerkungen

Wenn das Steuerelement zum Bearbeiten und Durchsuchen sich im Dateidurchsuchungsmodus befindet und der Benutzer auf die Schaltfläche zum Durchsuchen klickt, zeigt das Steuerelement das standardmäßige Dialogfeld zur Dateiauswahl an.

Eine vollständige Liste der verfügbaren Flags finden Sie unter [OPENFILENAME-Struktur](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

## <a name="cmfceditbrowsectrlenablefolderbrowsebutton"></a><a name="enablefolderbrowsebutton"></a>CMFCEditBrowseCtrl::EnableFolderBrowseButton

Zeigt die Schaltfläche "Durchsuchen" im aktuellen Bearbeitungs-Suchsteuerelement an und versetzt das Steuerelement in den *Ordner-Suchmodus.*

```
void EnableFolderBrowseButton();
```

### <a name="remarks"></a>Bemerkungen

Wenn sich das Steuerelement zum Durchsuchen des Ordners im Ordnersuchmodus befindet und der Benutzer auf die Schaltfläche "Durchsuchen" klickt, zeigt das Steuerelement das Dialogfeld für die Standardordnerauswahl an.

## <a name="cmfceditbrowsectrlgetmode"></a><a name="getmode"></a>CMFCEditBrowseCtrl::GetMode

Ruft den Suchmodus des aktuellen Bearbeitungs-Suchsteuerelements ab.

```
CMFCEditBrowseCtrl::BrowseMode GetMode() const;
```

### <a name="return-value"></a>Rückgabewert

Einer der Enumerationswerte, der den aktuellen Modus des Bearbeitungssuchsteuerelements angibt. Der Suchmodus bestimmt, ob das Framework die Schaltfläche "Durchsuchen" anzeigt und welche Aktion auftritt, wenn ein Benutzer auf diese Schaltfläche klickt.

In der folgenden Tabelle sind die möglichen Rückgabewerte aufgelistet:

|Wert|BESCHREIBUNG|
|-----------|-----------------|
|`BrowseMode_Default`|**benutzerdefinierter Modus**. Es wird eine programmerdefinierte Aktion ausgeführt.|
|`BrowseMode_File`|**Dateimodus**. Das Dialogfeld des Standarddateibrowsers wird angezeigt.|
|`BrowseMode_Folder`|**Ordnermodus**. Das Dialogfeld des Standardordnerbrowsers wird angezeigt.|
|`BrowseMode_None`|Die Schaltfläche "Durchsuchen" wird nicht angezeigt.|

### <a name="remarks"></a>Bemerkungen

Standardmäßig wird `CMFCEditBrowseCtrl` ein Objekt in `BrowseMode_None` den Modus initialisiert. Ändern Sie den Suchmodus mit den Methoden [CMFCEditBrowseCtrl::EnableBrowseButton](#enablebrowsebutton), [CMFCEditBrowseCtrl::EnableFileBrowseButton](#enablefilebrowsebutton)und [CMFCEditBrowseCtrl::EnableFolderBrowseButton.](#enablefolderbrowsebutton)

## <a name="cmfceditbrowsectrlonafterupdate"></a><a name="onafterupdate"></a>CMFCEditBrowseCtrl::OnAfterUpdate

Wird vom Framework aufgerufen, nachdem das Bearbeitungs-Browse-Steuerelement mit dem Ergebnis einer Suchaktion aktualisiert wurde.

```
virtual void OnAfterUpdate();
```

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um eine benutzerdefinierte Aktion zu implementieren.

## <a name="cmfceditbrowsectrlonbrowse"></a><a name="onbrowse"></a>CMFCEditBrowseCtrl::OnBrowse

Wird vom Framework aufgerufen, nachdem der Benutzer auf die Schaltfläche "Durchsuchen" des Bearbeitungs-Suchsteuerelements geklickt hat.

```
virtual void OnBrowse();
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um benutzerdefinierten Code auszuführen, wenn der Benutzer auf die Schaltfläche "Durchsuchen" des Bearbeitungs-Suchsteuerelements klickt. Leiten Sie Ihre eigene `CMFCEditBrowseCtrl` Klasse von `OnBrowse` der Klasse ab, und überschreiben Sie ihre Methode. Implementieren Sie bei dieser Methode eine benutzerdefinierte Suchaktion, und aktualisieren Sie optional das Textfeld des Bearbeitungs-Browse-Steuerelements. Verwenden Sie in Ihrer Anwendung die [EnableBrowseButton-Methode,](#enablebrowsebutton) um das Bearbeitungssuchsteuerelement in den *benutzerdefinierten Suchmodus zu* versetzen.

## <a name="cmfceditbrowsectrlonchangelayout"></a><a name="onchangelayout"></a>CMFCEditBrowseCtrl::OnChangeLayout

Zeichnet das aktuelle Bearbeitungs-Suchsteuerelement neu.

```
virtual void OnChangeLayout();
```

### <a name="remarks"></a>Bemerkungen

Das Framework ruft diese Methode auf, wenn sich der Suchmodus des Bearbeitungssuchsteuerelements ändert. Weitere Informationen finden Sie unter [CMFCEditBrowseCtrl::GetMode](#getmode).

## <a name="cmfceditbrowsectrlondrawbrowsebutton"></a><a name="ondrawbrowsebutton"></a>CMFCEditBrowseCtrl::OnDrawBrowseButton

Wird vom Framework aufgerufen, um die Schaltfläche "Durchsuchen" auf dem Bearbeitungs-Browse-Steuerelement zu zeichnen.

```
virtual void OnDrawBrowseButton(
    CDC* pDC,
    CRect rect,
    BOOL bIsButtonPressed,
    BOOL bIsButtonHot);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Ein Zeiger zu einem Gerätekontext.

*Rect*<br/>
Das umgrenzende Rechteck der Schaltfläche "Durchsuchen".

*bIsButtonPressed*<br/>
TRUE, wenn die Taste gedrückt wird; andernfalls FALSE.

*bIsButtonHot*<br/>
TRUE, wenn die Schaltfläche hervorgehoben ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion in einer abgeleiteten Klasse, um die Darstellung der Schaltfläche "Durchsuchen" anzupassen.

## <a name="cmfceditbrowsectrlsetbrowsebuttonimage"></a><a name="setbrowsebuttonimage"></a>CMFCEditBrowseCtrl::SetBrowseButtonImage

Legt ein benutzerdefiniertes Bild auf der Schaltfläche "Durchsuchen" des Bearbeitungs-Browse-Steuerelements fest.

```
void SetBrowseButtonImage(
    HICON hIcon,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy= TRUE);

void SetBrowseButtonImage(UINT uiBmpResId);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
Das Handle eines Symbols.

*hBitmap*<br/>
Das Handle einer Bitmap.

*uiBmpResId*<br/>
Die Ressourcen-ID einer Bitmap.

*bAutoDestroy*<br/>
TRUE, um das angegebene Symbol oder die Bitmap zu löschen, wenn diese Methode beendet wird; andernfalls FALSE. Der Standardwert ist TRUE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um ein benutzerdefiniertes Bild auf die Schaltfläche "Durchsuchen" anzuwenden. Standardmäßig erhält das Framework ein Standardbild, wenn sich das Bearbeitungs-Suchsteuerelement im *Datei-Suchmodus* oder im *Ordner-Suchmodus* befindet.

## <a name="cmfceditbrowsectrlonillegalfilename"></a><a name="onillegalfilename"></a>CMFCEditBrowseCtrl::OnIllegalFileName

Wird vom Framework aufgerufen, wenn ein ungültiger Dateiname in das Bearbeitungssteuerelement eingegeben wurde.

```
virtual BOOL OnIllegalFileName(CString& strFileName);
```

### <a name="parameters"></a>Parameter

*strFileName*<br/>
Gibt den ungültigen Dateinamen an.

### <a name="return-value"></a>Rückgabewert

Sollte FALSE zurückgeben, wenn dieser Dateiname nicht weiter an das Dateidialogfeld übergeben werden kann. In diesem Fall wird der Fokus auf das Bearbeitungssteuerelement zurückgesetzt, und der Benutzer sollte die Bearbeitung fortsetzen. Die Standardimplementierung zeigt ein Meldungsfeld an, das den Benutzer über den ungültigen Dateinamen informiert, und gibt FALSE zurück. Sie können diese Methode überschreiben, den Dateinamen korrigieren und TRUE zur weiteren Verarbeitung zurückgeben.

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
