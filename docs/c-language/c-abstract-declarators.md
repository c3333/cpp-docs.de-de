---
title: C-Deklaratoren (abstrakt)
ms.date: 11/04/2016
helpviewer_keywords:
- declarators, abstract
- abstract declarations
ms.assetid: 6a556ad7-0555-421a-aa02-294d77cda8b5
ms.openlocfilehash: 540b938e2c4121f189216942bc06630fc61ee19c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220859"
---
# <a name="c-abstract-declarators"></a>C-Deklaratoren (abstrakt)

Ein abstrakter Deklarator ist ein Deklarator ohne einen Bezeichner, der aus mindestens einem Zeiger-, Array- oder Funktionsmodifizierer besteht. Der Zeigermodifizierer (<strong>\*</strong>) steht immer vor dem Bezeichner in einem Deklarator. Modifizierer des Arrays ( **[ ]** ) und der Funktion ( **( )** ) folgen dem Bezeichner. Vor diesem Hintergrund können Sie ermitteln, wo der Bezeichner in einem abstrakten Deklarator stehen würde, und den Deklarator entsprechend interpretieren. Weitere Informationen und Beispiele für komplexe Deklaratoren erhalten Sie unter [Interpretieren von komplexeren Deklaratoren](../c-language/interpreting-more-complex-declarators.md). Im Allgemeinen kann **`typedef`** zum Vereinfachen von Deklaratoren verwendet werden. Weitere Informationen finden Sie unter [Typedef-Deklarationen](../c-language/typedef-declarations.md).

Abstrakte Deklaratoren können komplex sein. Klammern in einem komplexen abstrakten Deklarator geben eine bestimmte Interpretation an, so wie bei komplexen Deklaratoren in Deklarationen.

Diese Beispiele veranschaulichen abstrakte Deklaratoren:

```
int *         // The type name for a pointer to type int:

int *[3]      // An array of three pointers to int

int (*) [5]   // A pointer to an array of five int

int *()       // A function with no parameter specification
              // returning a pointer to int

// A pointer to a function taking no arguments and
// returning an int

int (*) ( void )

// An array of an unspecified number of constant pointers to
// functions each with one parameter that has type unsigned int
// and an unspecified number of other parameters returning an int

int (*const []) ( unsigned int, ... )
```

> [!NOTE]
> Der abstrakte Deklarator, der aus einem Satz von leeren Klammern, **( )** , besteht, ist nicht zulässig, da er nicht eindeutig ist. Es ist unmöglich zu ermitteln, ob der implizite Bezeichner in die Klammern (in diesem Fall ist dies ein unveränderter Typ) oder vor die Klammern gehört (in diesem Fall ist dies ein Funktionstyp).

## <a name="see-also"></a>Siehe auch

[Deklaratoren und Variablendeklarationen](../c-language/declarators-and-variable-declarations.md)
