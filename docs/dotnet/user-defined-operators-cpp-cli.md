---
title: Benutzerdefinierte Operatoren (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- user-defined operators under /clr
ms.assetid: 42f93b4a-6de4-4e34-b07b-5a62ac014f2c
ms.openlocfilehash: ee5aa122983a315e55884c643a9b7894f075e260
ms.sourcegitcommit: 43cee7a0d41a062661229043c2f7cbc6ace17fa3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "92008951"
---
# <a name="user-defined-operators-ccli"></a>Benutzerdefinierte Operatoren (C++/CLI)

Benutzerdefinierte Operatoren für verwaltete Typen sind als statische Member oder Instanzmember oder im globalen Gültigkeitsbereich zulässig. Allerdings sind nur statische Operatoren über Metadaten für Clients zugänglich, die in einer anderen Sprache als Visual C++ geschrieben sind.

In einem Verweistyp muss einer der Parameter eines statischen benutzerdefinierten Operators einer der folgenden Parameter sein:

- Ein Handle ( `type` ^) für eine Instanz des einschließenden Typs.

- Verweistyp Dereferenzierung ( `type` ^& oder Typ ^%) an ein Handle für eine Instanz des einschließenden Typs.

Bei einem Werttyp muss einer der Parameter eines statischen benutzerdefinierten Operators einer der folgenden Parameter sein:

- Desselben Typs wie der einschließende Werttyp.

- Eine Zeigertyp Dereferenzierung ( `type` ^) zum einschließenden Typ.

- Eine Verweistyp Dereferenzierung ( `type` % oder `type`&) zum einschließenden Typ.

- Eine Verweistyp Dereferenzierung ( `type` ^% oder `type` ^&) zum handle.

Sie können die folgenden Operatoren definieren:

|Betreiber|Unäre/binäre Formulare?|
|--------------|--------------------------|
|!|Unär|
|!=|Binary|
|%|Binary|
|&|Unär und binär|
|&&|Binary|
|*|Unär und binär|
|+|Unär und binär|
|++|Unär|
|,|Binary|
|-|Unär und binär|
|--|Unär|
|->|Unär|
|/|Binary|
|<|Binary|
|<<|Binary|
|\<=|Binary|
|=|Binary|
|==|Binary|
|>|Binary|
|>=|Binary|
|>>|Binary|
|^|Binary|
|false|Unär|
|true|Unär|
|&#124;|Binary|
|&#124;&#124;|Binary|
|~|Unär|

## <a name="example-user-defined-operators"></a>Beispiel: benutzerdefinierte Operatoren

```cpp
// mcppv2_user-defined_operators.cpp
// compile with: /clr
using namespace System;
public ref struct X {
   X(int i) : m_i(i) {}
   X() {}

   int m_i;

   // static, binary, user-defined operator
   static X ^ operator + (X^ me, int i) {
      return (gcnew X(me -> m_i + i));
   }

   // instance, binary, user-defined operator
   X^ operator -( int i ) {
      return gcnew X(this->m_i - i);
   }

   // instance, unary, user-defined pre-increment operator
   X^ operator ++() {
      return gcnew X(this->m_i++);
   }

   // instance, unary, user-defined post-increment operator
   X^ operator ++(int i) {
      return gcnew X(this->m_i++);
   }

   // static, unary user-defined pre- and post-increment operator
   static X^ operator-- (X^ me) {
      return (gcnew X(me -> m_i - 1));
   }
};

int main() {
   X ^hX = gcnew X(-5);
   System::Console::WriteLine(hX -> m_i);

   hX = hX + 1;
   System::Console::WriteLine(hX -> m_i);

   hX = hX - (-1);
   System::Console::WriteLine(hX -> m_i);

   ++hX;
   System::Console::WriteLine(hX -> m_i);

   hX++;
   System::Console::WriteLine(hX -> m_i);

   hX--;
   System::Console::WriteLine(hX -> m_i);

   --hX;
   System::Console::WriteLine(hX -> m_i);
}
```

```Output
-5
-4
-3
-2
-1
-2
-3
```

## <a name="example-operator-synthesis"></a>Beispiel: Operator Synthese

Im folgenden Beispiel wird die-Operator Synthese veranschaulicht, die nur verfügbar ist, wenn Sie **/CLR** für die Kompilierung verwenden. Die Operator Synthese erstellt die Zuweisungs Form eines binären Operators, sofern nicht definiert, wobei die linke Seite des Zuweisungs Operators einen CLR-Typ aufweist.

```cpp
// mcppv2_user-defined_operators_2.cpp
// compile with: /clr
ref struct A {
   A(int n) : m_n(n) {};
   static A^ operator + (A^ r1, A^ r2) {
      return gcnew A( r1->m_n + r2->m_n);
   };
   int m_n;
};

int main() {
   A^ a1 = gcnew A(10);
   A^ a2 = gcnew A(20);

   a1 += a2;   // a1 = a1 + a2   += not defined in source
   System::Console::WriteLine(a1->m_n);
}
```

```Output
30
```

## <a name="see-also"></a>Siehe auch

[Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md)
