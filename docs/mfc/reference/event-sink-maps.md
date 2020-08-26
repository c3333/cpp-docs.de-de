---
title: Ereignissenkenzuordnungen
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 2cbfbc70ae14ccda95c377cb1587bf9d2a1ad3e6
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837263"
---
# <a name="event-sink-maps"></a>Ereignissenkenzuordnungen

Wenn ein eingebettetes OLE-Steuerelement ein Ereignis auslöst, empfängt der Container des Steuer Elements das Ereignis mithilfe eines als "Ereignis Senke Map" bezeichneten Mechanismus, der von MFC bereitgestellt wird. Diese Ereignis senkenzuordnung bestimmt Handlerfunktionen für jedes bestimmte Ereignis sowie Parameter dieser Ereignisse. Weitere Informationen zu ereignissenkenmaps finden Sie im Artikel [ActiveX-Steuerelement Container](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Ereignissenkenzuordnungen

|Name|Beschreibung|
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Startet die Definition einer ereignissenkmap.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklariert eine Ereignis Senke-Zuordnung.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Beendet die Definition einer ereignissenkmap.|
|[ON_EVENT](#on_event)|Definiert einen Ereignishandler für ein bestimmtes Ereignis.|
|[ON_EVENT_RANGE](#on_event_range)|Definiert einen Ereignishandler für ein bestimmtes Ereignis, das aus einem Satz von OLE-Steuerelementen ausgelöst wird.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Empfängt Ereignisse, die vom-Steuerelement ausgelöst werden, bevor Sie vom Container des Steuer Elements behandelt werden.|
|[ON_PROPNOTIFY](#on_propnotify)|Definiert einen Handler zum Behandeln von Eigenschafts Benachrichtigungen von einem OLE-Steuerelement.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definiert einen Handler zum Behandeln von Eigenschafts Benachrichtigungen aus einem Satz von OLE-Steuerelementen.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Empfängt Eigenschaften Benachrichtigungen, die vom-Steuerelement gesendet werden, bevor Sie vom Container des Steuer Elements behandelt werden.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a> BEGIN_EVENTSINK_MAP

Beginnt die Definition der ereignissenkmap.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Gibt den Namen der Steuerelement Klasse an, deren Ereignis Senke ist.

*BaseClass*<br/>
Gibt den Namen der Basisklasse von *TheClass*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungs Datei (CPP-Datei), in der die Member-Funktionen für Ihre Klasse definiert sind, die Ereignis Senke-Zuordnung mit dem BEGIN_EVENTSINK_MAP-Makro, END_EVENTSINK_MAP und fügen Sie anschließend Makro Einträge für jedes Ereignis hinzu, über das benachrichtigt werden soll

Weitere Informationen zu Ereignis Senk Karten und OLE-Steuerungs Containern finden Sie im Artikel [ActiveX-Steuerelement Container](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a> DECLARE_EVENTSINK_MAP

Ein OLE-Container kann eine Ereignis Senke-Zuordnung bereitstellen, um die Ereignisse anzugeben, über die ihr Container benachrichtigt wird.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_EVENTSINK_MAP-Makro am Ende der Klassen Deklaration. Klicken Sie anschließend in der auf. Cpp-Datei, die die Member-Funktionen für die-Klasse definiert, das BEGIN_EVENTSINK_MAP Makro, Makro Einträge für jedes der Ereignisse, die benachrichtigt werden sollen, und das END_EVENTSINK_MAP-Makro, um das Ende der Ereignis Senke-Liste zu deklarieren.

Weitere Informationen zu ereignissenkenmaps finden Sie im Artikel [ActiveX-Steuerelement Container](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** AFXWIN. h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a> END_EVENTSINK_MAP

Beendet die Definition der ereignissenkmap.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="on_event"></a><a name="on_event"></a> ON_EVENT

Verwenden Sie das ON_EVENT-Makro zum Definieren einer Ereignishandlerfunktion für ein Ereignis, das von einem OLE-Steuerelement ausgelöst wird

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, zu der diese Ereignis Senke-Zuordnung gehört.

*id*<br/>
Die Steuerelement-ID des OLE-Steuer Elements.

*DISPID*<br/>
Die Dispatch-ID des Ereignisses, das vom-Steuerelement ausgelöst wird.

*pfnhandler*<br/>
Zeiger auf eine Member-Funktion, die das Ereignis behandelt. Diese Funktion muss einen booleschen Rückgabetyp und Parametertypen aufweisen, die den Parameter des Ereignisses entsprechen (siehe *vtsParams*). Die Funktion sollte true zurückgeben, um anzugeben, dass das Ereignis behandelt wurde. andernfalls false.

*vtsParams*<br/>
Eine Sequenz von **VTS_** Konstanten, die die Typen der Parameter für das Ereignis angibt. Dabei handelt es sich um dieselben Konstanten, die in dispatchzuordnungseinträgen wie DISP_FUNCTION verwendet werden.

### <a name="remarks"></a>Bemerkungen

Das *vtsParams* -Argument ist eine durch Leerzeichen getrennte Liste mit Werten aus den **VTS_** Konstanten. Einer oder mehrere dieser Werte, getrennt durch Leerzeichen (nicht Kommas), gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze Ganzzahl gefolgt von einem booleschen Wert enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="on_event_range"></a><a name="on_event_range"></a> ON_EVENT_RANGE

Verwenden Sie das ON_EVENT_RANGE-Makro zum Definieren einer Ereignishandlerfunktion für ein Ereignis, das von einem OLE-Steuerelement ausgelöst wird, das eine Steuerelement-ID in einem zusammenhängenden Bereich von IDs

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, zu der diese Ereignis Senke-Zuordnung gehört.

*idfirst*<br/>
Die Steuerelement-ID des ersten OLE-Steuer Elements im Bereich.

*idlast*<br/>
Die Steuerelement-ID des letzten OLE-Steuer Elements im Bereich.

*DISPID*<br/>
Die Dispatch-ID des Ereignisses, das vom-Steuerelement ausgelöst wird.

*pfnhandler*<br/>
Zeiger auf eine Member-Funktion, die das Ereignis behandelt. Diese Funktion muss einen booleschen Rückgabetyp, einen ersten Parameter vom Typ uint (für die Steuerelement-ID) und zusätzliche Parametertypen aufweisen, die den Parameter des Ereignisses entsprechen (siehe *vtsParams*). Die Funktion sollte true zurückgeben, um anzugeben, dass das Ereignis behandelt wurde. andernfalls false.

*vtsParams*<br/>
Eine Sequenz von **VTS_** Konstanten, die die Typen der Parameter für das Ereignis angibt. Die erste Konstante muss den Typ "VTS_I4" für die Steuerelement-ID aufweisen. Dabei handelt es sich um dieselben Konstanten, die in dispatchzuordnungseinträgen wie DISP_FUNCTION verwendet werden.

### <a name="remarks"></a>Bemerkungen

Das *vtsParams* -Argument ist eine durch Leerzeichen getrennte Liste mit Werten aus den **VTS_** Konstanten. Einer oder mehrere dieser Werte, getrennt durch Leerzeichen (nicht Kommas), gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze Ganzzahl gefolgt von einem booleschen Wert enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Ereignishandler für das moueldown-Ereignis veranschaulicht, das für drei Steuerelemente (IDC_MYCTRL1 durch IDC_MYCTRL3) implementiert wird. Die Ereignishandlerfunktion `OnRangeMouseDown` wird in der Header Datei der Dialogfeld Klasse ( `CMyDlg` ) wie folgt deklariert:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Der folgende Code wird in der Implementierungs Datei der Dialogfeld Klasse definiert.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a> ON_EVENT_REFLECT

Wenn das ON_EVENT_REFLECT-Makro in der Ereignis Senke-Zuordnung der Wrapper Klasse eines OLE-Steuer Elements verwendet wird, empfängt Ereignisse, die vom Steuerelement ausgelöst werden, bevor Sie vom Container des Steuer Elements behandelt werden.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, zu der diese Ereignis Senke-Zuordnung gehört.

*DISPID*<br/>
Die Dispatch-ID des Ereignisses, das vom-Steuerelement ausgelöst wird.

*pfnhandler*<br/>
Zeiger auf eine Member-Funktion, die das Ereignis behandelt. Diese Funktion muss einen booleschen Rückgabetyp und Parametertypen aufweisen, die den Parameter des Ereignisses entsprechen (siehe *vtsParams*). Die Funktion sollte true zurückgeben, um anzugeben, dass das Ereignis behandelt wurde. andernfalls false.

*vtsParams*<br/>
Eine Sequenz von **VTS_** Konstanten, die die Typen der Parameter für das Ereignis angibt. Dabei handelt es sich um dieselben Konstanten, die in dispatchzuordnungseinträgen wie DISP_FUNCTION verwendet werden.

### <a name="remarks"></a>Bemerkungen

Das *vtsParams* -Argument ist eine durch Leerzeichen getrennte Liste mit Werten aus den **VTS_** Konstanten.

Einer oder mehrere dieser Werte, getrennt durch Leerzeichen (nicht Kommas), gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze Ganzzahl gefolgt von einem booleschen Wert enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="on_propnotify"></a><a name="on_propnotify"></a> ON_PROPNOTIFY

Verwenden Sie das ON_PROPNOTIFY-Makro zum Definieren eines Zuordnungs Eintrags für die Ereignis Senke für die Behandlung von Eigenschafts Benachrichtigungen von einem OLE

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, zu der diese Ereignis Senke-Zuordnung gehört.

*id*<br/>
Die Steuerelement-ID des OLE-Steuer Elements.

*DISPID*<br/>
Die Dispatch-ID der Eigenschaft, die an der Benachrichtigung beteiligt ist.

*pfnrequest*<br/>
Zeiger auf eine Member-Funktion, die die `OnRequestEdit` Benachrichtigung für diese Eigenschaft behandelt. Diese Funktion muss einen bool-Rückgabetyp und einen **bool** - <strong>\*</strong> Parameter aufweisen. Diese Funktion sollte den-Parameter auf true festlegen, damit die-Eigenschaft geändert werden kann, und false, um Sie zu unterbinden. Die Funktion sollte true zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls false.

*PFN geändert*<br/>
Zeiger auf eine Member-Funktion, die die `OnChanged` Benachrichtigung für diese Eigenschaft behandelt. Die Funktion sollte einen booleschen Rückgabetyp und einen uint-Parameter aufweisen. Die Funktion sollte true zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Das *vtsParams* -Argument ist eine durch Leerzeichen getrennte Liste mit Werten aus den **VTS_** Konstanten. Einer oder mehrere dieser Werte, getrennt durch Leerzeichen (nicht Kommas), gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze Ganzzahl gefolgt von einem booleschen Wert enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a> ON_PROPNOTIFY_RANGE

Verwenden Sie das ON_PROPNOTIFY_RANGE-Makro zum Definieren eines Zuordnungs Eintrags für die Ereignis Senke, um Eigenschafts Benachrichtigungen von einem OLE-Steuerelement mit einer Steuerelement-ID in einem zusammenhängenden Bereich von IDs zu

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, zu der diese Ereignis Senke-Zuordnung gehört.

*idfirst*<br/>
Die Steuerelement-ID des ersten OLE-Steuer Elements im Bereich.

*idlast*<br/>
Die Steuerelement-ID des letzten OLE-Steuer Elements im Bereich.

*DISPID*<br/>
Die Dispatch-ID der Eigenschaft, die an der Benachrichtigung beteiligt ist.

*pfnrequest*<br/>
Zeiger auf eine Member-Funktion, die die `OnRequestEdit` Benachrichtigung für diese Eigenschaft behandelt. Diese Funktion sollte über einen `BOOL` Rückgabetyp und `UINT` - `BOOL*` Parameter verfügen. Die-Funktion sollte den-Parameter auf true festlegen, damit die-Eigenschaft geändert werden kann, und false, um dies zu unterbinden. Die Funktion sollte true zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls false.

*PFN geändert*<br/>
Zeiger auf eine Member-Funktion, die die `OnChanged` Benachrichtigung für diese Eigenschaft behandelt. Die Funktion sollte über einen `BOOL` Rückgabetyp und einen `UINT` Parameter verfügen. Die Funktion sollte true zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls false.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a> ON_PROPNOTIFY_REFLECT

Das ON_PROPNOTIFY_REFLECT-Makro, wenn es in der Ereignis Senke-Zuordnung der Wrapper Klasse eines OLE-Steuer Elements verwendet wird, empfängt Eigenschafts Benachrichtigungen, die vom Steuerelement gesendet werden, bevor Sie vom Container des Steuer Elements behandelt werden.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parameter

*spiegeln*<br/>
Die Klasse, zu der diese Ereignis Senke-Zuordnung gehört.

*DISPID*<br/>
Die Dispatch-ID der Eigenschaft, die an der Benachrichtigung beteiligt ist.

*pfnrequest*<br/>
Zeiger auf eine Member-Funktion, die die `OnRequestEdit` Benachrichtigung für diese Eigenschaft behandelt. Diese Funktion muss einen bool-Rückgabetyp und einen **bool** - <strong>\*</strong> Parameter aufweisen. Diese Funktion sollte den-Parameter auf true festlegen, damit die-Eigenschaft geändert werden kann, und false, um Sie zu unterbinden. Die Funktion sollte true zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls false.

*PFN geändert*<br/>
Zeiger auf eine Member-Funktion, die die `OnChanged` Benachrichtigung für diese Eigenschaft behandelt. Die Funktion sollte einen booleschen Rückgabetyp und keine Parameter aufweisen. Die Funktion sollte true zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls false.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxdisp. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
