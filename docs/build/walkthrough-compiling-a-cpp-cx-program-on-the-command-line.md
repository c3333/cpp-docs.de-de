---
title: 'Exemplarische Vorgehensweise: Kompilieren eines C++- bzw. CX-Programms in der Befehlszeile'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 456373fc9009920b734243f6a6c1af3d2c0301d4
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373683"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines C++- bzw. CX-Programms in der Befehlszeile

> [!NOTE]
> Für neue UWP-Apps und -Komponenten empfiehlt es sich, [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) zu verwenden, eine C++17-Standardsprachprojektion für Windows-Runtime-APIs. C++/WinRT ist im Windows 10 SDK ab Version 1803 erhältlich. C++/WinRT wird vollständig in Headerdateien implementiert und wurde entwickelt, um Ihnen erstklassigen Zugriff auf die moderne Windows-API zu ermöglichen.

Der Microsoft Visual C++-Compiler (MSVC) unterstützt C++-Komponentenerweiterungen (C++/CX), die zusätzliche Typen und Operatoren für das Windows-Runtime-Programmiermodell bereitstellen. Sie können C++/CX verwenden, um UWP-Apps und Windows Desktop-Apps zu erstellen. Weitere Informationen finden Sie unter [Einführung in C++/CX](https://docs.microsoft.com/archive/msdn-magazine/2013/april/component-extensions-a-tour-of-c-cx) und [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

In dieser exemplarischen Vorgehensweise verwenden Sie einen Texteditor zur Erstellung eines grundlegenden C++/CX-Programms und kompilieren es dann auf der Befehlszeile. (Sie können Sie Ihr C++/CX-Programm verwenden, statt das gezeigte einzugeben oder Sie können ein C++/CX-Codebeispiel aus einem anderen Hilfeartikel verwenden. Diese Technik ist nützlich zum Erstellen und Testen von kleinen Modulen, die keine Benutzeroberflächenelemente enthalten.)

> [!NOTE]
> Sie können auch die Visual Studio IDE für die Kompilierung von C++/CX-Programmen verwenden. Da die IDE Design, Debuggen, Emulation und Unterstützung für die Bereitstellung, die auf der Befehlszeile nicht verfügbar ist, enthält, empfehlen wir die Verwendung der IDE zum Erstellen von UWP-Apps. Weitere Informationen finden Sie unter [Erstellen einer UWP-App in C++](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Voraussetzungen

Sie benötigen grundlegende Kenntnisse der Programmiersprache C++.

## <a name="compiling-a-ccx-program"></a>Kompilieren eines C++/CX-Programms

Zur Aktivierung der Kompilierung für C++/CX müssen Sie die Compileroption [/ZW](reference/zw-windows-runtime-compilation.md) verwenden. Der MSVC-Compiler generiert eine .exe-Datei, die auf die Windows Runtime abzielt und mit den erforderlichen Bibliotheken verknüpft wird.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>So kompilieren Sie eine C++/CX-Anwendung in der Befehlszeile

1. Öffnen Sie ein **Developer-Eingabeaufforderungsfenster**. (Öffnen Sie im **Start-Fenster** **Apps**. Öffnen Sie den Ordner **Visual Studio-Tools** unter Ihrer Version von Visual Studio, und wählen Sie dann die Verknüpfung **Developer-Eingabeaufforderung** aus.) Weitere Informationen zum Öffnen eines Developer-Eingabeaufforderungsfensters finden Sie unter [Verwenden des MSVC-Toolsets auf der Befehlszeile](building-on-the-command-line.md).

   Administratoranmeldeinformationen sind möglicherweise erforderlich, um den Code abhängig vom Betriebssystem und der Konfiguration des Computers zu kompilieren. Zum Ausführen des Eingabeaufforderungsfensters als Administrator öffnen Sie das Kontextmenü für die **Developer-Eingabeaufforderung**, und wählen Sie dann **Als Administrator ausführen** aus.

1. Geben Sie an der Eingabeaufforderung **notepad basiccx.cpp** ein.

   Sie werden aufgefordert, eine Datei zu erstellen. Wählen Sie **Ja** aus.

1. Geben Sie die folgenden Zeilen in Notepad ein:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Klicken Sie in der Menüleiste auf **Datei** > **Speichern**.

   Sie haben eine C++-Quelldatei erstellt, die den Namespace [Plattformnamespace](../cppcx/platform-namespace-c-cx.md) der Windows-Runtime verwendet.

1. Geben Sie an der Eingabeaufforderung **cl /EHsc /ZW basiccx.cpp /link /SUBSYSTEM:CONSOLE** ein. Der cl.exe-Compiler kompiliert den Quellcode in eine .obj-Datei und führt dann den Linker aus, um ein ausführbares Programm namens basiccx.exe zu generieren. (Die Compileroption [/EHsc](reference/eh-exception-handling-model.md) gibt das C++-Ausnahmebehandlungsmodell, und das Flag [/link](reference/link-pass-options-to-linker.md) gibt eine Konsolenanwendung an.)

1. Geben Sie zum Ausführen des basiccx.exe-Programms an der Eingabeaufforderung **basiccx** ein.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Siehe auch

[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
