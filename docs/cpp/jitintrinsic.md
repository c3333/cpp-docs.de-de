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
ms.openlocfilehash: 4626ba82d1d24582951bbffd8e6be687007d390f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178180"
---
# <a name="jitintrinsic"></a>jitintrinsic

Markiert die Funktion als signifikant bei der 64-Bit-Common Language Runtime. Dies wird in bestimmten Funktionen in von Microsoft bereitgestellten Bibliotheken verwendet.

## <a name="syntax"></a>Syntax

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Bemerkungen

**jitintrinsier** fügt einer Funktions Signatur ein modopt (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) hinzu.

Benutzer werden davon abgeraten, diesen **__declspec** Modifizierer zu verwenden, da unerwartete Ergebnisse auftreten können.

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
