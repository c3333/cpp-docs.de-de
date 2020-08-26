---
title: Zusammengesetzte Steuerelement Makros
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 7ac13a11646faca53b38ec610dc0388bdd14d251
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833542"
---
# <a name="composite-control-macros"></a>Zusammengesetzte Steuerelement Makros

Diese Makros definieren ereignissenkenmaps und-Einträge.

|Makro|Beschreibung|
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Markiert den Anfang der Ereignis Senke-Zuordnung für das zusammengesetzte Steuerelement.|
|[END_SINK_MAP](#end_sink_map)|Markiert das Ende der Ereignis senkmap für das zusammengesetzte Steuerelement.|
|[SINK_ENTRY](#sink_entry)|Eintrag zur Ereignis Senke-Zuordnung.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Eintrag zur Ereignis Senke-Zuordnung mit einem zusätzlichen Parameter.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Ähnlich wie SINK_ENTRY_EX mit der Ausnahme, dass Sie einen Zeiger auf die IID annimmt.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Eintrag zur Ereignis Senke-Zuordnung mit manuell bereitgestellten Typinformationen für die Verwendung mit [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Ähnlich wie SINK_ENTRY_INFO mit der Ausnahme, dass Sie einen Zeiger auf die IID annimmt.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a> BEGIN_SINK_MAP

Deklariert den Anfang der Ereignis Senke-Zuordnung für das zusammengesetzte Steuerelement.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parameter

*_class*<br/>
in Gibt das Steuerelement an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Bemerkungen

Die CE-ATL-Implementierung von ActiveX-Ereignis senken unterstützt nur Rückgabewerte vom Typ HRESULT oder void aus den Ereignishandlermethoden. alle anderen Rückgabewerte werden nicht unterstützt, und ihr Verhalten ist nicht definiert.

## <a name="end_sink_map"></a><a name="end_sink_map"></a> END_SINK_MAP

Deklariert das Ende der Ereignis Senke-Zuordnung für das zusammengesetzte Steuerelement.

```
END_SINK_MAP()
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Bemerkungen

Die CE-ATL-Implementierung von ActiveX-Ereignis senken unterstützt nur Rückgabewerte vom Typ HRESULT oder void aus den Ereignishandlermethoden. alle anderen Rückgabewerte werden nicht unterstützt, und ihr Verhalten ist nicht definiert.

## <a name="sink_entry"></a><a name="sink_entry"></a> SINK_ENTRY

Deklariert die Handlerfunktion (*FN*) für das angegebene Ereignis (*DISPID*) des durch die *ID*identifizierten Steuer Elements.

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Bezeichnet das-Steuerelement.

*DISPID*<br/>
in Identifiziert das angegebene Ereignis.

*fn*<br/>
in Der Name der Ereignishandlerfunktion. Diese Funktion muss die `_stdcall` -Aufruf Konvention verwenden und über die entsprechende dispinterface-Signatur verfügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Bemerkungen

Die CE-ATL-Implementierung von ActiveX-Ereignis senken unterstützt nur Rückgabewerte vom Typ HRESULT oder void aus den Ereignishandlermethoden. alle anderen Rückgabewerte werden nicht unterstützt, und ihr Verhalten ist nicht definiert.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a> SINK_ENTRY_EX und SINK_ENTRY_EX_P

Deklariert die Handlerfunktion (*FN*) für das angegebene Ereignis (*DISPID*) der Dispatchschnittstelle (*IID*) für das durch die *ID*identifizierte Steuerelement.

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Bezeichnet das-Steuerelement.

*IID*<br/>
in Bezeichnet die Dispatch-Schnittstelle.

*piid*<br/>
in Zeiger auf die Dispatch-Schnittstelle.

*DISPID*<br/>
in Identifiziert das angegebene Ereignis.

*fn*<br/>
in Der Name der Ereignishandlerfunktion. Diese Funktion muss die `_stdcall` -Aufruf Konvention verwenden und über die entsprechende dispinterface-Signatur verfügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Bemerkungen

Die CE-ATL-Implementierung von ActiveX-Ereignis senken unterstützt nur Rückgabewerte vom Typ HRESULT oder void aus den Ereignishandlermethoden. alle anderen Rückgabewerte werden nicht unterstützt, und ihr Verhalten ist nicht definiert.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a> SINK_ENTRY_INFO und SINK_ENTRY_INFO_P

Verwenden Sie das SINK_ENTRY_INFO-Makro innerhalb einer Ereignissenkenzuordnung, um die von [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) benötigten Informationen bereitzustellen, um Ereignisse an die relevante Handlerfunktion weiterzuleiten.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*id*<br/>
in Eine Ganzzahl ohne Vorzeichen, die die Ereignis Quelle identifiziert. Dieser Wert muss dem *NID* -Vorlagen Parameter entsprechen, der in der zugehörigen [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) -Basisklasse verwendet wird.

*IID*<br/>
in IID, die die Dispatchschnittstelle identifiziert.

*piid*<br/>
in Zeiger auf IID, der die Dispatchschnittstelle identifiziert.

*DISPID*<br/>
in DISPID, die das angegebene Ereignis identifiziert.

*fn*<br/>
in Der Name der Ereignishandlerfunktion. Diese Funktion muss die `_stdcall` -Aufruf Konvention verwenden und über die entsprechende dispinterface-Signatur verfügen.

*Opo*<br/>
in Typinformationen für die Ereignishandlerfunktion. Diese Typinformationen werden in Form eines Zeigers auf eine-Struktur bereitgestellt `_ATL_FUNC_INFO` . CC_CDECL ist die einzige Option, die in Windows CE für das Feld Callin der Struktur unterstützt wird `_ATL_FUNC_INFO` . Alle anderen Werte werden nicht unterstützt, daher ist das Verhalten nicht definiert.

### <a name="remarks"></a>Bemerkungen

Die ersten vier Makro Parameter sind identisch mit denen für das [SINK_ENTRY_EX](#sink_entry_ex) Makro. Der Final-Parameter stellt Typinformationen für das-Ereignis bereit. Die CE-ATL-Implementierung von ActiveX-Ereignis senken unterstützt nur Rückgabewerte vom Typ HRESULT oder void aus den Ereignishandlermethoden. alle anderen Rückgabewerte werden nicht unterstützt, und ihr Verhalten ist nicht definiert.

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)<br/>
[Globale Funktionen des zusammengesetzten Steuer Elements](../../atl/reference/composite-control-global-functions.md)
