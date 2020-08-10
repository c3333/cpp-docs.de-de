---
title: Datentypspezifizierer und Entsprechungen
ms.date: 11/04/2016
helpviewer_keywords:
- type specifiers [C++], list
- widening integers
- data types [C++], equivalents
- sign-extending integral types
- zero-extending
- identifiers, data type
- data types [C++], specifiers
- simple types, names
- type names [C++], simple
ms.assetid: 0d4b515a-4f68-4786-83cf-a5d43c7cb6f3
ms.openlocfilehash: cc8ba746bea7f6ea885beb625de414d83367b53f
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520680"
---
# <a name="data-type-specifiers-and-equivalents"></a>Datentypspezifizierer und Entsprechungen

In diesem Buch wird anstelle der langen Formen im Allgemeinen die Form der Typspezifizierer verwendet, die in der folgenden Tabelle aufgelistet sind, und es wird davon ausgegangen, dass der Typ **`char`** standardmäßig signiert ist. Daher entspricht **`char`** in diesem Buch **`signed char`** .

## <a name="type-specifiers-and-equivalents"></a>Typspezifizierer und Entsprechungen

| Typspezifizierer | Entsprechung(en) |
|--|--|
| **`signed char`** <sup>1</sup> | **`char`** |
| **`signed int`** | **`signed`** , **`int`** |
| **`signed short int`** | **`short`** , **`signed short`** |
| **`signed long int`** | **`long`** , **`signed long`** |
| **`unsigned char`** | — |
| **`unsigned int`** | **`unsigned`** |
| **`unsigned short int`** | **`unsigned short`** |
| **`unsigned long int`** | **`unsigned long`** |
| **`float`** | — |
| **`long double`** <sup>2</sup> | — |

<sup>1</sup> Wenn Sie den **`char`** -Typ standardmäßig nicht signiert ausführen (durch Angabe der Compileroption **`/J`** ), können Sie **`signed char`** nicht als **`char`** abkürzen.

<sup>2</sup> Auf 32-Bit- und 64-Bit-Betriebssystemen ordnet der Microsoft-C-Compiler **`long double`** dem Typ **`double`** zu.

**Microsoft-spezifisch**

Sie können die **`/J`** -Compileroption angeben, um den Standardtyp **`char`** von **`signed char`** in **`unsigned char`** zu ändern. Wenn diese Option aktiviert ist, hat **`char`** dieselbe Bedeutung wie **`unsigned char`** , und Sie müssen das **`signed`** -Schlüsselwort verwenden, um einen signierten Zeichenwert anzugeben. Wenn ein **`char`** -Wert explizit als **`signed`** deklariert ist, hat die **`/J`** -Option keine Auswirkung darauf, und der Wert wird um das Vorzeichen erweitert, wenn er zu einem **`int`** -Typ erweitert wurde. Der **`char`** -Typ wird mit Null erweitert, wenn er auf den **`int`** -Typ erweitert wird.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Typspezifizierer](../c-language/c-type-specifiers.md)
