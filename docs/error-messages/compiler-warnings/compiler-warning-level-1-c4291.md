---
title: Compilerwarnung (Stufe 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: e45856702eef7f24595d10b81f39047d8f9a08b2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221002"
---
# <a name="compiler-warning-level-1-c4291"></a>Compilerwarnung (Stufe 1) C4291

' Deklaration ': Es wurde kein passender Operator gelöscht gefunden. der Arbeitsspeicher wird nicht freigegeben, wenn die Initialisierung eine Ausnahme auslöst.

Eine Platzierung [New](../../cpp/new-operator-cpp.md) wird verwendet, für die kein Platzierungs [Lösch](../../cpp/delete-operator-cpp.md)Vorgang erfolgt.

Wenn Arbeitsspeicher für ein Objekt mit Operator zugewiesen wird **`new`** , wird der Konstruktor des Objekts aufgerufen. Wenn der Konstruktor eine Ausnahme auslöst, sollte der Arbeitsspeicher, der dem Objekt zugeordnet wurde, die Zuordnung aufgehoben werden. Dies kann nur dann erfolgen, wenn eine Operator **`delete`** Funktion vorhanden ist, die mit dem Operator übereinstimmt **`new`** .

Wenn Sie den-Operator **`new`** ohne zusätzliche Argumente verwenden und mit den Optionen [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)oder/EHa kompilieren, um die Ausnahmebehandlung zu aktivieren, generiert der Compiler Code, um den Operator aufzurufen, **`delete`** Wenn der Konstruktor eine Ausnahme auslöst.

Wenn Sie das Platzierungs Formular des Operators verwenden **`new`** (das Formular mit Argumenten zusätzlich zur Größe der Zuordnung) und der Konstruktor des Objekts eine Ausnahme auslöst, generiert der Compiler weiterhin Code, um Operator aufzurufen. Dies geschieht **`delete`** jedoch nur, wenn eine Platzierungs Form des Operators vorhanden ist, **`delete`** die mit der Platzierungs Form des Operators übereinstimmt, **`new`** der den Arbeitsspeicher zugewiesen hat. Beispiel:

```cpp
// C4291.cpp
// compile with: /EHsc /W1
#include <malloc.h>

class CList
{
public:
   CList(int)
   {
      throw "Fail!";
   }
};

void* operator new(size_t size, char* pszFilename, int nLine)
{
   return malloc(size);
}

int main(void)
{
   try
   {
      // This will call ::operator new(unsigned int) to allocate heap
      // memory. Heap memory pointed to by pList1 will automatically be
      // deallocated by a call to ::operator delete(void*) when
      // CList::CList(int) throws an exception.
      CList* pList1 = new CList(10);
   }
   catch (...)
   {
   }

   try
   {
      // This will call the overloaded ::operator new(size_t, char*, int)
      // to allocate heap memory. When CList::CList(int) throws an
      // exception, ::operator delete(void*, char*, int) should be called
      // to deallocate the memory pointed to by pList2. Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291
   }
   catch (...)
   {
   }
}
```

Im obigen Beispiel wird die Warnung C4291 generiert, da keine Platzierungs Form von Operator definiert wurde, die mit **`delete`** der Platzierungs Form des Operators übereinstimmt **`new`** . Um das Problem zu beheben, fügen Sie den folgenden Code oberhalb von **Main**ein. Beachten Sie, dass alle überladenen Operator **`delete`** Funktionsparameter mit denen des überladenen Operators **`new`** , mit Ausnahme des ersten Parameters, identisch sind.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
