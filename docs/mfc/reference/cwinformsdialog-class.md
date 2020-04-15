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
ms.openlocfilehash: 3772033df59e065cedca61012cd479c812cf5b66
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367430"
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

*TManagedControl*<br/>
Das .NET Framework-Benutzersteuerelement, das in der MFC-Anwendung angezeigt werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|Erstellt ein `CWinFormsDialog`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CWinFormsDialog::GetControl](#getcontrol)|Ruft einen Verweis auf das Windows Forms-Benutzersteuerelement ab.|
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|Ruft ein Fensterhandle für das Windows Forms-Benutzersteuerelement ab.|
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|Initialisiert das MFC-Dialogfeld, indem ein Windows Forms-Benutzersteuerelement erstellt und gehostet wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name||
|----------|-|
|[CWinFormsDialog::operator -&gt;](#operator_-_gt)|Ersetzt [CWinFormsDialog::GetControl](#getcontrol) in Ausdrücken.|
|[CWinFormsDialog::operator TManagedControl](#operator-tmanagedcontrol-hat)|Gibt einen Typ als Verweis auf ein Windows Forms-Benutzersteuerelement um.|

## <a name="remarks"></a>Bemerkungen

`CWinFormsDialog`ist ein Wrapper für eine MFC-Dialogklasse ( [CDialog](../../mfc/reference/cdialog-class.md)), die ein Windows Forms-Benutzersteuerelement hostet. Dadurch können .NET Framework-Steuerelemente in einem modalen oder moduslosen MFC-Dialogfeld angezeigt werden.

Weitere Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows-Formularbenutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md) und [Hosten einer Windows Form User Control als MFC-Dialogfeld](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md).

## <a name="requirements"></a>Anforderungen

**Kopf:** afxwinforms.h

## <a name="cwinformsdialogcwinformsdialog"></a><a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog

Erstellt ein `CWinFormsDialog`-Objekt.

```
CWinFormsDialog(UINT nIDTemplate = IDD);
```

### <a name="parameters"></a>Parameter

*nIDTemplate*<br/>
Enthält die ID einer Dialogfeldvorlagenressource. Verwenden Sie den Dialog-Editor, um die Dialogvorlage zu erstellen und in der Ressourcenskriptdatei der Anwendung zu speichern. Weitere Informationen zu Dialogfeldvorlagen finden Sie unter [CDialog Class](../../mfc/reference/cdialog-class.md).

## <a name="cwinformsdialoggetcontrol"></a><a name="getcontrol"></a>CWinFormsDialog::GetControl

Ruft einen Verweis auf das Windows Forms-Benutzersteuerelement ab.

```
inline TManagedControl^ GetControl() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das Windows Forms-Steuerelement im MFC-Dialogfeld zurück.

## <a name="cwinformsdialoggetcontrolhandle"></a><a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle

Ruft ein Fensterhandle für das Windows Forms-Benutzersteuerelement ab.

```
inline HWND GetControlHandle() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt ein Fensterhandle an das Windows Forms-Benutzersteuerelement zurück.

## <a name="cwinformsdialogoninitdialog"></a><a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog

Initialisiert das MFC-Dialogfeld, indem ein Windows Forms-Benutzersteuerelement erstellt und gehostet wird.

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>Rückgabewert

Ein boolescher Wert, der angibt, ob die Anwendung den Eingabefokus auf eines der Steuerelemente im Dialogfeld festgelegt hat. Wenn `OnInitDialog` ein Wert ungleich Null zurückgegeben wird, legt Windows den Eingabefokus auf das erste Steuerelement im Dialogfeld fest. Diese Methode kann nur 0 zurückgeben, wenn die Anwendung den Eingabefokus explizit auf eines der Steuerelemente im Dialogfeld festgelegt hat.

### <a name="remarks"></a>Bemerkungen

Wenn das MFC-Dialogfeld erstellt wird (mit der [Create](../../mfc/reference/cdialog-class.md#create), [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)oder [DoModal-Methode,](../../mfc/reference/cdialog-class.md#domodal) die von [CDialog](../../mfc/reference/cdialog-class.md)geerbt wurde), wird eine WM_INITDIALOG Nachricht gesendet, und diese Methode wird aufgerufen. Es erstellt eine Instanz eines Windows Forms-Steuerelements im Dialogfeld und passt die Größe des Dialogfelds an die Größe des Benutzersteuerelements an. Anschließend wird das neue Steuerelement im MFC-Dialogfeld gehostet.

Überschreiben Sie diese Memberfunktion, wenn Sie eine spezielle Verarbeitung durchführen müssen, wenn das Dialogfeld initialisiert wird. Weitere Informationen zur Verwendung dieser Methode finden Sie unter [CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog).

## <a name="cwinformsdialogoperator--gt"></a><a name="operator_-_gt"></a>CWinFormsDialog::operator -&gt;

Ersetzt [CWinFormsDialog::GetControl](#getcontrol) in Ausdrücken.

```
inline TManagedControl^  operator->() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator stellt eine praktische `GetControl` Syntax bereit, die in Ausdrücken ersetzt wird.

Informationen zur Verwendung von Windows Forms finden Sie unter [Verwenden einer Windows Form Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="cwinformsdialogoperator-tmanagedcontrol"></a><a name="operator-tmanagedcontrol-hat"></a>CWinFormsDialog::operator TManagedControl

Gibt einen Typ als Verweis auf ein Windows Forms-Benutzersteuerelement um.

```
inline operator TManagedControl^() const throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Typ als Verweis auf ein Windows Forms-Steuerelement um. Es wird verwendet, `CWinFormsDialog<TManagedControl>` um ein Dialogfeld an Funktionen zu übergeben, die einen Zeiger auf ein Windows Forms-Benutzersteuerelementobjekt akzeptieren.

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CWinFormsView-Klasse](../../mfc/reference/cwinformsview-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)
