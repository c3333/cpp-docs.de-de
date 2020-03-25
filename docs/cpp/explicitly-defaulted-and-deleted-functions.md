---
title: Explizit vorgegebene und gelöschte Funktionen
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: b43588aac1d246c83f5281456625eeb0ff36b94d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179977"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Explizit vorgegebene und gelöschte Funktionen

In C++11 erhalten Sie durch Defaulted- und Deleted-Funktionen explizite Kontrolle darüber, ob die speziellen Memberfunktionen automatisch generiert werden. Deleted-Funktionen stellen außerdem eine einfache Sprache zur Verfügung, um zu verhindern, dass problematische Typerweiterungen in Argumenten zu Funktionen aller Typen (spezielle Memberfunktionen sowie normale Memberfunktionen und nicht-Memberfunktionen) auftreten, die andernfalls einen unerwünschten Funktionsaufruf auslösen könnten.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Vorteile von expliziten Defaulted- und Deleted-Funktionen

In C++ generiert der Compiler automatisch den Standardkonstruktor, den Kopierkonstruktor, den Kopierzuweisungsoperator und den Destruktor für einen Typ, wenn es keinen eigenen deklariert. Diese Funktionen werden als *spezielle Member-Funktionen*bezeichnet und bewirken, dass einfache benutzerdefinierte Typen sich wie Strukturen in C++ C Verhalten. Das heißt, Sie können diese ohne zusätzlichen Codierungsaufwand erstellen, kopieren und zerstören. C++11 stellt Verschiebesemantik für die Sprache bereit und fügt den Bewegungskonstruktor und den Bewegungszuweisungsoperator zur Liste der speziellen Memberfunktionen hinzu, die der Compiler automatisch generieren kann.

Dies ist für einfache Typen praktisch, komplexe Typen definieren jedoch häufig mindestens eine der speziellen Memberfunktionen selbst, wodurch verhindert werden kann, dass andere spezielle Memberfunktionen automatisch generiert werden. In der Praxis:

- Wenn ein Konstruktor explizit deklariert wird, wird kein Standardkonstruktor automatisch generiert.

- Wenn ein virtueller Destruktor explizit deklariert wird, wird kein Standarddestruktor automatisch generiert.

- Wenn ein Bewegungskonstruktor oder Bewegungszuweisungsoperator explizit deklariert wird, tritt Folgendes ein:

   - Es wird kein Kopierkonstruktor automatisch generiert.

   - Es wird kein Kopierzuweisungsoperator automatisch generiert.

- Wenn ein Kopierkonstruktor, Kopierzuweisungsoperator, Bewegungskonstruktor, Bewegungszuweisungsoperator oder Destruktor explizit deklariert wird, tritt Folgendes ein:

   - Es wird kein Bewegungskonstruktor automatisch generiert.

   - Es wird kein Bewegungszuweisungsoperator automatisch generiert.

> [!NOTE]
> Darüber hinaus gibt der C++11-Standard die folgenden zusätzlichen Regeln an:
>
> - Wenn ein Kopierkonstruktor oder Destruktor explizit deklariert wird, wird die automatische Generierung des Kopierzuweisungsoperators abgelehnt.
> - Wenn ein Kopierzuweisungsoperator oder Destruktor explizit deklariert wird, wird die automatische Generierung eines Kopierkonstruktors abgelehnt.
>
> In beiden Fällen werden die erforderlichen Funktionen weiterhin automatisch von Visual Studio implizit generiert, und es wird keine Warnung+ ausgegeben.

Die Folgen dieser Regeln können auch in Objekthierarchien einfließen. Wenn z. b. aus irgendeinem Grund eine Basisklasse keinen Standardkonstruktor hat, der von einer abgeleiteten Klasse aufgerufen werden kann, d. –. ein **öffentlicher** oder **geschützter** Konstruktor, der keine Parameter annimmt –, kann eine Klasse, die von ihr abgeleitet ist, nicht automatisch Ihren eigenen Standardkonstruktor generieren.

Diese Regeln können die Implementierung einfacher, benutzerdefinierter Typen und allgemeiner C++-Idiome erschweren, wenn beispielsweise ein benutzerdefinierter Typ als non-copyable festgelegt wird, indem der Kopierkonstruktor und der Kopierzuweisungsoperator als privat deklariert und nicht definiert werden.

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Vor C++11 war dieser Codeausschnitt die idiomatische Form von non-copyable-Typen. Es gibt allerdings mehrere Probleme:

- Der Kopierkonstruktor muss als privat deklariert werden, um ihn auszublenden. Da der Vorgang jedoch nicht deklariert wird, wird die automatische Generierung des Standardkonstruktors verhindert. Sie müssen den Standardkonstruktor, falls erforderlich, explizit definieren, auch wenn er keine Aktionen ausführt.

- Auch wenn der explizit definierte Standardkonstruktor keine Aktionen ausführt, wird er vom Compiler als wichtig betrachtet. Er ist weniger effizient als ein automatisch generierter Standardkonstruktor und verhindert, dass `noncopyable` ein echter POD-Typ ist.

- Obwohl der Kopierkonstruktor und der Kopierzuweisungsoperator vom äußeren Code ausgeblendet werden, können die Memberfunktionen und Friends von `noncopyable` sie weiterhin anzeigen und aufrufen. Wenn sie deklariert, aber nicht definiert werden, verursacht deren Aufruf einen Linkerfehler.

- Obwohl dies eine häufig akzeptierte Vorgehensweise ist, ist der Zweck nicht klar, es sei denn, Ihnen sind alle Regeln für die automatische Generierung der speziellen Memberfunktionen bekannt.

In C++11 kann das non-copyable-Idiom auf einfachere Weise implementiert werden.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Beachten Sie, wie die Probleme mit dem Idiom vor Version C++11 gelöst werden:

- Die Generierung des Standardkonstruktors wird weiterhin verhindert, indem ein Kopierkonstruktor deklariert wird, sie kann jedoch durch explizite Festlegung auf den Standardwert wieder aktiviert werden.

- Bestimmte explizit auf den Standardwert festgelegte Memberfunktionen gelten weiterhin als unwichtig, sodass Leistungseinbußen vermieden werden und nicht verhindert wird, dass `noncopyable` ein echter POD-Typ ist.

- Der Kopierkonstruktor und der Kopierzuweisungsoperator sind öffentlich, jedoch gelöscht. Die Definition oder der Aufruf einer gelöschten Funktion ist ein Fehler, der zum Zeitpunkt der Kompilierung auftritt.

- Der Zweck ist für jeden nachvollziehbar, der mit `=default` und `=delete` vertraut ist. Sie müssen die Regeln für die automatische Generierung spezieller Memberfunktionen nicht verstehen.

Es sind ähnliche Idiome für die Erstellung von benutzerdefinierten Typen vorhanden, die unbeweglich sind, die nur dynamisch oder nicht dynamisch zugeordnet werden können. Jedes dieser Idiome verfügt über Implementierungen aus Vorversionen von C++11, bei denen ähnliche Probleme auftreten und die in C++11 auf ähnliche Weise gelöst werden, indem sie in Bezug auf spezielle auf den Standardwert festgelegte und gelöschte Memberfunktionen implementiert werden.

## <a name="explicitly-defaulted-functions"></a>Explizit auf den Standardwert festgelegte Funktionen

Sie können spezielle Memberfunktionen auf den Standardwert zurücksetzen, um explizit anzugeben, dass die spezielle Memberfunktion die Standardimplementierung verwendet, um die spezielle Memberfunktion mit einem nicht öffentlichen Zugriffsqualifizierer zu definieren oder um eine spezielle Memberfunktion erneut zu aktivieren, deren automatische Generierung durch andere Bedingungen verhindert wurde.

Sie legen eine spezielle Memberfunktion auf den Standardwert fest, indem Sie sie wie in diesem Beispiel deklarieren:

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Beachten Sie, dass Sie eine spezielle Memberfunktion außerhalb des Texts einer Klasse auf den Standardwert festlegen können, solange sie inlinable ist.

Aufgrund der Leistungsvorteile von trivialen speziellen Memberfunktionen wird empfohlen, automatisch generierte spezielle Memberfunktionen leeren Funktionsrümpfen vorzuziehen, wenn Sie das Standardverhalten verwenden möchten. Hierzu können Sie entweder die spezielle Memberfunktion explizit auf den Standardwert festlegen oder sie nicht deklarieren (und indem Sie auch keine anderen speziellen Memberfunktionen deklarieren, die deren automatische Generierung verhindern würden).

## <a name="deleted-functions"></a>Deleted-Funktionen

Sie können spezielle Memberfunktionen sowie normale Memberfunktionen und nicht-Memberfunktionen löschen, damit sie weder angezeigt noch aufgerufen werden. Das Löschen von speziellen Memberfunktionen ist eine sauberere Methode, um zu verhindern, dass der Compiler spezielle Memberfunktionen generiert, die Sie nicht benötigen. Die Funktion muss gelöscht werden, wenn sie deklariert wird. Sie kann danach nicht auf die Weise gelöscht werden, dass eine Funktion deklariert und später auf den Standardwert festgelegt wird.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

Das Löschen von normalen Memberfunktionen oder nicht-Memberfunktionen verhindert, dass problematische Typerweiterungen eine unbeabsichtigte Funktion aufrufen. Dies funktioniert, weil gelöschte Funktionen weiterhin an der Überladungsauflösung beteiligt sind und eine bessere Übereinstimmung als die Funktion bereitstellen, die aufgerufen werden könnte, nachdem die Typen erweitert wurden. Der Funktionsaufruf wird in die spezifischere, aber gelöschte Funktion aufgelöst und verursacht einen Compilerfehler.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Beachten Sie im vorhergehenden Beispiel, dass das Aufrufen von `call_with_true_double_only` mithilfe eines **float** -Arguments einen Compilerfehler verursachen würde, aber das Aufrufen von `call_with_true_double_only` mithilfe eines **int** -Arguments nicht. im **int** -Fall wird das Argument von " **int** " in " **Double** " herauf gestuft und die **doppelte** Version der Funktion aufgerufen, obwohl dies möglicherweise nicht beabsichtigt ist. Um sicherzustellen, dass jeder Aufruf dieser Funktion mithilfe eines non-double-Arguments einen Compilerfehler verursacht, können Sie eine Vorlagenversion der gelöschten Funktion deklarieren.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
