---
title: Ereignissenkenzuordnungen
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps [MFC]
ms.assetid: a9757eb2-5f4a-45ec-a2cd-ce5eec85b16f
ms.openlocfilehash: 731ed2403aae3332e81702673d1181e9e52399a2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365724"
---
# <a name="event-sink-maps"></a>Ereignissenkenzuordnungen

Wenn ein eingebettetes OLE-Steuerelement ein Ereignis auslöst, empfängt der Container des Steuerelements das Ereignis mithilfe eines Mechanismus, der als "Ereignissenkenzuordnung" bezeichnet wird und von MFC bereitgestellt wird. Diese Ereignissenkenzuordnung bezeichnet Handlerfunktionen für jedes bestimmte Ereignis sowie Parameter dieser Ereignisse. Weitere Informationen zu Ereignissenkenzuordnungen finden Sie im Artikel [ActiveX Control Containers](../../mfc/activex-control-containers.md).

### <a name="event-sink-maps"></a>Ereignissenkenzuordnungen

|||
|-|-|
|[BEGIN_EVENTSINK_MAP](#begin_eventsink_map)|Startet die Definition einer Ereignissenkenzuordnung.|
|[DECLARE_EVENTSINK_MAP](#declare_eventsink_map)|Deklariert eine Ereignissenkenzuordnung.|
|[END_EVENTSINK_MAP](#end_eventsink_map)|Beendet die Definition einer Ereignissenkenzuordnung.|
|[ON_EVENT](#on_event)|Definiert einen Ereignishandler für ein bestimmtes Ereignis.|
|[ON_EVENT_RANGE](#on_event_range)|Definiert einen Ereignishandler für ein bestimmtes Ereignis, das von einer Gruppe von OLE-Steuerelementen ausgelöst wird.|
|[ON_EVENT_REFLECT](#on_event_reflect)|Empfängt Ereignisse, die vom Steuerelement ausgelöst werden, bevor sie vom Container des Steuerelements verarbeitet werden.|
|[ON_PROPNOTIFY](#on_propnotify)|Definiert einen Handler für die Behandlung von Eigenschaftenbenachrichtigungen aus einem OLE-Steuerelement.|
|[ON_PROPNOTIFY_RANGE](#on_propnotify_range)|Definiert einen Handler für die Behandlung von Eigenschaftenbenachrichtigungen aus einer Gruppe von OLE-Steuerelementen.|
|[ON_PROPNOTIFY_REFLECT](#on_propnotify_reflect)|Empfängt Vom Steuerelement gesendete Eigenschaftsbenachrichtigungen, bevor sie vom Container des Steuerelements verarbeitet werden.|

## <a name="begin_eventsink_map"></a><a name="begin_eventsink_map"></a>BEGIN_EVENTSINK_MAP

Beginnt die Definition der Ereignissenkenzuordnung.

```
BEGIN_EVENTSINK_MAP(theClass, baseClass)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Gibt den Namen der Steuerelementklasse an, deren Ereignissenkenzuordnung dies ist.

*Baseclass*<br/>
Gibt den Namen der Basisklasse *derKlasse*an.

### <a name="remarks"></a>Bemerkungen

Starten Sie in der Implementierungsdatei (.cpp), die die Memberfunktionen für Ihre Klasse definiert, die Ereignissenkenzuordnung mit dem Makro BEGIN_EVENTSINK_MAP, fügen Sie dann Makroeinträge für jedes ereignisbenachrichtigungsteilnehmer Ereignis hinzu, und schließen Sie die Ereignissenkenzuordnung mit dem END_EVENTSINK_MAP-Makro ab.

Weitere Informationen zu Ereignissenkenzuordnungen und OLE-Steuerelementcontainern finden Sie im Artikel [ActiveX Control Containers](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="declare_eventsink_map"></a><a name="declare_eventsink_map"></a>DECLARE_EVENTSINK_MAP

Ein OLE-Container kann eine Ereignissenkenzuordnung bereitstellen, um die Ereignisse anzugeben, über die Ihr Container benachrichtigt wird.

```
DECLARE_EVENTSINK_MAP()
```

### <a name="remarks"></a>Bemerkungen

Verwenden Sie das DECLARE_EVENTSINK_MAP-Makro am Ende der Klassendeklaration. Dann, in der . CPP-Datei, die die Memberfunktionen für die Klasse definiert, verwenden Sie die BEGIN_EVENTSINK_MAP Makros, Makroeinträge für jedes der ereignisse, über die benachrichtigt werden soll, und das END_EVENTSINK_MAP Makro, um das Ende der Ereignissenkenliste zu deklarieren.

Weitere Informationen zu Ereignissenkenzuordnungen finden Sie im Artikel [ActiveX Control Containers](../../mfc/activex-control-containers.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxwin.h

## <a name="end_eventsink_map"></a><a name="end_eventsink_map"></a>END_EVENTSINK_MAP

Beendet die Definition der Ereignissenkenzuordnung.

```
END_EVENTSINK_MAP()
```

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="on_event"></a><a name="on_event"></a>ON_EVENT

Verwenden Sie das ON_EVENT-Makro, um eine Ereignishandlerfunktion für ein Ereignis zu definieren, das von einem OLE-Steuerelement ausgelöst wird.

```
ON_EVENT(theClass, id, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, zu der diese Ereignissenkenzuordnung gehört.

*id*<br/>
Die Steuer-ID des OLE-Steuerelements.

*Dispid*<br/>
Die Dispatch-ID des Ereignisses, das vom Steuerelement ausgelöst wurde.

*pfnHandler*<br/>
Zeiger auf eine Memberfunktion, die das Ereignis verarbeitet. Diese Funktion sollte über einen BOOL-Rückgabetyp und Parametertypen verfügen, die den Parametern des Ereignisses entsprechen (siehe *vtsParams*). Die Funktion sollte TRUE zurückgeben, um anzugeben, dass das Ereignis behandelt wurde. andernfalls FALSE.

*vtsParams*<br/>
Eine Sequenz von **VTS_** Konstanten, die die Typen der Parameter für das Ereignis angibt. Dies sind die gleichen Konstanten, die in Dispatchkarteneinträgen wie DISP_FUNCTION verwendet werden.

### <a name="remarks"></a>Bemerkungen

Das Argument *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus der **VTS_** Konstanten. Mindestens einer dieser Werte, die durch Leerzeichen (keine Kommas) getrennt sind, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze ganze Zahl gefolgt von einem BOOL enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="on_event_range"></a><a name="on_event_range"></a>ON_EVENT_RANGE

Verwenden Sie das ON_EVENT_RANGE-Makro, um eine Ereignishandlerfunktion für ein Ereignis zu definieren, das von einem OLE-Steuerelement ausgelöst wird, das eine Steuerelement-ID innerhalb eines zusammenhängenden ID-Bereichs hat.

```
ON_EVENT_RANGE(theClass, idFirst, idLast, dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, zu der diese Ereignissenkenzuordnung gehört.

*idFirst*<br/>
Die Steuer-ID des ersten OLE-Steuerelements im Bereich.

*idLast*<br/>
Die Steuer-ID des letzten OLE-Steuerelements im Bereich.

*Dispid*<br/>
Die Dispatch-ID des Ereignisses, das vom Steuerelement ausgelöst wurde.

*pfnHandler*<br/>
Zeiger auf eine Memberfunktion, die das Ereignis verarbeitet. Diese Funktion sollte einen BOOL-Rückgabetyp, einen ersten Parameter vom Typ UINT (für die Steuer-ID) und zusätzliche Parametertypen haben, die den Parametern des Ereignisses entsprechen (siehe *vtsParams*). Die Funktion sollte TRUE zurückgeben, um anzugeben, dass das Ereignis behandelt wurde. andernfalls FALSE.

*vtsParams*<br/>
Eine Sequenz von **VTS_** Konstanten, die die Typen der Parameter für das Ereignis angibt. Die erste Konstante sollte vom Typ VTS_I4 für die Steuerelement-ID sein. Dies sind die gleichen Konstanten, die in Dispatchkarteneinträgen wie DISP_FUNCTION verwendet werden.

### <a name="remarks"></a>Bemerkungen

Das Argument *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus der **VTS_** Konstanten. Mindestens einer dieser Werte, die durch Leerzeichen (keine Kommas) getrennt sind, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze ganze Zahl gefolgt von einem BOOL enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird ein Ereignishandler für das MouseDown-Ereignis veranschaulicht, das für drei Steuerelemente implementiert ist (IDC_MYCTRL1 bis IDC_MYCTRL3). Die Ereignishandlerfunktion `OnRangeMouseDown`, wird in der Headerdatei `CMyDlg`der Dialogklasse ( ) als deklariert:

[!code-cpp[NVC_MFCAutomation#12](../../mfc/codesnippet/cpp/event-sink-maps_2.h)]

Der folgende Code ist in der Implementierungsdatei der Dialogklasse definiert.

[!code-cpp[NVC_MFCAutomation#13](../../mfc/codesnippet/cpp/event-sink-maps_3.cpp)]

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="on_event_reflect"></a><a name="on_event_reflect"></a>ON_EVENT_REFLECT

Das ON_EVENT_REFLECT-Makro, wenn es in der Ereignissenkenzuordnung der Wrapperklasse eines OLE-Steuerelements verwendet wird, empfängt Ereignisse, die vom Steuerelement ausgelöst werden, bevor sie vom Container des Steuerelements behandelt werden.

```
ON_EVENT_REFLECT(theClass,  dispid, pfnHandler,  vtsParams)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, zu der diese Ereignissenkenzuordnung gehört.

*Dispid*<br/>
Die Dispatch-ID des Ereignisses, das vom Steuerelement ausgelöst wurde.

*pfnHandler*<br/>
Zeiger auf eine Memberfunktion, die das Ereignis verarbeitet. Diese Funktion sollte über einen BOOL-Rückgabetyp und Parametertypen verfügen, die den Parametern des Ereignisses entsprechen (siehe *vtsParams*). Die Funktion sollte TRUE zurückgeben, um anzugeben, dass das Ereignis behandelt wurde. andernfalls FALSE.

*vtsParams*<br/>
Eine Sequenz von **VTS_** Konstanten, die die Typen der Parameter für das Ereignis angibt. Dies sind die gleichen Konstanten, die in Dispatchkarteneinträgen wie DISP_FUNCTION verwendet werden.

### <a name="remarks"></a>Bemerkungen

Das Argument *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus der **VTS_** Konstanten.

Mindestens einer dieser Werte, die durch Leerzeichen (keine Kommas) getrennt sind, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze ganze Zahl gefolgt von einem BOOL enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="on_propnotify"></a><a name="on_propnotify"></a>ON_PROPNOTIFY

Verwenden Sie das ON_PROPNOTIFY-Makro, um einen Ereignissenkenzuordnungseintrag für die Behandlung von Eigenschaftsbenachrichtigungen aus einem OLE-Steuerelement zu definieren.

```
ON_PROPNOTIFY(theClass, id, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, zu der diese Ereignissenkenzuordnung gehört.

*id*<br/>
Die Steuer-ID des OLE-Steuerelements.

*Dispid*<br/>
Die Dispatch-ID der an der Benachrichtigung beteiligten Eigenschaft.

*pfnRequest*<br/>
Zeiger auf eine Memberfunktion, `OnRequestEdit` die die Benachrichtigung für diese Eigenschaft verarbeitet. Diese Funktion sollte über einen BOOL-Rückgabetyp und einen **BOOL-Parameter** <strong>\*</strong> verfügen. Diese Funktion sollte den Parameter auf TRUE setzen, damit sich die Eigenschaft ändern kann und FALSE nicht zugelassen werden kann. Die Funktion sollte TRUE zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls FALSE.

*pfnChanged*<br/>
Zeiger auf eine Memberfunktion, `OnChanged` die die Benachrichtigung für diese Eigenschaft verarbeitet. Die Funktion sollte einen BOOL-Rückgabetyp und einen UINT-Parameter haben. Die Funktion sollte TRUE zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Das Argument *vtsParams* ist eine durch Leerzeichen getrennte Liste von Werten aus der **VTS_** Konstanten. Mindestens einer dieser Werte, die durch Leerzeichen (keine Kommas) getrennt sind, gibt die Parameterliste der Funktion an. Beispiel:

[!code-cpp[NVC_MFCAutomation#11](../../mfc/codesnippet/cpp/event-sink-maps_1.cpp)]

gibt eine Liste an, die eine kurze ganze Zahl gefolgt von einem BOOL enthält.

Eine Liste der **VTS_** Konstanten finden Sie unter [EVENT_CUSTOM](event-maps.md#event_custom).

## <a name="on_propnotify_range"></a><a name="on_propnotify_range"></a>ON_PROPNOTIFY_RANGE

Verwenden Sie das Makro ON_PROPNOTIFY_RANGE, um einen Ereignissenkenzuordnungseintrag für die Behandlung von Eigenschaftsbenachrichtigungen von jedem OLE-Steuerelement mit einer Steuerelement-ID innerhalb eines zusammenhängenden ID-Bereichs zu definieren.

```

ON_PROPNOTIFY_RANGE(theClass, idFirst, idLast, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, zu der diese Ereignissenkenzuordnung gehört.

*idFirst*<br/>
Die Steuer-ID des ersten OLE-Steuerelements im Bereich.

*idLast*<br/>
Die Steuer-ID des letzten OLE-Steuerelements im Bereich.

*Dispid*<br/>
Die Dispatch-ID der an der Benachrichtigung beteiligten Eigenschaft.

*pfnRequest*<br/>
Zeiger auf eine Memberfunktion, `OnRequestEdit` die die Benachrichtigung für diese Eigenschaft verarbeitet. Diese Funktion sollte `BOOL` über `UINT` einen `BOOL*` Rückgabetyp und Parameter verfügen. Die Funktion sollte den Parameter auf TRUE setzen, damit sich die Eigenschaft ändern kann und FALSE nicht zugelassen wird. Die Funktion sollte TRUE zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls FALSE.

*pfnChanged*<br/>
Zeiger auf eine Memberfunktion, `OnChanged` die die Benachrichtigung für diese Eigenschaft verarbeitet. Die Funktion sollte `BOOL` einen Rückgabetyp und einen `UINT` Parameter haben. Die Funktion sollte TRUE zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls FALSE.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="on_propnotify_reflect"></a><a name="on_propnotify_reflect"></a>ON_PROPNOTIFY_REFLECT

Das ON_PROPNOTIFY_REFLECT-Makro, wenn es in der Ereignissenkenzuordnung der Wrapperklasse eines OLE-Steuerelements verwendet wird, empfängt Vom Steuerelement gesendete Eigenschaftsbenachrichtigungen, bevor sie vom Container des Steuerelements verarbeitet werden.

```

ON_PROPNOTIFY_REFLECT(theClass, dispid, pfnRequest, pfnChanged)
```

### <a name="parameters"></a>Parameter

*theClass*<br/>
Die Klasse, zu der diese Ereignissenkenzuordnung gehört.

*Dispid*<br/>
Die Dispatch-ID der an der Benachrichtigung beteiligten Eigenschaft.

*pfnRequest*<br/>
Zeiger auf eine Memberfunktion, `OnRequestEdit` die die Benachrichtigung für diese Eigenschaft verarbeitet. Diese Funktion sollte über einen BOOL-Rückgabetyp und einen **BOOL-Parameter** <strong>\*</strong> verfügen. Diese Funktion sollte den Parameter auf TRUE setzen, damit sich die Eigenschaft ändern kann und FALSE nicht zugelassen werden kann. Die Funktion sollte TRUE zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls FALSE.

*pfnChanged*<br/>
Zeiger auf eine Memberfunktion, `OnChanged` die die Benachrichtigung für diese Eigenschaft verarbeitet. Die Funktion sollte einen BOOL-Rückgabetyp und keine Parameter haben. Die Funktion sollte TRUE zurückgeben, um anzugeben, dass die Benachrichtigung behandelt wurde. andernfalls FALSE.

### <a name="requirements"></a>Anforderungen

  **Header** afxdisp.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](../../mfc/reference/mfc-macros-and-globals.md)
