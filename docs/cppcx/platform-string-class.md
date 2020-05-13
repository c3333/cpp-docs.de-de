---
title: Platform::String-Klasse
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: 3f29c60d0d6a4618d97d8f750a048fcc18f976b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322111"
---
# <a name="platformstring-class"></a>Platform::String-Klasse

Stellt eine sequenzielle Auflistung von Unicode-Zeichen dar, die zum Darstellen von Text verwendet werden. Weitere Informationen und Beispiele finden Sie unter [Strings](../cppcx/strings-c-cx.md).

## <a name="syntax"></a>Syntax

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>Iterators

Zwei Iteratorfunktionen, die nicht Member der Zeichenfolgenklasse sind, können mit der Vorlagenfunktion `std::for_each` verwendet werden, um die Zeichen in einem Zeichenfolgenobjekt aufzulisten.

|Member|BESCHREIBUNG|
|------------|-----------------|
|`const char16* begin(String^ s)`|Gibt einen Zeiger auf den Anfang des angegebenen Zeichenfolgenobjekts zurück.|
|`const char16* end(String^ s)`|Gibt einen Zeiger nach dem Ende des angegebenen Zeichenfolgenobjekts zurück.|

## <a name="members"></a>Member

Die Zeichenfolgenklasse erbt vom Objekt und den Schnittstellen IDisposable, IEquatable und IPrintable.

Die Zeichenfolgenklasse verfügt auch über die folgenden Typen von Membern.

### <a name="constructors"></a>Konstruktoren

|Member|BESCHREIBUNG|
|------------|-----------------|
|[String::String](#ctor)|Initialisiert eine neue Instanz der Zeichenfolgenklasse.|

### <a name="methods"></a>Methoden

Die Zeichenfolgenklasse erbt die Methoden Equals(), Finalize(), GetHashCode(), GetType(), MemberwiseClose() und ToString() von [Platform::Object Class](../cppcx/platform-object-class.md). Die Zeichenfolge hat auch die folgenden Methoden.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[String::Begin](#begin)|Gibt einen Zeiger auf den Anfang der aktuellen Zeichenfolge zurück.|
|[String::CompareOrdinal](#compareordinal)|Vergleicht zwei `String` -Objekte durch Auswertung der numerischen Werte der entsprechenden Zeichen in den beiden Zeichenfolgenwerten, die durch die Objekte dargestellt werden.|
|[String::Concat](#concat)|Verkettet die Werte von zwei Zeichenfolgenobjekten.|
|[String::Data](#data)|Gibt einen Zeiger auf den Anfang der aktuellen Zeichenfolge zurück.|
|[String::Dispose](#dispose)|Gibt Ressourcen frei.|
|[String::Ende](#end)|Gibt einen Zeiger nach dem Ende der aktuellen Zeichenfolge zurück.|
|[String::Equals](#equals)|Gibt an, ob das angegebene Objekt gleich dem aktuellen Objekt ist.|
|[String::GetHashCode](#gethashcode)|Gibt den Hashcode für diese Instanz zurück.|
|[String::IsEmpty](#isempty)|Gibt an, ob das aktuelle String-Objekt leer ist.|
|[String::IsFastPass](#isfastpass)|Gibt an, ob das aktuelle String-Objekt an einem *Schnellpassvorgang* beteiligt ist. Bei einem Fast-Pass-Vorgang wird die Verweiszählung angehalten.|
|[String::Länge](#length)|Ruft die Länge des aktuellen Zeichenfolgenobjekts ab.|
|[String::ToString](#tostring)|Gibt ein neues Zeichenfolgenobjekt zurück, dessen Wert mit der aktuellen Zeichenfolge identisch ist.|

### <a name="operators"></a>Operatoren

Die String-Klasse verfügt über die folgenden Operatoren.

|Member|BESCHREIBUNG|
|------------|-----------------|
|[String::operator== Operator](#operator-equality)|Gibt an, ob zwei angegebene String-Objekte denselben Wert haben.|
|[operator+-Operator](#operator-plus)|Verkettet zwei Zeichenfolgeobjekte in ein neues Zeichenfolgeobjekt.|
|[String::operator> Operator](#operator-greater-than)|Gibt an, ob der Wert eines Zeichenfolgenobjekts größer als der Wert eines zweiten Zeichenfolgenobjekts ist.|
|[String::operator>= Operator](#operator-greater-than-or-equals)|Gibt an, ob der Wert eines String-Objekts größer oder gleich dem Wert eines zweiten String-Objekts ist.|
|[String::operator!= Operator](#operator-inequality)|Gibt an, ob zwei angegebene String-Objekte unterschiedliche Werte aufweisen.|
|[String::operator< Operator](#operator-less-than)|Gibt an, ob der Wert eines Zeichenfolgenobjekts kleiner als der Wert eines zweiten Zeichenfolgenobjekts ist.|

### <a name="requirements"></a>Anforderungen

**Mindestens unterstützter Client:** Windows 8

**Minimal unterstützter Server:** Windows Server 2012

**Namespace:** Platform

**Header** vccorlib.h (standardmäßig eingeschlossen)

## <a name="stringbegin-method"></a><a name="begin"></a>String::Begin-Methode

Gibt einen Zeiger auf den Anfang der aktuellen Zeichenfolge zurück.

### <a name="syntax"></a>Syntax

```cpp
char16* Begin();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Anfang der aktuellen Zeichenfolge.

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>String::CompareOrdinal-Methode

Statische Methode, die `String` zwei Objekte vergleicht, indem die numerischen Werte der entsprechenden Zeichen in den beiden Zeichenfolgenwerten ausgewertet werden, die von den Objekten dargestellt werden.

### <a name="syntax"></a>Syntax

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste String-Objekt.

*str2*<br/>
Das zweite String-Objekt.

### <a name="return-value"></a>Rückgabewert

Eine ganze Zahl, die die lexikalische Beziehung zwischen den beiden Vergleichswerten angibt. In der folgenden Tabelle sind die möglichen Rückgabewerte aufgelistet:

|Wert|Bedingung|
|-----------|---------------|
|-1|`str1` ist kleiner als `str2`.|
|0|`str1` ist gleich `str2`.|
|1|`str1` ist größer als `str2`.|

## <a name="stringconcat-method"></a><a name="concat"></a>String::Concat-Methode

Verkettet die Werte von zwei Zeichenfolgenobjekten.

### <a name="syntax"></a>Syntax

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste Zeichenfolgenobjekt oder `null`.

*str2*<br/>
Das zweite Zeichenfolgenobjekt oder `null`.

### <a name="return-value"></a>Rückgabewert

Ein neues Zeichenfolgen^-Objekt, dessen Wert die Verkettung der Werte von `str1` und `str2` ist.

Wenn `str1``null` und `str2` ungleich null ist, wird `str1` zurückgegeben. Wenn `str2``null` und `str1` ungleich null ist, wird `str2` zurückgegeben. Wenn `str1` und `str2` beide `null` sind, wird die leere Zeichenfolge (L "") zurückgegeben.

## <a name="stringdata-method"></a><a name="data"></a>String::Data-Methode

Gibt einen Zeiger zum Anfang des Datenpuffers des Objekts als ein Array im C-Format mit `char16`-Elementen (`wchar_t`) zurück.

### <a name="syntax"></a>Syntax

```cpp
const char16* Data();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den `const char16` Anfang eines Arrays`char16` von Unicode-Zeichen (ist ein typedef für `wchar_t`).

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode zum Konvertieren von `Platform::String^` zu `wchar_t*`. Wenn das `String`-Objekt den Gültigkeitsbereich verlässt, ist die Gültigkeit des Datenzeigers nicht mehr sichergestellt. Um die Daten über die `String` Lebensdauer des ursprünglichen Objekts hinaus zu speichern, verwenden Sie [wcscpy_s,](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) um das Array in den Speicher zu kopieren, den Sie selbst zugewiesen haben.

## <a name="stringdispose-method"></a><a name="dispose"></a>String::Dispose-Methode

Gibt Ressourcen frei.

### <a name="syntax"></a>Syntax

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>String::End-Methode

Gibt einen Zeiger nach dem Ende der aktuellen Zeichenfolge zurück.

### <a name="syntax"></a>Syntax

```cpp
char16* End();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger zur Übergabe des Endes der aktuellen Zeichenfolge.

### <a name="remarks"></a>Bemerkungen

End() gibt Begin() + Length zurück.

## <a name="stringequals-method"></a><a name="equals"></a>String::Equals-Methode

Gibt an, ob die angegebene Zeichenfolge über den gleichen Wert wie das aktuelle Objekt verfügt.

### <a name="syntax"></a>Syntax

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Das zu vergleichende Objekt.

### <a name="return-value"></a>Rückgabewert

**true,** wenn `str` es gleich dem aktuellen Objekt ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Diese Methode entspricht der statischen [String::CompareOrdinal](#compareordinal). In der ersten Überladung wird erwartet, dass der Parameter `str` zu einem String^-Objekt umgewandelt werden kann.

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>String::GetHashCode-Methode

Gibt den Hashcode für diese Instanz zurück.

### <a name="syntax"></a>Syntax

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>Rückgabewert

Der Hashcode für diese Instanz.

## <a name="stringisempty-method"></a><a name="isempty"></a>String::IsEmpty-Methode

Gibt an, ob das aktuelle String-Objekt leer ist.

### <a name="syntax"></a>Syntax

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn `String` das aktuelle Objekt **null** oder die leere Zeichenfolge (L"") ist; andernfalls **false**.

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>String::IsFastPass-Methode

Gibt an, ob das aktuelle String-Objekt an einem *Schnellpassvorgang* beteiligt ist. Bei einem Fast-Pass-Vorgang wird die Verweiszählung angehalten.

### <a name="syntax"></a>Syntax

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn `String` das aktuelle Objekt schnell vorbei ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Beim Aufruf einer Funktion, bei der ein Objekt mit Verweiszählung ein Parameter ist und die aufgerufene Funktion nur dieses Objekt liest, kann der Compiler die Verweiszählung sicher anhalten und die Aufrufleistung verbessern. Es gibt nichts nützliches, das Ihr Code mit dieser Eigenschaft ausführen kann. Das System behandelt alle Details.

## <a name="stringlength-method"></a><a name="length"></a>String::Length-Methode

Ruft die Anzahl der Zeichen `String` im aktuellen Objekt ab.

### <a name="syntax"></a>Syntax

```cpp
unsigned int Length();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Zeichen `String` im aktuellen Objekt.

### <a name="remarks"></a>Bemerkungen

Die Länge einer Zeichenfolge ohne Zeichen ist null. Die Länge der folgenden Zeichenfolge ist 5:

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

Das Zeichenarray, das von [String::Data](#data) zurückgegeben wird, hat ein zusätzliches Zeichen, das das beendende NULL oder '''''' ist. Dieses Zeichen ist ebenfalls zwei Bytes lang.

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>String::operator+ Operator

Verkettet zwei [String-Objekte](../cppcx/platform-string-class.md) in einem neuen [String-Objekt.](../cppcx/platform-string-class.md)

### <a name="syntax"></a>Syntax

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste `String`-Objekt.

*str2*<br/>
Das zweite `String`-Objekt, dessen Inhalt `str1` angefügt wird.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn *str1* gleich *str2*ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Dieser Operator erstellt ein `String^`-Objekt mit den Daten aus den zwei Operanden. Verwenden Sie es zur Vereinfachung, wenn nicht unbedingt extreme Leistung gefordert ist. Einige Aufrufe von "`+`" in einer Funktion werden sich wahrscheinlich nicht bemerkbar machen. Wenn Sie jedoch große Objekte oder Textdaten in einer kurzen Schleife bearbeiten, sollten Sie die standardmäßigen C++-Mechanismen und -typen verwenden.

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>String::operator== Operator

Gibt an, ob zwei angegebene Zeichenfolgenobjekte denselben Textwert haben.

### <a name="syntax"></a>Syntax

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste zu vergleichende `String`-Objekt.

*str2*<br/>
Das zweite zu vergleichende `String`-Objekt.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn `str1` der Inhalt `str2`von gleich ist; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Dieser Operator entspricht [String::CompareOrdinal](#compareordinal).

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>String::Operator&gt;

Gibt an, ob `String` der Wert eines Objekts `String` größer als der Wert eines zweiten Objekts ist.

### <a name="syntax"></a>Syntax

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste `String`-Objekt.

*str2*<br/>
Das zweite `String`-Objekt.

### <a name="return-value"></a>Rückgabewert

**true,** wenn `str1` der Wert von `str2`größer ist als der Wert von ; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Dieser Operator entspricht dem expliziten Aufrufen von [String::CompareOrdinal](#compareordinal) und dem Abrufen eines Ergebnisses größer als Null.

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>String::Operator&gt;=

Gibt an, ob `String` der Wert eines Objekts größer `String` oder gleich dem Wert eines zweiten Objekts ist.

### <a name="syntax"></a>Syntax

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste `String`-Objekt.

*str2*<br/>
Das zweite `String`-Objekt.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn `str1` der Wert von größer oder `str2`gleich dem Wert von ist; andernfalls **false**.

## <a name="stringoperator"></a><a name="operator-inequality"></a>String::operator!=

Gibt an, `String` ob zwei angegebene Objekte unterschiedliche Werte aufweisen.

### <a name="syntax"></a>Syntax

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste zu vergleichende `String`-Objekt.

*str2*<br/>
Das zweite zu vergleichende `String`-Objekt.

### <a name="return-value"></a>Rückgabewert

**wahr,** wenn `str1` nicht `str2`gleich ist ; andernfalls **false**.

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>String::Operator&lt;

Gibt an, ob `String` der Wert eines Objekts `String` kleiner als der Wert eines zweiten Objekts ist.

### <a name="syntax"></a>Syntax

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>Parameter

*str1*<br/>
Das erste `String`-Objekt.

*str2*<br/>
Das zweite `String`-Objekt.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der Wert von *str1* kleiner als der Wert von *str2*ist; andernfalls **false**.

## <a name="stringstring-constructor"></a><a name="ctor"></a>String::String-Konstruktor

Initialisiert eine neue Instanz `String` der Klasse mit einer Kopie der Eingabezeichenfolgendaten.

### <a name="syntax"></a>Syntax

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>Parameter

*s*<br/>
Eine Reihe von Breitzeichen, die die Zeichenfolge initialisieren. char16

*n*<br/>
Eine Zahl, die die Länge der Zeichenfolge angibt.

### <a name="remarks"></a>Bemerkungen

Wenn die Leistung entscheidend ist und Sie die Lebensdauer der Quellzeichenfolge steuern, können Sie [Platform::StringReference](../cppcx/platform-stringreference-class.md) anstelle von String verwenden.

### <a name="example"></a>Beispiel

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>String::ToString

Gibt `String` ein Objekt zurück, dessen Wert mit der aktuellen Zeichenfolge identisch ist.

### <a name="syntax"></a>Syntax

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>Rückgabewert

Ein `String` Objekt, dessen Wert mit der aktuellen Zeichenfolge identisch ist.

## <a name="see-also"></a>Siehe auch

[Plattformnamespace](../cppcx/platform-namespace-c-cx.md)
