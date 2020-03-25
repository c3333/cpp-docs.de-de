---
title: Compilerfehler C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165582"
---
# <a name="compiler-error-c3851"></a>Compilerfehler C3851

> "*char*": ein universeller Zeichen Name darf kein Zeichen im Basis Zeichensatz bezeichnen.

## <a name="remarks"></a>Bemerkungen

Im als C++ kompilierten Code können Sie keinen universellen Zeichennamen verwenden, der ein Zeichen des einfachen Quellzeichensatzes außerhalb einer Zeichenfolge oder eines Zeichenliterals darstellt. Weitere Informationen finden Sie unter [Character Sets](../../cpp/character-sets.md). In als C kompilierten Code können Sie keinen universellen Zeichennamen für Zeichen im Bereich 0x20-0x7F (einschließlich) verwenden, mit Ausnahme von 0x24 ("$"), 0x40 ("\@") oder 0x60 ("\`").

## <a name="example"></a>Beispiel

In den folgenden Beispielen wird C3851 generiert und anschließend gezeigt, wie dieses Problem behoben wird:

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
