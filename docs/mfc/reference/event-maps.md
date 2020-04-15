---
title: Ereigniszuordnungen
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: c79d2fb1ac73947ddb13adcbd444ff7b5d50bdb4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365736"
---
# <a name="event-maps"></a>Ereigniszuordnungen

Wenn ein Steuerelement seinen Container darüber informieren möchte, dass eine (vom Steuerelemententwickler festgelegte) Aktion stattgefunden hat (z. B. ein Tastendruck, ein Mausklick oder eine Änderung des Status des Steuerelements), ruft es eine Ereignis-Firing-Funktion auf. Diese Funktion benachrichtigt den Steuerelementcontainer, dass durch Das Auslösen des zugehörigen Ereignisses eine wichtige Aktion aufgetreten ist.

Die Microsoft Foundation-Klassenbibliothek bietet ein Programmiermodell, das für das Auslösen von Ereignissen optimiert ist. In diesem Modell werden "Ereigniszuordnungen" verwendet, um anzugeben, welche Funktionen welche Ereignisse für ein bestimmtes Steuerelement ausgelöst haben. Ereigniszuordnungen enthalten ein Makro für jedes Ereignis. Beispielsweise könnte eine Ereigniszuordnung, die ein Stock Click-Ereignis auslöst, wie folgt aussehen:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

Das `EVENT_STOCK_CLICK` Makro gibt an, dass das Steuerelement jedes Mal ein Stock Click-Ereignis ausfeuert, wenn ein Mausklick erkannt wird. Eine detailliertere Auflistung anderer Aktienereignisse finden Sie im Artikel [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md). Makros sind auch verfügbar, um benutzerdefinierte Ereignisse anzuzeigen.

Obwohl Ereigniszuordnungsmakros wichtig sind, fügen Sie sie in der Regel nicht direkt ein. Dies liegt daran, dass das **Eigenschaftenfenster** (in der **Klassenansicht**) automatisch Ereigniszuordnungseinträge in Ihren Quelldateien erstellt, wenn Sie damit Ereignislöschfunktionen mit Ereignissen verknüpfen. Jedes Mal, wenn Sie einen Ereigniszuordnungseintrag bearbeiten oder hinzufügen möchten, können Sie das **Eigenschaftenfenster** verwenden.

Zur Unterstützung von Ereigniszuordnungen stellt MFC die folgenden Makros bereit:

## <a name="event-map-macros"></a>Ereigniskartenmakros

### <a name="event-map-declaration-and-demarcation"></a>Ereigniskartendeklaration und Abgrenzung

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Erklärt, dass eine Ereigniszuordnung in einer Klasse verwendet wird, um Ereignisse Ereignislöschfunktionen zuzuordnen (muss in der Klassendeklaration verwendet werden).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Beginnt die Definition einer Ereigniszuordnung (muss in der Klassenimplementierung verwendet werden).|
|[END_EVENT_MAP](#end_event_map)|Beendet die Definition einer Ereigniszuordnung (muss in der Klassenimplementierung verwendet werden).|

### <a name="event-mapping-macros"></a>Ereigniszuordnungsmakros

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Gibt an, welche Ereignislöschfunktion das angegebene Ereignis ausführt.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Gibt an, welche Ereignislöschfunktion das angegebene Ereignis mit einer bestimmten Dispatch-ID auslöst.|

### <a name="message-mapping-macros"></a>Nachrichtenzuordnungsmakros

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Gibt ein benutzerdefiniertes Verb an, das vom OLE-Steuerelement behandelt wird.|
|[ON_STDOLEVERB](#on_stdoleverb)|Überschreibt eine Standardverbzuordnung des OLE-Steuerelements.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

Jede `COleControl`-abgeleitete Klasse in Ihrem Programm kann eine Ereigniszuordnung bereitstellen, um die Ereignisse anzugeben, die von Der steuerung ausgelöst werden.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_EVENT_MAP-Makro am Ende der Klassendeklaration. Verwenden Sie dann in der CPP-Datei, die die Memberfunktionen für die Klasse definiert, das BEGIN_EVENT_MAP Makro, Makroeinträge für jedes Ereignis des Steuerelements und das END_EVENT_MAP Makro, um das Ende der Ereignisliste zu deklarieren.

Weitere Informationen zu Ereigniszuordnungen finden Sie im Artikel [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Anforderungen

**Header** afxctl.h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

Beginnt die Definition der Ereigniszuordnung.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Steuerelementklasse an, deren Ereigniszuordnung dies ist.

*Baseclass*<br/>
Gibt den Namen der Basisklasse *derKlasse*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungsdatei (.cpp), die die Memberfunktionen für Ihre Klasse definiert, die Ereigniszuordnung mit dem BEGIN_EVENT_MAP-Makro, fügen Sie dann Makroeinträge für jedes Ihrer Ereignisse hinzu, und schließen Sie die Ereigniszuordnung mit dem END_EVENT_MAP-Makro ab.

Weitere Informationen zu Ereigniszuordnungen und dem BEGIN_EVENT_MAP-Makro finden Sie im Artikel [ActiveX Controls: Events](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Anforderungen

**Header** afxctl.h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

Verwenden Sie das END_EVENT_MAP-Makro, um die Definition der Ereigniszuordnung zu beenden.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Anforderungen

**Header** afxctl.h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

Definiert einen Ereigniszuordnungseintrag für ein benutzerdefiniertes Ereignis.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parameter

*pszName*<br/>
Der Name des Ereignisses.

*pfnFire*<br/>
Der Name der Ereignislöschfunktion.

*vtsParams*<br/>
Eine durch Leerzeichen getrennte Liste einer oder mehrerer Konstanten, die die Parameterliste der Funktion angeben.

### <a name="remarks"></a>Bemerkungen

Der Parameter *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus den `VTS_` Konstanten. Mindestens einer dieser Werte, die durch Leerzeichen (keine Kommas) getrennt sind, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

gibt eine Liste an, die eine 32-Bit-Ganzzahl enthält, die `IFontDisp` einen RGB-Farbwert darstellt, gefolgt von einem Zeiger auf die Schnittstelle eines OLE-Schriftartobjekts.

Die `VTS_` Konstanten und ihre Bedeutungen sind wie folgt:

|Symbol|Parametertyp|
|------------|--------------------|
|VTS_I2|**short**|
|VTS_I4|**Lange**|
|VTS_R4|**float**|
|VTS_R8|**double**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|CURRENCY|
|VTS_DATE|DATE|
|VTS_BSTR|**const** __\* char__|
|VTS_DISPATCH|LPDISPATCH|
|VTS_FONT|`IFontDispatch*`|
|VTS_HANDLE|HANDLE|
|VTS_SCODE|SCODE|
|VTS_BOOL|BOOL|
|VTS_VARIANT|`const VARIANT*`|
|VTS_PVARIANT|`VARIANT*`|
|VTS_UNKNOWN|LPUNKNOWN|
|VTS_OPTEXCLUSIVE|OLE_OPTEXCLUSIVE|
|VTS_PICTURE|`IPictureDisp*`|
|VTS_TRISTATE|OLE_TRISTATE|
|VTS_XPOS_PIXELS|OLE_XPOS_PIXELS|
|VTS_YPOS_PIXELS|OLE_YPOS_PIXELS|
|VTS_XSIZE_PIXELS|OLE_XSIZE_PIXELS|
|VTS_YSIZE_PIXELS|OLE_YSIZE_PIXELS|
|TS_XPOS_HIMETRIC|OLE_XPOS_HIMETRIC|
|VTS_YPOS_HIMETRIC|OLE_YPOS_HIMETRIC|
|VTS_XSIZE_HIMETRIC|OLE_XSIZE_HIMETRIC|
|VTS_YSIZE_HIMETRIC|OLE_YSIZE_HIMETRIC|

> [!NOTE]
> Für alle Variantentypen wurden zusätzliche Variantenkonstanten definiert, mit Ausnahme von VTS_FONT und VTS_PICTURE, die einen Zeiger auf die Variantendatenkonstante liefern. Diese Konstanten werden `VTS_Pconstantname` mithilfe der Konvention benannt. VTS_PCOLOR ist z. B. ein Zeiger auf eine VTS_COLOR Konstante.

### <a name="requirements"></a>Anforderungen

**Header** afxctl.h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

Definiert eine Ereignislöschfunktion für ein benutzerdefiniertes Ereignis, das zur Dispatch-ID gehört, die von *dispid*angegeben wird.

```cpp
EVENT_CUSTOM_ID(
    pszName,
    dispid,
    pfnFire,
    vtsParams)
```

### <a name="parameters"></a>Parameter

*pszName*<br/>
Der Name des Ereignisses.

*Dispid*<br/>
Die Dispatch-ID, die vom Steuerelement beim Auslösen des Ereignisses verwendet wird.

*pfnFire*<br/>
Der Name der Ereignislöschfunktion.

*vtsParams*<br/>
Eine Variablenliste von Parametern, die beim Auswechseln des Ereignisses an den Steuerelementcontainer übergeben werden.

### <a name="remarks"></a>Bemerkungen

Das Argument *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus den `VTS_` Konstanten. Mindestens einer dieser Werte, die durch Leerzeichen getrennt sind, nicht Durch Kommas, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

gibt eine Liste an, die eine 32-Bit-Ganzzahl enthält, die `IFontDisp` einen RGB-Farbwert darstellt, gefolgt von einem Zeiger auf die Schnittstelle eines OLE-Schriftartobjekts.

Eine Liste der `VTS_` Konstanten finden Sie [unter EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Anforderungen

**Header** afxctl.h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

Dieses Makro definiert einen Meldungszuordnungseintrag, der ein benutzerdefiniertes Verb einer bestimmten Memberfunktion des Steuerelements zuordnet.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*idsVerbName*<br/>
Die Zeichenfolgenressourcen-ID des Verbnamens.

*MemberFxn*<br/>
Die Funktion, die vom Framework aufgerufen wird, wenn das Verb aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Editor kann verwendet werden, um benutzerdefinierte Verbnamen zu erstellen, die der Zeichenfolgentabelle hinzugefügt werden.

Der Funktionsprototyp für *memberFxn* ist:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Die Werte der Parameter *lpMsg*, *hWndParent*und *lpRect* werden `IOleObject::DoVerb` den entsprechenden Parametern der Memberfunktion entnommen.

### <a name="requirements"></a>Anforderungen

**Header** afxole.h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

Verwenden Sie dieses Makro, um das Standardverhalten eines Standardverbs zu überschreiben.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Der Standardverbindex für das überschriebene Verb.

*MemberFxn*<br/>
Die Funktion, die vom Framework aufgerufen wird, wenn das Verb aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Der Standardverbindex hat `OLEIVERB_`die Form , gefolgt von einer Aktion. OLEIVERB_SHOW, OLEIVERB_HIDE und OLEIVERB_UIACTIVATE sind einige Beispiele für Standardverben.

Eine Beschreibung des Funktionsprototyps, der als *memberFxn-Parameter* verwendet werden soll, finden Sie [in ON_OLEVERB.](#on_oleverb)

### <a name="requirements"></a>Anforderungen

**Header** afxole.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
