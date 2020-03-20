---
title: 'Gewusst wie: Deklarieren von Handles in systemeigenen Typen'
ms.custom: get-started-article
ms.date: 11/04/2016
f1_keywords:
- gcroot
helpviewer_keywords:
- handles, declaring
- gcroot keyword [C++]
- types [C++], declaring handles in
ms.assetid: b8c0eead-17e5-4003-b21f-b673f997d79f
ms.openlocfilehash: 11dbc196a89a224afe02312fbe4dff99d8467f4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545036"
---
# <a name="how-to-declare-handles-in-native-types"></a>Gewusst wie: Deklarieren von Handles in systemeigenen Typen

Sie können einen Handles-Typ nicht in einem systemeigenen Typ deklarieren. Vcclr. h stellt die typsichere Wrapper Vorlage `gcroot` bereit, um auf ein CLR-Objekt aus C++ dem Heap zu verweisen. Mit dieser Vorlage können Sie ein virtuelles Handle in einen systemeigenen Typ einbetten und dieses Handle so behandeln, als wäre es der zugrunde liegende Typ. In den meisten Fällen können Sie das `gcroot`-Objekt als eingebetteten Typ ohne Umwandlung verwenden. Allerdings müssen Sie bei [for each in mithilfe von](../dotnet/for-each-in.md)`static_cast` den zugrunde liegenden verwalteten Verweis abrufen.

Die `gcroot` Vorlage wird mithilfe der Funktionen der Value-Klasse System:: Runtime:: InteropServices:: GCHandle implementiert, die "Handles" im Heap der Garbage Collection bereitstellt. Beachten Sie, dass die Handles selbst nicht in die Garbage Collection aufgenommen werden und freigegeben werden, wenn Sie nicht mehr vom Dekonstruktor in der `gcroot`-Klasse verwendet werden (dieser Dekonstruktor kann nicht manuell aufgerufen werden). Wenn Sie ein `gcroot` Objekt im systemeigenen Heap instanziieren, müssen Sie DELETE für diese Ressource aufzurufen.

Die Laufzeit behält eine Zuordnung zwischen dem Handle und dem CLR-Objekt bei, auf das verwiesen wird. Wenn das CLR-Objekt mit dem Heap der Garbage Collection verschoben wird, gibt das Handle die neue Adresse des Objekts zurück. Eine Variable muss nicht fixiert werden, bevor Sie einer `gcroot` Vorlage zugewiesen wird.

## <a name="example"></a>Beispiel

In diesem Beispiel wird gezeigt, wie ein `gcroot`-Objekt auf dem systemeigenen Stapel erstellt wird.

```cpp
// mcpp_gcroot.cpp
// compile with: /clr
#include <vcclr.h>
using namespace System;

class CppClass {
public:
   gcroot<String^> str;   // can use str as if it were String^
   CppClass() {}
};

int main() {
   CppClass c;
   c.str = gcnew String("hello");
   Console::WriteLine( c.str );   // no cast required
}
```

```Output
hello
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird gezeigt, wie ein `gcroot`-Objekt im systemeigenen Heap erstellt wird.

```cpp
// mcpp_gcroot_2.cpp
// compile with: /clr
// compile with: /clr
#include <vcclr.h>
using namespace System;

struct CppClass {
   gcroot<String ^> * str;
   CppClass() : str(new gcroot<String ^>) {}

   ~CppClass() { delete str; }

};

int main() {
   CppClass c;
   *c.str = gcnew String("hello");
   Console::WriteLine( *c.str );
}
```

```Output
hello
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird gezeigt, wie `gcroot` verwendet wird, um Verweise auf Werttypen (nicht Verweis Typen) in einem systemeigenen Typ mithilfe `gcroot` auf dem geschachtelt-Typ zu speichern.

```cpp
// mcpp_gcroot_3.cpp
// compile with: /clr
#include < vcclr.h >
using namespace System;

public value struct V {
   String^ str;
};

class Native {
public:
   gcroot< V^ > v_handle;
};

int main() {
   Native native;
   V v;
   native.v_handle = v;
   native.v_handle->str = "Hello";
   Console::WriteLine("String in V: {0}", native.v_handle->str);
}
```

```Output
String in V: Hello
```

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
