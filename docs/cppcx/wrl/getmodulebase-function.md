---
title: GetModuleBase-Funktion
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 0d130fffa9fad9ae327d03eaa01d84742094cc67
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213966"
---
# <a name="getmodulebase-function"></a>GetModuleBase-Funktion

Ruft einen [modulebase](modulebase-class.md) -Zeiger ab, der das Inkrementieren und Dekrementieren des Verweis zähgers eines [runtimeclass](runtimeclass-class.md) -Objekts ermöglicht.

## <a name="syntax"></a>Syntax

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `ModuleBase`-Objekt.

## <a name="remarks"></a>Bemerkungen

Diese Funktion wird intern zum Inkrement und Dekrement der Objekt Verweis Anzahl verwendet.

Sie können diese Funktion verwenden, um Verweis Zähler durch Aufrufen von [modulebase:: incrementobjectcount](modulebase-class.md#incrementobjectcount) und [modulebase::D ecrementobjectcount](modulebase-class.md#decrementobjectcount)zu steuern.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[Microsoft::WRL-Namespace](microsoft-wrl-namespace.md)
