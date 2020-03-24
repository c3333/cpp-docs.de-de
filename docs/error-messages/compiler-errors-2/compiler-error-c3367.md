---
title: Compilerfehler C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: bedc94039f8621a93672c0dfa0cad5a54aad796e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201161"
---
# <a name="compiler-error-c3367"></a>Compilerfehler C3367

'static_member_function': Eine statische Funktion kann nicht zum Erstellen eines ungebundenen Delegaten verwendet werden.

Wenn Sie einen ungebundenen Delegaten aufrufen, müssen Sie eine Instanz eines Objekts übergeben. Da eine statische Memberfunktion über den Klassennamen aufgerufen wird, können Sie nur einen ungebundenen Delegaten mit einer Instanzmemberfunktion instanziieren.

Weitere Informationen zu ungebundenen Delegaten finden Sie unter Gewusst [wie: definieren und Verwenden vonC++Delegaten (/CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C3367 generiert:

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```
