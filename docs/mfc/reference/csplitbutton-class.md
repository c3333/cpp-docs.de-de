---
title: CSplitButton-Klasse
ms.date: 11/19/2018
f1_keywords:
- CSplitButton
- AFXCMN/CSplitButton
- AFXCMN/CSplitButton::CSplitButton
- AFXCMN/CSplitButton::Create
- AFXCMN/CSplitButton::SetDropDownMenu
- AFXCMN/CSplitButton::OnDropDown
helpviewer_keywords:
- CSplitButton [MFC], CSplitButton
- CSplitButton [MFC], Create
- CSplitButton [MFC], SetDropDownMenu
- CSplitButton [MFC], OnDropDown
ms.assetid: 6844d0a9-6408-4e44-9b5f-57628ed8bad6
ms.openlocfilehash: 38fceed1cc42ca0aac2e6ddaf145db273c95771d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753131"
---
# <a name="csplitbutton-class"></a>CSplitButton-Klasse

Die `CSplitButton` Klasse stellt ein Steuerelement mit geteilten Schaltflächen dar. Das Steuerelement mit einer unterteilten Schaltfläche führt ein Standardverhalten aus, wenn ein Benutzer auf den Hauptteil der Schaltfläche klickt, und zeigt ein Dropdownmenü an, wenn ein Benutzer auf den Dropdownpfeil der Schaltfläche klickt.

## <a name="syntax"></a>Syntax

```
class CSplitButton : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitButton::CSplitButton](#csplitbutton)|Erstellt ein `CSplitButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitButton::Erstellen](#create)|Erstellt ein Split-Schaltflächensteuerelement mit angegebenen Stilen und fügt es an das aktuelle `CSplitButton` Objekt an.|
|[CSplitButton::SetDropDownMenu](#setdropdownmenu)|Legt das Dropdown-Menü fest, das angezeigt wird, wenn ein Benutzer auf den Dropdown-Pfeil des aktuellen Steuerelements für die geteilte Schaltfläche klickt.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CsplitButton::OnDropdown](#ondropdown)|Behandelt die BCN_DROPDOWN Benachrichtigung, die das System sendet, wenn ein Benutzer auf den Dropdown-Pfeil des aktuellen Steuerelements für die geteilte Schaltfläche klickt.|

## <a name="remarks"></a>Bemerkungen

Die `CSplitButton` Klasse wird von der [CButton-Klasse](../../mfc/reference/cbutton-class.md) abgeleitet. Das Steuerelement für die geteilte Schaltfläche ist ein Schaltflächensteuerelement, dessen Stil BS_SPLITBUTTON ist. Es wird ein benutzerdefiniertes Menü angezeigt, wenn ein Benutzer auf den Dropdown-Pfeil klickt. Weitere Informationen finden Sie unter BS_SPLITBUTTON und BS_DEFSPLITBUTTON Stile in [Schaltflächenstilen](/windows/win32/Controls/button-styles).

Die folgende Abbildung zeigt ein Dialogfeld, das ein Pager-Steuerelement und ein (1) geteiltes Schaltflächensteuerelement enthält. Der (2) Dropdown-Pfeil wurde bereits angeklickt und das Untermenü (3) wird angezeigt.

![Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.](../../mfc/reference/media/splitbutton_pager.png "Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.")

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

Diese Klasse wird in Windows Vista und höher unterstützt.

Weitere Anforderungen für diese Klasse werden unter [Buildanforderungen für allgemeine Windows Vista-Steuerelemente](../../mfc/build-requirements-for-windows-vista-common-controls.md)beschrieben.

## <a name="csplitbuttoncreate"></a><a name="create"></a>CSplitButton::Erstellen

Erstellt ein Split-Schaltflächensteuerelement mit angegebenen Stilen und fügt es an das aktuelle `CSplitButton` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*dwStyle*|[in] Eine bitweise Kombination (OR) von Stilen, die auf das Steuerelement angewendet werden sollen. Weitere Informationen finden Sie unter [Schaltflächenstile](../../mfc/reference/styles-used-by-mfc.md#button-styles).|
|*Rect*|[in] Ein Verweis auf eine [RECT-Struktur,](/windows/win32/api/windef/ns-windef-rect) die die Position und Größe des Steuerelements enthält.|
|*pParentWnd*|[in] Ein Nicht-NULL-Zeiger auf ein [CWnd-Objekt,](../../mfc/reference/cwnd-class.md) das das übergeordnete Fenster des Steuerelements ist.|
|*nID*|[in] Die ID des Steuerelements.|

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist; andernfalls FALSE.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a>CSplitButton::CSplitButton

Erstellt ein `CSplitButton`-Objekt. Die Parameter des Konstruktors geben ein Untermenü an, das angezeigt wird, wenn ein Benutzer auf den Dropdownpfeil des Steuerelements für die geteilte Schaltfläche klickt.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*nMenuId*|[in] Die Ressourcen-ID der Menüleiste.|
|*nSubMenuId*|[in] Die Ressourcen-ID eines Untermenüs.|
|*pMenu*|[in] Ein Zeiger auf ein [CMenu-Objekt,](../../mfc/reference/cmenu-class.md) das ein Untermenü angibt. Das `CSplitButton` Objekt löscht `CMenu` das Objekt und die `CSplitButton` zugehörigen HMENU, wenn das Objekt den Gültigkeitsbereich verlässt.|

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CSplitButton::Create-Methode,](#create) um ein `CSplitButton` Split-Button-Steuerelement zu erstellen und es an das Objekt anzufügen.

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a>CsplitButton::OnDropdown

Behandelt die BCN_DROPDOWN Benachrichtigung, die das System sendet, wenn ein Benutzer auf den Dropdown-Pfeil des aktuellen Steuerelements für die geteilte Schaltfläche klickt.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*pNMHDR*|[in] Zeiger auf eine [NMHDR-Struktur,](/windows/win32/api/richedit/ns-richedit-nmhdr) die Informationen über die [BCN_DROPDOWN-Benachrichtigung](/windows/win32/Controls/bcn-dropdown) enthält.|
|*pResult*|[out] (Nicht verwendet; es wird kein Wert zurückgegeben.) Rückgabewert der [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) Benachrichtigung.|

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer auf den Dropdown-Pfeil auf ein Steuerelement für geteilte `OnDropDown` Schaltflächen klickt, sendet das System eine BCN_DROPDOWN Benachrichtigung, die von der Methode verarbeitet wird. Das `CSplitButton` Objekt leitet die BCN_DROPDOWN Benachrichtigung jedoch nicht an das Steuerelement weiter, das das Steuerelement für die geteilte Schaltfläche enthält. Daher kann das enthaltende Steuerelement keine benutzerdefinierte Aktion als Reaktion auf die Benachrichtigung unterstützen.

Um eine benutzerdefinierte Aktion zu implementieren, die das enthaltende Steuerelement unterstützt, verwenden Sie ein [CButton-Objekt](../../mfc/reference/cbutton-class.md) mit der Formatvorlage BS_SPLITBUTTON anstelle eines Objekts. `CSplitButton` Implementieren Sie dann einen Handler `CButton` für die BCN_DROPDOWN Benachrichtigung im Objekt. Weitere Informationen finden Sie unter [Schaltflächenstile](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Um eine benutzerdefinierte Aktion zu implementieren, die das Steuerelement der geteilten Schaltfläche selbst unterstützt, verwenden Sie [die Nachrichtenreflexion](../../mfc/tn062-message-reflection-for-windows-controls.md). Leiten Sie Ihre eigene `CSplitButton` Klasse von der Klasse ab, und benennen Sie sie, z. B. CMySplitButton. Fügen Sie dann der Anwendung die folgende Meldungszuordnung hinzu, um die BCN_DROPDOWN-Benachrichtigung zu verarbeiten:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a>CSplitButton::SetDropDownMenu

Legt das Dropdown-Menü fest, das angezeigt wird, wenn ein Benutzer auf den Dropdown-Pfeil des aktuellen Steuerelements für die geteilte Schaltfläche klickt.

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parameter

|Parameter|Beschreibung|
|---------------|-----------------|
|*nMenuId*|[in] Die Ressourcen-ID der Menüleiste.|
|*nSubMenuId*|[in] Die Ressourcen-ID eines Untermenüs.|
|*pMenu*|[in] Zeiger auf ein [CMenu-Objekt,](../../mfc/reference/cmenu-class.md) das ein Untermenü angibt. Das `CSplitButton` Objekt löscht `CMenu` das Objekt und die `CSplitButton` zugehörigen HMENU, wenn das Objekt den Gültigkeitsbereich verlässt.|

### <a name="remarks"></a>Bemerkungen

Der Parameter *nMenuId* identifiziert eine Menüleiste, die eine horizontale Liste von Menüleistenelementen ist. Der Parameter *nSubMenuId* ist eine nullbasierte Indexnummer, die ein Untermenü identifiziert, d. h. die Dropdownliste der Menüelemente, die jedem Menüleistenelement zugeordnet sind. Eine typische Anwendung verfügt beispielsweise über ein Menü, das die Menüleistenelemente "Datei", "Bearbeiten" und "Hilfe" enthält. Das Menüleistenelement "Datei" verfügt über ein Untermenü, das die Menüelemente "Öffnen", "Schließen" und "Beenden" enthält. Wenn auf den Dropdown-Pfeil des Split-Button-Steuerelements geklickt wird, zeigt das Steuerelement das angegebene Untermenü und nicht die Menüleiste an.

Die folgende Abbildung zeigt ein Dialogfeld, das ein Pager-Steuerelement und ein (1) geteiltes Schaltflächensteuerelement enthält. Der (2) Dropdown-Pfeil wurde bereits angeklickt und das Untermenü (3) wird angezeigt.

![Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.](../../mfc/reference/media/splitbutton_pager.png "Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.")

### <a name="example"></a>Beispiel

Die erste Anweisung im folgenden Codebeispiel veranschaulicht die [CSplitButton::SetDropDownMenu-Methode.](#setdropdownmenu) Wir haben das Menü mit dem Visual Studio-Ressourcen-Editor erstellt, der automatisch die Menüleisten-ID IDR_MENU1. Der Parameter *nSubMenuId,* der Null ist, bezieht sich auf das einzige Untermenü der Menüleiste.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CSplitButton-Klasse](../../mfc/reference/csplitbutton-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)
