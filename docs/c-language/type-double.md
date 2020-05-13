---
title: Typ "double"
ms.date: 11/04/2016
helpviewer_keywords:
- mantissas, floating-point variables
- type double
- portability [C++], type double
- double data type
ms.assetid: 17c85b24-1475-4d41-a03c-ddf2d6561d34
ms.openlocfilehash: 43e6cc444f4d6a973fc58b5ce550e468066aca1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290731"
---
# <a name="type-double"></a>Typ "double"

Werte mit doppelter Genauigkeit und doppeltem Typ besitzen 8 Bytes. Das Format ist ähnlich wie das Gleitkommaformat, außer dass es einen 11-Bit-Exponenten in Excess-1023-Notation und eine 52-Bit-Mantisse sowie das implizite höchstwertige 1 Bit hat. Dieses Format erlaubt einen Bereich von etwa 1.7E-308 bis 1.7E+308 für den Typ „double“.

**Microsoft-spezifisch**

Der Typ „double“ enthält 64 Bit: 1 für das Vorzeichen, 11 für den Exponenten und 52 für die Mantisse. Sein Bereich ist +/-1.7E308 mit mindestens 15 Dezimalstellen.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Speicherung von einfachen Typen](../c-language/storage-of-basic-types.md)
