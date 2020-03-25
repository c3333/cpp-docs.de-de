---
title: Einschränkungen für generische Typparameter (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: be5af8f6b2edaa8f93fef7ae06b2175b54b25396
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172477"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>Einschränkungen für generische Typparameter (C++/CLI)

In generischen Typ- oder Methodendeklarationen können Sie einen Typparameter mit Einschränkungen näher bestimmen. Eine Einschränkung ist eine Anforderung, die Typen erfüllen müssen, die als Typargumente verwendet werden. Eine Einschränkung könnte beispielsweise sein, dass das Typargument eine bestimmte Schnittstelle implementieren oder von einer bestimmten Klasse erben muss.

Einschränkungen sind optional; die Nicht-Angabe einer Einschränkung für einen Parameter ist gleichbedeutend mit dem Einschränken dieses Parameters auf <xref:System.Object>.

## <a name="syntax"></a>Syntax

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>Parameter

*type-parameter*<br/>
Einer der einzuschränkenden Typparameter.

*constraint list*<br/>
*constraint list* ist eine durch Trennzeichen getrennte Liste von Einschränkungsspezifikationen. Die Liste kann Schnittstellen enthalten, die durch den Typparameter implementiert werden sollen.

Die Liste kann auch eine Klasse enthalten. Damit ein Typargument eine Einschränkung in einer Basisklasse erfüllen kann, muss es sich in derselben Klasse befinden wie die Einschränkung oder von der Einschränkung abgeleitet werden.

Sie können auch mit **gcnew()** angeben, dass das Typargument einen öffentlichen parameterlosen Konstruktor besitzen muss. Mit **ref class** können Sie angeben, dass das Typargument ein Verweistyp sein muss, einschließlich aller Klassen-, Schnittstellen-, Delegat- oder Arraytypen. Mit **value class** können Sie angeben, dass das Typargument ein Werttyp sein muss. Jeder Werttyp außer „Nullable\<T>“ kann angegeben werden.

Sie können auch einen generischen Parameter als Einschränkung angeben. Das für den einzuschränkenden Typ bereitgestellte Typargument muss vom Typ der Einschränkung sein oder von diesem Typ abgeleitet werden. Dies wird als reine Typeinschränkung bezeichnet.

## <a name="remarks"></a>Bemerkungen

Die Einschränkungsklausel besteht aus **where**, gefolgt von einem Typparameter, einem Doppelpunkt ( **:** ) und der Einschränkung (Constraint), die die Art der Beschränkung im Typparameter angibt. **where** ist ein kontextbezogenes Schlüsselwort. Weitere Informationen finden Sie unter [Kontextbezogene Schlüsselwörter](context-sensitive-keywords-cpp-component-extensions.md). Trennen Sie mehrere **where**-Klauseln durch Leerzeichen.

Einschränkungen werden auf Typparameter angewendet, um die Typen zu begrenzen, die als Argumente für einen generischen Typ oder eine generische Methode verwendet werden können.

Klassen- und Schnittstelleneinschränkungen geben an, dass die Argumenttypen zu einer bestimmten Klasse gehören, von einer bestimmten Klasse erben oder eine bestimmte Schnittstelle implementieren müssen.

Durch Anwendung von Einschränkungen auf generische Typen oder Methoden kann der Code in diesem Typ bzw. dieser Methode von den bekannten Features der eingeschränkten Typen profitieren. So können Sie beispielsweise eine generische Klasse erstellen, deren Typparameter die Schnittstelle `IComparable<T>` implementiert:

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

Diese Einschränkung erfordert, dass ein für `T` verwendetes Typargument `IComparable<T>` zur Kompilierzeit implementiert. Sie ermöglicht auch den Aufruf von Schnittstellenmethoden wie z.B. `CompareTo`. Für die Instanz des Typparameters ist keine Umwandlung notwendig, um Schnittstellenmethoden aufrufen zu können.

Statische Methoden in der Klasse des Typarguments können nicht über den Typparameter aufgerufen werden; der Aufruf kann nur über den tatsächlichen benannten Typ erfolgen.

Eine Einschränkung kann kein Werttyp sein, dies umfasst auch integrierte Typen wie **int** oder **double**. Da Werttypen keine abgeleiteten Klassen aufweisen können, kann nur eine Klasse die Einschränkung überhaupt erfüllen. In diesem Fall kann der generische Code umgeschrieben werden, und der Typparameter wird durch den angegebenen Werttyp ersetzt.

Einschränkungen sind in einigen Fällen erforderlich, da der Compiler die Verwendung von Methoden oder anderen Features eines unbekannten Typs nur zulässt, wenn die Einschränkungen implizieren, dass der unbekannte Typ die Methoden oder Schnittstellen unterstützt.

Mehrere Einschränkungen für den gleichen Typparameter können in einer durch Trennzeichen getrennten Liste angegeben werden.

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

Bei mehreren Typparametern verwenden Sie für jeden eine **where**-Klausel. Beispiel:

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

Als Zusammenfassung: Verwenden Sie Einschränkungen in Ihrem Code entsprechend den folgenden Regeln:

- Wenn mehrere Einschränkungen aufgeführt werden, kann dies in beliebiger Reihenfolge erfolgen.

- Einschränkungen können auch Klassentypen sein, wie z.B. abstrakte Basisklasse. Einschränkungen können jedoch keine Werttypen oder versiegelte Klassen sein.

- Einschränkungen können nicht selbst Typparameter sein, können aber Typparameter in einem offenen konstruierten Typ enthalten. Beispiel:

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die Verwendung von Einschränkungen zum Aufrufen von Instanzmethoden in Typparametern.

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

## <a name="example"></a>Beispiel

Wenn ein generischer Typparameter als Einschränkung verwendet wird, wird dies als reine Typeinschränkung bezeichnet. Reine Typeinschränkungen sind nützlich, wenn eine Memberfunktion mit eigenem Typparameter diesen Parameter auf den Typparameter des enthaltenden Typs einschränken muss.

Im folgenden Beispiel ist `T` eine reine Typeinschränkung im Kontext der `Add`-Methode.

Reine Typeinschränkungen können auch in generischen Klassendefinitionen verwendet werden. Das Verwenden reiner Typeinschränkungen bei generischen Klassen ist nur bis zu einem gewissen Punkt nützlich, da der Compiler zu einer reinen Typeinschränkung nichts annehmen kann, außer dass sie von <xref:System.Object> abgeleitet ist. Verwenden Sie reine Typeinschränkungen in generischen Klassen in Szenarien, wenn Sie eine Vererbungsbeziehung zwischen zwei Typparametern erzwingen möchten.

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>Weitere Informationen

[Generics](generics-cpp-component-extensions.md)
