---
title: Explizite Spezialisierung von Funktionsvorlagen
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: 638b5dbca1b3c0c9b9c9c946418ea70354ff6266
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220560"
---
# <a name="explicit-specialization-of-function-templates"></a>Explizite Spezialisierung von Funktionsvorlagen

Bei einer Funktionsvorlage können Sie ein spezielles Verhalten für einen bestimmten Typ definieren, indem Sie eine explizite Spezialisierung (Überschreibung) der Funktionsvorlage für diesen Typ angeben. Beispiel:

```cpp
template<> void MySwap(double a, double b);
```

Diese Deklaration ermöglicht es Ihnen, eine andere Funktion für Variablen zu definieren **`double`** . Wie nicht-Vorlagen Funktionen werden Standard Typkonvertierungen (z. b. das herauf Stufen einer Variablen vom Typ **`float`** zu **`double`** ) angewendet.

## <a name="example"></a>Beispiel

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>Weitere Informationen

[Funktions Vorlagen](../cpp/function-templates.md)
