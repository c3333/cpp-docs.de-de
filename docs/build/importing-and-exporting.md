---
title: Importieren und Exportieren
ms.date: 05/06/2019
helpviewer_keywords:
- DLLs [C++], importing
- exporting DLLs [C++]
- importing DLLs [C++]
- DLLs [C++], exporting from
- __declspec(dllimport) keyword [C++]
ms.assetid: 7c44c2aa-2117-4cec-9615-a65bfd3f8f7b
ms.openlocfilehash: 03931f7f128ab0666890bb8e76677db67dda8fc7
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220643"
---
# <a name="importing-and-exporting"></a>Importieren und Exportieren

Sie können öffentliche Symbole in eine Anwendung importieren oder Funktionen aus einer DLL mithilfe von zwei Methoden exportieren:

- Verwenden einer Moduldefinitionsdatei (DEF) beim Erstellen der DLL

- Verwenden der Schlüsselwörter **__declspec(dllimport)** oder **__declspec(dllexport)** in einer Funktionsdefinition in der Hauptanwendung

## <a name="using-a-def-file"></a>Verwenden einer DEF-Datei

Eine Moduldefinitionsdatei (.def) ist eine Textdatei mit einer oder mehreren Modulanweisungen, die verschiedene Attribute einer DLL beschreiben. Wenn Sie **__declspec(dllimport)** oder **__declspec(dllexport)** nicht verwenden, um die Funktionen einer DLL zu exportieren, ist für die DLL eine DEF-Datei erforderlich.

Sie können DEF-Dateien verwenden, um [in eine Anwendung zu importieren](importing-using-def-files.md) oder [aus einer DLL zu exportieren](exporting-from-a-dll-using-def-files.md).

## <a name="using-__declspec"></a>Verwenden von __declspec

Sie müssen **__declspec(dllimport)** nicht verwenden, damit Ihr Code korrekt kompiliert wird. Tun Sie dies jedoch, kann der Compiler besseren Code generieren. Der Compiler kann besseren Code generieren, da er bestimmen kann, ob eine Funktion in einer DLL vorhanden ist oder nicht. Auf dieser Grundlage kann der Compiler Code erzeugen, der eine Ebene der Dereferenzierung überspringt, die normalerweise in einem Funktionsaufruf vorhanden wäre, der eine DLL-Grenze überschritten hat. Sie müssen jedoch **__declspec(dllimport)** verwenden, um Variablen zu importieren, die in einer DLL verwendet werden.

Wenn ein geeigneter Exportbereich in der DEF-Datei verwendet wird, ist **__declspec(dllexport)** nicht erforderlich. **__declspec(dllexport)** wurde hinzugefügt, um eine einfache Möglichkeit bieten zu können, Funktionen aus einer EXE- oder DLL-Datei exportieren zu können, ohne dass eine DEF-Datei verwendet werden muss.

Das Win32-Format für portierbare ausführbare Dateien wurde so entworfen, dass die Anzahl von Seiten minimiert wird, die erforderlich sind, um Fehler bei Importen zu beheben. Dazu werden alle Importadressen für sämtliche Programme an einer Stelle namens Importadressentabelle platziert. Dadurch ist es möglich, dass das Ladeprogramm nur ein oder zwei Seiten bearbeitet, wenn auf diese Importe zugegriffen wird.

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Importieren in eine Anwendung mithilfe von __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Exportieren aus einer DLL](exporting-from-a-dll.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
