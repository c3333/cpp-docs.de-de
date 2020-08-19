---
title: __lidt
ms.date: 09/02/2019
f1_keywords:
- __lidt
- __lidt_cpp
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
ms.openlocfilehash: 87a49643e7cd11ae57dc01130f250895cf012065
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562492"
---
# <a name="__lidt"></a>__lidt

**Microsoft-spezifisch**

Lädt das interruptdeskriptortabellenregister (IDTR) mit dem Wert an der angegebenen Speicheradresse.

## <a name="syntax"></a>Syntax

```C
void __lidt(void * Source);
```

### <a name="parameters"></a>Parameter

*Ausgangs*\
in Zeiger auf den Wert, der in den IDTR kopiert werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`__lidt`|x86, x64|

**Headerdatei** \<intrin.h>

## <a name="remarks"></a>Bemerkungen

Die `__lidt` -Funktion entspricht der `LIDT` -Computer Anweisung und ist nur im Kernel Modus verfügbar. Weitere Informationen finden Sie im Dokument "Intel Architecture Software Developer es Manual, Volume 2: Instruction Set Reference" auf der Website der [Intel Corporation](https://software.intel.com/articles/intel-sdm) .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)\
[__sidt](../intrinsics/sidt.md)
