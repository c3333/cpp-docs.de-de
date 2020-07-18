---
title: Referenz für MASM-Operatoren
ms.date: 07/15/2020
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c29b173a1dcf29c297e41f136044599fbd5218a5
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446462"
---
# <a name="masm-operators-reference"></a>Referenz für MASM-Operatoren

## <a name="arithmetic"></a>Arithmetik

:::row:::
   :::column span="":::
      [`*`lik](operator-multiply.md)<br/>[`+`eren](operator-add.md)<br/>[`-`(subtrahieren oder negieren)](operator-subtract-2.md)
   :::column-end:::
   :::column span="":::
      [`.`Flächen](operator-dot.md)<br/>[`/`glie](operator-subtract-1.md)
   :::column-end:::
   :::column span="":::
      [`[]`Sin](operator-brackets.md)<br/>[`MOD`ergibt](operator-mod.md)
   :::column-end:::
:::row-end:::

## <a name="control-flow"></a>Ablaufsteuerung

:::row:::
   :::column span="":::
      [`!`(logische Laufzeit nicht)](operator-logical-not-masm-run-time.md)<br/>[`!=`(Laufzeit nicht gleich)](operator-not-equal-masm.md)<br/>[`||`(logischer Lauf Zeit Modul oder)](operator-logical-or.md)<br/>[`&&`(logisches Lauf Zeit Modul und)](operator-logical-and-masm-run-time.md)<br/>[`<`(Laufzeit kleiner als)](operator-less-than-masm-run-time.md)
   :::column-end:::
   :::column span="":::
      [`<=`(Laufzeit ist kleiner oder gleich)](operator-less-or-equal-masm-run-time.md)<br/>[`==`(Laufzeit gleich)](operator-equal-masm-run-time.md)<br/>[`>`(Laufzeit größer als)](operator-greater-than-masm-run-time.md)<br/>[`>=`(Laufzeit größer oder gleich)](operator-greater-or-equal-masm-run-time.md)<br/>[`&`(Bitweises and-Lauf Zeit Modul)](operator-bitwise-and.md)
   :::column-end:::
   :::column span="":::
      [`CARRY?`(Lauf Zeit Test ausführen)](operator-carry-q.md)<br/>[`OVERFLOW?`(Lauf Zeit Überlauf Test)](operator-overflow-q.md)<br/>[`PARITY?`(Lauf Zeit Paritäts Test)](operator-parity-q.md)<br/>[`SIGN?`(Lauf Zeit Signatur-Test)](operator-sign-q.md)<br/>[`ZERO?`(Lauf Zeit Zero-Test)](operator-zero-q.md)
   :::column-end:::
:::row-end:::

## <a name="logical-and-shift"></a>Logisches und Shift

:::row:::
   :::column span="":::
      [`AND`(Bitweises and)](operator-and.md)<br/>[`NOT`(Bitweises NOT)](operator-not.md)
   :::column-end:::
   :::column span="":::
      [`OR`(Bitweises OR)](operator-or.md)<br/>[`SHL`(UMSCHALT Bits nach links)](operator-shl.md)
   :::column-end:::
   :::column span="":::
      [`SHR`(UMSCHALT Bits rechts)](operator-shr.md)<br/>[`XOR`(Bitweises exklusives OR)](operator-xor.md)
   :::column-end:::
:::row-end:::

## <a name="macro"></a>Makro

:::row:::
   :::column span="":::
      [`!`(Zeichenliteral)](operator-logical-not-masm.md)<br/>[`%`(als Text behandeln)](operator-percent.md)
   :::column-end:::
   :::column span="":::
      [`;;`(als Kommentar behandeln)](operator-semicolons.md)<br/>[`< >`(als ein Literalformat behandeln)](operator-literal.md)
   :::column-end:::
   :::column span="":::
      [`& &`(Parameterwert ersetzen)](operator-logical-and-masm.md)
   :::column-end:::
:::row-end:::

## <a name="miscellaneous"></a>Sonstiges

:::row:::
   :::column span="":::
      [`' '`(als Zeichenfolge behandeln)](operator-single-quote.md)<br/>[`" "`(als Zeichenfolge behandeln)](operator-double-quote.md)<br/>`:`(Definition der lokalen Bezeichnung)
   :::column-end:::
   :::column span="":::
      `::`(Segment und Offset registrieren)<br/>`::`(Definition der globalen Bezeichnung)
   :::column-end:::
   :::column span="":::
      [`;`(als Kommentar behandeln)](operator-semicolon.md)<br/>[`DUP`(Wiederholungs Deklaration)](operator-dup.md)
   :::column-end:::
:::row-end:::

## <a name="record"></a>Datensatz

:::row:::
   :::column span="":::
      [`MASK`(Aufzeichnen der Datensatz-oder Feld-Bitmaske)](operator-mask.md)
   :::column-end:::
   :::column span="2":::
      [`WIDTH`(Datensatz-oder Feldbreite erhalten)](operator-width.md)
   :::column-end:::
:::row-end:::

## <a name="relational"></a>Relational

:::row:::
   :::column span="":::
      [`EQ`hoch](operator-eq.md)<br/>[`GE`(größer oder gleich)](operator-ge.md)
   :::column-end:::
   :::column span="":::
      [`GT`(größer als)](operator-gt.md)<br/>[`LE`(kleiner oder gleich)](operator-le.md)
   :::column-end:::
   :::column span="":::
      [`LT`(kleiner als)](operator-lt.md)<br/>[`NE`(ungleich)](operator-ne.md)
   :::column-end:::
:::row-end:::

## <a name="segment"></a>Segment

:::row:::
   :::column span="":::
      [`:`(Segment Überschreibung)](operator-colon.md)<br/>`::`(Segment und Offset registrieren)<br/>[`IMAGEREL`(relativer Bild Offset)](operator-imagerel.md)
   :::column-end:::
   :::column span="":::
      [`LROFFSET`(Offset des Lade Moduls)](operator-lroffset.md)<br/>[`OFFSET`(relativer Segment Verhältnis)](operator-offset.md)
   :::column-end:::
   :::column span="":::
      [`SECTIONREL`(relativer Abschnitt relativer Offset)](operator-sectionrel.md)<br/>[`SEG`(Segment erhalten)](operator-seg.md)
   :::column-end:::
:::row-end:::

## <a name="type"></a>type

:::row:::
   :::column span="":::
      [`HIGH`(hohe 8 Bits der niedrigsten 16 Bits)](operator-high.md)<br/>[`HIGH32`(hohe 32 Bits von 64 Bits)](operator-high32.md)<br/>[`HIGHWORD`(hohe 16 Bits der niedrigsten 32 Bits)](operator-highword.md)<br/>[`LENGTH`(Anzahl von Elementen im Array)](operator-length.md)<br/>[`LENGTHOF`(Anzahl von Elementen im Array)](operator-lengthof.md)<br/>[`LOW`(niedrige 8 Bits)](operator-low.md)
   :::column-end:::
   :::column span="":::
      [`LOW32`(niedrige 32 Bits)](operator-low32.md)<br/>[`LOWWORD`(niedrige 16 Bits)](operator-lowword.md)<br/>[`OPATTR`(Informationen zum Argumenttyp "Get")](operator-opattr.md)<br/>[`PTR`(Zeiger auf oder als Typ)](operator-ptr.md)<br/>[`SHORT`(kurzbezeichnungstyp markieren)](operator-short.md)
   :::column-end:::
   :::column span="":::
      [`SIZE`(Größe des Typs oder der Variablen)](operator-size.md)<br/>[`SIZEOF`(Größe des Typs oder der Variablen)](operator-sizeof.md)<br/>[`THIS`(Aktueller Speicherort)](operator-this.md)<br/>[`TYPE`(Ausdruckstyp "Ausdruck")](operator-type.md)<br/>[`.TYPE`(Informationen zum Argumenttyp "Get")](operator-dot-type.md)
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Weitere Informationen

[Microsoft Macro Assembler-Referenz](microsoft-macro-assembler-reference.md)\
[MASM-BNF-Grammatik](masm-bnf-grammar.md)
