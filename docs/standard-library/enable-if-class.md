---
title: enable_if-Klasse
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 1017fc315a4440350a0190cf4b40e644cda16876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230038"
---
# <a name="enable_if-class"></a>enable_if-Klasse

Wandelt einen Typ für die SFINAE-Überladungsauflösung bedingt in eine Instanz um. Die-Typdefinition `enable_if<Condition,Type>::type` ist bereits vorhanden – und ist ein Synonym für `Type` –, wenn gleich `Condition` ist **`true`** .

## <a name="syntax"></a>Syntax

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>Parameter

*B*\
Der Wert, der das Vorhandensein des Ergebnistyps bestimmt.

*Bund*\
Der Typ, der instanziiert werden soll, wenn *B* gleich true ist.

## <a name="remarks"></a>Bemerkungen

Wenn *B* `enable_if<B, T>` den Wert "true" hat, verfügt über eine benannte Typdefinition namens "Type", die ein Synonym für " *T*" ist.

Wenn *B* false ist, `enable_if<B, T>` verfügt nicht über eine nicht benannte typedef mit dem Namen "Type".

Die folgende Alias-Vorlage steht zur Verfügung:

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

In C++ ist eine fehlgeschlagene Substitution von Vorlagenparametern kein eigentlicher Fehler – dies wird als *SFINAE* (Substitution Failure Is Not An Error) bezeichnet. Normalerweise wird `enable_if` verwendet, um Kandidaten aus einer Überladungsauflösung zu entfernen – also aus dem Überladungssatz auszusortieren, sodass eine Definition zugunsten einer anderen zurückgewiesen werden kann. Dies entspricht dem SFINAE-Verhalten. Weitere Informationen zu SFINAE finden Sie unter [Substitution failure is not an error](https://go.microsoft.com/fwlink/p/?linkid=394798) auf Wikipedia.

Im Folgenden finden Sie vier Beispielszenarien:

- Szenario 1: Umschließen des Rückgabetyps einer Funktion:

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
}
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
}
```

- Szenario 2: Hinzufügen eines Funktionsparameters mit einem Standardargument:

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- Szenario 3: Hinzufügen eines Vorlagenparameters mit einem Standardargument:

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- Szenario 4: Wenn Ihre Funktion über ein Argument ohne Vorlage verfügt, können Sie ihren Typ umschließen:

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

Szenario 1 funktioniert nicht mit Konstruktoren und Konvertierungsoperatoren, da diese keine Rückgabetypen haben.

In Szenario 2 bleibt der Parameter unbenannt. Sie können ihn `::type Dummy = BAR` nennen, aber der Namens-`Dummy` ist irrelevant, und eine Benennung löst wahrscheinlich eine Warnung über einen nicht referenzierten Parameter aus. Sie müssen einen `FOO` Funktionsparameter typ und ein `BAR`-Standardargument auswählen.  Sie könnten **`int`** und `0` , aber dann könnten Benutzer Ihres Codes versehentlich an die Funktion übergeben werden, eine zusätzliche Ganzzahl, die ignoriert würde. Stattdessen wird empfohlen, dass Sie `void **` und entweder und verwenden, `0` **`nullptr`** da fast nichts in konvertierbar ist `void **` :

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

Szenario 2 funktioniert auch mit normalen Konstruktoren.  Allerdings funktioniert es nicht mit Konvertierungsoperatoren, da diese keine zusätzlichen Parameter aufnehmen können.  Es funktioniert ebenfalls nicht mit [variadic](../cpp/ellipses-and-variadic-templates.md)-Konstruktoren, da die Hinzufügung zusätzlicher Parameter dazu führt, dass der Funktionsparameter einen nicht abgeleiteten Kontext verpackt und dadurch den Zweck von `enable_if` verfehlt.

Szenario 3 verwendet den Namen `Dummy`, aber dieser ist optional. Nur „`typename = typename`“ wäre geeignet, aber wenn Ihnen dies seltsam vorkommt, können Sie einen „Dummy“-Namen wählen. Wählen Sie jedoch keinen Namen, der auch in der Funktionsdefinition verwendet werden könnte. Wenn Sie keinen Typ für das `enable_if` angeben, bleibt es standardmäßig leer, was verständlich ist, da es Sie nicht kümmern muss, was `Dummy` ist. Dies funktioniert für alle Elemente einschließlich Konvertierungsoperatoren und [variadic](../cpp/ellipses-and-variadic-templates.md)-Konstruktoren.

Szenario 4 funktioniert mit Konstruktoren, die keine Rückgabetypen haben, und löst dadurch die Umschließungseinschränkung von Szenario 1 auf.  Szenario 4 ist allerdings auf Funktionsargumente ohne Vorlage beschränkt, die nicht immer zur Verfügung stehen.  (Die Verwendung von Szenario 4 mit einem Funktionsargument mit Vorlage verhindert, dass die Ableitung eines Vorlagenarguments in diesem Szenario funktioniert.)

`enable_if` ist leistungsstark, aber bei falscher Verwendung auch gefährlich.  Da es sein Zweck ist, Kandidaten vor einer Überladungsauflösung verschwinden zu lassen, wenn es fehlerhaft verwendet wird, können seine Wirkungen sehr verwirrend sein.  Hier sind einige Empfehlungen dafür:

- Verwenden Sie `enable_if` nicht, um zur Kompilierungszeit zwischen Implementierungen auszuwählen. Schreiben Sie niemals ein `enable_if` für `CONDITION` und ein anderes für `!CONDITION`.  Verwenden Sie stattdessen ein *tag dispatch*-Muster – z.B. einen Algorithmus, der Implementierungen abhängig von den Stärken der Iteratoren auswählt, die sie erhalten.

- Verwenden Sie nicht `enable_if`, um Anforderungen zu erzwingen.  Wenn Sie Vorlagenparameter überprüfen möchten und die Validierung fehlschlägt und statt der Auswahl einer anderen Implementierung zu einem Fehler führt, verwenden Sie [static_assert](../cpp/static-assert.md).

- Verwenden Sie `enable_if`, wenn Sie einen Überladungssatz haben, der einen ansonsten guten Code mehrdeutig macht.  Dies tritt sehr häufig bei der impliziten Konvertierung von Konstruktoren auf.

## <a name="example"></a>Beispiel

In diesem Beispiel wird erläutert, wie die Vorlagenfunktion [std::make_pair()](../standard-library/utility-functions.md#make_pair) von der C++-Standardbibliothek `enable_if` genutzt wird.

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

In diesem Beispiel gibt `make_pair("foo", "bar")``pair<const char *, const char *>` zurück. Überladungsauslösung, die bestimmen muss, welche `func()` Sie möchten. `pair<A, B>` hat einen impliziten Konvertierungskonstruktor aus `pair<X, Y>`.  Dies ist nicht neu, sondern war schon in C++98 vorhanden. In C++98/03 ist allerdings die Signatur des impliziten Konvertierungskonstruktors immer vorhanden, selbst wenn es `pair<int, int>(const pair<const char *, const char *>&)` ist.  Bei der Überladungs Auflösung ist es nicht wichtig, dass ein Versuch, diesen Konstruktor zu instanziieren, entsetzlich ist, da `const char *` nicht implizit in konvertierbar ist **`int`** . er prüft nur Signaturen, bevor Funktionsdefinitionen instanziiert werden.  Deshalb ist der Beispielcode mehrdeutig, da Signaturen zur Konvertierung von `pair<const char *, const char *>` in `pair<int, int>` und in `pair<string, string>` vorhanden sind.

In C++11 wurde diese Mehrdeutigkeit durch Verwendung von `enable_if` aufgelöst, um sicherzustellen, dass `pair<A, B>(const pair<X, Y>&)`**nur dann** vorhanden ist, wenn `const X&` implizit in `A` konvertierbar ist und `const Y&` implizit in `B` konvertierbar ist.  Dadurch kann die Überladungsauflösung festlegen, dass `pair<const char *, const char *>` nicht in `pair<int, int>` konvertierbar ist und dass die Überladung, die `pair<string, string>` aufnimmt, realisierbar ist.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<type_traits>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[<type_traits>](../standard-library/type-traits.md)
