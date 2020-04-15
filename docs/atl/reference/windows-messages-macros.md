---
title: Windows-Nachrichtenmakros
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: a5a6d45c64d6123128ae362c1ef5643392439f41
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329409"
---
# <a name="windows-messages-macros"></a>Windows-Nachrichtenmakros

Dieses Makro leitet Fensternachrichten weiter.

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|Verwenden Sie diese Datei, um eine Nachricht, die von einem Fenster empfangen wurde, zur Verarbeitung an ein anderes Fenster weiterzuleiten.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="wm_forwardmsg"></a><a name="wm_forwardmsg"></a>WM_FORWARDMSG

Dieses Makro leitet eine Nachricht, die von einem Fenster empfangen wurde, zur Verarbeitung an ein anderes Fenster weiter.

```
WM_FORWARDMSG
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Nachricht verarbeitet wurde, Null, wenn nicht.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie WM_FORWARDMSG, um eine Nachricht, die von einem Fenster empfangen wurde, zur Verarbeitung an ein anderes Fenster weiterzuleiten. Die Parameter LPARAM und WPARAM werden wie folgt verwendet:

|Parameter|Verwendung|
|---------------|-----------|
|Wparam|Vom Benutzer definierte Daten|
|Lparam|Ein Zeiger auf `MSG` eine Struktur, die Informationen zu einer Nachricht enthält|

### <a name="example"></a>Beispiel

Stellt im folgenden `m_hWndOther` Beispiel das andere Fenster dar, das diese Nachricht empfängt.

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
