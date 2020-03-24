---
title: C-stilartige Umwandlungen mit -clr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
ms.openlocfilehash: 2b7e492c62047e3b38224637f842d8a7fcbae84f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172593"
---
# <a name="c-style-casts-with-clr-ccli"></a>C-stilartige Umwandlungen mit /clr (C++/CLI)

Das folgende Thema gilt nur für die Common Language Runtime.

Bei Verwendung mit CLR-Typen versucht der Compiler C-stilartige Umwandlungen einer der unten aufgeführten Umwandlungen zuzuordnen, und zwar in der folgenden Reihenfolge:

1. const_cast

2. safe_cast

3. safe_cast plus const_cast

4. static_cast

5. static_cast plus const_cast

Wenn keine der oben aufgeführten Umwandlungen gültig ist und der Typ des Ausdrucks sowie der Zieltyp CLR-Verweistypen sind, wird eine C-stilartige Umwandlung (Castclass-MSIL-Anweisung) einer Laufzeitüberprüfung zugeordnet. Andernfalls wird eine C-stilartige Umwandlung als ungültig betrachtet, und der Compiler gibt einen Fehler aus.

## <a name="remarks"></a>Bemerkungen

Eine C-stilartige Umwandlung wird nicht empfohlen. Verwenden Sie beim Kompilieren mit [/clr (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md)[safe_cast](safe-cast-cpp-component-extensions.md).

Das folgende Beispiel zeigt eine C-stilartige Umwandlung, die zu **const_cast** zuordnet.

```cpp
// cstyle_casts_1.cpp
// compile with: /clr
using namespace System;

ref struct R {};
int main() {
   const R^ constrefR = gcnew R();
   R^ nonconstR = (R^)(constrefR);
}
```

Das folgende Beispiel zeigt eine C-stilartige Umwandlung, die zu **safe_cast** zuordnet.

```cpp
// cstyle_casts_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Object ^ o = "hello";
   String ^ s = (String^)o;
}
```

Das folgende Beispiel zeigt eine C-stilartige Umwandlung, die zu **safe_cast** plus **const_cast** zuordnet.

```cpp
// cstyle_casts_3.cpp
// compile with: /clr
using namespace System;

ref struct R {};
ref struct R2 : public R {};

int main() {
   const R^ constR2 = gcnew R2();
   try {
   R2^ b2DR = (R2^)(constR2);
   }
   catch(InvalidCastException^ e) {
      System::Console::WriteLine("Invalid Exception");
   }
}
```

Das folgende Beispiel zeigt eine C-stilartige Umwandlung, die zu **static_cast** zuordnet.

```cpp
// cstyle_casts_4.cpp
// compile with: /clr
using namespace System;

struct N1 {};
struct N2 {
   operator N1() {
      return N1();
   }
};

int main() {
   N2 n2;
   N1 n1 ;
   n1 = (N1)n2;
}
```

Das folgende Beispiel zeigt eine C-stilartige Umwandlung, die zu **static_cast** plus **const_cast** zuordnet.

```cpp
// cstyle_casts_5.cpp
// compile with: /clr
using namespace System;
struct N1 {};

struct N2 {
   operator const N1*() {
      static const N1 n1;
      return &n1;
   }
};

int main() {
   N2 n2;
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast
}
```

Das folgende Beispiel zeigt eine C-stilartige Umwandlung, die zu einer Laufzeitüberprüfung zuordnet.

```cpp
// cstyle_casts_6.cpp
// compile with: /clr
using namespace System;

ref class R1 {};
ref class R2 {};

int main() {
   R1^ r  = gcnew R1();
   try {
      R2^ rr = ( R2^)(r);
   }
   catch(System::InvalidCastException^ e) {
      Console::WriteLine("Caught expected exception");
   }
}
```

Das folgende Beispiel zeigt eine ungültige C-stilartige Umwandlung, die dazu führt, dass der Compiler einen Fehler ausgibt.

```cpp
// cstyle_casts_7.cpp
// compile with: /clr
using namespace System;
int main() {
   String^s = S"hello";
   int i = (int)s;   // C2440
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

Compileroption: `/clr`

## <a name="see-also"></a>Weitere Informationen

[Komponentenerweiterungen für .NET und UWP](component-extensions-for-runtime-platforms.md)
