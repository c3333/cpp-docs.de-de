---
title: C-Verbundzuweisung
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], assignment
- compound assignment operators
- assignment operators, compound
ms.assetid: db7b5893-cd56-4f1c-9981-5a024200ab63
ms.openlocfilehash: 39a9391e2a62a59c5e7fd7937c1f3d12509b76ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327898"
---
# <a name="c-compound-assignment"></a>C-Verbundzuweisung

Die Verbundzuweisungsoperatoren kombinieren den Einfachzuweisungsoperator mit einem anderen binären Operator. Verbundzuweisungsoperatoren führen einen Vorgang aus, der vom zusätzlichen Operator angegeben wurde, und weisen das Ergebnis dann dem linken Operanden zu. Zum Beispiel kann ein Verbundzuweisungsausdruck wie

> *Ausdruck1* **+=** *Ausdruck2*

verstanden werden als

> *Ausdruck1* **=** *Ausdruck1* **+** *Ausdruck2*

Allerdings ist der Verbundzuweisungsausdruck nicht mit der erweiterten Version äquivalent, da der Verbundzuweisungsausdruck *expression1* nur einmal auswertet, während die erweiterte Version *expression1* zweimal auswertet: in der Additions- und in der Zuweisungsoperation.

Die Operanden des Verbundzuweisungsoperators müssen vom Typ „Ganzzahl“ oder „Gleitkomma“ sein. Jeder Verbundzuweisungsoperator führt die Konvertierungen aus, die der entsprechende binäre Operator ausführt, und schränkt die Typen seiner Operanden entsprechend ein. Die Operatoren für die Additionszuweisung (`+=`) und die Subtraktionszuweisung ( **-=** ) können über einen linken Operanden vom Zeigertyp verfügen. In diesem Fall muss der rechte Operand integralen Typs sein. Das Ergebnis eines Verbundzuweisungsvorgangs hat den Wert und Typ des linken Operanden.

```C
#define MASK 0xff00

n &= MASK;
```

In diesem Beispiel wird ein bitweiser inklusiver AND-Vorgang für `n` und `MASK` ausgeführt, und das Ergebnis wird `n` zugewiesen. Die Manifestkonstante `MASK` wird mit einer [#define](../preprocessor/hash-define-directive-c-cpp.md)-Präprozessoranweisung definiert.

## <a name="see-also"></a>Siehe auch

[C-Zuweisungsoperatoren](../c-language/c-assignment-operators.md)
