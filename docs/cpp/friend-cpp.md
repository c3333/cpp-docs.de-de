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
ms.openlocfilehash: 772eada8257917a6127b15ea2e50946aebb3bc74
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227464"
---
# <a name="friend-c"></a>Friend (C++)

In einigen Fällen ist es bequemer, den Zugriff auf Element Ebene auf Funktionen zu gewähren, die keine Member einer Klasse oder auf alle Member einer separaten Klasse sind. Nur der Klassenimplementierer kann seine „Friends“ deklarieren. Eine Funkion oder Klasse kann sich nicht selbst als „Friend“ einer Klasse deklarieren. Verwenden Sie in einer Klassendefinition das **`friend`** -Schlüsselwort und den Namen einer nicht-Member-Funktion oder einer anderen Klasse, um ihm Zugriff auf die privaten und geschützten Member der Klasse zu gewähren. In einer Vorlagen Definition kann ein Typparameter als Friend deklariert werden.

## <a name="syntax"></a>Syntax

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Friend-Deklarationen

Wenn Sie eine Friend-Funktion deklarieren, die zuvor nicht deklariert wurde, wird diese Funktion in den einschließenden Nichtklassenbereich exportiert.

In einer Friend-Deklaration deklarierte Funktionen werden so behandelt, als wären Sie mit dem- **`extern`** Schlüsselwort deklariert worden. Weitere Informationen finden Sie unter [extern](extern-cpp.md).

Obwohl Funktionen mit globalem Gültigkeitsbereich als Friends vor ihrem Prototypen deklariert werden können, können Memberfunktionen nicht als Friends vor der Darstellung ihrer vollständigen Klassendeklaration deklariert werden. Der folgende Code zeigt, warum hierbei ein Fehler auftritt:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

Im vorhergehenden Beispiel wird der Klassenname `ForwardDeclared` in den Bereich eingegeben. Die vollständige Deklaration (besonders der Teil, in der die Funktion als `IsAFriend` deklariert wird) ist jedoch nicht bekannt. Daher generiert die **`friend`** Deklaration in der-Klasse `HasFriends` einen Fehler.

Ab c++ 11 gibt es zwei Formen von Friend-Deklarationen für eine Klasse:

```cpp
friend class F;
friend F;
```

In der ersten Form wird eine neue Klasse von F eingeführt, wenn im innersten Namespace keine vorhandene Klasse mit diesem Namen gefunden wurde. **C++ 11**: das zweite Formular führt nicht zu einer neuen Klasse. Sie kann verwendet werden, wenn die Klasse bereits deklariert wurde, und Sie muss beim Deklarieren eines Vorlagen-Typparameters oder einer typedef als Friend verwendet werden.

Verwenden Sie, `class friend F` Wenn der referenzierte Typ noch nicht deklariert wurde:

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

Im folgenden Beispiel `friend F` verweist auf die-Klasse, die `F` außerhalb des Bereichs von NS deklariert wird.

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

Verwenden `friend F` Sie, um einen Vorlagen Parameter als Friend zu deklarieren:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Verwenden `friend F` Sie, um eine typedef als Friend zu deklarieren:

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

Eine **`friend`** Funktion ist eine Funktion, die kein Member einer Klasse ist, aber auf die privaten und geschützten Member der Klasse zugreifen kann. Friend-Funktionen gelten nicht als Klassenmember. Es sind normale externe Funktionen, denen spezielle Zugriffsrechte gewährt werden. Freunde befinden sich nicht im Bereich der Klasse, und Sie werden nicht mithilfe der Member-Selection-Operatoren () aufgerufen **.** und- **>** ), es sei denn, Sie sind Mitglieder einer anderen Klasse. Eine **`friend`** Funktion wird von der Klasse deklariert, die Zugriff gewährt. Die **`friend`** Deklaration kann an beliebiger Stelle in der Klassen Deklaration platziert werden. Sie wird nicht durch die Schlüsselwörter der Zugriffssteuerung beeinflusst.

Das folgende Beispiel zeigt eine `Point`-Klasse und die Friend-Funktion `ChangePrivate`. Die **`friend`** Funktion hat Zugriff auf den privaten Datenmember des Objekts, das `Point` Sie als Parameter empfängt.

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

Im vorherigen Beispiel wird nur der Funktion `A::Func1( B& )` Friend-Zugriff auf die `B`-Klasse gewährt. Daher ist der Zugriff auf den privaten Member `_b` in `Func1` der Klasse richtig, `A` aber nicht in `Func2` .

Eine **`friend`** Klasse ist eine Klasse, deren Element Funktionen Friend-Funktionen einer Klasse sind, d. h., deren Member-Funktionen Zugriff auf die privaten und geschützten Member der anderen Klasse haben. Angenommen, die **`friend`** Deklaration in der Klasse lautete wie folgt `B` :

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

Ein verwalteter Typ (in C++/CLI) darf keine Friend-Funktionen, Friend-Klassen oder Friend-Schnittstellen aufweisen.

Die Friendship-Klasse wird nicht vererbt. Dies bedeutet, dass die von `YourOtherClass` abgeleiteten Klassen nicht auf die privaten Member von `YourClass` zugreifen können. Die Friendship-Klasse ist nicht transitiv. Daher können Klassen, die Friends von `YourOtherClass` sind, nicht auf die privaten Member von `YourClass` zugreifen.

Die folgende Abbildung zeigt vier Klassendeklarationen: `Base`, `Derived`, `aFriend` und `anotherFriend`. Nur die `aFriend`-Klasse hat direkten Zugriff auf die privaten Member der `Base`-Klassendeklaration (und auf alle Member, die `Base` möglicherweise geerbt hat).

![Auswirkungen von Friend-Beziehungen](../cpp/media/vc38v41.gif "Auswirkungen von Friend-Beziehungen") <br/>
Auswirkungen von Friend-Beziehungen

## <a name="inline-friend-definitions"></a>Inline-Friend-Definitionen

Friend-Funktionen können (bei Angabe eines Funktions Texts) innerhalb von Klassen Deklarationen definiert werden. Diese Funktionen sind Inlinefunktionen und wie Memberinlinefunktionen verhalten sie sich, als wären sie sofort definiert worden, nachdem alle Klassenmember angezeigt wurden, jedoch bevor der Klassengültigkeitsbereich geschlossen wurde (Ende der Klassendeklaration). Friend-Funktionen, die innerhalb von Klassen Deklarationen definiert sind, befinden sich im Gültigkeitsbereich der einschließenden Klasse.

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)
