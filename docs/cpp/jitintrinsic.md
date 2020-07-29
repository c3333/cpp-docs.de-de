---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: cecadcad15ee65a44ad5a8245efdb69903c89459
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233703"
---
# <a name="jitintrinsic"></a>jitintrinsic

Markiert die Funktion als signifikant bei der 64-Bit-Common Language Runtime. Dies wird in bestimmten Funktionen in von Microsoft bereitgestellten Bibliotheken verwendet.

## <a name="syntax"></a>Syntax

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Bemerkungen

**`jitintrinsic`** Fügt einer Funktions Signatur ein modopt ()-Zeichen hinzu <xref:System.Runtime.CompilerServices.IsJitIntrinsic> .

Benutzer werden von der Verwendung dieses **`__declspec`** Modifizierers abgeraten, da unerwartete Ergebnisse auftreten können.

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
