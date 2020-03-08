---
title: CDialogBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDialogBar
- AFXEXT/CDialogBar
- AFXEXT/CDialogBar::CDialogBar
- AFXEXT/CDialogBar::Create
helpviewer_keywords:
- CDialogBar [MFC], CDialogBar
- CDialogBar [MFC], Create
ms.assetid: da2f7a30-970c-44e3-87f0-6094bd002cab
ms.openlocfilehash: af84c5239a9cb3cbddb1ab4f0230e5b1a3373573
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883621"
---
# <a name="cdialogbar-class"></a>CDialogBar-Klasse

Stellt die Funktionalität eines nicht modalen Windows-Dialogfelds in einer Steuerleiste bereit.

## <a name="syntax"></a>Syntax

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialogBar:: CDialogBar](#cdialogbar)|Erstellt ein `CDialogBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialogBar:: Create](#create)|Erstellt eine Windows-Dialog Leiste und fügt Sie an das `CDialogBar`-Objekt an.|

## <a name="remarks"></a>Bemerkungen

Eine Dialog Leiste ähnelt einem Dialogfeld, in dem Sie standardmäßige Windows-Steuerelemente enthält, zwischen denen der Benutzer Tabstopps leisten kann. Eine weitere Ähnlichkeit besteht darin, dass Sie eine Dialogfeld Vorlage erstellen, die die Dialog Leiste darstellt.

Das Erstellen und Verwenden einer Dialog Leiste ähnelt dem Erstellen und Verwenden eines `CFormView` Objekts. Verwenden Sie zuerst den [Dialog-Editor](../../windows/dialog-editor.md) , um eine Dialogfeld Vorlage mit dem Format WS_CHILD und ohne anderen Stil zu definieren. Die Vorlage darf nicht über die Format WS_VISIBLE verfügen. Rufen Sie im Anwendungscode den-Konstruktor auf, um das `CDialogBar` Objekt zu erstellen, und rufen Sie dann `Create` auf, um das Dialogfeld Fenster zu erstellen und es an das `CDialogBar`-Objekt anzufügen.

Weitere Informationen zu `CDialogBar`finden Sie in den Artikeln [Dialog leisten](../../mfc/dialog-bars.md) und [Technical Note 31](../../mfc/tn031-control-bars.md)(Steuer leisten).

> [!NOTE]
>  In der aktuellen Version kann ein `CDialogBar`-Objekt keine Windows Forms Steuerelemente hosten. Weitere Informationen zu Windows Forms-Steuerelementen in C++Visual finden [Sie unter Verwenden eines Windows Form-Benutzer Steuer Elements in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Afxext. h

##  <a name="cdialogbar"></a>CDialogBar:: CDialogBar

Erstellt ein `CDialogBar`-Objekt.

```
CDialogBar();
```

##  <a name="create"></a>CDialogBar:: Create

Lädt die durch `lpszTemplateName` oder `nIDTemplate`angegebene Dialogfeld-Ressourcen Vorlage, erstellt das Fenster der Dialog Leiste, legt den Stil fest und ordnet es dem `CDialogBar`-Objekt zu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

virtual BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*pparser*<br/>
Ein Zeiger auf das übergeordnete `CWnd`-Objekt.

*lpsztemplatename*<br/>
Ein Zeiger auf den Namen der Dialogfeld-Ressourcen Vorlage des `CDialogBar` Objekts.

*nstyle*<br/>
Der Symbolleisten Stil. Zusätzliche Symbolleisten Stile werden unterstützt:

- CBRS_TOP Steuerleiste oben im Rahmen Fenster angezeigt wird.

- CBRS_BOTTOM Steuerleiste befindet sich am unteren Rand des Rahmen Fensters.

- CBRS_NOALIGN Steuerleiste wird nicht neu positioniert, wenn die Größe des übergeordneten Elements geändert wird.

- In CBRS_TOOLTIPS Steuerleiste werden Quick Infos angezeigt.

- CBRS_SIZE_DYNAMIC Steuerleiste ist dynamisch.

- CBRS_SIZE_FIXED Steuerleiste ist korrigiert.

- CBRS_FLOATING Steuerleiste ist unverankert.

- In CBRS_FLYBY Status Leiste werden Informationen zur Schaltfläche angezeigt.

- CBRS_HIDE_INPLACE Steuerleiste wird dem Benutzer nicht angezeigt.

*NID*<br/>
Die Steuerelement-ID der Dialog Leiste.

*nidtemplate*<br/>
Die Ressourcen-ID der Dialogfeld Vorlage des `CDialogBar` Objekts.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn Sie die CBRS_TOP oder CBRS_BOTTOM Ausrichtungs Format angeben, entspricht die Breite der Dialog Leiste dem Rahmen Fenster, und die Höhe entspricht der von " *nidtemplate*" angegebenen Ressource. Wenn Sie die CBRS_LEFT oder CBRS_RIGHT Ausrichtungs Format angeben, wird die Höhe der Dialog Leiste im Rahmen Fenster und deren Breite der von *nidtemplate*angegebenen Ressource entspricht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel-CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)<br/>
[CControlBar Class](../../mfc/reference/ccontrolbar-class.md)
