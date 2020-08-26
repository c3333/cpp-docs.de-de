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
ms.openlocfilehash: 3fd67eed7e80a2e594710df8ae8bc6fd13f0e96c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837670"
---
# <a name="ctaskdialog-class"></a>CTaskDialog Class

Ein Popupdialogfeld, das wie ein Meldungsfeld funktioniert, aber zusätzliche Informationen für den Benutzer anzeigen kann. `CTaskDialog` enthält auch Funktionen zum Erfassen von Informationen des Benutzers.

## <a name="syntax"></a>Syntax

```
class CTaskDialog : public CObject
```

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[CTaskDialog:: CTaskDialog](#ctaskdialog)|Erstellt ein `CTaskDialog`-Objekt.|

### <a name="methods"></a>Methoden

|Name|Beschreibung|
|-|-|
|[CTaskDialog:: addcommandcontrol](#addcommandcontrol)|Fügt der ein Befehlszeilen-Steuerelement hinzu `CTaskDialog` .|
|[CTaskDialog:: AddRadioButton](#addradiobutton)|Fügt der ein Optionsfeld hinzu `CTaskDialog` .|
|[CTaskDialog:: clickcommandcontrol](#clickcommandcontrol)|Klickt Programm gesteuert auf ein Befehls Schaltflächen-Steuerelement oder eine Schaltfläche|
|[CTaskDialog:: clickradio Button](#clickradiobutton)|Klickt Programm gesteuert auf ein Optionsfeld.|
|[CTaskDialog::D omodal](#domodal)|Zeigt das `CTaskDialog` an.|
|[CTaskDialog:: getcommonbuttoncount](#getcommonbuttoncount)|Ruft die Anzahl der verfügbaren allgemeinen Schaltflächen ab.|
|[CTaskDialog:: getcommonbuttonflag](#getcommonbuttonflag)|Konvertiert eine standardmäßige Windows-Schaltfläche in den allgemeinen Schalt Flächentyp, der der Klasse zugeordnet ist `CTaskDialog` .|
|[CTaskDialog:: getcommonbuttonid](#getcommonbuttonid)|Konvertiert einen der allgemeinen Schaltflächen Typen, die der-Klasse zugeordnet sind `CTaskDialog` , in eine Windows-Standard Schaltfläche.|
|[CTaskDialog:: GetOptions](#getoptions)|Gibt die Optionsflags für dieses zurück `CTaskDialog` .|
|[CTaskDialog:: getselectedcommandcontrolid](#getselectedcommandcontrolid)|Gibt das ausgewählte Befehls Schaltflächen-Steuerelement zurück.|
|[CTaskDialog:: getselectedradiobuttonid](#getselectedradiobuttonid)|Gibt das ausgewählte Optionsfeld zurück.|
|[CTaskDialog:: getverificationcheckboxstate](#getverificationcheckboxstate)|Ruft den Status des Kontrollkästchens für die Überprüfung ab.|
|[CTaskDialog:: iscommandcontrolenabled](#iscommandcontrolenabled)|Bestimmt, ob ein Befehlszeilen-Steuerelement oder eine gemeinsame Schaltfläche aktiviert ist.|
|[CTaskDialog:: isradiobuttonaktivierte](#isradiobuttonenabled)|Bestimmt, ob ein Optionsfeld aktiviert ist.|
|[CTaskDialog:: IsSupported](#issupported)|Bestimmt, ob der Computer, auf dem die Anwendung ausgeführt wird, die unterstützt `CTaskDialog` .|
|[CTaskDialog:: loadcommandcontrols](#loadcommandcontrols)|Fügt Befehlszeilen-Steuerelemente hinzu, indem Daten aus der Zeichen folgen Tabelle verwendet werden.|
|[CTaskDialog:: loadradiobuttons](#loadradiobuttons)|Fügt mithilfe von Daten aus der Zeichen folgen Tabelle Options Felder hinzu.|
|[CTaskDialog:: NavigateTo](#navigateto)|Überträgt den Fokus auf einen anderen `CTaskDialog` .|
|[CTaskDialog:: oncommandcontrolclick](#oncommandcontrolclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf ein Befehls Schaltflächen-Steuerelement klickt.|
|[CTaskDialog:: OnCreate](#oncreate)|Das Framework ruft diese Methode auf, nachdem die erstellt wurde `CTaskDialog` .|
|[CTaskDialog:: OnDestroy](#ondestroy)|Das Framework ruft diese Methode unmittelbar vor dem Zerstören von auf `CTaskDialog` .|
|[CTaskDialog:: onexpandbuttonclick](#onexpandbuttonclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf die Erweiterungs Schaltfläche klickt.|
|[CTaskDialog:: onhelp](#onhelp)|Das Framework ruft diese Methode auf, wenn der Benutzer die Hilfe anfordert.|
|[CTaskDialog:: onhyperlinkclick](#onhyperlinkclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf einen Link klickt.|
|[CTaskDialog:: OnInit](#oninit)|Das Framework ruft diese Methode auf, wenn `CTaskDialog` initialisiert wird.|
|[CTaskDialog:: onnavigatepage](#onnavigatepage)|Das Framework ruft diese Methode auf, wenn der Benutzer den Fokus in Bezug auf Steuerelemente auf dem verschiebt `CTaskDialog` .|
|[CTaskDialog:: onradiobuttonclick](#onradiobuttonclick)|Das Framework ruft diese Methode auf, wenn der Benutzer ein Optionsfeld-Steuerelement auswählt.|
|[CTaskDialog:: OnTimer](#ontimer)|Das Framework ruft diese Methode auf, wenn der Timer abläuft.|
|[CTaskDialog:: onverificationcheckboxclick](#onverificationcheckboxclick)|Das Framework ruft diese Methode auf, wenn der Benutzer auf das Kontrollkästchen Überprüfung klickt.|
|[CTaskDialog:: removeallcommandcontrols](#removeallcommandcontrols)|Entfernt alle Befehls Steuerelemente aus der `CTaskDialog` .|
|[CTaskDialog:: removeallradiobuttons](#removeallradiobuttons)|Entfernt alle Options Felder aus dem `CTaskDialog` .|
|[CTaskDialog:: setcommandcontroloptions](#setcommandcontroloptions)|Aktualisiert ein Befehlszeilen-Steuerelement auf dem `CTaskDialog` .|
|[CTaskDialog:: setcommonbuttonoptions](#setcommonbuttonoptions)|Aktualisiert eine Teilmenge der allgemeinen Schaltflächen, die aktiviert werden sollen, und erfordert eine UAC-Erhöhung.|
|[CTaskDialog:: setcommonbuttons](#setcommonbuttons)|Fügt der allgemeine Schaltflächen hinzu `CTaskDialog` .|
|[CTaskDialog:: setContent](#setcontent)|Aktualisiert den Inhalt von `CTaskDialog` .|
|[CTaskDialog:: setdefaultcommandcontrol](#setdefaultcommandcontrol)|Gibt das Standard Steuerelement der Befehls Schaltfläche an.|
|[CTaskDialog:: setdefaultradiobutton](#setdefaultradiobutton)|Gibt die Standard Schaltfläche an.|
|[CTaskDialog:: setdialogwidth](#setdialogwidth)|Passt die Breite des an `CTaskDialog` .|
|[CTaskDialog:: abtexpansionarea](#setexpansionarea)|Aktualisiert den Erweiterungsbereich von `CTaskDialog` .|
|[CTaskDialog:: setfootericon](#setfootericon)|Aktualisiert das footersymbol für das `CTaskDialog` .|
|[CTaskDialog:: setfootertext](#setfootertext)|Aktualisiert den Text in der Fußzeile von `CTaskDialog` .|
|[CTaskDialog:: setmainicon](#setmainicon)|Aktualisiert das Hauptsymbol von `CTaskDialog` .|
|[CTaskDialog:: setmaininstruction](#setmaininstruction)|Aktualisiert die Haupt Anweisung von `CTaskDialog` .|
|[CTaskDialog::-toptions](#setoptions)|Konfiguriert die Optionen für das `CTaskDialog` .|
|[CTaskDialog:: setprogressbarmarquee](#setprogressbarmarquee)|Konfiguriert eine Marquee-Leiste für den `CTaskDialog` und fügt diese dem Dialogfeld hinzu.|
|[CTaskDialog:: setprogressbarposition](#setprogressbarposition)|Passt die Position der Statusanzeige an.|
|[CTaskDialog:: setprogressbarrange](#setprogressbarrange)|Passt den Bereich der Statusanzeige an.|
|[CTaskDialog:: setprogressbarstate](#setprogressbarstate)|Legt den Status der Statusanzeige fest und zeigt Sie auf dem an `CTaskDialog` .|
|[CTaskDialog:: Setter-Option](#setradiobuttonoptions)|Aktiviert oder deaktiviert ein Optionsfeld.|
|[CTaskDialog:: setverificationcheckbox](#setverificationcheckbox)|Legt den aktivierten Zustand des Kontrollkästchens Überprüfung fest.|
|[CTaskDialog:: setverificationcheckboxtext](#setverificationcheckboxtext)|Legt den Text auf der rechten Seite des Kontrollkästchens fest.|
|[CTaskDialog:: SetWindowTitle](#setwindowtitle)|Legt den Titel des fest `CTaskDialog` .|
|[CTaskDialog:: ShowDialog](#showdialog)|Erstellt eine und zeigt diese an `CTaskDialog` .|
|[CTaskDialog:: taskdialogcallback](#taskdialogcallback)|Das Framework ruft dies als Reaktion auf verschiedene Windows-Meldungen auf.|

### <a name="data-members"></a>Datenelemente

|Name|Beschreibung|
|-|-|
|`m_aButtons`|Das Array von Befehls Schaltflächen-Steuerelementen für den `CTaskDialog` .|
|`m_aRadioButtons`|Das Array von Optionsfeld-Steuerelementen für das-Steuerelement `CTaskDialog` .|
|`m_bVerified`|`TRUE` Gibt an, dass das Kontrollkästchen Überprüfung aktiviert ist. Gibt an, dass `FALSE` es nicht ist.|
|`m_footerIcon`|Das Symbol in der Fußzeile von `CTaskDialog` .|
|`m_hWnd`|Ein Handle für das Fenster für das `CTaskDialog` .|
|`m_mainIcon`|Das Hauptsymbol von `CTaskDialog` .|
|`m_nButtonDisabled`|Eine Maske, die angibt, welche der allgemeinen Schaltflächen deaktiviert sind.|
|`m_nButtonElevation`|Eine Maske, die angibt, welche der allgemeinen Schaltflächen UAC-Rechte erfordern.|
|`m_nButtonId`|Die ID des ausgewählten Befehls Schaltflächen-Steuer Elements.|
|`m_nCommonButton`|Eine Maske, die angibt, welche allgemeinen Schaltflächen auf dem angezeigt werden `CTaskDialog` .|
|`m_nDefaultCommandControl`|Die ID des Befehls Schaltflächen-Steuer Elements, das ausgewählt wird, wenn das `CTaskDialog` angezeigt wird.|
|`m_nDefaultRadioButton`|Die ID des Optionsfeld-Steuer Elements, das ausgewählt wird, wenn das `CTaskDialog` angezeigt wird.|
|`m_nFlags`|Eine Maske, die die Optionen für angibt `CTaskDialog` .|
|`m_nProgressPos`|Die aktuelle Position für die Statusanzeige.  Dabei muss es sich um einen Wert zwischen `m_nProgressRangeMin` und `m_nProgressRangeMax` handeln.|
|`m_nProgressRangeMax`|Der Maximalwert für die Statusanzeige.|
|`m_nProgressRangeMin`|Der minimale Wert für die Statusanzeige.|
|`m_nProgressState`|Der Status der Statusanzeige. Weitere Informationen finden Sie unter [CTaskDialog:: setprogressbarstate](#setprogressbarstate).|
|`m_nRadioId`|Die ID des ausgewählten Optionsfeld-Steuer Elements.|
|`m_nWidth`|Die Breite des `CTaskDialog` in Pixel.|
|`m_strCollapse`|Die Zeichenfolge `CTaskDialog` , die rechts neben dem Erweiterungs Feld angezeigt wird, wenn die erweiterten Informationen ausgeblendet werden.|
|`m_strContent`|Die Inhalts Zeichenfolge des `CTaskDialog` .|
|`m_strExpand`|Die Zeichenfolge `CTaskDialog` , die rechts neben dem Erweiterungs Feld angezeigt wird, wenn die erweiterten Informationen angezeigt werden.|
|`m_strFooter`|Die Fußzeile von `CTaskDialog` .|
|`m_strInformation`|Die erweiterten Informationen für die `CTaskDialog` .|
|`m_strMainInstruction`|Die Haupt Anweisung von `CTaskDialog` .|
|`m_strTitle`|Der Titel der `CTaskDialog`.|
|`m_strVerification`|Die Zeichenfolge, die die `CTaskDialog` rechts neben dem Überprüfungs Kontrollkästchen anzeigt.|

## <a name="remarks"></a>Bemerkungen

Die `CTaskDialog` -Klasse ersetzt das standardmäßige Windows-Meldungs Feld und verfügt über zusätzliche Funktionen, z. b. neue Steuerelemente zum Erfassen von Informationen vom Benutzer. Diese Klasse befindet sich in der MFC-Bibliothek in Visual Studio 2010 und höher. Der `CTaskDialog` ist ab Windows Vista verfügbar. In früheren Versionen von Windows kann das Objekt nicht angezeigt werden `CTaskDialog` . Verwenden `CTaskDialog::IsSupported` Sie, um zur Laufzeit zu bestimmen, ob der aktuelle Benutzer das Aufgaben Dialogfeld anzeigen kann. Das standardmäßige Windows-Meldungs Feld wird weiterhin unterstützt.

`CTaskDialog`Ist nur verfügbar, wenn Sie die Anwendung mithilfe der Unicode-Bibliothek erstellen.

Der `CTaskDialog` verfügt über zwei verschiedene Konstruktoren. Mit einem Konstruktor können Sie zwei Befehls Schaltflächen und maximal sechs reguläre Schaltflächen-Steuerelemente angeben. Nachdem Sie das erstellt haben, können Sie weitere Befehls Schaltflächen hinzufügen `CTaskDialog` . Der zweite Konstruktor unterstützt keine Befehls Schaltflächen, Sie können jedoch eine unbegrenzte Anzahl von regulären Schaltflächen-Steuerelementen hinzufügen. Weitere Informationen zu den Konstruktoren finden Sie unter [CTaskDialog:: CTaskDialog](#ctaskdialog).

In der folgenden Abbildung wird ein Beispiel gezeigt `CTaskDialog` , in dem die Position einiger Steuerelemente veranschaulicht wird.

![Beispiel für CTaskDialog](../../mfc/reference/media/ctaskdialogsample.png "Beispiel für CTaskDialog") <br/>
CTaskDialog-Beispiel

## <a name="requirements"></a>Requirements (Anforderungen)

**Mindestens Erforderliches Betriebssystem:** Windows Vista

**Header:** afxtaskdialog. h

## <a name="ctaskdialogaddcommandcontrol"></a><a name="addcommandcontrol"></a> CTaskDialog:: addcommandcontrol

Fügt der ein neues Befehlszeilen-Steuerelement hinzu `CTaskDialog` .

```cpp
void AddCommandControl(
    int nCommandControlID,
    const CString& strCaption,
    BOOL bEnabled = TRUE,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parameter

*ncommandcontrolid*<br/>
in Die Befehls Steuerungs-Identifikationsnummer.

*Überschrift*<br/>
in Die Zeichenfolge, die dem `CTaskDialog` Benutzer angezeigt wird. Verwenden Sie diese Zeichenfolge, um den Zweck des Befehls zu erläutern.

*benabled*<br/>
in Ein boolescher Parameter, der angibt, ob die neue Schaltfläche aktiviert oder deaktiviert ist.

*brequireselevations*<br/>
in Ein boolescher Parameter, der angibt, ob für einen Befehl eine Erhöhung erforderlich ist.

### <a name="remarks"></a>Bemerkungen

Der `CTaskDialog Class` kann eine unbegrenzte Anzahl von Befehls Schaltflächen-Steuerelementen anzeigen. Wenn jedoch ein Befehlszeilen-Steuerelement `CTaskDialog` anzeigt, können maximal sechs Schaltflächen angezeigt werden. Wenn eine über keine Befehls Schaltflächen-Steuer `CTaskDialog` Elemente verfügt, kann Sie eine unbegrenzte Anzahl von Schaltflächen anzeigen.

Wenn der Benutzer ein Befehls Schaltflächen-Steuerelement auswählt, wird `CTaskDialog` geschlossen. Wenn die Anwendung das Dialogfeld mithilfe von [CTaskDialog::D omodal](#domodal)anzeigt, wird `DoModal` das *ncommandcontrolid* -Element des ausgewählten Befehls Schaltflächen-Steuer Elements zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogaddradiobutton"></a><a name="addradiobutton"></a> CTaskDialog:: AddRadioButton

Fügt der ein Optionsfeld hinzu `CTaskDialog` .

```cpp
void CTaskDialog::AddRadioButton(
    int nRadioButtonID,
    const CString& strCaption,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>Parameter

*nradiobuttonid*<br/>
in Die ID der Options Schaltfläche.

*Überschrift*<br/>
in Die Zeichenfolge, die das `CTaskDialog` neben dem Optionsfeld anzeigt.

*benabled*<br/>
in Ein boolescher Parameter, der angibt, ob das Optionsfeld aktiviert ist.

### <a name="remarks"></a>Bemerkungen

Die Options Felder für die [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) ermöglichen es Ihnen, Informationen vom Benutzer zu erfassen. Verwenden Sie die Funktion " [CTaskDialog:: getselectedradiobuttonid](#getselectedradiobuttonid) ", um zu bestimmen, welches Optionsfeld ausgewählt ist.

`CTaskDialog`Erfordert nicht, dass die *nradiobuttonid* -Parameter für die einzelnen Options Felder eindeutig sind. Allerdings kann es zu unerwartetem Verhalten kommen, wenn Sie für jedes Optionsfeld keinen eindeutigen Bezeichner verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogclickcommandcontrol"></a><a name="clickcommandcontrol"></a> CTaskDialog:: clickcommandcontrol

Klickt Programm gesteuert auf ein Befehls Schaltflächen-Steuerelement oder eine Schaltfläche

```
protected:
void ClickCommandControl(int nCommandControlID) const;
```

### <a name="parameters"></a>Parameter

*ncommandcontrolid*<br/>
in Die Befehls-ID des zu klickenden Steuer Elements.

### <a name="remarks"></a>Bemerkungen

Diese Methode generiert den Windows-Nachrichten TDM_CLICK_BUTTON.

## <a name="ctaskdialogclickradiobutton"></a><a name="clickradiobutton"></a> CTaskDialog:: clickradio Button

Klickt Programm gesteuert auf ein Optionsfeld.

```
protected:
void ClickRadioButton(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parameter

*nradiobuttonid*<br/>
in Die ID des Options Felds, auf das geklickt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode generiert den Windows-Nachrichten TDM_CLICK_RADIO_BUTTON.

## <a name="ctaskdialogctaskdialog"></a><a name="ctaskdialog"></a> CTaskDialog:: CTaskDialog

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

*"straucontent"*<br/>
in Die Zeichenfolge, die für den Inhalt des verwendet werden soll `CTaskDialog` .

*chanmaininstruction*<br/>
in Die Haupt Anweisung von `CTaskDialog` .

*Trend*<br/>
in Der Titel von `CTaskDialog` .

*ncommonbuttons*<br/>
in Eine Maske der allgemeinen Schaltflächen, die der hinzugefügt werden sollen `CTaskDialog` .

*ntaskdialogoptions*<br/>
in Der Satz von Optionen, die für das verwendet werden sollen `CTaskDialog` .

*Fußzeile*<br/>
in Die als Fußzeile zu verwendende Zeichenfolge.

*nidcommandcontrolsfirst*<br/>
in Die Zeichen folgen-ID des ersten Befehls.

*nidcommandcontrolslast*<br/>
in Die Zeichen folgen-ID des letzten Befehls.

### <a name="remarks"></a>Bemerkungen

Es gibt zwei Möglichkeiten, wie Sie Ihrer Anwendung hinzufügen können `CTaskDialog` . Die erste Möglichkeit besteht darin, einen der-Konstruktoren zu verwenden, um einen zu erstellen `CTaskDialog` und ihn mit [CTaskDialog::D omodal](#domodal)anzuzeigen. Die zweite Möglichkeit besteht darin, die statische Funktion [CTaskDialog:: ShowDialog](#showdialog)zu verwenden, die es Ihnen ermöglicht, einen anzuzeigen, `CTaskDialog` ohne explizit ein-Objekt zu erstellen `CTaskDialog` .

Der zweite Konstruktor erstellt Befehlszeilen-Steuerelemente mithilfe von Daten aus der Ressourcen Datei Ihrer Anwendung. Die Zeichen folgen Tabelle in der Ressourcen Datei enthält mehrere Zeichen folgen mit zugeordneten Zeichen folgen-IDs. Diese Methode fügt ein Befehlszeilen-Steuerelement für jeden gültigen Eintrag in der Zeichen folgen Tabelle zwischen " *nidcommandcontrolsfirst* " und " *ncommandcontrolslast*, einschließlich", hinzu. Für diese Befehlszeilen-Steuerelemente ist die Zeichenfolge in der Zeichen folgen Tabelle die Beschriftung des Steuer Elements, und die Zeichen folgen-ID ist die ID des Steuer Elements.

Eine Liste gültiger Optionen finden Sie unter [CTaskDialog:: Setter](#setoptions) .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogdomodal"></a><a name="domodal"></a> CTaskDialog::D omodal

Zeigt die an `CTaskDialog` und macht Sie modal.

```
INT_PTR DoModal (HWND hParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parameter

*hParent*<br/>
in Das übergeordnete Fenster für das `CTaskDialog` .

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die der vom Benutzer vorgenommenen Auswahl entspricht.

### <a name="remarks"></a>Bemerkungen

Zeigt diese Instanz von [CTaskDialog](../../mfc/reference/ctaskdialog-class.md)an. Die Anwendung wartet dann darauf, dass der Benutzer das Dialogfeld schließt.

Das `CTaskDialog` schließt, wenn der Benutzer eine gemeinsame Schaltfläche, ein Befehls Verknüpfungs Steuerelement oder den schließt `CTaskDialog` . Der Rückgabewert ist der Bezeichner, der angibt, wie das Dialogfeld vom Benutzer geschlossen wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetcommonbuttoncount"></a><a name="getcommonbuttoncount"></a> CTaskDialog:: getcommonbuttoncount

Ruft die Anzahl der allgemeinen Schaltflächen ab.

```
int GetCommonButtonCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der verfügbaren allgemeinen Schaltflächen.

### <a name="remarks"></a>Bemerkungen

Die Standard Schaltflächen sind die Standard Schaltflächen, die Sie für " [CTaskDialog:: CTaskDialog](#ctaskdialog)" bereitstellen. Die [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) zeigt die Schaltflächen unten im Dialogfeld an.

Die Aufzählungs Liste der Schaltflächen wird in "kommctrl. h" bereitgestellt.

## <a name="ctaskdialoggetcommonbuttonflag"></a><a name="getcommonbuttonflag"></a> CTaskDialog:: getcommonbuttonflag

Konvertiert eine standardmäßige Windows-Schaltfläche in den allgemeinen Schalt Flächentyp, der der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)zugeordnet ist

```
int GetCommonButtonFlag(int nButtonId) const;
```

### <a name="parameters"></a>Parameter

*nbuttonid*<br/>
in Der standardmäßige Windows-Schaltflächen Wert.

### <a name="return-value"></a>Rückgabewert

Der Wert der entsprechenden `CTaskDialog` allgemeinen Schaltfläche. Wenn keine entsprechende allgemeine Schaltfläche vorhanden ist, gibt diese Methode 0 zurück.

## <a name="ctaskdialoggetcommonbuttonid"></a><a name="getcommonbuttonid"></a> CTaskDialog:: getcommonbuttonid

Konvertiert einen der allgemeinen Schaltflächen Typen, die der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) zugeordnet sind, in eine Windows-Standard Schaltfläche.

```
int GetCommonButtonId(int nFlag);
```

### <a name="parameters"></a>Parameter

*Kennzeichnung*<br/>
in Der allgemeine Schalt Flächentyp, der der-Klasse zugeordnet ist `CTaskDialog` .

### <a name="return-value"></a>Rückgabewert

Der Wert der entsprechenden Windows-Standard Schaltfläche. Wenn keine entsprechende Windows-Schaltfläche vorhanden ist, gibt die Methode 0 zurück.

## <a name="ctaskdialoggetoptions"></a><a name="getoptions"></a> CTaskDialog:: GetOptions

Gibt die Optionsflags für dieses zurück `CTaskDialog` .

```
int GetOptions() const;
```

### <a name="return-value"></a>Rückgabewert

Die Flags für den `CTaskDialog` .

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu den Optionen, die für die [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)verfügbar sind, finden Sie unter [CTaskDialog:: Setter](#setoptions).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialoggetselectedcommandcontrolid"></a><a name="getselectedcommandcontrolid"></a> CTaskDialog:: getselectedcommandcontrolid

Gibt das ausgewählte Befehls Schaltflächen-Steuerelement zurück.

```
int GetSelectedCommandControlID() const;
```

### <a name="return-value"></a>Rückgabewert

Die ID des derzeit ausgewählten Befehls Schaltflächen-Steuer Elements.

### <a name="remarks"></a>Bemerkungen

Sie müssen diese Methode nicht verwenden, um die ID der Befehls Schaltfläche abzurufen, die der Benutzer ausgewählt hat. Diese ID wird entweder von [CTaskDialog::D omodal](#domodal) oder [CTaskDialog:: ShowDialog](#showdialog)zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialoggetselectedradiobuttonid"></a><a name="getselectedradiobuttonid"></a> CTaskDialog:: getselectedradiobuttonid

Gibt das ausgewählte Optionsfeld zurück.

```
int GetSelectedRadioButtonID() const;
```

### <a name="return-value"></a>Rückgabewert

Die ID des ausgewählten Options Felds.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode verwenden, wenn der Benutzer das Dialogfeld schließt, um das ausgewählte Optionsfeld abzurufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialoggetverificationcheckboxstate"></a><a name="getverificationcheckboxstate"></a> CTaskDialog:: getverificationcheckboxstate

Ruft den Status des Kontrollkästchens für die Überprüfung ab.

```
BOOL GetVerificationCheckboxState() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Kontrollkästchen aktiviert ist, false, wenn dies nicht der Fall ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogiscommandcontrolenabled"></a><a name="iscommandcontrolenabled"></a> CTaskDialog:: iscommandcontrolenabled

Bestimmt, ob ein Befehlszeilen-Steuerelement oder eine Schaltfläche aktiviert ist.

```
BOOL IsCommandControlEnabled(int nCommandControlID) const;
```

### <a name="parameters"></a>Parameter

*ncommandcontrolid*<br/>
in Die ID des Befehls Schaltflächen-Steuer Elements oder der zu testenden Schaltfläche.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Steuerelement aktiviert ist, false, wenn es nicht ist.

### <a name="remarks"></a>Bemerkungen

Mit dieser Methode können Sie die Verfügbarkeit der Befehls Schaltflächen-Steuerelemente und der allgemeinen Schaltflächen der `CTaskDialog` Klasse * ermitteln.

Wenn *ncommandcontrolid* kein gültiger Bezeichner für eine gemeinsame `CTaskDialog` Schaltfläche oder ein Befehls Schaltflächen-Steuerelement ist, löst diese Methode eine Ausnahme aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogisradiobuttonenabled"></a><a name="isradiobuttonenabled"></a> CTaskDialog:: isradiobuttonaktivierte

Bestimmt, ob ein Optionsfeld aktiviert ist.

```
BOOL IsRadioButtonEnabled(int nRadioButtonID) const;
```

### <a name="parameters"></a>Parameter

*nradiobuttonid*<br/>
in Die ID des zu testenden Options Felds.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Options Schaltfläche aktiviert ist, false, wenn dies nicht der Fall ist.

### <a name="remarks"></a>Bemerkungen

Wenn *nradiobuttonid* kein gültiger Bezeichner für ein Optionsfeld ist, löst diese Methode eine Ausnahme aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogissupported"></a><a name="issupported"></a> CTaskDialog:: IsSupported

Bestimmt, ob der Computer, auf dem die Anwendung ausgeführt wird, die unterstützt `CTaskDialog` .

```
static BOOL IsSupported();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Computer die unterstützt `CTaskDialog` . Andernfalls false.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um zur Laufzeit zu bestimmen, ob der Computer, auf dem Ihre Anwendung ausgeführt wird, die Klasse unterstützt `CTaskDialog` . Wenn der Computer das nicht unterstützt `CTaskDialog` , sollten Sie eine weitere Methode zum Kommunizieren von Informationen an den Benutzer bereitstellen. Die Anwendung stürzt ab, wenn versucht wird, einen `CTaskDialog` auf einem Computer zu verwenden, der die-Klasse nicht unterstützt `CTaskDialog` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogloadcommandcontrols"></a><a name="loadcommandcontrols"></a> CTaskDialog:: loadcommandcontrols

Fügt Befehlszeilen-Steuerelemente hinzu, indem Daten aus der Zeichen folgen Tabelle verwendet werden.

```cpp
void LoadCommandControls(
    int nIDCommandControlsFirst,
    int nIDCommandControlsLast);
```

### <a name="parameters"></a>Parameter

*nidcommandcontrolsfirst*<br/>
in Die Zeichen folgen-ID des ersten Befehls.

*nidcommandcontrolslast*<br/>
in Die Zeichen folgen-ID des letzten Befehls.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt Befehls Schaltflächen-Steuerelemente, indem Sie Daten aus der Ressourcen Datei Ihrer Anwendung verwendet. Die Zeichen folgen Tabelle in der Ressourcen Datei enthält mehrere Zeichen folgen mit zugeordneten Zeichen folgen-IDs. Neue Befehlszeilen Steuerelemente, die mit dieser Methode hinzugefügt wurden, verwenden die Zeichenfolge für die Beschriftung des Steuer Elements und die Zeichen folgen-ID für die ID des Steuer Elements Der ausgewählte Bereich von Zeichen folgen wird von " *nidcommandcontrolsfirst* " und " *ncommandcontrolslast*" (einschließlich) bereitgestellt. Wenn ein leerer Eintrag im Bereich vorhanden ist, wird von der Methode kein Befehlszeilen-Steuerelement für diesen Eintrag hinzugefügt.

Standardmäßig sind neue Befehls Schaltflächen-Steuerelemente aktiviert, und es ist keine Erhöhung der Rechte erforderlich.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogloadradiobuttons"></a><a name="loadradiobuttons"></a> CTaskDialog:: loadradiobuttons

Fügt Optionsfeld-Steuerelemente hinzu, indem Daten aus der Zeichen folgen Tabelle verwendet werden.

```cpp
void LoadRadioButtons(
    int nIDRadioButtonsFirst,
    int nIDRadioButtonsLast);
```

### <a name="parameters"></a>Parameter

*nidradiobuttonsfirst*<br/>
in Die Zeichen folgen-ID des ersten Options Felds.

*nidradiobuttonslast*<br/>
in Die Zeichen folgen-ID des letzten Options Felds.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt Options Felder mithilfe von Daten aus der Ressourcen Datei Ihrer Anwendung. Die Zeichen folgen Tabelle in der Ressourcen Datei enthält mehrere Zeichen folgen mit zugeordneten Zeichen folgen-IDs. Neue Options Felder, die mithilfe dieser Methode hinzugefügt wurden, verwenden die Zeichenfolge für die Beschriftung des Options Felds und die Zeichen folgen-ID für die ID des Options Felds. Der ausgewählte Bereich von Zeichen folgen wird von " *nidradiobuttonsfirst* " und " *nradiobuttonslast*" (einschließlich) bereitgestellt. Wenn ein leerer Eintrag im Bereich vorhanden ist, wird von der Methode kein Optionsfeld für diesen Eintrag hinzugefügt.

Standardmäßig sind neue Options Felder aktiviert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialognavigateto"></a><a name="navigateto"></a> CTaskDialog:: NavigateTo

Überträgt den Fokus auf einen anderen `CTaskDialog` .

```
protected:
void NavigateTo(CTaskDialog& oTaskDialog) const;
```

### <a name="parameters"></a>Parameter

*otaskdialog*<br/>
in Das `CTaskDialog` , das den Fokus erhält.

### <a name="remarks"></a>Bemerkungen

Diese Methode blendet den aktuellen aus, `CTaskDialog` Wenn er das *otaskdialog-Dialog*Feld anzeigt. Der *otaskdialog* wird am gleichen Speicherort wie der aktuelle angezeigt `CTaskDialog` .

## <a name="ctaskdialogoncommandcontrolclick"></a><a name="oncommandcontrolclick"></a> CTaskDialog:: oncommandcontrolclick

Das Framework ruft diese Methode auf, wenn der Benutzer auf ein Befehls Schaltflächen-Steuerelement klickt.

```
virtual HRESULT OnCommandControlClick(int nCommandControlID);
```

### <a name="parameters"></a>Parameter

*ncommandcontrolid*<br/>
in Die ID des Befehls Schaltflächen-Steuer Elements, das vom Benutzer ausgewählt wurde.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogoncreate"></a><a name="oncreate"></a> CTaskDialog:: OnCreate

Das Framework ruft diese Methode auf, nachdem die erstellt wurde `CTaskDialog` .

```
virtual HRESULT OnCreate();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogondestroy"></a><a name="ondestroy"></a> CTaskDialog:: OnDestroy

Das Framework ruft diese Methode unmittelbar vor dem Zerstören von auf `CTaskDialog` .

```
virtual HRESULT OnDestroy();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonexpandbuttonclick"></a><a name="onexpandbuttonclick"></a> CTaskDialog:: onexpandbuttonclick

Das Framework ruft diese Methode auf, wenn der Benutzer auf die Erweiterungs Schaltfläche klickt.

```
virtual HRESULT OnExpandButtonClicked(BOOL bExpanded);
```

### <a name="parameters"></a>Parameter

*bexpanded*<br/>
in Ein Wert ungleich 0 (null) gibt an, dass zusätzliche Informationen angezeigt werden. 0 gibt an, dass die zusätzlichen Informationen ausgeblendet sind.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonhelp"></a><a name="onhelp"></a> CTaskDialog:: onhelp

Das Framework ruft diese Methode auf, wenn der Benutzer die Hilfe anfordert.

```
virtual HRESULT OnHelp();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonhyperlinkclick"></a><a name="onhyperlinkclick"></a> CTaskDialog:: onhyperlinkclick

Das Framework ruft diese Methode auf, wenn der Benutzer auf einen Link klickt.

```
virtual HRESULT OnHyperlinkClick(const CString& strHref);
```

### <a name="parameters"></a>Parameter

*"strauhref"*<br/>
in Die Zeichenfolge, die den Hyperlink darstellt.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode ruft [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) auf, bevor S_OK zurückgegeben wird.

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogoninit"></a><a name="oninit"></a> CTaskDialog:: OnInit

Das Framework ruft diese Methode auf, wenn `CTaskDialog` initialisiert wird.

```
virtual HRESULT OnInit();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonnavigatepage"></a><a name="onnavigatepage"></a> CTaskDialog:: onnavigatepage

Das Framework ruft diese Methode als Reaktion auf die [CTaskDialog:: NavigateTo](#navigateto) -Methode auf.

```
virtual HRESULT OnNavigatePage();
```

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonradiobuttonclick"></a><a name="onradiobuttonclick"></a> CTaskDialog:: onradiobuttonclick

Das Framework ruft diese Methode auf, wenn der Benutzer ein Optionsfeld-Steuerelement auswählt.

```
virtual HRESULT OnRadioButtonClick(int nRadioButtonID);
```

### <a name="parameters"></a>Parameter

*nradiobuttonid*<br/>
in Die ID des Optionsfeld-Steuer Elements, auf das der Benutzer geklickt hat.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogontimer"></a><a name="ontimer"></a> CTaskDialog:: OnTimer

Das Framework ruft diese Methode auf, wenn der Timer abläuft.

```
virtual HRESULT OnTimer(long lTime);
```

### <a name="parameters"></a>Parameter

*lTime*<br/>
in Die Zeit in Millisekunden seit der `CTaskDialog` Erstellung oder der zurück setzung des Timers.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogonverificationcheckboxclick"></a><a name="onverificationcheckboxclick"></a> CTaskDialog:: onverificationcheckboxclick

Das Framework ruft diese Methode auf, wenn der Benutzer auf das Kontrollkästchen Überprüfung klickt.

```
virtual HRESULT OnVerificationCheckboxClick(BOOL bChecked);
```

### <a name="parameters"></a>Parameter

*bCheck*<br/>
in TRUE gibt an, dass das Kontrollkästchen Überprüfung aktiviert ist. FALSE gibt an, dass es nicht ist.

### <a name="return-value"></a>Rückgabewert

Die Standard Implementierung gibt S_OK zurück.

### <a name="remarks"></a>Bemerkungen

Überschreiben diese Methode in einer abgeleiteten Klasse, um benutzerdefiniertes Verhalten zu implementieren.

## <a name="ctaskdialogremoveallcommandcontrols"></a><a name="removeallcommandcontrols"></a> CTaskDialog:: removeallcommandcontrols

Entfernt alle Befehlszeilen-Steuerelemente aus der `CTaskDialog` .

```cpp
void RemoveAllCommandControls();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogremoveallradiobuttons"></a><a name="removeallradiobuttons"></a> CTaskDialog:: removeallradiobuttons

Entfernt alle Options Felder aus dem `CTaskDialog` .

```cpp
void RemoveAllRadioButtons();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetcommandcontroloptions"></a><a name="setcommandcontroloptions"></a> CTaskDialog:: setcommandcontroloptions

Aktualisiert ein Befehlszeilen-Steuerelement auf dem `CTaskDialog` .

```cpp
void SetCommandControlOptions(
    int nCommandControlID,
    BOOL bEnabled,
    BOOL bRequiresElevation = FALSE);
```

### <a name="parameters"></a>Parameter

*ncommandcontrolid*<br/>
in Die ID des zu aktualisierenden Befehls Steuer Elements.

*benabled*<br/>
in Ein boolescher Parameter, der angibt, ob das angegebene Befehls Schaltflächen-Steuerelement aktiviert oder deaktiviert ist.

*brequireselevations*<br/>
in Ein boolescher Parameter, der angibt, ob das angegebene Befehls Schaltflächen-Steuerelement eine Erhöhung erfordert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um zu ändern, ob ein Befehlszeilen-Steuerelement aktiviert ist oder eine Rechte Erweiterung erfordert, nachdem es der Klasse hinzugefügt wurde `CTaskDialog` .

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetcommonbuttonoptions"></a><a name="setcommonbuttonoptions"></a> CTaskDialog:: setcommonbuttonoptions

Aktualisiert eine Teilmenge der allgemeinen Schaltflächen, die aktiviert werden sollen, und erfordert eine UAC-Erhöhung.

```cpp
void SetCommonButtonOptions(
    int nDisabledButtonMask,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parameter

*ndisabledbuttonmask*<br/>
in Eine Maske für die zu deaktivierenden allgemeinen Schaltflächen.

*Nelke*<br/>
in Eine Maske für die allgemeinen Schaltflächen, die eine Rechte Erweiterung erfordern.

### <a name="remarks"></a>Bemerkungen

Sie können die allgemeinen Schaltflächen, die für eine Instanz der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md) verfügbar sind, mithilfe des Konstruktors [CTaskDialog:: CTaskDialog](#ctaskdialog) und der [CTaskDialog:: setcommonbuttons](#setcommonbuttons)-Methode festlegen. `CTaskDialog::SetCommonButtonOptions` unterstützt nicht das Hinzufügen von neuen allgemeinen Schaltflächen.

Wenn Sie diese Methode verwenden, um eine gemeinsame Schaltfläche zu deaktivieren oder zu erhöhen, die für diese nicht verfügbar ist `CTaskDialog` , löst diese Methode eine Ausnahme mithilfe des [sicher](diagnostic-services.md#ensure) -Makros aus.

Diese Methode aktiviert jede Schaltfläche, die für verfügbar ist, `CTaskDialog` aber nicht in der *ndisabledbuttonmask*, auch wenn Sie zuvor deaktiviert war. Diese Methode behandelt die Erhöhung der Rechte auf ähnliche Weise: Sie zeichnet allgemeine Schaltflächen als nicht benötigte Rechte auf, wenn die Schaltfläche allgemein verfügbar ist, aber nicht in *nelevationbuttonmask*enthalten ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcommonbuttons"></a><a name="setcommonbuttons"></a> CTaskDialog:: setcommonbuttons

Fügt der allgemeine Schaltflächen hinzu `CTaskDialog` .

```cpp
void SetCommonButtons(
    int nButtonMask,
    int nDisabledButtonMask = 0,
    int nElevationButtonMask = 0);
```

### <a name="parameters"></a>Parameter

*nbuttonmask*<br/>
in Eine Maske der Schaltflächen, die der hinzugefügt werden sollen `CTaskDialog` .

*ndisabledbuttonmask*<br/>
in Eine Maske der zu deaktivierenden Schaltflächen.

*Nelke*<br/>
in Eine Maske der Schaltflächen, die eine Rechte Erweiterung erfordern.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode nicht aufrufen, nachdem das Anzeige Fenster für diese Instanz der- `CTaskDialog` Klasse erstellt wurde. Wenn Sie dies tun, löst diese Methode eine Ausnahme aus.

Die durch *nbuttonmask* gekennzeichneten Schaltflächen überschreiben alle allgemeinen Schaltflächen, die zuvor zu hinzugefügt wurden `CTaskDialog` . Nur die in *nbuttonmask* aufgeführten Schaltflächen sind verfügbar.

Wenn entweder *ndisabledbuttonmask* oder *nelevationbuttonmask* eine Schaltfläche enthalten, die nicht in *nbuttonmask*enthalten ist, löst diese Methode eine Ausnahme mithilfe des [sicher](diagnostic-services.md#ensure) -Makros aus.

Standardmäßig sind alle allgemeinen Schaltflächen aktiviert, und es ist keine Erhöhung der Rechte erforderlich.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#6](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_6.cpp)]

## <a name="ctaskdialogsetcontent"></a><a name="setcontent"></a> CTaskDialog:: setContent

Aktualisiert den Inhalt von `CTaskDialog` .

```cpp
void SetContent(const CString& strContent);
```

### <a name="parameters"></a>Parameter

*"straucontent"*<br/>
in Die Zeichenfolge, die dem Benutzer angezeigt werden soll.

### <a name="remarks"></a>Bemerkungen

Der Inhalt der- `CTaskDialog` Klasse ist der Text, der dem Benutzer im Hauptabschnitt des Dialog Felds angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetdefaultcommandcontrol"></a><a name="setdefaultcommandcontrol"></a> CTaskDialog:: setdefaultcommandcontrol

Gibt das Standard Steuerelement der Befehls Schaltfläche an.

```cpp
void SetDefaultCommandControl(int nCommandControlID);
```

### <a name="parameters"></a>Parameter

*ncommandcontrolid*<br/>
in Die ID des Befehls Schaltflächen-Steuer Elements, das die Standardeinstellung ist.

### <a name="remarks"></a>Bemerkungen

Das Standard Befehls Schaltflächen-Steuerelement ist das Steuerelement, das ausgewählt wird, wenn das dem `CTaskDialog` Benutzer zum ersten Mal angezeigt wird.

Diese Methode löst eine Ausnahme aus, wenn das von *ncommandcontrolid*angegebene Befehls Schaltflächen Steuerelement nicht gefunden werden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#2](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_1.cpp)]

## <a name="ctaskdialogsetdefaultradiobutton"></a><a name="setdefaultradiobutton"></a> CTaskDialog:: setdefaultradiobutton

Gibt die Standard Schaltfläche an.

```cpp
void SetDefaultRadioButton(int nRadioButtonID);
```

### <a name="parameters"></a>Parameter

*nradiobuttonid*<br/>
in Die ID des Options Felds, das der Standardwert ist.

### <a name="remarks"></a>Bemerkungen

Das Optionsfeld Standard ist die Schaltfläche, die ausgewählt wird, wenn der `CTaskDialog` Benutzer zum ersten Mal angezeigt wird.

Diese Methode löst eine Ausnahme aus, wenn Sie das durch *nradiobuttonid*angegebene Optionsfeld nicht finden kann.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetdialogwidth"></a><a name="setdialogwidth"></a> CTaskDialog:: setdialogwidth

Passt die Breite des an `CTaskDialog` .

```cpp
void SetDialogWidth(int nWidth = 0);
```

### <a name="parameters"></a>Parameter

*nwidth*<br/>
in Die Breite des Dialog Felds in Pixel.

### <a name="remarks"></a>Bemerkungen

Der *nwidth* -Parameter muss größer oder gleich 0 sein. Andernfalls löst diese Methode eine Ausnahme aus.

Wenn *nwidth* auf 0 festgelegt ist, legt diese Methode das Dialogfeld auf die Standardgröße fest.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetexpansionarea"></a><a name="setexpansionarea"></a> CTaskDialog:: abtexpansionarea

Aktualisiert den Erweiterungsbereich von `CTaskDialog` .

```cpp
void SetExpansionArea(
    const CString& strExpandedInformation,
    const CString& strCollapsedLabel = _T(""),
    const CString& strExpandedLabel = _T(""));
```

### <a name="parameters"></a>Parameter

*strexpandedinformation*<br/>
in Die Zeichenfolge, die `CTaskDialog` im Hauptteil des Dialog Felds angezeigt wird, wenn der Benutzer auf die Erweiterungs Schaltfläche klickt.

*"Strauch Bezeichnung"*<br/>
in Die Zeichenfolge, die das `CTaskDialog` neben der Erweiterungs Schaltfläche anzeigt, wenn der erweiterte Bereich reduziert wird.

*strexpandedlabel*<br/>
in Die Zeichenfolge, die das `CTaskDialog` neben der Erweiterungs Schaltfläche anzeigt, wenn der erweiterte Bereich angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Der Erweiterungsbereich der- `CTaskDialog` Klasse ermöglicht es Ihnen, zusätzliche Informationen für den Benutzer bereitzustellen. Der Erweiterungsbereich befindet sich im Hauptteil des `CTaskDialog` , der sich direkt unterhalb des Titels und der Inhalts Zeichenfolge befindet.

Wenn das zum `CTaskDialog` ersten Mal angezeigt wird, werden die erweiterten Informationen nicht angezeigt, und Sie werden `strCollapsedLabel` neben der Erweiterungs Schaltfläche angezeigt. Wenn der Benutzer auf die Erweiterungs Schaltfläche klickt, wird `CTaskDialog` *strexpandedinformation* angezeigt, und die Bezeichnung wird in *strexpandedlabel*geändert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootericon"></a><a name="setfootericon"></a> CTaskDialog:: setfootericon

Aktualisiert das footersymbol von `CTaskDialog` .

```cpp
void SetFooterIcon(HICON hFooterIcon);
void SetFooterIcon(LPCWSTR lpszFooterIcon);
```

### <a name="parameters"></a>Parameter

*hfootericon*<br/>
in Das neue Symbol für das `CTaskDialog` .

*lpszfootericon*<br/>
in Das neue Symbol für das `CTaskDialog` .

### <a name="remarks"></a>Bemerkungen

Das footersymbol wird am Ende der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)angezeigt. Ihm kann der FooterText zugeordnet werden. Sie können den FooterText mit [CTaskDialog:: setfootertext](#setfootertext)ändern.

Diese Methode löst eine Ausnahme mit dem Makro [sicher](diagnostic-services.md#ensure) aus, wenn der `CTaskDialog` angezeigt wird oder der Eingabeparameter NULL ist.

Ein-Zeichen `CTaskDialog` kann nur ein- `HICON` oder `LPCWSTR` als footersymbol akzeptieren. Dies wird konfiguriert, indem die Option TDF_USE_HICON_FOOTER im Konstruktor oder [CTaskDialog:: Setter](#setoptions)festgelegt wird. Standardmäßig `CTaskDialog` ist so konfiguriert, `LPCWSTR` dass als Eingabetyp für das footersymbol verwendet wird. Diese Methode generiert eine Ausnahme, wenn Sie versuchen, das Symbol mit dem unzulässigen Typ festzulegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetfootertext"></a><a name="setfootertext"></a> CTaskDialog:: setfootertext

Aktualisiert den Text in der Fußzeile von `CTaskDialog` .

```cpp
void SetFooterText(const CString& strFooterText);
```

### <a name="parameters"></a>Parameter

*"strintertext"*<br/>
in Der neue Text für die Fußzeile.

### <a name="remarks"></a>Bemerkungen

Das footersymbol wird neben dem FooterText am unteren Rand des angezeigt `CTaskDialog` . Sie können das footersymbol mit [CTaskDialog:: setfootericon](#setfootericon)ändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmainicon"></a><a name="setmainicon"></a> CTaskDialog:: setmainicon

Aktualisiert das Hauptsymbol von `CTaskDialog` .

```cpp
void SetMainIcon(HICON hMainIcon);
void SetMainIcon(LPCWSTR lpszMainIcon);
```

### <a name="parameters"></a>Parameter

*hmainicon*<br/>
in Das neue Symbol.

*lpszmainicon*<br/>
in Das neue Symbol.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem Makro [sicher](diagnostic-services.md#ensure) aus, wenn der `CTaskDialog` angezeigt wird oder der Eingabeparameter NULL ist.

Ein `CTaskDialog` kann nur ein `HICON` oder ein `LPCWSTR` Hauptsymbol akzeptieren. Sie können dies konfigurieren, indem Sie die TDF_USE_HICON_MAIN-Option im Konstruktor oder in der [CTaskDialog:: Setter](#setoptions) -Methode festlegen. Standardmäßig `CTaskDialog` ist so konfiguriert, `LPCWSTR` dass als Eingabetyp für das Hauptsymbol verwendet wird. Diese Methode generiert eine Ausnahme, wenn Sie versuchen, das Symbol mit dem unzulässigen Typ festzulegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetmaininstruction"></a><a name="setmaininstruction"></a> CTaskDialog:: setmaininstruction

Aktualisiert die Haupt Anweisung von `CTaskDialog` .

```cpp
void SetMainInstruction(const CString& strInstructions);
```

### <a name="parameters"></a>Parameter

*~ Instructions*<br/>
in Die neue Haupt Anweisung.

### <a name="remarks"></a>Bemerkungen

Die Haupt Anweisung der- `CTaskDialog` Klasse ist Text, der dem Benutzer in einer großen Fett Schrift angezeigt wird. Sie befindet sich im Dialogfeld unterhalb der Titelleiste.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetoptions"></a><a name="setoptions"></a> CTaskDialog::-toptions

Konfiguriert die Optionen für das `CTaskDialog` .

```cpp
void SetOptions(int nOptionFlag);
```

### <a name="parameters"></a>Parameter

*noptionflag*<br/>
in Der Satz von Flags, die für den verwendet werden sollen `CTaskDialog` .

### <a name="remarks"></a>Bemerkungen

Diese Methode löscht alle aktuellen Optionen für das `CTaskDialog` . Um die aktuellen Optionen beizubehalten, müssen Sie Sie zuerst mit [CTaskDialog:: GetOptions](#getoptions) abrufen und Sie mit den Optionen kombinieren, die Sie festlegen möchten.

In der folgenden Tabelle sind alle gültigen Optionen aufgeführt.

|Name|Beschreibung|
|-|-|
|TDF_ENABLE_HYPERLINKS|Aktiviert Hyperlinks in `CTaskDialog` .|
|TDF_USE_HICON_MAIN|Konfiguriert den `CTaskDialog` `HICON` so, dass für das Hauptsymbol verwendet wird. Die Alternative ist die Verwendung von `LPCWSTR` .|
|TDF_USE_HICON_FOOTER|Konfiguriert den `CTaskDialog` so, dass ein als `HICON` footersymbol verwendet wird. Die Alternative ist die Verwendung von `LPCWSTR` .|
|TDF_ALLOW_DIALOG_CANCELLATION|Ermöglicht es dem Benutzer, die `CTaskDialog` mithilfe der Tastatur oder mithilfe des Symbols in der oberen rechten Ecke des Dialog Felds zu schließen, auch wenn die Schaltfläche **Abbrechen** nicht aktiviert ist. Wenn dieses Flag nicht festgelegt ist und die Schaltfläche **Abbrechen** nicht aktiviert ist, kann der Benutzer das Dialogfeld nicht mit Alt + F4, der Escapetaste oder der Schaltfläche Schließen der Titelleiste schließen.|
|TDF_USE_COMMAND_LINKS|Konfiguriert die für die Verwendung von Befehls Schaltflächen-Steuer `CTaskDialog` Elementen.|
|TDF_USE_COMMAND_LINKS_NO_ICON|Konfiguriert den so `CTaskDialog` , dass Befehls Schaltflächen-Steuerelemente verwendet werden, ohne dass neben dem Steuerelement ein Symbol angezeigt wird TDF_USE_COMMAND_LINKS überschreibt TDF_USE_COMMAND_LINKS_NO_ICON.|
|TDF_EXPAND_FOOTER_AREA|Gibt an, dass der Erweiterungsbereich aktuell erweitert ist.|
|TDF_EXPANDED_BY_DEFAULT|Bestimmt, ob der Erweiterungsbereich Standardmäßig erweitert wird.|
|TDF_VERIFICATION_FLAG_CHECKED|Gibt an, dass das Kontrollkästchen Überprüfung aktuell ausgewählt ist.|
|TDF_SHOW_PROGRESS_BAR|Konfiguriert den `CTaskDialog` , um eine Statusanzeige anzuzeigen.|
|TDF_SHOW_MARQUEE_PROGRESS_BAR|Konfiguriert die Statusanzeige als Marquee-Statusanzeige. Wenn Sie diese Option aktivieren, müssen Sie TDF_SHOW_PROGRESS_BAR auf das erwartete Verhalten festlegen.|
|TDF_CALLBACK_TIMER|Gibt an, dass das `CTaskDialog` Rückruf Intervall auf ungefähr 200 Millisekunden festgelegt ist.|
|TDF_POSITION_RELATIVE_TO_WINDOW|Konfiguriert den `CTaskDialog` , der relativ zum übergeordneten Fenster zentriert werden soll. Wenn dieses Flag nicht aktiviert ist, `CTaskDialog` wird der relativ zum Monitor zentriert.|
|TDF_RTL_LAYOUT|Konfiguriert die `CTaskDialog` für ein Lese Layout von rechts nach links.|
|TDF_NO_DEFAULT_RADIO_BUTTON|Gibt an, dass kein Optionsfeld ausgewählt wird, wenn das `CTaskDialog` angezeigt wird.|
|TDF_CAN_BE_MINIMIZED|Ermöglicht es dem Benutzer, die zu minimieren `CTaskDialog` . Um diese Option zu unterstützen, `CTaskDialog` kann nicht modal sein. MFC unterstützt diese Option nicht, da MFC kein Modell unterstützt `CTaskDialog` .|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogsetprogressbarmarquee"></a><a name="setprogressbarmarquee"></a> CTaskDialog:: setprogressbarmarquee

Konfiguriert eine Marquee-Leiste für den `CTaskDialog` und fügt diese dem Dialogfeld hinzu.

```cpp
void SetProgressBarMarquee(
    BOOL bEnabled = TRUE,
    int nMarqueeSpeed = 0);
```

### <a name="parameters"></a>Parameter

*benabled*<br/>
in TRUE, um die Marquee-Leiste zu aktivieren. FALSE, wenn die Marquee-Leiste deaktiviert und aus der entfernt werden soll `CTaskDialog` .

*nmarqueespeed*<br/>
in Eine ganze Zahl, die die Geschwindigkeit der Marquee-Leiste angibt.

### <a name="remarks"></a>Bemerkungen

Die Marquee-Leiste wird unterhalb des Haupttexts der- `CTaskDialog` Klasse angezeigt.

Verwenden Sie *nmarqueespeed* , um die Geschwindigkeit der Marquee-Leiste festzulegen. größere Werte weisen auf eine langsamere Geschwindigkeit hin. Der Wert 0 für *nmarqueespeed* bewirkt, dass die Marquee-Leiste die Standardgeschwindigkeit für Windows verschiebt.

Diese Methode löst eine Ausnahme mit dem Makro [sicher](diagnostic-services.md#ensure) aus, wenn *nmarqueespeed* kleiner als 0 ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarposition"></a><a name="setprogressbarposition"></a> CTaskDialog:: setprogressbarposition

Passt die Position der Statusanzeige an.

```cpp
void SetProgressBarPosition(int nProgressPos);
```

### <a name="parameters"></a>Parameter

*nprogresspos*<br/>
in Die Position für die Statusanzeige.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem Element " [sicherstellen](diagnostic-services.md#ensure) " aus, wenn sich " *nprogresspos* " nicht im Statusanzeige Bereich befindet. Sie können den Bereich der Statusanzeige mit [CTaskDialog:: setprogressbarrange](#setprogressbarrange)ändern.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarrange"></a><a name="setprogressbarrange"></a> CTaskDialog:: setprogressbarrange

Passt den Bereich der Statusanzeige an.

```cpp
void SetProgressBarRange(
    int nRangeMin,
    int nRangeMax);
```

### <a name="parameters"></a>Parameter

*nrangemin*<br/>
in Die untere Grenze der Statusanzeige.

*nrangemax*<br/>
in Die obere Grenze der Statusanzeige.

### <a name="remarks"></a>Bemerkungen

Die Position der Statusanzeige ist relativ zu *nrangemin* und *nrangemax*. Wenn *nrangemin* beispielsweise 50 und *nrangemax* den Wert 100 hat, liegt die Position 75 in der Mitte der Statusanzeige. Verwenden Sie [CTaskDialog:: setprogressbarposition](#setprogressbarposition) , um die Position der Statusanzeige festzulegen.

Um die Statusanzeige anzuzeigen, muss die Option TDF_SHOW_PROGRESS_BAR aktiviert und TDF_SHOW_MARQUEE_PROGRESS_BAR nicht aktiviert sein. Diese Methode legt TDF_SHOW_PROGRESS_BAR automatisch fest und löscht TDF_SHOW_MARQUEE_PROGRESS_BAR. Verwenden Sie [CTaskDialog:: Setter](#setoptions) , um die Optionen für diese Instanz der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)manuell zu ändern.

Diese Methode löst eine Ausnahme mit dem Makro [sicher](diagnostic-services.md#ensure) aus, wenn *nrangemin* nicht kleiner als *nrangemax*ist. Diese Methode löst auch eine Ausnahme aus, wenn das `CTaskDialog` bereits angezeigt wird und über eine Marquee-Statusanzeige verfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetprogressbarstate"></a><a name="setprogressbarstate"></a> CTaskDialog:: setprogressbarstate

Legt den Status der Statusanzeige fest und zeigt Sie auf dem an `CTaskDialog` .

```cpp
void SetProgressBarState(int nState = PBST_NORMAL);
```

### <a name="parameters"></a>Parameter

*nstatusinformationen*<br/>
in Der Status der Statusanzeige. Die möglichen Werte finden Sie im Abschnitt "Hinweise".

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem Makro [sicher](diagnostic-services.md#ensure) aus, wenn `CTaskDialog` bereits angezeigt wird und über eine Marquee-Statusanzeige verfügt.

In der folgenden Tabelle sind die möglichen Werte für *nState*aufgeführt. In allen diesen Fällen wird die Statusanzeige mit der regulären Farbe aufgefüllt, bis die festgelegte Positionsposition erreicht ist. An diesem Punkt ändert sich die Farbe basierend auf dem Zustand.

|Name|Beschreibung|
|-|-|
|PBST_NORMAL|Wenn die Statusleiste ausgefüllt ist, wird die `CTaskDialog` Farbe des Balkens nicht geändert. Standardmäßig ist die reguläre Farbe grün.|
|PBST_ERROR|Nachdem die Statusanzeige ausgefüllt wurde, `CTaskDialog` ändert die Farbe des Balkens in die Fehlerfarbe. Standardmäßig ist dies rot.|
|PBST_PAUSED|Nachdem die Statusanzeige ausgefüllt wurde, `CTaskDialog` ändert die Farbe des Balkens in die angehaltene Farbe. Standardmäßig ist dies gelb.|

Sie können den Speicherort der Statusleiste mit [CTaskDialog:: setprogressbarposition](#setprogressbarposition)festlegen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#4](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_7.cpp)]

## <a name="ctaskdialogsetradiobuttonoptions"></a><a name="setradiobuttonoptions"></a> CTaskDialog:: Setter-Option

Aktiviert oder deaktiviert ein Optionsfeld.

```cpp
void SetRadioButtonOptions(
    int nRadioButtonID,
    BOOL bEnabled);
```

### <a name="parameters"></a>Parameter

*nradiobuttonid*<br/>
in Die ID des Optionsfeld-Steuer Elements.

*benabled*<br/>
in "True", um das Optionsfeld zu aktivieren. FALSE, um das Optionsfeld zu deaktivieren.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem Element " [sicherstellen](diagnostic-services.md#ensure) " aus, wenn " *nradiobuttonid* " keine gültige ID für ein Optionsfeld ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#3](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_2.cpp)]

## <a name="ctaskdialogsetverificationcheckbox"></a><a name="setverificationcheckbox"></a> CTaskDialog:: setverificationcheckbox

Legt den aktivierten Zustand des Kontrollkästchens Überprüfung fest.

```cpp
void SetVerificationCheckbox(BOOL bChecked);
```

### <a name="parameters"></a>Parameter

*bCheck*<br/>
in TRUE, wenn das Kontrollkästchen Überprüfung aktiviert werden soll, wenn das `CTaskDialog` angezeigt wird. FALSE, wenn das Kontrollkästchen Überprüfung deaktiviert werden soll, wenn das `CTaskDialog` angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetverificationcheckboxtext"></a><a name="setverificationcheckboxtext"></a> CTaskDialog:: setverificationcheckboxtext

Legt den Text fest, der rechts neben dem Überprüfungs Kontrollkästchen angezeigt wird.

```cpp
void SetVerificationCheckboxText(CString& strVerificationText);
```

### <a name="parameters"></a>Parameter

*"stringentext"*<br/>
in Der Text, der von dieser Methode neben dem Kontrollkästchen Überprüfung angezeigt wird.

### <a name="remarks"></a>Bemerkungen

Diese Methode löst eine Ausnahme mit dem Makro [sicher](diagnostic-services.md#ensure) aus, wenn diese Instanz der `CTaskDialog` Klasse bereits angezeigt wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#5](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_4.cpp)]

## <a name="ctaskdialogsetwindowtitle"></a><a name="setwindowtitle"></a> CTaskDialog:: SetWindowTitle

Legt den Titel des fest `CTaskDialog` .

```cpp
void SetWindowTitle(CString& strWindowTitle);
```

### <a name="parameters"></a>Parameter

*Fenstertitel*<br/>
in Der neue Titel für die `CTaskDialog` .

### <a name="remarks"></a>Bemerkungen

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#7](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_3.cpp)]

## <a name="ctaskdialogshowdialog"></a><a name="showdialog"></a> CTaskDialog:: ShowDialog

Erstellt eine und zeigt diese an `CTaskDialog` .

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

*"straucontent"*<br/>
in Die Zeichenfolge, die für den Inhalt des verwendet werden soll `CTaskDialog` .

*chanmaininstruction*<br/>
in Die Haupt Anweisung von `CTaskDialog` .

*Trend*<br/>
in Der Titel von `CTaskDialog` .

*nidcommandcontrolsfirst*<br/>
in Die Zeichen folgen-ID des ersten Befehls.

*nidcommandcontrolslast*<br/>
in Die Zeichen folgen-ID des letzten Befehls.

*ncommonbuttons*<br/>
in Eine Maske der Schaltflächen, die der hinzugefügt werden sollen `CTaskDialog` .

*ntaskdialogoptions*<br/>
in Der Satz von Optionen, die für das verwendet werden sollen `CTaskDialog` .

*Fußzeile*<br/>
in Die als Fußzeile zu verwendende Zeichenfolge.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die der vom Benutzer vorgenommenen Auswahl entspricht.

### <a name="remarks"></a>Bemerkungen

Diese statische Methode ermöglicht es Ihnen, eine Instanz der-Klasse zu erstellen, `CTaskDialog` ohne explizit ein- `CTaskDialog` Objekt im Code zu erstellen. Da kein-Objekt vorhanden ist `CTaskDialog` , können Sie keine anderen Methoden von aufzurufen, `CTaskDialog` Wenn Sie diese Methode zum Anzeigen eines `CTaskDialog` für den Benutzer verwenden.

Diese Methode erstellt Befehls Schaltflächen-Steuerelemente, indem Sie Daten aus der Ressourcen Datei Ihrer Anwendung verwendet. Die Zeichen folgen Tabelle in der Ressourcen Datei enthält mehrere Zeichen folgen mit zugeordneten Zeichen folgen-IDs. Diese Methode fügt ein Befehlszeilen-Steuerelement für jeden gültigen Eintrag in der Zeichen folgen Tabelle zwischen " *nidcommandcontrolsfirst* " und " *ncommandcontrolslast*, einschließlich", hinzu. Für diese Befehlszeilen-Steuerelemente ist die Zeichenfolge in der Zeichen folgen Tabelle die Beschriftung des Steuer Elements, und die Zeichen folgen-ID ist die ID des Steuer Elements.

Eine Liste gültiger Optionen finden Sie unter [CTaskDialog:: Setter](#setoptions) .

Das `CTaskDialog` schließt, wenn der Benutzer eine gemeinsame Schaltfläche, ein Befehls Verknüpfungs Steuerelement oder den schließt `CTaskDialog` . Der Rückgabewert ist der Bezeichner, der angibt, wie das Dialogfeld vom Benutzer geschlossen wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CTaskDialog#1](../../mfc/reference/codesnippet/cpp/ctaskdialog-class_5.cpp)]

## <a name="ctaskdialogtaskdialogcallback"></a><a name="taskdialogcallback"></a> CTaskDialog:: taskdialogcallback

Das Framework ruft diese Methode als Reaktion auf verschiedene Windows-Meldungen auf.

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

*HWND*<br/>
in Ein Handle für die- `m_hWnd` Struktur für das `CTaskDialog` .

*unotifizierung*<br/>
in Der Benachrichtigungs Code, der die generierte Meldung angibt.

*wParam*<br/>
in Weitere Informationen zur Meldung.

*lParam*<br/>
in Weitere Informationen zur Meldung.

*dwref-Daten*<br/>
in Ein Zeiger auf das- `CTaskDialog` Objekt, für das die Rückruf Meldung gilt.

### <a name="return-value"></a>Rückgabewert

Hängt vom jeweiligen Benachrichtigungs Code ab. Weitere Informationen finden Sie im Abschnitt Hinweise.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung von `TaskDialogCallback` behandelt die jeweilige Nachricht und ruft dann die entsprechende on-Methode der [CTaskDialog-Klasse](../../mfc/reference/ctaskdialog-class.md)auf. Beispielsweise wird in Reaktion auf die TDN_BUTTON_CLICKED Nachricht `TaskDialogCallback` [CTaskDialog:: oncommandcontrolclick](#oncommandcontrolclick)aufgerufen.

Die Werte für " *wParam* " und " *LPARAM* " hängen von der spezifischen generierten Meldung ab. Es ist möglich, dass einer oder beide dieser Werte leer sind. In der folgenden Tabelle werden die standardmäßig unterstützten Benachrichtigungen und die Werte von *wParam* und *LPARAM* aufgeführt. Wenn Sie diese Methode in einer abgeleiteten Klasse überschreiben, sollten Sie den Rückruf Code für jede Nachricht in der folgenden Tabelle implementieren.

|Benachrichtigungs Meldung|*wParam* Wert|*LPARAM* Wert|
|--------------------------|--------------------|--------------------|
|TDN_CREATED|Nicht verwendet.|Nicht verwendet.|
|TDN_NAVIGATED|Nicht verwendet.|Nicht verwendet.|
|TDN_BUTTON_CLICKED|Die Befehlszeilen-Steuerelement-ID.|Wird nicht verwendet.|
|TDN_HYPERLINK_CLICKED|Wird nicht verwendet.|Eine [LPCWSTR](/windows/win32/WinProg/windows-data-types) -Struktur, die den Link enthält.|
|TDN_TIMER|Die Zeit in Millisekunden seit der `CTaskDialog` Erstellung oder der zurück setzung des Timers.|Wird nicht verwendet.|
|TDN_DESTROYED|Nicht verwendet.|Nicht verwendet.|
|TDN_RADIO_BUTTON_CLICKED|Die Optionsfeld-ID.|Wird nicht verwendet.|
|TDN_DIALOG_CONSTRUCTED|Nicht verwendet.|Nicht verwendet.|
|TDN_VERIFICATION_CLICKED|1, wenn das Kontrollkästchen aktiviert ist, andernfalls 0.|Wird nicht verwendet.|
|TDN_HELP|Nicht verwendet.|Nicht verwendet.|
|TDN_EXPANDO_BUTTON_CLICKED|0, wenn der Erweiterungsbereich reduziert ist. ungleich 0 (null), wenn der Erweiterungs Text angezeigt wird.|Wird nicht verwendet.|

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Exemplarische Vorgehensweise: Hinzufügen eines CTaskDialog zu einer Anwendung](../../mfc/walkthrough-adding-a-ctaskdialog-to-an-application.md)
