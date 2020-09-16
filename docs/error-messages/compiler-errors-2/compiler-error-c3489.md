---
title: Compilerfehler C3489
ms.date: 11/04/2016
f1_keywords:
- C3489
helpviewer_keywords:
- C3489
ms.assetid: 47b58d69-459d-4499-abc7-5f0b9303d773
ms.openlocfilehash: 3b192a14a39b7c0c9d264bda8073c54f0f395924
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685765"
---
# <a name="compiler-error-c3489"></a>Compilerfehler C3489

"var" ist erforderlich, wenn der Standarderfassungsmodus ein Modus nach Wert ist.

Wenn Sie angeben, dass der Standarderfassungsmodus für einen lambda-Ausdruck ein Modus nach Wert ist, können Sie keine Variable nach Wert an die Erfassungsklausel dieses Ausdrucks übergeben.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Übergeben Sie die Variable nicht explizit an die Erfassungsklausel, oder

- geben Sie "nach Wert" nicht als Standarderfassungsmodus an, oder

- geben Sie "nach Verweis" als Standarderfassungsmodus an, oder

- übergeben Sie die Variable nach Verweis an die Erfassungsklausel. (Dies kann das Verhalten des Lambda-Ausdrucks ändern.)

## <a name="examples"></a>Beispiele

Im folgenden Beispiel wird C3489 generiert. Die Variable `n` wird in der Erfassungsklausel eines lambda-Ausdrucks, dessen Standarderfassungsmodus der Modus nach Wert ist, nach Wert angezeigt:

```cpp
// C3489a.cpp

int main()
{
   int n = 5;
   [=, n]() { return n; } (); // C3489
}
```

Im folgenden Beispiel werden vier mögliche Lösungen für den Fehler C3489 gezeigt:

```cpp
// C3489b.cpp

int main()
{
   int n = 5;

   // Possible resolution 1:
   // Do not explicitly pass n to the capture clause.
   [=]() { return n; } ();

   // Possible resolution 2:
   // Do not specify by-value as the default capture mode.
   [n]() { return n; } ();

   // Possible resolution 3:
   // Specify by-reference as the default capture mode.
   [&, n]() { return n; } ();

   // Possible resolution 4:
   // Pass n by reference to the capture clause.
   [&n]() { return n; } ();
}
```

## <a name="see-also"></a>Siehe auch

[Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md)
