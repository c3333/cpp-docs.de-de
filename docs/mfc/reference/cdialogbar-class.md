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
ms.openlocfilehash: cf9a2658807959108b3bb0af672d4c1835b58bc5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375676"
---
# <a name="cdialogbar-class"></a>CDialogBar-Klasse

Stellt die Funktionalität eines nicht modalen Windows-Dialogfelds in einer Steuerleiste bereit.

## <a name="syntax"></a>Syntax

```
class CDialogBar : public CControlBar
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialogBar::CDialogBar](#cdialogbar)|Erstellt ein `CDialogBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDialogBar::Erstellen](#create)|Erstellt eine Windows-Dialogleiste und `CDialogBar` fügt sie an das Objekt an.|

## <a name="remarks"></a>Bemerkungen

Eine Dialogleiste ähnelt einem Dialogfeld, da sie standardmäßige Windows-Steuerelemente enthält, zwischen denen der Benutzer eine Registerkarte durchführen kann. Eine weitere Ähnlichkeit besteht darin, dass Sie eine Dialogvorlage erstellen, um die Dialogleiste darzustellen.

Das Erstellen und Verwenden einer Dialogleiste `CFormView` ähnelt dem Erstellen und Verwenden eines Objekts. Verwenden Sie zunächst den [Dialogeditor,](../../windows/dialog-editor.md) um eine Dialogvorlage mit dem Stil WS_CHILD und keinem anderen Stil zu definieren. Die Vorlage darf nicht den Stil WS_VISIBLE haben. Rufen Sie im Anwendungscode den Konstruktor auf, um das `CDialogBar` Objekt zu erstellen, und rufen Sie dann auf, `Create` um das Dialogleistenfenster zu erstellen und es an das `CDialogBar` Objekt anzufügen.

Weitere Informationen `CDialogBar`finden Sie im Artikel [Dialogleisten](../../mfc/dialog-bars.md) und [Technischer Hinweis 31](../../mfc/tn031-control-bars.md), Steuerleisten.

> [!NOTE]
> In der aktuellen `CDialogBar` Version kann ein Objekt keine Windows Forms-Steuerelemente hosten. Weitere Informationen zu Windows Forms-Steuerelementen in Visual C++ finden Sie unter [Verwenden einer Windows Form-Benutzersteuerung in MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`CDialogBar`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxext.h

## <a name="cdialogbarcdialogbar"></a><a name="cdialogbar"></a>CDialogBar::CDialogBar

Erstellt ein `CDialogBar`-Objekt.

```
CDialogBar();
```

## <a name="cdialogbarcreate"></a><a name="create"></a>CDialogBar::Erstellen

Lädt die von `lpszTemplateName` oder `nIDTemplate`angegebene Dialogfeld-Ressourcenvorlage erstellt das Dialogleistenfenster, legt `CDialogBar` dessen Stil fest und ordnet es dem Objekt zu.

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

*pParentWnd*<br/>
Ein Zeiger auf `CWnd` das übergeordnete Objekt.

*lpszTemplateName*<br/>
Ein Zeiger auf den `CDialogBar` Namen der Dialogfeldressourcenvorlage des Objekts.

*nStyle*<br/>
Der Symbolleistenstil. Weitere unterstützte Symbolleistenstile sind:

- CBRS_TOP Steuerleiste befindet sich oben im Rahmenfenster.

- CBRS_BOTTOM Steuerleiste befindet sich am unteren Rand des Rahmenfensters.

- CBRS_NOALIGN Steuerleiste wird nicht neu positioniert, wenn die Größe des übergeordneten Elements geändert wird.

- CBRS_TOOLTIPS Steuerleiste zeigt Werkzeugtipps an.

- CBRS_SIZE_DYNAMIC Steuerleiste ist dynamisch.

- CBRS_SIZE_FIXED Steuerleiste ist fixiert.

- CBRS_FLOATING Steuerleiste ist schwebend.

- CBRS_FLYBY Statusleiste zeigt Informationen zur Schaltfläche an.

- CBRS_HIDE_INPLACE Steuerleiste wird dem Benutzer nicht angezeigt.

*nID*<br/>
Die Steuerelement-ID der Dialogleiste.

*nIDTemplate*<br/>
Die Ressourcen-ID `CDialogBar` der Dialogfeldvorlage des Objekts.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Wenn Sie den CBRS_TOP oder CBRS_BOTTOM Ausrichtungsstil angeben, ist die Breite der Dialogleiste die des Rahmenfensters und die Höhe der von *nIDTemplate*angegebenen Ressource. Wenn Sie den CBRS_LEFT oder CBRS_RIGHT Ausrichtungsstil angeben, ist die Höhe der Dialogleiste die höhe des Rahmenfensters und ihre Breite die der von *nIDTemplate*angegebenen Ressource.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCMessageMaps#13](../../mfc/reference/codesnippet/cpp/cdialogbar-class_1.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel STRGBARS](../../overview/visual-cpp-samples.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CFormView-Klasse](../../mfc/reference/cformview-class.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)
