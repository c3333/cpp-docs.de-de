---
title: CMultiPageDHtmlDialog-Klasse
ms.date: 03/27/2019
f1_keywords:
- CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog
- AFXDHTML/CMultiPageDHtmlDialog::CMultiPageDHtmlDialog
helpviewer_keywords:
- CMultiPageDHtmlDialog [MFC], CMultiPageDHtmlDialog
ms.assetid: 971accc1-824d-4df4-b4c1-b1a20e0f7e4f
ms.openlocfilehash: 89e4830c3b5c6cb663ca2d2935adaaae3f356958
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319664"
---
# <a name="cmultipagedhtmldialog-class"></a>CMultiPageDHtmlDialog-Klasse

Ein mehrseitiges Dialogfeld zeigt mehrere HTML-Seiten sequenziell an und behandelt die Ereignisse jeder Seite.

## <a name="syntax"></a>Syntax

```
class CMultiPageDHtmlDialog : public CDHtmlDialog
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMultiPageDHtmlDialog::CMultiPageDHtmlDialog](#cmultipagedhtmldialog)|Erstellt ein mehrseitiges DHTML-Dialogobjekt (Wizard-Stil).|
|[CMultiPageDHtmlDialog::'CMultiPageDHtmlDialog](#_dtorcmultipagedhtmldialog)|Zerstört ein mehrseitiges DHTML-Dialogobjekt.|

## <a name="remarks"></a>Bemerkungen

Der Mechanismus hierfür ist eine [DHTML- und URL-Ereigniszuordnung](dhtml-event-maps.md), die eingebettete Ereigniszuordnungen für jede Seite enthält.

## <a name="example"></a>Beispiel

Dieses mehrseitige Dialogfeld setzt drei HTML-Ressourcen voraus, die einfache Assistenten-ähnliche Funktionen definieren. Die erste Seite hat eine **Schaltfläche Weiter,** die zweite eine **Prev-** und eine **Next-Schaltfläche** und die dritte eine **Prev-Schaltfläche.** Wenn eine der Schaltflächen gedrückt wird, ruft eine Handlerfunktion [CDHtmlDialog::LoadFromResource](../../mfc/reference/cdhtmldialog-class.md#loadfromresource) auf, um die entsprechende neue Seite zu laden.

Die relevanten Teile der Klassendeklaration (in CMyMultiPageDlg.h):

[!code-cpp[NVC_MFCDocView#181](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_1.h)]

Die relevanten Teile der Klassenimplementierung (in CMyMultipageDlg.cpp):

[!code-cpp[NVC_MFCDocView#182](../../mfc/codesnippet/cpp/cmultipagedhtmldialog-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

[CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)

`CMultiPageDHtmlDialog`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdhtml.h

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="cmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::CMultiPageDHtmlDialog

Erstellt ein mehrseitiges DHTML-Dialogobjekt (Wizard-Stil).

```
CMultiPageDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID = NULL,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd* pParentWnd = NULL);

CMultiPageDHtmlDialog();
```

### <a name="parameters"></a>Parameter

*lpszTemplateName*<br/>
Die null-terminierte Zeichenfolge, die der Name einer Dialogfeldvorlagenressource ist.

*szHtmlResID*<br/>
Die null-terminierte Zeichenfolge, die der Name einer HTML-Ressource ist.

*pParentWnd*<br/>
Ein Zeiger auf das übergeordnete oder Besitzerfensterobjekt (vom Typ [CWnd](../../mfc/reference/cwnd-class.md)), zu dem das Dialogobjekt gehört. Wenn es SICH um NULL handelt, wird das übergeordnete Fenster des Dialogobjekts auf das Hauptanwendungsfenster festgelegt.

*nIDTemplate*<br/>
Enthält die ID-Nummer einer Dialogfeldvorlagenressource.

*nHtmlResID*<br/>
Enthält die ID-Nummer einer HTML-Ressource.

## <a name="cmultipagedhtmldialogcmultipagedhtmldialog"></a><a name="_dtorcmultipagedhtmldialog"></a>CMultiPageDHtmlDialog::'CMultiPageDHtmlDialog

Zerstört ein mehrseitiges DHTML-Dialogobjekt.

```
virtual ~CMultiPageDHtmlDialog();
```

## <a name="see-also"></a>Siehe auch

[CDHtmlDialog-Klasse](../../mfc/reference/cdhtmldialog-class.md)
