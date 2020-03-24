---
title: typename
ms.date: 11/04/2016
f1_keywords:
- typename_cpp
helpviewer_keywords:
- typename template specifier
ms.assetid: 52e1d901-220d-4f0d-ab43-dae7e05fb491
ms.openlocfilehash: 789bb879922bbd96a04085159205d02fb7f495c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160683"
---
# <a name="typename"></a>typename

Stellt in Vorlagen Definitionen einen Hinweis für den Compiler bereit, dass ein unbekannter Bezeichner ein Typ ist. In Vorlagen Parameterlisten wird verwendet, um einen Typparameter anzugeben.

## <a name="syntax"></a>Syntax

```
typename identifier;
```

## <a name="remarks"></a>Bemerkungen

Dieses Schlüsselwort muss verwendet werden, wenn ein Name in einer Vorlagen Definition ein qualifizierter Name ist, der von einem Vorlagen Argument abhängig ist. Dies ist optional, wenn der qualifizierte Name nicht abhängig ist. Weitere Informationen finden Sie unter [Vorlagen und Namensauflösung](../cpp/templates-and-name-resolution.md).

**Typname** kann von jedem beliebigen Typ an beliebiger Stelle in einer Vorlagen Deklaration oder-Definition verwendet werden. Es ist in der Basisklassenliste nicht zulässig, außer als Vorlagenargument für eine Vorlagenbasisklasse.

```cpp
template <class T>
class C1 : typename T::InnerType // Error - typename not allowed.
{};
template <class T>
class C2 : A<typename T::InnerType>  // typename OK.
{};
```

Das Schlüsselwort " **typame** " kann auch anstelle der **Klasse** in Vorlagen Parameterlisten verwendet werden. Die folgenden Anweisungen sind z. b. semantisch äquivalent:

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

## <a name="see-also"></a>Weitere Informationen

[Vorlagen](../cpp/templates-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
