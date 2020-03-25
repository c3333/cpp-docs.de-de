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
ms.openlocfilehash: c9d77cef790bdd0a65651ffb7246e685175482b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179990"
---
# <a name="explicit-specialization-of-function-templates"></a>Explizite Spezialisierung von Funktionsvorlagen

Bei einer Funktionsvorlage können Sie ein spezielles Verhalten für einen bestimmten Typ definieren, indem Sie eine explizite Spezialisierung (Überschreibung) der Funktionsvorlage für diesen Typ angeben. Beispiel:

```cpp
template<> void MySwap(double a, double b);
```

Diese Deklaration ermöglicht es Ihnen, eine andere Funktion für **doppelte** Variablen zu definieren. Wie nicht-Vorlagen Funktionen werden Standard Typkonvertierungen (z. b. das herauf Stufen einer Variablen vom Typ " **float** " in " **Double**") angewendet.

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

[Funktionsvorlagen](../cpp/function-templates.md)
