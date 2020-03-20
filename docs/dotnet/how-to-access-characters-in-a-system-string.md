---
title: 'Gewusst wie: Zugriff auf Zeichen in einem System::String'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: 3c44c5e7651bb1c5b4c28654b896cbe64bd5bec7
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545342"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Gewusst wie: Zugriff auf Zeichen in einem System::String

Sie können auf Zeichen eines <xref:System.String> Objekts zugreifen, um Hochleistungs Aufrufe von nicht verwalteten Funktionen zu erhalten, die `wchar_t*` Zeichen folgen verwenden. Die-Methode ergibt einen inneren Zeiger auf das erste Zeichen des <xref:System.String> Objekts. Dieser Zeiger kann direkt manipuliert oder fixiert und an eine Funktion übermittelt werden, die eine normale `wchar_t` Zeichenfolge erwartet.

## <a name="example"></a>Beispiel

`PtrToStringChars` gibt eine <xref:System.Char>zurück, bei der es sich um einen inneren Zeiger handelt (wird auch als `byref`bezeichnet). Dies unterliegt der Garbage Collection. Sie müssen diesen Zeiger nicht anheften, es sei denn, Sie übergeben ihn an eine native Funktion.

Betrachten Sie folgenden Code.  Das anhechern ist nicht erforderlich, da `ppchar` ein innerer Zeiger ist, und wenn die Garbage Collector die Zeichenfolge verschiebt, auf die Sie verweist, wird auch `ppchar`aktualisiert. Ohne einen [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)funktioniert der Code und führt nicht zu Leistungseinbußen, die durch anhenung verursacht werden.

Wenn Sie `ppchar` an eine native Funktion übergeben, muss Sie ein angeheftender Zeiger sein. der Garbage Collector kann keine Zeiger auf den nicht verwalteten Stapel Rahmen aktualisieren.

```cpp
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

## <a name="example"></a>Beispiel

In diesem Beispiel wird gezeigt, wo anheften benötigt wird.

```cpp
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

## <a name="example"></a>Beispiel

Ein innerer Zeiger verfügt über alle Eigenschaften eines systemeigenen C++ Zeigers. Beispielsweise können Sie damit eine verknüpfte Datenstruktur durchlaufen und Einfügungen und Löschungen nur mit einem Zeiger ausführen:

```cpp
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>Siehe auch

[Verwenden von C++-Interop (implizites PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
