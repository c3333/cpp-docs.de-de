---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: affec6dcd88290b24a92cd9035a131baee38bcf1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214268"
---
# <a name="interior_ptr-ccli"></a>interior_ptr (C++/CLI)

Ein *innerer Zeiger* deklariert einen Zeiger in einen Verweistyp, aber nicht auf das Objekt selbst. Ein innerer Zeiger kann auf ein Verweishandle, einen Werttyp, das Handle eines Boxed-Typs, einen Member eines verwalteten Typs oder ein Element eines verwalteten Arrays zeigen.

## <a name="all-runtimes"></a>Alle Laufzeiten

(Es gibt keine Hinweise für diese Sprachfunktion, die für alle Laufzeiten gültig sind.)

## <a name="windows-runtime"></a>Windows-Runtime

(Es gibt keine Hinweise für diese Sprachfunktion, die nur für Windows-Runtime gelten.)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Im folgenden Syntaxbeispiel wird ein innerer Zeiger dargestellt.

### <a name="syntax"></a>Syntax

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>Parameter

*cv_qualifier*<br/>
**`const`** oder **`volatile`** Qualifizierer.

*type*<br/>
Der Typ von *initializer*.

*var*<br/>
Der Name der **interior_ptr**-Variablen.

*initializer*<br/>
Ein Member eines Verweistyps, ein Element eines verwalteten Arrays oder jedes andere Objekt, das Sie einem nativen Zeiger zuweisen können.

### <a name="remarks"></a>Bemerkungen

Ein nativer Zeiger kann kein Element nachverfolgen, da sein Speicherort sich auf dem verwalteten Heap ändert, was dazu führt, dass der Garbage Collector Instanzen eines Objekts verschiebt. Damit ein Zeiger ordnungsgemäß auf die Instanz verweisen kann, muss die Runtime den Zeiger mit dem neu positionierten Objekt aktualisieren.

Ein **interior_ptr** repräsentiert eine Obermenge der Funktionalität eines nativen Zeigers.  Daher kann alles, was einem nativen Zeiger zugewiesen werden kann, auch einem **interior_ptr** zugewiesen werden.  Ein innerer Zeiger darf die gleichen Vorgänge ausführen wie native Zeiger, einschließlich Vergleichs- und Zeigerarithmetik.

Ein innerer Zeiger kann nur auf dem Stapel deklariert werden.  Ein innerer Zeiger kann nicht als Member einer Klasse deklariert werden.

Da innere Zeiger nur auf dem Stapel vorhanden sind, ergibt das Übernehmen der Adresse eines inneren Zeigers einen nicht verwalteten Zeiger.

**interior_ptr** eine implizite Konvertierung in durchführen **`bool`** , die die Verwendung in Bedingungs Anweisungen ermöglicht.

Informationen dazu, wie ein innerer Zeiger deklariert wird, der in ein Objekt verweist, dass auf dem der Garbage Collection unterzogenen Heap nicht verschoben werden kann, finden Sie unter [pin_ptr](pin-ptr-cpp-cli.md).

**interior_ptr** befindet sich im cli-Namespace.  Weitere Informationen finden Sie unter [Namespaces „Platform“, „default“ und „cli“](platform-default-and-cli-namespaces-cpp-component-extensions.md).

Weitere Informationen zu inneren Zeigern finden Sie unter

- [Gewusst wie: Deklarieren und Verwenden von inneren Zeigern und verwalteten Arrays (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [Gewusst wie: Deklarieren von Werttypen mit dem interior_ptr-Schlüsselwort (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [Gewusst wie: Überladen von Funktionen mit inneren und systemeigenen Zeigern (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [Gewusst wie: Deklarieren von inneren Zeigern mit dem const-Schlüsselwort (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

### <a name="examples"></a>Beispiele

Das folgende Beispiel zeigt, wie Sie einen inneren Zeiger in einen Verweistyp deklarieren und verwenden.

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>Weitere Informationen

[Komponenten Erweiterungen für .net und UWP](component-extensions-for-runtime-platforms.md)
