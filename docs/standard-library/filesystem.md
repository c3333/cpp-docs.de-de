---
title: '&lt;filesystem&gt;'
description: Beschreibt die Klassen, Funktionen und Typen im filesystem Header der C++-Standard Bibliothek.
ms.date: 01/22/2020
f1_keywords:
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: 0cf5e16eb21c02cfb96577c1dada873f087a71cf
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835830"
---
# &lt;filesystem&gt;

Schließen Sie den Header &lt; filesystem> für den Zugriff auf Klassen und Funktionen ein, die Informationen über Pfade, Dateien und Verzeichnisse bearbeiten und abrufen.

## <a name="syntax"></a>Syntax

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Bei der Veröffentlichung von Visual Studio 2017 war der \<filesystem> Header noch kein C++-Standard. C++ in Visual Studio 2017 RTW implementiert den endgültigen Entwurfs Standard, der in [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)enthalten ist. Visual Studio 2017 Version 15,7 und höher unterstützt den neuen c++ 17- \<filesystem> Standard.
> Dies ist eine vollständig neue Implementierung, die mit der vorherigen Version nicht kompatibel ist `std::experimental` . Dies wurde durch die Unterstützung von Symlinks, Fehlerbehebungen und Änderungen am standardmäßigen erforderliches Verhalten notwendig. Zurzeit werden von einschließlich \<filesystem> der neuen `std::filesystem` und der vorherigen bereitstellt `std::experimental::filesystem` . Durch Einschließen von wird \<experimental/filesystem> nur die alte Implementierung bereitstellt experimental . Die experimental Implementierung wird in der nächsten ABI-Break-Version der Bibliotheken entfernt.

Dieser Header unterstützt Dateisysteme für eine von zwei umfangreichen Klassen von Host Betriebssystemen: Microsoft Windows und POSIX.

Der überwiegende Teil der Funktionalität ist für beide Betriebssysteme gleich. In diesem Dokuments sind die Unterschiede aufgeführt. Beispiel:

- Windows unterstützt mehrere Stamm Namen, z `c:` `\\network_name` . b. oder. Ein Dateisystem besteht aus einer Gesamtstruktur von Strukturen, die jeweils über ein eigenes Stammverzeichnis verfügen, z. b. `c:\` oder `\\network_name\` , und jeweils über ein eigenes Aktuelles Verzeichnis verfügen, um einen relativen Pfadnamen zu vervollständigen (einer, der kein absoluter Pfadname ist).

- POSIX unterstützt eine einzelne Struktur ohne Stamm Namen, das einzige Stammverzeichnis `/` und ein einzelnes Aktuelles Verzeichnis.

Ein weiterer wichtiger Unterschied ist die systemeigene Darstellung von Pfadnamen:

- Windows verwendet eine NULL terminierte Sequenz von **`wchar_t`** , die als UTF-16 codiert ist (ein oder mehrere-Elemente für jeden char Acter).

- POSIX verwendet eine NULL terminierte Sequenz von **`char`** , die als UTF-8 codiert ist (ein oder mehrere-Elemente für jeden char Acter).

- Ein Objekt der Klasse `path` speichert den Pfadnamen im systemeigenen Format, unterstützt jedoch die einfache Konvertierung zwischen diesem gespeicherten Formular und mehreren externen Formularen:

  - Eine NULL terminierte Sequenz von **`char`** , die vom Betriebssystem bevorzugt codiert ist.

  - Eine NULL terminierte Sequenz von **`char`** , die als UTF-8 codiert ist.

  - Eine NULL terminierte Sequenz von **`wchar_t`** , die vom Betriebssystem bevorzugt codiert ist.

  - Eine NULL terminierte Sequenz von **`char16_t`** , die als UTF-16 codiert ist.

  - Eine NULL terminierte Sequenz von **`char32_t`** , die als UTF-32-codiert ist.

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

|name|Beschreibung|
|-|-|
|[directory_entry-Klasse](../standard-library/directory-entry-class.md)|Beschreibt ein Objekt, das von oder zurückgegeben wird `directory_iterator` `recursive_directory_iterator` und ein enthält `path` .|
|[directory_iterator-Klasse](../standard-library/directory-iterator-class.md)|Beschreibt einen Eingabeiterator, der alle Dateinamen in einem Dateisystemverzeichnis durchläuft.|
|[filesystem_Error-Klasse](../standard-library/filesystem-error-class.md)|Eine Basisklasse für Ausnahmen, die ausgelöst werden, um einen Systemüberlauf auf niedriger Ebene zu melden.|
|[path-Klasse](../standard-library/path-class.md)|Definiert eine Klasse, die ein für die Verwendung als Dateiname geeignetes Objekt des Vorlagentyps `String` speichert.|
|[recursive_directory_iterator-Klasse](../standard-library/recursive-directory-iterator-class.md)|Beschreibt einen Eingabeiterator, der alle Dateinamen in einem Dateisystemverzeichnis durchläuft. Der Iterator kann die Verzeichnisse auch absteigend anordnen.|
|[file_status-Klasse](../standard-library/file-status-class.md)|Bricht ein `file_type`um.|

### <a name="structs"></a>Strukturen

|Name|Beschreibung|
|-|-|
|[space_info Struktur](../standard-library/space-info-structure.md)|Enthält Informationen zu einem Volume.|

## <a name="functions"></a>Functions

[\<filesystem> Funktionen](../standard-library/filesystem-functions.md)

## <a name="operators"></a>Operatoren

[\<filesystem> Veranstalter](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>Enumerationen

|Name|Beschreibung|
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|Eine mit [copy_file](../standard-library/filesystem-functions.md#copy_file) verwendete Enumeration, mit der das Verhalten bestimmt wird, wenn eine Datei vorhanden ist.|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|Eine Enumeration, die Optionen für Verzeichnisiteratoren angibt.|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|Eine Enumeration für Dateitypen.|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| Listet Optionen für die- `permissions` Funktion auf. |
|[perms](../standard-library/filesystem-enumerations.md#perms)|Ein Bitmaskentyp, mit dem Berechtigungen und Optionen zu Berechtigungen übermittelt werden.|

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)
