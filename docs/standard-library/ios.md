---
title: '&lt;ios&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ios>
- ios/std::<ios>
helpviewer_keywords:
- ios header
ms.assetid: d3d4c161-2f37-4f04-93cc-0a2a89984a9c
ms.openlocfilehash: 8ba03e5ab5dd90a6f29e08b01576803a00f0bd24
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845483"
---
# <a name="ltiosgt"></a>&lt;ios&gt;

Definiert verschiedene Typen und Funktionen, die grundlegend für den Umgang mit iostreams sind. Dieser Header wird in der Regel von einem anderen iostream-Header eingeschlossen. Sie müssen ihn nur selten direkt einschließen.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: \<ios>

**Namespace:** std

> [!NOTE]
> Die- \<ios> Bibliothek verwendet die- `#include <iosfwd>` Anweisung.

## <a name="remarks"></a>Bemerkungen

Eine große Gruppe von Funktionen sind Manipulatoren. Ein in deklarierter Manipulator \<ios> ändert die Werte, die im Argument Objekt der Klasse [ios_base](../standard-library/ios-base-class.md)gespeichert sind. Andere Manipulatoren führen Aktionen für Streams aus, die von Objekten eines Typs gesteuert werden, der von dieser Klasse abgeleitet wird, z. b. eine Spezialisierung einer der Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md) oder [basic_ostream](../standard-library/basic-ostream-class.md). Beispielsweise löscht [noskipws](../standard-library/ios-functions.md#noskipws)(**Str**) das formatflag `ios_base::skipws` im-Objekt `str` , das einen dieser Typen aufweisen kann.

Aufgrund von speziellen Einfüge- und Extraktionsvorgängen für die aus `ios_base` abgeleiteten Klassen können Sie einen Manipulator auch aufrufen, indem Sie ihn in einen Ausgabestream einfügen oder ihn aus einem Eingabestream extrahieren. Beispiel:

```cpp
istr>> noskipws;
```

Ruft [noskipws](../standard-library/ios-functions.md#noskipws)(**istr**) auf.

## <a name="members"></a>Member

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|-|-|
|[erhältlich](../standard-library/ios-typedefs.md#ios)|Unterstützt die ios-Klasse aus der alten iostream-Bibliothek.|
|[streamoff](../standard-library/ios-typedefs.md#streamoff)|Unterstützt interne Vorgänge.|
|[streampos](../standard-library/ios-typedefs.md#streampos)|Enthält die aktuelle Position des Pufferzeigers oder Dateizeigers.|
|[streamsize](../standard-library/ios-typedefs.md#streamsize)|Gibt die Größe des Streams an.|
|[wios](../standard-library/ios-typedefs.md#wios)|Unterstützt die wios-Klasse aus der alten iostream-Bibliothek.|
|[wstreampos](../standard-library/ios-typedefs.md#wstreampos)|Enthält die aktuelle Position des Pufferzeigers oder Dateizeigers.|

### <a name="manipulators"></a>Manipulatoren

|Name|Beschreibung|
|-|-|
|[boolalpha](../standard-library/ios-functions.md#boolalpha)|Gibt an, dass Variablen des Typs [bool](../cpp/bool-cpp.md) als **`true`** oder **`false`** im Stream angezeigt werden.|
|[31.12.2012](../standard-library/ios-functions.md#dec)|Gibt an, dass ganzzahlige Variablen in Basis-10-Schreibweise angezeigt werden.|
|[defaultfloat](../standard-library/ios-functions.md#ios_defaultfloat)|Konfiguriert die Flags eines `ios_base`-Objekts, sodass ein Standard-Anzeigeformat für Floatwerte verwendet wird.|
|[fixed](../standard-library/ios-functions.md#fixed)|Gibt an, dass eine Gleitkommazahl in fester Dezimalschreibweise angezeigt wird.|
|[hex](../standard-library/ios-functions.md#hex)|Gibt an, dass ganzzahlige Variablen in Basis-16-Schreibweise angezeigt werden.|
|[hexfloat](../standard-library/ios-functions.md#hexfloat)|
|[internal](../standard-library/ios-functions.md#internal)|Bewirkt, dass ein Nummernzeichen linksbündig und die Zahl rechtsbündig ausgerichtet wird.|
|[linken](../standard-library/ios-functions.md#left)|Bewirkt, dass Text, der nicht so breit ist wie die Ausgabebreite, im Stream linksbündig angezeigt wird.|
|[noboolalpha](../standard-library/ios-functions.md#noboolalpha)|Gibt an, dass Variablen des Typs [bool](../cpp/bool-cpp.md) im Stream als 1 oder 0 angezeigt werden.|
|[noshowbase](../standard-library/ios-functions.md#noshowbase)|Deaktiviert die Angabe der Schreibweisenbasis, mit der eine Zahl angezeigt wird.|
|[noshowpoint](../standard-library/ios-functions.md#noshowpoint)|Zeigt nur den ganzzahligen Teil von Gleitkommazahlen an, dessen Bruchteil null ist.|
|[noshowpos](../standard-library/ios-functions.md#noshowpos)|Bewirkt, dass positive Zahlen nicht explizit signiert werden.|
|[noskipws](../standard-library/ios-functions.md#noskipws)|Bewirkt, dass Leerzeichen vom Eingabestream gelesen werden.|
|[nounitbuf](../standard-library/ios-functions.md#nounitbuf)|Bewirkt, dass die Ausgabe gepuffert und verarbeitet wird, wenn der Puffer voll ist.|
|[nouppercase](../standard-library/ios-functions.md#nouppercase)|Gibt an, dass hexadezimale Ziffern und der Exponent in wissenschaftlicher Schreibweise in Kleinbuchstaben angezeigt werden.|
|[31.10](../standard-library/ios-functions.md#oct)|Gibt an, dass ganzzahlige Variablen in Basis-8-Schreibweise angezeigt werden.|
|[Richting](../standard-library/ios-functions.md#right)|Bewirkt, dass Text, der nicht so breit ist wie die Ausgabebreite, im Stream rechtsbündig angezeigt wird.|
|[wissenschaftlich](../standard-library/ios-functions.md#scientific)|Bewirkt, dass Gleitkommazahlen in wissenschaftlicher Schreibweise angezeigt werden.|
|[showbase](../standard-library/ios-functions.md#showbase)|Gibt die Schreibweisenbasis an, mit der eine Zahl angezeigt wird.|
|[showpoint](../standard-library/ios-functions.md#showpoint)|Zeigt den ganzzahligen Teil einer Gleitkommazahl und Ziffern rechts vom Dezimaltrennzeichen an, selbst wenn der Bruchteil null ist.|
|[Showpos](../standard-library/ios-functions.md#showpos)|Bewirkt, dass positive Zahlen explizit signiert werden.|
|[skipws](../standard-library/ios-functions.md#skipws)|Bewirkt, dass Leerzeichen nicht vom Eingabestream gelesen werden.|
|[Unitbuf](../standard-library/ios-functions.md#unitbuf)|Bewirkt, dass die Ausgabe verarbeitet wird, wenn der Puffer nicht leer ist.|
|[uppercase](../standard-library/ios-functions.md#uppercase)|Gibt an, dass hexadezimale Ziffern und der Exponent in wissenschaftlicher Schreibweise in Großbuchstaben angezeigt werden.|

### <a name="error-reporting"></a>Fehlerberichterstellung

|Name|Beschreibung|
|-|-|
|[io_errc](../standard-library/ios-functions.md#io_errc)||
|[is_error_code_enum](../standard-library/ios-functions.md#is_error_code_enum)||
|[iostream_category](../standard-library/ios-functions.md#iostream_category)||
|[make_error_code](../standard-library/ios-functions.md#make_error_code)||
|[make_error_condition](../standard-library/ios-functions.md#make_error_condition)||

### <a name="classes"></a>Klassen

|name|Beschreibung|
|-|-|
|[basic_ios](../standard-library/basic-ios-class.md)|Die Klassen Vorlage beschreibt die Speicher-und Element Funktionen, die sowohl für die Eingabedaten Ströme (von Klassen Vorlagen [basic_istream](../standard-library/basic-istream-class.md)) als auch für die Ausgabestreams (der Klassen Vorlage [basic_ostream](../standard-library/basic-ostream-class.md)), die von den Vorlagen Parametern abhängen, gemeinsam|
|[fpos](../standard-library/fpos-class.md)|Die Klassen Vorlage beschreibt ein Objekt, das alle Informationen speichern kann, die zum Wiederherstellen eines beliebigen Datei Positions Indikators innerhalb eines Streams benötigt werden.|
|[ios_base](../standard-library/ios-base-class.md)|Die Klasse beschreibt die Speicher- und Memberfunktionen, die Eingabe- und Ausgabestreams gemeinsam sind, die nicht von den Vorlagenparametern abhängen.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream-Programmierung](../standard-library/iostream-programming.md)\
[Iostreams-Konventionen](../standard-library/iostreams-conventions.md)
