---
title: Friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 20116674feffaa5b4bbddf707dd3a4d0c1d9ad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364440"
---
# <a name="friend-c"></a>Friend (C++)

Unter bestimmten Umständen ist es bequemer, Funktionen, die nicht Mitglieder einer Klasse sind, oder allen Membern in einer separaten Klasse Zugriff auf Memberebene zu gewähren. Nur der Klassenimplementierer kann seine „Friends“ deklarieren. Eine Funkion oder Klasse kann sich nicht selbst als „Friend“ einer Klasse deklarieren. Verwenden Sie in einer **friend** Klassendefinition das friend-Schlüsselwort und den Namen einer Nicht-Member-Funktion oder einer anderen Klasse, um ihr Zugriff auf die privaten und geschützten Member Ihrer Klasse zu gewähren. In einer Vorlagendefinition kann ein Typparameter als Freund deklariert werden.

## <a name="syntax"></a>Syntax

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Friend-Deklarationen

Wenn Sie eine Friend-Funktion deklarieren, die zuvor nicht deklariert wurde, wird diese Funktion in den einschließenden Nichtklassenbereich exportiert.

Funktionen, die in einer Friend-Deklaration deklariert wurden, werden so behandelt, als ob sie mit dem schlüsselwortsuchenden Schlüsselwort **extern** deklariert worden wären. Weitere Informationen finden Sie unter [extern](extern-cpp.md).

Obwohl Funktionen mit globalem Gültigkeitsbereich als Friends vor ihrem Prototypen deklariert werden können, können Memberfunktionen nicht als Friends vor der Darstellung ihrer vollständigen Klassendeklaration deklariert werden. Der folgende Code zeigt, warum hierbei ein Fehler auftritt:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

Im vorhergehenden Beispiel wird der Klassenname `ForwardDeclared` in den Bereich eingegeben. Die vollständige Deklaration (besonders der Teil, in der die Funktion als `IsAFriend` deklariert wird) ist jedoch nicht bekannt. Daher generiert die Friend-Deklaration in der Klasse **friend** `HasFriends` einen Fehler.

Ab C++11 gibt es zwei Formen von Freunddeklarationen für eine Klasse:

```cpp
friend class F;
friend F;
```

Das erste Formular führt eine neue Klasse F ein, wenn im innersten Namespace keine vorhandene Klasse mit diesem Namen gefunden wurde. **C++11**: Das zweite Formular führt keine neue Klasse ein. Sie kann verwendet werden, wenn die Klasse bereits deklariert wurde, und sie muss beim Deklarieren eines Vorlagentypparameters oder eines typedef als Freund verwendet werden.

Verwenden `class friend F` Sie diese Verwendung, wenn der referenzierte Typ noch nicht deklariert wurde:

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

Bezieht `friend F` sich im folgenden `F` Beispiel auf die Klasse, die außerhalb des Bereichs von NS deklariert wird.

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

Verwenden `friend F` Sie diese Verwendung, um einen Vorlagenparameter als Freund zu deklarieren:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Verwenden `friend F` Sie diese Form, um eine typedef als Freund zu deklarieren:

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Um zwei befreundete Klassen zu deklarieren, muss die gesamte zweite Klasse als Friend der ersten Klasse angegeben werden. Diese Einschränkung besteht, weil der Compiler über genügend Informationen verfügt, um einzelne Friend-Funktionen nur an der Stelle zu deklarieren, in der die zweite Klasse deklariert wird.

> [!NOTE]
> Obwohl die gesamte zweite Klasse Friend der ersten Klasse sein muss, können Sie auswählen, welche Funktionen in der ersten Klasse Friends der zweiten Klasse sind.

## <a name="friend-functions"></a>friend-Funktionen

Eine **Friend-Funktion** ist eine Funktion, die kein Mitglied einer Klasse ist, aber Zugriff auf die privaten und geschützten Member der Klasse hat. Friend-Funktionen gelten nicht als Klassenmember. Es sind normale externe Funktionen, denen spezielle Zugriffsrechte gewährt werden. Freunde befinden sich nicht im Bereich der Klasse und werden nicht mit den Memberauswahloperatoren (**aufgerufen.** und**>**- ) es sei denn, sie sind Mitglieder einer anderen Klasse. Eine **Friend-Funktion** wird von der Klasse deklariert, die Zugriff gewährt. Die **Friend-Deklaration** kann an einer beliebigen Stelle in der Klassendeklaration platziert werden. Sie wird nicht durch die Schlüsselwörter der Zugriffssteuerung beeinflusst.

Das folgende Beispiel zeigt eine `Point`-Klasse und die Friend-Funktion `ChangePrivate`. Die **Friend-Funktion** hat Zugriff auf `Point` das private Datenmember des Objekts, das sie als Parameter empfängt.

```cpp
// friend_functions.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
    friend void ChangePrivate( Point & );
public:
    Point( void ) : m_i(0) {}
    void PrintPrivate( void ){cout << m_i << endl; }

private:
    int m_i;
};

void ChangePrivate ( Point &i ) { i.m_i++; }

int main()
{
   Point sPoint;
   sPoint.PrintPrivate();
   ChangePrivate(sPoint);
   sPoint.PrintPrivate();
// Output: 0
           1
}
```

## <a name="class-members-as-friends"></a>Klassenmember als „Friends“

Klassenmemberfunktionen können in anderen Klassen als "Friends" deklariert werden. Betrachten Sie das folgenden Beispiel:

```cpp
// classes_as_friends1.cpp
// compile with: /c
class B;

class A {
public:
   int Func1( B& b );

private:
   int Func2( B& b );
};

class B {
private:
   int _b;

   // A::Func1 is a friend function to class B
   // so A::Func1 has access to all members of B
   friend int A::Func1( B& );
};

int A::Func1( B& b ) { return b._b; }   // OK
int A::Func2( B& b ) { return b._b; }   // C2248
```

Im vorherigen Beispiel wird nur der Funktion `A::Func1( B& )` Friend-Zugriff auf die `B`-Klasse gewährt. Daher ist der Zugriff `_b` auf `Func1` den `A` privaten Member `Func2`in der Klasse korrekt, aber nicht in .

Bei der `friend`-Klasse handelt es sich um eine Klasse, deren sämtliche Memberfunktionen Friend-Funktionen einer Klasse sind, d. h. deren Memberfunktionen Zugriff auf die privaten und geschützten Member der anderen Klasse haben. Angenommen, die `friend`-Deklaration in der `B`-Klasse lautete:

```cpp
friend class A;
```

In diesem Fall wären allen Memberfunktionen in der `A`-Klasse Friend-Zugriff auf die `B`-Klasse gewährt worden. Der folgende Code ist ein Beispiel für eine Friend-Klasse:

```cpp
// classes_as_friends2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class YourClass {
friend class YourOtherClass;  // Declare a friend class
public:
   YourClass() : topSecret(0){}
   void printMember() { cout << topSecret << endl; }
private:
   int topSecret;
};

class YourOtherClass {
public:
   void change( YourClass& yc, int x ){yc.topSecret = x;}
};

int main() {
   YourClass yc1;
   YourOtherClass yoc1;
   yc1.printMember();
   yoc1.change( yc1, 5 );
   yc1.printMember();
}
```

Die Friendship-Klasse wurde nicht gegenseitig festgelegt, es sei denn, sie wurde explizit als solche angegeben. Im obigen Beispiel können Memberfunktionen von `YourClass` nicht auf die privaten Member von `YourOtherClass` zugreifen.

Ein verwalteter Typ (in C++/CLI) kann keine Friend-Funktionen, Freundesklassen oder Freundesschnittstellen haben.

Die Friendship-Klasse wird nicht vererbt. Dies bedeutet, dass die von `YourOtherClass` abgeleiteten Klassen nicht auf die privaten Member von `YourClass` zugreifen können. Die Friendship-Klasse ist nicht transitiv. Daher können Klassen, die Friends von `YourOtherClass` sind, nicht auf die privaten Member von `YourClass` zugreifen.

Die folgende Abbildung zeigt vier Klassendeklarationen: `Base`, `Derived`, `aFriend` und `anotherFriend`. Nur die `aFriend`-Klasse hat direkten Zugriff auf die privaten Member der `Base`-Klassendeklaration (und auf alle Member, die `Base` möglicherweise geerbt hat).

![Auswirkungen von Friend-Beziehungen](../cpp/media/vc38v41.gif "Auswirkungen von Friend-Beziehungen") <br/>
Auswirkungen von Friend-Beziehungen

## <a name="inline-friend-definitions"></a>Inline-Friend-Definitionen

Friend-Funktionen können innerhalb von Klassendeklarationen definiert werden (ein Funktionstext). Diese Funktionen sind Inlinefunktionen und wie Memberinlinefunktionen verhalten sie sich, als wären sie sofort definiert worden, nachdem alle Klassenmember angezeigt wurden, jedoch bevor der Klassengültigkeitsbereich geschlossen wurde (Ende der Klassendeklaration). Friend-Funktionen, die innerhalb von Klassendeklarationen definiert sind, befinden sich im Bereich der einschließenden Klasse.

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)
