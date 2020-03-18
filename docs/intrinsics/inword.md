---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 7daaf1abd5089716061f118e30e9534e5c5c18ee
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440980"
---
# <a name="__inword"></a>__inword

**Microsoft-spezifisch**

Liest Daten mithilfe der `in` Anweisung aus dem angegebenen Port.

## <a name="syntax"></a>Syntax

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parameter

*Port*\
in Der Port, von dem gelesen werden soll.

## <a name="return-value"></a>Rückgabewert

Das gelesene Wort vom Datentyp.

## <a name="requirements"></a>Requirements (Anforderungen)

|Intrinsic|Aufbau|
|---------------|------------------|
|`__inword`|x86, x64|

**Header Datei** \<"intrin. h" >

## <a name="remarks"></a>Bemerkungen

Diese Routine ist nur als systeminterne Funktion verfügbar.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Systeminterne Compilerfunktionen](../intrinsics/compiler-intrinsics.md)
