---
title: pin_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- pin_ptr_cpp
- stdcli::language::pin_ptr
- pin_ptr
helpviewer_keywords:
- pinning pointers
- pin_ptr keyword [C++]
ms.assetid: 6c2e6c73-4ec2-4dce-8e1f-ccf3a9f9d0aa
ms.openlocfilehash: 9a9144229b75c09a892ddbf5bd592e67c7c2b6d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230557"
---
# <a name="pin_ptr-ccli"></a>pin_ptr (C++/CLI)

Deklariert einen *festen Zeiger*, der nur mit der Common Language Runtime verwendet wird.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

## <a name="windows-runtime"></a>Windows-Runtime

(Dieses Sprachfeature wird in der Windows-Runtime nicht unterstützt.)

## <a name="common-language-runtime"></a>Common Language Runtime

Ein *fester Zeiger* ist ein innerer Zeiger, der verhindert, dass das Objekt, auf das gezeigt wird, in den Heap der Garbage Collection verschoben wird. Das bedeutet, dass der Wert eines festen Zeigers von der Common Language Runtime nicht verändert wird. Dies ist erforderlich, wenn Sie die Adresse einer verwalteten Klasse an eine nicht verwaltete Funktion übergeben, sodass die Adresse während der Auflösung des nicht verwalteten Funktionsaufrufs nicht unerwartet geändert wird.

### <a name="syntax"></a>Syntax

```cpp
[cli::]pin_ptr<cv_qualifiertype>var = &initializer;
```

### <a name="parameters"></a>Parameter

*cv_qualifier*<br/>
**`const`** oder **`volatile`** Qualifizierer. Standardmäßig ist ein angeheftender Zeiger **`volatile`** . Es ist redundant, aber kein Fehler beim Deklarieren eines fixierenden Zeigers **`volatile`** .

*type*<br/>
Der Typ von *initializer*.

*var*<br/>
Der Name der Variable **pin_ptr**.

*initializer*<br/>
Ein Member eines Verweistyps, ein Element eines verwalteten Arrays oder jedes andere Objekt, das Sie einem nativen Zeiger zuweisen können.

### <a name="remarks"></a>Bemerkungen

Ein **pin_ptr** repräsentiert eine Obermenge der Funktionalität eines nativen Zeigers. Daher kann alles, was einem nativen Zeiger zugewiesen werden kann, auch einem **pin_ptr** zugewiesen werden. Ein innerer Zeiger darf die gleichen Vorgänge ausführen wie native Zeiger, einschließlich Vergleichs- und Zeigerarithmetik.

Ein Objekt oder untergeordnetes Objekt einer verwalteten Klasse kann angeheftet werden. In diesem Fall verschiebt die Common Language Runtime dieses Objekt während der Garbage Collection nicht. Dies wird hauptsächlich dazu genutzt, einen Zeiger als tatsächlichen Parameter eines nicht verwalteten Funktionsaufrufs an verwaltete Daten zu übergeben. Während des Auflistungszyklus untersucht die Runtime die für den festen Zeiger erstellten Metadaten und verschiebt das Element nicht, auf das gezeigt wird.

Beim Anheften eines Objekts werden auch die zugehörigen Wertfelder angeheftet, also Felder mit primitivem Typ oder Werttyp. Durch ein Nachverfolgungshandle (`%`) deklarierte Felder werden jedoch nicht angeheftet.

Das Anheften eines untergeordneten Objekts, das in einem verwalteten Objekt definiert ist, hat den gleichen Effekt wie das Anheften des gesamten Objekts.

Wenn der feste Zeiger neu zugewiesen wird und auf einen neuen Wert zeigt, wird die vorherige Instanz, auf die gezeigt wurde, nicht mehr als angeheftet betrachtet.

Ein Objekt ist nur dann angeheftet, während ein **pin_ptr** darauf zeigt. Das Objekt ist nicht mehr angeheftet, wenn der feste Zeiger den Gültigkeitsbereich verlässt oder auf [nullptr](nullptr-cpp-component-extensions.md) festgelegt wird. Nachdem **pin_ptr** den Gültigkeitsbereich verlassen hat, kann das Objekt, das zuvor angeheftet war, durch den Garbage Collector in den Heap verschoben werden. Native Zeiger, die weiterhin auf das Objekt zeigen, werden nicht aktualisiert, und das Entfernen von Verweisen aus einem dieser Zeiger kann eine nicht behebbare Ausnahme auslösen.

Wenn keine festen Zeiger auf das Objekt zeigen (alle festen Zeiger haben den Gültigkeitsbereich verlassen, wurden neu zugewiesen und zeigen jetzt auf andere Objekte oder ihnen wurde [nullptr](nullptr-cpp-component-extensions.md) zugewiesen), ist das Objekt garantiert nicht angeheftet.

Ein fester Zeiger kann auf ein Verweishandle, ein Handle mit Werttyp oder geschachteltem Typ, einen Member eines verwalteten Typs oder ein Element eines verwalteten Arrays zeigen. Er kann nicht auf einen Verweistyp zeigen.

Die Verwendung der Adresse eines **pin_ptr**, der auf ein natives Objekt zeigt, führt zu nicht definiertem Verhalten.

Feste Zeiger können nur als nicht statische lokale Variablen im Stapel deklariert werden.

Feste Zeiger können nicht für Folgendes verwendet werden:

- Funktionsparameter

- Rückgabetyp einer Funktion

- Member einer Klasse

- Zieltyp einer Umwandlung

**pin_ptr** befindet sich im Namespace `cli`. Weitere Informationen finden Sie unter [Namespaces „Platform“, „default“ und „cli“](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Weitere Informationen zu inneren Zeigern finden Sie unter [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md).

Weitere Informationen zum Anheften von Zeigern finden Sie unter Gewusst wie: Anheften von Zeigern [und Arrays](how-to-pin-pointers-and-arrays.md) und Gewusst [wie: Deklarieren von anheften und Werttypen](how-to-declare-pinning-pointers-and-value-types.md).

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Beispiel verwendet **pin_ptr**, um die Position des ersten Elements eines Arrays einzuschränken.

```cpp
// pin_ptr_1.cpp
// compile with: /clr
using namespace System;
#define SIZE 10

#pragma unmanaged
// native function that initializes an array
void native_function(int* p) {
   for(int i = 0 ; i < 10 ; i++)
    p[i] = i;
}
#pragma managed

public ref class A {
private:
   array<int>^ arr;   // CLR integer array

public:
   A() {
      arr = gcnew array<int>(SIZE);
   }

   void load() {
   pin_ptr<int> p = &arr[0];   // pin pointer to first element in arr
   int* np = p;   // pointer to the first element in arr
   native_function(np);   // pass pointer to native function
   }

   int sum() {
      int total = 0;
      for (int i = 0 ; i < SIZE ; i++)
         total += arr[i];
      return total;
   }
};

int main() {
   A^ a = gcnew A;
   a->load();   // initialize managed array using the native function
   Console::WriteLine(a->sum());
}
```

```Output
45
```

Das folgende Beispiel zeigt, dass ein innerer Zeiger in einen festen Zeiger konvertiert werden kann und dass der Rückgabetyp des address-of-Operators (`&`) ein innerer Zeiger ist, wenn sich der Operand nicht im verwalteten Heap befindet.

```cpp
// pin_ptr_2.cpp
// compile with: /clr
using namespace System;

ref struct G {
   G() : i(1) {}
   int i;
};

ref struct H {
   H() : j(2) {}
   int j;
};

int main() {
   G ^ g = gcnew G;   // g is a whole reference object pointer
   H ^ h = gcnew H;

   interior_ptr<int> l = &(g->i);   // l is interior pointer

   pin_ptr<int> k = &(h->j);   // k is a pinning interior pointer

   k = l;   // ok
   Console::WriteLine(*k);
};
```

```Output
1
```

Das folgende Beispiel zeigt, dass ein fester Zeiger in einen anderen Typ umgewandelt werden kann.

```cpp
// pin_ptr_3.cpp
// compile with: /clr
using namespace System;

ref class ManagedType {
public:
   int i;
};

int main() {
   ManagedType ^mt = gcnew ManagedType;
   pin_ptr<int> pt = &mt->i;
   *pt = 8;
   Console::WriteLine(mt->i);

   char *pc = ( char* ) pt;
   *pc = 255;
   Console::WriteLine(mt->i);
}
```

```Output
8
255
```
