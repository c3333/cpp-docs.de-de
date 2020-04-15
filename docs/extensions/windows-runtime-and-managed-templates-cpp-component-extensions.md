---
title: Windows-Runtime und verwaltete Vorlagen (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: 5765370e611e5822b3b2d156d2eee5d21e5b453d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376303"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows-Runtime und verwaltete Vorlagen (C++/CLI und C++/CX)

Mit Vorlagen können Sie einen Prototyp einer Windows-Runtime oder einen Common Language Runtime-Typ definieren und dann Variationen dieses Typs mithilfe verschiedener Vorlagentypparameter instanziieren.

## <a name="all-runtimes"></a>Alle Laufzeiten

Sie können Vorlagen von Wert- oder Referenztypen erstellen.  Weitere Informationen zum Erstellen von Wert- oder Referenztypen finden Sie unter [Klassen und Strukturen](classes-and-structs-cpp-component-extensions.md).

Weitere Informationen zu C++-Standardklassenvorlagen finden Sie unter [Klassenvorlagen](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Windows-Runtime

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Windows-Runtime gelten.)

### <a name="requirements"></a>Anforderungen

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Es gibt einige Einschränkungen für das Erstellen von Klassenvorlagen aus verwalteten Typen, die in den folgenden Codebeispielen veranschaulicht werden.

### <a name="requirements"></a>Anforderungen

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Es ist möglich, einen generischen Typ mit einem Vorlagenparameter eines verwalteten Typs zu instanziieren, aber Sie können keine verwaltete Vorlage mit einem Vorlagenparameter eines generischen Typs instanziieren. Dies liegt daran, dass generische Typen zur Laufzeit aufgelöst werden. Weitere Informationen finden Sie unter [Generics und Vorlagen (C++/CLI)](generics-and-templates-visual-cpp.md).

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

Ein generischer Typ oder eine generische Funktion kann nicht in einer verwalteten Vorlage geschachtelt werden.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

Sie können nicht auf Vorlagen zugreifen, die in einer referenzierten Assembly mit C++/CLI-Sprachsyntax definiert sind, aber Sie können Reflektion verwenden. Wenn eine Vorlage nicht instanziiert wird, wird sie nicht in den Metadaten angezeigt. Wenn eine Vorlage instanziiert ist, werden nur Memberfunktionen, auf die verwiesen wird, in den Metadaten angezeigt.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

Sie können den verwalteten Modifizierer einer Klasse in einer teilweisen Spezialisierung oder expliziten Spezialisierung einer Klassenvorlage ändern.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>Siehe auch

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
