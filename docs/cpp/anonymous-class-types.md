---
title: Anonyme Klassentypen
ms.date: 11/04/2016
helpviewer_keywords:
- class types [C++], anonymous
- anonymous class types
ms.assetid: 9ba667b2-8c2a-4c29-82a6-fa120b9233c8
ms.openlocfilehash: e227f48588c3c4f59c0d0bd28ab16178de159b58
ms.sourcegitcommit: 89d9e1cb08fa872483d1cde98bc2a7c870e505e9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "82032082"
---
# <a name="anonymous-class-types"></a>Anonyme Klassentypen

Klassen können anonym sein, d. h. sie können ohne *Bezeichner*deklariert werden. Dies ist nützlich, wenn Sie einen Klassennamen durch einen **typedef-Namen** ersetzen, wie im Folgenden:

```cpp
typedef struct
{
    unsigned x;
    unsigned y;
} POINT;
```

> [!NOTE]
> Die Verwendung von anonymen Klassen, die im vorherigen Beispiel gezeigt wird, ist für das Beibehalten der Kompatibilität mit existierendem C-Code nützlich. In einigen C-Codes ist die Verwendung von **typedef** in Verbindung mit anonymen Strukturen weit verbreitet.

Anonyme Klassen sind außerdem nützlich, wenn Sie möchten, dass ein Verweis auf einen Klassenmember so angezeigt wird, als befände er sich nicht in einer separaten Klasse, wie im Folgenden gezeigt:

```cpp
struct PTValue
{
    POINT ptLoc;
    union
    {
        int  iValue;
        long lValue;
    };
};

PTValue ptv;
```

Im vorherigen Code `iValue` kann mit dem Objektmemberauswahloperator (**.**) wie folgt zugegriffen werden:

```cpp
int i = ptv.iValue;
```

Anonyme Klassen unterliegen bestimmten Einschränkungen. (Weitere Informationen zu anonymen Gewerkschaften finden Sie unter [Unions](../cpp/unions.md).) Anonyme Klassen:

- Können keinen Konstruktor oder Destruktor aufweisen.

- Kann nicht als Argumente an Funktionen übergeben werden (es sei denn, die Typprüfung wird mit Auslassungsfunktionen besiegt).

- Können nicht als Rückgabewerte von Funktionen zurückgegeben werden.

## <a name="anonymous-structs"></a>Anonyme Strukturen

**Microsoft Specific**

Eine Microsoft C-Erweiterung ermöglicht es Ihnen, eine Strukturvariable innerhalb einer anderen Struktur zu deklarieren, ohne ihr einen Namen zu geben. Diese geschachtelten Strukturen werden als anonyme Strukturen bezeichnet. In C++ sind anonyme Strukturen nicht zulässig.

Sie können auf Member einer anonymen Struktur zugreifen, als ob sie Member der enthaltenden Struktur wären.

```cpp
// anonymous_structures.c
#include <stdio.h>

struct phone
{
    int  areacode;
    long number;
};

struct person
{
    char   name[30];
    char   gender;
    int    age;
    int    weight;
    struct phone;    // Anonymous structure; no name needed
} Jim;

int main()
{
    Jim.number = 1234567;
    printf_s("%d\n", Jim.number);
}
//Output: 1234567
```

**END Microsoft Spezifisch**
