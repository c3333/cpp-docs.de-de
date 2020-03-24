---
title: Compilerfehler C3888
ms.date: 11/04/2016
f1_keywords:
- C3888
helpviewer_keywords:
- C3888
ms.assetid: 40820812-79c5-4dcd-a19d-b4164d25fc8a
ms.openlocfilehash: 40156dfaad5965d30a32d3aa2ac574a5f91999ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176403"
---
# <a name="compiler-error-c3888"></a>Compilerfehler C3888

"name": Der diesem literal-Datenmember zugeordnete Konstantenausdruck wird von C++/CLI nicht unterstützt

Das *name* -Datenmember, das mit dem [literal](../../extensions/literal-cpp-component-extensions.md) -Schlüsselwort deklariert wird, wird mit einem Wert initialisiert, der vom Compiler nicht unterstützt wird. Der Compiler unterstützt nur konstante integrale, Enumerations- oder Zeichenfolgentypen. Der Fehler **C3888** wurde wahrscheinlich dadurch verursacht, dass das Datenmember mit einem Bytearray initialisiert wird.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Vergewissern Sie sich, dass das deklarierte literal-Datenmember ein unterstützter Typ ist.

## <a name="see-also"></a>Weitere Informationen

[literal](../../extensions/literal-cpp-component-extensions.md)
