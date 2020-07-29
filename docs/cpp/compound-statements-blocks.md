---
title: Verbundanweisungen (Blöcke)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: a06a3d9ce887150ba3333e8e9e874ab337f8b4df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221808"
---
# <a name="compound-statements-blocks"></a>Verbundanweisungen (Blöcke)

Eine Verbund Anweisung besteht aus null oder mehr Anweisungen, die in geschweiften Klammern (**{}**) eingeschlossen sind. Einer Verbundanweisung kann an einer jeder beliebigen Stelle, an der eine Anweisung erwartet wird. Verbundanweisungen werden im Allgemeinen "Blöcke" genannt.

## <a name="syntax"></a>Syntax

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Bemerkungen

Im folgenden Beispiel wird eine Verbund Anweisung als *Anweisungs* Teil der- **`if`** Anweisung verwendet (Weitere Informationen zur Syntax finden Sie in [der if-Anweisung](../cpp/if-else-statement-cpp.md) ):

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
> Da eine Deklaration eine-Anweisung ist, kann eine Deklaration eine der-Anweisungen in der *-Anweisungs Liste*sein. Folglich verfügen Namen, die innerhalb einer Verbundanweisung deklariert werden, jedoch nicht explizit als statisch deklariert werden, über einen lokalen Gültigkeitsbereich und eine lokale Lebensdauer (für Objekte). Ausführliche Informationen zur Behandlung von Namen mit lokalem Gültigkeitsbereich finden Sie im [Bereich](../cpp/scope-visual-cpp.md) .

## <a name="see-also"></a>Weitere Informationen

[Übersicht über C++-Anweisungen](../cpp/overview-of-cpp-statements.md)
