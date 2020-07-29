---
title: Indizierung
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 2573f30b2dfee20d12afea2a1072bbdcef46228b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231077"
---
# <a name="subscripting"></a>Indizierung

Der Index Operator (**[]**) wird, wie der Funktions Aufrufoperator, als binärer Operator betrachtet. Der Indexoperator muss eine nicht statische Memberfunktion sein, die ein einzelnes Argument akzeptiert. Dieses Argument kann einen beliebigen Typ aufweisen und legt den gewünschten Arrayindex fest.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie ein Vektor vom Typ erstellt wird, der die über **`int`** Prüfung von Begrenzungen implementiert:

```cpp
// subscripting.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class IntVector {
public:
   IntVector( int cElements );
   ~IntVector() { delete [] _iElements; }
   int& operator[](int nSubscript);
private:
   int *_iElements;
   int _iUpperBound;
};

// Construct an IntVector.
IntVector::IntVector( int cElements ) {
   _iElements = new int[cElements];
   _iUpperBound = cElements;
}

// Subscript operator for IntVector.
int& IntVector::operator[](int nSubscript) {
   static int iErr = -1;

   if( nSubscript >= 0 && nSubscript < _iUpperBound )
      return _iElements[nSubscript];
   else {
      clog << "Array bounds violation." << endl;
      return iErr;
   }
}

// Test the IntVector class.
int main() {
   IntVector v( 10 );
   int i;

   for( i = 0; i <= 10; ++i )
      v[i] = i;

   v[3] = v[9];

   for ( i = 0; i <= 10; ++i )
      cout << "Element: [" << i << "] = " << v[i] << endl;
}
```

```Output
Array bounds violation.
Element: [0] = 0
Element: [1] = 1
Element: [2] = 2
Element: [3] = 9
Element: [4] = 4
Element: [5] = 5
Element: [6] = 6
Element: [7] = 7
Element: [8] = 8
Element: [9] = 9
Array bounds violation.
Element: [10] = 10
```

## <a name="comments"></a>Kommentare

Wenn `i` im vorangehenden Programm 10 erreicht, erkennt der **Operator []** , dass ein Index außerhalb des gültigen Bereichs verwendet wird, und gibt eine Fehlermeldung aus.

Beachten Sie, dass der Funktions **Operator []** einen Verweistyp zurückgibt. Dadurch wird sie zu einem L-Wert, und Sie können auf beiden Seiten von Zuweisungsoperatoren indizierte Ausdrücke verwenden.

## <a name="see-also"></a>Siehe auch

[Operator Überladung](../cpp/operator-overloading.md)
