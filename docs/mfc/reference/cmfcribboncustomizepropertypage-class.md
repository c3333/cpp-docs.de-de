---
title: Cmscribboncustomizepropertypage-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::AddCustomCategory
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizePropertyPage::OnOK
helpviewer_keywords:
- CMFCRibbonCustomizePropertyPage [MFC], CMFCRibbonCustomizePropertyPage
- CMFCRibbonCustomizePropertyPage [MFC], AddCustomCategory
- CMFCRibbonCustomizePropertyPage [MFC], OnOK
ms.assetid: ea32a99a-dfbe-401e-8975-aa191552532f
ms.openlocfilehash: 92408e91b41b474da3a2da6ad0646feb3a6b8fc2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831839"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>Cmscribboncustomizepropertypage-Klasse

Implementiert eine benutzerdefinierte Seite für das Dialogfeld " **Anpassen** " in Menü bandbasierten Anwendungen.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|-|-|
|[CMF cribboncustomizepropertypage:: CMF cribboncustomizepropertypage](#cmfcribboncustomizepropertypage)|Erstellt ein `CMFCRibbonCustomizePropertyPage`-Objekt.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|-|-|
|[CMF cribboncustomizepropertypage:: addcustomcategory](#addcustomcategory)|Fügt dem Kombinations Feld **Befehle** eine benutzerdefinierte Kategorie hinzu.|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) -Objekt abzurufen, das diesem Klassentyp zugeordnet ist.|
|[CMF cribboncustomizepropertypage:: OnOK](#onok)|Wird vom System aufgerufen, wenn ein Benutzer im Dialogfeld **Anpassen** auf **OK** klickt.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie dem Dialogfeld " **Anpassen** " benutzerdefinierte Befehle hinzufügen möchten, müssen Sie die AFX_WM_ON_RIBBON_CUSTOMIZE Nachricht verarbeiten. Instanziieren Sie im Nachrichten Handler ein- `CMFCRibbonCustomizePropertyPage` Objekt auf dem Stapel. Erstellen Sie eine Liste mit benutzerdefinierten Befehlen, und rufen `AddCustomCategory` Sie dann auf, um die neue Seite dem Dialogfeld **Anpassen** hinzuzufügen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie ein `CMFCRibbonCustomizePropertyPage` -Objekt erstellen und eine benutzerdefinierte Kategorie hinzufügen.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMF cribboncustomizepropertypage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxribboncustomizedialog. h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a> CMF cribboncustomizepropertypage:: addcustomcategory

Fügt dem Kombinations Feld **Befehle** eine benutzerdefinierte Kategorie hinzu.

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parameter

*lpszname*\
in Gibt den Namen der benutzerdefinierten Kategorie an.

*lstids*\
in Enthält Menüband-Befehls-IDs, die in der benutzerdefinierten Kategorie angezeigt werden.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt dem Kombinations Feld **Befehle** eine Kategorie mit dem Namen *lpszname* hinzu. Wenn der Benutzer die Kategorie auswählt, werden die in *lstids* angegebenen Befehle in der Befehlsliste angezeigt.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a> CMF cribboncustomizepropertypage:: CMF cribboncustomizepropertypage

Erstellt ein `CMFCRibbonCustomizePropertyPage`-Objekt.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parameter

*pribbonbar*<br/>
in Ein Zeiger auf ein Menüband-Steuerelement, für das die Optionen angepasst werden können.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a> CMF cribboncustomizepropertypage:: OnOK

Calleld vom System, wenn ein Benutzer im Dialogfeld **Anpassen** auf **OK** klickt.

```
virtual void OnOK();
```

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung wendet die im Dialogfeld **Anpassen** ausgewählten Optionen auf die Symbolleiste für den schnell Zugriff an.

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
