---
title: Compilerfehler C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: b2c5737a4442761cbaa84b532907e579eddb423d
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686064"
---
# <a name="compiler-error-c3904"></a>Compilerfehler C3904

' Property_accessor ': Es müssen zahlen Parameter angegeben werden.

Überprüfen Sie die Anzahl der Parameter in der `get` -Methode und der- `set` Methode auf Eigenschaften Dimensionen.

- Die Anzahl der Parameter für die `get` Methode muss gleich der Anzahl der Dimensionen der Eigenschaft oder 0 (null) für nicht indizierte Eigenschaften sein.

- Die Anzahl der Parameter der- `set` Methode muss eine höhere Anzahl als die Anzahl der Dimensionen der-Eigenschaft sein.

Weitere Informationen finden Sie unter [property](../../extensions/property-cpp-component-extensions.md).

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3904 generiert.

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

Im folgenden Beispiel wird C3904 generiert.

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
