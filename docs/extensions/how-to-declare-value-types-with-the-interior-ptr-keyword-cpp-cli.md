---
title: 'Gewusst wie: Deklarieren von Werttypen mit dem interior_ptr-Schlüsselwort (C++/CLI)'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- _ptr keyword
- value types, declaring
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
ms.openlocfilehash: 22c0fe4424e4df81ebb0355dfac2168af725b971
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172281"
---
# <a name="how-to-declare-value-types-with-the-interior_ptr-keyword-ccli"></a>Gewusst wie: Deklarieren von Werttypen mit dem interior_ptr-Schlüsselwort (C++/CLI)

Ein **interior_ptr** kann mit einem Werttyp verwendet werden.

> [!IMPORTANT]
> Dieses Sprachfeature wird durch die Compileroption `/clr` unterstützt, nicht jedoch durch die Compileroption `/ZW`.

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das folgende C++/CLI-Beispiel veranschaulicht, wie ein **interior_ptr** mit einem Werttyp verwendet werden kann.

### <a name="code"></a>Code

```cpp
// interior_ptr_value_types.cpp
// compile with: /clr
value struct V {
   V(int i) : data(i){}
   int data;
};

int main() {
   V v(1);
   System::Console::WriteLine(v.data);

   // pointing to a value type
   interior_ptr<V> pv = &v;
   pv->data = 2;

   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);

   // pointing into a value type
   interior_ptr<int> pi = &v.data;
   *pi = 3;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(v.data);
   System::Console::WriteLine(pv->data);
}
```

```Output
1
2
2
3
3
3
```

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

In einem Werttyp wird **dieser** Zeiger als interior_ptr ergibt.

Im Text einer nicht statischen Memberfunktion eines Werttyps `V` ist **dies** ein Ausdruck vom Typ `interior_ptr<V>`, dessen Wert die Adresse des Objekts ist, für das die Funktion aufgerufen wird.

### <a name="code"></a>Code

```cpp
// interior_ptr_value_types_this.cpp
// compile with: /clr /LD
value struct V {
   int data;
   void f() {
      interior_ptr<V> pv1 = this;
      // V* pv2 = this;   error
   }
};
```

## <a name="example"></a>Beispiel

### <a name="description"></a>BESCHREIBUNG

Das folgende Beispiel zeigt, wie Sie den address-of-Operator mit statischen Membern verwenden.

Die Adresse eines statischen Visual C++-Typmembers ergibt einen nativen Zeiger.  Die Adresse eines statischen Werttypmembers ist ein verwalteter Zeiger, da ein Werttypmember auf dem Runtime-Heap zugeordnet wird und vom Garbage Collector verschoben werden kann.

### <a name="code"></a>Code

```cpp
// interior_ptr_value_static.cpp
// compile with: /clr
using namespace System;
value struct V { int i; };

ref struct G {
   static V v = {22};
   static int i = 23;
   static String^ pS = "hello";
};

int main() {
   interior_ptr<int> p1 = &G::v.i;
   Console::WriteLine(*p1);

   interior_ptr<int> p2 = &G::i;
   Console::WriteLine(*p2);

   interior_ptr<String^> p3 = &G::pS;
   Console::WriteLine(*p3);
}
```

```Output
22
23
hello
```

## <a name="see-also"></a>Weitere Informationen

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)
