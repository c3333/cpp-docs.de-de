---
title: CMFCPropertyGridFileProperty-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360578"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty-Klasse

Die `CMFCPropertyGridFileProperty` Klasse unterstützt ein Eigenschaftenlistensteuerelement, das ein Dialogfeld für die Dateiauswahl öffnet.

## <a name="syntax"></a>Syntax

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|Erstellt ein `CMFCPropertyGridFileProperty`-Objekt.|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|`CMFCPropertyGridFileProperty::OnClickButton`|(Überschreibt [CMFCPropertyGridProperty::OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>Bemerkungen

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

Erstellt ein `CMFCPropertyGridFileProperty`-Objekt.

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>Parameter

*strName*<br/>
[in] Der Name der Eigenschaft.

*bOpenFileDialog*<br/>
[in] TRUE, um ein Dialogfeld **"Datei öffnen"** zu öffnen; FALSE, um ein Dialogfeld **Datei speichern** zu öffnen.

*strFileName*<br/>
[in] Der ursprüngliche Dateiname.

*lpszDefExt*<br/>
[in] Eine Zeichenfolge aus einer oder mehreren Dateinamenerweiterungen. Der Standardwert ist NULL.

*dwFlags*<br/>
[in] Dialogfeldflags. Der Standardwert ist eine bitweise Kombination (OR) von OFN_HIDEREADONLY und OFN_OVERWRITEPROMPT.

*lpszFilter*<br/>
[in] Eine Zeichenfolge aus einem oder mehreren Dateifiltern. Der Standardwert ist NULL.

*lpszDescr*<br/>
[in] Die Eigenschaftenelementbeschreibung. Der Standardwert ist NULL.

*dwData*<br/>
[in] Anwendungsspezifische Daten, die dem Eigenschaftselement zugeordnet sind. Zum Beispiel eine 32-Bit-Ganzzahl oder ein Zeiger auf andere Daten. Der Standardwert ist 0.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Eine vollständige Liste der verfügbaren Flags finden Sie unter [OPENFILENAME-Struktur](/windows/win32/api/commdlg/ns-commdlg-openfilenamew).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Objekt mit dem Konstruktor der `CMFCPropertyGridFileProperty` Klasse erstellt wird. Dieses Beispiel ist Teil des [Visual Studio-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl-Klasse](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty-Klasse](../../mfc/reference/cmfcpropertygridproperty-class.md)
