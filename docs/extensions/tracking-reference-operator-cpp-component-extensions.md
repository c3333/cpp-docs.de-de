---
title: Nachverfolgungsverweisoperator (C++/CLI und C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: ccd31b3e334dc5a4cd2e48b94c9dbe85cf13c16b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368234"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Nachverfolgungsverweisoperator (C++/CLI und C++/CX)

Ein *Tracking-Verweis* (`%`) verhält sich wie`&`ein gewöhnlicher C++-Verweis ( ), mit der Ausnahme, dass, wenn ein Objekt einem Tracking-Verweis zugewiesen wird, die Referenzanzahl des Objekts erhöht wird.

## <a name="all-platforms"></a>Alle Plattformen

Ein Nachverfolgungsverweis verfügt über die folgenden Eigenschaften.

- Die Zuweisung eines Objekts zu einem Nachverfolgungsverweis bewirkt, dass die Referenzanzahl des Objekts erhöht wird.

- Wenn Sie einen `*` dereferenzieren, ist das Ergebnis ein nativer Verweis (`&`). Wenn Sie einen `^` dereferenzieren, ist das Ergebnis ein Nachverfolgungsverweis (`%`). Solange Sie über einen `%` zu einem Objekt verfügen, bleibt das Objekt im Speicher erhalten.

- Der Punktzugriffsoperator (`.`) für Member wird verwendet, um auf einen Member des Objekts zuzugreifen.

- Nachverfolgungsverweise gelten für Werttypen und Handles (beispielsweise `String^`).

- Einem Nachverfolgungsverweis kann kein NULL- oder **nullptr**-Wert zugewiesen werden. Ein Nachverfolgungsverweis kann einem anderen gültigen Objekt so oft wie erforderlich neu zugewiesen werden.

- Ein Nachverfolgungsverweis kann nicht als unärer Adressenübernahmeoperator (Take-Address-Operator) verwendet werden.

## <a name="windows-runtime"></a>Windows-Runtime

Ein Nachverfolgungsverweis verhält sich wie ein Standard-C++-Verweis, und zwar mit Ausnahme, dass ein % per Referenzzählung behandelt wird. Der folgende Ausschnitt zeigt die Konvertierung zwischen %- und ^-Typen:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

Im folgenden Beispiel wird das Übergeben einer ^-Funktion gezeigt, die ein % aufweist.

```cpp
ref class Foo sealed {};

    // internal or private
    void UseFooHelper(Foo% f)
    {
        auto x = %f;
    }

    // public method on ABI boundary
    void UseFoo(Foo^ f)
    {
        if (f != nullptr) { UseFooHelper(*f); }
    }
```

## <a name="common-language-runtime"></a>Common Language Runtime

Sie können in C++/CLI einen Nachverfolgungsverweis auf ein Handle verwenden, um eine Bindung zu einem Objekt eines CLR-Typs auf dem Heap der Garbage Collection herzustellen.

In der CLR wird der Wert einer Nachverfolgungsverweisvariablen automatisch aktualisiert, wenn der Garbage Collector das referenzierte Objekt verschiebt.

Ein Nachverfolgungsverweis kann nur auf dem Stapel deklariert werden. Ein Nachverfolgungsverweis kann kein Klassenmember sein.

Die Verwendung eines systemeigenen C++-Verweises auf ein Objekt auf dem Heap der Garbage Collection ist nicht möglich.

Weitere Informationen über Nachverfolgungsverweise in C++/CLI finden Sie unter:

- [Vorgehensweise: Verwenden von Nachverfolgungsverweisen in C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Beispiele

Das folgende Beispiel für C++/CLI veranschaulicht, wie ein Nachverfolgungsverweis mit systemeigenen und verwalteten Typen verwendet wird.

```cpp
// tracking_reference_1.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;
};

value struct MyStruct {
   int k;
};

int main() {
   MyClass ^ x = ref new MyClass;
   MyClass ^% y = x;   // tracking reference handle to reference object

   int %ti = x->i;   // tracking reference to member of reference type

   int j = 0;
   int %tj = j;   // tracking reference to object on the stack

   int * pi = new int[2];
   int % ti2 = pi[0];   // tracking reference to object on native heap

   int *% tpi = pi;   // tracking reference to native pointer

   MyStruct ^ x2 = ref new MyStruct;
   MyStruct ^% y2 = x2;   // tracking reference to value object

   MyStruct z;
   int %tk = z.k;   // tracking reference to member of value type

   delete[] pi;
}
```

Das folgende Beispiel für C++/CLI veranschaulicht, wie ein Nachverfolgungsverweis an ein Array gebunden wird.

```cpp
// tracking_reference_2.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int> ^ a = ref new array<Int32>(5);
   a[0] = 21;
   Console::WriteLine(a[0]);
   array<int> ^% arr = a;
   arr[0] = 222;
   Console::WriteLine(a[0]);
}
```

```Output
21
222
```
