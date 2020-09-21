---
title: Compilerfehler C2001
ms.date: 11/04/2016
f1_keywords:
- C2001
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
ms.openlocfilehash: 6b40a3bd186b5c45a0ea5163f433635ab1e7b07f
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743489"
---
# <a name="compiler-error-c2001"></a>Compilerfehler C2001

Zeilen-Zeilen Ausdruck in konstanter Konstante

Eine Zeichen folgen Konstante kann in einer zweiten Zeile nur dann fortgesetzt werden, wenn Sie die folgenden Schritte ausführen:

- Beenden Sie die erste Zeile mit einem umgekehrten Schrägstrich.

- Schließen Sie die Zeichenfolge in der ersten Zeile mit einem doppelten Anführungszeichen, und öffnen Sie die Zeichenfolge in der nächsten Zeile mit einem weiteren doppelten Anführungszeichen.

Das Beenden der ersten Zeile mit \n ist nicht ausreichend.

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C2001 generiert:

```cpp
// C2001.cpp
// C2001 expected
#include <stdio.h>

int main()
{
    printf_s("Hello,
             world");
    printf_s("Hello,\n
             world");
}
```

Leerzeichen am Anfang der nächsten Zeile nach einem Zeilen Fortsetzungs Zeichen sind in der Zeichen folgen Konstante enthalten. Keines der oben gezeigten Beispiele bettet ein Zeilen einzeitiges Zeichen in die Zeichen folgen Konstante ein. Wie hier gezeigt, können Sie ein Zeilen Trennzeichen einbetten:

```cpp
// C2001b.cpp
#include <stdio.h>

int main()
{
    printf_s("Hello,\n\
             world");

    printf_s("Hello,\
             \nworld");

    printf_s("Hello,\n"
             "world");

    printf_s("Hello,"
             "\nworld");

    printf_s("Hello,"
             " world");

    printf_s("Hello,\
             world");
}
```
