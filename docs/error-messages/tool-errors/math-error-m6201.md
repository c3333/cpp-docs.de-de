---
title: Mathematischer Fehler M6201
ms.date: 11/04/2016
f1_keywords:
- M6201
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
ms.openlocfilehash: 0b1cd0d3fcd86a2174b19da41176dd97f547a295
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193705"
---
# <a name="math-error-m6201"></a>Mathematischer Fehler M6201

"Function": _DOMAIN Fehler

Ein Argument für die angegebene Funktion befand sich außerhalb der Domäne der zulässigen Eingabewerte für diese Funktion.

## <a name="example"></a>Beispiel

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Dieser Fehler Ruft die `_matherr`-Funktion mit dem Funktionsnamen, den Argumenten und dem Fehlertyp auf. Sie können die `_matherr`-Funktion umschreiben, um die Behandlung bestimmter Fehler in der Lauf Zeit-Gleit Komma Zeit anzupassen.
