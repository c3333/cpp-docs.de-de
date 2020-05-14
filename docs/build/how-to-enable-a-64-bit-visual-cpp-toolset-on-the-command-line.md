---
title: 'Vorgehensweise: Aktivieren eines 64-Bit-MSVC-Toolsets über die Befehlszeile'
ms.date: 07/24/2019
helpviewer_keywords:
- x64 [C++]
- 64-bit compiler [C++], command line usage
- 64-bit compiler [C++], toolset enabling at command line
- command line [C++], 64-bit compiler
- Itanium [C++], command-line compiler
- IPF
- Itanium [C++]
- IPF, command-line compiler
- x64 [C++], command-line compiler
ms.assetid: 4da93a19-e20d-4778-902a-5eee9a6a90b5
ms.openlocfilehash: 60399994cd5fc2f39efeadc6ffcf917138aada37
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078531"
---
# <a name="how-to-enable-a-64-bit-x64-hosted-msvc-toolset-on-the-command-line"></a>Vorgehensweise: Aktivieren eines auf x64 gehosteten 64-Bit-MSVC-Toolsets über die Befehlszeile

Visual Studio enthält C++ Compiler, Linker und andere Tools, die Sie verwenden können, um plattformspezifische Versionen Ihrer Apps zu erstellen, die unter 32-Bit-, 64-Bit- oder ARM-basierten Windows-Betriebssystemen ausgeführt werden können. Mithilfe anderer optionaler Visual Studio-Workloads können Sie C++-Tools für andere Zielplattformen verwenden, wie etwa iOS, Android und Linux. Die Standardbuildarchitektur verwendet auf x86 gehostete 32-Bit-Tools, um x86-nativen 32-Bit-Windows-Code zu erstellen. Allerdings besitzen Sie vermutlich einen 64-Bit-Computer. Wenn Visual Studio auf einem 64-Bit-Betriebssystem von Windows installiert wird, stehen zusätzliche Verknüpfungen der Developer-Eingabeaufforderung für die auf x64 gehosteten nativen und kreuzkompatiblen 64-Bit-Compiler zur Verfügung. Sie können die für 64-Bit-Code verfügbare Prozessor- und Arbeitsspeicherkapazität nutzen, indem Sie das auf x64 gehostete 64-Bit Toolset verwenden, wenn Sie Builds aus Code für x86-, x64- oder ARM-Prozessoren erstellen.

## <a name="use-a-64-bit-hosted-developer-command-prompt-shortcut"></a>Verwenden einer auf 64-Bit gehosteten Developer-Eingabeaufforderungsverknüpfung

Um unter Windows 10 auf diese Eingabeaufforderungen zuzugreifen, öffnen Sie im **Startmenü** den Ordner für Ihre Visual Studio-Version, z.B. **Visual Studio 2019**, und wählen Sie dann eine der Developer-Eingabeaufforderungen für native oder kreuzkompatible x64-Tools aus.

![x64 Native Tools-Eingabeaufforderung](media/x64-native-tools-command-prompt.png "x64 Native Tools im Startmenü")

Zum Zugreifen auf diese Eingabeaufforderungen unter Windows 8 klicken Sie auf dem **Start**-Bildschirm auf **Alle Apps**. Öffnen Sie unter der Überschrift für die installierte Version von Visual Studio den Ordner **Visual Studio** (möglicherweise heißt er in älteren Visual Studio-Versionen **Visual Studio-Tools**). Wählen Sie in früheren Windows-Versionen **Start** aus, erweitern Sie **Alle Programme**, den Ordner für Ihre Version von **Visual Studio** (und in älteren Versionen von Visual Studio **Visual Studio-Tools**). Weitere Informationen finden Sie unter [Developer command prompt shortcuts (Tastenkombinationen für die Developer-Eingabeaufforderung)](building-on-the-command-line.md#developer_command_prompt_shortcuts).

## <a name="use-vcvarsallbat-to-set-a-64-bit-hosted-build-architecture"></a>Verwenden von Vcvarsall.bat zum Festlegen einer 64-Bit-gehosteten Buildarchitektur

Jede der Buildkonfigurationen mit nativen oder kreuzkompatiblen Tools kann durch Ausführen der Befehlsdatei „vcvarsall.bat“ auf der Befehlszeile verwendet werden. Diese Befehlsdatei konfiguriert die Pfad- und Umgebungsvariablen, die eine bestimmte Buildarchitektur in einem vorhandenen Eingabeaufforderungsfenster aktivieren. Ausführliche Anweisungen finden Sie unter [Speicherorte der Developer-Befehlsdatei](building-on-the-command-line.md#developer_command_file_locations).

## <a name="remarks"></a>Hinweise

> [!NOTE]
> Informationen zu den spezifischen Tools, die in den einzelnen Visual Studio-Editionen enthalten sind, finden Sie unter [Visual C++-Tools und -Features in Visual Studio-Editionen](../overview/visual-cpp-tools-and-features-in-visual-studio-editions.md).
>
> Informationen zum Verwenden der Visual Studio-IDE zum Erstellen von 64-Bit-Anwendungen finden Sie unter [Vorgehensweise: Configure Visual C++ Projects to Target 64-Bit, x64 Platforms (Vorgehensweise: Konfigurieren von Visual C++-Projekten für 64-Bit-Zielplattformen (x64))](how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md).

Wenn Sie eine C++-Workload im Visual Studio-Installer installieren, werden immer auf x86 gehostete native und kreuzkompatible 32-Bit-Compilertools zum Erstellen von x86- und x64-Code installiert. Wenn Sie die Workload Universelle Windows-Plattform einschließen, werden außerdem auf x86 gehostete kreuzkompatible Compilertools zum Erstellen von ARM-Code installiert. Wenn Sie diese Workloads auf einem x64-64-Bit-Prozessor installieren, erhalten Sie darüber hinaus native und kreuzkompatible 64-Bit-Compilertools zum Erstellen von x86-, x64- und ARM-Code. Die 32-Bit- und die 64-Bit-Tools generieren identischen Code, jedoch unterstützen die 64-Bit-Tools mehr Speicher für vorkompilierte Headersymbole und die Optimierung des gesamten Programms ([/GL](reference/gl-whole-program-optimization.md)- und [/LTCG](reference/ltcg-link-time-code-generation.md)-Optionen). Wenn Sie mit 32-Bit-Tools auf Speicherbegrenzungen treffen, versuchen Sie es mit den 64-Bit-Tools.

## <a name="see-also"></a>Siehe auch

[Konfigurieren von C++-Projekten für 64-Bit-x64-Ziele](configuring-programs-for-64-bit-visual-cpp.md)<br/>
