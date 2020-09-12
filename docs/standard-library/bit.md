---
title: '&lt;bit&gt;'
description: Funktionen für den Zugriff auf, die Bearbeitung und Verarbeitung einzelner Bits und Sequenzen von Bits.
ms.date: 08/28/2020
f1_keywords:
- <bit>
helpviewer_keywords:
- bit header
ms.openlocfilehash: 5652d0af767520710ee08b1827e0df27c477ee6d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040053"
---
# <a name="ltbitgt"></a>&lt;bit&gt;

Definiert Funktionen für den Zugriff auf, die Bearbeitung und Verarbeitung einzelner Bits und Sequenzen von Bits.

Beispielsweise gibt es Funktionen zum Rotieren von Bits, zum Ermitteln der Anzahl von aufeinander folgenden oder gelöschten Bits. Informationen dazu, ob eine Zahl eine ganzzahlige Potenz von zwei ist, die kleinste Anzahl von Bits zum Darstellen einer Zahl finden usw.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<bit>

**Namespace:** std

[/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md) ist erforderlich.

## <a name="members"></a>Member

### <a name="types"></a>Typen

| Typ | BESCHREIBUNG |
|--------|----------|
| [Endian](bit-enum.md) | Gibt die enumeralität von skalaren Typen an. |

### <a name="functions"></a>Functions

| Funktion | BESCHREIBUNG |
|-----|-----|
|[bit_cast](bit-functions.md#bit_cast) | Interpretiert die Objektdarstellung von einem Typ in einen anderen. |
|[bit_ceil](bit-functions.md#bit_ceil) | Ermittelt die kleinste Potenz von zwei größer als oder gleich einem Wert. |
|[bit_floor](bit-functions.md#bit_floor) | Suchen Sie die größte ganzzahlige Potenz von zwei, die nicht größer als ein Wert ist. |
|[bit_width](bit-functions.md#bit_width) | Suchen Sie die kleinste Anzahl von Bits, die für die Darstellung eines Werts benötigt werden. |
|[countl_zero](bit-functions.md#countl_zero) | Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf NULL festgelegt sind, beginnend mit dem signifikantesten Bit. |
|[countl_one](bit-functions.md#countl_one) | Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf 1 festgelegt sind, beginnend mit dem signifikantesten Bit. |
|[countr_zero](bit-functions.md#countr_zero) | Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf 0 (null) festgelegt sind, beginnend mit dem geringsten Bit |
|[countr_one](bit-functions.md#countl_one) | Zählen Sie die Anzahl aufeinander folgender Bits, die auf 1 festgelegt sind, beginnend mit dem am wenigsten bedeutenden Bit. |
|[has_single_bit](bit-functions.md#has_single_bit) | Überprüfen Sie, ob für einen Wert nur ein einzelnes Bit auf 1 festgelegt ist. Dies entspricht dem Testen, ob ein Wert eine Potenz von zwei ist. |
|[popcount](bit-functions.md#popcount) | Zählen Sie die Anzahl der Bits, die auf 1 festgelegt sind. |
|[rotl](bit-functions.md#rotl) | Berechnen Sie das Ergebnis einer bitweisen linken Drehung. |
|[RotR](bit-functions.md#rotr) | Berechnen Sie das Ergebnis einer bitweisen Rechtsdrehung. |

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](cpp-standard-library-header-files.md)