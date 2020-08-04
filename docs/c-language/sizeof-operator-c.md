---
title: sizeof-Operator (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 1d06fc8b541cbce3771a485c8f71953be8f7d552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229518"
---
# <a name="sizeof-operator-c"></a>sizeof-Operator (C)

Der **`sizeof`** -Operator gibt die Größe des Speichers in Bytes an, die erforderlich ist, um ein Objekt dieses Operandentyps zu speichern. Mithilfe dieses Operators können Sie es vermeiden, rechnerabhängige Datengrößen in Ihren Programmen anzugeben.

## <a name="syntax"></a>Syntax

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>Hinweise

Der Operand ist entweder ein Bezeichner, bei dem es sich um einen *unären Ausdruck* (unary-expression) handelt, oder ein Typumwandlungsausdruck (d.h. ein Typspezifizierer in Klammern). *unary-expression* kann kein Bitfeldobjekt, keinen unvollständigen Typ und keinen Funktionskennzeichner darstellen. Das Ergebnis ist eine vorzeichenlose Ganzzahlkonstante. Der Standardheader STDDEF.H definiert diesen Typ als **size_t**.

Wenn Sie den Operator **`sizeof`** auf einen Arraybezeichner anwenden, stellt das Ergebnis die Größe des gesamten Arrays und nicht nur die Größe des Zeigers dar, der vom Arraybezeichner dargestellt wird.

Wenn Sie den Operator **`sizeof`** auf den Namen eines Struktur- oder Union-Typs oder auf den Bezeichner eines Struktur- oder Union-Typs anwenden, stellt das Ergebnis die Anzahl von Bytes in der Struktur oder Union einschließlich interner und nachfolgender Füllzeichen dar. Diese Größe enthält möglicherweise interne und nachfolgende Füllzeichen, die verwendet werden, um die Member der Struktur oder Union an Arbeitsspeichergrenzen auszurichten. Daher stimmt das Ergebnis möglicherweise nicht mit der Größe überein, die durch Addieren der Speicheranforderungen der einzelnen Member berechnet wird.

Wenn ein Array ohne Größenangabe das letzte Element einer Struktur ist, gibt der **`sizeof`** -Operator die Größe der Struktur ohne das Array zurück.

```
buffer = calloc(100, sizeof (int) );
```

Dieses Beispiel verwendet den **`sizeof`** -Operator, um die Größe eines **`int`** -Elements (die computerspezifisch ist) als Argument an eine Laufzeitfunktion mit dem Namen `calloc` zu übergeben. Der Wert, der von dieser Funktion zurückgegeben wird, wird in `buffer` gespeichert.

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

In diesem Beispiel ist `strings` ein Array von Zeigern auf **`char`** . Die Anzahl von Zeigern ist die Anzahl von Elementen im Array, ist jedoch nicht festgelegt. Die Anzahl von Zeigern lässt sich ganz einfach ermitteln, indem mithilfe des **`sizeof`** -Operators die Anzahl von Elementen im Array berechnet wird. Der ganzzahlige **`const`** -Wert `string_no` wird mit dieser Zahl initialisiert. Da es sich um einen **`const`** -Wert handelt, kann `string_no` nicht geändert werden.

## <a name="see-also"></a>Siehe auch

[C-Operatoren](c-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
