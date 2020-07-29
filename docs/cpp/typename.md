---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 62e8a2026babbfea3cd1583def05a03b4bc4a229
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223511"
---
# <a name="typename"></a>typename

Stellt in Vorlagen Definitionen einen Hinweis für den Compiler bereit, dass ein unbekannter Bezeichner ein Typ ist. In Vorlagen Parameterlisten wird verwendet, um einen Typparameter anzugeben.

## <a name="syntax"></a>Syntax

```
typename identifier;
```

## <a name="remarks"></a>Bemerkungen

Dieses Schlüsselwort muss verwendet werden, wenn ein Name in einer Vorlagen Definition ein qualifizierter Name ist, der von einem Vorlagen Argument abhängig ist. Dies ist optional, wenn der qualifizierte Name nicht abhängig ist. Weitere Informationen finden Sie unter [Vorlagen und Namensauflösung](../cpp/templates-and-name-resolution.md).

**`typename`** kann von jedem beliebigen Typ an beliebiger Stelle in einer Vorlagen Deklaration oder-Definition verwendet werden. Es ist in der Basisklassenliste nicht zulässig, außer als Vorlagenargument für eine Vorlagenbasisklasse.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

Das- **`typename`** Schlüsselwort kann auch anstelle von **`class`** in Vorlagen Parameterlisten verwendet werden. Die folgenden Anweisungen sind z. b. semantisch äquivalent:

```cpp
template<class T1, class T2>...
template<typename T1, typename T2>...
```

## <a name="example"></a>Beispiel

```cpp
// typename.cpp
template<class T> class X
{
   typename T::Y m_y;   // treat Y as a type
};

int main()
{
}
```

## <a name="see-also"></a>Siehe auch

[Vorlagen](../cpp/templates-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
