---
title: Compilerwarnung (Stufen 2 und 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 9b6fb56045d53cd18689f3903bb3d7a08c3d4e4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198003"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Compilerwarnung (Stufen 2 und 3) C4008

'Bezeichner': 'Attribut'-Attribut wird ignoriert

Der Compiler ignoriert die Attribute `__fastcall`, **static**oder **inline** für eine Funktion (Warnstufe 3) oder für Daten (Warnstufe 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. `__fastcall` -Attribute werden mit Daten.

1. Attribute**static** oder **inline** mit **main** -Funktion.
