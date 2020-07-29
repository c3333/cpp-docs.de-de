---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 2c6487370bfa4d3af6c9c7c40b7f83a252c2e01d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222575"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

Definiert die Containerklassen Vorlage `complex` und deren unterstützende Vorlagen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**:\<complex>

**Namespace:** std

## <a name="remarks"></a>Bemerkungen

Eine komplexe Zahl ist ein geordnetes Paar aus reellen Zahlen. Rein geometrisch ausgedrückt ist die komplexe Ebene die reelle zweidimensionale Ebene. Die speziellen Merkmale der komplexen Ebene, durch die sie sich von der reellen Ebene unterscheidet, sind darin begründet, dass sie eine zusätzliche algebraische Struktur hat. Diese algebraische Struktur hat zwei grundlegende Vorgänge:

- Addition definiert als (*a*, *b*) + (*c*, *d*) = (*a*  +  *c*, *b*  +  *d*)

- Multiplikation definiert als (*a*, *b*) \* (*c*, *d*) = (*AC*  -  *BD*, *AD*  +  *BC*)

Die Menge der komplexen Zahlen mit den Operationen für komplexe Addition und komplexe Multiplikation ist im standardmäßigen algebraischen Sinn ein Körper:

- Die Operationen Addition und Multiplikation sind kommutativ und assoziativ, und Multiplikation erfolgt vor Addition, genau so, wie dies für reelle Addition und Multiplikation für den Körper der reellen Zahlen der Fall ist.

- Die komplexe Zahl (0, 0) ist die additive Identität, und (1, 0) ist die multiplikative Identität.

- Der Additive umgekehrten Wert für eine komplexe Zahl (*a*, *b*) ist (-*a*,-*b*), und die multiplikative Umkehrung für alle komplexen Zahlen außer (0, 0) ist

   (*a*/(*a*<sup>2</sup>  +  *b*<sup>2</sup>),-*b*/(*a*<sup>2</sup>  +  *b*<sup>2</sup>))

Durch die Darstellung einer komplexen Zahl *z* =*(a*, *b*) in der Form *z*  =  *a*  +  *BI*, wobei *i*<sup>2</sup> =-1, können die Regeln für die Algebra des Satzes von reellen Zahlen auf die Menge der komplexen Zahlen und deren Komponenten angewendet werden. Beispiel:

   (1 + 2*i*) \* (2 + 3*i*) = 1 \* (2 + 3*i*) + 2*i* \* (2 + 3*i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7*i*

Das System der komplexen Zahlen ist ein Körper, jedoch kein geordneter Körper. Es gibt keine Reihenfolge der komplexen Zahlen, wie es für das Feld mit reellen Zahlen und deren Teilmengen gibt. Daher können Ungleichheiten nicht auf komplexe Zahlen angewendet werden, die sich auf reelle Zahlen befinden.

Es gibt drei allgemeine Formen der Darstellung einer komplexen Zahl *z*:

- Kartesisch: *z*  =  *a*  +  *BI*

- Polar: *z*  =  *r* (COS *p*  +  *i* Sin *p*)

- Exponentiell: *z*  =  *r* \* *e*<sup>*IP*</sup>

Die Ausdrücke, die in diesen Standarddarstellungen einer komplexen Zahl verwendet werden, werden wie folgt bezeichnet:

- Die reelle kartesische Komponente oder der Realteil *a*

- Die imaginäre kartesische Komponente oder der Imaginärteil *b*

- Der Modulo oder absolute Wert einer komplexen Zahl *r*.

- Der Argument-oder Phasenwinkel- *p* im Bogenmaße.

Sofern nicht anders angegeben, müssen Funktionen, die mehrere Werte zurückgeben können, einen Prinzipal Wert für ihre Argumente zurückgeben, der größer als-und kleiner oder gleich +, ist, damit Sie einen einzelnen Wert erhalten. Alle Winkel müssen in Bogenmaß ausgedrückt werden, wobei in einem Kreis 2-Bogenmaß (360 Grad) vorhanden sind.

## <a name="members"></a>Member

### <a name="functions"></a>Functions

|||
|-|-|
|[Stäbchen](../standard-library/complex-functions.md#abs)|Berechnet den Betrag einer komplexen Zahl.|
|[ACOS](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[gebeut](../standard-library/complex-functions.md#arg)|Extrahiert das Argument aus einer komplexen Zahl.|
|[ASIN](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[Atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|Gibt die konjugierte Zahl einer komplexen Zahl zurück.|
|[Erzeugnissen](../standard-library/complex-functions.md#cos)|Gibt den Kosinus einer komplexen Zahl zurück.|
|[cosh](../standard-library/complex-functions.md#cosh)|Gibt den Kosinus Hyperbolicus einer komplexen Zahl zurück.|
|[exp](../standard-library/complex-functions.md#exp)|Gibt die Exponentialfunktion einer komplexen Zahl zurück.|
|[imag](../standard-library/complex-functions.md#imag)|Extrahiert die imaginäre Komponente einer komplexen Zahl.|
|[angezeigt](../standard-library/complex-functions.md#log)|Gibt den natürlichen Logarithmus einer komplexen Zahl zurück.|
|[LOG10](../standard-library/complex-functions.md#log10)|Gibt den Zehnerlogarithmus einer komplexen Zahl zurück.|
|[norm](../standard-library/complex-functions.md#norm)|Extrahiert die Norm einer komplexen Zahl.|
|[Bär](../standard-library/complex-functions.md#polar)|Gibt die komplexe Zahl, die einem angegebenen Betrag und Argument entspricht, in kartesischer Form zurück.|
|[Pow](../standard-library/complex-functions.md#pow)|Wertet die komplexe Zahl aus, die sich dadurch ergibt, dass eine Basis, die eine komplexe Zahl ist, mit einer anderen komplexen Zahl potenziert wird.|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|Extrahiert die reelle Komponente einer komplexen Zahl.|
|[Tod](../standard-library/complex-functions.md#sin)|Gibt den Sinus einer komplexen Zahl zurück.|
|[sinh](../standard-library/complex-functions.md#sinh)|Gibt den Sinus Hyperbolicus einer komplexen Zahl zurück.|
|[SQRT](../standard-library/complex-functions.md#sqrt)|Gibt die Quadratwurzel einer komplexen Zahl zurück.|
|[ungs](../standard-library/complex-functions.md#tan)|Gibt den Tangens einer komplexen Zahl zurück.|
|[tanh](../standard-library/complex-functions.md#tanh)|Gibt den Tangens Hyperbolicus einer komplexen Zahl zurück.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Operator! =](../standard-library/complex-operators.md#op_neq)|Testet zwei komplexe Zahlen auf Ungleichheit, von denen eine oder beide einer Teilmenge des Typs für die reellen und imaginären Teile angehören.|
|[KOM](../standard-library/complex-operators.md#op_star)|Multipliziert zwei komplexe Zahlen, von denen eine oder beide einer Teilmenge des Typs für die reellen und imaginären Teile angehören.|
|[Operator +](../standard-library/complex-operators.md#op_add)|Addiert zwei komplexe Zahlen, von denen eine oder beide einer Teilmenge des Typs für die reellen und imaginären Teile angehören.|
|[KOM](../standard-library/complex-operators.md#operator-)|Subtrahiert zwei komplexe Zahlen, von denen eine oder beide einer Teilmenge des Typs für die reellen und imaginären Teile angehören.|
|[KOM](../standard-library/complex-operators.md#op_div)|Dividiert zwei komplexe Zahlen, von denen eine oder beide einer Teilmenge des Typs für die reellen und imaginären Teile angehören.|
|[Operator<\<](../standard-library/complex-operators.md#op_lt_lt)|Eine Vorlagenfunktion, die eine komplexe Zahl in den Ausgabestream einfügt.|
|[Operator = =](../standard-library/complex-operators.md#op_eq_eq)|Testet zwei komplexe Zahlen auf Gleichheit, von denen eine oder beide einer Teilmenge des Typs für die reellen und imaginären Teile angehören.|
|[Operator>>](../standard-library/complex-operators.md#op_gt_gt)|Eine Vorlagenfunktion, die einen komplexen Wert aus dem Eingabestream extrahiert.|

### <a name="classes"></a>Klassen

|||
|-|-|
|[viel\<double>](../standard-library/complex-double.md)|Die explizit spezialisierte Klassen Vorlage beschreibt ein Objekt, das ein geordnetes Paar von Objekten speichert, die beide **`double`** den Typ haben, wobei das erste Element den reellen Teil einer komplexen Zahl und das zweite den imaginären Teil darstellt.|
|[viel\<float>](../standard-library/complex-float.md)|Die explizit spezialisierte Klassen Vorlage beschreibt ein Objekt, das ein geordnetes Paar von Objekten speichert, die beide **`float`** den Typ haben, wobei das erste Element den reellen Teil einer komplexen Zahl und das zweite den imaginären Teil darstellt.|
|[viel\<long double>](../standard-library/complex-long-double.md)|Die explizit spezialisierte Klassen Vorlage beschreibt ein Objekt, das ein geordnetes Paar von Objekten speichert, die beide **`long double`** den Typ haben, wobei das erste Element den reellen Teil einer komplexen Zahl und das zweite den imaginären Teil darstellt.|
|[viel](../standard-library/complex-class.md)|In der Klassen Vorlage wird ein Objekt beschrieben, mit dem das System für komplexe Zahlen dargestellt und komplexe arithmetische Operationen durchgeführt werden.|

### <a name="literals"></a>Literale

Der- \<complex> Header definiert die folgenden [benutzerdefinierten Literale](../cpp/user-defined-literals-cpp.md) , mit denen eine komplexe Zahl erstellt wird, bei der der reelle Teil 0 (null) und der Imaginärteil der Wert des Eingabe Parameters ist.

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|Rückgabewert: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|Gibt `complex<double>{0.0, static_cast<double>(d)}` zurück.|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|Gibt `complex<float>{0.0f, static_cast<float>(d)}` zurück.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
