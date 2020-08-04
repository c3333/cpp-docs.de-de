---
title: Exportieren aus einer DLL mithilfe von DEF-Dateien
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 8fdbb060502f339eb748306eef582d2f296b1f60
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229830"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Exportieren aus einer DLL mithilfe von DEF-Dateien

Eine Moduldefinitionsdatei oder DEF-Datei (*.def) ist eine Textdatei mit einer oder mehreren Modulanweisungen, die verschiedene Attribute einer DLL beschreiben. Wenn Sie für das Exportieren von DLL-Funktionen nicht das **`__declspec(dllexport)`** -Schlüsselwort verwenden, ist eine DEF-Datei für die DLL erforderlich.

Eine DEF-Datei muss mindestens die folgenden Moduldefinitionsanweisungen enthalten:

- Die erste Anweisung in der Datei muss die LIBRARY-Anweisung sein. Sie kennzeichnet die Zugehörigkeit der DEF-Datei zu einer DLL. Auf die LIBRARY-Anweisung folgt der Name der DLL. Der Linker speichert diesen Namen in der Importbibliothek der DLL.

- Durch die EXPORTS-Anweisung werden die Namen und optional die Ordinalwerte der von der DLL exportierten Funktionen aufgelistet. Sie weisen der Funktion einen Ordinalwert zu, indem Sie dem Funktionsnamen ein @-Zeichen und eine Zahl nachstellen. Die Ordinalzahlen müssen sich in einem Bereich von 1 bis N befinden, wobei N die Gesamtzahl der von der DLL exportierten Funktionen angibt. Informationen zum Exportieren von Funktionen anhand der Ordnungszahl finden Sie unter diesem Thema sowie unter [Exportieren von Funktionen aus einer DLL über die Ordnungszahl statt über den Namen](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md).

Die DEF-Datei für eine DLL, die den Code für die Implementierung einer binären Suchstruktur enthält, könnte z. B. folgendermaßen aussehen:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Wenn Sie zum Erstellen einer MFC-DLL den [MFC-DLL-Assistenten](../mfc/reference/mfc-dll-wizard.md) verwenden, erstellt der Assistent eine DEF-Gerüstdatei und fügt sie automatisch dem Projekt hinzu. Fügen Sie die Namen der zu exportierenden Funktionen in diese Datei ein. Für MFC-fremde DLLs müssen Sie die DEF-Datei selbst erstellen und dem Projekt hinzufügen. Navigieren Sie dann zu **Projekt** > **Eigenschaften** > **Linker** > **Eingabe** > **Moduldefinitionsdatei**, und geben Sie den Namen der DEF-Datei ein. Wiederholen Sie diesen Schritt für jede Konfiguration und Plattform, oder führen Sie alles gleichzeitig aus, indem Sie **Konfiguration = Alle Konfigurationen** und **Plattform = Alle Plattformen** auswählen.

Wenn Sie Funktionen in eine C++-Datei exportieren, müssen Sie entweder die dekorierten Namen in die DEF-Datei einfügen oder die exportierten Funktionen unter Verwendung von extern „C“ mit der standardmäßigen C-Bindung definieren. Wenn Sie die dekorierten Namen in der DEF-Datei angeben müssen, können Sie diese mithilfe des Tools [DUMPBIN](../build/reference/dumpbin-reference.md) oder mit der [/MAP](../build/reference/map-generate-mapfile.md)-Linkeroption abrufen. Beachten Sie, dass die vom Compiler erzeugten, ergänzten Namen compilerspezifisch sind. Wenn Sie die vom Microsoft C++-Compiler (MSVC) erzeugten, dekorierten Namen in eine DEF-Datei einfügen, ist es erforderlich, dass Anwendungen, die mit der DLL verknüpft werden, mit derselben Version von MSVC erstellt wurden. Auf diese Weise wird gewährleistet, dass die ergänzten Namen in der aufrufenden Anwendung mit den exportierten Namen in der DEF-Datei der DLL übereinstimmen.

> [!NOTE]
> Eine mit Visual Studio 2015 erstellte DLL kann von Anwendungen verwendet werden, die mit Visual Studio 2017 oder Visual Studio 2019 erstellt wurden.

Wenn Sie eine [Erweiterungs-DLL](../build/extension-dlls-overview.md) erstellen und den Export über eine DEF-Datei vornehmen, fügen Sie den folgenden Code am Anfang und am Ende der Headerdateien ein, in denen die exportierten Klassen enthalten sind:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Diese Zeilen stellen sicher, dass MFC-Variablen, die intern verwendet bzw. Klassen hinzugefügt werden, von der Erweiterungs-MFC-DLL exportiert (bzw. importiert) werden. Wenn Sie z. B. eine Klasse mithilfe von `DECLARE_DYNAMIC` ableiten, wird das Makro erweitert und Ihrer Klasse wird eine Membervariable `CRuntimeClass` hinzugefügt. Ohne diese vier Zeilen wird die DLL u. U. nicht einwandfrei kompiliert bzw. verknüpft, oder es tritt ein Fehler auf, wenn die Clientanwendung mit der DLL verknüpft wird.

Der Linker verwendet beim Erstellen der DLL die DEF-Datei, um eine Exportdatei (.exp) und eine Importbibliothek (.lib) zu erstellen. Anschließend verwendet der Linker die Exportdatei zum Erstellen der DLL-Datei. Ausführbare, implizit mit der DLL verknüpfte Dateien werden bei ihrer Erstellung mit der Importbibliothek verknüpft.

Beachten Sie, dass MFC selbst die DEF-Dateien verwendet, um Funktionen und Klassen aus MFCx0.dll zu exportieren.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Exportieren aus einer DLL mithilfe von „__declspec(dllexport)“](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe von „AFX_EXT_CLASS“](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren von C++-Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von C-Funktionen zur Verwendung in ausführbaren C- oder C++-Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Festlegen der Exportmethode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [DEF-Dateien](reference/module-definition-dot-def-files.md)

- [Regeln für Moduldefinitionsanweisungen](reference/rules-for-module-definition-statements.md)

- [Dekorierte Namen](reference/decorated-names.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Siehe auch

[Exportieren aus einer DLL](exporting-from-a-dll.md)
