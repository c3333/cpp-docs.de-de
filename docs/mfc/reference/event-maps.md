---
title: Ereigniszuordnungen
ms.date: 09/07/2019
helpviewer_keywords:
- event maps [MFC]
ms.assetid: 1ed53aee-bc53-43cd-834a-6fb935c0d29b
ms.openlocfilehash: ef8ee6b87bdeb9d5da9f34d303e0c0fda89443c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222796"
---
# <a name="event-maps"></a>Ereigniszuordnungen

Jedes Mal, wenn ein Steuerelement den Container benachrichtigen soll, dass eine Aktion (die vom Steuerelement Entwickler festgelegt wurde) stattgefunden hat (z. b. eine Tastatureingabe, ein Mausklick oder eine Änderung am Zustand des-Steuer Elements), wird eine Ereignis auslösenden Funktion aufgerufen. Diese Funktion benachrichtigt den Steuerelement Container, dass eine wichtige Aktion aufgetreten ist, indem das zugehörige Ereignis ausgelöst wurde.

Der Microsoft Foundation Class-Bibliothek bietet ein für das Auslösen von Ereignissen optimiertes Programmiermodell. In diesem Modell werden "Ereignis Zuordnungen" verwendet, um zu bestimmen, welche Funktionen welche Ereignisse für ein bestimmtes Steuerelement auslösen. Ereignis Zuordnungen enthalten ein Makro für jedes Ereignis. Beispielsweise könnte eine Ereignis Zuordnung, die ein "Stock Click"-Ereignis auslöst, wie folgt aussehen:

[!code-cpp[NVC_MFCAxCtl#16](../../mfc/reference/codesnippet/cpp/event-maps_1.cpp)]

Das- `EVENT_STOCK_CLICK` Makro gibt an, dass das Steuerelement jedes Mal, wenn ein Mausklick entdeckt wird, ein geklickclick-Ereignis auslöst. Eine ausführlichere Auflistung von anderen Aktien Ereignissen finden Sie im Artikel ActiveX-Steuer [Elemente: Ereignisse](../../mfc/mfc-activex-controls-events.md). Makros sind auch verfügbar, um benutzerdefinierte Ereignisse anzugeben.

Obwohl ereigniszuordnungs-Makros wichtig sind, fügen Sie Sie in der Regel nicht direkt ein. Dies liegt daran, dass das **Eigenschaften** Fenster (in **Klassenansicht**) automatisch Ereignis Zuordnungs Einträge in den Quelldateien erstellt, wenn Sie es verwenden, um Ereignis auslösenden Funktionen Ereignissen zuzuordnen. Jedes Mal, wenn Sie einen Ereignis Zuordnungs Eintrag bearbeiten oder hinzufügen möchten, können Sie das **Eigenschaften** Fenster verwenden.

Um Ereignis Zuordnungen zu unterstützen, stellt MFC die folgenden Makros bereit:

## <a name="event-map-macros"></a>Ereignis Zuordnungs Makros

### <a name="event-map-declaration-and-demarcation"></a>Deklaration und Abgrenzung von Ereignis Zuordnungen

|||
|-|-|
|[DECLARE_EVENT_MAP](#declare_event_map)|Deklariert, dass eine Ereignis Zuordnung in einer Klasse verwendet wird, um Ereignisse Ereignis auslösenden Funktionen zuzuordnen (muss in der Klassen Deklaration verwendet werden).|
|[BEGIN_EVENT_MAP](#begin_event_map)|Beginnt die Definition einer Ereignis Zuordnung (muss in der Klassen Implementierung verwendet werden).|
|[END_EVENT_MAP](#end_event_map)|Beendet die Definition einer Ereignis Zuordnung (muss in der Klassen Implementierung verwendet werden).|

### <a name="event-mapping-macros"></a>Ereignis Zuordnungs Makros

|||
|-|-|
|[EVENT_CUSTOM](#event_custom)|Gibt an, welche Ereignis auslösende Funktion das angegebene Ereignis auslöst.|
|[EVENT_CUSTOM_ID](#event_custom_id)|Gibt an, welche Ereignis auslösende Funktion das angegebene Ereignis mit einer angegebenen Dispatch-ID auslöst.|

### <a name="message-mapping-macros"></a>Nachrichten Zuordnungs Makros

|||
|-|-|
|[ON_OLEVERB](#on_oleverb)|Gibt ein vom OLE-Steuerelement behandeltes benutzerdefiniertes Verb an|
|[ON_STDOLEVERB](#on_stdoleverb)|Überschreibt eine standardmäßige Verb Zuordnung des OLE-Steuer Elements.|

## <a name="declare_event_map"></a><a name="declare_event_map"></a>DECLARE_EVENT_MAP

Jede `COleControl` von abgeleitete Klasse in Ihrem Programm kann eine Ereignis Zuordnung bereitstellen, um die Ereignisse anzugeben, die von Ihrem Steuerelement ausgelöst werden.

```cpp
DECLARE_EVENT_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_EVENT_MAP-Makro am Ende der Klassen Deklaration. Verwenden Sie dann in der CPP-Datei, die die Element Funktionen für die Klasse definiert, das BEGIN_EVENT_MAP Makro, die Makro Einträge für jedes der Steuerelemente des Steuer Elements und das END_EVENT_MAP Makro, um das Ende der Ereignisliste zu deklarieren.

Weitere Informationen zu Ereignis Zuordnungen finden Sie im Artikel [ActiveX-Steuerelemente: Ereignisse](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** afxctl. h

## <a name="begin_event_map"></a><a name="begin_event_map"></a>BEGIN_EVENT_MAP

Beginnt die Definition ihrer Ereignis Zuordnung.

```cpp
BEGIN_EVENT_MAP(theClass,  baseClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Steuerelement Klasse an, deren Ereignis Zuordnung lautet.

*BaseClass*<br/>
Gibt den Namen der Basisklasse von *TheClass*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungs Datei (. cpp), die die Element Funktionen für die Klasse definiert, die Ereignis Zuordnung mit dem BEGIN_EVENT_MAP-Makro, fügen Sie dann Makro Einträge für jedes der Ereignisse hinzu, und vervollständigen Sie die Ereignis Zuordnung mit dem END_EVENT_MAP-Makro.

Weitere Informationen zu Ereignis Zuordnungen und dem BEGIN_EVENT_MAP-Makro finden Sie im Artikel ActiveX-Steuer [Elemente: Ereignisse](../../mfc/mfc-activex-controls-events.md).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** afxctl. h

## <a name="end_event_map"></a><a name="end_event_map"></a>END_EVENT_MAP

Verwenden Sie das END_EVENT_MAP-Makro, um die Definition der Ereignis Zuordnung zu beenden.

```cpp
END_EVENT_MAP()
```

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** afxctl. h

## <a name="event_custom"></a><a name="event_custom"></a>EVENT_CUSTOM

Definiert einen Ereignis Zuordnungs Eintrag für ein benutzerdefiniertes Ereignis.

```cpp
EVENT_CUSTOM(pszName, pfnFire,  vtsParams)
```

### <a name="parameters"></a>Parameter

*pszName*<br/>
Der Name des Ereignisses.

*pfnfire*<br/>
Der Name der Ereignis auslösenden Funktion.

*vtsParams*<br/>
Eine durch Leerzeichen getrennte Liste von einer oder mehreren Konstanten, die die Parameterliste der Funktion angeben.

### <a name="remarks"></a>Bemerkungen

Der *vtsParams* -Parameter ist eine durch Leerzeichen getrennte Liste mit Werten aus den `VTS_` Konstanten. Einer oder mehrere dieser Werte, getrennt durch Leerzeichen (nicht Kommas), gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

gibt eine Liste mit einer 32-Bit-Ganzzahl an, die einen RGB-Farbwert darstellt, gefolgt von einem Zeiger auf die- `IFontDisp` Schnittstelle eines OLE-Schriftart Objekts.

Die `VTS_` Konstanten und ihre Bedeutungen lauten wie folgt:

|Symbol|Parametertyp|
|------------|--------------------|
|VTS_I2|**`short`**|
|VTS_I4|**`long`**|
|VTS_R4|**`float`**|
|VTS_R8|**`double`**|
|VTS_COLOR|OLE_COLOR|
|VTS_CY|WÄHRUNG|
|VTS_DATE|DATE|
|VTS_BSTR|**`const`**__Char \* __|
|VTS_DISPATCH|Lpdispatch|
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
> Für alle Variant-Typen wurden zusätzliche Variant-Konstanten definiert, mit Ausnahme von VTS_FONT und VTS_PICTURE, die einen Zeiger auf die Variant-Daten Konstante bereitstellen. Diese Konstanten werden mithilfe der `VTS_Pconstantname` Konvention benannt. VTS_PCOLOR ist beispielsweise ein Zeiger auf eine VTS_COLOR Konstante.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** afxctl. h

## <a name="event_custom_id"></a><a name="event_custom_id"></a>EVENT_CUSTOM_ID

Definiert eine Ereignis auslösende Funktion für ein benutzerdefiniertes Ereignis, das zur von *DISPID*angegebenen Dispatch-ID gehört.

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

*DISPID*<br/>
Die vom Steuerelement beim Auslösen des Ereignisses verwendete Dispatch-ID.

*pfnfire*<br/>
Der Name der Ereignis auslösenden Funktion.

*vtsParams*<br/>
Eine Variablen Liste von Parametern, die beim Auslösen des Ereignisses an den Steuerelement Container übermittelt werden.

### <a name="remarks"></a>Bemerkungen

Das *vtsParams* -Argument ist eine durch Leerzeichen getrennte Liste mit Werten aus den `VTS_` Konstanten. Einer oder mehrere dieser Werte, getrennt durch Leerzeichen, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCActiveXControl#13](../../mfc/codesnippet/cpp/event-maps_2.cpp)]

gibt eine Liste mit einer 32-Bit-Ganzzahl an, die einen RGB-Farbwert darstellt, gefolgt von einem Zeiger auf die- `IFontDisp` Schnittstelle eines OLE-Schriftart Objekts.

Eine Liste der `VTS_` Konstanten finden Sie unter [EVENT_CUSTOM](#event_custom).

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** afxctl. h

## <a name="on_oleverb"></a><a name="on_oleverb"></a>ON_OLEVERB

Dieses Makro definiert einen Meldungs Zuordnungs Eintrag, der einer bestimmten Member-Funktion des Steuer Elements ein benutzerdefiniertes Verb zuordnet.

```cpp
ON_OLEVERB(idsVerbName,  memberFxn)
```

### <a name="parameters"></a>Parameter

*idsverbname*<br/>
Die Zeichen folgen Ressourcen-ID für den Namen des Verbs.

*Mitgliedschaft*<br/>
Die Funktion, die vom Framework aufgerufen wird, wenn das Verb aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Der Ressourcen-Editor kann verwendet werden, um benutzerdefinierte Verb Namen zu erstellen, die der Zeichen folgen Tabelle hinzugefügt werden.

Der Funktionsprototyp für *mitgliedsfxn* lautet:

```cpp
BOOL memberFxn(
   LPMSG    lpMsg,
   HWND     hWndParent,
   LPCRECT  lpRect);
```

Die Werte der Parameter *lpmsg*, *hwndParent*und *lprect* werden aus den entsprechenden Parametern der `IOleObject::DoVerb` Member-Funktion entnommen.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** Afxole. h

## <a name="on_stdoleverb"></a><a name="on_stdoleverb"></a>ON_STDOLEVERB

Verwenden Sie dieses Makro, um das Standardverhalten eines Standard Verbs zu überschreiben.

```cpp
ON_STDOLEVERB(iVerb, memberFxn)
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Der standardmäßige Verb Index für das überschriebene Verb.

*Mitgliedschaft*<br/>
Die Funktion, die vom Framework aufgerufen wird, wenn das Verb aufgerufen wird.

### <a name="remarks"></a>Bemerkungen

Der standardmäßige Verb Index hat das Format `OLEIVERB_` , gefolgt von einer Aktion. OLEIVERB_SHOW, OLEIVERB_HIDE und OLEIVERB_UIACTIVATE sind einige Beispiele für Standard Verben.

Unter [ON_OLEVERB](#on_oleverb) finden Sie eine Beschreibung des Funktions Prototyps, der als *Mitglieds* Parameter verwendet werden soll.

### <a name="requirements"></a>Requirements (Anforderungen)

**Header** Afxole. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
