---
title: Exportieren aus einer DLL mithilfe von DEF-Dateien
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078520"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Exportieren aus einer DLL mithilfe von DEF-Dateien

Eine Modul Definition oder DEF-Datei (*. def) ist eine Textdatei, die eine oder mehrere Modul Anweisungen enthält, die verschiedene Attribute einer DLL beschreiben. Wenn Sie das **__declspec (dllexport)** -Schlüsselwort nicht zum Exportieren der DLL-Funktionen verwenden, benötigt die DLL eine DEF-Datei.

Eine minimale DEF-Datei muss die folgenden Modul Definitions Anweisungen enthalten:

- Die erste Anweisung in der Datei muss die {1}LIBRARY{2}-Anweisung sein. Diese Anweisung identifiziert die DEF-Datei als zu einer DLL gehörend. Auf die {1}LIBRARY{2}-Anweisung folgt der Name der DLL. Der Linker speichert diesen Namen in der Importbibliothek der DLL.

- Durch die {1}EXPORTS{2}-Anweisung werden die Namen und optional die Ordinalwerte der von der DLL exportierten Funktionen aufgelistet. Sie weisen der Funktion einen Ordinalwert zu, indem Sie dem Funktionsnamen ein @-Zeichen und eine Zahl nachstellen. Die Ordinalzahlen müssen sich in einem Bereich von 1 bis N befinden, wobei N die Gesamtzahl der von der DLL exportierten Funktionen angibt. Wenn Sie Funktionen nach Ordinalzahl exportieren möchten, finden Sie weitere [Informationen unter Exportieren von Funktionen aus einer DLL nach Ordinal anstelle des Namens](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) und dieses Themas.

Die DEF-Datei für eine DLL, die den Code für die Implementierung einer binären Suchstruktur enthält, könnte z. B. folgendermaßen aussehen:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Wenn Sie den [MFC-DLL-Assistenten](../mfc/reference/mfc-dll-wizard.md) zum Erstellen einer MFC-DLL verwenden, erstellt der Assistent eine Skeleton DEF-Datei für Sie und fügt Sie automatisch dem Projekt hinzu. Fügen Sie die Namen der zu exportierenden Funktionen in diese Datei ein. Erstellen Sie die DEF-Datei für nicht-MFC-DLLs selbst, und fügen Sie Sie Ihrem Projekt hinzu. Wechseln Sie dann zu **Projekt** > **Eigenschaften** > **Linker** > **Eingabe** > **Modul Definitionsdatei** , und geben Sie den Namen der DEF-Datei ein. Wiederholen Sie diesen Schritt für jede Konfiguration und Plattform, oder führen Sie alles gleichzeitig aus, indem Sie **Konfiguration = alle Konfigurationen**und **Plattform = alle Plattformen**auswählen.

Wenn Sie Funktionen in eine C++ Datei exportieren, müssen Sie entweder die ergänzten Namen in der DEF-Datei platzieren oder die exportierten Funktionen mit der Standard-c-Verknüpfung mithilfe von extern "c" definieren. Wenn Sie die ergänzten Namen in der DEF-Datei platzieren müssen, können Sie Sie mit dem [DUMPBIN](../build/reference/dumpbin-reference.md) -Tool oder mit der Option Linker [/map](../build/reference/map-generate-mapfile.md) abrufen. Beachten Sie, dass die vom Compiler erzeugten, ergänzten Namen compilerspezifisch sind. Wenn Sie die ergänzten Namen, die vom Microsoft C++ -Compiler (MSVC) erstellt werden, in eine DEF-Datei einfügen, müssen Anwendungen, die mit Ihrer DLL verknüpft werden, auch mit derselben Version von MSVC erstellt werden, sodass die ergänzten Namen in der aufrufenden Anwendung mit den exportierten Namen in der DEF-Datei der dll übereinstimmen.

> [!NOTE]
> Eine mit Visual Studio 2015 entwickelte dll kann von Anwendungen verwendet werden, die mit Visual Studio 2017 oder Visual Studio 2019 erstellt wurden.

Wenn Sie eine Erweiterungs- [dll](../build/extension-dlls-overview.md)entwickeln und mithilfe einer DEF-Datei exportieren, platzieren Sie den folgenden Code am Anfang und Ende der Header Dateien, die die exportierten Klassen enthalten:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Diese Zeilen stellen sicher, dass MFC-Variablen, die intern verwendet oder den Klassen hinzugefügt werden, von der MFC-Erweiterungs-DLL exportiert (oder importiert) werden. Wenn Sie z. B. eine Klasse mithilfe von `DECLARE_DYNAMIC` ableiten, wird das Makro erweitert und Ihrer Klasse wird eine Membervariable `CRuntimeClass` hinzugefügt. Ohne diese vier Zeilen wird die DLL u. U. nicht einwandfrei kompiliert bzw. verknüpft, oder es tritt ein Fehler auf, wenn die Clientanwendung mit der DLL verknüpft wird.

Beim Erstellen der dll verwendet der Linker die DEF-Datei, um eine Exportdatei (. exp) und eine Import Bibliothek (LIB-Datei) zu erstellen. Anschließend verwendet der Linker die Exportdatei zum Erstellen der DLL-Datei. Ausführbare, implizit mit der DLL verknüpfte Dateien werden bei ihrer Erstellung mit der Importbibliothek verknüpft.

Beachten Sie, dass MFC selbst DEF-Dateien verwendet, um Funktionen und Klassen aus "MFCx0. dll" zu exportieren.

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Exportieren aus einer DLL mithilfe von __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Exportieren und Importieren mithilfe AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Exportieren C++ von Funktionen zur Verwendung in ausführbaren C-Dateien](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Exportieren von c-Funktionen zur Verwendung in C++ausführbaren c-oder-Programmier Dateien](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Bestimmen der zu verwendenden Export Methode](determining-which-exporting-method-to-use.md)

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Initialisieren einer dll](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [DEF-Dateien](reference/module-definition-dot-def-files.md)

- [Regeln für Modul Definitions Anweisungen](reference/rules-for-module-definition-statements.md)

- [Ergänzte Namen](reference/decorated-names.md)

- [Importieren und Exportieren von Inlinefunktionen](importing-and-exporting-inline-functions.md)

- [Gegenseitige Importe](mutual-imports.md)

## <a name="see-also"></a>Weitere Informationen

[Exportieren aus einer DLL](exporting-from-a-dll.md)
