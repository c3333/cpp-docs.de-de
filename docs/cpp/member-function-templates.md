---
title: Memberfunktionsvorlagen
ms.date: 11/04/2016
helpviewer_keywords:
- function templates, member functions
ms.assetid: 83d51835-6a27-40ed-997c-7d90dc9182d8
ms.openlocfilehash: ee36d4f33f3e4216e2ad9c434ac1da4ca3aa83e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177980"
---
# <a name="member-function-templates"></a>Memberfunktionsvorlagen

Der Ausdruck "Membervorlage" bezieht sich auf Memberfunktionsvorlagen und geschachtelte Klassenvorlagen. Memberfunktionsvorlagen sind Vorlagenfunktionen, die Member einer Klasse oder einer Klassenvorlage sind.

Memberfunktionen können in mehreren Kontexten Funktionsvorlagen sein. Alle Funktionen von Klassenvorlagen sind generisch, werden jedoch nicht als Membervorlagen oder Memberfunktionsvorlagen bezeichnet. Wenn diese Memberfunktionen eigene Vorlagenargumente übernehmen, werden sie als Memberfunktionsvorlagen betrachtet.

## <a name="example"></a>Beispiel

Memberfunktionsvorlagen von nicht auf Vorlagen basierenden Klassen oder Vorlagenklassen werden als Funktionsvorlagen mit ihren Vorlagenparametern deklariert.

```cpp
// member_function_templates.cpp
struct X
{
   template <class T> void mf(T* t) {}
};

int main()
{
   int i;
   X* x = new X();
   x->mf(&i);
}
```

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt eine Memberfunktionsvorlage einer Vorlagenklasse.

```cpp
// member_function_templates2.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u)
   {
   }
};

int main()
{
}
```

## <a name="example"></a>Beispiel

```cpp
// defining_member_templates_outside_class.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="example"></a>Beispiel

Lokale Klassen dürfen keine Membervorlagen haben.

Membervorlagenfunktionen können keine virtuellen Funktionen sein und können keine virtuellen Funktionen einer Basisklasse überschreiben, wenn sie mit dem gleichen Namen wie eine virtuelle Funktion der Basisklasse deklariert werden.

Das folgende Beispiel zeigt eine auf Vorlagen basierende benutzerdefinierte Konvertierung:

```cpp
// templated_user_defined_conversions.cpp
template <class T>
struct S
{
   template <class U> operator S<U>()
   {
      return S<U>();
   }
};

int main()
{
   S<int> s1;
   S<long> s2 = s1;  // Convert s1 using UDC and copy constructs S<long>.
}
```

## <a name="see-also"></a>Weitere Informationen

[Funktionsvorlagen](../cpp/function-templates.md)
