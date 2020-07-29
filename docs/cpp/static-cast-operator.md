---
title: static_cast-Operator
ms.date: 11/04/2016
f1_keywords:
- static_cast_cpp
helpviewer_keywords:
- static_cast keyword [C++]
ms.assetid: 1f7c0c1c-b288-476c-89d6-0e2ceda5c293
ms.openlocfilehash: 8551d41417647ee4f759e2547e2c1909c59d78cd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213202"
---
# <a name="static_cast-operator"></a>static_cast-Operator

Konvertiert einen *Ausdruck* in den Typ *-ID-Typ,* der nur auf den Typen basiert, die im Ausdruck vorhanden sind.

## <a name="syntax"></a>Syntax

```
static_cast <type-id> ( expression )
```

## <a name="remarks"></a>Bemerkungen

Im Standard-C++ wird zur Laufzeit keine Typüberprüfung durchgeführt, um die Sicherheit der Konvertierung zu gewährleisten. In C++/CX wird eine Überprüfung der Kompilierzeit und der Laufzeit durchgeführt. Weitere Informationen finden Sie unter [Umwandlung](casting.md)definiert sind.

Der- **`static_cast`** Operator kann für Vorgänge verwendet werden, z. b. die Typumwandlung eines Zeigers auf eine Basisklasse in einen Zeiger auf eine abgeleitete Klasse. Solche Konvertierungen sind nicht immer sicher.

Im Allgemeinen verwenden Sie, wenn Sie numerische Datentypen, z. b. Enumerationwerte, in eine Gleit Komma Zahl **`static_cast`** oder int konvertieren möchten, und Sie sind sicher, dass die Datentypen an der Konvertierung beteiligt sind. **`static_cast`** Konvertierungen sind nicht so sicher wie **`dynamic_cast`** Konvertierungen, da **`static_cast`** keine Lauf Zeittyp Überprüfung durchführt **`dynamic_cast`** . Ein-Wert **`dynamic_cast`** für einen mehrdeutigen Zeiger schlägt fehl, während ein **`static_cast`** zurückgibt, als wäre nichts falsch gewesen. Dies kann gefährlich sein. Obwohl **`dynamic_cast`** Konvertierungen sicherer sind, **`dynamic_cast`** funktioniert nur bei Zeigern oder verweisen, und die Lauf Zeittyp Überprüfung ist ein zusätzlicher Aufwand. Weitere Informationen finden Sie unter [dynamic_cast-Operator](../cpp/dynamic-cast-operator.md).

Im folgende Beispiel ist die Zeile `D* pd2 = static_cast<D*>(pb);` nicht sicher, da `D` Felder und Methoden aufweisen kann, die nicht in `B` enthalten sind. Allerdings ist die Zeile `B* pb2 = static_cast<B*>(pd);` eine sichere Konvertierung, da `D` immer alle Elemente von `B` enthält.

```cpp
// static_cast_Operator.cpp
// compile with: /LD
class B {};

class D : public B {};

void f(B* pb, D* pd) {
   D* pd2 = static_cast<D*>(pb);   // Not safe, D can have fields
                                   // and methods that are not in B.

   B* pb2 = static_cast<B*>(pd);   // Safe conversion, D always
                                   // contains all of B.
}
```

Im Gegensatz zu [dynamic_cast](../cpp/dynamic-cast-operator.md)wird bei der Konvertierung von keine Lauf Zeit Überprüfung **`static_cast`** durchgeführt `pb` . Das Objekt, auf das mit `pb` gezeigt wird, ist möglicherweise kein Objekt vom Typ `D`. In diesem Fall kann die Verwendung von `*pd2` zu schwerwiegenden Fehlern führen. Beispielsweise kann das Aufrufen einer Funktion, die ein Member der `D`-Klasse, aber nicht der `B`-Klasse ist, eine Zugriffsverletzung verursachen.

Die **`dynamic_cast`** **`static_cast`** Operatoren und verschieben einen Zeiger in eine Klassenhierarchie. Abhängig **`static_cast`** von den Informationen, die in der CAST-Anweisung bereitgestellt werden, ist dies jedoch nicht möglich. Beispiel:

```cpp
// static_cast_Operator_2.cpp
// compile with: /LD /GR
class B {
public:
   virtual void Test(){}
};
class D : public B {};

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);
   D* pd2 = static_cast<D*>(pb);
}
```

Wenn `pb` tatsächlich auf ein Objekt vom Typ `D` zeigt, erhalten `pd1` und `pd2` den gleichen Wert. Sie rufen außerdem den gleichen Wert ab, wenn `pb == 0`.

Wenn `pb` auf ein Objekt vom Typ `B` und nicht auf die gesamte `D` Klasse verweist, **`dynamic_cast`** weiß, dass ausreichend ist, um 0 (null) zurückzugeben. Allerdings **`static_cast`** beruht auf der-Aussage des Programmierers, die `pb` auf ein Objekt vom Typ zeigt `D` und einfach einen Zeiger auf dieses vermeintliche Objekt zurückgibt `D` .

Folglich **`static_cast`** kann die Umkehrung impliziter Konvertierungen durchführen. in diesem Fall sind die Ergebnisse nicht definiert. Es bleibt dem Programmierer überlassen, zu überprüfen, ob die Ergebnisse einer **`static_cast`** Konvertierung sicher sind.

Dieses Verhalten gilt auch für andere Typen als Klassentypen. Beispielsweise **`static_cast`** kann verwendet werden, um von einer int in eine zu konvertieren **`char`** . Allerdings verfügt das resultierende **`char`** möglicherweise nicht über genügend Bits, um den gesamten Wert zu speichern **`int`** . Auch hier bleibt der Programmierer dabei, zu überprüfen, ob die Ergebnisse einer **`static_cast`** Konvertierung sicher sind.

Der- **`static_cast`** Operator kann auch verwendet werden, um eine implizite Konvertierung auszuführen, einschließlich Standard Konvertierungen und benutzerdefinierter Konvertierungen. Beispiel:

```cpp
// static_cast_Operator_3.cpp
// compile with: /LD /GR
typedef unsigned char BYTE;

void f() {
   char ch;
   int i = 65;
   float f = 2.5;
   double dbl;

   ch = static_cast<char>(i);   // int to char
   dbl = static_cast<double>(f);   // float to double
   i = static_cast<BYTE>(ch);
}
```

Der **`static_cast`** Operator kann einen ganzzahligen Wert explizit in einen Enumerationstyp konvertieren. Wenn der Wert des ganzzahligen Typs nicht innerhalb des Bereichs von Enumerationswerten liegt, ist der resultierende Enumerationswert nicht definiert.

Der- **`static_cast`** Operator konvertiert einen NULL-Zeiger Wert in den NULL-Zeiger Wert des Zieltyps.

Jeder Ausdruck kann vom-Operator explizit in den Typ "void" konvertiert werden **`static_cast`** . Der void-Zieltyp kann optional das- **`const`** ,-oder-Attribut enthalten **`volatile`** **`__unaligned`** .

Der **`static_cast`** Operator kann die **`const`** **`volatile`** Attribute, oder nicht umwandeln **`__unaligned`** . Weitere Informationen zum Entfernen dieser Attribute finden Sie unter [const_cast-Operator](../cpp/const-cast-operator.md) .

**C++/CLI:** Aufgrund der Gefahr, dass deaktivierte Umwandlungen zusätzlich zu einer Garbage Collector verschoben werden, sollte die Verwendung von **`static_cast`** nur in Leistungs kritischem Code erfolgen, wenn Sie sicher sind, dass Sie ordnungsgemäß funktioniert. Wenn Sie **`static_cast`** im Releasemodus verwenden müssen, ersetzen Sie ihn durch [safe_cast](../extensions/safe-cast-cpp-component-extensions.md) in ihren Debugbuilds, um den Erfolg sicherzustellen.

## <a name="see-also"></a>Weitere Informationen

[Umwandlungs Operatoren](../cpp/casting-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)
