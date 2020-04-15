---
title: CMFCDesktopAlertDialog-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::CreateFromParams
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::GetDlgSize
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::HasFocus
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertDialog::PreTranslateMessage
helpviewer_keywords:
- CMFCDesktopAlertDialog [MFC], CreateFromParams
- CMFCDesktopAlertDialog [MFC], GetDlgSize
- CMFCDesktopAlertDialog [MFC], HasFocus
- CMFCDesktopAlertDialog [MFC], PreTranslateMessage
ms.assetid: a53c60aa-9607-485b-b826-ec64962075f6
ms.openlocfilehash: 479959e9b021255e309caf6fee02588a8cd8f1d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367656"
---
# <a name="cmfcdesktopalertdialog-class"></a>CMFCDesktopAlertDialog-Klasse

Die `CMFCDesktopAlertDialog` Klasse wird zusammen mit der [CMFCDesktopAlertWnd-Klasse](../../mfc/reference/cmfcdesktopalertwnd-class.md) verwendet, um ein benutzerdefiniertes Dialogfeld in einem Popupfenster anzuzeigen.

Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMFCDesktopAlertDialog : public CDialogEx
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCDesktopAlertDialog::CreateFromParams](#createfromparams)||
|[CMFCDesktopAlertDialog::GetDlgSize](#getdlgsize)||
|[CMFCDesktopAlertDialog::HasFocus](#hasfocus)||
|[CMFCDesktopAlertDialog::PreTranslateMessage](#pretranslatemessage)|(Überschreibt `CDialogEx::PreTranslateMessage`.)|

### <a name="remarks"></a>Bemerkungen

Führen Sie die folgenden Schritte aus, um ein benutzerdefiniertes Dialogfeld in einem Popupfenster anzuzeigen:

1. Leiten Sie eine Klasse von `CMFCDesktopAlertDialog` ab.

1. Erstellen Sie eine untergeordnete Dialogfeldvorlage in den Ressourcen des Projekts.

1. Rufen Sie [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) mit der Ressourcen-ID der Dialogfeldvorlage und einem Zeiger auf die Laufzeitklasseninformationen der abgeleiteten Klasse als Parameter auf.

1. Programmieren Sie das benutzerdefinierte Dialogfeld so, dass es alle Benachrichtigungen von den gehosteten Steuerelementen verarbeitet, oder programmieren Sie die gehosteten Steuerelemente so, dass sie diese Benachrichtigungen direkt verarbeiten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCDesktopAlertDialog](../../mfc/reference/cmfcdesktopalertdialog-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxDesktopAlertDialog.h

## <a name="cmfcdesktopalertdialogcreatefromparams"></a><a name="createfromparams"></a>CMFCDesktopAlertDialog::CreateFromParams

```
BOOL CreateFromParams(
    CMFCDesktopAlertWndInfo& params,
    CMFCDesktopAlertWnd* pParent);
```

### <a name="parameters"></a>Parameter

[in] *params*<br/>

[in] *pParent*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertdialoggetdlgsize"></a><a name="getdlgsize"></a>CMFCDesktopAlertDialog::GetDlgSize

```
CSize GetDlgSize();
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertdialoghasfocus"></a><a name="hasfocus"></a>CMFCDesktopAlertDialog::HasFocus

```
BOOL HasFocus() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmfcdesktopalertdialogpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCDesktopAlertDialog::PreTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parameter

[in] *pMsg*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd Class](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWndInfo-Klasse](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CDialogEx-Klasse](../../mfc/reference/cdialogex-class.md)
