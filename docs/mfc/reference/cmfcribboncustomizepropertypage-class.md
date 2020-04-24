---
title: CMFCRibbonCustomizePropertyPage-Klasse
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
ms.openlocfilehash: 57fbd1e1f574beebff8baab014e7ab615f56333f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754173"
---
# <a name="cmfcribboncustomizepropertypage-class"></a>CMFCRibbonCustomizePropertyPage-Klasse

Implementiert eine benutzerdefinierte Seite für das Dialogfeld **Anpassen** in Multifunktionsleisten-basierten Anwendungen.

## <a name="syntax"></a>Syntax

```
class CMFCRibbonCustomizePropertyPage: public CMFCPropertyPage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage](#cmfcribboncustomizepropertypage)|Erstellt ein `CMFCRibbonCustomizePropertyPage`-Objekt.|
|`CMFCRibbonCustomizePropertyPage::~CMFCRibbonCustomizePropertyPage`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|||
|-|-|
|Name|BESCHREIBUNG|
|[CMFCRibbonCustomizePropertyPage::AddCustomCategory](#addcustomcategory)|Fügt dem **Kombinationsfeld Befehle** eine benutzerdefinierte Kategorie hinzu.|
|`CMFCRibbonCustomizePropertyPage::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCRibbonCustomizePropertyPage::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|[CMFCRibbonCustomizePropertyPage::OnOK](#onok)|Wird vom System aufgerufen, wenn ein Benutzer im Dialogfeld **Anpassen** auf **OK** klickt.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie dem Dialogfeld **Anpassen** benutzerdefinierte Befehle hinzufügen möchten, müssen Sie die AFX_WM_ON_RIBBON_CUSTOMIZE Nachricht behandeln. Instanziieren Sie im Nachrichtenhandler `CMFCRibbonCustomizePropertyPage` ein Objekt auf dem Stapel. Erstellen Sie eine Liste benutzerdefinierter Befehle, und rufen Sie dann auf, `AddCustomCategory` um die neue Seite dem Dialogfeld **Anpassen** hinzuzufügen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird `CMFCRibbonCustomizePropertyPage` veranschaulicht, wie ein Objekt erstellt und eine benutzerdefinierte Kategorie hinzugefügt wird.

[!code-cpp[NVC_MFC_RibbonApp#22](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizepropertypage-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

[CMFCRibbonCustomizePropertyPage](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxribboncustomizedialog.h

## <a name="cmfcribboncustomizepropertypageaddcustomcategory"></a><a name="addcustomcategory"></a>CMFCRibbonCustomizePropertyPage::AddCustomCategory

Fügt dem **Kombinationsfeld Befehle** eine benutzerdefinierte Kategorie hinzu.

```cpp
void AddCustomCategory(
    LPCTSTR lpszName,
    const CList<UINT, UINT>& lstIDS);
```

### <a name="parameters"></a>Parameter

|||
|-|-|
|Parameter|Beschreibung|
|*lpszName*|[in] Gibt den benutzerdefinierten Kategorienamen an.|
|*lstIDS*|[in] Enthält Multifunktionsleistenbefehls-IDs, die in der benutzerdefinierten Kategorie angezeigt werden sollen.|

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt dem Kombinationsfeld **Befehle** eine Kategorie mit dem Namen *lpszName* hinzu. Wenn der Benutzer die Kategorie auswählt, werden die in *lstIDS* angegebenen Befehle in der Befehlsliste angezeigt.

## <a name="cmfcribboncustomizepropertypagecmfcribboncustomizepropertypage"></a><a name="cmfcribboncustomizepropertypage"></a>CMFCRibbonCustomizePropertyPage::CMFCRibbonCustomizePropertyPage

Erstellt ein `CMFCRibbonCustomizePropertyPage`-Objekt.

```
CMFCRibbonCustomizePropertyPage(CMFCRibbonBar* pRibbonBar = NULL);
```

### <a name="parameters"></a>Parameter

*pRibbonBar*<br/>
[in] Ein Zeiger auf ein Menübandsteuerelement, für das die Optionen angepasst werden sollen.

## <a name="cmfcribboncustomizepropertypageonok"></a><a name="onok"></a>CMFCRibbonCustomizePropertyPage::OnOK

Vom System angerufen, wenn ein Benutzer im Dialogfeld **Anpassen** auf **OK** klickt.

```
virtual void OnOK();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung wendet die im Dialogfeld **Anpassen** ausgewählten Optionen auf die Schnellzugriffssymbolleiste an.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)
