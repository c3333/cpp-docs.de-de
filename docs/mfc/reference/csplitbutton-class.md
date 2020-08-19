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
ms.openlocfilehash: 484cef2787c9e5c166a7b20b017251b559d7221c
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562544"
---
# <a name="csplitbutton-class"></a>CSplitButton-Klasse

Die- `CSplitButton` Klasse stellt ein Steuerelement für unterteilte Schaltflächen Das Steuerelement mit einer unterteilten Schaltfläche führt ein Standardverhalten aus, wenn ein Benutzer auf den Hauptteil der Schaltfläche klickt, und zeigt ein Dropdownmenü an, wenn ein Benutzer auf den Dropdownpfeil der Schaltfläche klickt.

## <a name="syntax"></a>Syntax

```
class CSplitButton : public CButton
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitButton:: CSplitButton](#csplitbutton)|Erstellt ein `CSplitButton`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitButton:: Create](#create)|Erstellt ein Steuerelement für eine unterteilte Schaltfläche mit angegebenen Stilen und fügt es an das aktuelle- `CSplitButton` Objekt an.|
|[CSplitButton:: setdropdownmenu](#setdropdownmenu)|Legt das Dropdown Menü fest, das angezeigt wird, wenn ein Benutzer auf den Dropdown Pfeil des aktuellen Steuer Elements für eine unterteilte Schaltfläche klickt.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSplitButton:: OnDropDown](#ondropdown)|Behandelt die BCN_DROPDOWN Benachrichtigung, die vom System gesendet wird, wenn ein Benutzer auf den Dropdown Pfeil des aktuellen Trenn Schaltflächen-Steuer Elements klickt.|

## <a name="remarks"></a>Bemerkungen

Die- `CSplitButton` Klasse wird von der [CButton](../../mfc/reference/cbutton-class.md) -Klasse abgeleitet. Das Steuerelement unterteilte Schaltflächen ist ein Schaltflächen-Steuerelement, dessen Format BS_SPLITBUTTON ist Wenn ein Benutzer auf den Dropdown Pfeil klickt, wird ein benutzerdefiniertes Menü angezeigt. Weitere Informationen finden Sie unter BS_SPLITBUTTON-und BS_DEFSPLITBUTTON Stile in [Schalt](/windows/win32/Controls/button-styles)Flächen Formaten.

In der folgenden Abbildung wird ein Dialogfeld dargestellt, das ein Pager-Steuerelement und ein (1) Split Button-Steuerelement enthält. Auf den (2) Dropdown Pfeil wurde bereits geklickt, und das Untermenü (3) wird angezeigt.

![Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.](../../mfc/reference/media/splitbutton_pager.png "Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.")

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CSplitButton`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

Diese Klasse wird in Windows Vista und höher unterstützt.

Weitere Anforderungen für diese Klasse werden unter [Buildanforderungen für allgemeine Windows Vista](../../mfc/build-requirements-for-windows-vista-common-controls.md)-Steuerelemente beschrieben.

## <a name="csplitbuttoncreate"></a><a name="create"></a> CSplitButton:: Create

Erstellt ein Steuerelement für eine unterteilte Schaltfläche mit angegebenen Stilen und fügt es an das aktuelle- `CSplitButton` Objekt an.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parameter

*dwstyle*\
in Eine bitweise Kombination (or) der Stile, die auf das-Steuerelement angewendet werden sollen. Weitere Informationen finden Sie unter [Schaltflächen Stile](../../mfc/reference/styles-used-by-mfc.md#button-styles).

*Rect*\
in Ein Verweis auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur, die die Position und Größe des Steuer Elements enthält.

*pparser*\
in Ein nicht-NULL-Zeiger auf ein [CWnd](../../mfc/reference/cwnd-class.md) -Objekt, das das übergeordnete Fenster des Steuer Elements ist.

*NID*\
in Die ID des Steuer Elements.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn diese Methode erfolgreich ist. andernfalls false.

## <a name="csplitbuttoncsplitbutton"></a><a name="csplitbutton"></a> CSplitButton:: CSplitButton

Erstellt ein `CSplitButton`-Objekt. Die Parameter des Konstruktors geben ein Untermenü an, das angezeigt wird, wenn ein Benutzer auf den Dropdown Pfeil des Steuer Elements für die unterteilte Schaltfläche klickt.

```
CSplitButton();

CSplitButton(
    UINT nMenuId,
    UINT nSubMenuId)
CSplitButton(CMenu* pMenu)
```

### <a name="parameters"></a>Parameter

*nmenuid*\
in Die Ressourcen-ID der Menüleiste.

*nsubmenuid*\
in Die Ressourcen-ID eines Untermenüs.

*pmenu*\
in Ein Zeiger auf ein [CMenu](../../mfc/reference/cmenu-class.md) -Objekt, das ein Untermenü angibt. Das `CSplitButton` -Objekt löscht das `CMenu` -Objekt und das zugehörige HMENU, wenn das Objekt den Gültigkeits `CSplitButton` Bereich verlässt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die [CSplitButton:: Create](#create) -Methode, um ein Steuerelement unterteilte Schaltflächen zu erstellen und an das-Objekt anzufügen `CSplitButton` .

## <a name="csplitbuttonondropdown"></a><a name="ondropdown"></a> CSplitButton:: OnDropDown

Behandelt die BCN_DROPDOWN Benachrichtigung, die vom System gesendet wird, wenn ein Benutzer auf den Dropdown Pfeil des aktuellen Trenn Schaltflächen-Steuer Elements klickt.

```
afx_msg void OnDropDown(
    NMHDR* pNMHDR,
    LRESULT* pResult);
```

### <a name="parameters"></a>Parameter

*pNMHDR*\
in Zeiger auf eine [NMHDR](/windows/win32/api/richedit/ns-richedit-nmhdr) -Struktur, die Informationen über die [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) Benachrichtigung enthält.

*pResult*\
vorgenommen (Wird nicht verwendet. es wird kein Wert zurückgegeben.) Rückgabewert der [BCN_DROPDOWN](/windows/win32/Controls/bcn-dropdown) Benachrichtigung.

### <a name="remarks"></a>Bemerkungen

Wenn der Benutzer auf den Dropdown Pfeil auf einem Trenn Schaltfläche-Steuerelement klickt, sendet das System eine BCN_DROPDOWN Benachrichtigungs Meldung, die von der `OnDropDown` Methode verarbeitet wird. Das- `CSplitButton` Objekt weiterleiten die BCN_DROPDOWN Benachrichtigung jedoch nicht an das-Steuerelement, das das Steuerelement für die unterteilte Schaltfläche enthält. Folglich kann das enthaltende Steuerelement eine benutzerdefinierte Aktion nicht als Antwort auf die Benachrichtigung unterstützen.

Um eine benutzerdefinierte Aktion zu implementieren, die das enthaltende Steuerelement unterstützt, verwenden Sie ein [CButton](../../mfc/reference/cbutton-class.md) -Objekt mit einem Stil von BS_SPLITBUTTON anstelle eines- `CSplitButton` Objekts. Implementieren Sie dann einen Handler für die BCN_DROPDOWN Benachrichtigung im- `CButton` Objekt. Weitere Informationen finden Sie unter [Schaltflächen Stile](../../mfc/reference/styles-used-by-mfc.md#button-styles).

Verwenden Sie [Nachrichten Reflektion](../../mfc/tn062-message-reflection-for-windows-controls.md), um eine benutzerdefinierte Aktion zu implementieren, die das Steuerelement für die unterteilte Schaltfläche Leiten Sie eine eigene Klasse von der `CSplitButton` -Klasse ab, und benennen Sie Sie, z. b. cmysplitbutton. Fügen Sie der Anwendung dann die folgende Meldungs Zuordnung hinzu, um die BCN_DROPDOWN Benachrichtigung zu behandeln:

```
BEGIN_MESSAGE_MAP(CMySplitButton,
    CSplitButton)
    ON_NOTIFY_REFLECT(BCN_DROPDOWN, &CMySplitButton::OnDropDown)
END_MESSAGE_MAP()
```

## <a name="csplitbuttonsetdropdownmenu"></a><a name="setdropdownmenu"></a> CSplitButton:: setdropdownmenu

Legt das Dropdown Menü fest, das angezeigt wird, wenn ein Benutzer auf den Dropdown Pfeil des aktuellen Steuer Elements für eine unterteilte Schaltfläche klickt.

```cpp
void SetDropDownMenu(
    UINT nMenuId,
    UINT nSubMenuId);

void SetDropDownMenu(CMenu* pMenu);
```

### <a name="parameters"></a>Parameter

*nmenuid*\
in Die Ressourcen-ID der Menüleiste.

*nsubmenuid*\
in Die Ressourcen-ID eines Untermenüs.

*pmenu*\
in Ein Zeiger auf ein [CMenu](../../mfc/reference/cmenu-class.md) -Objekt, das ein Untermenü angibt. Das `CSplitButton` -Objekt löscht das `CMenu` -Objekt und das zugehörige HMENU, wenn das Objekt den Gültigkeits `CSplitButton` Bereich verlässt.

### <a name="remarks"></a>Bemerkungen

Der *nmenuid* -Parameter identifiziert eine Menüleiste, bei der es sich um eine horizontale Liste von Menüleisten Elementen handelt. Der *nsubmenuid* -Parameter ist eine Null basierte Indexnummer, die ein Untermenü identifiziert. Dies ist die Dropdown Liste mit Menü Elementen, die jedem Menüleisten Element zugeordnet sind. Beispielsweise verfügt eine typische Anwendung über ein Menü, das die Menüleisten Elemente, "file", "Edit" und "Help" enthält. Das Menüleisten Element "Datei" enthält ein Untermenü mit den Menü Elementen "Öffnen", "Schließen" und "beenden". Wenn Sie auf den Dropdown Pfeil des Trenn Schaltflächen-Steuer Elements klicken, zeigt das-Steuerelement das angegebene Untermenü an, nicht die Menüleiste.

In der folgenden Abbildung wird ein Dialogfeld dargestellt, das ein Pager-Steuerelement und ein (1) Split Button-Steuerelement enthält. Auf den (2) Dropdown Pfeil wurde bereits geklickt, und das Untermenü (3) wird angezeigt.

![Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.](../../mfc/reference/media/splitbutton_pager.png "Dialogfeld mit einer Trennschaltfläche und einem Pagersteuerelement.")

### <a name="example"></a>Beispiel

Die erste Anweisung im folgenden Codebeispiel veranschaulicht die [CSplitButton:: setdropdownmenu](#setdropdownmenu) -Methode. Wir haben das Menü mit dem Ressourcen-Editor von Visual Studio erstellt, der automatisch die Menüleisten-ID IDR_MENU1. Der *nsubmenuid* -Parameter, der 0 (null) ist, verweist auf das einzige Untermenü der Menüleiste.

[!code-cpp[NVC_MFC_CSplitButton_s2#1](../../mfc/reference/codesnippet/cpp/csplitbutton-class_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CSplitButton-Klasse](../../mfc/reference/csplitbutton-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)
