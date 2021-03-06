---
title: SafeInt-Klasse
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt
- SafeInt::SafeInt
- SafeInt.SafeInt
helpviewer_keywords:
- SafeInt class
- SafeInt class, constructor
ms.assetid: 27a8f087-2511-46f9-8d76-2aeb66ca272f
ms.openlocfilehash: d61ce20a8644ca64d37c0eca605d52fb308c0863
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560959"
---
# <a name="safeint-class"></a>SafeInt-Klasse

Erweitert die primitiven Ganzzahlen, um Ganzzahlüberlauf zu vermeiden, und ermöglicht Ihnen, verschiedene Typen von ganzen Zahlen zu vergleichen.

> [!NOTE]
> Die neueste Version der safeint-Bibliothek finden Sie unter [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) . Um die safeint-Bibliothek zu verwenden, Klonen Sie das Repository, und `#include "SafeInt.hpp"`

## <a name="syntax"></a>Syntax

```cpp
template<typename T, typename E = _SAFEINT_DEFAULT_ERROR_POLICY>
class SafeInt;
```

### <a name="parameters"></a>Parameter

*`T`*\
Der Typ des Ganzzahl- oder booleschen Parameters, der `SafeInt` ersetzt.

*`E`*\
Ein Aufzählungsdatentyp, der die Fehlerbehandlungsrichtlinie definiert.

*`U`*\
Der Typ des Ganzzahl- oder booleschen Parameters für den zweiten Operanden.

*RHS*\
[in] Ein Eingabeparameter, der den Wert auf der rechten Seite des Operators in mehreren eigenständigen Funktionen darstellt.

*Ich*\
[in] Ein Eingabeparameter, der den Wert auf der rechten Seite des Operators in mehreren eigenständigen Funktionen darstellt.

*Bohrer*\
[in] Ein Eingabeparameter, der den Wert auf der rechten Seite des Operators in mehreren eigenständigen Funktionen darstellt.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

| name                          |  BESCHREIBUNG |
|---------------------------|--------------------|
| [Safeint:: safeint](#safeint)  |  Der Standardkonstruktor. |

### <a name="assignment-operators"></a>Zuweisungsoperatoren

| Name  |  Syntax |
|----|---------|
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const U& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const T& rhs) throw()` |
| =     |  `template<typename U>`<br />`SafeInt<T,E>& operator= (const SafeInt<U, E>& rhs)` |
| =     |  `SafeInt<T,E>& operator= (const SafeInt<T,E>& rhs) throw()` |

### <a name="casting-operators"></a>Umwandlungsoperatoren

| Name              |  Syntax |
|------|---------------------------------|
| bool              |  `operator bool() throw()` |
| char              |  `operator char() const` |
| char mit Vorzeichen       |  `operator signed char() const` |
| unsigned char     |  `operator unsigned char() const` |
| __int16           |  `operator __int16() const` |
| unsigned __int16  |  `operator unsigned __int16() const` |
| __int32           |  `operator __int32() const` |
| unsigned __int32  |  `operator unsigned __int32() const` |
| long              |  `operator long() const` |
| unsigned long     |  `operator unsigned long() const` |
| __int64           |  `operator __int64() const` |
| unsigned __int64  |  `operator unsigned __int64() const` |
| wchar_t           |  `operator wchar_t() const` |

### <a name="comparison-operators"></a>Vergleichsoperatoren

| Name  |  Syntax |
|----|----------------|
| \<     |  `template<typename U>`<br /><br /> `bool operator< (U rhs) const throw()` |
| \<     |  `bool operator< (SafeInt<T,E> rhs) const throw()` |
| \>=    |  `template<typename U>`<br /><br /> `bool operator>= (U rhs) const throw()` |
| \>=    |  `Bool operator>= (SafeInt<T,E> rhs) const throw()` |
| \>     |  `template<typename U>`<br /><br /> `bool operator> (U rhs) const throw()` |
| \>     |  `Bool operator> (SafeInt<T,E> rhs) const throw()` |
| \<=    |  `template<typename U>`<br /><br /> `bool operator<= (U rhs) const throw()` |
| \<=    |  `bool operator<= (SafeInt<T,E> rhs) const throw()` |
| ==    |  `template<typename U>`<br /><br /> `bool operator== (U rhs) const throw()` |
| ==    |  `bool operator== (bool rhs) const throw()` |
| ==    |  `bool operator== (SafeInt<T,E> rhs) const throw()` |
| !=    |  `template<typename U>`<br /><br /> `bool operator!= (U rhs) const throw()` |
| !=    |  `bool operator!= (bool b) const throw()` |
| !=    |  `bool operator!= (SafeInt<T,E> rhs) const throw()` |

### <a name="arithmetic-operators"></a>Arithmetische Operatoren

| Name  |  Syntax |
|----|--------------|
| +     |  `const SafeInt<T,E>& operator+ () const throw()` |
| -     |  `SafeInt<T,E> operator- () const` |
| ++    |  `SafeInt<T,E>& operator++ ()` |
| --    |  `SafeInt<T,E>& operator-- ()` |
| %     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator% (U rhs) const` |
| %     |  `SafeInt<T,E> operator% (SafeInt<T,E> rhs) const` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (U rhs)` |
| %=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator%= (SafeInt<U, E> rhs)` |
| \*     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator* (U rhs) const` |
| \*     |  `SafeInt<T,E> operator* (SafeInt<T,E> rhs) const` |
| \*=    |  `SafeInt<T,E>& operator*= (SafeInt<T,E> rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (U rhs)` |
| \*=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator*= (SafeInt<U, E> rhs)` |
| /     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator/ (U rhs) const` |
| /     |  `SafeInt<T,E> operator/ (SafeInt<T,E> rhs ) const` |
| /=    |  `SafeInt<T,E>& operator/= (SafeInt<T,E> i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (U i)` |
| /=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator/= (SafeInt<U, E> i)` |
| +     |  `SafeInt<T,E> operator+ (SafeInt<T,E> rhs) const` |
| +     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator+ (U rhs) const` |
| +=    |  `SafeInt<T,E>& operator+= (SafeInt<T,E> rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (U rhs)` |
| +=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator+= (SafeInt<U, E> rhs)` |
| -     |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator- (U rhs) const` |
| -     |  `SafeInt<T,E> operator- (SafeInt<T,E> rhs) const` |
| -=    |  `SafeInt<T,E>& operator-= (SafeInt<T,E> rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (U rhs)` |
| -=    |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator-= (SafeInt<U, E> rhs)` |

### <a name="logical-operators"></a>Logische Operatoren

| Name     |  Syntax |
|------|--------------|
| !        |  `bool operator !() const throw()` |
| ~        |  `SafeInt<T,E> operator~ () const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (U bits) const throw()` |
| \<\<       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator<< (SafeInt<U, E> bits) const throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (U bits) throw()` |
| \<\<=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator<<= (SafeInt<U, E> bits) throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (U bits) const throw()` |
| \>\>       |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator>> (SafeInt<U, E> bits) const throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (U bits) throw()` |
| \>\>=      |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator>>= (SafeInt<U, E> bits) throw()` |
| &        |  `SafeInt<T,E> operator& (SafeInt<T,E> rhs) const throw()` |
| &        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator& (U rhs) const throw()` |
| &=       |  `SafeInt<T,E>& operator&= (SafeInt<T,E> rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (U rhs) throw()` |
| &=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&= (SafeInt<U, E> rhs) throw()` |
| ^        |  `SafeInt<T,E> operator^ (SafeInt<T,E> rhs) const throw()` |
| ^        |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator^ (U rhs) const throw()` |
| ^=       |  `SafeInt<T,E>& operator^= (SafeInt<T,E> rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (U rhs) throw()` |
| ^=       |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator^= (SafeInt<U, E> rhs) throw()` |
| &#124;   |  `SafeInt<T,E> operator&#124; (SafeInt<T,E> rhs) const throw()` |
| &#124;   |  `template<typename U>`<br /><br /> `SafeInt<T,E> operator&#124; (U rhs) const throw()` |
| &#124;=  |  `SafeInt<T,E>& operator&#124;= (SafeInt<T,E> rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (U rhs) throw()` |
| &#124;=  |  `template<typename U>`<br /><br /> `SafeInt<T,E>& operator&#124;= (SafeInt<U, E> rhs) throw()` |

## <a name="remarks"></a>Bemerkungen

Die `SafeInt`-Klasse schützt vor Ganzzahlüberlauf in mathematischen Operationen. Betrachten Sie beispielsweise das Hinzufügen von zwei 8-Bit-Ganzzahlen: eine hat den Wert 200 und die zweite den Wert 100. Die richtige mathematische Operation wäre 200 + 100 = 300. Jedoch geht aufgrund des 8-Bit-Ganzzahllimits das obere Bit verloren, und der Compiler gibt 44 (300 - 2<sup>8</sup>) als Ergebnis zurück. Jeder Vorgang, der von dieser mathematischen Gleichung abhängig ist, wird unerwartetes Verhalten hervorrufen.

Die `SafeInt`-Klasse überprüft, ob ein arithmetischer Überlauf auftritt, oder ob der Code versucht, durch 0 (null) zu dividieren. In beiden Fällen ruft die Klasse den Fehlerhandler auf, um das Programm vor dem möglichen Problem zu warnen.

Diese Klasse ermöglicht Ihnen auch, zwei verschiedene Typen von ganzen Zahlen zu vergleichen, solange sie `SafeInt`-Objekte sind. Wenn Sie einen Vergleich durchführen, müssen Sie in der Regel die Zahlen zunächst in denselben Typ konvertieren. Eine Zahl in einen anderen Typ umzuwandeln, erfordert oft Überprüfungen, um sicherzustellen, dass kein Datenverlust auftritt.

In der Operatorentabelle in diesem Thema sind die von der `SafeInt`-Klasse unterstützten mathematischen und Vergleichsoperatoren aufgelistet. Die meisten mathematischen Operatoren geben ein `SafeInt`-Objekt des Typs `T` zurück.

Vergleichsvorgänge zwischen einem `SafeInt`- und einem Ganzzahltyp können in beiden Richtungen ausgeführt werden. Beispielsweise sind `SafeInt<int>(x) < y` und `y> SafeInt<int>(x)` beide gültig und geben das gleiche Ergebnis zurück.

Viele binäre Operatoren unterstützen nicht die Verwendung von zwei unterschiedlichen `SafeInt` Typen. Ein Beispiel hierfür ist der `&`-Operator. `SafeInt<T, E> & int` wird unterstützt, aber `SafeInt<T, E> & SafeInt<U, E>` nicht. Im zweiten Beispiel weiß der Compiler nicht, welcher Parametertyp zurückgegeben werden soll. Eine Lösung dieses Problems ist die Umwandlung des zweiten Parameters zurück in den Basistyp. Bei Verwendung der gleichen Parameter kann dies mit `SafeInt<T, E> & (U)SafeInt<U, E>` erfolgen.

> [!NOTE]
> Für bitweise Vorgänge sollten die beiden verschiedenen Parameter gleich groß sein. Wenn die Größen unterschiedlich sind, löst der Compiler eine [ASSERT](../mfc/reference/diagnostic-services.md#assert)-Ausnahme aus. Die Ergebnisse dieses Vorgangs können nicht unbedingt genau sein. Um dieses Problem zu beheben, wandeln Sie den kleineren Parameter um, bis er die gleiche Größe wie der größere Parameter hat.

Bei den Schiebeoperatoren löst die Verschiebung von mehr Bits, als für den Vorlagentyp vorhanden sind, eine ASSERT-Ausnahme aus. Dies hat im Releasemodus keine Auswirkungen. Das Mischen von zwei Typen von SafeInt-Parametern für die Schiebeoperatoren ist möglich, da der Rückgabetyp mit dem ursprünglichen Typ identisch ist. Die Anzahl auf der rechten Seite des Operators gibt nur die Anzahl der zu verschiebenden Bits an.

Wenn Sie einen logischen Vergleich mit einem safeint-Objekt durchführen, ist der Vergleich streng arithmetisch. Betrachten Sie beispielsweise die folgenden Ausdrücke:

- `SafeInt<uint>((uint)~0) > -1`

- `((uint)~0) > -1`

Die erste-Anweisung wird in aufgelöst **`true`** , aber die zweite-Anweisung wird in aufgelöst **`false`** . Die bitweise Negation von 0 ist 0xFFFFFFFF. In der zweiten Anweisung wird der Standardvergleichsoperator 0xFFFFFFFF mit 0xFFFFFFFF verglichen und die Gleichheit festgestellt. Der Vergleichsoperator für die `SafeInt`-Klasse erkennt, dass der zweite Parameter negativ ist, während der erste Parameter kein Vorzeichen hat. Aus diesem Grund erkennt der logische `SafeInt`-Operator bei identischer Bitdarstellung, dass die Ganzzahl ohne Vorzeichen größer als -1 ist.

Seien Sie vorsichtig bei der gemeinsamen Verwendung der `SafeInt`-Klasse mit dem ternären Operator `?:`. Betrachten Sie die folgende Codezeile.

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : -1;
```

Der Compiler wandelt sie wie folgt um:

```cpp
Int x = flag ? SafeInt<unsigned int>(y) : SafeInt<unsigned int>(-1);
```

Wenn `flag` **`false`** den Wert hat, löst der Compiler eine Ausnahme aus, anstatt den Wert von-1 an zuzuweisen `x` . In der folgenden Zeile sehen Sie den richtigen Code, um dieses Verhalten zu vermeiden.

```cpp
Int x = flag ? (int) SafeInt<unsigned int>(y) : -1;
```

`T` und `U` können einem booleschen Typ, Zeichentyp oder Ganzzahltyp zugewiesen werden. Die Ganzzahltypen können mit oder ohne Vorzeichen sein und eine beliebige Größe von 8 Bits bis 64 Bits haben.

> [!NOTE]
> Die `SafeInt`-Klasse akzeptiert zwar jede beliebige Ganzzahl, doch mit Typen ohne Vorzeichen ist ihre Leistung effizienter.

`E` ist der Mechanismus zur Fehlerbehandlung, den `SafeInt` verwendet. Zwei Mechanismen für die Fehlerbehandlung werden mit der SafeInt-Bibliothek bereitgestellt. Die Standardrichtlinie ist `SafeIntErrorPolicy_SafeIntException`, die eine [SafeIntException-Klasse](safeintexception-class.md)-Ausnahme auslöst, wenn ein Fehler auftritt. Die andere Richtlinie ist `SafeIntErrorPolicy_InvalidParameter`, wodurch das Programm beendet wird, wenn ein Fehler auftritt.

Es gibt zwei Optionen zur Optimierung der Fehlerrichtlinie. Die erste Option ist, den Parameter `E` beim Erstellen einer `SafeInt`-Instanz festzulegen. Verwenden Sie diese Option, wenn Sie die Fehlerbehandlungsrichtlinie für nur eine `SafeInt`-Instanz ändern möchten. Die andere Option ist, _SAFEINT_DEFAULT_ERROR_POLICY als Ihre benutzerdefinierte Fehlerbehandlungsklasse zu definieren, bevor Sie die `SafeInt`-Bibliothek einbeziehen. Verwenden Sie diese Option, wenn Sie die Standard-Fehlerbehandlungsrichtlinie für alle Instanzen der `SafeInt`-Klasse in Ihrem Code ändern möchten.

> [!NOTE]
> Eine angepasste Klasse, die Fehler aus der SafeInt-Bibliothek behandelt, sollte die Steuerung nicht an den Code zurückgeben, der den Fehlerhandler aufgerufen hat. Nachdem der Fehlerhandler aufgerufen wurde, kann das Ergebnis des `SafeInt` Vorgangs nicht als vertrauenswürdig eingestuft werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`SafeInt`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Safeint. HPP
> [!NOTE]
> Die neueste Version dieser Bibliothek finden Sie unter [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) . Klonen Sie die Bibliothek, und fügen Sie safeint. HPP ein, um die safeint-Bibliothek zu verwenden.
> Bevorzugen Sie dieses GitHub-Repository, <safeint. h>. Dabei handelt es sich um eine moderne Version von <safeint. h->, die eine kleine Anzahl von Fehlerbehebungen umfasst, moderne Features von C++ verwendet, die zu effizienterem Code führen und für beliebige Plattformen mithilfe von gcc-, clang-oder Intel-Compilern portabel sind.

### <a name="example"></a>Beispiel

```c
#include "SafeInt.hpp" // set path to your clone of the SafeInt GitHub repo (https://github.com/dcleblanc/SafeInt)

int main()
{
    int divisor = 3;
    int dividend = 6;
    int result;

    bool success = SafeDivide(dividend, divisor, result); // result = 2
    success = SafeDivide(dividend, 0, result); // expect fail. result isn't modified.
}
```

**Namespace:** keine

## <a name="safeintsafeint"></a><a name="safeint"></a> Safeint:: safeint

Erstellt ein `SafeInt`-Objekt.

```cpp
SafeInt() throw

SafeInt (const T& i) throw ()

SafeInt (bool b) throw ()

template <typename U>
SafeInt (const SafeInt <U, E>& u)

I template <typename U>
SafeInt (const U& i)
```

### <a name="parameters"></a>Parameter

`i`<br/>
[in] Der Wert für das neue `SafeInt`-Objekt. Dabei muss es sich je nach Konstruktor um einen Parameter vom Typ „T“ oder „U“ handeln.

`b`<br/>
[in] Der boolesche Wert für das neue `SafeInt`-Objekt.

`u`<br/>
[in] Ein `SafeInt`-Objekt vom Typ „U“. Das neue `SafeInt`-Objekt hat den gleichen Wert wie *u*, ist aber vom Typ „T“.

`U` Der Typ der in der gespeicherten Daten `SafeInt` . Dies kann entweder ein boolescher Wert, ein Zeichen oder eine ganze Zahl sein. Wenn es sich um einen ganzzahligen Typ handelt, kann er signiert oder nicht signiert werden und zwischen 8 und 64 Bits liegen.

### <a name="remarks"></a>Bemerkungen

Der Eingabeparameter für den Konstruktor *i* oder *u* muss ein boolescher, Zeichen- oder Ganzzahltyp sein. Wenn es sich um einen anderen Parametertyp handelt, ruft die- `SafeInt` Klasse [static_assert](../cpp/static-assert.md) auf, um einen ungültigen Eingabeparameter anzugeben.

Die Konstruktoren, die den Vorlagentyp `U` verwenden, konvertieren den Eingabeparameter automatisch in den durch `T` angegebenen Typ. Die `SafeInt`-Klasse konvertiert die Daten ohne Verlust von Daten. Sie meldet dem Fehlerhandler, `E` Wenn die Daten nicht ohne Datenverlust in den Typ konvertiert werden können `T` .

Wenn Sie eine `SafeInt`-Instanz aus einem booleschen Parameter erstellen, müssen Sie den Wert sofort initialisieren. `SafeInt`Mit dem Code können Sie keine erstellen `SafeInt<bool> sb;` . Dies verursacht einen Compilerfehler.
