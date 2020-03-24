---
title: Compilerwarnung (Stufe 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: cd161a37683703fd67b4c682558a51121c130816
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175713"
---
# <a name="compiler-warning-level-1-c4291"></a>Compilerwarnung (Stufe 1) C4291

' Deklaration ': Es wurde kein passender Operator gelöscht gefunden. der Arbeitsspeicher wird nicht freigegeben, wenn die Initialisierung eine Ausnahme auslöst.

Eine Platzierung [New](../../cpp/new-operator-cpp.md) wird verwendet, für die kein Platzierungs [Lösch](../../cpp/delete-operator-cpp.md)Vorgang erfolgt.

Wenn Arbeitsspeicher für ein Objekt mit dem Operator **New**zugeordnet wird, wird der Konstruktor des Objekts aufgerufen. Wenn der Konstruktor eine Ausnahme auslöst, sollte der Arbeitsspeicher, der dem Objekt zugeordnet wurde, die Zuordnung aufgehoben werden. Dies ist nur möglich, wenn eine Operator **Delete** -Funktion vorhanden ist, die mit dem **New**-Operator übereinstimmt.

Wenn Sie den **New** -Operator ohne zusätzliche Argumente verwenden und mit den Optionen [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)oder/EHa kompilieren, um die Ausnahmebehandlung zu aktivieren, generiert der Compiler Code, um den Operator **Delete** aufzurufen, wenn der Konstruktor eine Ausnahme auslöst.

Wenn Sie das Platzierungs Formular des **New** -Operators verwenden (das Formular mit Argumenten zusätzlich zur Größe der Zuordnung) und der Konstruktor des Objekts eine Ausnahme auslöst, generiert der Compiler weiterhin Code, um Operator **Delete**aufzurufen. Dies ist jedoch nur der Fall, wenn eine Platzierungs Form von Operator **Delete** vorhanden ist, die mit der Platzierungs Form des Operators **New** übereinstimmt, der den Arbeitsspeicher zugewiesen hat. Beispiel:

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

Im obigen Beispiel wird die Warnung C4291 generiert, da keine Platzierungs Form von Operator **Delete** definiert wurde, die mit der Platzierungs Form von Operator **New**übereinstimmt. Um das Problem zu beheben, fügen Sie den folgenden Code oberhalb von **Main**ein. Beachten Sie, dass alle überladenen Operator **Delete** -Funktionsparameter mit denen des überladenen Operators **New**, mit Ausnahme des ersten Parameters, identisch sind.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
