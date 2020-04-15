---
title: CMFCWindowsManagerDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: e3928c0d3ae4f607dceb99c0762277e8ea9ddbde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319823"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog-Klasse

Das `CMFCWindowsManagerDialog` Objekt ermöglicht es einem Benutzer, untergeordnete MDI-Fenster in einer MDI-Anwendung zu verwalten.

## <a name="syntax"></a>Syntax

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|Erstellt ein `CMFCWindowsManagerDialog`-Objekt.|

## <a name="remarks"></a>Bemerkungen

Der `CMFCWindowsManagerDialog` enthält eine Liste der untergeordneten MDI-Fenster, die derzeit in der Anwendung geöffnet sind. Der Benutzer kann den Status der untergeordneten MDI-Fenster manuell steuern, indem er dieses Dialogfeld verwendet.

`CMFCWindowsManagerDialog`ist in die [CMDIFrameWndEx-Klasse](../../mfc/reference/cmdiframewndex-class.md)eingebettet. Der `CMFCWindowsManagerDialog` ist keine Klasse, die Sie manuell erstellen sollten. Rufen Sie stattdessen die Funktion [CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)auf, `CMFCWindowsManagerDialog` und es wird ein Objekt erstellt und angezeigt.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCWindowsManagerDialog` veranschaulicht, `CMDIFrameWndEx::ShowWindowsDialog`wie ein Objekt durch Aufrufen erstellt wird. Dieser Codeausschnitt ist Teil des [Visual Studio Demo-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxWindowsManagerDialog.h

## <a name="cmfcwindowsmanagerdialogcmfcwindowsmanagerdialog"></a><a name="cmfcwindowsmanagerdialog"></a>CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

Erstellt ein [CMFCWindowsManagerDialog-Objekt.](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>Parameter

*pMDIFrame*<br/>
[in] Ein Zeiger auf das übergeordnete oder Besitzerfenster.

*bHelpButton*<br/>
[in] Ein boolescher Parameter, der angibt, ob das Framework eine **Hilfeschaltfläche** anzeigt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu visuellen Managern finden Sie unter [Visualisierungs-Manager](../../mfc/visualization-manager.md).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx-Klasse](../../mfc/reference/cmdiframewndex-class.md)
