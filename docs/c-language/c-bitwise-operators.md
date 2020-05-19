---
title: C-Operatoren zur Bitmanipulation
ms.date: 01/29/2018
helpviewer_keywords:
- '| operator, bitwise operators'
- bitwise operators, Visual C
- bitwise operators
- operators [C], bitwise
- ^ operator, bitwise operators
- AND operator
- ampersand operator (&)
- ^ operator
- '& operator, bitwise operators'
ms.assetid: e22127b1-9a2d-4876-b01d-c8f72cec3317
ms.openlocfilehash: 50be8ae38f21d0a9f46c180abf179e1358b707cd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168772"
---
# <a name="c-bitwise-operators"></a>C-Operatoren zur Bitmanipulation

Die bitweisen Operatoren führen bitweise AND ( **&** )-, bitweise exklusive OR ( **^** )- und bitweise inklusive OR( **&#124;** )-Operationen durch.

## <a name="syntax"></a>Syntax

*AND-Ausdruck*: &nbsp;&nbsp;*Gleichheitsausdruck* &nbsp;&nbsp;*AND-Ausdruck* **&** *Gleichheitsausdruck*

*exclusive-OR-expression*: &nbsp;&nbsp;*AND-Ausdruck* &nbsp;&nbsp;*exklusiver-OR-Ausdruck* **^** *AND-Ausdruck*

*inklusiver-OR-Ausdruck*: &nbsp;&nbsp;*exklusiver-OR-Ausdruck*&nbsp;&nbsp;*inklusiver-OR-Ausdruck* &#124; *exklusiver-OR-Ausdruck*

Die Operanden für bitweise Operatoren müssen Ganzzahltypen aufweisen, aber ihre Typen können unterschiedlich sein. Diese Operatoren führen die üblichen arithmetischen Konvertierungen aus. Der Typ des Ergebnisses ist der Typ der Operanden nach der Konvertierung.

Die bitweisen C-Operatoren sind im Folgenden beschrieben:

|Operator|Beschreibung|
|--------------|-----------------|
|**&**|Der bitweise AND-Operator vergleicht jedes Bit seines ersten Operanden mit dem entsprechenden Bit seines zweiten Operanden. Wenn beide Bits 1 sind, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 (null) festgelegt.|
|**^**|Der bitweise exklusive OR-Operator vergleicht jedes Bit seines ersten Operanden mit dem entsprechenden Bit seines zweiten Operanden. Wenn ein Bit 0 (null) und das andere Bit 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 (null) festgelegt.|
|**&#124;**|Der bitweise inklusive OR-Operator vergleicht jedes Bit seines ersten Operanden mit dem entsprechenden Bit seines zweiten Operanden. Wenn jedes Bit 1 ist, wird das entsprechende Ergebnisbit auf 1 festgelegt. Andernfalls wird das entsprechende Ergebnisbit auf 0 (null) festgelegt.|

## <a name="examples"></a>Beispiele

Diese Deklarationen werden für die folgenden drei Beispiele verwendet:

```C
short i = 0xAB00;
short j = 0xABCD;
short n;

n = i & j;
```

Das Ergebnis, das `n` in diesem ersten Beispiel zugewiesen wird, entspricht `i` (0xAB00 hexadezimal).

```C
n = i | j;

n = i ^ j;
```

Der bitweise inklusive OR-Operator im zweiten Beispiel ergibt den Wert 0xABCD (hexadezimal), während der bitweise exklusive OR-Operator im dritten Beispiel 0xCD (hexadezimal) zurückgibt.

**Microsoft-spezifisch**

Die Ergebnisse der bitweisen Operationen für ganze Zahlen mit Vorzeichen hängen gemäß ANSI C-Standard von der jeweiligen Implementierung ab. Für den Microsoft C-Compiler funktionieren bitweise Operationen für ganze Zahlen mit Vorzeichen genauso wie bitweise Operationen für ganze Zahlen ohne Vorzeichen. So kann beispielsweise `-16 & 99` binär ausgedrückt werden als

```Expression
  11111111 11110000
& 00000000 01100011
  _________________
  00000000 01100000
```

Das Ergebnis der bitweisen AND-Operation ist 96 dezimal.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Bitweiser AND-Operator (&)](../cpp/bitwise-and-operator-amp.md)<br/>
[Bitweiser exklusiver OR-Operator: ^](../cpp/bitwise-exclusive-or-operator-hat.md)<br/>
[Bitweiser inklusiver OR-Operator: &#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)
