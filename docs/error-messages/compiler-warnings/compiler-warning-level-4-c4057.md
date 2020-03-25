---
title: Compilerwarnung (Stufe 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 45d2db56a7b0fc871de60743954012faf0f5c366
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185385"
---
# <a name="compiler-warning-level-4-c4057"></a>Compilerwarnung (Stufe 4) C4057

'Operator': 'Bezeichner1' Dereferenzierung in leicht unterschiedliche Basistypen von 'Bezeichner2'

Zwei Zeigerausdrücke verweisen auf unterschiedliche Basistypen. Die Ausdrücke werden ohne Konvertierung verwendet.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Typen mit und ohne Vorzeichen werden gemischt verwendet.

1. **short** - und **long** -Typen werden gemischt verwendet.
