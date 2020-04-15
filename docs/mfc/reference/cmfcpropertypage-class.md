---
title: CMFCPropertyPage-Klasse
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage
- AFXPROPERTYPAGE/CMFCPropertyPage::CMFCPropertyPage
helpviewer_keywords:
- CMFCPropertyPage [MFC], CMFCPropertyPage
ms.assetid: d279d7f2-2d81-418d-9f23-6147d6e8df09
ms.openlocfilehash: e493f016b6384a768935186c31e3fc71ade6382f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361757"
---
# <a name="cmfcpropertypage-class"></a>CMFCPropertyPage-Klasse

Die `CMFCPropertyPage` Klasse unterstützt die Anzeige von Popupmenüs auf einer Eigenschaftenseite.

## <a name="syntax"></a>Syntax

```
class CMFCPropertyPage : public CPropertyPage
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMFCPropertyPage::CMFCPropertyPage](#cmfcpropertypage)|Erstellt ein `CMFCPropertyPage`-Objekt.|
|`CMFCPropertyPage::~CMFCPropertyPage`|Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|`CMFCPropertyPage::CreateObject`|Wird vom Framework verwendet, um eine dynamische Instanz dieses Klassentyps zu erstellen.|
|`CMFCPropertyPage::GetThisClass`|Wird vom Framework verwendet, um einen Zeiger auf das [CRuntimeClass-Objekt](../../mfc/reference/cruntimeclass-structure.md) abzuholen, das diesem Klassentyp zugeordnet ist.|
|`CMFCPropertyPage::OnSetActive`|Diese Memberfunktion wird vom Framework aufgerufen, wenn die Seite vom Benutzer ausgewählt wird und zur aktiven Seite wird. (Überschreibt [CPropertyPage::OnSetActive](../../mfc/reference/cpropertypage-class.md#onsetactive).)|
|`CMFCPropertyPage::PreTranslateMessage`|Übersetzt Fensternachrichten, bevor sie an die [TranslateMessage-](/windows/win32/api/winuser/nf-winuser-translatemessage) und [DispatchMessage-Windows-Funktionen](/windows/win32/api/winuser/nf-winuser-dispatchmessage) gesendet werden. Weitere Informationen und Methodensyntax finden Sie unter [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage). (Überschreibt `CPropertyPage::PreTranslateMessage`.)|

## <a name="remarks"></a>Bemerkungen

Die `CMFCPropertyPage` Klasse stellt einzelne Seiten eines Eigenschaftenblatts dar, das auch als Registerkartendialogfeld bezeichnet wird.

Verwenden `CMFCPropertyPage` Sie die Klasse zusammen mit der [CMFCPropertySheet-Klasse.](../../mfc/reference/cmfcpropertysheet-class.md) Um Menüs auf einer Eigenschaftenseite zu verwenden, ersetzen Sie alle Vorkommen der `CPropertyPage` Klasse durch die `CMFCPropertyPage` Klasse.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CPropertyPage](../../mfc/reference/cpropertypage-class.md)

[CMFCPropertyPage](../../mfc/reference/cmfcpropertypage-class.md)

## <a name="requirements"></a>Anforderungen

**Kopf:** afxpropertypage.h

## <a name="cmfcpropertypagecmfcpropertypage"></a><a name="cmfcpropertypage"></a>CMFCPropertyPage::CMFCPropertyPage

Erstellt ein `CMFCPropertyPage`-Objekt.

```
CMFCPropertyPage(
    UINT nIDTemplate,
    UINT nIDCaption=0);

CMFCPropertyPage(
    LPCTSTR lpszTemplateName,
    UINT nIDCaption=0);
```

### <a name="parameters"></a>Parameter

*nIDTemplate*<br/>
Ressourcen-ID der Vorlage für diese Seite.

*nIDCaption*<br/>
Ressourcen-ID der Bezeichnung, die auf der Registerkarte für diese Seite angezeigt werden soll. Wenn 0, wird der Name aus der Dialogfeldvorlage für diese Seite abgerufen. Der Standardwert ist 0.

*lpszTemplateName*<br/>
Zeigt auf den Namen der Vorlage für diese Seite. Lässt keine NULL-Werte zu.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu den Konstruktorparametern finden Sie unter [CPropertyPage::CPropertyPage](../../mfc/reference/cpropertypage-class.md#cpropertypage).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertySheet-Klasse](../../mfc/reference/cmfcpropertysheet-class.md)
