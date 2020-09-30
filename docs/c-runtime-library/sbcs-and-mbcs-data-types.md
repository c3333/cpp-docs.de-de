---
title: SBCS- und MBCS-Datentypen
description: Darstellung von Einzel-und Multibytezeichen in der Microsoft C-Laufzeit.
ms.topic: conceptual
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 27d32ffd079cdc82ab8a799df9d9ec778b546a3b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590250"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS- und MBCS-Datentypen

Jede Microsoft MBCS-Lauf Zeit Bibliotheks Routine, die nur ein Multibytezeichen oder 1 Byte eines multibytezeichens verarbeitet, erwartet ein **`unsigned int`** Argument (wobei 0x00 <= Zeichen Wert <= 0xFFFF und 0x00 <= Bytewert <= 0xFF). Eine MBCS-Routine, die Multibytezeichen-Bytes oder-Zeichen in einem Zeichen folgen Kontext verarbeitet, erwartet, dass eine Multibytezeichenfolge als Zeiger dargestellt wird **`unsigned char`** .

> [!CAUTION]
> Jedes Byte eines multibytezeichens kann in einem 8-Bit-Zeichen dargestellt werden **`char`** . Allerdings ist ein SBCS-oder MBCS-Einzel Byte Zeichen vom Typ **`char`** mit einem Wert größer als 0x7F negativ. Wenn ein solches Zeichen direkt in ein **`int`** oder ein konvertiert wird **`long`** , wird das Ergebnis vom Compiler mit Vorzeichen erweitert und kann daher unerwartete Ergebnisse liefern.

Es empfiehlt sich, ein Byte eines multibytezeichens als 8-Bit-Zeichen darzustellen **`unsigned char`** . Wenn Sie ein negatives Ergebnis vermeiden möchten, konvertieren Sie ein Einzel Byte Zeichen vom Typ **`char`** in ein-Zeichen, **`unsigned char`** bevor Sie es in ein **`int`** oder eine konvertieren **`long`** .

Da einige Funktionen zur Verarbeitung von SBCS-Zeichen folgen Parameter (signiert) akzeptieren **`char`** <strong>\*</strong> , wird eine Compilerwarnung des Typs nicht übereinstimmen, wenn **_MBCS** definiert wird. Es gibt drei Möglichkeiten, diese Warnung zu vermeiden, die in der Reihenfolge ihrer Effizienz aufgeführt werden:

1. Verwenden Sie die typsicheren Inlinefunktionen in TCHAR.H. Dies ist das Standardverhalten.

1. Verwenden Sie die direkten Makros in TCHAR.H, indem Sie **_MB_MAP_DIRECT** in der Befehlszeile definieren. In diesem Fall müssen Sie die Typübereinstimmung manuell sicherstellen. Dies ist die schnellste Methode, jedoch nicht typsicher.

1. Verwenden Sie die typsicheren statisch verknüpften Bibliotheksfunktionen in TCHAR.H. Definieren Sie hierzu in der Befehlszeile die Konstante **_NO_INLINING**. Dies ist die langsamste Methode; sie bietet jedoch auch die größte Typsicherheit.

## <a name="see-also"></a>Weitere Informationen

[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
