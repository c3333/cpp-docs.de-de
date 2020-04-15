---
title: CMFCToolBarComboBoxEdit-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxEdit::CMFCToolBarComboBoxEdit
helpviewer_keywords:
- CMFCToolBarComboBoxEdit [MFC], CMFCToolBarComboBoxEdit
ms.assetid: 4789c34a-ce58-48ba-a26f-38748b601352
ms.openlocfilehash: dfbf24f5833d143adc6d21b6cb54dd9ac81c2f0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372200"
---
# <a name="cmfctoolbarcomboboxedit-class"></a>CMFCToolBarComboBoxEdit-Klasse

Das Framework `CMFCToolBarComboBoxEdit` verwendet die Klasse, um eine Symbolleistenschaltfläche zu erstellen, die sich wie ein bearbeitbares Kombinationsfeldsteuerelement verhält.

## <a name="syntax"></a>Syntax

```
class CMFCToolBarComboBoxEdit : public CEdit
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCToolBarComboBoxBearbeiten::CMFCToolBarComboBoxBearbeiten](#cmfctoolbarcomboboxedit)|Erstellt ein `CMFCToolBarComboBoxEdit`-Objekt.|
|`CMFCToolBarComboBoxEdit::~CMFCToolBarComboBoxEdit`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCToolBarComboBoxEdit::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. (Überschreibt [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|

### <a name="remarks"></a>Bemerkungen

Leiten Sie eine `CMFCToolBarComboBoxEdit` Klasse von der Klasse ab, um ihre Bearbeitungsvorgänge anzupassen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxtoolbarcomboboxbutton.h

## <a name="cmfctoolbarcomboboxeditcmfctoolbarcomboboxedit"></a><a name="cmfctoolbarcomboboxedit"></a>CMFCToolBarComboBoxBearbeiten::CMFCToolBarComboBoxBearbeiten

Erstellt ein `CMFCToolBarComboBoxEdit`-Objekt.

```
CMFCToolBarComboBoxEdit(CMFCToolBarComboBoxButton& combo);
```

### <a name="parameters"></a>Parameter

*Verbunddiagramm*<br/>
[in] Ein Verweis auf ein [CMFCToolBarComboBoxButton-Objekt,](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md) bei dem es sich um eine Symbolleistenschaltfläche handelt, die ein Kombinationsfeldsteuerelement enthält.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMFCToolBarComboBoxEdit` wie ein Objekt der Klasse erstellt wird. Dieser Codeausschnitt ist Teil des [IE-Demobeispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_IEDemo#5](../../mfc/reference/codesnippet/cpp/cmfctoolbarcomboboxedit-class_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarComboBoxButton-Klasse](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)
