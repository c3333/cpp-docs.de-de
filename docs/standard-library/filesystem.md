---
title: '&lt;:::no-loc(filesystem):::&gt;'
description: 'Beschreibt die Klassen, Funktionen und Typen im :::no-loc(filesystem)::: Header der C++-Standard Bibliothek.'
ms.date: 01/22/2020
f1_keywords:
- <:::no-loc(filesystem):::>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- ':::no-loc(filesystem):::'
- ':::no-loc(experimental):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(char16_t):::'
- ':::no-loc(char32_t):::'
ms.openlocfilehash: 1b3f541619bde85131915a4d1586a44675c2906a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219143"
---
# &lt;:::no-loc(filesystem):::&gt;

Schließen Sie den Header &lt; :::no-loc(filesystem):::> für den Zugriff auf Klassen und Funktionen ein, die Informationen über Pfade, Dateien und Verzeichnisse bearbeiten und abrufen.

## <a name="syntax"></a>Syntax

```cpp
#include <:::no-loc(filesystem):::> // C++17 standard header file name
#include <:::no-loc(experimental):::/:::no-loc(filesystem):::> // Header file for pre-standard implementation
using namespace std:::::no-loc(experimental)::::::::no-loc(filesystem):::::v1;
```

> [!IMPORTANT]
> Bei der Veröffentlichung von Visual Studio 2017 war der \<:::no-loc(filesystem):::> Header noch kein C++-Standard. C++ in Visual Studio 2017 RTW implementiert den endgültigen Entwurfs Standard, der in [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)enthalten ist. Visual Studio 2017 Version 15,7 und höher unterstützt den neuen c++ 17- \<:::no-loc(filesystem):::> Standard.
> Dies ist eine vollständig neue Implementierung, die mit der vorherigen Version nicht kompatibel ist `std:::::no-loc(experimental):::` . Dies wurde durch die Unterstützung von Symlinks, Fehlerbehebungen und Änderungen am standardmäßigen erforderliches Verhalten notwendig. Zurzeit werden von einschließlich \<:::no-loc(filesystem):::> der neuen `std:::::no-loc(filesystem):::` und der vorherigen bereitstellt `std:::::no-loc(experimental)::::::::no-loc(filesystem):::` . Durch Einschließen von wird \<:::no-loc(experimental):::/:::no-loc(filesystem):::> nur die alte Implementierung bereitstellt :::no-loc(experimental)::: . Die :::no-loc(experimental)::: Implementierung wird in der nächsten ABI-Break-Version der Bibliotheken entfernt.

Dieser Header unterstützt Dateisysteme für eine von zwei umfangreichen Klassen von Host Betriebssystemen: Microsoft Windows und POSIX.

Der überwiegende Teil der Funktionalität ist für beide Betriebssysteme gleich. In diesem Dokuments sind die Unterschiede aufgeführt. Beispiel:

- Windows unterstützt mehrere Stamm Namen, z `c:` `\\network_name` . b. oder. Ein Dateisystem besteht aus einer Gesamtstruktur von Strukturen, die jeweils über ein eigenes Stammverzeichnis verfügen, z. b. `c:\` oder `\\network_name\` , und jeweils über ein eigenes Aktuelles Verzeichnis verfügen, um einen relativen Pfadnamen zu vervollständigen (einer, der kein absoluter Pfadname ist).

- POSIX unterstützt eine einzelne Struktur ohne Stamm Namen, das einzige Stammverzeichnis `/` und ein einzelnes Aktuelles Verzeichnis.

Ein weiterer wichtiger Unterschied ist die systemeigene Darstellung von Pfadnamen:

- Windows verwendet eine NULL terminierte Sequenz von **`:::no-loc(wchar_t):::`** , die als UTF-16 codiert ist (ein oder mehrere-Elemente für jeden :::no-loc(char)::: Acter).

- POSIX verwendet eine NULL terminierte Sequenz von **`:::no-loc(char):::`** , die als UTF-8 codiert ist (ein oder mehrere-Elemente für jeden :::no-loc(char)::: Acter).

- Ein Objekt der Klasse `path` speichert den Pfadnamen im systemeigenen Format, unterstützt jedoch die einfache Konvertierung zwischen diesem gespeicherten Formular und mehreren externen Formularen:

  - Eine NULL terminierte Sequenz von **`:::no-loc(char):::`** , die vom Betriebssystem bevorzugt codiert ist.

  - Eine NULL terminierte Sequenz von **`:::no-loc(char):::`** , die als UTF-8 codiert ist.

  - Eine NULL terminierte Sequenz von **`:::no-loc(wchar_t):::`** , die vom Betriebssystem bevorzugt codiert ist.

  - Eine NULL terminierte Sequenz von **`:::no-loc(char16_t):::`** , die als UTF-16 codiert ist.

  - Eine NULL terminierte Sequenz von **`:::no-loc(char32_t):::`** , die als UTF-32-codiert ist.

  Gegenseitige Konvertierungen zwischen diesen Darstellungen werden nach Bedarf dadurch vermittelt, dass mindestens ein `codecvt`-Facet verwendet wird. Wenn kein bestimmtes Gebiets Schema Objekt angegeben wird, werden diese Facetten aus dem globalen Gebiets Schema abgerufen.

Ein weiterer Unterschied ist das Detail, über das das jeweilige Betriebssystem Ihnen die Möglichkeit gibt, Datei- oder Verzeichniszugriffsberechtigungen anzugeben:

- Windows zeichnet auf, ob eine Datei schreibgeschützt oder beschreibbar ist. Dies ist ein Attribut, das für Verzeichnisse keine Bedeutung hat.

- POSIX zeichnet auf, ob eine Datei gelesen, geschrieben oder ausgeführt werden kann (überprüft, wenn ein Verzeichnis ausgeführt wird). Und, ob jeder Vorgang für den Besitzer, die Gruppe des Besitzers oder für alle zulässig ist, sowie einige andere Berechtigungen.

Beiden Systemen gemeinsam ist die Struktur, die für einen Pfadnamen gilt, sobald Sie über den Stammnamen hinausgelangen. Für Pfadname `c:/abc/xyz/def.ext` :

- Der Stammname ist `c:` .

- Das Stammverzeichnis ist `/` .

- Der Stammpfad ist `c:/` .

- Der relative Pfad ist `abc/xyz/def.ext` .

- Der übergeordnete Pfad ist `c:/abc/xyz` .

- Der Dateiname ist `def.ext`.

- Der Stamm ist `def` .

- Die Erweiterung ist `.ext` .

Ein geringfügiger Unterschied ist das bevorzugte Trennzeichen zwischen der Sequenz von Verzeichnissen in einem Pfadnamen. Beide Betriebssysteme ermöglichen das Schreiben eines Schrägstrichs `/` , aber in manchen Kontexten bevorzugt Windows einen umgekehrten Schrägstrich `\` . Die-Implementierung speichert das bevorzugte Trennzeichen in dem Datenmember `preferred_separator` in `path` .

Schließlich `path` haben-Objekte ein wichtiges Feature: Sie können Sie überall dort verwenden, wo ein filename-Argument in den im Header definierten Klassen erforderlich ist [\<fstream>](fstream.md) .

Weitere Informationen und Codebeispiele finden Sie unter [Dateisystem Navigation (C++)](../standard-library/file-system-navigation.md).

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|||
|-|-|
|[directory_entry-Klasse](../standard-library/directory-entry-class.md)|Beschreibt ein Objekt, das von oder zurückgegeben wird `directory_iterator` `recursive_directory_iterator` und ein enthält `path` .|
|[directory_iterator-Klasse](../standard-library/directory-iterator-class.md)|Beschreibt einen Eingabeiterator, der alle Dateinamen in einem Dateisystemverzeichnis durchläuft.|
|[:::no-loc(filesystem):::_Error-Klasse](../standard-library/:::no-loc(filesystem):::-error-class.md)|Eine Basisklasse für Ausnahmen, die ausgelöst werden, um einen Systemüberlauf auf niedriger Ebene zu melden.|
|[path-Klasse](../standard-library/path-class.md)|Definiert eine Klasse, die ein für die Verwendung als Dateiname geeignetes Objekt des Vorlagentyps `String` speichert.|
|[recursive_directory_iterator-Klasse](../standard-library/recursive-directory-iterator-class.md)|Beschreibt einen Eingabeiterator, der alle Dateinamen in einem Dateisystemverzeichnis durchläuft. Der Iterator kann die Verzeichnisse auch absteigend anordnen.|
|[file_status-Klasse](../standard-library/file-status-class.md)|Bricht ein `file_type`um.|

### <a name="structs"></a>Strukturen

|||
|-|-|
|[space_info Struktur](../standard-library/space-info-structure.md)|Enthält Informationen zu einem Volume.|

## <a name="functions"></a>Functions

[\<:::no-loc(filesystem):::>Funktionen](../standard-library/:::no-loc(filesystem):::-functions.md)

## <a name="operators"></a>Operatoren

[\<:::no-loc(filesystem):::>Veranstalter](../standard-library/:::no-loc(filesystem):::-operators.md)

## <a name="enumerations"></a>Enumerationen

|||
|-|-|
|[copy_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#copy_options)|Eine mit [copy_file](../standard-library/:::no-loc(filesystem):::-functions.md#copy_file) verwendete Enumeration, mit der das Verhalten bestimmt wird, wenn eine Datei vorhanden ist.|
|[directory_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#directory_options)|Eine Enumeration, die Optionen für Verzeichnisiteratoren angibt.|
|[file_type](../standard-library/:::no-loc(filesystem):::-enumerations.md#file_type)|Eine Enumeration für Dateitypen.|
|[perm_options](../standard-library/:::no-loc(filesystem):::-enumerations.md#perm_options)| Listet Optionen für die- `permissions` Funktion auf. |
|[perms](../standard-library/:::no-loc(filesystem):::-enumerations.md#perms)|Ein Bitmaskentyp, mit dem Berechtigungen und Optionen zu Berechtigungen übermittelt werden.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)
