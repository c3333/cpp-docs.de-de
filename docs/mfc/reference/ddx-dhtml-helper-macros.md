---
title: DDX_DHtml Hilfsobjekte
ms.date: 11/04/2016
f1_keywords:
- AFXDHTML/DDX_DHtml_ElementValue
- AFXDHTML/DDX_DHtml_ElementInnerText
- AFXDHTML/DDX_DHtml_ElementInnerHtml
- AFXDHTML/DDX_DHtml_Anchor_Href
- AFXDHTML/DDX_DHtml_Anchor_Target
- AFXDHTML/DDX_DHtml_Img_Src
- AFXDHTML/DDX_DHtml_Frame_Src
- AFXDHTML/DDX_DHtml_IFrame_Src
helpviewer_keywords:
- macros [MFC], exchanging data with HMTL pages
- DDX macros [MFC]
- HTML pages [MFC], helper macros
- DDX (dialog data exchange), DHtml helper macros
- macros [MFC], DDX_DHtml helpers
ms.assetid: c46302d2-ea43-4fea-bfc2-6f590d99f267
ms.openlocfilehash: 90c80dbc5c8b6788f3afad3cf77d796139fbd946
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866656"
---
# <a name="ddx_dhtml-helper-macros"></a>DDX_DHtml Hilfsobjekte

Die DDX_DHtml-Hilfsobjekte ermöglichen den einfachen Zugriff auf die häufig verwendeten Eigenschaften von Steuerelementen auf einer HTML-Seite.

### <a name="data-exchange-macros"></a>Datenaustausch Makros

|||
|-|-|
|[DDX_DHtml_ElementValue](#ddx_dhtml_elementvalue)|Legt die Value-Eigenschaft des ausgewählten Steuer Elements fest oder ruft Sie ab.|
|[DDX_DHtml_ElementInnerText](#ddx_dhtml_elementinnertext)|Legt den Text zwischen den Start-und Endtags des aktuellen Elements fest oder ruft diesen ab.|
|[DDX_DHtml_ElementInnerHtml](#ddx_dhtml_elementinnerhtml)|Legt den HTML-Code zwischen den Start-und Endtags des aktuellen Elements fest oder ruft diesen ab.|
|[DDX_DHtml_Anchor_Href](#ddx_dhtml_anchor_href)|Legt die Ziel-URL oder den Ankerpunkt fest oder ruft Sie ab.|
|[DDX_DHtml_Anchor_Target](#ddx_dhtml_anchor_target)|Legt das Zielfenster oder den Zielrahmen fest oder ruft es ab.|
|[DDX_DHtml_Img_Src](#ddx_dhtml_img_src)|Legt den Namen eines Bilds oder eines Videoclips im Dokument fest oder ruft ihn ab.|
|[DDX_DHtml_Frame_Src](#ddx_dhtml_frame_src)|Legt die URL des zugeordneten Frames fest oder ruft Sie ab.|
|[DDX_DHtml_IFrame_Src](#ddx_dhtml_iframe_src)|Legt die URL des zugeordneten Frames fest oder ruft Sie ab.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdhtml. h

## <a name="ddx_dhtml_anchor_href"></a>DDX_DHtml_Anchor_Href

Legt die Ziel-URL oder den Ankerpunkt fest oder ruft Sie ab.

```
DDX_DHtml_Anchor_Href(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLANCHORELEMENT_HREF Dispatch-ID auf.

## <a name="ddx_dhtml_anchor_target"></a>DDX_DHtml_Anchor_Target

Legt das Zielfenster oder den Zielrahmen fest oder ruft es ab.

```
DDX_DHtml_Anchor_Target(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLANCHORELEMENT_TARGET Dispatch-ID auf.

## <a name="ddx_dhtml_elementinnerhtml"></a>DDX_DHtml_ElementInnerHtml

Legt den HTML-Code zwischen den Start-und Endtags des aktuellen Elements fest oder ruft diesen ab.

```
DDX_DHtml_ElementInnerHtml(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLELEMENT_INNERHTML Dispatch-ID auf.

## <a name="ddx_dhtml_elementinnertext"></a>DDX_DHtml_ElementInnerText

Legt den Text zwischen den Start-und Endtags des aktuellen Elements fest oder ruft diesen ab.

```
DDX_DHtml_ElementInnerText(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLELEMENT_INNERTEXT Dispatch-ID auf.

## <a name="ddx_dhtml_elementvalue"></a>DDX_DHtml_ElementValue

Legt die Value-Eigenschaft des ausgewählten Steuer Elements fest oder ruft Sie ab.

```
DDX_DHtml_ElementValue(
    CDataExchange* dx,
    LPCTSTR name,
    var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert. Siehe *Wert* in [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext).

## <a name="remarks"></a>Bemerkungen

Dieses Makro ist nur erfolgreich, wenn es für Steuerelemente mit einer Value-Eigenschaft ausgeführt wird. Steuerelemente, die über eine Value-Eigenschaft verfügen, umfassen Bearbeitungsfelder, Listenfelder und Kombinations Felder.

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_A_VALUE Dispatch-ID auf.

## <a name="ddx_dhtml_frame_src"></a>DDX_DHtml_Frame_Src

Legt die URL des zugeordneten Frames fest oder ruft Sie ab.

```
DDX_DHtml_Frame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLFRAMEBASE_SRC Dispatch-ID auf.

## <a name="ddx_dhtml_iframe_src"></a>DDX_DHtml_IFrame_Src

Legt die URL des zugeordneten Frames fest oder ruft Sie ab.

```
DDX_DHtml_IFrame_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLFRAMEBASE_SRC Dispatch-ID auf.

## <a name="ddx_dhtml_img_src"></a>DDX_DHtml_Img_Src

Ruft den Namen eines Bilds oder eines Videoclips im Dokument ab oder ruft ihn ab.

```
DDX_DHtml_Img_Src(
    CDataExchange* dx,
    LPCTSTR name,
    CString& var)
```

#### <a name="parameters"></a>Parameter

*Market*<br/>
Ein Zeiger auf ein [CDataExchange](../../mfc/reference/cdataexchange-class.md) -Objekt.

*name*<br/>
Der Wert, den Sie für den ID-Parameter des HTML-Steuer Elements angegeben haben.

*var*<br/>
Der ausgetauschte Wert.

## <a name="remarks"></a>Bemerkungen

Wenn das DDX_DHtml_Img_Src-Makro zum Abrufen der src-Eigenschaft für ein Bildelement verwendet wird, gibt das Internet Explorer-Image Objekt die URL für den vollständigen Escapezeichen für die Bildquelle zurück. Wenn Sie z. b. das DDX_DHtml_Img_Src-Makro verwenden, um die src-Eigenschaft eines Bild Elements auf die Zeichenfolge "Some interessantes Bild" festzulegen, gibt Internet Explorer beim Abrufen dieser Eigenschaft die Zeichenfolge "res: Knotens"//d: \ MyApplication \ MyApp. exe/some %2 0 interessantiges %2 0 Bild "zurück.

Dieses Makro ruft die [CDHtmlDialog::D DX_DHtml_ElementText](../../mfc/reference/cdhtmldialog-class.md#ddx_dhtml_elementtext) -Funktion mithilfe der DISPID_IHTMLIMGELEMENT_SRC Dispatch-ID auf.

## <a name="see-also"></a>Weitere Informationen

[CDHtmlDialog-Klasse](../../mfc/reference/cdhtmldialog-class.md)
