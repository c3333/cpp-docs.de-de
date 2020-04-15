---
title: CTaskDialog Class
ms.date: 11/19/2018
f1_keywords:
- CTaskDialog
- AFXTASKDIALOG/CTaskDialog
- AFXTASKDIALOG/CTaskDialog::CTaskDialog
- AFXTASKDIALOG/CTaskDialog::AddCommandControl
- AFXTASKDIALOG/CTaskDialog::AddRadioButton
- AFXTASKDIALOG/CTaskDialog::ClickCommandControl
- AFXTASKDIALOG/CTaskDialog::ClickRadioButton
- AFXTASKDIALOG/CTaskDialog::DoModal
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonCount
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonFlag
- AFXTASKDIALOG/CTaskDialog::GetCommonButtonId
- AFXTASKDIALOG/CTaskDialog::GetOptions
- AFXTASKDIALOG/CTaskDialog::GetSelectedCommandControlID
- AFXTASKDIALOG/CTaskDialog::GetSelectedRadioButtonID
- AFXTASKDIALOG/CTaskDialog::GetVerificationCheckboxState
- AFXTASKDIALOG/CTaskDialog::IsCommandControlEnabled
- AFXTASKDIALOG/CTaskDialog::IsRadioButtonEnabled
- AFXTASKDIALOG/CTaskDialog::IsSupported
- AFXTASKDIALOG/CTaskDialog::LoadCommandControls
- AFXTASKDIALOG/CTaskDialog::LoadRadioButtons
- AFXTASKDIALOG/CTaskDialog::NavigateTo
- AFXTASKDIALOG/CTaskDialog::OnCommandControlClick
- AFXTASKDIALOG/CTaskDialog::OnCreate
- AFXTASKDIALOG/CTaskDialog::OnDestroy
- AFXTASKDIALOG/CTaskDialog::OnExpandButtonClick
- AFXTASKDIALOG/CTaskDialog::OnHelp
- AFXTASKDIALOG/CTaskDialog::OnHyperlinkClick
- AFXTASKDIALOG/CTaskDialog::OnInit
- AFXTASKDIALOG/CTaskDialog::OnNavigatePage
- AFXTASKDIALOG/CTaskDialog::OnRadioButtonClick
- AFXTASKDIALOG/CTaskDialog::OnTimer
- AFXTASKDIALOG/CTaskDialog::OnVerificationCheckboxClick
- AFXTASKDIALOG/CTaskDialog::RemoveAllCommandControls
- AFXTASKDIALOG/CTaskDialog::RemoveAllRadioButtons
- AFXTASKDIALOG/CTaskDialog::SetCommandControlOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetCommonButtons
- AFXTASKDIALOG/CTaskDialog::SetContent
- AFXTASKDIALOG/CTaskDialog::SetDefaultCommandControl
- AFXTASKDIALOG/CTaskDialog::SetDefaultRadioButton
- AFXTASKDIALOG/CTaskDialog::SetDialogWidth
- AFXTASKDIALOG/CTaskDialog::SetExpansionArea
- AFXTASKDIALOG/CTaskDialog::SetFooterIcon
- AFXTASKDIALOG/CTaskDialog::SetFooterText
- AFXTASKDIALOG/CTaskDialog::SetMainIcon
- AFXTASKDIALOG/CTaskDialog::SetMainInstruction
- AFXTASKDIALOG/CTaskDialog::SetOptions
- AFXTASKDIALOG/CTaskDialog::SetProgressBarMarquee
- AFXTASKDIALOG/CTaskDialog::SetProgressBarPosition
- AFXTASKDIALOG/CTaskDialog::SetProgressBarRange
- AFXTASKDIALOG/CTaskDialog::SetProgressBarState
- AFXTASKDIALOG/CTaskDialog::SetRadioButtonOptions
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckbox
- AFXTASKDIALOG/CTaskDialog::SetVerificationCheckboxText
- AFXTASKDIALOG/CTaskDialog::SetWindowTitle
- AFXTASKDIALOG/CTaskDialog::ShowDialog
- AFXTASKDIALOG/CTaskDialog::TaskDialogCallback
helpviewer_keywords:
- CTaskDialog [MFC], CTaskDialog
- CTaskDialog [MFC], AddCommandControl
- CTaskDialog [MFC], AddRadioButton
- CTaskDialog [MFC], ClickCommandControl
- CTaskDialog [MFC], ClickRadioButton
- CTaskDialog [MFC], DoModal
- CTaskDialog [MFC], GetCommonButtonCount
- CTaskDialog [MFC], GetCommonButtonFlag
- CTaskDialog [MFC], GetCommonButtonId
- CTaskDialog [MFC], GetOptions
- CTaskDialog [MFC], GetSelectedCommandControlID
- CTaskDialog [MFC], GetSelectedRadioButtonID
- CTaskDialog [MFC], GetVerificationCheckboxState
- CTaskDialog [MFC], IsCommandControlEnabled
- CTaskDialog [MFC], IsRadioButtonEnabled
- CTaskDialog [MFC], IsSupported
- CTaskDialog [MFC], LoadCommandControls
- CTaskDialog [MFC], LoadRadioButtons
- CTaskDialog [MFC], NavigateTo
- CTaskDialog [MFC], OnCommandControlClick
- CTaskDialog [MFC], OnCreate
- CTaskDialog [MFC], OnDestroy
- CTaskDialog [MFC], OnExpandButtonClick
- CTaskDialog [MFC], OnHelp
- CTaskDialog [MFC], OnHyperlinkClick
- CTaskDialog [MFC], OnInit
- CTaskDialog [MFC], OnNavigatePage
- CTaskDialog [MFC], OnRadioButtonClick
- CTaskDialog [MFC], OnTimer
- CTaskDialog [MFC], OnVerificationCheckboxClick
- CTaskDialog [MFC], RemoveAllCommandControls
- CTaskDialog [MFC], RemoveAllRadioButtons
- CTaskDialog [MFC], SetCommandControlOptions
- CTaskDialog [MFC], SetCommonButtonOptions
- CTaskDialog [MFC], SetCommonButtons
- CTaskDialog [MFC], SetContent
- CTaskDialog [MFC], SetDefaultCommandControl
- CTaskDialog [MFC], SetDefaultRadioButton
- CTaskDialog [MFC], SetDialogWidth
- CTaskDialog [MFC], SetExpansionArea
- CTaskDialog [MFC], SetFooterIcon
- CTaskDialog [MFC], SetFooterText
- CTaskDialog [MFC], SetMainIcon
- CTaskDialog [MFC], SetMainInstruction
- CTaskDialog [MFC], SetOptions
- CTaskDialog [MFC], SetProgressBarMarquee
- CTaskDialog [MFC], SetProgressBarPosition
- CTaskDialog [MFC], SetProgressBarRange
- CTaskDialog [MFC], SetProgressBarState
- CTaskDialog [MFC], SetRadioButtonOptions
- CTaskDialog [MFC], SetVerificationCheckbox
- CTaskDialog [MFC], SetVerificationCheckboxText
- CTaskDialog [MFC], SetWindowTitle
- CTaskDialog [MFC], ShowDialog
- CTaskDialog [MFC], TaskDialogCallback
ms.assetid: 1991ec98-ae56-4483-958b-233809c8c559
ms.openlocfilehash: e9aeee31d2952d5362c983934ce85f0332f553fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366634"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

Ein Popupdialogfeld, das wie ein Meldungsfeld funktioniert, aber zusätzliche Informationen für den Benutzer anzeigen kann. `CTaskDialog` enthält auch Funktionen zum Erfassen von Informationen des Benutzers.

## <a name="syntax"></a>Syntax

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|||
|-|-|
|[CTaskDialog::CTaskDialog](#ctaskdialog)|Erstellt ein `CTaskDialog`-Objekt.|

### <a name="methods"></a>Methoden

|||
|-|-|
|[CTaskDialog::AddCommandControl](#addcommandcontrol)|Fügt dem `CTaskDialog`ein Befehlsschaltflächensteuerelement hinzu.|
|[CTaskDialog::AddRadioButton](#addradiobutton)|Fügt dem `CTaskDialog`ein Optionsfeld hinzu.|
|[CTaskDialog::ClickCommandControl](#clickcommandcontrol)|Klickt programmgesteuert auf eine Befehlsschaltflächensteuerung oder eine gemeinsame Schaltfläche.|
|[CTaskDialog::ClickRadioButton](#clickradiobutton)|Klickt programmgesteuert auf ein Optionsfeld.|
|[CTaskDialog::DoModal](#domodal)|Zeigt das `CTaskDialog` an.|
|[CTaskDialog::GetCommonButtonCount](#getcommonbuttoncount)|Ruft die Anzahl der verfügbaren allgemeinen Schaltflächen ab.|
|[CTaskDialog::GetCommonButtonFlag](#getcommonbuttonflag)|Konvertiert eine Standardmäßige Windows-Schaltfläche in den `CTaskDialog` gemeinsamen Schaltflächentyp, der der Klasse zugeordnet ist.|
|[CTaskDialog::GetCommonButtonId](#getcommonbuttonid)|Konvertiert einen der gängigen Schaltflächentypen, die der `CTaskDialog` Klasse zugeordnet sind, in eine Standard-Windows-Schaltfläche.|
|[CTaskDialog::GetOptions](#getoptions)|Gibt die Optionsflags `CTaskDialog`für diese zurück.|
|[CTaskDialog::GetSelectedCommandControlID](#getselectedcommandcontrolid)|Gibt das ausgewählte Befehlsschaltflächensteuerelement zurück.|
|[CTaskDialog::GetSelectedRadioButtonID](#getselectedradiobuttonid)|Gibt das ausgewählte Optionsfeld zurück.|
|[CTaskDialog::GetVerificationCheckboxState](#getverificationcheckboxstate)|Ruft den Status des Überprüfungshäuptchens ab.|
|[CTaskDialog::IsCommandControlEnabled](#iscommandcontrolenabled)|Bestimmt, ob ein Befehlsschaltflächensteuerelement oder eine gemeinsame Schaltfläche aktiviert ist.|
|[CTaskDialog::IsRadioButtonEnabled](#isradiobuttonenabled)|Bestimmt, ob ein Optionsfeld aktiviert ist.|
|[CTaskDialog::Unterstützt](#issupported)|Bestimmt, ob der Computer, auf `CTaskDialog`dem die Anwendung ausgeführt wird, die unterstützt.|
|[CTaskDialog::LoadCommandControls](#loadcommandcontrols)|Fügt Befehlsschaltflächensteuerelemente mithilfe von Daten aus der Zeichenfolgentabelle hinzu.|
|[CTaskDialog::LoadRadioButtons](#loadradiobuttons)|Fügt Optionsfelder mithilfe von Daten aus der Zeichenfolgentabelle hinzu.|
|[CTaskDialog::NavigateTo](#navigateto)|Überträgt den `CTaskDialog`Fokus auf eine andere .|
|[CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf ein Befehlsschaltflächensteuerelement klickt.|
|[CTaskDialog::OnCreate](#oncreate)|Das Framework ruft diese Methode `CTaskDialog`auf, nachdem es die erstellt hat.|
|[CTaskDialog::OnDestroy](#ondestroy)|Das Framework ruft diese Methode unmittelbar `CTaskDialog`auf, bevor sie die zerstört.|
|[CTaskDialog::OnExpandButtonClick](#onexpandbuttonclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf die Erweiterungsschaltfläche klickt.|
|[CTaskDialog::OnHelp](#onhelp)|Das Framework ruft diese Methode auf, wenn der Benutzer Hilfe anfordert.|
|[CTaskDialog::OnHyperlinkClick](#onhyperlinkclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf einen Hyperlink klickt.|
|[CTaskDialog::OnInit](#oninit)|Das Framework ruft diese `CTaskDialog` Methode auf, wenn die initialisiert wird.|
|[CTaskDialog::OnNavigatePage](#onnavigatepage)|Das Framework ruft diese Methode auf, wenn der `CTaskDialog`Benutzer den Fokus in Bezug auf Steuerelemente auf der verschiebt.|
|[CtaskDialog::OnRadioButtonClick](#onradiobuttonclick)|Das Framework ruft diese Methode auf, wenn der Benutzer ein Optionsfeldsteuerelement auswählt.|
|[CTaskDialog::OnTimer](#ontimer)|Das Framework ruft diese Methode auf, wenn der Timer abläuft.|
|[CTaskDialog::OnVerificationCheckboxClick](#onverificationcheckboxclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf das Kontrollkästchen Überprüfung klickt.|
|[CTaskDialog::RemoveAllCommandControls](#removeallcommandcontrols)|Entfernt alle Befehlssteuerelemente `CTaskDialog`aus der .|
|[CTaskDialog::RemoveAllRadioButtons](#removeallradiobuttons)|Entfernt alle Optionsfelder aus `CTaskDialog`der .|
|[CTaskDialog::SetCommandControlOptions](#setcommandcontroloptions)|Aktualisiert ein Befehlsschaltflächensteuerelement auf der `CTaskDialog`.|
|[CTaskDialog::SetCommonButtonOptions](#setcommonbuttonoptions)|Aktualisiert eine Teilmenge der allgemeinen Schaltflächen, die aktiviert werden sollen, und erfordert eine UAC-Erhöhung.|
|[CTaskDialog::SetCommonButtons](#setcommonbuttons)|Fügt dem allgemeine `CTaskDialog`Schaltflächen hinzu.|
|[CTaskDialog::SetContent](#setcontent)|Aktualisiert den Inhalt `CTaskDialog`der .|
|[CTaskDialog::SetDefaultCommandControl](#setdefaultcommandcontrol)|Gibt das Standardmäßige Befehlsschaltflächensteuerelement an.|
|[CTaskDialog::SetDefaultRadioButton](#setdefaultradiobutton)|Gibt das Standardoptionsfeld an.|
|[CTaskDialog::SetDialogWidth](#setdialogwidth)|Passt die Breite `CTaskDialog`der an.|
|[CTaskDialog::SetExpansionArea](#setexpansionarea)|Aktualisiert den Erweiterungsbereich der `CTaskDialog`.|
|[CTaskDialog::SetFooterIcon](#setfootericon)|Aktualisiert das Fußzeilensymbol `CTaskDialog`für die .|
|[CTaskDialog::SetFooterText](#setfootertext)|Aktualisiert den Text in der `CTaskDialog`Fußzeile der .|
|[CTaskDialog::SetMainIcon](#setmainicon)|Aktualisiert das Hauptsymbol `CTaskDialog`der .|
|[CTaskDialog::SetMainInstruction](#setmaininstruction)|Aktualisiert die Hauptanweisung `CTaskDialog`der .|
|[CTaskDialog::SetOptionen](#setoptions)|Konfiguriert die Optionen `CTaskDialog`für die .|
|[CTaskDialog::SetProgressBarMarquee](#setprogressbarmarquee)|Konfiguriert eine Rahmenleiste für `CTaskDialog` die und fügt sie dem Dialogfeld hinzu.|
|[CTaskDialog::SetProgressBarPosition](#setprogressbarposition)|Passt die Position der Fortschrittsleiste an.|
|[CtaskDialog::SetProgressBarRange](#setprogressbarrange)|Passt den Bereich der Fortschrittsleiste an.|
|[CtaskDialog::SetProgressBarState](#setprogressbarstate)|Legt den Status der Fortschrittsleiste `CTaskDialog`fest und zeigt sie auf der an.|
|[CTaskDialog::SetRadioButtonOptions](#setradiobuttonoptions)|Aktiviert oder deaktiviert ein Optionsfeld.|
|[CTaskDialog::SetVerificationCheckbox](#setverificationcheckbox)|Legt den aktivierten Status des Kontrollkästchens Überprüfung fest.|
|[CTaskDialog::SetVerificationCheckboxText](#setverificationcheckboxtext)|Legt den Text auf der rechten Seite des Kontrollkästchens Überprüfung fest.|
|[CTaskDialog::SetWindowTitle](#setwindowtitle)|Legt den Titel `CTaskDialog`der fest.|
|[CTaskDialog::Dialog anzeigen](#showdialog)|Erstellt und `CTaskDialog`zeigt eine an.|
|[CTaskDialog::TaskDialogCallback](#taskdialogcallback)|Das Framework ruft dies als Reaktion auf verschiedene Windows-Nachrichten auf.|

### <a name="data-members"></a>Datenelemente

|||
|-|-|
|`m_aButtons`|Das Array der Befehlsschaltflächensteuerelemente für die `CTaskDialog`.|
|`m_aRadioButtons`|Das Array von Optionstastensteuerelementen für die `CTaskDialog`.|
|`m_bVerified`|`TRUE`zeigt an, dass das Kontrollkästchen Überprüfung aktiviert ist; `FALSE` zeigt an, dass dies nicht der Fall ist.|
|`m_footerIcon`|Das Symbol in der `CTaskDialog`Fußzeile des .|
|`m_hWnd`|Ein Handle zum Fenster `CTaskDialog`für die .|
|`m_mainIcon`|Das Hauptsymbol `CTaskDialog`der .|
|`m_nButtonDisabled`|Eine Maske, die angibt, welche der gemeinsamen Schaltflächen deaktiviert sind.|
|`m_nButtonElevation`|Eine Maske, die angibt, welche der allgemeinen Schaltflächen eine UAC-Höhe erfordern.|
|`m_nButtonId`|Die ID des ausgewählten Befehlstastensteuerelements.|
|`m_nCommonButton`|Eine Maske, die angibt, `CTaskDialog`welche allgemeinen Schaltflächen auf der angezeigt werden.|
|`m_nDefaultCommandControl`|Die ID des Befehlstastensteuerelements, `CTaskDialog` das beim Anzeigen des ausgewählt wird.|
|`m_nDefaultRadioButton`|Die ID des Optionsfeldsteuerelements, `CTaskDialog` das beim Anzeigen des Optionsfeldsteuerelements ausgewählt wird.|
|`m_nFlags`|Eine Maske, die die `CTaskDialog`Optionen für die angibt.|
|`m_nProgressPos`|Die aktuelle Position für den Fortschrittsbalken.  Dabei muss es sich um einen Wert zwischen `m_nProgressRangeMin` und `m_nProgressRangeMax` handeln.|
|`m_nProgressRangeMax`|Der maximale Wert für den Fortschrittsbalken.|
|`m_nProgressRangeMin`|Der Mindestwert für den Fortschrittsbalken.|
|`m_nProgressState`|Der Status der Fortschrittsleiste. Weitere Informationen finden Sie unter [CTaskDialog::SetProgressBarState](#setprogressbarstate).|
|`m_nRadioId`|Die ID des ausgewählten Optionsfeldsteuerelements.|
|`m_nWidth`|Die Breite des `CTaskDialog` in Pixel.|
|`m_strCollapse`|Die Zeichenfolge `CTaskDialog` zeigt die Anzeige rechts neben dem Erweiterungsfeld an, wenn die erweiterten Informationen ausgeblendet werden.|
|`m_strContent`|Die Inhaltszeichenfolge `CTaskDialog`der .|
|`m_strExpand`|Die Zeichenfolge `CTaskDialog` zeigt die Anzeige rechts neben dem Erweiterungsfeld an, wenn die erweiterten Informationen angezeigt werden.|
|`m_strFooter`|Die Fußzeile `CTaskDialog`der .|
|`m_strInformation`|Die erweiterten Informationen `CTaskDialog`für die .|
|`m_strMainInstruction`|Die Hauptanweisung `CTaskDialog`der .|
|`m_strTitle`|Der Titel der `CTaskDialog`.|
|`m_strVerification`|Die Zeichenfolge, `CTaskDialog` die rechts neben dem Kontrollkästchen Überprüfung angezeigt wird.|

## <a name="remarks"></a>Bemerkungen

Die `CTaskDialog` Klasse ersetzt das standardmäßige Windows-Meldungsfeld und verfügt über zusätzliche Funktionen, z. B. neue Steuerelemente zum Sammeln von Informationen vom Benutzer. Diese Klasse befindet sich in der MFC-Bibliothek in Visual Studio 2010 und höher. Der `CTaskDialog` ist ab Windows Vista verfügbar. Frühere Versionen von Windows `CTaskDialog` können das Objekt nicht anzeigen. Verwenden `CTaskDialog::IsSupported` Sie diese Option, um zur Laufzeit zu bestimmen, ob der aktuelle Benutzer das Aufgabendialogfeld anzeigen kann. Das standardmäßige Windows-Meldungsfeld wird weiterhin unterstützt.

Der `CTaskDialog` ist nur verfügbar, wenn Sie Ihre Anwendung mithilfe der Unicode-Bibliothek erstellen.

Der `CTaskDialog` hat zwei verschiedene Konstruktoren. Mit einem Konstruktor können Sie zwei Befehlsschaltflächen und maximal sechs reguläre Schaltflächensteuerelemente angeben. Sie können weitere Befehlsschaltflächen `CTaskDialog`hinzufügen, nachdem Sie die erstellt haben. Der zweite Konstruktor unterstützt keine Befehlsschaltflächen, aber Sie können eine unbegrenzte Anzahl von regulären Schaltflächensteuerelementen hinzufügen. Weitere Informationen zu den Konstruktoren finden Sie unter [CTaskDialog::CTaskDialog](#ctaskdialog).

Die folgende Abbildung `CTaskDialog` zeigt ein Beispiel, um die Position einiger Steuerelemente zu veranschaulichen.

![Beispiel für CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Beispiel für CTaskDialog") <br/>
CTaskDialog-Beispiel

## <a name="requirements"></a>Anforderungen

**Mindestes erforderliches Betriebssystem:** Windows Vista

**Kopfzeile:** afxtaskdialog.h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a>CTaskDialog::AddCommandControl

Fügt dem `CTaskDialog`ein neues Befehlsschaltflächensteuerelement hinzu.

```
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parameter

*nCommandControlID*<br/>
[in] Die Identifikationsnummer der Befehlssteuerung.

*strCaption*<br/>
[in] Die Zeichenfolge, `CTaskDialog` die dem Benutzer angezeigt wird. Verwenden Sie diese Zeichenfolge, um den Zweck des Befehls zu erläutern.

*bAktiviert*<br/>
[in] Ein boolescher Parameter, der angibt, ob die neue Schaltfläche aktiviert oder deaktiviert ist.

*bRequiresElevation*<br/>
[in] Ein boolescher Parameter, der angibt, ob ein Befehl eine Höhe erfordert.

### <a name="remarks"></a>Bemerkungen

Der `CTaskDialog Class` kann eine unbegrenzte Anzahl von Befehlstastensteuerungen anzeigen. Wenn jedoch `CTaskDialog` ein Befehlstastensteuerelement angezeigt wird, können maximal sechs Schaltflächen angezeigt werden. Wenn `CTaskDialog` ein keine Befehlstastensteuerelemente hat, kann eine unbegrenzte Anzahl von Schaltflächen angezeigt werden.

Wenn der Benutzer ein Befehlsschaltflächensteuerelement auswählt, wird der `CTaskDialog` befehlsgesteuert. Wenn Ihre Anwendung das Dialogfeld mit [CTaskDialog::DoModal](#domodal)anzeigt, `DoModal` wird die *nCommandControlID* des ausgewählten Befehlsschaltflächensteuerelements zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a>CTaskDialog::AddRadioButton

Fügt dem `CTaskDialog`ein Optionsfeld hinzu.

```
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parameter

*nRadioButtonID*<br/>
[in] Die Identifikationsnummer des Optionsfelds.

*strCaption*<br/>
[in] Die Zeichenfolge, `CTaskDialog` die neben dem Optionsfeld angezeigt wird.

*bAktiviert*<br/>
[in] Ein boolescher Parameter, der angibt, ob das Optionsfeld aktiviert ist.

### <a name="remarks"></a>Bemerkungen

Mit den Optionsfeldern für die [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) können Sie Informationen vom Benutzer sammeln. Verwenden Sie die Funktion [CTaskDialog::GetSelectedRadioButtonID,](#getselectedradiobuttonid) um zu bestimmen, welche Optionsschaltfläche ausgewählt ist.

Der `CTaskDialog` erfordert nicht, dass die *nRadioButtonID-Parameter* für jeden Optionsfeldeinschlag eindeutig sind. Es kann jedoch zu unerwartetem Verhalten kommen, wenn Sie nicht für jedes Optionsfeld einen eindeutigen Bezeichner verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a>CTaskDialog::ClickCommandControl

Klickt programmgesteuert auf eine Befehlsschaltflächensteuerung oder eine gemeinsame Schaltfläche.

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parameter

*nCommandControlID*<br/>
[in] Die Befehls-ID des zu klickenden Steuerelements.

### <a name="remarks"></a>Bemerkungen

Diese Methode generiert die Windows-Meldung TDM_CLICK_BUTTON.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a>CTaskDialog::ClickRadioButton

Klickt programmgesteuert auf ein Optionsfeld.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parameter

*nRadioButtonID*<br/>
[in] Die ID des zu klickenden Optionsfelds.

### <a name="remarks"></a>Bemerkungen

Diese Methode generiert die Windows-Meldung TDM_CLICK_RADIO_BUTTON.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a>CTaskDialog::CTaskDialog

Erstellt eine Instanz der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md).

```
CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nCommonButtons = TDCBF_OK_BUTTON | TDCBF_CANCEL_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));

CTaskDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Parameter

*strContent*<br/>
[in] Die Zeichenfolge, die für `CTaskDialog`den Inhalt der verwendet werden soll.

*strMainInstruction*<br/>
[in] Die Hauptanweisung `CTaskDialog`der .

*strTitle*<br/>
[in] Der Titel `CTaskDialog`der .

*nCommonButtons*<br/>
[in] Eine Maske der allgemeinen Schaltflächen, die dem `CTaskDialog`hinzugefügt werden sollen.

*nTaskDialogOptionen*<br/>
[in] Der Satz von Optionen, `CTaskDialog`die für die verwendet werden sollen.

*strFooter*<br/>
[in] Die Zeichenfolge, die als Fußzeile verwendet werden soll.

*nIDCommandControlsFirst*<br/>
[in] Die Zeichenfolgen-ID des ersten Befehls.

*nIDCommandControlsLast*<br/>
[in] Die Zeichenfolgen-ID des letzten Befehls.

### <a name="remarks"></a>Bemerkungen

Es gibt zwei Möglichkeiten, `CTaskDialog` wie Sie ihrer Anwendung eine hinzufügen können. Die erste Möglichkeit besteht darin, einen der `CTaskDialog` Konstruktoren zu verwenden, um eine zu erstellen und mit [CTaskDialog::DoModal](#domodal)anzuzeigen. Die zweite Möglichkeit besteht darin, die statische Funktion [CTaskDialog::ShowDialog](#showdialog)zu verwenden, mit der Sie eine `CTaskDialog` anzeigen können, ohne explizit ein `CTaskDialog` Objekt zu erstellen.

Der zweite Konstruktor erstellt Befehlsschaltflächensteuerelemente mithilfe von Daten aus der Ressourcendatei Ihrer Anwendung. Die Zeichenfolgentabelle in der Ressourcendatei enthält mehrere Zeichenfolgen mit zugeordneten Zeichenfolgen-IDs. Diese Methode fügt ein Befehlsschaltflächensteuerelement für jeden gültigen Eintrag in der Zeichenfolgentabelle zwischen *nIDCommandControlsFirst* und *nCommandControlsLast*einschließlich hinzu. Für diese Befehlsschaltflächensteuerelemente ist die Zeichenfolge in der Zeichenfolgentabelle die Beschriftung des Steuerelements und die Zeichenfolgen-ID die ID des Steuerelements.

Siehe [CTaskDialog::SetOptions](#setoptions) für eine Liste gültiger Optionen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a>CTaskDialog::DoModal

Zeigt `CTaskDialog` die und macht sie modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parameter

*hEltern*<br/>
[in] Das übergeordnete Fenster `CTaskDialog`für die .

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die der vom Benutzer getroffenen Auswahl entspricht.

### <a name="remarks"></a>Bemerkungen

Zeigt diese Instanz des [CTaskDialog](../../mfc/reference/ctaskdialog-class.md)an. Die Anwendung wartet dann darauf, dass der Benutzer das Dialogfeld schließt.

Der `CTaskDialog` wird geschlossen, wenn der Benutzer eine gemeinsame Schaltfläche, ein `CTaskDialog`Befehlsverknüpfungssteuerelement oder die schließt. Der Rückgabewert ist der Bezeichner, der angibt, wie der Benutzer das Dialogfeld geschlossen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a>CTaskDialog::GetCommonButtonCount

Ruft die Anzahl der allgemeinen Schaltflächen ab.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der verfügbaren allgemeinen Schaltflächen.

### <a name="remarks"></a>Bemerkungen

Die allgemeinen Schaltflächen sind die Standardschaltflächen, die Sie [cTaskDialog::CTaskDialog](#ctaskdialog)bereitstellen. Die [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) zeigt die Schaltflächen am unteren Rand des Dialogfelds an.

Die aufgezählte Liste der Schaltflächen wird in CommCtrl.h bereitgestellt.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a>CTaskDialog::GetCommonButtonFlag

Konvertiert eine Standardmäßige Windows-Schaltfläche in den allgemeinen Schaltflächentyp, der der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)zugeordnet ist.

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parameter

*nButtonId*<br/>
[in] Der standardmäßige Windows-Schaltflächenwert.

### <a name="return-value"></a>Rückgabewert

Der Wert der `CTaskDialog` entsprechenden gemeinsamen Schaltfläche. Wenn keine entsprechende gemeinsame Schaltfläche vorhanden ist, gibt diese Methode 0 zurück.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a>CTaskDialog::GetCommonButtonId

Konvertiert einen der gängigen Schaltflächentypen, die der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) zugeordnet sind, in eine Standard-Windows-Schaltfläche.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parameter

*nFlag*<br/>
[in] Der der `CTaskDialog` Klasse zugeordnete gemeinsame Schaltflächentyp.

### <a name="return-value"></a>Rückgabewert

Der Wert der entsprechenden Windows-Standardschaltfläche. Wenn keine entsprechende Windows-Schaltfläche vorhanden ist, gibt die Methode 0 zurück.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a>CTaskDialog::GetOptions

Gibt die Optionsflags `CTaskDialog`für diese zurück.

```
int GetOptions() const;
```

### <a name="return-value"></a>Rückgabewert

Die Flags `CTaskDialog`für die .

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu den Optionen, die für die [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)verfügbar sind, finden Sie unter [CTaskDialog::SetOptions](#setoptions).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a>CTaskDialog::GetSelectedCommandControlID

Gibt das ausgewählte Befehlsschaltflächensteuerelement zurück.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Rückgabewert

Die ID des aktuell ausgewählten Befehlsschaltflächensteuerelements.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Methode nicht verwenden, um die ID der vom Benutzer ausgewählten Befehlsschaltfläche abzurufen. Diese ID wird entweder von [CTaskDialog::DoModal](#domodal) oder [CTaskDialog::ShowDialog](#showdialog)zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a>CTaskDialog::GetSelectedRadioButtonID

Gibt das ausgewählte Optionsfeld zurück.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Rückgabewert

Die ID des ausgewählten Optionsfelds.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode verwenden, nachdem der Benutzer das Dialogfeld zum Abrufen des ausgewählten Optionsfelds geschlossen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a>CTaskDialog::GetVerificationCheckboxState

Ruft den Status des Überprüfungshäuptchens ab.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Kontrollkästchen aktiviert ist, FALSE, wenn dies nicht der Fall ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a>CTaskDialog::IsCommandControlEnabled

Bestimmt, ob ein Befehlsschaltflächensteuerelement oder eine Schaltfläche aktiviert ist.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parameter

*nCommandControlID*<br/>
[in] Die ID des zu testenden Befehlstastensteuerelements oder der Schaltfläche.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Steuerelement aktiviert ist, FALSE, wenn es nicht ist.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie die Verfügbarkeit sowohl der Befehlsschaltflächensteuerelemente als auch der allgemeinen Schaltflächen der `CTaskDialog` Klasse* bestimmen.

Wenn *nCommandControlID* kein gültiger Bezeichner für eine gemeinsame `CTaskDialog` Schaltfläche oder ein Befehlsschaltflächensteuerelement ist, löst diese Methode eine Ausnahme aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a>CTaskDialog::IsRadioButtonEnabled

Bestimmt, ob ein Optionsfeld aktiviert ist.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parameter

*nRadioButtonID*<br/>
[in] Die ID des zu testenden Optionsfelds.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Optionsfeld aktiviert ist, FALSE, wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Wenn *nRadioButtonID* kein gültiger Bezeichner für ein Optionsfeld ist, löst diese Methode eine Ausnahme aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a>CTaskDialog::Unterstützt

Bestimmt, ob der Computer, auf `CTaskDialog`dem die Anwendung ausgeführt wird, die unterstützt.

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der `CTaskDialog`Computer die unterstützt ; FALSE sonst.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um zur Laufzeit zu bestimmen, ob der Computer, auf dem die Anwendung ausgeführt wird, die `CTaskDialog` Klasse unterstützt. Wenn der Computer die `CTaskDialog`nicht unterstützt, sollten Sie eine andere Methode zum Kommunizieren von Informationen an den Benutzer bereitstellen. Ihre Anwendung stürzt ab, wenn `CTaskDialog` sie versucht, eine `CTaskDialog` auf einem Computer zu verwenden, der die Klasse nicht unterstützt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a>CTaskDialog::LoadCommandControls

Fügt Befehlsschaltflächensteuerelemente mithilfe von Daten aus der Zeichenfolgentabelle hinzu.

```
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parameter

*nIDCommandControlsFirst*<br/>
[in] Die Zeichenfolgen-ID des ersten Befehls.

*nIDCommandControlsLast*<br/>
[in] Die Zeichenfolgen-ID des letzten Befehls.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt Befehlsschaltflächensteuerelemente mithilfe von Daten aus der Ressourcendatei Ihrer Anwendung. Die Zeichenfolgentabelle in der Ressourcendatei enthält mehrere Zeichenfolgen mit zugeordneten Zeichenfolgen-IDs. Neue Befehlsschaltflächensteuerelemente, die mit dieser Methode hinzugefügt werden, verwenden die Zeichenfolge für die Beschriftung des Steuerelements und die Zeichenfolgen-ID für die ID des Steuerelements. Der ausgewählte Zeichenfolgenbereich wird von *nIDCommandControlsFirst* und *nCommandControlsLast*einschließlich bereitgestellt. Wenn sich ein leerer Eintrag im Bereich befindet, fügt die Methode kein Befehlsschaltflächensteuerelement für diesen Eintrag hinzu.

Standardmäßig sind neue Befehlsschaltflächensteuerelemente aktiviert und erfordern keine Erhöhung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a>CTaskDialog::LoadRadioButtons

Fügt Optionssteuerelemente mithilfe von Daten aus der Zeichenfolgentabelle hinzu.

```
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parameter

*nIDRadioButtonsFirst*<br/>
[in] Die Zeichenfolgen-ID des ersten Optionsfelds.

*nIDRadioButtonsLast*<br/>
[in] Die Zeichenfolgen-ID des letzten Optionsfelds.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt Optionsfelder mithilfe von Daten aus der Ressourcendatei Ihrer Anwendung. Die Zeichenfolgentabelle in der Ressourcendatei enthält mehrere Zeichenfolgen mit zugeordneten Zeichenfolgen-IDs. Neue Optionsfelder, die mit dieser Methode hinzugefügt werden, verwenden die Zeichenfolge für die Beschriftung des Optionsfelds und die Zeichenfolgen-ID für die ID des Optionsfelds. Der ausgewählte Zeichenfolgenbereich wird von *nIDRadioButtonsFirst* und *nRadioButtonsLast*einschließlich bereitgestellt. Wenn sich ein leerer Eintrag im Bereich befindet, fügt die Methode kein Optionsfeld für diesen Eintrag hinzu.

Standardmäßig sind neue Optionsfelder aktiviert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a>CTaskDialog::NavigateTo

Überträgt den `CTaskDialog`Fokus auf eine andere .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parameter

*oTaskDialog*<br/>
[in] Der `CTaskDialog` erhält den Fokus.

### <a name="remarks"></a>Bemerkungen

Diese Methode blendet `CTaskDialog` den aktuellen Ausblenden aus, wenn der *oTaskDialog*angezeigt wird. Der *oTaskDialog* wird an derselben Stelle `CTaskDialog`wie der aktuelle angezeigt.

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a>CTaskDialog::OnCommandControlClick

Das Framework ruft diese Methode auf, wenn der Benutzer auf ein Befehlsschaltflächensteuerelement klickt.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parameter

*nCommandControlID*<br/>
[in] Die ID des Befehlsschaltflächensteuerelements, das der Benutzer ausgewählt hat.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a>CTaskDialog::OnCreate

Das Framework ruft diese Methode `CTaskDialog`auf, nachdem es die erstellt hat.

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a>CTaskDialog::OnDestroy

Das Framework ruft diese Methode unmittelbar `CTaskDialog`auf, bevor sie die zerstört.

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a>CTaskDialog::OnExpandButtonClick

Das Framework ruft diese Methode auf, wenn der Benutzer auf die Erweiterungsschaltfläche klickt.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parameter

*bExpanded*<br/>
[in] Ein Wert ungleich Null gibt an, dass die zusätzlichen Informationen angezeigt werden. 0 gibt an, dass die zusätzlichen Informationen ausgeblendet sind.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a>CTaskDialog::OnHelp

Das Framework ruft diese Methode auf, wenn der Benutzer Hilfe anfordert.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a>CTaskDialog::OnHyperlinkClick

Das Framework ruft diese Methode auf, wenn der Benutzer auf einen Hyperlink klickt.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parameter

*strHref*<br/>
[in] Die Zeichenfolge, die den Hyperlink darstellt.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [ShellExecute auf,](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) bevor sie S_OK zurückgibt.

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a>CTaskDialog::OnInit

Das Framework ruft diese `CTaskDialog` Methode auf, wenn die initialisiert wird.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a>CTaskDialog::OnNavigatePage

Das Framework ruft diese Methode als Reaktion auf die [CTaskDialog::NavigateTo-Methode](#navigateto) auf.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a>CtaskDialog::OnRadioButtonClick

Das Framework ruft diese Methode auf, wenn der Benutzer ein Optionsfeldsteuerelement auswählt.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parameter

*nRadioButtonID*<br/>
[in] Die ID des Optionsfeldsteuerelements, auf das der Benutzer geklickt hat.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a>CTaskDialog::OnTimer

Das Framework ruft diese Methode auf, wenn der Timer abläuft.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parameter

*Ltime*<br/>
[in] Zeit in Millisekunden `CTaskDialog` seit der Erstellung oder dem Zurücksetzen des Timers.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a>CTaskDialog::OnVerificationCheckboxClick

Das Framework ruft diese Methode auf, wenn der Benutzer auf das Kontrollkästchen Überprüfung klickt.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parameter

*bGeprüft*<br/>
[in] TRUE gibt an, dass das Kontrollkästchen Überprüfung aktiviert ist. FALSE gibt an, dass dies nicht der Fall ist.

### <a name="return-value"></a>Rückgabewert

Die Standardimplementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a>CTaskDialog::RemoveAllCommandControls

Entfernt alle Befehlsschaltflächensteuerelemente aus der `CTaskDialog`.

```
void RemoveAllCommandControls();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a>CTaskDialog::RemoveAllRadioButtons

Entfernt alle Optionsfelder aus `CTaskDialog`der .

```
void RemoveAllRadioButtons();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a>CTaskDialog::SetCommandControlOptions

Aktualisiert ein Befehlsschaltflächensteuerelement auf der `CTaskDialog`.

```
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parameter

*nCommandControlID*<br/>
[in] Die ID des zu aktualisierenden Befehlssteuerelements.

*bAktiviert*<br/>
[in] Ein boolescher Parameter, der angibt, ob das angegebene Befehlsschaltflächensteuerelement aktiviert oder deaktiviert ist.

*bRequiresElevation*<br/>
[in] Ein boolescher Parameter, der angibt, ob das angegebene Befehlsschaltflächensteuerelement eine Höhe erfordert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um zu ändern, ob ein Befehlsschaltflächensteuerelement aktiviert ist oder eine Erhöhung erfordert, nachdem es der `CTaskDialog` Klasse hinzugefügt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a>CTaskDialog::SetCommonButtonOptions

Aktualisiert eine Teilmenge der allgemeinen Schaltflächen, die aktiviert werden sollen und eine UAC-Erhöhung erfordern.

```
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parameter

*nDisabledButtonMask*<br/>
[in] Eine Maske für die allgemeinen Schaltflächen, die deaktiviert werden sollen.

*nElevationButtonMask*<br/>
[in] Eine Maske für die allgemeinen Schaltflächen, die eine Erhöhung erfordern.

### <a name="remarks"></a>Bemerkungen

Sie können die allgemeinen Schaltflächen für eine Instanz der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) festlegen, indem Sie den Konstruktor [CTaskDialog::CTaskDialog](#ctaskdialog) und die Methode [CTaskDialog::SetCommonButtons](#setcommonbuttons)verwenden. `CTaskDialog::SetCommonButtonOptions`unterstützt das Hinzufügen neuer allgemeiner Schaltflächen nicht.

Wenn Sie diese Methode verwenden, um eine allgemeine Schaltfläche zu `CTaskDialog`deaktivieren oder zu erhöhen, die für diese nicht verfügbar ist, löst diese Methode mithilfe des [Makros ENSURE](diagnostic-services.md#ensure) eine Ausnahme aus.

Diese Methode aktiviert jede Schaltfläche, `CTaskDialog` die für die, aber nicht in der *nDisabledButtonMask*verfügbar ist, auch wenn sie zuvor deaktiviert wurde. Diese Methode behandelt die Höhe auf ähnliche Weise: Sie zeichnet allgemeine Schaltflächen auf, die keine Erhöhung erfordern, wenn die gemeinsame Schaltfläche verfügbar ist, aber nicht in *nElevationButtonMask*enthalten ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a>CTaskDialog::SetCommonButtons

Fügt dem allgemeine `CTaskDialog`Schaltflächen hinzu.

```
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parameter

*nButtonMask*<br/>
[in] Eine Maske der Schaltflächen, `CTaskDialog`die der hinzugefügt werden sollen.

*nDisabledButtonMask*<br/>
[in] Eine Maske der zu deaktivierenden Schaltflächen.

*nElevationButtonMask*<br/>
[in] Eine Maske der Schaltflächen, die eine Höhe erfordern.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode nicht aufrufen, nachdem `CTaskDialog` das Anzeigefenster für diese Instanz der Klasse erstellt wurde. Wenn Sie dies tun, löst diese Methode eine Ausnahme aus.

Die von *nButtonMask* angezeigten Schaltflächen überschreiben `CTaskDialog`alle allgemeinen Schaltflächen, die zuvor dem hinzugefügt wurden. Nur die in *nButtonMask* angegebenen Schaltflächen sind verfügbar.

Wenn *nDisabledButtonMask* oder *nElevationButtonMask* eine Schaltfläche enthalten, die sich nicht in *nButtonMask*befindet, löst diese Methode mithilfe des [Makros ENSURE](diagnostic-services.md#ensure) eine Ausnahme aus.

Standardmäßig sind alle gängigen Schaltflächen aktiviert und erfordern keine Erhöhung.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a>CTaskDialog::SetContent

Aktualisiert den Inhalt `CTaskDialog`der .

```
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parameter

*strContent*<br/>
[in] Die Zeichenfolge, die dem Benutzer angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Der Inhalt `CTaskDialog` der Klasse ist der Text, der dem Benutzer im Hauptbereich des Dialogfelds angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a>CTaskDialog::SetDefaultCommandControl

Gibt das Standardmäßige Befehlsschaltflächensteuerelement an.

```
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parameter

*nCommandControlID*<br/>
[in] Die ID des Befehlsschaltflächensteuerelements als Standard.

### <a name="remarks"></a>Bemerkungen

Das Standardbefehlsschaltflächensteuerelement ist das `CTaskDialog` Steuerelement, das ausgewählt wird, wenn das dem Benutzer zum ersten Mal angezeigt wird.

Diese Methode löst eine Ausnahme aus, wenn sie das von *nCommandControlID*angegebene Befehlsschaltflächensteuerelement nicht finden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a>CTaskDialog::SetDefaultRadioButton

Gibt das Standardoptionsfeld an.

```
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parameter

*nRadioButtonID*<br/>
[in] Die ID des Optionsfelds, um die Standardeinstellung zu sein.

### <a name="remarks"></a>Bemerkungen

Das Standard-Optionsfeld ist die Schaltfläche, die ausgewählt wird, wenn die `CTaskDialog` dem Benutzer zum ersten Mal angezeigt wird.

Diese Methode löst eine Ausnahme aus, wenn sie das von *nRadioButtonID*angegebene Optionsfeld nicht finden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a>CTaskDialog::SetDialogWidth

Passt die Breite `CTaskDialog`der an.

```
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
[in] Die Breite des Dialogfelds in Pixel.

### <a name="remarks"></a>Bemerkungen

Der Parameter *nWidth* muss größer oder gleich 0 sein. Andernfalls löst diese Methode eine Ausnahme aus.

Wenn *nWidth* auf 0 gesetzt ist, legt diese Methode das Dialogfeld auf die Standardgröße fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a>CTaskDialog::SetExpansionArea

Aktualisiert den Erweiterungsbereich der `CTaskDialog`.

```
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parameter

*strExpandedInformation*<br/>
[in] Die Zeichenfolge, `CTaskDialog` die im Hauptteil des Dialogfelds angezeigt wird, wenn der Benutzer auf die Erweiterungsschaltfläche klickt.

*strCollapsedLabel*<br/>
[in] Die Zeichenfolge, `CTaskDialog` die neben der Erweiterungsschaltfläche angezeigt wird, wenn der erweiterte Bereich reduziert wird.

*strExpandedLabel*<br/>
[in] Die Zeichenfolge, `CTaskDialog` die neben der Erweiterungsschaltfläche angezeigt wird, wenn der erweiterte Bereich angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Der Erweiterungsbereich `CTaskDialog` der Klasse ermöglicht es Ihnen, dem Benutzer zusätzliche Informationen zur Verfügung zu stellen. Der Erweiterungsbereich befindet sich `CTaskDialog`im Hauptteil der , die sich direkt unter der Titel- und Inhaltszeichenfolge befindet.

Wenn `CTaskDialog` der zum ersten Mal angezeigt wird, `strCollapsedLabel` werden die erweiterten Informationen nicht angezeigt und neben der Erweiterungsschaltfläche angezeigt. Wenn der Benutzer auf die `CTaskDialog` Erweiterungsschaltfläche klickt, zeigt die *strExpandedInformation* an und ändert die Bezeichnung in *strExpandedLabel*.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a>CTaskDialog::SetFooterIcon

Aktualisiert das Fußzeilensymbol `CTaskDialog`der .

```
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parameter

*hFooterIcon*<br/>
[in] Das neue Symbol `CTaskDialog`für die .

*lpszFooterIcon*<br/>
[in] Das neue Symbol `CTaskDialog`für die .

### <a name="remarks"></a>Bemerkungen

Das Fußzeilensymbol wird unten in der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)angezeigt. Es kann zugeordneter Fußzeilentext haben. Sie können den Fußzeilentext mit [CTaskDialog::SetFooterText](#setfootertext)ändern.

Diese Methode löst eine Ausnahme mit `CTaskDialog` dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn der angezeigt wird oder der Eingabeparameter NULL ist.

A `CTaskDialog` kann nur `HICON` `LPCWSTR` ein oder als Fußzeilensymbol akzeptieren. Dies wird konfiguriert, indem Die Option TDF_USE_HICON_FOOTER im Konstruktor oder [CTaskDialog::SetOptions](#setoptions)festgelegt wird. Standardmäßig ist `CTaskDialog` der so konfiguriert, dass er als Eingabetyp für das Fußzeilensymbol verwendet `LPCWSTR` wird. Diese Methode generiert eine Ausnahme, wenn Sie versuchen, das Symbol mit dem ungeeigneten Typ festzulegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a>CTaskDialog::SetFooterText

Aktualisiert den Text in der `CTaskDialog`Fußzeile der .

```
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parameter

*strFooterText*<br/>
[in] Der neue Text für die Fußzeile.

### <a name="remarks"></a>Bemerkungen

Das Fußzeilensymbol wird neben dem Fußzeilentext `CTaskDialog`am unteren Rand des angezeigt. Sie können das Fußzeilensymbol mit [CTaskDialog::SetFooterIcon](#setfootericon)ändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a>CTaskDialog::SetMainIcon

Aktualisiert das Hauptsymbol `CTaskDialog`der .

```
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parameter

*hMainIcon*<br/>
[in] Das neue Symbol.

*lpszMainIcon*<br/>
[in] Das neue Symbol.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit `CTaskDialog` dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn der angezeigt wird oder der Eingabeparameter NULL ist.

A `CTaskDialog` kann nur `HICON` `LPCWSTR` ein oder als Hauptsymbol akzeptieren. Sie können dies konfigurieren, indem Sie die Option TDF_USE_HICON_MAIN im Konstruktor oder in der [CTaskDialog::SetOptions-Methode](#setoptions) festlegen. Standardmäßig ist `CTaskDialog` der so konfiguriert, dass er als Eingabetyp für das Hauptsymbol verwendet `LPCWSTR` wird. Diese Methode generiert eine Ausnahme, wenn Sie versuchen, das Symbol mit dem ungeeigneten Typ festzulegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a>CTaskDialog::SetMainInstruction

Aktualisiert die Hauptanweisung `CTaskDialog`der .

```
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parameter

*strInstrInstruktionen*<br/>
[in] Die neue Hauptanweisung.

### <a name="remarks"></a>Bemerkungen

Die Hauptanweisung `CTaskDialog` der Klasse ist Text, der dem Benutzer in einer großen Fettschrift angezeigt wird. Sie befindet sich im Dialogfeld unterhalb der Titelleiste.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a>CTaskDialog::SetOptionen

Konfiguriert die Optionen `CTaskDialog`für die .

```
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parameter

*nOptionFlag*<br/>
[in] Der Satz von Flags, `CTaskDialog`die für die verwendet werden sollen.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode werden alle `CTaskDialog`aktuellen Optionen für die entfernt. Um die aktuellen Optionen beizubehalten, müssen Sie sie zuerst mit [CTaskDialog::GetOptions](#getoptions) abrufen und mit den Optionen kombinieren, die Sie festlegen möchten.

In der folgenden Tabelle sind alle gültigen Optionen aufgeführt.

|||
|-|-|
|TDF_ENABLE_HYPERLINKS|Aktiviert Hyperlinks `CTaskDialog`im .|
|TDF_USE_HICON_MAIN|Konfiguriert die `CTaskDialog` für `HICON` die Verwendung eines für das Hauptsymbol. Die Alternative ist `LPCWSTR`die Verwendung einer .|
|TDF_USE_HICON_FOOTER|Konfiguriert die `CTaskDialog` für `HICON` die Verwendung eines für das Fußzeilensymbol. Die Alternative ist `LPCWSTR`die Verwendung einer .|
|TDF_ALLOW_DIALOG_CANCELLATION|Ermöglicht es dem `CTaskDialog` Benutzer, die über die Tastatur oder über das Symbol in der oberen rechten Ecke des Dialogfelds zu schließen, auch wenn die Schaltfläche **Abbrechen** nicht aktiviert ist. Wenn dieses Flag nicht gesetzt ist und die **Schaltfläche Abbrechen** nicht aktiviert ist, kann der Benutzer das Dialogfeld nicht mit Alt+F4, der Escape-Taste oder der Schaltfläche Schließen der Titelleiste schließen schließen.|
|TDF_USE_COMMAND_LINKS|Konfiguriert die `CTaskDialog` befehlsoptionstastengesteuerten.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Konfiguriert die `CTaskDialog` Befehlsschaltflächensteuerelemente, ohne dass neben dem Steuerelement ein Symbol angezeigt wird. TDF_USE_COMMAND_LINKS überschreibt TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Gibt an, dass der Erweiterungsbereich derzeit erweitert ist.|
|TDF_EXPANDED_BY_DEFAULT|Bestimmt, ob der Erweiterungsbereich standardmäßig erweitert wird.|
|TDF_VERIFICATION_FLAG_CHECKED|Gibt an, dass das Kontrollkästchen Überprüfung derzeit aktiviert ist.|
|TDF_SHOW_PROGRESS_BAR|Konfiguriert die, `CTaskDialog` um eine Fortschrittsleiste anzuzeigen.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Konfiguriert die Fortschrittsleiste als Eine Auswahl-Fortschrittsleiste. Wenn Sie diese Option aktivieren, müssen Sie festlegen, TDF_SHOW_PROGRESS_BAR das erwartete Verhalten aufweisen.|
|TDF_CALLBACK_TIMER|Gibt an, dass das `CTaskDialog` Rückrufintervall auf ca. 200 Millisekunden festgelegt ist.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Konfiguriert die `CTaskDialog` zentrierte in Bezug auf das übergeordnete Fenster. Wenn dieses Flag nicht `CTaskDialog` aktiviert ist, wird das relativ zum Monitor zentriert.|
|TDF_RTL_LAYOUT|Konfiguriert das `CTaskDialog` für ein Leselayout von rechts nach links.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Gibt an, dass kein `CTaskDialog` Optionsfeld ausgewählt ist, wenn das angezeigt wird.|
|TDF_CAN_BE_MINIMIZED|Ermöglicht dem Benutzer, `CTaskDialog`die zu minimieren. Um diese Option `CTaskDialog` zu unterstützen, kann die nicht modal sein. MFC unterstützt diese Option nicht, da MFC `CTaskDialog`keine moduslose unterstützt.|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a>CTaskDialog::SetProgressBarMarquee

Konfiguriert eine Rahmenleiste für `CTaskDialog` die und fügt sie dem Dialogfeld hinzu.

```
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parameter

*bAktiviert*<br/>
[in] TRUE, um die Festzeltleiste zu aktivieren; FALSE, um die Festzeltleiste zu `CTaskDialog`deaktivieren und aus der zu entfernen.

*nMarqueeSpeed*<br/>
[in] Eine ganze Zahl, die die Geschwindigkeit der Festzeltleiste angibt.

### <a name="remarks"></a>Bemerkungen

Die Festzeltleiste wird unter dem `CTaskDialog` Haupttext der Klasse angezeigt.

Verwenden Sie *nMarqueeSpeed,* um die Geschwindigkeit der Festzeltleiste festzulegen. größere Werte weisen auf eine langsamere Geschwindigkeit hin. Mit dem Wert 0 für *nMarqueeSpeed* wird die Festzeltleiste mit der Standardgeschwindigkeit für Windows verschoben.

Diese Methode löst eine Ausnahme mit dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn *nMarqueeSpeed* kleiner als 0 ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a>CTaskDialog::SetProgressBarPosition

Passt die Position der Fortschrittsleiste an.

```
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parameter

*nProgressPos*<br/>
[in] Die Position für die Fortschrittsleiste.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn *nProgressPos* sich nicht im Fortschrittsbalkenbereich befindet. Sie können den Statusleistenbereich mit [CTaskDialog::SetProgressBarRange](#setprogressbarrange)ändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a>CtaskDialog::SetProgressBarRange

Passt den Bereich der Fortschrittsleiste an.

```
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parameter

*nRangeMin*<br/>
[in] Die untere Grenze des Fortschrittsbalkens.

*nRangeMax*<br/>
[in] Die obere Grenze des Fortschrittsbalkens.

### <a name="remarks"></a>Bemerkungen

Die Position des Fortschrittsbalkens ist relativ zu *nRangeMin* und *nRangeMax*. Wenn *nRangeMin* beispielsweise 50 und *nRangeMax* 100 ist, befindet sich eine Position von 75 auf halbem Weg über dem Fortschrittsbalken. Verwenden Sie [CTaskDialog::SetProgressBarPosition,](#setprogressbarposition) um die Position der Fortschrittsleiste festzulegen.

Um die Fortschrittsleiste anzuzeigen, muss die Option TDF_SHOW_PROGRESS_BAR aktiviert sein, und TDF_SHOW_MARQUEE_PROGRESS_BAR darf nicht aktiviert werden. Diese Methode legt automatisch TDF_SHOW_PROGRESS_BAR fest und löscht TDF_SHOW_MARQUEE_PROGRESS_BAR. Verwenden Sie [CTaskDialog::SetOptions,](#setoptions) um die Optionen für diese Instanz der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)manuell zu ändern.

Diese Methode löst eine Ausnahme mit dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn *nRangeMin* nicht kleiner als *nRangeMax*ist. Diese Methode löst auch `CTaskDialog` eine Ausnahme aus, wenn die bereits angezeigt wird und über eine Fortschrittsleiste im Rahmen verfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a>CtaskDialog::SetProgressBarState

Legt den Status der Fortschrittsleiste `CTaskDialog`fest und zeigt sie auf der an.

```
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parameter

*nState*<br/>
[in] Der Status der Fortschrittsleiste. Die möglichen Werte finden Sie im Abschnitt "Bemerkungen".

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit `CTaskDialog` dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn das bereits angezeigt wird und über eine Fortschrittsleiste im Festzelt verfügt.

In der folgenden Tabelle sind die möglichen Werte für *nState*aufgeführt. In all diesen Fällen füllt sich der Fortschrittsbalken mit der regulären Farbe, bis er die angegebene Stoppposition erreicht. An diesem Punkt ändert es die Farbe basierend auf dem Zustand.

|||
|-|-|
|PBST_NORMAL|Nachdem der Fortschrittsbalken `CTaskDialog` gefüllt wurde, ändert der die Farbe des Balkens nicht. Standardmäßig ist die reguläre Farbe grün.|
|PBST_ERROR|Nachdem die Fortschrittsleiste `CTaskDialog` gefüllt wurde, ändert die Farbe des Balkens die Fehlerfarbe. Standardmäßig ist dies rot.|
|PBST_PAUSED|Nachdem die Fortschrittsleiste `CTaskDialog` gefüllt wurde, ändert die Farbe des Balkens in die angehaltene Farbe. Standardmäßig ist dies gelb.|

Sie können festlegen, wo die Fortschrittsleiste mit [CTaskDialog::SetProgressBarPosition](#setprogressbarposition)beendet wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a>CTaskDialog::SetRadioButtonOptions

Aktiviert oder deaktiviert ein Optionsfeld.

```
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parameter

*nRadioButtonID*<br/>
[in] Die ID des Optionsfeldsteuerelements.

*bAktiviert*<br/>
[in] TRUE, um den Optionsfeld zu aktivieren; FALSE, um das Optionsfeld zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn *nRadioButtonID* keine gültige ID für ein Optionsfeld ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a>CTaskDialog::SetVerificationCheckbox

Legt den aktivierten Status des Kontrollkästchens Überprüfung fest.

```
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parameter

*bGeprüft*<br/>
[in] TRUE, damit das Kontrollkästchen Überprüfung `CTaskDialog` aktiviert ist, wenn der angezeigt wird; FALSE, damit das Kontrollkästchen Überprüfung `CTaskDialog` deaktiviert ist, wenn der angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a>CTaskDialog::SetVerificationCheckboxText

Legt den Text fest, der rechts neben dem Kontrollkästchen Überprüfung angezeigt wird.

```
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parameter

*strVerificationText*<br/>
[in] Der Text, der mit dieser Methode neben dem Kontrollkästchen Überprüfung angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem `CTaskDialog` [ENSURE-Makro](diagnostic-services.md#ensure) aus, wenn diese Instanz der Klasse bereits angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a>CTaskDialog::SetWindowTitle

Legt den Titel `CTaskDialog`der fest.

```
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parameter

*strWindowTitle*<br/>
[in] Der neue Titel `CTaskDialog`für die .

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a>CTaskDialog::Dialog anzeigen

Erstellt und `CTaskDialog`zeigt eine an.

```
static INT_PTR ShowDialog(
    const CString& strContent,
    const CString& strMainInstruction,
    const CString& strTitle,
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast,
    int nCommonButtons = TDCBF_YES_BUTTON | TDCBF_NO_BUTTON,
    int nTaskDialogOptions = TDF_ENABLE_HYPERLINKS | TDF_USE_COMMAND_LINKS,
    const CString& strFooter = _T(""));
```

### <a name="parameters"></a>Parameter

*strContent*<br/>
[in] Die Zeichenfolge, die für `CTaskDialog`den Inhalt der verwendet werden soll.

*strMainInstruction*<br/>
[in] Die Hauptanweisung `CTaskDialog`der .

*strTitle*<br/>
[in] Der Titel `CTaskDialog`der .

*nIDCommandControlsFirst*<br/>
[in] Die Zeichenfolgen-ID des ersten Befehls.

*nIDCommandControlsLast*<br/>
[in] Die Zeichenfolgen-ID des letzten Befehls.

*nCommonButtons*<br/>
[in] Eine Maske der Schaltflächen, `CTaskDialog`die der hinzugefügt werden sollen.

*nTaskDialogOptionen*<br/>
[in] Der Satz von Optionen, `CTaskDialog`die für die verwendet werden sollen.

*strFooter*<br/>
[in] Die Zeichenfolge, die als Fußzeile verwendet werden soll.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die der vom Benutzer getroffenen Auswahl entspricht.

### <a name="remarks"></a>Bemerkungen

Mit dieser statischen Methode können `CTaskDialog` Sie eine Instanz `CTaskDialog` der Klasse erstellen, ohne explizit ein Objekt im Code zu erstellen. Da kein `CTaskDialog` Objekt vorhanden ist, können Sie `CTaskDialog` keine anderen Methoden der `CTaskDialog` aufrufen, wenn Sie diese Methode verwenden, um dem Benutzer eine anzuzeigen.

Diese Methode erstellt Befehlsschaltflächensteuerelemente mithilfe von Daten aus der Ressourcendatei Ihrer Anwendung. Die Zeichenfolgentabelle in der Ressourcendatei enthält mehrere Zeichenfolgen mit zugeordneten Zeichenfolgen-IDs. Diese Methode fügt ein Befehlsschaltflächensteuerelement für jeden gültigen Eintrag in der Zeichenfolgentabelle zwischen *nIDCommandControlsFirst* und *nCommandControlsLast*einschließlich hinzu. Für diese Befehlsschaltflächensteuerelemente ist die Zeichenfolge in der Zeichenfolgentabelle die Beschriftung des Steuerelements und die Zeichenfolgen-ID die ID des Steuerelements.

Siehe [CTaskDialog::SetOptions](#setoptions) für eine Liste gültiger Optionen.

Der `CTaskDialog` wird geschlossen, wenn der Benutzer eine gemeinsame Schaltfläche, ein `CTaskDialog`Befehlsverknüpfungssteuerelement oder die schließt. Der Rückgabewert ist der Bezeichner, der angibt, wie der Benutzer das Dialogfeld geschlossen hat.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a>CTaskDialog::TaskDialogCallback

Das Framework ruft diese Methode als Reaktion auf verschiedene Windows-Nachrichten auf.

```
friend:
HRESULT TaskDialogCallback(
    HWND hWnd,
    UINT uNotification,
    WPARAM wParam,
    LPARAM lParam,
    LONG_PTR dwRefData);
```

### <a name="parameters"></a>Parameter

*Hwnd*<br/>
[in] Ein Handle `m_hWnd` für die `CTaskDialog`Struktur für die .

*uBenachrichtigung*<br/>
[in] Der Benachrichtigungscode, der die generierte Nachricht angibt.

*wParam*<br/>
[in] Weitere Informationen zur Nachricht.

*lParam*<br/>
[in] Weitere Informationen zur Nachricht.

*dwRefData*<br/>
[in] Ein Zeiger auf `CTaskDialog` das Objekt, auf das die Rückrufnachricht angewendet wird.

### <a name="return-value"></a>Rückgabewert

Abhängig vom spezifischen Benachrichtigungscode. Weitere Informationen finden Sie im Abschnitt zu den Hinweisen.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung `TaskDialogCallback` von behandelt die spezifische Nachricht und ruft dann die entsprechende On-Methode der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)auf. Ruft z. B. als `TaskDialogCallback` Reaktion auf die TDN_BUTTON_CLICKED Nachricht [CTaskDialog::OnCommandControlClick](#oncommandcontrolclick)auf.

Die Werte für *wParam* und *lParam* hängen von der spezifischen generierten Nachricht ab. Es ist möglich, dass einer oder beide dieser Werte leer sind. In der folgenden Tabelle sind die Standardbenachrichtigungen aufgeführt, die unterstützt werden und welche Werte *wParam* und *lParam* darstellen. Wenn Sie diese Methode in einer abgeleiteten Klasse überschreiben, sollten Sie den Rückrufcode für jede Nachricht in der folgenden Tabelle implementieren.

|Benachrichtigungsnachricht|*wParam* Wert|*lParam* Wert|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Wird nicht verwendet.|Wird nicht verwendet.|
|TDN_NAVIGATED|Wird nicht verwendet.|Wird nicht verwendet.|
|TDN_BUTTON_CLICKED|Die Befehlstastensteuerungs-ID.|Wird nicht verwendet.|
|TDN_HYPERLINK_CLICKED|Wird nicht verwendet.|Eine [LPCWSTR-Struktur,](/windows/win32/WinProg/windows-data-types) die den Link enthält.|
|TDN_TIMER|Zeit in Millisekunden `CTaskDialog` seit der Erstellung oder dem Zurücksetzen des Timers.|Wird nicht verwendet.|
|TDN_DESTROYED|Wird nicht verwendet.|Wird nicht verwendet.|
|TDN_RADIO_BUTTON_CLICKED|Die Options-ID.|Wird nicht verwendet.|
|TDN_DIALOG_CONSTRUCTED|Wird nicht verwendet.|Wird nicht verwendet.|
|TDN_VERIFICATION_CLICKED|1 wenn das Kontrollkästchen aktiviert ist, 0, wenn nicht.|Wird nicht verwendet.|
|TDN_HELP|Wird nicht verwendet.|Wird nicht verwendet.|
|TDN_EXPANDO_BUTTON_CLICKED|0, wenn der Erweiterungsbereich eingestürzt ist; ungleich Null, wenn der Erweiterungstext angezeigt wird.|Wird nicht verwendet.|

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Exemplarische Vorgehensweise: Hinzufügen eines CTaskDialog zu einer Anwendung](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
