---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: 9d2f3097637b3708c16f3048a34dd32b7f6fd80b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840140"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Definiert das Valarray-Klassen Vorlagen-und zahlreiche unterstützende Klassen Vorlagen und-Funktionen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<valarray>

**Namespace:** std

> [!NOTE]
> Die \<valarray> Bibliothek verwendet die Anweisung "#include <initializer_list>".

## <a name="remarks"></a>Bemerkungen

Diese Klassen Vorlagen und-Funktionen sind im Interesse einer verbesserten Leistung ungewöhnliche Breitengrade. Insbesondere kann jede Funktion, die den Typ zurück `valarray<T1>` gibt, ein Objekt eines anderen Typs T2 zurückgeben. In diesem Fall muss jede Funktion, die ein oder mehrere Argumente des Typs akzeptiert, `valarray<T2>` über Ladungen haben, die beliebige Kombinationen dieser Argumente akzeptieren, die jeweils durch ein Argument des Typs T2 ersetzt werden.

## <a name="members"></a>Member

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[Stäbchen](../standard-library/valarray-functions.md#abs)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem absoluten Wert der Elemente des valarray-Eingabeobjekts sind.|
|[ACOS](../standard-library/valarray-functions.md#acos)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Arkuskosinus der Elemente des valarray-Eingabeobjekts sind.|
|[ASIN](../standard-library/valarray-functions.md#asin)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Arkussinus der Elemente des valarray-Eingabeobjekts sind.|
|[Atan](../standard-library/valarray-functions.md#atan)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Hauptwert des Arkustangens der Elemente des valarray-Eingabeobjekts sind.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Arkustangens der kartesischen Komponenten sind, die durch eine Kombination aus Konstanten und Elementen von valarray-Objekten angegeben sind.|
|[beginnen](../standard-library/valarray-functions.md#begin)||
|[Erzeugnissen](../standard-library/valarray-functions.md#cos)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Kosinus der Elemente des valarray-Eingabeobjekts sind.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Kosinus Hyperbolicus der Elemente des valarray-Eingabeobjekts sind.|
|[end](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich der natürlichen Exponentialfunktion der Elemente des valarray-Eingabeobjekts sind.|
|[angezeigt](../standard-library/valarray-functions.md#log)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem natürlichen Logarithmus der Elemente des valarray-Eingabeobjekts sind.|
|[LOG10](../standard-library/valarray-functions.md#log10)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Logarithmus zur Basis 10 (dekadischer Logarithmus) der Elemente des valarray-Eingabeobjekts sind.|
|[Pow](../standard-library/valarray-functions.md#pow)|Verarbeitet die Elemente von valarray-Eingabeobjekten und Konstanten und gibt ein valarray-Objekt zurück, dessen Elemente gleich einer mit einem Exponenten potenzierten Basis sind, wobei Basis und Exponent jeweils durch die Elemente eines valarray-Eingabeobjekts oder eine Konstante angegeben sind.|
|[Tod](../standard-library/valarray-functions.md#sin)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Sinus der Elemente des valarray-Eingabeobjekts sind.|
|[sinh](../standard-library/valarray-functions.md#sinh)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Sinus Hyperbolicus der Elemente des valarray-Eingabeobjekts sind.|
|[SQRT](../standard-library/valarray-functions.md#sqrt)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich der Quadratwurzel der Elemente des valarray-Eingabeobjekts sind.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[ungs](../standard-library/valarray-functions.md#tan)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Tangens der Elemente des valarray-Eingabeobjekts sind.|
|[tanh](../standard-library/valarray-functions.md#tanh)|Verarbeitet die Elemente eines valarray-Eingabeobjekts und gibt ein valarray-Objekt zurück, dessen Elemente gleich dem Tangens Hyperbolicus der Elemente des valarray-Eingabeobjekts sind.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator! =](../standard-library/valarray-operators.md#op_neq)|Überprüft, ob die entsprechenden Elemente von zwei gleich großen valarray-Objekten ungleich sind oder ob alle Elemente eines valarray-Objekts entsprechend einem angegebenen Wert des Elementtyps des valarray-Objekts ungleich sind.|
|[KOM](../standard-library/valarray-operators.md#op_mod)|Ruft den Rest der Division der entsprechenden Elemente von zwei gleich großen valarray-Objekten oder der Division eines valarray-Objekts durch einen angegebenen Wert des valarray Elementtyps oder der Division eines angegebenen Werts durch ein valarray-Objekt ab.|
|[Operator&](../standard-library/valarray-operators.md#op_amp)|Ruft das bitweise `AND` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps ab.|
|[Operator&&](../standard-library/valarray-operators.md#op_amp_amp)|Ruft das logische `AND` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.|
|[Operator>](../standard-library/valarray-operators.md#op_gt)|Überprüft, ob die Elemente eines valarray-Objekts größer sind als die Elemente eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer oder kleiner sind als ein angegebener Wert des Elementtyps des valarray-Objekts.|
|[Operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Überprüft, ob die Elemente eines valarray-Objekts größer gleich den Elementen eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer gleich oder kleiner gleich einem angegebenen Wert sind.|
|[Operator>>](../standard-library/valarray-operators.md#op_gt_gt)|Verschiebt die Bits für jedes Element eines valarray-Objekts um eine angegebene Anzahl von Positionen oder um einen elementweisen Betrag, der durch ein zweites valarray-Objekt angegeben ist, nach rechts.|
|[Operator<](../standard-library/valarray-operators.md#op_lt)|Überprüft, ob die Elemente eines valarray-Objekts kleiner sind als die Elemente eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer oder kleiner sind als ein angegebener Wert.|
|[Operator<=](../standard-library/valarray-operators.md#op_lt_eq)|Überprüft, ob die Elemente eines valarray-Objekts kleiner gleich den Elementen eines gleich großen valarray-Objekts oder ob alle Elemente eines valarray-Objekts größer gleich oder kleiner gleich einem angegebenen Wert sind.|
|[Operator<<](../standard-library/valarray-operators.md#op_lt_lt)|Verschiebt die Bits für jedes Element eines valarray-Objekts um eine angegebene Anzahl von Positionen oder um einen elementweisen Betrag, der durch ein zweites valarray-Objekt angegeben ist, nach links.|
|[KOM](../standard-library/valarray-operators.md#op_star)|Ruft das elementweise Produkt zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.|
|[Operator +](../standard-library/valarray-operators.md#op_add)|Ruft die elementweise Summe zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.|
|[KOM](../standard-library/valarray-operators.md#operator-)|Ruft die elementweise Differenz zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.|
|[KOM](../standard-library/valarray-operators.md#op_div)|Ruft den elementweise Quotienten zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.|
|[Operator = =](../standard-library/valarray-operators.md#op_eq_eq)|Überprüft, ob die entsprechenden Elemente von zwei gleich großen valarray-Objekten gleich sind oder ob alle Elemente eines valarray-Objekts entsprechend einem angegebenen Wert des Elementtyps des valarray-Objekts gleich sind.|
|[Operator ^](../standard-library/valarray-operators.md#op_xor)|Ruft das bitweise exklusive `OR` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps ab.|
|[operator|](../standard-library/valarray-operators.md#op_or)|Ruft das bitweise `OR` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps ab.|
|[operator||](../standard-library/valarray-operators.md#op_lor)|Ruft das logische `OR` zwischen den entsprechenden Elementen von zwei gleich großen valarray-Objekten oder zwischen einem valarray-Objekt und einem angegebenen Wert des Elementtyps des valarray-Objekts ab.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[Gslice-Klasse](../standard-library/gslice-class.md)|Eine Hilfsklasse der valarray-Klasse, die zum Definieren von mehrdimensionalen Segmenten eines valarray-Objekts verwendet wird.|
|[Gslice_array-Klasse](../standard-library/gslice-array-class.md)|Eine interne, zusätzliche Klassen Vorlage, die allgemeine Slice-Objekte unterstützt, indem Vorgänge zwischen Teilmengen Arrays bereitgestellt werden, die durch das allgemeine Slice eines Valarray-Objekts definiert werden.|
|[Indirect_array-Klasse](../standard-library/indirect-array-class.md)|Eine interne, zusätzliche Klassen Vorlage, die Objekte unterstützt, die Teilmengen von Valarray sind, indem Vorgänge zwischen Teilmengen Arrays bereitgestellt werden, die durch Angeben einer Teilmenge von Indizes eines übergeordneten Valarray-Objekts definiert werden.|
|[Mask_array-Klasse](../standard-library/mask-array-class.md)|Eine interne, zusätzliche Klassen Vorlage, die Objekte unterstützt, die Teilmengen von übergeordneten Valarray-Objekten sind, die mit einem booleschen Ausdruck angegeben werden, indem Vorgänge zwischen den Teilmengen Arrays bereitgestellt werden.|
|[Slice-Klasse](../standard-library/slice-class.md)|Eine Hilfsklasse für die valarray-Klasse, die dazu verwendet wird, eindimensionale vektorähnliche Teilmengen eines valarray-Objekts zu definieren.|
|[Slice_array-Klasse](../standard-library/slice-array-class.md)|Eine interne Hilfsklassen Vorlage, die Slice-Objekte unterstützt, indem Vorgänge zwischen Teilmengen Arrays bereitgestellt werden, die durch das Slice eines Valarray-Objekts definiert werden.|
|[Valarray-Klasse](../standard-library/valarray-class.md)|In der Klassen Vorlage wird ein Objekt beschrieben, das eine Sequenz von Elementen des Typs steuert, `Type` die als Array gespeichert werden und für die Ausführung von hoch Geschwindigkeits mathematischen Operationen entworfen wurden, die für die Rechenleistung optimiert sind.|

### <a name="specializations"></a>Spezialisierungen

|Name|Beschreibung|
|-|-|
|[Valarray- \<bool> Klasse](../standard-library/valarray-bool-class.md)|Eine spezialisierte Version des Valarray-Klassen Vorlagen \<**Type**> Elements für Elemente des Typs **`bool`** .|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)
