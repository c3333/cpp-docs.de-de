---
title: Compilerwarnung (Stufe 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754856"
---
# <a name="compiler-warning-level-1-c4291"></a>Compilerwarnung (Stufe 1) C4291

'Deklaration': kein übereinstimmender Operatorlöschen gefunden; Speicher wird nicht freigegeben, wenn die Initialisierung eine Ausnahme auslöst

Es wird eine [neue](../../cpp/new-operator-cpp.md) Platzierung verwendet, für die es keine Platzierung [löschen](../../cpp/delete-operator-cpp.md)gibt.

Wenn Speicher für ein Objekt mit dem Operator **new**reserviert wird, wird der Konstruktor des Objekts aufgerufen. Wenn der Konstruktor eine Ausnahme auslöst, sollte der für das Objekt reservierte Speicher verteilt werden. Dies kann nur geschehen, wenn eine **Operatorlöschfunktion** vorhanden ist, die mit dem Operator **new**übereinstimmt.

Wenn Sie den Operator **new** ohne zusätzliche Argumente verwenden und mit den Optionen [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md)oder /EHa kompilieren, um die Ausnahmebehandlung zu aktivieren, generiert der Compiler Code zum **Aufrufen von Operatordelete,** wenn der Konstruktor eine Ausnahme auslöst.

Wenn Sie das Platzierungsformular des **neuen** Operators (das Formular mit Argumenten zusätzlich zur Größe der Zuordnung) verwenden und der Konstruktor des Objekts eine Ausnahme auslöst, generiert der Compiler weiterhin Code zum Aufrufen von Operator **delete**. Dies wird jedoch nur der Fall sein, wenn eine Platzierungsform des **Operatorslöschens** vorhanden ist, die mit dem Platzierungsformular des **neuen** Operators übereinstimmt, der den Speicher zugewiesen hat. Beispiel:

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

Im obigen Beispiel wird die Warnung C4291 generiert, da keine Platzierungsform für den **Operatordelete** definiert wurde, die mit der Platzierungsform des Operators **new**übereinstimmt. Um das Problem zu lösen, fügen Sie den folgenden Code über **main**ein. Beachten Sie, dass alle **überladenen Operatorlöschfunktionsparameter** mit denen des überladenen Operators **new**übereinstimmen, mit Ausnahme des ersten Parameters.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
