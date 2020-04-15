---
title: DHTML-Ereigniszuordnungen
ms.date: 11/04/2016
f1_keywords:
- vc.macros.shared
helpviewer_keywords:
- event map macros [MFC]
- DHTML [MFC], event map macros
- macros [MFC], DHTML event map
- DHTML events [MFC], event map
- DHTML events [MFC]
ms.assetid: 9a2c8ae7-7216-4a5e-bc60-6b98695be0c6
ms.openlocfilehash: 30c755b2901374cffab3ce91d0683811ef6624b6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365804"
---
# <a name="dhtml-event-maps"></a>DHTML-Ereigniszuordnungen

Die folgenden Makros können zum Behandeln von DHTML-Ereignissen verwendet werden.

## <a name="dhtml-event-map-macros"></a>DHTML-Ereigniszuordnungsmakros

Die folgenden Makros können verwendet werden, um DHTML-Ereignisse in [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-derived-Klassen zu behandeln.

|||
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Markiert den Anfang der DHTML-Ereigniszuordnung.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Markiert den Anfang der DHTML-Ereigniszuordnung.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklariert die DHTML-Ereigniszuordnung.|
|[DHTML_EVENT](#dhtml_event)|Wird verwendet, um ein Ereignis auf Dokumentebene für ein einzelnes HTML-Element zu behandeln.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Wird verwendet, um ein Ereignis zu behandeln, das von einem ActiveX-Steuerelement ausgelöst wird.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Wird verwendet, um ein Ereignis auf Dokumentebene für alle HTML-Elemente mit einer bestimmten CSS-Klasse zu behandeln.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Wird verwendet, um ein Ereignis auf Elementebene zu behandeln.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Wird verwendet, `onafterupdate` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Wird verwendet, `onbeforeupdate` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Wird verwendet, `onblur` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Wird verwendet, `onchange` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Wird verwendet, `onclick` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Wird verwendet, `ondataavailable` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Wird verwendet, `ondatasetchanged` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Wird verwendet, `ondatasetcomplete` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Wird verwendet, `ondblclick` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Wird verwendet, `ondragstart` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Wird verwendet, `onerrorupdate` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Wird verwendet, `onfilterchange` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Wird verwendet, `onfocus` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Wird verwendet, `onhelp` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Wird verwendet, `onkeydown` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Wird verwendet, `onkeypress` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Wird verwendet, `onkeyup` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Wird verwendet, `onmousedown` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Wird verwendet, `onmousemove` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Wird verwendet, `onmouseout` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Wird verwendet, `onmouseover` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Wird verwendet, `onmouseup` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Wird verwendet, `onresize` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Wird verwendet, `onrowenter` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Wird verwendet, `onrowexit` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Wird verwendet, `onselectstart` um das Ereignis aus einem HTML-Element zu behandeln.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Wird verwendet, um ein Ereignis auf Dokumentebene für alle Elemente mit einem bestimmten HTML-Tag zu behandeln.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Markiert das Ende der DHTML-Ereigniszuordnung.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Markiert das Ende der DHTML-Ereigniszuordnung. |

## <a name="url-event-map-macros"></a>URL-Ereigniskartenmakros

Die folgenden Makros können verwendet werden, um DHTML-Ereignisse in [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-derived-Klassen zu behandeln.

|||
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Markiert den Start der mehrseitigen DHTML- und URL-Ereigniszuordnung.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Markiert den Beginn einer eingebetteten DHTML-Ereigniszuordnung.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Markiert den Beginn einer URL-Ereigniseintragszuordnung.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklariert die mehrseitige DHTML- und URL-Ereigniszuordnung.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Markiert das Ende der mehrseitigen DHTML- und URL-Ereigniszuordnung.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Markiert das Ende einer eingebetteten DHTML-Ereigniszuordnung.|
|[END_URL_ENTRIES](#end_url_entries)|Markiert das Ende einer URL-Ereigniseintragszuordnung.|
|[URL_EVENT_ENTRY](#url_event_entry)|Ordnet eine URL oder HTML-Ressource einer Seite in einem mehrseitigen Dialogfeld zu.|

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a>BEGIN_DHTML_EVENT_MAP

Markiert den Anfang der DHTML-Ereigniszuordnung, wenn er in `className`der Quelldatei für die von identifizierte Klasse platziert wird.

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die DHTML-Ereigniszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) abstammen und das [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) Makros in ihre Klassendefinition einbeziehen.

### <a name="remarks"></a>Bemerkungen

Fügen Sie Ihrer Klasse eine DHTML-Ereigniszuordnung hinzu, um Informationen `CDHtmlDialog` bereitzustellen, die zum Weiterleiten von Ereignissen verwendet werden können, die von HTML-Elementen oder ActiveX-Steuerelementen in einer Webseite ausgelöst werden, um Funktionen in Ihrer Klasse zu verwenden.

Platzieren Sie das BEGIN_DHTML_EVENT_MAP-Makro in der Implementierungsdatei (.cpp) der Klasse, gefolgt von DHTML_EVENT Makros für die Ereignisse, die die Klasse verarbeiten soll (z. B. DHTML_EVENT_ONMOUSEOVER für Mouseover-Ereignisse). Verwenden [END_DHTML_EVENT_MAP](#end_dhtml_event_map) Sie das END_DHTML_EVENT_MAP-Makro, um das Ende der Ereigniszuordnung zu markieren. Diese Makros implementieren die folgende Funktion:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a>BEGIN_DHTML_EVENT_MAP_INLINE

Markiert den Anfang der DHTML-Ereigniszuordnung innerhalb der Klassendefinition für *className*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die DHTML-Ereigniszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) abstammen und das [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) Makros in ihre Klassendefinition einbeziehen.

### <a name="remarks"></a>Bemerkungen

Fügen Sie Ihrer Klasse eine DHTML-Ereigniszuordnung hinzu, um Informationen `CDHtmlDialog` bereitzustellen, die zum Weiterleiten von Ereignissen verwendet werden können, die von HTML-Elementen oder ActiveX-Steuerelementen in einer Webseite ausgelöst werden, um Funktionen in Ihrer Klasse zu verwenden.

Platzieren Sie das BEGIN_DHTML_EVENT_MAP-Makro in der Definitionsdatei (.h) der Klasse, gefolgt von DHTML_EVENT Makros für die Ereignisse, die die Klasse behandeln soll (z. B. DHTML_EVENT_ONMOUSEOVER für Mouseover-Ereignisse). Verwenden [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) Sie das END_DHTML_EVENT_MAP_INLINE-Makro, um das Ende der Ereigniszuordnung zu markieren. Diese Makros implementieren die folgende Funktion:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a>DECLARE_DHTML_EVENT_MAP

Deklariert eine DHTML-Ereigniszuordnung in einer Klassendefinition.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in der Definition von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-abgeleiteten Klassen verwendet.

Verwenden Sie [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) oder [BEGIN_DHTML_EVENT_MAP_INLINE,](#begin_dhtml_event_map_inline) um die Karte zu implementieren.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) deklariert die folgende Funktion:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event"></a><a name="dhtml_event"></a>DHTML_EVENT

Behandelt (auf Dokumentebene) ein Ereignis, das durch *Dispid* identifiziert wird, das durch das HTML-Element stammt, das durch *elemName*identifiziert wird.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Die DISPID des zu behandelnden Ereignisses.

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft, oder NULL, um Dokumentereignisse zu behandeln.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a>DHTML_EVENT_AXCONTROL

Behandelt das Ereignis, das durch *Dispid* identifiziert wird, das vom ActiveX-Steuerelement ausgelöst wird, das von *controlName*identifiziert wird.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*controlName*<br/>
Ein LPCWSTR, der die HTML-ID des Steuerelements beim Auslösen des Ereignisses hält.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a>DHTML_EVENT_CLASS

Behandelt (auf Dokumentebene) ein Ereignis, das durch *Dispid* identifiziert wird, das von einem HTML-Element mit der CSS-Klasse stammt, die durch *elemName*identifiziert wird.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*elemName*<br/>
Ein LPCWSTR, der die CSS-Klasse der HTML-Elemente enthält, die das Ereignis beschaffen.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a>DHTML_EVENT_ELEMENT

Behandelt (an dem von *elemName*identifizierten Element ) ein Ereignis, das durch *dispid*identifiziert wird.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

Wenn dieses Makro zum Behandeln von nicht bubbling-Ereignissen verwendet wird, ist die Quelle des Ereignisses das von *elemName*identifizierte Element.

Wenn dieses Makro zum Behandeln von bubbling-Ereignissen verwendet wird, ist das von *elemName* identifizierte Element möglicherweise nicht die Quelle des Ereignisses (die Quelle könnte ein beliebiges Element sein, das in *elemName*enthalten ist).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a>DHTML_EVENT_ONAFTERUPDATE

Behandelt (auf Dokumentebene) `onafterupdate` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a>DHTML_EVENT_ONBEFOREUPDATE

Behandelt (auf Dokumentebene) `onbeforeupdate` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a>DHTML_EVENT_ONBLUR

Behandelt (auf Elementebene) `onblur` das Ereignis. Dies ist ein nicht bubbling Ereignis.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a>DHTML_EVENT_ONCHANGE

Behandelt (auf Elementebene) `onchange` das Ereignis. Dies ist ein nicht bubbling Ereignis.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a>DHTML_EVENT_ONCLICK

Behandelt (auf Dokumentebene) `onclick` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a>DHTML_EVENT_ONDATAAVAILABLE

Behandelt (auf Dokumentebene) `ondataavailable` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a>DHTML_EVENT_ONDATASETCHANGED

Behandelt (auf Dokumentebene) `ondatasetchanged` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a>DHTML_EVENT_ONDATASETCOMPLETE

Behandelt (auf Dokumentebene) `ondatasetcomplete` das Ereignis, das vom `elemName`HTML-Element stammt, das durch identifiziert wurde.

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a>DHTML_EVENT_ONDBLCLICK

Behandelt (auf Dokumentebene) `ondblclick` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a>DHTML_EVENT_ONDRAGSTART

Behandelt (auf Dokumentebene) `ondragstart` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a>DHTML_EVENT_ONERRORUPDATE

Behandelt (auf Dokumentebene) `onerrorupdate` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a>DHTML_EVENT_ONFILTERCHANGE

Behandelt (auf Dokumentebene) `onfilterchange` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a>DHTML_EVENT_ONFOCUS

Behandelt (auf Elementebene) `onfocus` das Ereignis. Dies ist ein nicht bubbling Ereignis.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a>DHTML_EVENT_ONHELP

Behandelt (auf Dokumentebene) `onhelp` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a>DHTML_EVENT_ONKEYDOWN

Behandelt (auf Dokumentebene) `onkeydown` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a>DHTML_EVENT_ONKEYPRESS

Behandelt (auf Dokumentebene) `onkeypress` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a>DHTML_EVENT_ONKEYUP

Behandelt (auf Dokumentebene) `onkeyup` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a>DHTML_EVENT_ONMOUSEDOWN

Behandelt (auf Dokumentebene) `onmousedown` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a>DHTML_EVENT_ONMOUSEMOVE

Behandelt (auf Dokumentebene) `onmousemove` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a>DHTML_EVENT_ONMOUSEOUT

Behandelt (auf Dokumentebene) `onmouseout` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a>DHTML_EVENT_ONMOUSEOVER

Behandelt (auf Dokumentebene) `onmouseover` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a>DHTML_EVENT_ONMOUSEUP

Behandelt (auf Dokumentebene) `onmouseup` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a>DHTML_EVENT_ONRESIZE

Behandelt (auf Elementebene) `onresize` das Ereignis. Dies ist ein nicht bubbling Ereignis.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a>DHTML_EVENT_ONROWENTER

Behandelt (auf Dokumentebene) `onrowenter` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a>DHTML_EVENT_ONROWEXIT

Behandelt (auf Dokumentebene) `onrowexit` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a>DHTML_EVENT_ONSELECTSTART

Behandelt (auf Dokumentebene) `onselectstart` das Ereignis, das vom HTML-Element stammt, das durch *elemName*identifiziert wurde.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*elemName*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a>DHTML_EVENT_TAG

Behandelt (auf Dokumentebene) ein Ereignis, das durch `dispid` ein beliebiges HTML-Element mit dem html-Tag identifiziert wurde, das durch *elemName*identifiziert wird.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*Dispid*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*elemName*<br/>
Das HTML-Tag der HTML-Elemente, die das Ereignis beschaffen.

*MemberFxn*<br/>
Die Handlerfunktion für das Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereigniszuordnung](#begin_dhtml_event_map_inline) in Ihrer Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a>END_DHTML_EVENT_MAP

Markiert das Ende der DHTML-Ereigniszuordnung.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Muss in Verbindung mit [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)verwendet werden.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a>BEGIN_DHTML_URL_EVENT_MAP

Startet die Definition einer DHTML- und URL-Ereigniszuordnung in einem mehrseitigen Dialogfeld.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Legen Sie BEGIN_DHTML_URL_EVENT_MAP in die Implementierungsdatei Ihrer [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-derived-Klasse. Folgen Sie ihm mit [eingebetteten DHTML-Ereigniszuordnungen](#begin_embed_dhtml_event_map) und [URL-Einträgen](#begin_url_entries), und schließen Sie es dann mit [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Schließen Sie das [DECLARE_DHTML_URL_EVENT_MAP-Makro](#declare_dhtml_url_event_map) in die Klassendefinition ein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a>BEGIN_EMBED_DHTML_EVENT_MAP

Startet die Definition einer eingebetteten DHTML-Ereigniszuordnung in einem mehrseitigen Dialogfeld.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die Ereigniszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)ableiten. Die eingebettete DHTML-Ereigniszuordnung muss sich in einer [DHTML- und URL-Ereigniszuordnung befinden.](#begin_dhtml_url_event_map)

*mapName*<br/>
Gibt die Seite an, deren Ereigniszuordnung dies ist. Dies entspricht *mapName* im [URL_EVENT_ENTRY](#url_event_entry) Makro, das die URL oder HTML-Ressource tatsächlich definiert.

### <a name="remarks"></a>Bemerkungen

Da ein mehrseitiges DHTML-Dialogfeld aus mehreren HTML-Seiten besteht, von denen jede DHTML-Ereignisse aussetzen kann, werden eingebettete Ereigniszuordnungen verwendet, um Handlern pro Seite Ereignisse zuzuordnen.

Eingebettete Ereigniszuordnungen in einer DHTML- und URL-Ereigniszuordnung bestehen aus einem BEGIN_EMBED_DHTML_EVENT_MAP-Makro gefolgt von [DHTML_EVENT](#dhtml_event) Makros und einem [END_EMBED_DHTML_EVENT_MAP-Makro.](#end_embed_dhtml_event_map)

Jede eingebettete Ereigniszuordnung erfordert einen entsprechenden [URL-Ereigniseintrag,](#url_event_entry) um *mapName* (in BEGIN_EMBED_DHTML_EVENT_MAP) einer URL oder HTML-Ressource zuzuordnen.

### <a name="example"></a>Beispiel

Siehe das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a>BEGIN_URL_ENTRIES

Startet die Definition einer URL-Ereigniseintragszuordnung in einem mehrseitigen Dialogfeld.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die URL-Ereigniseintragszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)ableiten. Die URL-Ereigniseintragszuordnung muss sich in einer [DHTML- und URL-Ereigniszuordnung befinden.](#begin_dhtml_url_event_map)

### <a name="remarks"></a>Bemerkungen

Da ein mehrseitiges DHTML-Dialogfeld aus mehreren HTML-Seiten besteht, werden URL-Ereigniseinträge verwendet, um URLs oder HTML-Ressourcen entsprechenden [eingebetteten DHTML-Ereigniszuordnungen](#begin_embed_dhtml_event_map)zuzuordnen. Setzen Sie URL_EVENT_ENTRY Makros zwischen BEGIN_URL_ENTRIES und [END_URL_ENTRIES](#end_url_entries) Makros.

### <a name="example"></a>Beispiel

Siehe das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a>DECLARE_DHTML_URL_EVENT_MAP

Deklariert eine DHTML- und URL-Ereigniszuordnung in einer Klassendefinition.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in der Definition von [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-derived-Klassen verwendet.

Eine DHTML- und URL-Ereigniszuordnung enthält [eingebettete DHTML-Ereigniszuordnungen](#begin_embed_dhtml_event_map) und [URL-Ereigniseinträge,](#begin_url_entries) um DHTML-Ereignisse den Handlern auf Seitenbasis zuzuordnen. Verwenden Sie [BEGIN_DHTML_URL_EVENT_MAP,](#begin_dhtml_url_event_map) um die Karte zu implementieren.

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a>END_DHTML_URL_EVENT_MAP

Markiert das Ende einer DHTML- und URL-Ereigniszuordnung.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die Ereigniszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)ableiten. Dies sollte *className* im entsprechenden [BEGIN_DHTML_URL_EVENT_MAP-Makro](#begin_dhtml_url_event_map) entsprechen.

### <a name="example"></a>Beispiel

Siehe das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a>END_EMBED_DHTML_EVENT_MAP

Markiert das Ende einer eingebetteten DHTML-Ereigniszuordnung.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Beispiel

Siehe das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="end_url_entries"></a><a name="end_url_entries"></a>END_URL_ENTRIES

Markiert das Ende einer URL-Ereigniseintragszuordnung.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Beispiel

Siehe das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="url_event_entry"></a><a name="url_event_entry"></a>URL_EVENT_ENTRY

Ordnet eine URL oder HTML-Ressource einer Seite in einem mehrseitigen Dialogfeld zu.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parameter

*Classname*<br/>
Der Name der Klasse, die die URL-Ereigniseintragszuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CMultiPageDHtmlDialog](../../mfc/reference/cmultipagedhtmldialog-class.md)ableiten. Die URL-Ereigniseintragszuordnung muss sich in einer [DHTML- und URL-Ereigniszuordnung befinden.](#begin_dhtml_url_event_map)

*url*<br/>
Die URL oder HTML-Ressource für die Seite.

*mapName*<br/>
Gibt die Seite an, deren URL *URL*ist. Dies entspricht *mapName* im [BEGIN_EMBED_DHTML_EVENT_MAP-Makro,](#begin_embed_dhtml_event_map) das Ereignisse von dieser Seite zuordnet.

### <a name="remarks"></a>Bemerkungen

Wenn es sich bei der Seite um eine HTML-Ressource handelt, muss *URL* die Zeichenfolgendarstellung der ID-Nummer der Ressource sein (d. h. "123", nicht 123 oder ID_HTMLRES1).

Der Seitenbezeichner *mapName*ist ein beliebiges Symbol, das zum Verknüpfen eingebetteter DHTML-Ereigniszuordnungen mit URL-Ereigniseintragszuordnungen verwendet wird. Sie ist im Gültigkeitsbereich auf die DHTML- und URL-Ereigniszuordnung beschränkt.

### <a name="example"></a>Beispiel

Siehe das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map).

### <a name="requirements"></a>Anforderungen

  **Header** afxdhtml.h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a>END_DHTML_EVENT_MAP_INLINE

Markiert das Ende der DHTML-Ereigniszuordnung.

### <a name="syntax"></a>Syntax

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Bemerkungen

Muss in Verbindung mit [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)verwendet werden.

### <a name="requirements"></a>Anforderungen

**Kopf:** afxdhtml.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)
