---
title: Dateisystemnavigation
description: Verwenden der C++-Standard Bibliothek-Dateisystem-APIs, um im Dateisystem zu navigieren.
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 26abe2fad6cacf8959507f15e967278e85254024
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87203285"
---
# <a name="file-system-navigation"></a>Dateisystemnavigation

Der \<filesystem> Header implementiert die technische Spezifikation des C++-Dateisystems ISO/IEC TS 18822:2015 (Abschließender Entwurf: [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)) und verfügt über Typen und Funktionen, mit denen Sie plattformunabhängigen Code für die Navigation im Datei System schreiben können. Da er plattformübergreifend ist, enthält er APIs, die für Windows-Systeme nicht relevant sind. Beispielsweise `is_fifo(const path&)` gibt immer **`false`** unter Windows zurück.

## <a name="overview"></a>Übersicht

Verwenden Sie die \<filesystem> APIs für die folgenden Aufgaben:

- Durchlaufen von Dateien und Verzeichnissen unter einem angegebenen Pfad

- Abrufen von Informationen zu Dateien, einschließlich Erstellungszeitpunkt, Größe, Erweiterung und Stammverzeichnis

- Erstellen, Zerlegen und Vergleichen von Pfaden

- Erstellen, kopieren und Löschen von Verzeichnissen

- Kopieren und Löschen von Dateien

Weitere Informationen zu Datei-E/A mit der Standardbibliothek finden Sie unter [iostream-Programmierung](../standard-library/iostream-programming.md).

## <a name="paths"></a>Pfade

### <a name="constructing-and-composing-paths"></a>Erstellen und Zerlegen von Pfaden

In Windows (ab XP) werden Pfade systemintern in Unicode gespeichert. Die [path](../standard-library/path-class.md) -Klasse führt automatisch alle erforderlichen Zeichen folgen Konvertierungen durch. Sie akzeptiert Argumente sowohl für breit-als auch für schmale Zeichen Arrays und sowohl `std::string` `std::wstring` als auch als UTF8 oder UTF16 formatierte Typen. Mit der `path` -Klasse werden Pfadtrennzeichen automatisch normalisiert. Sie können einen einzelnen Schrägstrich als Verzeichnistrennzeichen in Konstruktorargumenten verwenden. Mit diesem Trennzeichen können Sie die gleichen Zeichen folgen zum Speichern von Pfaden in Windows-und UNIX-Umgebungen verwenden:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Zum Verketten zweier Pfade können Sie überladene `/` - und `/=` -Operatoren verwenden, die analog zu den `+` - und `+=` -Operatoren in `std::string` und `std::wstring`sind. `path`Wenn Sie dies nicht tun, stellt das-Objekt die Trennzeichen bereit.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Überprüfen von Pfaden

Die Path-Klasse verfügt über mehrere Methoden, die Informationen über verschiedene Teile des Pfads selbst zurückgeben. Diese Informationen unterscheiden sich von den Informationen über die Dateisystem Entität, auf die Sie möglicherweise verweist. Sie können den Stamm, relativen Pfad, Dateinamen, die Dateierweiterung usw. abrufen. Sie können Pfadobjekte durchlaufen, um alle Ordner in der Hierarchie zu überprüfen. Im folgenden Beispiel wird gezeigt, wie ein Pfad Objekt durchlaufen wird. Und zum Abrufen von Informationen über die Teile.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Durch den Code wird die folgende Ausgabe generiert:

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>Vergleichen von Pfaden

Die `path` -Klasse überlädt die gleichen Vergleichsoperatoren wie `std::string` und `std::wstring`. Wenn Sie zwei Pfade vergleichen, erstellen Sie einen Zeichen folgen Vergleich, nachdem die Trennzeichen normalisiert wurden. Wenn ein nach stehender Schrägstrich (oder umgekehrter Schrägstrich) fehlt, wird er nicht hinzugefügt und wirkt sich auf den Vergleich aus. Im folgenden Beispiel wird der Vergleich von Pfadwerten veranschaulicht:

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

Um diesen Code auszuführen, fügen Sie ihn in das vollständige Beispiel oben vor `main` ein, und heben Sie in main die Auskommentierung der Zeile auf, die ihn aufruft.

### <a name="converting-between-path-and-string-types"></a>Konvertieren zwischen Pfad- und Zeichenfolgentypen

Ein `path` -Objekt ist implizit in `std::wstring` oder `std::string`konvertibel. Dies bedeutet, dass Sie einen Pfad an Funktionen wie [wofstream:: Open](../standard-library/basic-ofstream-class.md#open)übergeben können, wie im folgenden Beispiel gezeigt:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>Durchlaufen von Verzeichnissen und Dateien

Der \<filesystem> -Header stellt den [directory_iterator](../standard-library/directory-iterator-class.md) Typ bereit, um einzelne Verzeichnisse zu durchlaufen, und die [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) -Klasse, um rekursiv über ein Verzeichnis und seine Unterverzeichnisse zu iterieren. Wenn Sie einen Iterator erstellt haben, indem Sie ihm ein `path` -Objekt übergeben haben, verweist der Iterator auf den ersten „directory_entry“ im Pfad. Erstellen Sie den End-Iterator, indem Sie den Standardkonstruktor aufrufen.

Beim Durchlaufen eines Verzeichnisses können verschiedene Arten von Elementen entdeckt werden. Zu diesen Elementen gehören Verzeichnisse, Dateien, symbolische Verknüpfungen, Socketdateien und andere. `directory_iterator` gibt die Elemente als [directory_entry](../standard-library/directory-entry-class.md)-Objekte zurück.
