---
title: Referenz für MASM-Operatoren
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: db79473f5d4264b869eeac334fa7957cfe553364
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88830942"
---
# <a name="masm-operators-reference"></a>Referenz für MASM-Operatoren

## <a name="arithmetic"></a>Arithmetik

:::row:::
   :::column span="":::
      [`*` lik](operator-multiply.md)\
      [`+` eren](operator-add.md)\
      [`-` (subtrahieren oder negieren)](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.` Flächen](operator-dot.md)\
      [`/` glie](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]` Sin](operator-brackets.md)\
      [`MOD` ergibt](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>Ablaufsteuerung

:::row:::
   :::column span="":::
      [`!` (logische Laufzeit nicht)](operator-logical-not-masm-run-time.md)\
      [`!=` (Laufzeit nicht gleich)](operator-not-equal-masm.md)\
      [`||` (logischer Lauf Zeit Modul oder)](operator-logical-or.md)\
      [`&&` (logisches Lauf Zeit Modul und)](operator-logical-and-masm-run-time.md)\
      [`<` (Laufzeit kleiner als)](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=` (Laufzeit ist kleiner oder gleich)](operator-less-or-equal-masm-run-time.md)\
      [`==` (Laufzeit gleich)](operator-equal-masm-run-time.md)\
      [`>` (Laufzeit größer als)](operator-greater-than-masm-run-time.md)\
      [`>=` (Laufzeit größer oder gleich)](operator-greater-or-equal-masm-run-time.md)\
      [`&` (Bitweises and-Lauf Zeit Modul)](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?` (Lauf Zeit Test ausführen)](operator-carry-q.md)\
      [`OVERFLOW?` (Lauf Zeit Überlauf Test)](operator-overflow-q.md)\
      [`PARITY?` (Lauf Zeit Paritäts Test)](operator-parity-q.md)\
      [`SIGN?` (Lauf Zeit Signatur-Test)](operator-sign-q.md)\
      [`ZERO?` (Lauf Zeit Zero-Test)](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>Logisches und Shift

:::row:::
   :::column span="":::
      [`AND` (Bitweises and)](operator-and.md)\
      [`NOT` (Bitweises NOT)](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR` (Bitweises OR)](operator-or.md)\
      [`SHL` (UMSCHALT Bits nach links)](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR` (UMSCHALT Bits rechts)](operator-shr.md)\
      [`XOR` (Bitweises exklusives OR)](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>Makro

:::row:::
   :::column span="":::
      [`!` (Zeichenliteral)](operator-logical-not-masm.md)\
      [`%` (als Text behandeln)](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;` (als Kommentar behandeln)](operator-semicolons.md)\
      [`< >` (als ein Literalformat behandeln)](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &` (Parameterwert ersetzen)](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>Verschiedenes

:::row:::
   :::column span="":::
      [`' '` (als Zeichenfolge behandeln)](operator-single-quote.md)\
      [`" "` (als Zeichenfolge behandeln)](operator-double-quote.md)\
      `:` (Definition der lokalen Bezeichnung)
   :::column-end:::
   :::column span="":::
      `::` (Segment und Offset registrieren) \
      `::` (Definition der globalen Bezeichnung)
   :::column-end:::
   :::column span="":::
      [`;` (als Kommentar behandeln)](operator-semicolon.md)\
      [`DUP` (Wiederholungs Deklaration)](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Datensatz

:::row:::
   :::column span="":::
      [`MASK` (Aufzeichnen der Datensatz-oder Feld-Bitmaske)](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH` (Datensatz-oder Feldbreite erhalten)](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>Relational

:::row:::
   :::column span="":::
      [`EQ` hoch](operator-eq.md)\
      [`GE` (größer oder gleich)](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT` (größer als)](operator-gt.md)\
      [`LE` (kleiner oder gleich)](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT` (kleiner als)](operator-lt.md)\
      [`NE` (ungleich)](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`:` (Segment Überschreibung)](operator-colon.md)\
      `::` (Segment und Offset registrieren) \
      [`IMAGEREL` (relativer Bild Offset)](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET` (Offset des Lade Moduls)](operator-lroffset.md)\
      [`OFFSET` (relativer Segment Verhältnis)](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL` (relativer Abschnitt relativer Offset)](operator-sectionrel.md)\
      [`SEG` (Segment erhalten)](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>type

:::row:::
   :::column span="":::
      [`HIGH` (hohe 8 Bits der niedrigsten 16 Bits)](operator-high.md)\
      [`HIGH32` (hohe 32 Bits von 64 Bits)](operator-high32.md)\
      [`HIGHWORD` (hohe 16 Bits der niedrigsten 32 Bits)](operator-highword.md)\
      [`LENGTH` (Anzahl von Elementen im Array)](operator-length.md)\
      [`LENGTHOF` (Anzahl von Elementen im Array)](operator-lengthof.md)\
      [`LOW` (niedrige 8 Bits)](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32` (niedrige 32 Bits)](operator-low32.md)\
      [`LOWWORD` (niedrige 16 Bits)](operator-lowword.md)\
      [`OPATTR` (Informationen zum Argumenttyp "Get")](operator-opattr.md)\
      [`PTR` (Zeiger auf oder als Typ)](operator-ptr.md)\
      [`SHORT` (kurzbezeichnungstyp markieren)](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE` (Größe des Typs oder der Variablen)](operator-size.md)\
      [`SIZEOF` (Größe des Typs oder der Variablen)](operator-sizeof.md)\
      [`THIS` (Aktueller Speicherort)](operator-this.md)\
      [`TYPE` (Ausdruckstyp "Ausdruck")](operator-type.md)\
      [`.TYPE` (Informationen zum Argumenttyp "Get")](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen

[Microsoft Macro Assembler-Referenz](microsoft-macro-assembler-reference.md)\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
