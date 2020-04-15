---
title: SafeInt-Funktionen
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: c1c5593aee19254d4348d4e8658ffe9c3f0cf1b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368252"
---
# <a name="safeint-functions"></a>SafeInt-Funktionen

Die SafeInt-Bibliothek stellt mehrere Funktionen bereit, die Sie verwenden können, ohne eine Instanz der [SafeInt-Klasse](../safeint/safeint-class.md) zu erstellen. Wenn Sie einen einzelnen mathematischen Vorgang vor Ganzzahlüberlauf schützen möchten, können Sie diese Funktionen verwenden. Wenn Sie mehrere mathematische Vorgänge schützen möchten, sollten Sie `SafeInt`-Objekte erstellen. Es ist jedoch effizienter, `SafeInt`-Objekte zu erstellen, anstatt diese Funktionen mehrmals zu verwenden.

Mit diesen Funktionen können Sie mathematische Operationen mit zwei verschiedenen Typen von Parametern vergleichen oder ausführen, ohne sie zuerst in denselben Typ konvertieren zu müssen.

Jede dieser Funktionen hat zwei Vorlagentypen: `T` und `U`. Jeder dieser Typen kann ein boolescher Wert, Zeichen oder integraler Typ sein. Integrale Typen können mit oder ohne Vorzeichen sein und eine beliebige Größe von 8 Bits bis 64 Bits haben.

> [!NOTE]
> Die neueste Version dieser Bibliothek [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt)befindet sich unter .

## <a name="in-this-section"></a>In diesem Abschnitt

Funktion                      | BESCHREIBUNG
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | Addiert zwei Zahlen und schützt vor Überlauf.
[SafeCast](#safecast)         | Wandelt einen Parametertyp in einen anderen Typ um.
[SafeDivide](#safedivide)     | Dividiert zwei Zahlen und schützt vor Division durch 0 (null).
[SafeEquals](#safeequals), [SafeGreaterThan](#safegreaterthan), [SafeGreaterThanEquals](#safegreaterthanequals), [SafeLessThan](#safelessthan), [SafeLessThanEquals](#safelessthanequals), [SafeNotEquals](#safenotequals) | Vergleicht zwei Zahlen. Mit diesen Funktionen können Sie zwei verschiedene Typen von Zahlen vergleichen, ohne ihre Typen zu ändern.
[SafeModulus](#safemodulus)   | Führt die Modulooperation für zwei Zahlen durch.
[SafeMultiply](#safemultiply) | Multipliziert zwei Zahlen miteinander und schützt vor Überlauf.
[SafeSubtract](#safesubtract) | Subtrahiert zwei Zahlen und schützt vor Überlauf.

## <a name="related-sections"></a>Verwandte Abschnitte

`Section`                                                  | BESCHREIBUNG
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | Die `SafeInt`-Klasse.
[SafeIntException](../safeint/safeintexception-class.md) | Die Exception-Klasse, die für die SafeInt-Bibliothek spezifisch ist.

## <a name="safeadd"></a><a name="safeadd"></a>SafeAdd

Addiert zwei Zahlen in einer Weise, die vor Überlauf schützt.

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu addierende Zahl. Muss vom Typ T sein.

*U*<br/>
[in] Die zweite zu addierende Zahl. Muss vom Typ U sein.

*result*<br/>
[out] Der Parameter, in dem `SafeAdd` das Ergebnis speichert.

### <a name="return-value"></a>Rückgabewert

**true**, wenn kein Fehler auftritt; **false**, wenn ein Fehler auftritt.

## <a name="safecast"></a><a name="safecast"></a>SafeCast

Wandelt einen Zahlentyp in einen anderen Typ um.

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>Parameter

*From*<br/>
[in] Die zu konvertierende Quellzahl. Muss vom Typ `T` sein.

*An*<br/>
[out] Ein Verweis auf den neuen Zahlentyp. Muss vom Typ `U` sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn kein Fehler auftritt; **false**, wenn ein Fehler auftritt.

## <a name="safedivide"></a><a name="safedivide"></a>SafeDivide

Dividiert zwei Zahlen in einer Weise, die vor Division durch 0 (null) schützt.

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Der Divisor. Muss vom Typ T sein.

*U*<br/>
[in] Der Dividend. Muss vom Typ U sein.

*result*<br/>
[out] Der Parameter, in dem `SafeDivide` das Ergebnis speichert.

### <a name="return-value"></a>Rückgabewert

**true**, wenn kein Fehler auftritt; **false**, wenn ein Fehler auftritt.

## <a name="safeequals"></a><a name="safeequals"></a>SafeEquals

Vergleicht zwei Zahlen auf Gleichheit.

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu vergleichende Zahl. Muss vom Typ T sein.

*U*<br/>
[in] Die zweite zu vergleichende Zahl. Muss vom Typ U sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn *t* und *u* gleich sind, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Die Methode verbessert `==`, da Sie mit `SafeEquals` zwei verschiedene Typen von Zahlen vergleichen können.

## <a name="safegreaterthan"></a><a name="safegreaterthan"></a>SafeGreaterThan

Vergleicht zwei Zahlen.

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu vergleichende Zahl. Muss vom Typ `T` sein.

*U*<br/>
[in] Die zweite zu vergleichende Zahl. Muss vom Typ `U` sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn *t* größer als *u* ist, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

`SafeGreaterThan` erweitert den regulären Vergleichsoperator, da Sie damit zwei verschiedene Typen von Zahlen vergleichen können.

## <a name="safegreaterthanequals"></a><a name="safegreaterthanequals"></a>SafeGreaterThanEquals

Vergleicht zwei Zahlen.

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu vergleichende Zahl. Muss vom Typ `T` sein.

*U*<br/>
[in] Die zweite zu vergleichende Zahl. Muss vom Typ `U` sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn *t* größer als oder gleich *u* ist, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

`SafeGreaterThanEquals` verbessert den Standardvergleichsoperator, da Sie damit zwei verschiedene Typen von Zahlen vergleichen können.

## <a name="safelessthan"></a><a name="safelessthan"></a>SafeLessThan

Bestimmt, ob eine Zahl kleiner als eine andere ist.

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste Zahl. Muss vom Typ `T` sein.

*U*<br/>
[in] Die zweite Zahl. Muss vom Typ `U` sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn *t* kleiner als *u* ist, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Diese Methode verbessert den Standardvergleichsoperator, da Sie mit `SafeLessThan` zwei verschiedene Typen von Zahlen vergleichen können.

## <a name="safelessthanequals"></a><a name="safelessthanequals"></a>SafeLessThanEquals

Vergleicht zwei Zahlen.

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu vergleichende Zahl. Muss vom Typ `T` sein.

*U*<br/>
[in] Die zweite zu vergleichende Zahl. Muss vom Typ `U` sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn *t* kleiner als oder gleich *u* ist, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

`SafeLessThanEquals` erweitert den regulären Vergleichsoperator, da Sie damit zwei verschiedene Typen von Zahlen vergleichen können.

## <a name="safemodulus"></a><a name="safemodulus"></a>SafeModulus

Führt die Modulooperation für zwei Zahlen durch.

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Der Divisor. Muss vom Typ `T` sein.

*U*<br/>
[in] Der Dividend. Muss vom Typ `U` sein.

*result*<br/>
[out] Der Parameter, in dem `SafeModulus` das Ergebnis speichert.

### <a name="return-value"></a>Rückgabewert

**true**, wenn kein Fehler auftritt; **false**, wenn ein Fehler auftritt.

## <a name="safemultiply"></a><a name="safemultiply"></a>SafeMultiply

Multipliziert zwei Zahlen in einer Weise miteinander, die vor Überlauf schützt.

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu multiplizierende Zahl. Muss vom Typ `T` sein.

*U*<br/>
[in] Die zweite zu multiplizierende Zahl. Muss vom Typ `U` sein.

*result*<br/>
[out] Der Parameter, in dem `SafeMultiply` das Ergebnis speichert.

### <a name="return-value"></a>Rückgabewert

`true`, wenn kein Fehler auftritt; `false`, wenn ein Fehler auftritt.

## <a name="safenotequals"></a><a name="safenotequals"></a>SafeNotEquals

Bestimmt, ob zwei Zahlen ungleich sind.

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste zu vergleichende Zahl. Muss vom Typ `T` sein.

*U*<br/>
[in] Die zweite zu vergleichende Zahl. Muss vom Typ `U` sein.

### <a name="return-value"></a>Rückgabewert

**true**, wenn *t* und *u* nicht gleich sind, andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Die Methode verbessert `!=`, da Sie mit `SafeNotEquals` zwei verschiedene Typen von Zahlen vergleichen können.

## <a name="safesubtract"></a><a name="safesubtract"></a>SafeSubtract

Subtrahiert zwei Zahlen in einer Weise, die vor Überlauf schützt.

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parameter

*T*<br/>
[in] Die erste Zahl in der Subtraktion. Muss vom Typ `T` sein.

*U*<br/>
[in] Die von *t* zu subtrahierende Zahl. Muss vom Typ `U` sein.

*result*<br/>
[out] Der Parameter, in dem `SafeSubtract` das Ergebnis speichert.

### <a name="return-value"></a>Rückgabewert

**true**, wenn kein Fehler auftritt; **false**, wenn ein Fehler auftritt.
