---
title: Lvalue-verweisdedeklarator:&amp;
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- reference operator
- '& operator [C++], reference operator'
ms.assetid: edf0513d-3dcc-4663-b276-1269795dda51
ms.openlocfilehash: 30dd6ba9cb91395f72124cad71908a4e6bcdf7dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225981"
---
# <a name="lvalue-reference-declarator-amp"></a>Lvalue-verweisdedeklarator:&amp;

Enthält die Adresse eines Objekts, verhält sich jedoch syntaktisch wie ein Objekt.

## <a name="syntax"></a>Syntax

```
type-id & cast-expression
```

## <a name="remarks"></a>Bemerkungen

Sie können sich einen lvalue-Verweis als einen anderen Namen für ein Objekt vorstellen. Eine lvalue-Verweisdeklaration enthält eine optionale Liste von Bezeichnern, gefolgt von einem Verweisdeklarator. Ein Verweis muss initialisiert werden und kann nicht geändert werden.

Jedes Objekt, dessen Adresse in einen angegebenen Zeigertyp konvertiert werden kann, kann auch in den ähnlichen Referenztyp konvertiert werden. Beispielsweise kann jedes Objekt, dessen Adresse in den Typ `char *` konvertiert werden kann, auch in den Typ `char &` konvertiert werden.

Verwechseln Sie keine Verweis Deklarationen mit der Verwendung des [address-of-Operators](../cpp/address-of-operator-amp.md). Wenn dem `&` *Bezeichner* ein Typ vorangestellt ist, z **`int`** **`char`** . b. oder, wird der *Bezeichner* als Verweis auf den Typ deklariert. Wenn dem `&` *Bezeichner* kein Typ vorangestellt ist, ist die Verwendung der des address-of-Operators.

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt den Verweisdeklarator, indem ein `Person`-Objekt und ein Verweis auf dieses Objekt deklariert wird. Da `rFriend` ein Verweis auf `myFriend` ist, ändert die Aktualisierung einer der Variablen das gleiche Objekt.

```cpp
// reference_declarator.cpp
// compile with: /EHsc
// Demonstrates the reference declarator.
#include <iostream>
using namespace std;

struct Person
{
    char* Name;
    short Age;
};

int main()
{
   // Declare a Person object.
   Person myFriend;

   // Declare a reference to the Person object.
   Person& rFriend = myFriend;

   // Set the fields of the Person object.
   // Updating either variable changes the same object.
   myFriend.Name = "Bill";
   rFriend.Age = 40;

   // Print the fields of the Person object to the console.
   cout << rFriend.Name << " is " << myFriend.Age << endl;
}
```

```Output
Bill is 40
```

## <a name="see-also"></a>Siehe auch

[Referenzen](../cpp/references-cpp.md)<br/>
[Verweistyp-Funktionsargumente](../cpp/reference-type-function-arguments.md)<br/>
[Verweistyp-Funktions Rückgabe](../cpp/reference-type-function-returns.md)<br/>
[Verweise auf Zeiger](../cpp/references-to-pointers.md)
