---
title: Compilerwarnung (Stufen 2 und 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: ab51b16331cc6a102c828234d2c2b8be84f2d276
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225240"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Compilerwarnung (Stufen 2 und 3) C4008

'Bezeichner': 'Attribut'-Attribut wird ignoriert

Der Compiler hat das-,- **`__fastcall`** **`static`** oder- **`inline`** Attribut für eine Funktion (Warnung der Stufe 3) oder Daten (Warnung der Stufe 2) ignoriert.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. **`__fastcall`** Attribut mit Daten.

1. **`static`** oder **`inline`** Attribut mit **Main** -Funktion.
