---
title: Windows-Nachrichten Makros
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: b4cd3c2eea24449eb17050b147d9c59560d8358f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834439"
---
# <a name="windows-messages-macros"></a>Windows-Nachrichten Makros

Dieses Makro leitet Fenster Meldungen weiter.

|Name|Beschreibung|
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Verwenden Sie, um eine Nachricht, die von einem Fenster empfangen wurde, zur Verarbeitung an ein anderes Fenster zu weiter|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlbase. h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a> WM_FORWARDMSG

Dieses Makro leitet eine Nachricht, die von einem Fenster empfangen wurde, zur Verarbeitung an ein anderes Fenster weiter.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Meldung verarbeitet wurde, andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie WM_FORWARDMSG, um eine von einem Fenster empfangene Nachricht zur Verarbeitung an ein anderes Fenster weiterzuleiten. Die Parameter LParam und wParam werden wie folgt verwendet:

|Parameter|Verwendung|
|---------------|-----------|
|WParam|Vom benutzerdefinierte Daten|
|LParam|Ein Zeiger auf eine- `MSG` Struktur, die Informationen zu einer Meldung enthält.|

### <a name="example"></a>Beispiel

Im folgenden Beispiel `m_hWndOther` stellt das andere Fenster dar, das diese Nachricht empfängt.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
