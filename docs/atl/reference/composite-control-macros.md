---
title: Zusammengesetzte Steuerungsmakros
ms.date: 05/06/2019
f1_keywords:
- atlcom/ATL::BEGIN_SINK_MAP
- atlcom/ATL::END_SINK_MAP
- atlcom/ATL::SINK_ENTRY
helpviewer_keywords:
- composite controls, macros
ms.assetid: 17f2dd5e-07e6-4aa6-b965-7a361c78c45e
ms.openlocfilehash: 67ad18c07a92cfecca44667908a8488e8c2da234
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331517"
---
# <a name="composite-control-macros"></a>Zusammengesetzte Steuerungsmakros

Diese Makros definieren Ereignissenkenzuordnungen und Einträge.

|||
|-|-|
|[BEGIN_SINK_MAP](#begin_sink_map)|Markiert den Anfang der Ereignissenkenzuordnung für das zusammengesetzte Steuerelement.|
|[END_SINK_MAP](#end_sink_map)|Markiert das Ende der Ereignissenkenzuordnung für das zusammengesetzte Steuerelement.|
|[SINK_ENTRY](#sink_entry)|Eintrag zur Ereignissenkenzuordnung.|
|[SINK_ENTRY_EX](#sink_entry_ex)|Eintrag in die Ereignissenkenzuordnung mit einem zusätzlichen Parameter.|
|[SINK_ENTRY_EX_P](#sink_entry_ex)| (Visual Studio 2017) Ähnlich wie SINK_ENTRY_EX außer, dass es einen Zeiger auf iid benötigt.|
|[SINK_ENTRY_INFO](#sink_entry_info)|Eingabe in die Ereignissenkenzuordnung mit manuell bereitgestellten Typinformationen zur Verwendung mit [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md).|
|[SINK_ENTRY_INFO_P](#sink_entry_info)| (Visual Studio 2017) Ähnlich wie SINK_ENTRY_INFO außer, dass es einen Zeiger auf iid benötigt.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="begin_sink_map"></a><a name="begin_sink_map"></a>BEGIN_SINK_MAP

Deklariert den Anfang der Ereignissenkenzuordnung für das zusammengesetzte Steuerelement.

```
BEGIN_SINK_MAP(_class)
```

### <a name="parameters"></a>Parameter

*_class*<br/>
[in] Gibt das Steuerelement an.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Bemerkungen

Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

## <a name="end_sink_map"></a><a name="end_sink_map"></a>END_SINK_MAP

Deklariert das Ende der Ereignissenkenzuordnung für das zusammengesetzte Steuerelement.

```
END_SINK_MAP()
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Bemerkungen

Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

## <a name="sink_entry"></a><a name="sink_entry"></a>SINK_ENTRY

Deklariert die Handlerfunktion (*fn*) für das angegebene Ereignis (*dispid*), des durch *id*identifizierten Steuerelements .

```
SINK_ENTRY( id, dispid, fn )
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Identifiziert das Steuerelement.

*Dispid*<br/>
[in] Identifiziert das angegebene Ereignis.

*fn*<br/>
[in] Name der Ereignishandlerfunktion. Diese Funktion muss `_stdcall` die aufrufende Konvention verwenden und über die entsprechende Signatur im Dispinterface-Stil verfügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#104](../../atl/codesnippet/cpp/composite-control-macros_1.h)]

### <a name="remarks"></a>Bemerkungen

Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

## <a name="sink_entry_ex-and-sink_entry_ex_p"></a><a name="sink_entry_ex"></a>SINK_ENTRY_EX und SINK_ENTRY_EX_P

Deklariert die Handlerfunktion (*fn*) für das angegebene Ereignis (*dispid*), der Dispatch-Schnittstelle (*iid*), für das durch *id*identifizierte Steuerelement .

```
SINK_ENTRY_EX( id, iid, dispid, fn )
SINK_ENTRY_EX_P( id, piid, dispid, fn ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Identifiziert das Steuerelement.

*Iid*<br/>
[in] Identifiziert die Dispatchschnittstelle.

*piid*<br/>
[in] Zeiger auf die Dispatch-Schnittstelle.

*Dispid*<br/>
[in] Identifiziert das angegebene Ereignis.

*fn*<br/>
[in] Name der Ereignishandlerfunktion. Diese Funktion muss `_stdcall` die aufrufende Konvention verwenden und über die entsprechende Signatur im Dispinterface-Stil verfügen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#136](../../atl/codesnippet/cpp/composite-control-macros_2.h)]

### <a name="remarks"></a>Bemerkungen

Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

## <a name="sink_entry_info-and-sink_entry_info_p"></a><a name="sink_entry_info"></a>SINK_ENTRY_INFO und SINK_ENTRY_INFO_P

Verwenden Sie das SINK_ENTRY_INFO-Makro in einer Ereignissenkenzuordnung, um die von [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) benötigten Informationen bereitzustellen, um Ereignisse an die entsprechende Handlerfunktion weiterzuleiten.

```
SINK_ENTRY_INFO( id, iid, dispid, fn, info )
SINK_ENTRY_INFO_P( id, piid, dispid, fn, info ) // (Visual Studio 2017)
```

### <a name="parameters"></a>Parameter

*id*<br/>
[in] Nicht signierte ganzzahlige Daten, die die Ereignisquelle identifizieren. Dieser Wert muss mit dem *nID-Vorlagenparameter* übereinstimmen, der in der zugehörigen [IDispEventSimpleImpl-Basisklasse](../../atl/reference/idispeventsimpleimpl-class.md) verwendet wird.

*Iid*<br/>
[in] IID, die die Dispatchschnittstelle identifiziert.

*piid*<br/>
[in] Zeiger auf IID, die die Dispatchschnittstelle identifiziert.

*Dispid*<br/>
[in] DISPID, das das angegebene Ereignis identifiziert.

*fn*<br/>
[in] Name der Ereignishandlerfunktion. Diese Funktion muss `_stdcall` die aufrufende Konvention verwenden und über die entsprechende Signatur im Dispinterface-Stil verfügen.

*info*<br/>
[in] Geben Sie Informationen für die Ereignishandlerfunktion ein. Diese Typinformationen werden in Form eines Zeigers auf eine `_ATL_FUNC_INFO` Struktur bereitgestellt. CC_CDECL ist die einzige Option, die in Windows `_ATL_FUNC_INFO` CE für das CALLCONV-Feld der Struktur unterstützt wird. Jeder andere Wert wird nicht unterstützt, so dass sein Verhalten nicht definiert ist.

### <a name="remarks"></a>Bemerkungen

Die ersten vier Makroparameter entsprechen denen [SINK_ENTRY_EX](#sink_entry_ex) für das SINK_ENTRY_EX-Makro. Der letzte Parameter stellt Typinformationen für das Ereignis bereit. Die CE ATL-Implementierung von ActiveX-Ereignissenken unterstützt nur Rückgabewerte vom Typ HRESULT oder void von Ihren Ereignishandlermethoden. Jeder andere Rückgabewert wird nicht unterstützt, und sein Verhalten ist nicht definiert.

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)<br/>
[Globale Funktionen der Composite Control](../../atl/reference/composite-control-global-functions.md)
