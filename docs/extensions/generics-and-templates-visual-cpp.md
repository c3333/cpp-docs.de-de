---
title: Generics und Vorlagen (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 567286ee24e9df968b2d352489fe12f2735854eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172346"
---
# <a name="generics-and-templates-ccli"></a>Generics und Vorlagen (C++/CLI)

Generics und Vorlagen sind Sprachfeatures, die Unterstützung für parametrisierte Typen bieten. Sie unterscheiden sich jedoch in Funktionsweise und Verwendung. Dieses Thema bietet einen Überblick über die Unterschiede.

Weitere Informationen finden Sie unter [Windows-Runtime und verwaltete Vorlagen](windows-runtime-and-managed-templates-cpp-component-extensions.md).

## <a name="comparing-templates-and-generics"></a>Vergleich zwischen Vorlagen und Generics

Hauptunterschiede zwischen Generics und C++-Vorlagen:

- Generics sind so lange generisch, bis die Typen zur Laufzeit ersetzt werden. Vorlagen werden zur Kompilierzeit spezialisiert und sind daher zur Laufzeit noch keine parametrisierten Typen.

- Die Common Language Runtime unterstützt Generics insbesondere in MSIL. Da die Laufzeit Generics kennt, können generische Typen durch bestimmte Typen ersetzt werden, wenn auf eine Assembly verwiesen wird, die einen generischen Typ enthält. Im Gegensatz dazu werden Vorlagen zur Kompilierzeit in normale Typen aufgelöst, und die resultierenden Typen sind in anderen Assemblys möglicherweise nicht spezialisiert.

- Generics, die in zwei verschiedenen Assemblys mit dem gleichen Typargument spezialisiert wurden, weisen den gleichen Typ auf. Vorlagen, die in zwei verschiedenen Assemblys mit dem gleichen Typargument spezialisiert wurden, werden zur Laufzeit als verschiedene Typen betrachtet.

- Generics werden als ein einziger ausführbarer Code generiert, der für alle Verweistypargumente verwendet wird (dies gilt nicht für Werttypen, die über eine eindeutige Implementierung pro Werttyp verfügen). Der JIT-Compiler kennt Generics und kann den Code für die Verweis- oder Werttypen optimieren, die als Typargumente verwendet werden. Vorlagen generieren separaten Laufzeitcode für jede Spezialisierung.

- Generics lassen keine Vorlagenparameter ohne Typ zu, wie z.B. `template <int i> C {}`. Vorlagen lassen diese zu.

- Generics lassen eine explizite Spezialisierung (d.h. eine benutzerdefinierte Implementierung einer Vorlage für einen bestimmten Typ) nicht zu. Vorlagen lassen diese zu.

- Generics lassen keine partielle Spezialisierung zu (eine benutzerdefinierte Implementierung für eine Teilmenge der Typargumente). Vorlagen lassen diese zu.

- Generics lassen die Verwendung von Typparametern als Basisklasse für den generischen Typ nicht zu. Vorlagen lassen diese zu.

- Vorlagen unterstützen template-template-Parameter (z.B. `template<template<class T> class X> class MyClass`), Generics nicht.

## <a name="combining-templates-and-generics"></a>Kombinieren von Vorlagen und Generics

Der grundlegende Unterschied zwischen Vorlagen und Generics wirkt sich auf die Erstellung von Anwendungen aus, die Vorlagen und Generics kombinieren. Nehmen Sie z.B. an, Sie haben eine Vorlagenklasse, für die Sie einen generischen Wrapper erstellen möchten, um diese Vorlage für andere Sprachen als generischen Typ verfügbar zu machen. Generics können keinen Typparameter akzeptieren, der diese dann an die Vorlage übergibt, da die Vorlage diesen Typparameter zur Kompilierzeit benötigt, die Generics den Typparameter aber erst zur Laufzeit auflösen. Das Schachteln einer Vorlage in einem generischen Typ funktioniert ebenfalls nicht, da es keine Möglichkeit gibt, die Vorlagen zur Kompilierzeit auf beliebige generische Typen erweitern, die zur Laufzeit instanziiert werden können.

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Nachfolgend sehen Sie ein einfaches Beispiel für die gemeinsame Verwendung von Vorlagen und Generics. In diesem Beispiel übergibt die Vorlagenklasse ihre Parameter an den generischen Typ. Umgekehrt ist dies nicht möglich.

Dieses Idiom sollte verwendet werden, wenn Sie eine vorhandene generische API um Vorlagencode erweitern möchten, der lokal für eine C++/CLI-Assembly geschrieben wurde, oder wenn Sie einem generischen Typ eine weitere Ebene der Parametrisierung hinzufügen möchten, um bestimmte Vorlagenfeatures zu nutzen, die von Generics nicht unterstützt werden.

### <a name="code"></a>Code

```cpp
// templates_and_generics.cpp
// compile with: /clr
using namespace System;

generic <class ItemType>
ref class MyGeneric {
   ItemType m_item;

public:
   MyGeneric(ItemType item) : m_item(item) {}
   void F() {
      Console::WriteLine("F");
   }
};

template <class T>
public ref class MyRef {
MyGeneric<T>^ ig;

public:
   MyRef(T t) {
      ig = gcnew MyGeneric<T>(t);
      ig->F();
    }
};

int main() {
   // instantiate the template
   MyRef<int>^ mref = gcnew MyRef<int>(11);
}
```

```Output
F
```

## <a name="see-also"></a>Weitere Informationen

[Generics](generics-cpp-component-extensions.md)
