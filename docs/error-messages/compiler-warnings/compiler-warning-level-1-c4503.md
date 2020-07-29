---
title: Compilerwarnung (Stufe 1) C4503
ms.date: 05/14/2018
f1_keywords:
- C4503
helpviewer_keywords:
- C4503
ms.assetid: 7c5a98ae-5b6d-41d8-b881-12d3ffd5e392
ms.openlocfilehash: 1d3af2b5629906679db46f6f669084c11a41f7ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233248"
---
# <a name="compiler-warning-level-1-c4503"></a>Compilerwarnung (Stufe 1) C4503

> '*Identifier*': die Länge des ergänzten Namens wurde überschritten, der Name wurde abgeschnitten.

## <a name="remarks"></a>Bemerkungen

Diese Compilerwarnung ist veraltet und wird nicht in Visual Studio 2017 und späteren Compilern generiert.

Der ergänzte Name war länger als die compilerbeschränkung (4096) und wurde abgeschnitten. Um diese Warnung und das Abschneiden zu vermeiden, verringern Sie die Anzahl der Argumente oder die namens Längen der verwendeten Bezeichner. Ergänzte Namen, die länger sind als das Compilerlimit, werden auf einen Hash angewendet, und es besteht keine Gefahr eines Namens Konflikts.

Wenn Sie eine ältere Version von Visual Studio verwenden, kann diese Warnung ausgegeben werden, wenn Ihr Code Vorlagen enthält, die sich wiederholt auf Vorlagen spezialisiert haben. Beispielsweise eine Zuordnung von Maps (aus der C++-Standard Bibliothek). In diesem Fall können Sie Typedefs einen Typ (z. b. einen **`struct`** ) erstellen, der die Zuordnung enthält.

Möglicherweise entscheiden Sie sich jedoch, den Code nicht neu zu strukturieren.  Es ist möglich, eine Anwendung zu senden, die C4503 generiert. Wenn Sie jedoch Verknüpfungs Zeitfehler für ein abgeschnittenes Symbol erhalten, kann es schwieriger sein, den Typ des Symbols im Fehler zu bestimmen. Das Debuggen kann auch schwieriger sein. der Debugger hat möglicherweise die Zuordnung des Symbol namens zu dem Typnamen möglicherweise schwierig. Der abgeschnittene Name ist jedoch nicht von der Richtigkeit des Programms betroffen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden C4503-Compilern vor Visual Studio 2017 generiert:

```cpp
// C4503.cpp
// compile with: /W1 /EHsc /c
// C4503 expected
#include <string>
#include <map>

class Field{};

typedef std::map<std::string, Field> Screen;
typedef std::map<std::string, Screen> WebApp;
typedef std::map<std::string, WebApp> WebAppTest;
typedef std::map<std::string, WebAppTest> Hello;
Hello MyWAT;
```

Dieses Beispiel zeigt eine Möglichkeit, Ihren Code umzuschreiben, um C4503 aufzulösen:

```cpp
// C4503b.cpp
// compile with: /W1 /EHsc /c
#include <string>
#include <map>

class Field{};

struct Screen2 {
   std::map<std::string, Field> Element;
};

struct WebApp2 {
   std::map<std::string, Screen2> Element;
};

struct WebAppTest2 {
   std::map<std::string, WebApp2> Element;
};

struct Hello2 {
   std::map<std::string, WebAppTest2> Element;
};

Hello2 MyWAT2;
```
