---
title: Linkertoolwarnung LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183357"
---
# <a name="linker-tools-warning-lnk4092"></a>Linkertoolwarnung LNK4092

der freigegebene beschreibbare Abschnitt "section" enthält Umsetzungen; Image wird möglicherweise nicht ordnungsgemäß ausgeführt

Der Linker gibt diese Warnung aus, wenn Sie über einen freigegebenen Abschnitt verfügen, um Sie vor einem potenziell ernsten Problem zu warnen.

Eine Möglichkeit zum Freigeben von Daten zwischen mehreren Prozessen besteht darin, einen Abschnitt als "Shared" zu markieren. Das Markieren eines Abschnitts als freigegeben kann jedoch Probleme verursachen. Beispielsweise haben Sie eine DLL, die Deklarationen wie diese in einem freigegebenen Daten Abschnitt enthält:

```
int var = 1;
int *pvar = &var;
```

Der Linker kann `pvar` nicht auflösen, da sein Wert davon abhängt, wo die dll in den Arbeitsspeicher geladen wird, sodass ein Verschiebungs Daten Satz in die DLL eingefügt wird. Wenn die dll in den Arbeitsspeicher geladen wird, kann die Adresse `var` aufgelöst und `pvar` zugewiesen werden. Wenn die gleiche dll von einem anderen Prozess geladen, aber nicht mit derselben Adresse geladen werden kann, wird die Verschiebung für die Adresse von `var` für den zweiten Prozess aktualisiert, und der Adressbereich des ersten Prozesses verweist auf die falsche Adresse.
