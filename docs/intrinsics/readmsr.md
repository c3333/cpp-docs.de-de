---
title: __readmsr
ms.date: 09/02/2019
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 029119bc47d0172c7e9cc5fbf8cd20c4ee23e0f0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219650"
---
# <a name="__readmsr"></a>__readmsr

**Microsoft-spezifisch**

Generiert die- `rdmsr` Anweisung, die das modellspezifische Register liest, das von angegeben wird, **`register`** und gibt den Wert zurück.

## <a name="syntax"></a>Syntax

```C
__int64 __readmsr(
   int register
);
```

### <a name="parameters"></a>Parameter

*sich*\
in Das modellspezifische Register, das gelesen werden soll.

## <a name="return-value"></a>Rückgabewert

Der Wert im angegebenen Register.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Diese Funktion ist nur im Kernel Modus verfügbar, und die Routine ist nur als systeminterne Funktion verfügbar.

Weitere Informationen finden Sie in der AMD-Dokumentation.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)
