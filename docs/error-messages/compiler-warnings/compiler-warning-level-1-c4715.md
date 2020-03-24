---
title: Compilerwarnung (Stufe 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 7dba86d591f18fd7c9c562078204916000d47384
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175323"
---
# <a name="compiler-warning-level-1-c4715"></a>Compilerwarnung (Stufe 1) C4715

"Function": nicht alle Steuerelement Pfade geben einen Wert zurück.

Die angegebene Funktion kann möglicherweise keinen Wert zurückgeben.

## <a name="example"></a>Beispiel

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

Um diese Warnung zu vermeiden, ändern Sie den Code so, dass alle Pfade der Funktion einen Rückgabewert zuweisen:

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

Es ist möglich, dass Ihr Code einen aufzurufenden Vorgang enthält, wie im folgenden Beispiel gezeigt:

```cpp
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

Dieser Code generiert auch eine Warnung, da der Compiler nicht weiß, dass `fatal` nie zurückgibt. Um zu verhindern, dass dieser Code eine Fehlermeldung erzeugt, deklarieren Sie `fatal` mithilfe [__declspec (noreturn)](../../cpp/noreturn.md).
