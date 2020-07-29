---
title: duration-Klasse
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 454c03aeb1a4666543a28759d02405a512453ffc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217791"
---
# <a name="duration-class"></a>duration-Klasse

Beschreibt einen Typ, der ein *Zeitintervall* enthält, bei dem es sich um die verstrichene Zeit zwischen zwei Situationen handelt.

## <a name="syntax"></a>Syntax

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>Bemerkungen

Mit dem Vorlagenargument `Rep` wird der Typ beschrieben, der zum Aufnehmen der Anzahl von Zeiteinheiten im Intervall verwendet wird. Das template-Argument `Period` ist eine Instanziierung von [ratio](../standard-library/ratio.md), mit dem die Größe des von jeder Zeiteinheit dargestellten Intervalls beschrieben wird.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|duration::period Typedef|Stellt ein Synonym für den Vorlagenparameter `Period` dar.|
|duration::rep Typedef|Stellt ein Synonym für den Vorlagenparameter `Rep` dar.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[duration](#duration)|Erstellt ein `duration`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[count](#count)|Gibt die Anzahl von Zeiteinheiten im Zeitintervall zurück.|
|[max](#max)|Statisch. Gibt den maximal zulässigen Wert des Vorlagenparameters `Ref` zurück.|
|[min](#min)|Statisch. Gibt den niedrigsten zulässigen Wert des Vorlagenparameters `Ref` zurück.|
|[Zins](#zero)|Statisch. Tatsächlich wird `Rep`(0) zurückgegeben.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[Duration:: Operator-](#operator-)|Gibt eine Kopie des `duration`-Objekts zusammen mit einer negierten Taktanzahl zurück.|
|[Duration:: Operator--](#operator--)|Verringert die gespeicherte Taktanzahl.|
|[Duration:: Operator =](#op_eq)|Reduziert die gespeicherte Taktanzahl-Modulo um einen angegebenen Wert.|
|[Duration:: Operator * =](#op_star_eq)|Multipliziert die gespeicherte Taktanzahl mit einem angegebenen Wert.|
|[Duration:: Operator/=](#op_div_eq)|Dividiert die gespeicherte Taktanzahl durch die Taktanzahl eines angegebenen `duration`-Objekts.|
|[Duration:: Operator +](#op_add)|Gibt zurück **`*this`** .|
|[Duration:: Operator + +](#op_add_add)|Erhöht die gespeicherte Taktanzahl.|
|[Duration:: Operator + =](#op_add_eq)|Fügt der gespeicherten Taktanzahl die Taktanzahl eines angegebenen `duration`-Objekts hinzu.|
|[Duration:: Operator-=](#operator-_eq)|Subtrahiert die Taktanzahl eines angegebenen `duration`-Objekts von der gespeicherten Taktanzahl.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<chrono>

**Namespace:** std::chrono

## <a name="durationcount"></a><a name="count"></a>Dauer:: count

Ruft die Anzahl von Zeiteinheiten im Zeitintervall ab.

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Zeiteinheiten im Zeitintervall.

## <a name="durationduration-constructor"></a><a name="duration"></a>Dauer::d urationskonstruktor

Erstellt ein `duration`-Objekt.

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>Parameter

*Rep2*\
Ein arithmetischer Typ, der die Anzahl von Zeiteinheiten darstellt.

*Period2*\
Eine `std::ratio`-Vorlagenspezialisierung zur Darstellung des Zeitraums von Zeiteinheiten in Sekunden.

*R*\
Die Anzahl der Zeiteinheiten der Standardperiode.

*Local*\
Die Anzahl der Ticks des durch *Period2*angegebenen Zeitraums.

### <a name="remarks"></a>Bemerkungen

Vom Standardkonstruktor wird ein nicht initialisiertes Objekt erstellt. Durch die Wertinitialisierung mithilfe von leeren Klammern wird ein Objekt initialisiert, das ein Zeitintervall mit null Zeiteinheiten darstellt.

Mit dem zweiten, einem Vorlagen Argument-Konstruktor wird ein-Objekt erstellt, das ein Zeitintervall von *R* -Takt Ticks mit einem Standard Zeitraum von darstellt `std::ratio<1>` . Um das Abrunden der Takt Anzahl zu vermeiden, ist es ein Fehler, ein Duration-Objekt aus einem Darstellungstyp zu erstellen *Rep2* , das als Gleit kommatyp behandelt werden kann, wenn `duration::rep` nicht als Gleit kommatyp behandelt werden kann.

Der dritte, zwei Vorlagen Argument-Konstruktor erstellt ein-Objekt, das ein Zeitintervall darstellt, dessen Länge das von *Dur*angegebene Zeitintervall ist. Um die Verkürzung von Taktanzahlen zu vermeiden, ist das Erstellen eines Dauerobjekts aus einem anderen Dauerobjekt, dessen Typ mit dem Zieltyp *unvereinbar* ist, ein Fehler.

Ein Duration `D1` -Typ ist mit einem anderen Duration-Typ nicht *verwendbar* , `D2` Wenn nicht als Gleit `D2` kommatyp behandelt werden kann und [ratio_divide \<D1::period, D2::period> :: Type::d en](../standard-library/ratio.md) nicht 1 ist.

Wenn *Rep2* nicht implizit in konvertierbar ist `rep` und entweder " `treat_as_floating_point<rep>` *true* " oder " `treat_as_floating_point<Rep2>` *false" enthält*, wird der zweite Konstruktor nicht an der Überladungs Auflösung beteiligt. Weitere Informationen finden Sie unter [<type_traits>](../standard-library/type-traits.md).

Sofern kein Überlauf in die Konvertierung induziert wurde und `treat_as_floating_point<rep>` nicht *TRUE* ist bzw. beide `ratio_divide<Period2, period>::den` nicht 1 entsprechen und `treat_as_floating_point<Rep2>` nicht *FALSE* ist, wird der dritte Konstruktor nicht an der Überladungsauflösung beteiligt. Weitere Informationen finden Sie unter [<type_traits>](../standard-library/type-traits.md).

## <a name="durationmax"></a><a name="max"></a>Dauer:: Max

Statische Methode, von der die Obergrenze für Werte vom Vorlagenparametertyp `Ref` zurückgegeben wird.

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>Rückgabewert

Tatsächlich wird `duration(duration_values<rep>::max())` zurückgegeben.

## <a name="durationmin"></a><a name="min"></a>Dauer:: min

Statische Methode, von der die Untergrenze für Werte vom Vorlagenparametertyp `Ref` zurückgegeben wird.

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>Rückgabewert

Tatsächlich wird `duration(duration_values<rep>::min())` zurückgegeben.

## <a name="durationoperator-"></a><a name="operator-"></a>Duration:: Operator-

Gibt eine Kopie des `duration`-Objekts zusammen mit einer negierten Taktanzahl zurück.

```cpp
constexpr duration operator-() const;
```

## <a name="durationoperator--"></a><a name="operator--"></a>Duration:: Operator--

Verringert die gespeicherte Taktanzahl.

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Methode gibt zurück **`*this`** .

Die zweite Methode gibt eine Kopie von zurück **`*this`** , die vor dem Dekrement erstellt wird.

## <a name="durationoperator"></a><a name="op_eq"></a>Duration:: Operator =

Reduziert die gespeicherte Taktanzahl-Modulo um einen angegebenen Wert.

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parameter

*Div*\
Für die erste Methode stellt *div* eine Takt Anzahl dar. Bei der zweiten Methode ist *div* ein- `duration` Objekt, das eine Takt Anzahl enthält.

### <a name="return-value"></a>Rückgabewert

Das `duration`-Objekt nach dem Modulo-Vorgang wird ausgeführt.

## <a name="durationoperator"></a><a name="op_star_eq"></a>Duration:: Operator * =

Multipliziert die gespeicherte Taktanzahl mit einem angegebenen Wert.

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>Parameter

*Mult*\
Ein Wert des von `duration::rep` angegebenen Typs.

### <a name="return-value"></a>Rückgabewert

Das `duration`-Objekt nach Ausführung der Multiplikation.

## <a name="durationoperator"></a><a name="op_div_eq"></a>Duration:: Operator/=

Dividiert die gespeicherte Taktanzahl mit einem angegebenen Wert.

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>Parameter

*Div*\
Ein Wert des von `duration::rep` angegebenen Typs.

### <a name="return-value"></a>Rückgabewert

Das `duration`-Objekt nach Ausführung der Division.

## <a name="durationoperator"></a><a name="op_add"></a>Duration:: Operator +

Gibt zurück **`*this`** .

```cpp
constexpr duration operator+() const;
```

## <a name="durationoperator"></a><a name="op_add_add"></a>Duration:: Operator + +

Erhöht die gespeicherte Taktanzahl.

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>Rückgabewert

Die erste Methode gibt zurück **`*this`** .

Die zweite Methode gibt eine Kopie von zurück **`*this`** , die vor dem Inkrement erstellt wird.

## <a name="durationoperator"></a><a name="op_add_eq"></a>Duration:: Operator + =

Fügt der gespeicherten Taktanzahl die Taktanzahl eines angegebenen `duration`-Objekts hinzu.

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>Parameter

*Local*\
Ein `duration`-Objekt.

### <a name="return-value"></a>Rückgabewert

Das `duration`-Objekt nach Ausführung der Addition.

## <a name="durationoperator-"></a><a name="operator-_eq"></a>Duration:: Operator-=

Subtrahiert die Taktanzahl eines angegebenen `duration`-Objekts von der gespeicherten Taktanzahl.

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>Parameter

*Local*\
Ein `duration`-Objekt.

### <a name="return-value"></a>Rückgabewert

Das `duration`-Objekt nach Ausführung der Subtraktion.

## <a name="durationzero"></a><a name="zero"></a>Duration:: Zero

Gibt `duration(duration_values<rep>::zero())`zurück.

```cpp
static constexpr duration zero();
```

## <a name="durationoperator-mod"></a><a name="op_mod_eq"></a>Duration:: Operator mod =

Reduziert die gespeicherte Taktanzahl-Modulo Div oder Div.count().

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>Parameter

*Div*\
Der Divisor, der ein Duration-Objekt oder ein Wert ist, der Taktzähler darstellt.

### <a name="remarks"></a>Bemerkungen

Die erste Memberfunktion reduziert die gespeicherte Taktanzahl-Modulo Div und gibt *dies zurück. Die zweite Memberfunktion reduziert die gespeicherte Taktanzahl-Modulo Div.count() und gibt \*dies zurück.

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values-Struktur](../standard-library/duration-values-structure.md)
