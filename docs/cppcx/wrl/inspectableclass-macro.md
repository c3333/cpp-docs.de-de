---
title: InspectableClass-Makro
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: 755a8f58ffc290d73d6060b0b0924905ecbf6028
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213875"
---
# <a name="inspectableclass-macro"></a>InspectableClass-Makro

Legt den Ablaufklassennamen und die Vertrauensebene fest.

## <a name="syntax"></a>Syntax

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>Parameter

*runtimeclassname*<br/>
Der vollständige wörtliche Name der Laufzeitklasse.

*Trust Level*<br/>
Einer der [Trust Level](/windows/win32/api/inspectable/ne-inspectable-trustlevel) -Enumerationswerte.

## <a name="remarks"></a>Bemerkungen

Das **inspectableclass** -Makro kann nur mit Windows-Runtime Typen verwendet werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Weitere Informationen

[RuntimeClass-Klasse](runtimeclass-class.md)
