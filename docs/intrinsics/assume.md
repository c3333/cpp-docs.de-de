---
title: __assume
ms.date: 09/02/2019
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: 06189405703a7cc34f3bd807ec79612394ee899f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368196"
---
# <a name="__assume"></a>__assume

**Microsoft Specific**

Übergibt einen Hinweis an den Optimierer.

## <a name="syntax"></a>Syntax

```C
__assume(
   expression
)
```

### <a name="parameters"></a>Parameter

*Ausdruck*\
Ein beliebiger Ausdruck, von dem angenommen wird, dass er "true" ergibt.

## <a name="remarks"></a>Bemerkungen

Der Optimierer geht davon aus, dass die durch `expression` dargestellte Bedingung zu dem Zeitpunkt "true" ist, zu dem das Schlüsselwort angezeigt wird, und "true" bleibt, bis `expression` geändert wird (z. B. durch die Zuweisung zu einer Variablen). Durch die selektive Verwendung von Hinweisen, die von `__assume` an den Optimierer übergeben werden, kann die Optimierung verbessert werden.

Wenn die `__assume`-Anweisung als Widerspruch geschrieben wurde (ein Ausdruck, der immer in "false" ausgewertet wird), wird diese immer als `__assume(0)` behandelt. Wenn der Code sich nicht wie erwartet verhält, stellen Sie, wie zuvor beschrieben, sicher, dass der von Ihnen definierte `expression` gültig ist und stimmt. Weitere Informationen zum erwarteten Verhalten von `__assume(0)` finden Sie weiter unten in den Hinweisen.

> [!WARNING]
> Ein Programm darf keine ungültige `__assume`-Anweisung an einem erreichbaren Pfad enthalten. Wenn der Compiler eine ungültige `__assume`-Anweisung erreichen kann, kann das Programm möglicherweise ein unvorhersehbares und möglicherweise gefährliches Verhalten verursachen.

`__assume` ist keine echte systeminterne Funktion. Sie muss nicht als Funktion deklariert werden und kann nicht in einer `#pragma intrinsic`-Anweisung verwendet werden. Es wird zwar kein Code generiert, der vom Optimierer generierte Code ist jedoch davon betroffen.

Verwenden `__assume` Sie in einem [ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) nur, wenn die Assertion nicht wiederhergestellt werden kann. Verwenden Sie `__assume` nicht in einer Assert-Anweisung, für die Sie über den folgenden Fehlerwiederherstellungscode verfügen, da der Compiler den Fehlerbehebungscode aus Optimierungsgründen möglicherweise löscht.

Die `__assume(0)`-Anweisung ist ein Sonderfall. Verwenden Sie `__assume(0)`, um einen Codepfad anzugeben, der nicht erreicht werden kann. Im folgenden Beispiel wird veranschaulicht, wie `__assume(0)` verwendet wird, um anzugeben, dass der Standardfall einer Switch-Anweisung nicht erreicht werden kann. Dies zeigt die typische Verwendung von `__assume(0)`.

Aus Kompatibilität mit früheren Versionen ist **_assume** ein Synonym für **__assume** es sei denn, die Compileroption [/Za \(Disable language extensions)](../build/reference/za-ze-disable-language-extensions.md) wird angegeben.

## <a name="requirements"></a>Anforderungen

|Intrinsic|Aufbau|
|---------------|------------------|
|`__assume`|x86, ARM, x64, ARM64|

## <a name="example"></a>Beispiel

```cpp
// compiler_intrinsics__assume.cpp
#ifdef DEBUG
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )
#else
# define ASSERT(e)    ( __assume(e) )
#endif

void func1(int i)
{
}

int main(int p)
{
   switch(p){
      case 1:
         func1(1);
         break;
      case 2:
         func1(-1);
         break;
      default:
         __assume(0);
            // This tells the optimizer that the default
            // cannot be reached. As so, it does not have to generate
            // the extra code to check that 'p' has a value
            // not represented by a case arm. This makes the switch
            // run faster.
   }
}
```

Die Verwendung von `__assume(0)` teilt dem Optimierer mit, dass der Standardfall erreicht werden kann. Das Beispiel veranschaulicht, dass der Programmierer weiß, dass die einzig möglichen Eingaben für `p` 1 oder 2 lauten. Wenn ein anderer Wert für `p` übergeben wird, wird das Programm ungültig und führt zu unvorhersehbarem Verhalten.

Als Ergebnis der `__assume(0)`-Anweisung, generiert der Compiler keinen Code, um zu testen, ob `p` einen Wert hat, der nicht in einer Case-Anweisung dargestellt werden kann. Damit dies funktioniert, muss die `__assume(0)`-Anweisung die erste Anweisung im Hauptteil des Standardfalls sein.

Da der Compiler Code auf der Grundlage von `__assume` generiert, wird dieser Code möglicherweise nicht ordnungsgemäß ausgeführt, wenn der Ausdruck innerhalb der `__assume`-Anweisung zur Laufzeit "false" ist. Wenn Sie nicht sicher sind, dass der Ausdruck zur Laufzeit immer "true" ist, können Sie die `assert`-Funktion verwenden, um den Code zu schützen.

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

Leider wird durch diese Verwendung von `assert` verhindert, dass der Compiler die Standardfalloptimierung durchführt, die zuvor in diesem Dokument beschrieben wurde. Als Alternative können Sie wie folgt ein separates Makro verwenden.

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[Compiler-Intrinsics](../intrinsics/compiler-intrinsics.md)\
[Keywords](../cpp/keywords-cpp.md)
