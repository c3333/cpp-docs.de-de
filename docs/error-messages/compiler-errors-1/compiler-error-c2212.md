---
title: Compilerfehler C2212
ms.date: 11/04/2016
f1_keywords:
- C2212
helpviewer_keywords:
- C2212
ms.assetid: 3fdab304-272c-4d07-bfd4-fad75170e536
ms.openlocfilehash: c243925548f8c90bdff49421b0d38357b9e677a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216283"
---
# <a name="compiler-error-c2212"></a>Compilerfehler C2212

"Bezeichner": __based für Zeiger auf Funktionen nicht verfügbar.

Zeiger auf Funktionen können nicht deklariert werden **`__based`** . Wenn Sie Code basierte Daten benötigen, verwenden Sie das- **`__declspec`** Schlüsselwort oder das- `data_seg` pragma.
