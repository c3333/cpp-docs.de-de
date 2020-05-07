---
title: Unterlauf von Gleitkommawerten
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: 93230b50b81ede44a9c55406db1566df2660c1ba
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344064"
---
# <a name="underflow-of-floating-point-values"></a>Unterlauf von Gleitkommawerten

**ANSI 4.5.1** Ob die mathematischen Funktionen den ganzzahligen Ausdruck `errno` bei Unterlaufbereichsfehlern auf den Wert des `ERANGE`-Makros festlegen

Ein Gleitkommaunterlauf legt den Ausdruck `errno` nicht auf `ERANGE` fest. Wenn ein Wert nahe 0 (Null) ist und schließlich ein Unterlauf stattfindet, wird der Wert auf 0 (Null) festgelegt.

## <a name="see-also"></a>Siehe auch

[Bibliotheksfunktionen](../c-language/library-functions.md)
