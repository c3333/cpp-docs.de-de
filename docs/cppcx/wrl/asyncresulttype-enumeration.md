---
title: AsyncResultType-Enumeration
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: b8a2a9ec803fba1be0012fcb58bf3b42e78f9071
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214161"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType-Enumeration

Gibt den Ergebnistyp an, der von der `GetResults()` Methode zurückgegeben wird.

## <a name="syntax"></a>Syntax

```cpp
enum AsyncResultType;
```

## <a name="members"></a>Members

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`MultipleResults`|Mehrere Ergebnisse, die progressiv zwischen `Start` Status und vor dem Aufruf von `Close()` dargestellt werden.|
|`SingleResult`|Ein einzelnes Ergebnis, das nach dem Auftreten des `Complete` Ereignisses angezeigt wird.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
