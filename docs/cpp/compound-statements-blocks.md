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
ms.openlocfilehash: 60d7e88c5ccccac5a1d967a91c8a82dd954d9afc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337344"
---
# <a name="compound-statements-blocks"></a>Verbundanweisungen (Blöcke)

Eine zusammengesetzte Anweisung besteht aus null oder mehr Anweisungen, die in geschweifte Klammern eingeschlossen sind **.** Einer Verbundanweisung kann an einer jeder beliebigen Stelle, an der eine Anweisung erwartet wird. Verbundanweisungen werden im Allgemeinen "Blöcke" genannt.

## <a name="syntax"></a>Syntax

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Bemerkungen

Im folgenden Beispiel wird eine zusammengesetzte Anweisung als *Anweisungsteil* der **if-Anweisung** verwendet (details details zur Syntax finden Sie unter [Die if-Anweisung):](../cpp/if-else-statement-cpp.md)

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
> Da eine Deklaration eine Anweisung ist, kann eine Deklaration eine der Anweisungen in der *Anweisungsliste*sein. Folglich verfügen Namen, die innerhalb einer Verbundanweisung deklariert werden, jedoch nicht explizit als statisch deklariert werden, über einen lokalen Gültigkeitsbereich und eine lokale Lebensdauer (für Objekte). Weitere Informationen zur Behandlung von Namen mit lokalem Bereich finden Sie unter [Bereich.](../cpp/scope-visual-cpp.md)

## <a name="see-also"></a>Siehe auch

[Übersicht über C++-Anweisungen](../cpp/overview-of-cpp-statements.md)
