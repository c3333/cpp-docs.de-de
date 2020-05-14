---
title: 'Exemplarische Vorgehensweise: Kompilieren eines C++-/CLI-Programms in der Befehlszeile'
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 8a5c5659367350a80725b365ef9c431bbec209d1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877456"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines C++-/CLI-Programms in der Befehlszeile

Sie können Visual C++-Programme erstellen, die auf die Common Language Runtime (CLR) abzielen und .NET Framework verwenden, und diese in der Befehlszeile erstellen. Visual C++ unterstützt die the C++/CLI-Programmiersprache, die über zusätzliche Typen und Operatoren für das .NET-Programmiermodell verfügt. Allgemeine Informationen zu C++/CLI finden Sie unter [.NET-Programmierung mit C++/CLI (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md).

In dieser exemplarischen Vorgehensweise verwenden Sie einen Texteditor zur Erstellung eines grundlegenden C++/CLI-Programms und kompilieren es dann auf der Befehlszeile. (Sie können Sie Ihr C++/CLI-Programm verwenden, statt das gezeigte einzugeben, oder Sie können ein C++/CLI-Codebeispiel aus einem anderen Hilfeartikel verwenden. Diese Technik ist nützlich zum Erstellen und Testen von kleinen Modulen, die keine Benutzeroberflächenelemente enthalten.)

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen grundlegende Kenntnisse der Programmiersprache C++.

## <a name="compiling-a-ccli-program"></a>Kompilieren eines C++/CLI-Programms

Die folgenden Schritte zeigen, wie Sie eine C++/CLI-Konsolenanwendung kompilieren, die .NET Framework-Klassen verwendet.

Zur Aktivierung der Kompilierung für C++/CLI müssen Sie die Compileroption [/clr](reference/clr-common-language-runtime-compilation.md) verwenden. Der MSVC-Compiler generiert eine EXE-Datei, die MSIL-Code oder gemischten MSIL- und nativen Code sowie Links zu den erforderlichen .NET-Framework-Bibliotheken enthält.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>So kompilieren Sie eine C++/CLI-Anwendung in der Befehlszeile

1. Öffnen Sie ein **Developer-Eingabeaufforderungsfenster**. Eine spezielle Anleitung finden Sie unter [Öffnen eines Developer-Eingabeaufforderungsfensters](building-on-the-command-line.md#developer_command_prompt).

   Administratoranmeldeinformationen sind möglicherweise erforderlich, um den Code abhängig vom Betriebssystem und der Konfiguration des Computers zu kompilieren. Zum Ausführen des Eingabeaufforderungsfensters als Administrator klicken Sie mit der rechten Maustaste, um das Kontextmenü für die Eingabeaufforderung zu öffnen, und klicken Sie dann auf **Mehr** > **Als Administrator ausführen**.

1. Geben Sie an der Eingabeaufforderung `notepad basicclr.cpp` ein.

   Wenn Sie aufgefordert werden, eine Datei zu erstellen, wählen Sie **Ja** aus.

1. Geben Sie die folgenden Zeilen in Notepad ein:

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. Klicken Sie in der Menüleiste auf **Datei** > **Speichern**.

   Sie haben nun eine Visual C++-Quelldatei erstellt, die eine .NET-Framework-Klasse (<xref:System.Console>) im Namespace <xref:System> enthält.

1. Geben Sie an der Eingabeaufforderung `cl /clr basicclr.cpp` ein. Der cl.exe-Compiler kompiliert den Quellcode in eine .obj-Datei, die MSIL enthält, und führt dann den Linker aus, um ein ausführbares Programm namens basicclr.exe zu generieren.

1. Geben Sie zum Ausführen des basicclr.exe-Programms an der Eingabeaufforderung `basicclr` ein.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>Siehe auch

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
