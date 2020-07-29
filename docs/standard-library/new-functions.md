---
title: '&lt;new&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: 6b51a5bcbb9c90370cef1391d4020862d2e2cefd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212175"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt;-Funktionen

## <a name="get_new_handler"></a><a name="get_new_handler"></a>get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Bemerkungen

Gibt den aktuellen zurück `new_handler` .

## <a name="launder"></a><a name="launder"></a>launter

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>Parameter

*PTR*\
Die Adresse eines Bytes im Arbeitsspeicher, das ein Objekt enthält, dessen Typ mit *T*vergleichbar ist.

### <a name="return-value"></a>Rückgabewert

Ein Wert vom Typ *T \* * , der auf X zeigt.

### <a name="remarks"></a>Bemerkungen

Wird auch als eine Zeiger Optimierungs Barriere bezeichnet.

Wird als konstanter Ausdruck verwendet, wenn der Wert des Arguments in einem konstanten Ausdruck verwendet werden kann. Ein Byte des Speichers ist durch einen Zeiger Wert erreichbar, der auf ein Objekt zeigt, wenn es sich im Speicher befindet, der von einem anderen Objekt belegt wird, einem Objekt mit einem ähnlichen Zeiger.

### <a name="example"></a>Beispiel

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a><a name="nothrow"></a>nothrow

Stellt ein Objekt bereit, das als Argument für die **`nothrow`** Versionen von und verwendet werden soll **`new`** **`delete`** .

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Bemerkungen

Das Objekt wird als Funktionsargument verwendet, um auf den Parametertyp [std::nothrow_t](../standard-library/nothrow-t-structure.md) abzustimmen.

### <a name="example"></a>Beispiel

Beispiele zur Verwendung von `std::nothrow_t` als Funktionsparameter finden Sie unter [operator new](../standard-library/new-operators.md#op_new) und [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr).

## <a name="set_new_handler"></a><a name="set_new_handler"></a>set_new_handler

Installiert eine Benutzerfunktion, die aufgerufen werden soll, wenn der **New-Operator** beim Versuch, Arbeitsspeicher zuzuweisen, fehlschlägt.

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>Parameter

*Pnew*\
Das `new_handler` zu installierende.

### <a name="return-value"></a>Rückgabewert

0 (null) beim ersten Aufruf und der vorherige `new_handler` bei nachfolgenden Aufrufen.

### <a name="remarks"></a>Bemerkungen

Die Funktion speichert *Pnew* in einem statischen [neuen handlerzeiger](../standard-library/new-typedefs.md#new_handler) , den Sie verwaltet, und gibt dann den zuvor im Zeiger gespeicherten Wert zurück. Der neue Handler wird von [Operator new](../standard-library/new-operators.md#op_new)(**size_t**) verwendet.

### <a name="example"></a>Beispiel

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
