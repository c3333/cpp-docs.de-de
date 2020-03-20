---
title: 'Gewusst wie: Verwenden eines systemeigenen Typs in einer CLR-Kompilierung'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: b506c3d825c4c26236a4ac3fc9682067a011315a
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545204"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>Gewusst wie: Verwenden eines systemeigenen Typs in einer /clr-Kompilierung

Sie können einen systemeigenen Typ in einer **/CLR** -Kompilierung definieren, und jede Verwendung dieses systemeigenen Typs innerhalb der Assembly ist gültig. Systemeigene Typen können jedoch nicht von Metadaten verwendet werden, auf die verwiesen wird.

Jede Assembly muss die Definition aller systemeigenen Typen enthalten, die Sie verwenden wird.

Weitere Informationen finden Sie unter [/clr (Common Language Runtime-Kompilierung)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Beispiel

In diesem Beispiel wird eine Komponente erstellt, die einen systemeigenen Typ definiert und verwendet.

```cpp
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird ein Client definiert, der die-Komponente verwendet. Beachten Sie, dass es sich um einen Fehler handelt, der auf den systemeigenen Typ zugreifen kann, es sei denn, er ist in kompiliert.

```cpp
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
