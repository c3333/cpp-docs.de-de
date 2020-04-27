---
title: _ATL_FUNC_INFO Struktur
ms.date: 11/04/2016
f1_keywords:
- _ATL_FUNC_INFO
- ATL::_ATL_FUNC_INFO
- ATL._ATL_FUNC_INFO
helpviewer_keywords:
- _ATL_FUNC_INFO structure
- ATL_FUNC_INFO structure
ms.assetid: 441ebe2c-f971-47de-9f52-a258e8d6f88e
ms.openlocfilehash: b1c740cf1a1ed344dbceb028bd1f39a87fc09363
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168591"
---
# <a name="_atl_func_info-structure"></a>_ATL_FUNC_INFO Struktur

Enthält Typinformationen, die verwendet werden, um eine Methode oder Eigenschaft für eine dispinterface zu beschreiben.

## <a name="syntax"></a>Syntax

```cpp
struct _ATL_FUNC_INFO {
    CALLCONV cc;
    VARTYPE vtReturn;
    SHORT nParams;
    VARTYPE pVarTypes[_ATL_MAX_VARTYPES];
};
```

## <a name="members"></a>Member

`cc`<br/>
Die Aufrufkonvention. Wenn diese Struktur mit der [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) -Klasse verwendet wird, muss dieser Member CC_STDCALL werden. `CC_CDECL`ist die einzige Option, die in Windows CE für `CALLCONV` das-Feld `_ATL_FUNC_INFO` der-Struktur unterstützt wird. Alle anderen Werte werden nicht unterstützt, daher ist das Verhalten nicht definiert.

`vtReturn`<br/>
Der Varianttyp des Funktions Rückgabewerts.

`nParams`<br/>
Die Anzahl der Funktionsparameter.

`pVarTypes`<br/>
Ein Array von Variant-Typen der Funktionsparameter.

## <a name="remarks"></a>Bemerkungen

Intern verwendet ATL diese Struktur zum Speichern von Informationen, die aus einer Typbibliothek abgerufen wurden. Sie müssen diese Struktur möglicherweise direkt bearbeiten, wenn Sie Typinformationen für einen Ereignishandler bereitstellen, der mit der [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md) -Klasse und [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) Makro verwendet wird.

## <a name="example"></a>Beispiel

Wenn eine in IDL definierte dispinterface-Methode angegeben ist:

[!code-cpp[NVC_ATL_Windowing#139](../../atl/codesnippet/cpp/atl-func-info-structure_1.idl)]

definieren Sie eine `_ATL_FUNC_INFO` Struktur:

[!code-cpp[NVC_ATL_Windowing#140](../../atl/codesnippet/cpp/atl-func-info-structure_2.h)]

## <a name="requirements"></a>Anforderungen

Header: atlcom.h

## <a name="see-also"></a>Weitere Informationen:

[Klassen und Strukturen](../../atl/reference/atl-classes.md)<br/>
[IDispEventSimpleImpl-Klasse](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)
