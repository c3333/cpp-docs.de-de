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
ms.openlocfilehash: 099a08298357d99a3d09ed6fc1209d463f6a4526
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837423"
---
# <a name="dhtml-event-maps"></a>DHTML-Ereigniszuordnungen

Die folgenden Makros können zum Verarbeiten von DHTML-Ereignissen verwendet werden.

## <a name="dhtml-event-map-macros"></a>DHTML-Ereignis Zuordnungs Makros

Die folgenden Makros können zum Verarbeiten von DHTML-Ereignissen in von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-abgeleiteten Klassen verwendet werden.

|Name|Beschreibung|
|-|-|
|[BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)|Markiert den Anfang der DHTML-Ereignis Zuordnung.|
|[BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)|Markiert den Anfang der DHTML-Ereignis Zuordnung.|
|[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map)|Deklariert die DHTML-Ereignis Zuordnung.|
|[DHTML_EVENT](#dhtml_event)|Wird verwendet, um ein Ereignis auf Dokument Ebene für ein einzelnes HTML-Element zu verarbeiten.|
|[DHTML_EVENT_AXCONTROL](#dhtml_event_axcontrol)|Wird zur Behandlung eines von einem ActiveX-Steuerelement ausgelösten Ereignisses verwendet.|
|[DHTML_EVENT_CLASS](#dhtml_event_class)|Wird verwendet, um ein Ereignis auf Dokument Ebene für alle HTML-Elemente mit einer bestimmten CSS-Klasse zu behandeln.|
|[DHTML_EVENT_ELEMENT](#dhtml_event_element)|Wird verwendet, um ein Ereignis auf Element Ebene zu behandeln.|
|[DHTML_EVENT_ONAFTERUPDATE](#dhtml_event_onafterupdate)|Wird verwendet, um das- `onafterupdate` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONBEFOREUPDATE](#dhtml_event_onbeforeupdate)|Wird verwendet, um das- `onbeforeupdate` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONBLUR](#dhtml_event_onblur)|Wird verwendet, um das- `onblur` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONCHANGE](#dhtml_event_onchange)|Wird verwendet, um das- `onchange` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONCLICK](#dhtml_event_onclick)|Wird verwendet, um das- `onclick` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONDATAAVAILABLE](#dhtml_event_ondataavailable)|Wird verwendet, um das- `ondataavailable` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONDATASETCHANGED](#dhtml_event_ondatasetchanged)|Wird verwendet, um das- `ondatasetchanged` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONDATASETCOMPLETE](#dhtml_event_ondatasetcomplete)|Wird verwendet, um das- `ondatasetcomplete` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONDBLCLICK](#dhtml_event_ondblclick)|Wird verwendet, um das- `ondblclick` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONDRAGSTART](#dhtml_event_ondragstart)|Wird verwendet, um das- `ondragstart` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONERRORUPDATE](#dhtml_event_onerrorupdate)|Wird verwendet, um das- `onerrorupdate` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONFILTERCHANGE](#dhtml_event_onfilterchange)|Wird verwendet, um das- `onfilterchange` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONFOCUS](#dhtml_event_onfocus)|Wird verwendet, um das- `onfocus` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONHELP](#dhtml_event_onhelp)|Wird verwendet, um das- `onhelp` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONKEYDOWN](#dhtml_event_onkeydown)|Wird verwendet, um das- `onkeydown` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONKEYPRESS](#dhtml_event_onkeypress)|Wird verwendet, um das- `onkeypress` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONKEYUP](#dhtml_event_onkeyup)|Wird verwendet, um das- `onkeyup` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONMOUSEDOWN](#dhtml_event_onmousedown)|Wird verwendet, um das- `onmousedown` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONMOUSEMOVE](#dhtml_event_onmousemove)|Wird verwendet, um das- `onmousemove` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONMOUSEOUT](#dhtml_event_onmouseout)|Wird verwendet, um das- `onmouseout` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONMOUSEOVER](#dhtml_event_onmouseover)|Wird verwendet, um das- `onmouseover` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONMOUSEUP](#dhtml_event_onmouseup)|Wird verwendet, um das- `onmouseup` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONRESIZE](#dhtml_event_onresize)|Wird verwendet, um das- `onresize` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONROWENTER](#dhtml_event_onrowenter)|Wird verwendet, um das- `onrowenter` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONROWEXIT](#dhtml_event_onrowexit)|Wird verwendet, um das- `onrowexit` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_ONSELECTSTART](#dhtml_event_onselectstart)|Wird verwendet, um das- `onselectstart` Ereignis aus einem HTML-Element zu verarbeiten.|
|[DHTML_EVENT_TAG](#dhtml_event_tag)|Wird verwendet, um ein Ereignis auf Dokument Ebene für alle Elemente mit einem bestimmten HTML-Tag zu verarbeiten.|
|[END_DHTML_EVENT_MAP](#end_dhtml_event_map)|Markiert das Ende der DHTML-Ereignis Zuordnung.|
|[END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline)|Markiert das Ende der DHTML-Ereignis Zuordnung. |

## <a name="url-event-map-macros"></a>URL-Ereignis Zuordnungs Makros

Die folgenden Makros können verwendet werden, um DHTML-Ereignisse in von [cmultiteigedhtmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-abgeleiteten Klassen zu verarbeiten.

|Name|Beschreibung|
|-|-|
|[BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)|Markiert den Anfang der mehrseitigen-DHTML-und URL-Ereignis Zuordnung.|
|[BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map)|Markiert den Anfang einer eingebetteten DHTML-Ereignis Zuordnung.|
|[BEGIN_URL_ENTRIES](#begin_url_entries)|Markiert den Anfang einer URL-Ereignis Eintrags Zuordnung.|
|[DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map)|Deklariert die mehrseitigen-DHTML-und URL-Ereignis Zuordnung.|
|[END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map)|Markiert das Ende der mehrseitigen-DHTML-und URL-Ereignis Zuordnung.|
|[END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map)|Markiert das Ende einer eingebetteten DHTML-Ereignis Zuordnung.|
|[END_URL_ENTRIES](#end_url_entries)|Markiert das Ende einer URL-Ereignis Eintrags Zuordnung.|
|[URL_EVENT_ENTRY](#url_event_entry)|Ordnet eine URL oder eine HTML-Ressource einer Seite in einem mehrseitigen Dialogfeld zu.|

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="begin_dhtml_event_map"></a><a name="begin_dhtml_event_map"></a> BEGIN_DHTML_EVENT_MAP

Markiert den Anfang der DHTML-Ereignis Zuordnung, wenn Sie in der Quelldatei für die durch identifizierte Klasse platziert wird `className` .

```cpp
BEGIN_DHTML_EVENT_MAP(className)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die DHTML-Ereignis Zuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) abgeleitet werden und das [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) Makro innerhalb ihrer Klassendefinition einschließen.

### <a name="remarks"></a>Bemerkungen

Fügen Sie der-Klasse eine DHTML-Ereignis Zuordnung hinzu, um Informationen bereitzustellen `CDHtmlDialog` , die zum Weiterleiten von Ereignissen verwendet werden können, die von HTML-Elementen oder ActiveX-Steuerelementen in einer Webseite an Handlerfunktionen in ihrer Klasse ausgelöst werden

Platzieren Sie das BEGIN_DHTML_EVENT_MAP-Makro in der Implementierungs Datei (. cpp) der Klasse, gefolgt von DHTML_EVENT Makros für die Ereignisse, die von der Klasse behandelt werden sollen (z. b. DHTML_EVENT_ONMOUSEOVER für Mouseover-Ereignisse). Verwenden Sie das [END_DHTML_EVENT_MAP](#end_dhtml_event_map) -Makro, um das Ende der Ereignis Zuordnung zu markieren. Diese Makros implementieren die folgende Funktion:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="begin_dhtml_event_map_inline"></a><a name="begin_dhtml_event_map_inline"></a> BEGIN_DHTML_EVENT_MAP_INLINE

Markiert den Anfang der DHTML-Ereignis Zuordnung innerhalb der Klassendefinition für *className*.

```cpp
BEGIN_DHTML_EVENT_MAP_INLINE(className)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die DHTML-Ereignis Zuordnung enthält. Diese Klasse sollte direkt oder indirekt von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md) abgeleitet werden und das [DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) Makro innerhalb ihrer Klassendefinition einschließen.

### <a name="remarks"></a>Bemerkungen

Fügen Sie der-Klasse eine DHTML-Ereignis Zuordnung hinzu, um Informationen bereitzustellen `CDHtmlDialog` , die zum Weiterleiten von Ereignissen verwendet werden können, die von HTML-Elementen oder ActiveX-Steuerelementen in einer Webseite an Handlerfunktionen in ihrer Klasse ausgelöst werden

Platzieren Sie das BEGIN_DHTML_EVENT_MAP-Makro in der Definitionsdatei (. h) der Klasse, gefolgt von DHTML_EVENT Makros für die Ereignisse, die von der Klasse behandelt werden sollen (z. b. DHTML_EVENT_ONMOUSEOVER für Mouseover-Ereignisse). Verwenden Sie das [END_DHTML_EVENT_MAP_INLINE](#end_dhtml_event_map_inline) -Makro, um das Ende der Ereignis Zuordnung zu markieren. Diese Makros implementieren die folgende Funktion:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap();`

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="declare_dhtml_event_map"></a><a name="declare_dhtml_event_map"></a> DECLARE_DHTML_EVENT_MAP

Deklariert eine DHTML-Ereignis Zuordnung in einer Klassendefinition.

```cpp
DECLARE_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Dieses Makro muss in der Definition von [CDHtmlDialog](../../mfc/reference/cdhtmldialog-class.md)-abgeleiteten Klassen verwendet werden.

Verwenden Sie [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map) oder [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline) , um die Zuordnung zu implementieren.

[DECLARE_DHTML_EVENT_MAP](#declare_dhtml_event_map) deklariert die folgende Funktion:

`virtual const DHtmlEventMapEntry* GetDHtmlEventMap( );`

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event"></a><a name="dhtml_event"></a> DHTML_EVENT

Handles (auf Dokument Ebene) ein Ereignis, das durch *DISPID* identifiziert wird, stammt durch das durch Element *Name*identifizierte HTML-Element.

```cpp
DHTML_EVENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die DISPID des zu behandelnden Ereignisses.

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements mit der Ermittlung des Ereignisses enthält, oder NULL, um Dokument Ereignisse zu behandeln.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_axcontrol"></a><a name="dhtml_event_axcontrol"></a> DHTML_EVENT_AXCONTROL

Behandelt das Ereignis, das durch *DISPID* identifiziert wird, das durch das durch *ControlName*identifizierte ActiveX-Steuerelement ausgelöst wird.

```cpp
DHTML_EVENT_AXCONTROL(dispid, controlName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*ControlName*<br/>
Ein LPCWSTR, der die HTML-ID des Steuer Elements enthält, das das Ereignis auslöst.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_class"></a><a name="dhtml_event_class"></a> DHTML_EVENT_CLASS

Handles (auf Dokument Ebene) ein durch *DISPID* bezeichnetes Ereignis, das von einem beliebigen HTML-Element mit der durch *ElementName*identifizierten CSS-Klasse stammt.

```cpp
DHTML_EVENT_CLASS(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*Elementname*<br/>
Ein LPCWSTR mit der CSS-Klasse der HTML-Elemente, die das Ereignis beziehen.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_element"></a><a name="dhtml_event_element"></a> DHTML_EVENT_ELEMENT

Handles (bei dem durch *elemname*identifizierten Element) ein Ereignis, das durch *DISPID*identifiziert wird.

```cpp
DHTML_EVENT_ELEMENT(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

Wenn dieses Makro verwendet wird, um nicht bubblindende Ereignisse zu behandeln, ist die Quelle des Ereignisses das Element, das durch Element *Name*identifiziert wird.

Wenn dieses Makro verwendet wird, um bubblingereignisse zu behandeln, ist das durch *elemname* identifizierte Element möglicherweise nicht die Quelle des Ereignisses (die Quelle könnte ein beliebiges Element in *elemname*sein).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onafterupdate"></a><a name="dhtml_event_onafterupdate"></a> DHTML_EVENT_ONAFTERUPDATE

Handles (auf Dokument Ebene) das Ereignis, das `onafterupdate` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONAFTERUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onbeforeupdate"></a><a name="dhtml_event_onbeforeupdate"></a> DHTML_EVENT_ONBEFOREUPDATE

Handles (auf Dokument Ebene) das Ereignis, das `onbeforeupdate` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONBEFOREUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onblur"></a><a name="dhtml_event_onblur"></a> DHTML_EVENT_ONBLUR

Behandelt das Ereignis auf der Element Ebene `onblur` . Dabei handelt es sich um ein nicht bubblines Ereignis.

```cpp
DHTML_EVENT_ONBLUR(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onchange"></a><a name="dhtml_event_onchange"></a> DHTML_EVENT_ONCHANGE

Behandelt das Ereignis auf der Element Ebene `onchange` . Dabei handelt es sich um ein nicht bubblines Ereignis.

```cpp
DHTML_EVENT_ONCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onclick"></a><a name="dhtml_event_onclick"></a> DHTML_EVENT_ONCLICK

Handles (auf Dokument Ebene) das Ereignis, das `onclick` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_ondataavailable"></a><a name="dhtml_event_ondataavailable"></a> DHTML_EVENT_ONDATAAVAILABLE

Handles (auf Dokument Ebene) das Ereignis, das `ondataavailable` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONDATAAVAILABLE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_ondatasetchanged"></a><a name="dhtml_event_ondatasetchanged"></a> DHTML_EVENT_ONDATASETCHANGED

Handles (auf Dokument Ebene) das Ereignis, das `ondatasetchanged` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONDATASETCHANGED(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_ondatasetcomplete"></a><a name="dhtml_event_ondatasetcomplete"></a> DHTML_EVENT_ONDATASETCOMPLETE

Handles (auf Dokument Ebene) das Ereignis, das `ondatasetcomplete` von dem durch identifizierten HTML-Element stammt `elemName` .

```cpp
DHTML_EVENT_ONDATASETCOMPLETE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_ondblclick"></a><a name="dhtml_event_ondblclick"></a> DHTML_EVENT_ONDBLCLICK

Handles (auf Dokument Ebene) das Ereignis, das `ondblclick` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONDBLCLICK(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_ondragstart"></a><a name="dhtml_event_ondragstart"></a> DHTML_EVENT_ONDRAGSTART

Handles (auf Dokument Ebene) das Ereignis, das `ondragstart` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONDRAGSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onerrorupdate"></a><a name="dhtml_event_onerrorupdate"></a> DHTML_EVENT_ONERRORUPDATE

Handles (auf Dokument Ebene) das Ereignis, das `onerrorupdate` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONERRORUPDATE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onfilterchange"></a><a name="dhtml_event_onfilterchange"></a> DHTML_EVENT_ONFILTERCHANGE

Handles (auf Dokument Ebene) das Ereignis, das `onfilterchange` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONFILTERCHANGE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onfocus"></a><a name="dhtml_event_onfocus"></a> DHTML_EVENT_ONFOCUS

Behandelt das Ereignis auf der Element Ebene `onfocus` . Dabei handelt es sich um ein nicht bubblines Ereignis.

```cpp
DHTML_EVENT_ONFOCUS(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onhelp"></a><a name="dhtml_event_onhelp"></a> DHTML_EVENT_ONHELP

Handles (auf Dokument Ebene) das Ereignis, das `onhelp` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONHELP(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onkeydown"></a><a name="dhtml_event_onkeydown"></a> DHTML_EVENT_ONKEYDOWN

Handles (auf Dokument Ebene) das Ereignis, das `onkeydown` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONKEYDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onkeypress"></a><a name="dhtml_event_onkeypress"></a> DHTML_EVENT_ONKEYPRESS

Handles (auf Dokument Ebene) das Ereignis, das `onkeypress` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONKEYPRESS(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onkeyup"></a><a name="dhtml_event_onkeyup"></a> DHTML_EVENT_ONKEYUP

Handles (auf Dokument Ebene) das Ereignis, das `onkeyup` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONKEYUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onmousedown"></a><a name="dhtml_event_onmousedown"></a> DHTML_EVENT_ONMOUSEDOWN

Handles (auf Dokument Ebene) das Ereignis, das `onmousedown` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONMOUSEDOWN(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onmousemove"></a><a name="dhtml_event_onmousemove"></a> DHTML_EVENT_ONMOUSEMOVE

Handles (auf Dokument Ebene) das Ereignis, das `onmousemove` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONMOUSEMOVE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onmouseout"></a><a name="dhtml_event_onmouseout"></a> DHTML_EVENT_ONMOUSEOUT

Handles (auf Dokument Ebene) das Ereignis, das `onmouseout` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONMOUSEOUT(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onmouseover"></a><a name="dhtml_event_onmouseover"></a> DHTML_EVENT_ONMOUSEOVER

Handles (auf Dokument Ebene) das Ereignis, das `onmouseover` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONMOUSEOVER(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onmouseup"></a><a name="dhtml_event_onmouseup"></a> DHTML_EVENT_ONMOUSEUP

Handles (auf Dokument Ebene) das Ereignis, das `onmouseup` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONMOUSEUP(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onresize"></a><a name="dhtml_event_onresize"></a> DHTML_EVENT_ONRESIZE

Behandelt das Ereignis auf der Element Ebene `onresize` . Dabei handelt es sich um ein nicht bubblines Ereignis.

```cpp
DHTML_EVENT_ONRESIZE(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onrowenter"></a><a name="dhtml_event_onrowenter"></a> DHTML_EVENT_ONROWENTER

Handles (auf Dokument Ebene) das Ereignis, das `onrowenter` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONROWENTER(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onrowexit"></a><a name="dhtml_event_onrowexit"></a> DHTML_EVENT_ONROWEXIT

Handles (auf Dokument Ebene) das Ereignis, das `onrowexit` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONROWEXIT(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_onselectstart"></a><a name="dhtml_event_onselectstart"></a> DHTML_EVENT_ONSELECTSTART

Handles (auf Dokument Ebene) das Ereignis, das `onselectstart` von dem durch Element *Name*identifizierten HTML-Element stammt.

```cpp
DHTML_EVENT_ONSELECTSTART(elemName, memberFxn)
```

### <a name="parameters"></a>Parameter

*Elementname*<br/>
Ein LPCWSTR, der die ID des HTML-Elements enthält, das das Ereignis beschafft.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="dhtml_event_tag"></a><a name="dhtml_event_tag"></a> DHTML_EVENT_TAG

Handles (auf Dokument Ebene) ein durch identifiziertes Ereignis, das von einem `dispid` beliebigen HTML-Element mit dem durch *ElementName*identifizierten HTML-Tag stammt.

```cpp
DHTML_EVENT_TAG(dispid, elemName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*DISPID*<br/>
Die Dispatch-ID des zu behandelnden Ereignisses.

*Elementname*<br/>
Das HTML-Tag der HTML-Elemente, die das Ereignis beziehen.

*Mitgliedschaft*<br/>
Die Handlerfunktion für das-Ereignis.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, um der [DHTML-Ereignis](#begin_dhtml_event_map_inline) Zuordnung in der-Klasse einen Eintrag hinzuzufügen.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="end_dhtml_event_map"></a><a name="end_dhtml_event_map"></a> END_DHTML_EVENT_MAP

Markiert das Ende der DHTML-Ereignis Zuordnung.

```cpp
END_DHTML_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Muss in Verbindung mit [BEGIN_DHTML_EVENT_MAP](#begin_dhtml_event_map)verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="begin_dhtml_url_event_map"></a><a name="begin_dhtml_url_event_map"></a> BEGIN_DHTML_URL_EVENT_MAP

Startet die Definition einer DHTML-und URL-Ereignis Zuordnung in einem mehrseitigen Dialogfeld.

```cpp
BEGIN_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Fügen Sie BEGIN_DHTML_URL_EVENT_MAP in die Implementierungs Datei Ihrer von [cmultiblogedhtmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)abgeleiteten Klasse ein. Befolgen Sie die [eingebetteten DHTML-Ereignis](#begin_embed_dhtml_event_map) Zuordnungen und [URL-Einträge](#begin_url_entries), und schließen Sie Sie dann mit [END_DHTML_URL_EVENT_MAP](#end_dhtml_url_event_map). Fügen Sie das [DECLARE_DHTML_URL_EVENT_MAP](#declare_dhtml_url_event_map) -Makro in die Klassendefinition ein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#196](../../mfc/codesnippet/cpp/dhtml-event-maps_1.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="begin_embed_dhtml_event_map"></a><a name="begin_embed_dhtml_event_map"></a> BEGIN_EMBED_DHTML_EVENT_MAP

Startet die Definition einer eingebetteten DHTML-Ereignis Zuordnung in einem mehrseitigen Dialogfeld.

```cpp
BEGIN_EMBED_DHTML_EVENT_MAP(className, mapName)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die Ereignis Zuordnung enthält. Diese Klasse sollte direkt oder indirekt von [cmultipaar-htmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)abgeleitet werden. Die eingebettete DHTML-Ereignis Zuordnung muss sich in einer [DHTML-und URL-Ereignis](#begin_dhtml_url_event_map)Zuordnung befinden.)

*mapname*<br/>
Gibt die Seite an, deren Ereignis Zuordnung lautet. Dies entspricht *MapName* im [URL_EVENT_ENTRY](#url_event_entry) Makro, das tatsächlich die URL oder die HTML-Ressource definiert.

### <a name="remarks"></a>Bemerkungen

Da ein mehrseitiges DHTML-Dialogfeld aus mehreren HTML-Seiten besteht, die jeweils DHTML-Ereignisse auslassen können, werden eingebettete Ereignis Zuordnungen verwendet, um Ereignisse auf Seitenbasis den Handlern zuzuordnen.

Eingebettete Ereignis Zuordnungen innerhalb einer DHTML-und URL-Ereignis Zuordnung bestehen aus einem BEGIN_EMBED_DHTML_EVENT_MAP Makro, gefolgt von [DHTML_EVENT](#dhtml_event) Makros und einem [END_EMBED_DHTML_EVENT_MAP](#end_embed_dhtml_event_map) -Makro.

Jede eingebettete Ereignis Zuordnung erfordert einen entsprechenden [URL-Ereignis Eintrag](#url_event_entry) , um *MapName* (angegeben in BEGIN_EMBED_DHTML_EVENT_MAP) einer URL-oder HTML-Ressource zuzuordnen.

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)an.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="begin_url_entries"></a><a name="begin_url_entries"></a> BEGIN_URL_ENTRIES

Startet die Definition einer URL-Ereignis Eintrags Zuordnung in einem mehrseitigen Dialogfeld.

```cpp
BEGIN_URL_ENTRIES(className)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die URL-Ereignis Eintrags Zuordnung enthält. Diese Klasse sollte direkt oder indirekt von [cmultipaar-htmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)abgeleitet werden. Die URL-Ereignis Eintrags Zuordnung muss sich in einer [DHTML-und URL-Ereignis](#begin_dhtml_url_event_map)Zuordnung befinden.)

### <a name="remarks"></a>Bemerkungen

Da ein mehrseitiges DHTML-Dialogfeld mehrere HTML-Seiten umfasst, werden URL-Ereignis Einträge verwendet, um URLs oder HTML-Ressourcen entsprechenden [eingebetteten DHTML-Ereignis](#begin_embed_dhtml_event_map)Zuordnungen zuzuordnen. Fügen Sie URL_EVENT_ENTRY Makros zwischen BEGIN_URL_ENTRIES und [END_URL_ENTRIES](#end_url_entries) Makros ein.

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)an.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="declare_dhtml_url_event_map"></a><a name="declare_dhtml_url_event_map"></a> DECLARE_DHTML_URL_EVENT_MAP

Deklariert eine DHTML-und URL-Ereignis Zuordnung in einer Klassendefinition.

```cpp
DECLARE_DHTML_URL_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Dieses Makro wird in der Definition von [cmultiteigedhtmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)-abgeleiteten Klassen verwendet.

Eine DHTML-und URL-Ereignis Zuordnung enthält [eingebettete DHTML-Ereignis](#begin_embed_dhtml_event_map) Zuordnungen und [URL-Ereignis Einträge](#begin_url_entries) , um den Handlern auf Seitenbasis DHTML-Ereignisse zuzuordnen. Verwenden Sie [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) , um die Zuordnung zu implementieren.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="end_dhtml_url_event_map"></a><a name="end_dhtml_url_event_map"></a> END_DHTML_URL_EVENT_MAP

Markiert das Ende einer DHTML-und URL-Ereignis Zuordnung.

```cpp
END_DHTML_URL_EVENT_MAP(className)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die Ereignis Zuordnung enthält. Diese Klasse sollte direkt oder indirekt von [cmultipaar-htmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)abgeleitet werden. Dies sollte mit *className* im entsprechenden [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map) -Makro übereinstimmen.

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)an.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="end_embed_dhtml_event_map"></a><a name="end_embed_dhtml_event_map"></a> END_EMBED_DHTML_EVENT_MAP

Markiert das Ende einer eingebetteten DHTML-Ereignis Zuordnung.

```cpp
END_EMBED_DHTML_EVENT_MAP()
```

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)an.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="end_url_entries"></a><a name="end_url_entries"></a> END_URL_ENTRIES

Markiert das Ende einer URL-Ereignis Eintrags Zuordnung.

```cpp
END_URL_ENTRIES()
```

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)an.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="url_event_entry"></a><a name="url_event_entry"></a> URL_EVENT_ENTRY

Ordnet eine URL oder eine HTML-Ressource einer Seite in einem mehrseitigen Dialogfeld zu.

```cpp
URL_EVENT_ENTRY(className, url,  mapName)
```

### <a name="parameters"></a>Parameter

*ClassName*<br/>
Der Name der Klasse, die die URL-Ereignis Eintrags Zuordnung enthält. Diese Klasse sollte direkt oder indirekt von [cmultipaar-htmldialog](../../mfc/reference/cmultipagedhtmldialog-class.md)abgeleitet werden. Die URL-Ereignis Eintrags Zuordnung muss sich in einer [DHTML-und URL-Ereignis](#begin_dhtml_url_event_map)Zuordnung befinden.)

*url*<br/>
Die URL oder die HTML-Ressource für die Seite.

*mapname*<br/>
Gibt die Seite an, deren URL *URL*ist. Dies entspricht *MapName* im [BEGIN_EMBED_DHTML_EVENT_MAP](#begin_embed_dhtml_event_map) -Makro, das Ereignisse von dieser Seite zuordnet.

### <a name="remarks"></a>Bemerkungen

Wenn es sich bei der Seite um eine HTML-Ressource handelt, muss *URL* die Zeichen folgen Darstellung der ID-Nummer der Ressource (d. h. "123", nicht 123 oder ID_HTMLRES1) sein.

Der Seiten Bezeichner *MapName*ist ein beliebiges Symbol, mit dem eingebettete DHTML-Ereignis Zuordnungen mit URL-Ereignis Eintrags Zuordnungen verknüpft werden. Er ist im Gültigkeitsbereich auf die DHTML-und URL-Ereignis Zuordnung beschränkt.

### <a name="example"></a>Beispiel

Sehen Sie sich das Beispiel in [BEGIN_DHTML_URL_EVENT_MAP](#begin_dhtml_url_event_map)an.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdhtml. h

## <a name="end_dhtml_event_map_inline"></a><a name="end_dhtml_event_map_inline"></a> END_DHTML_EVENT_MAP_INLINE

Markiert das Ende der DHTML-Ereignis Zuordnung.

### <a name="syntax"></a>Syntax

```cpp
END_DHTML_EVENT_MAP_INLINE( )
```

### <a name="remarks"></a>Bemerkungen

Muss in Verbindung mit [BEGIN_DHTML_EVENT_MAP_INLINE](#begin_dhtml_event_map_inline)verwendet werden.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdhtml. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)
