---
title: Compilerwarnung (Stufe 2) C4653
ms.date: 11/04/2016
f1_keywords:
- C4653
helpviewer_keywords:
- C4653
ms.assetid: 90ec3317-3d39-4b4c-bcd1-97e7c799e1b6
ms.openlocfilehash: 994e9a4963e7e10af2313b3dcea5bb8b2b93426e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161736"
---
# <a name="compiler-warning-level-2-c4653"></a>Compilerwarnung (Stufe 2) C4653

die Compileroption "Option" ist inkonsistent mit dem vorkompilierten Header aktuelle Befehlszeilenoption wird ignoriert.

Eine Option, die mit der Option Vorkompilierte Header verwenden ([/Yu](../../build/reference/yu-use-precompiled-header-file.md)) angegeben wurde, war nicht mit den Optionen konsistent, die beim Erstellen des vorkompilierten Headers angegeben wurden. Bei dieser Kompilierung wurde die Option verwendet, die beim Erstellen des vorkompilierten Headers angegeben wurde.

Diese Warnung kann auftreten, wenn während der Kompilierung des vorkompilierten Headers ein anderer Wert für die Option Paket Strukturen ([/ZP](../../build/reference/zp-struct-member-alignment.md)) angegeben wurde.
