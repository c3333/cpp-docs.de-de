---
title: CWinFormsDialog-Klasse
ms.date: 03/27/2019
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
helpviewer_keywords:
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
ms.openlocfilehash: a25823982b9276309e99a2a26cef8d6fe2e764bd
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040664"
---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog-Klasse

Ein Wrapper für eine MFC-Dialogfeldklasse, die ein Windows Forms-Benutzersteuerelement hostet.

## <a name="syntax"></a>Syntax

```
template <typename TManagedControl>
class CWinFormsDialog :
    public CDialog
```

#### <a name="parameters"></a>Parameter

*Tmanagedcontrol*<br/>
Das .NET Framework Benutzer Steuer Elements, das in der MFC-Anwendung angezeigt werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsDialog:: CWinFormsDialog](#cwinformsdialog)|Erstellt ein `CWinFormsDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsDialog:: GetControl](#getcontrol)|Ruft einen Verweis auf das Windows Forms Benutzer Steuerelement ab.|
|[CWinFormsDialog:: getcontrolhandle](#getcontrolhandle)|Ruft ein Fenster Handle für das Windows Forms Benutzer Steuerelement ab.|
|[CWinFormsDialog:: OnInitDialog](#oninitdialog)|Initialisiert das MFC-Dialogfeld, indem ein Windows Forms Benutzer Steuerelement erstellt und gehostet wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-|
|[CWinFormsDialog:: Operator-&gt;](#operator_-_gt)|Ersetzt [CWinFormsDialog:: GetControl](#getcontrol) in Ausdrücken.|
|[CWinFormsDialog:: Operator tmanagedcontrol ^](#operator-tmanagedcontrol-hat)|Wandelt einen Typ als Verweis in ein Windows Forms Benutzer Steuerelement um.|

## <a name="remarks"></a>Bemerkungen

`CWinFormsDialog` ist ein Wrapper für eine MFC-Dialogfeld Klasse ( [CDialog](../../mfc/reference/cdialog-class.md)), die ein Windows Forms Benutzer Steuerelement hostet. Dadurch können .NET Framework Steuerelemente in einem modalen oder nicht modalen MFC-Dialogfeld angezeigt werden.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) und [Hosting eines Windows Form-Benutzer Steuer Elements als MFC-Dialog Feld](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxwinforms. h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a> CWinFormsDialog:: CWinFormsDialog

Erstellt ein `CWinFormsDialog`-Objekt.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parameter

*nidtemplate*<br/>
Enthält die ID einer Dialogfeld Vorlagen-Ressource. Verwenden Sie den Dialog-Editor, um die Dialogfeld Vorlage zu erstellen und in der Ressourcen Skriptdatei der Anwendung zu speichern. Weitere Informationen zu Dialog Vorlagen finden Sie unter [CDialog-Klasse](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a> CWinFormsDialog:: GetControl

Ruft einen Verweis auf das Windows Forms Benutzer Steuerelement ab.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das Windows Forms-Steuerelement im MFC-Dialogfeld zurück.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a> CWinFormsDialog:: getcontrolhandle

Ruft ein Fenster Handle für das Windows Forms Benutzer Steuerelement ab.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Fenster Handle für das Windows Forms Benutzer Steuerelement zurück.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a> CWinFormsDialog:: OnInitDialog

Initialisiert das MFC-Dialogfeld, indem ein Windows Forms Benutzer Steuerelement erstellt und gehostet wird.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der angibt, ob die Anwendung den Eingabefokus auf eines der Steuerelemente im Dialogfeld festgelegt hat. Wenn einen Wert ungleich `OnInitDialog` 0 (null) zurückgibt, legt Windows den Eingabefokus auf das erste Steuerelement im Dialogfeld fest. Diese Methode kann nur dann 0 zurückgeben, wenn die Anwendung den Eingabefokus explizit auf eines der Steuerelemente im Dialogfeld festgelegt hat.

### <a name="remarks"></a>Bemerkungen

Wenn das MFC-Dialogfeld erstellt wird (mithilfe [Create](../../mfc/reference/cdialog-class.md#create)der Create [-, der](../../mfc/reference/cdialog-class.md#createindirect)- [Methode oder der](../../mfc/reference/cdialog-class.md#domodal) -Methode, die von [CDialog](../../mfc/reference/cdialog-class.md)geerbt wurde), wird eine WM_INITDIALOG Nachricht gesendet, und diese Methode wird aufgerufen. Er erstellt eine Instanz eines Windows Forms-Steuer Elements im Dialogfeld und passt die Größe des Dialog Felds an, um die Größe des Benutzer Steuer Elements anzupassen. Anschließend wird das neue Steuerelement im MFC-Dialogfeld gehostet.

Überschreiben Sie diese Member-Funktion, wenn Sie beim Initialisieren des Dialog Felds eine spezielle Verarbeitung ausführen müssen. Weitere Informationen zur Verwendung dieser Methode finden Sie unter [CDialog:: OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a> CWinFormsDialog:: Operator-&gt;

Ersetzt [CWinFormsDialog:: GetControl](#getcontrol) in Ausdrücken.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator stellt eine bequeme Syntax bereit, die `GetControl` in Ausdrücken ersetzt.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a> CWinFormsDialog:: Operator tmanagedcontrol ^

Wandelt einen Typ als Verweis in ein Windows Forms Benutzer Steuerelement um.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator wandelt einen Typ als Verweis in ein Windows Forms Steuerelement um. Es wird verwendet, um ein `CWinFormsDialog<TManagedControl>` Dialogfeld an Funktionen zu übergeben, die einen Zeiger auf ein Windows Forms Benutzer Steuerelement-Objekt akzeptieren.

## <a name="see-also"></a>Weitere Informationen

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
