---
title: 'Exemplarische Vorgehensweise: Kompilieren eines C++/CX-Programms in der Befehlszeile'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 83369fc7b458463ea1f44a347bbcd0ca4eb32224
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078209"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>Exemplarische Vorgehensweise: Kompilieren eines C++/CX-Programms in der Befehlszeile

> [!NOTE]
> Für neue UWP-apps und-Komponenten empfiehlt sich die Verwendung [ C++von/WinRT](/windows/uwp/cpp-and-winrt-apis/), einer standardmäßigen c++ 17-sprach Projektion für Windows-Runtime-APIs. C++/WinRT ist im Windows 10 SDK ab Version 1803 verfügbar. C++/WinRT wird vollständig in Header Dateien implementiert und wurde entwickelt, um Ihnen erstklassigen Zugriff auf die moderne Windows-API zu ermöglichen.

Der Microsoft C++ -Compiler (MSVC) C++ unterstützt KomponentenC++Erweiterungen (/CX), die über zusätzliche Typen und Operatoren für das Windows-Runtime Programmiermodell verfügen. Sie können/CX C++zum Erstellen von Apps für universelle Windows-Plattform (UWP) und Windows-Desktop verwenden. Weitere Informationen finden Sie unter Einführung [in C++/CX](https://msdn.microsoft.com/magazine/dn166929.aspx) und [Komponenten Erweiterungen für laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

In dieser exemplarischen Vorgehensweise verwenden Sie einen Texteditor zur Erstellung eines grundlegenden C++/CX-Programms und kompilieren es dann auf der Befehlszeile. (Sie können Sie Ihr C++/CX-Programm verwenden, statt das gezeigte einzugeben oder Sie können ein C++/CX-Codebeispiel aus einem anderen Hilfeartikel verwenden. Dieses Verfahren ist nützlich zum entwickeln und Testen von kleinen Modulen, die keine Benutzeroberflächen Elemente aufweisen.)

> [!NOTE]
> Sie können auch die Visual Studio IDE für die Kompilierung von C++/CX-Programmen verwenden. Da die IDE Entwurfs-, Debugging-, Emulations-und Bereitstellungs Unterstützung umfasst, die nicht in der Befehlszeile verfügbar ist, empfiehlt es sich, die IDE zum Erstellen von universelle Windows-Plattform-Apps (UWP) zu verwenden. Weitere Informationen finden Sie unter [Erstellen einer UWP-APP C++in ](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp).

## <a name="prerequisites"></a>Voraussetzungen

Sie lernen die Grundlagen der C++ Sprache kennen.

## <a name="compiling-a-ccx-program"></a>Kompilieren eines C++/CX-Programms

Um die Kompilierung C++für/CX zu aktivieren, müssen Sie die [/ZW](reference/zw-windows-runtime-compilation.md) -Compileroption verwenden. Der MSVC-Compiler generiert eine. exe-Datei, die die Windows-Runtime als Ziel hat, sowie Links zu den erforderlichen Bibliotheken.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>So kompilieren Sie eine C++/CX-Anwendung in der Befehlszeile

1. Öffnen Sie ein **Developer-Eingabeaufforderung** Fenster. (Öffnen Sie im **Start** Fenster **apps**. Öffnen Sie den Ordner **Visual Studio-Tools** unter ihrer Version von Visual Studio, und wählen Sie dann die **Developer-Eingabeaufforderung** Verknüpfung aus.) Weitere Informationen zum Öffnen eines Developer-Eingabeaufforderung Fensters finden Sie unter [Verwenden des MSVC-Toolsets in der Befehlszeile](building-on-the-command-line.md).

   Administratoranmeldeinformationen sind möglicherweise erforderlich, um den Code abhängig vom Betriebssystem und der Konfiguration des Computers zu kompilieren. Öffnen Sie das Kontextmenü für **Developer-Eingabeaufforderung** , und wählen Sie dann **als Administrator ausführen**aus, um das Eingabe Aufforderungs Fenster als Administrator auszuführen.

1. Geben Sie an der Eingabeaufforderung **Editor basiccx. cpp**ein.

   Wählen Sie **Ja** aus, wenn Sie aufgefordert werden, eine Datei zu erstellen.

1. Geben Sie die folgenden Zeilen in Notepad ein:

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. Wählen Sie in der Menüleiste **Datei** > **Speichern**aus.

   Sie haben eine C++ Quelldatei erstellt, die den [Namespace](../cppcx/platform-namespace-c-cx.md) Namespace Windows-Runtime Platform verwendet.

1. Geben Sie an der Eingabeaufforderung **cl/EHsc/ZW basiccx. cpp/Link/Subsystem: Console**ein. Der cl.exe-Compiler kompiliert den Quellcode in eine .obj-Datei und führt dann den Linker aus, um ein ausführbares Programm namens basiccx.exe zu generieren. (Die [/EHsc](reference/eh-exception-handling-model.md) -Compileroption C++ gibt das Ausnahme Behandlungsmodell an, und das [/Link](reference/link-pass-options-to-linker.md) -Flag gibt eine Konsolenanwendung an.)

1. Geben Sie zum Ausführen des basiccx. exe-Programms an der Eingabeaufforderung " **basiccx**" ein.

   Das Programm zeigt folgenden Text an und wird anschließend beendet:

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>Weitere Informationen

[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)<br/>
[MSVC-Compileroptionen](reference/compiler-options.md)
