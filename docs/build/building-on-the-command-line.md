---
title: Verwenden des Microsoft C++-Toolsets über die Befehlszeile
description: Verwenden Sie die Microsoft C++ Compiler Toolchain (MSVC) auf der Befehlszeile außerhalb der Visual Studio IDE.
ms.custom: conceptual
ms.date: 11/12/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: ec30cba8e119f96efc5bca156fa565db77904520
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422901"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Verwenden des Microsoft C++-Toolsets über die Befehlszeile

Sie können mithilfe von Tools, die in Visual Studio enthalten sind, C- und C++-Anwendungen auf der Befehlszeile erstellen. Das Microsoft C++ -Compilertoolset (MSVC) kann auch als eigenständiges Paket heruntergeladen werden, das die Visual Studio-IDE nicht enthält.

## <a name="download-and-install-the-tools"></a>Herunterladen und Installieren der Tools

Wenn Sie Visual Studio und einen C++-Workload installiert haben, verfügen Sie über alle Befehlszeilentools. Informationen zum Installieren von C++ und Visual Studio finden Sie unter [Installieren der C++-Unterstützung in Visual Studio](vscpp-step-0-installation.md). Wenn Sie nur die Befehlszeilentools wünschen, laden Sie die [Visual Studio Build Tools](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019) herunter. Wenn Sie die heruntergeladene ausführbare Datei ausführen, wird der Visual Studio-Installer aktualisiert und ausgeführt. Um nur die Tools zu installieren, die Sie für die C++-Entwicklung benötigen, wählen Sie die Workload **C++-Buildtools** aus. Sie können optionale Bibliotheken und Toolsets auswählen, die unter **Installationsdetails** enthalten sein sollen. Wählen Sie zum Erstellen von Code mithilfe der Visual Studio 2015- oder 2017-Toolsets die optionalen Buildtools von MSVC v140 oder v141 aus. Wenn Sie die gewünschten Einstellungen vorgenommen haben, wählen Sie **Installieren** aus.

## <a name="how-to-use-the-command-line-tools"></a>Verwenden der Befehlszeilentools

Wenn Sie eine der C++-Workloads im Visual Studio-Installer auswählen, installiert sie das Visual Studio-*Plattformtoolset*. Ein Plattformtoolset enthält alle C- und C++-Tools für eine bestimmte Visual Studio-Version. Zu den Tools gehören die C/C++-Compiler, Linker, Assembler und andere Buildtools sowie die entsprechenden Bibliotheken. Sie können all diese Tools über die Befehlszeile verwenden. Sie werden auch intern von der Visual Studio-IDE verwendet. Es gibt separate Compiler und Tools für das Hosten auf x86- und x64-Architekturen, um Code für x86-, x64-, ARM- und ARM64-Zielumgebungen zu erstellen. Jeder Satz Tools für eine bestimmte Host- und Zielbuildarchitektur ist in einem eigenen Verzeichnis gespeichert.

Um ordnungsgemäß zu funktionieren, müssen für die Tools verschiedene spezifische Umgebungsvariablen festgelegt werden. Diese Variablen werden verwendet, um die Tools dem Pfad hinzuzufügen und die Speicherorte von Includedateien, Bibliotheksdateien und SDKs festzulegen. Um das Festlegen dieser Umgebungsvariablen zu vereinfachen, erstellt der Installer während der Installation angepasste *Befehlsdateien* oder Batchdateien. Sie können eine dieser Befehlsdateien ausführen, um eine bestimmte Host- und Zielbuildarchitektur, eine Windows SDK-Version oder ein Plattformtoolset festzulegen. Aus praktischer Gründen erstellt das Installationsprogramm auch Verknüpfungen im Startmenü. Die Verknüpfungen starten Developer-Eingabeaufforderungen, indem sie diese Befehlsdateien für bestimmte Kombinationen von Host und Ziel verwenden. Diese Verknüpfungen stellen sicher, dass alle erforderlichen Umgebungsvariablen festgelegt und einsatzbereit sind.

Die erforderlichen Umgebungsvariablen sind für Ihre Installation und für die von Ihnen gewählte Buildarchitektur spezifisch. Sie können sich bei Updates oder Upgrades des Produkts ändern. Daher wird empfohlen, dass Sie eine installierte Verknüpfung oder Befehlsdatei zu einer Eingabeaufforderung verwenden, anstatt die Umgebungsvariablen selbst festzulegen. Weitere Informationen finden Sie unter [Set the path and environment variables for command-line builds (Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds)](setting-the-path-and-environment-variables-for-command-line-builds.md).

Welche Toolsets, Befehlsdateien und Verknüpfungen installiert werden, hängt vom Prozessor Ihres Computers und den während der Installation aktivierten Optionen ab. Die in x86-Systemen gehosteten Tools und Cross Tools, die x86-und x64-Code erstellen, sind immer installiert. Wenn Sie über ein Windows-System mit 64 Bit verfügen, werden die im x64-System gehosteten Tools und Cross Tools, die x86-und x64-Code erstellen, ebenfalls installiert. Wenn Sie die optionalen C++-Tools für Universelle Windows-Plattform auswählen, werden die x86-und x64-Tools, die ARM- und ARM64-Code erstellen, ebenfalls installiert. Von anderen Workloads werden möglicherweise zusätzliche Tools installiert.

## <a name="developer-command-prompt-shortcuts"></a><a name="developer_command_prompt_shortcuts"></a>Developer-Eingabeaufforderungsverknüpfungen

Die Eingabeaufforderungsverknüpfungen werden in einem versionsspezifischen Visual Studio-Ordner in Ihrem Startmenü gespeichert. Das Folgende ist eine Liste der grundlegenden Eingabeaufforderungsverknüpfungen und der von ihnen unterstützten Buildarchitekturen:

- **Developer-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x86-nativen 32-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code fest.
- **x86 Native Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x86-nativen 32-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code fest.
- **x64 Native Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x64-nativen 64-Bit-Tools zum Erstellen von x64-nativem 64-Bit-Code fest.
- **x86_x64 Cross Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x86-nativen 32-Bit-Tools zum Erstellen von x64-nativem 64-Bit-Code fest.
- **x64_x86 Cross Tools-Eingabeaufforderung**: Legt die Umgebung für die Verwendung von x64-nativen 64-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code fest.

::: moniker range=">= vs-2019"

Die Namen des Startmenü-Ordners und der Verknüpfungen hängen von der installierten Visual Studio-Version ab. Wenn Sie einen festlegen, hängt dieser auch vom **Spitznamen** der Installation ab. Angenommen, Sie haben Visual Studio 2019 installiert und der Installation den Spitznamen *Aktuell* gegeben. Die Verknüpfung der Developer-Eingabeaufforderung heißt **Developer-Eingabeaufforderung für VS 2019 (Aktuell)** , in einem Ordner mit dem Namen **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Die Namen des Startmenü-Ordners und der Verknüpfungen hängen von der installierten Visual Studio-Version ab. Wenn Sie einen festlegen, hängt dieser auch vom **Spitznamen** der Installation ab. Angenommen, Sie haben Visual Studio 2017 installiert und der Installation den Spitznamen *Aktuell* gegeben. Die Verknüpfung der Developer-Eingabeaufforderung heißt **Developer-Eingabeaufforderung für VS 2017 (Aktuell)** , in einem Ordner mit dem Namen **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Die Namen des Startmenü-Ordners und der Verknüpfungen hängen von der installierten Visual Studio-Version ab. Angenommen, Sie haben Visual Studio 2015 installiert. Die Verknüpfung der Developer-Eingabeaufforderung heißt **Developer-Eingabeaufforderung für VS 2015**.

::: moniker-end

### <a name="to-open-a-developer-command-prompt-window"></a><a name="developer_command_prompt"></a> So öffnen Sie ein Developer-Eingabeaufforderungsfenster

1. Öffnen Sie auf dem Desktop das Windows-**Startmenü**, und scrollen Sie dann nach unten, um den Ordner für Ihre Visual Studio-Version zu finden und zu öffnen, beispielsweise **Visual Studio 2019**.

1. Wählen Sie im Ordner die **Developer-Eingabeaufforderung** für Ihre Version von Visual Studio aus. Diese Verknüpfung startet ein Developer-Eingabeaufforderungsfenster, das die Standardbuildarchitektur mit x86-nativen 32-Bit-Tools zum Erstellen von x86-nativem 32-Bit-Code verwendet. Falls Sie eine andere als die Standardbuildarchitektur vorziehen, wählen Sie eine der Eingabeaufforderungen mit nativen oder kreuzkompatiblen Tools aus, um die Host- und die Zielarchitektur anzugeben.

Sogar noch schneller lässt sich eine Developer-Eingabeaufforderung öffnen, wenn Sie *Developer-Eingabeaufforderung* in das Suchfeld auf dem Desktop eingeben. Wählen Sie dann das gewünschte Ergebnis aus.

## <a name="developer-command-file-locations"></a><a name="developer_command_file_locations"></a> Speicherorte von Developer-Befehlsdateien

Wenn Sie es vorziehen, die Buildumgebung in einem vorhandenen Eingabeaufforderungsfenster festzulegen, können Sie eine der vom Installer erstellten Befehlsdateien verwenden. Es wird empfohlen, dass Sie die Umgebung in einem neuen Eingabeaufforderungsfenster festlegen. Wir raten davon ab, später im gleichen Befehlsfenster die Umgebung zu wechseln.

::: moniker range=">= vs-2019"

Der Speicherort der Befehlsdatei hängt von der installierten Version von Visual Studio und Ihren bei der Installation gewählten Optionen ab. Für Visual Studio 2019 ist der typische Installationsspeicherort in einem 64-Bit-System in \\Programme (x86)\\Microsoft Visual Studio\\2019\\*Edition*. Die *Edition* kann „Community“, „Professional“, „Enterprise“, „Buildtools“ oder ein anderer Spitzname sein.

::: moniker-end
::: moniker range="= vs-2017"

Der Speicherort der Befehlsdatei hängt von der installierten Version von Visual Studio und Ihren bei der Installation gewählten Optionen ab. Für Visual Studio 2017 ist der typische Installationsspeicherort in einem 64-Bit-System in \\Programme (x86)\\Microsoft Visual Studio\\2017\\*Edition*. Die *Edition* kann „Community“, „Professional“, „Enterprise“, „Buildtools“ oder ein anderer Spitzname sein.

::: moniker-end
::: moniker range="< vs-2017"

Der Speicherort der Befehlsdatei hängt von der Visual Studio-Version und dem Installationsverzeichnis ab. Für Visual Studio 2015 ist der typische Installationsspeicherort in \\Programme (x86)\\Microsoft Visual Studio 14.0.

::: moniker-end

Die primäre Befehlsdatei der Developer-Eingabeaufforderung, „VsDevCmd.bat“, befindet sich im Unterverzeichnis „Common7\\Tools“. Wenn keine Parameter angegeben werden, wird die Umgebung so festgelegt, dass die x86 Native Tools-Eingabeaufforderung zum Erstellen von 32-Bit-x86-Code verwendet wird.

::: moniker range=">= vs-2017"

Zum Einrichten spezifischer Buildarchitekturen gibt es weitere Befehlsdateien. Welche Befehlsdateien verfügbar sind, hängt von den Visual Studio-Workloads und den von Ihnen installierten Optionen ab. Für Visual Studio 2017 und Visual Studio 2019 ist dies das Unterverzeichnis „VC\\Auxiliary\\Build“.

::: moniker-end
::: moniker range="< vs-2017"

Zum Einrichten spezifischer Buildarchitekturen gibt es weitere Befehlsdateien. Welche Befehlsdateien verfügbar sind, hängt von den Visual Studio-Workloads und den von Ihnen installierten Optionen ab. In Visual Studio 2015 finden Sie die Dateien in den Unterverzeichnissen „VC“, „VC\\bin“ oder „VC\\bin\\*architecture*“, wobei *architecture* für eine der nativen oder kreuzkompatiblen Compileroptionen steht.

::: moniker-end

Diese Befehlsdateien legen Standardparameter fest und rufen „VsDevCmd.bat“ auf, um die angegebene Buildarchitekturumgebung einzurichten. Eine typische Installation kann etwa diese Befehlsdateien enthalten:

|Befehlsdatei|Host- und Zielarchitekturen|
|---|---|
|**vcvars32.bat**| Die x86-nativen 32-Bit-Tools werden zum Erstellen von 32-Bit-x86-Code verwendet.|
|**vcvars64.bat**| Die x64-nativen 64-Bit-Tools werden zum Erstellen von 64-Bit-x64-Code verwendet.|
|**vcvarsx86_amd64.bat**| Die x86-nativen 32-Bit kreuzkompatiblen Tools werden zum Erstellen von 64-Bit-x64-Code verwendet.|
|**vcvarsamd64_x86.bat**| Die x64-nativen 64-Bit kreuzkompatiblen Tools werden zum Erstellen von 32-Bit-x86-Code verwendet.|
|**vcvarsx86_arm.bat**| Die x86-nativen 32-Bit kreuzkompatiblen Tools werden zum Erstellen ARM-Code verwendet.|
|**vcvarsamd64_arm.bat**| Die x64-nativen 64-Bit kreuzkompatiblen Tools werden zum Erstellen ARM-Code verwendet.|
|**vcvarsall.bat**| Verwenden Sie Parameter zum Angeben der Host- und Zielarchitekturen, Windows SDK und Plattformoptionen. Um eine Liste der unterstützten Optionen anzuzeigen, rufen Sie diesen Befehl mit dem Parameter **/help** auf.|

> [!CAUTION]
> Die vcvarsall.bat-Datei und andere Visual Studio-Befehlsdateien können sich von Computer zu Computer unterscheiden. Ersetzen Sie eine fehlender oder beschädigte vcvarsall.bat-Datei nicht durch eine Datei von einem anderen Computer. Führen Sie den Visual Studio-Installer erneut aus, um die fehlende Datei zu ersetzen.
>
> Die vcvarsall.bat-Datei ist auch von Version zu Version unterschiedlich. Falls die aktuelle Version von Visual Studio auf einem Computer installiert ist, der außerdem über eine frühere Version von Visual Studio verfügt, sollten Sie nicht „vcvarsall.bat“ oder eine andere Visual Studio-Befehlsdatei aus einer anderen Version im selben Eingabeaufforderungsfenster ausführen.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Verwenden der Entwicklertools in einem vorhandenen Befehlsfenster

Die einfachste Möglichkeit, eine bestimmte Buildarchitektur in einem vorhandenen Befehlsfenster anzugeben, ist die Verwendung der Datei „vcvarsall.bat“. Legen Sie mit „vcvarsall.bat“ die Umgebungsvariablen fest, um die Befehlszeile für die native 32-Bit- oder 64-Bit-Kompilierung zu konfigurieren. Mit Argumenten können Sie die Kreuzkompilierung für x86-, x64-, ARM- oder ARM64-Prozessoren angeben. Als Ziel können Sie Microsoft Store, Universelle Windows-Plattform oder Windows Desktop-Plattformen angeben. Sie können sogar festlegen, welche Windows SDK verwendet werden sollen, und die Toolsetversion der Plattform auswählen.

Wenn keine Argumente angegeben werden, werden die Umgebungsvariablen mit „vcvarsall.bat“ so konfiguriert, dass der aktuelle native x86-Compiler für Ziele mit 32-Bit-Windows Desktop verwendet wird. Sie können Argumente hinzufügen, um die Umgebung so zu konfigurieren, dass Sie eines der nativen oder kreuzkompatiblen Compilertools verwendet. Wenn Sie eine Konfiguration angeben, die auf Ihrem Computer nicht installiert oder verfügbar ist, zeigt „vcvarsall.bat“ eine Fehlermeldung an.

### <a name="vcvarsall-syntax"></a>vcvarsall-Syntax

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

*architecture*<br/>
Dieses optionale Argument gibt die zu verwendende Host- und Zielarchitektur an. Wenn *architecture* nicht angegeben wird, wird die Standardbuildumgebung verwendet. Diese Argumente werden unterstützt:

|*architecture*|Compiler|Hostcomputerarchitektur|Buildausgabearchitektur (Zielarchitektur)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86-32-Bit systemeigen|x86, x64|x86|
|**x86\_amd64** oder **x86\_x64**|x64 kreuzkompatibel auf x86|x86, x64|x64|
|**x86_arm**|ARM auf x86-Cross|x86, x64|ARM|
|**x86_arm64**|ARM64 kreuzkompatibel auf x86|x86, x64|ARM64|
|**amd64** oder **x64**|x64 64-Bit nativ|x64|x64|
|**amd64\_x86** oder **x64\_x86**|x86 kreuzkompatibel auf x64|x64|x86|
|**amd64\_arm** oder **x64\_arm**|ARM kreuzkompatibel auf x64|x64|ARM|
|**amd64\_arm64** oder **x64\_arm64**|ARM64 kreuzkompatibel auf x64|x64|ARM64|

*platform_type*<br/>
Dieses optionale Argument ermöglicht Ihnen die Angabe von **store** oder **uwp** als Plattformtyp. Standardmäßig ist die Umgebung auf das Erstellen von Desktop- oder Konsolen-Apps festgelegt.

*winsdk_version*<br/>
Gibt optional die Version des zu verwendenden Windows SDK an. Standardmäßig wird das neueste installierte Windows SDK verwendet. Um die Windows SDK-Version anzugeben, können Sie eine vollständige Windows 10 SDK-Nummer, wie etwa **10.0.10240.0**, verwenden oder **8.1** angeben, wenn Sie das Windows 8.1 SDK verwenden möchten.

*vcversion*<br/>
Gibt optional das zu verwendende Visual Studio-Compilertoolset an. Standardmäßig ist die Umgebung auf die Verwendung des aktuellen Visual Studio-Compilertoolsets festgelegt.

::: moniker range=">= vs-2019"

Verwenden Sie **-vcvars_ver=14.2x.yyyyy**, um eine bestimmte Version des Compilertoolsets von Visual Studio 2019 anzugeben.

Verwenden Sie **-vcvars_ver=14.16**, um die neueste Version des Compilertoolsets von Visual Studio 2017 anzugeben.

::: moniker-end
::: moniker range="= vs-2017"

Verwenden Sie **-vcvars_ver=14.16**, um die neueste Version des Compilertoolsets von Visual Studio 2017 anzugeben.

Verwenden Sie **-vcvars_ver=14.1x.yyyyy**, um eine bestimmte Version des Compilertoolsets von Visual Studio 2017 anzugeben.

::: moniker-end

Verwenden Sie **-vcvars_ver=14.0**, um das Compilertoolset von Visual Studio 2015 anzugeben.

#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a><a name="vcvarsall"></a> Einrichten der Buildumgebung in einem vorhandenen Eingabeaufforderungsfenster

1. Verwenden Sie an der Eingabeaufforderung den CD-Befehl, um in das Visual Studio-Installationsverzeichnis zu wechseln. Verwenden Sie dann erneut CD, um in das Unterverzeichnis zu wechseln, das die konfigurationsspezifischen Befehlsdateien enthält. Für Visual Studio 2019 und Visual Studio 2017 ist dies das Unterverzeichnis *VC\\Auxiliary\\Build*. Verwenden Sie für Visual Studio 2015 das Unterverzeichnis *VC*.

1. Geben Sie den Befehl für Ihre bevorzugte Entwicklerumgebung ein. Um beispielsweise ARM-Code für UWP auf einer 64-Bit-Plattform mithilfe des aktuellen Windows SDK und Visual Studio 2019-Compilertoolsets zu erstellen, verwenden Sie diese Befehlszeile:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Erstellen einer eigenen Eingabeaufforderungsverknüpfung

::: moniker range=">= vs-2019"

Öffnen Sie das Dialogfeld „Eigenschaften“ für eine Verknüpfung zur Developer-Eingabeaufforderung, um das verwendete Befehlsziel anzuzeigen. Beispielsweise ist das Ziel für die Verknüpfung **x64 Native Tools-Eingabeaufforderung für VS 2019** ähnlich wie dies hier:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Öffnen Sie das Dialogfeld „Eigenschaften“ für eine Verknüpfung zur Developer-Eingabeaufforderung, um das verwendete Befehlsziel anzuzeigen. Beispielsweise ist das Ziel für die Verknüpfung **x64 Native Tools-Eingabeaufforderung für VS 2017** ähnlich wie dies hier:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Öffnen Sie das Dialogfeld „Eigenschaften“ für eine Verknüpfung zur Developer-Eingabeaufforderung, um das verwendete Befehlsziel anzuzeigen. Beispielsweise ist das Ziel für die Verknüpfung **VS2015 x64 Native Tools-Eingabeaufforderung** ähnlich wie dies hier:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

Die architekturspezifischen Batchdateien legen den *architecture*-Parameter fest und rufen „vcvarsall.bat“ auf. Sie können diesen Batchdateien die gleichen Optionen übergeben, die Sie an „vcvarsall.bat“ übergeben würden, oder Sie können „vcvarsall.bat“ einfach direkt aufrufen. Um Parameter für Ihre eigene Befehlsverknüpfung anzugeben, fügen Sie sie am Ende des Befehls in doppelten Anführungszeichen hinzu. Hier sehen Sie beispielsweise eine Verknüpfung zum Erstellen von ARM-Code für die UWP auf einer 64-Bit-Plattform mit dem neuesten Windows SDK. Wenn Sie ein früheres Compilertoolset verwenden möchten, geben Sie die Versionsnummer an. Verwenden Sie in Ihrer Verknüpfung etwas in der Art dieses Befehlsziels:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Passen Sie den Pfad an, damit er Ihr Visual Studio-Installationsverzeichnis angibt. Die vcvarsall.bat-Datei enthält zusätzliche Informationen über bestimmte Versionsnummern.

## <a name="command-line-tools"></a>Befehlszeilentools

Zum Erstellen eines C-/C++-Projekts über eine Eingabeaufforderung bietet Visual Studio die folgenden Befehlszeilentools:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Verwenden Sie den Compiler (cl.exe), um Quellcodedateien in Apps, Bibliotheken und DLLs zu kompilieren und zu verknüpfen.

[Link](reference/linking.md)<br/>
Verwenden Sie den Linker (link.exe), um kompilierte Objektdateien in Apps und DLLs zu verknüpfen.

[MSBuild](msbuild-visual-cpp.md)<br/>
Verwenden Sie MSBuild (msbuild.exe) und eine Projektdatei (.vcxproj), um einen Build zu konfigurieren und das Toolset indirekt aufzurufen. Dies entspricht dem Ausführen des Befehls **Build** für Projekte oder **Projektmappe erstellen** in der Visual Studio-IDE. Das Ausführen von MSBuild über die Befehlszeile ist ein fortgeschrittenes Szenario und wird allgemein nicht empfohlen.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Verwenden Sie DEVENV (devenv.exe) in Kombination mit einem Befehlszeilenschalter, wie **/Build** oder **/Clean**, um bestimmte Buildbefehle auszuführen, ohne die Visual Studio-IDE anzuzeigen. Im Allgemeinen ist DEVENV der direkten Verwendung von MSBuild vorzuziehen, da Sie Visual Studio die Komplexität von MSBuild überlassen können.

[NMAKE](reference/nmake-reference.md)<br/>
Verwenden Sie NMAKE (nmake.exe) unter Windows, um C++-Projekte auf der Grundlage eines traditionellen Makefiles zu erstellen.

Wenn Sie Builds über die Befehlszeile ausführen, ist der F1-Befehl für Soforthilfe nicht verfügbar. Stattdessen können Sie eine Suchmaschine verwenden, um Informationen über Warnungen, Fehler und Meldungen abzurufen, oder Sie können die Offline-Hilfedateien verwenden. Um die Suche in [docs.microsoft.com](https://docs.microsoft.com/cpp/) zu verwenden, geben Sie den Suchbegriff in das Suchfeld oben auf der Seite ein.

## <a name="in-this-section"></a>In diesem Abschnitt

In diesen Artikeln erfahren Sie, wie Sie Apps über die Befehlszeile erstellen und wie Sie die Buildumgebung der Befehlszeile anpassen. Einige zeigen, wie man 64-Bit-Toolsets verwendet und x86-, x64-, ARM- und ARM64-Plattformen als Ziel einsetzt. Außerdem wird die Verwendung der Befehlszeilen-Buildtools MSBuild und NMAKE beschrieben.

[Walkthrough: Compiling a Native C++ Program on the Command Line (Exemplarische Vorgehensweise: Kompilieren eines nativen C++-Programms in der Befehlszeile)](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).<br/>
Gibt ein Beispiel, das zeigt, wie Sie ein C++-Programm über die Befehlszeile erstellen und kompilieren.

[Exemplarische Vorgehensweise: Kompilieren eines C-Programms in der Befehlszeile](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Beschreibt, wie Sie ein in der Programmiersprache C geschriebenes Programm kompilieren.

[Exemplarische Vorgehensweise: Kompilieren eines C++ / CLI-Programms in der Befehlszeile](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Beschreibt, wie Sie ein C++-/CLI-Programm erstellen und kompilieren, das .NET Framework verwendet.

[Walkthrough: Compiling a C++/CX program on the command line (Exemplarische Vorgehensweise: Kompilieren eines C++- / CX-Programms in der Befehlszeile)](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Beschreibt, wie Sie ein C++-/CX-Programm erstellen und kompilieren, das die Windows Runtime verwendet.

[Set the path and environment variables for command-line builds (Festlegen der Pfad- und Umgebungsvariablen für Befehlszeilenbuilds)](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Beschreibt, wie Umgebungsvariablen für die Verwendung eines 32-Bit- oder 64-Bit-Toolsets für x86-, x64-, ARM- und ARM64-Plattformen festgelegt werden.

[NMAKE-Referenz](reference/nmake-reference.md)<br/>
Enthält Links zu Artikeln, in denen das Microsoft Program Maintenance Utility (NMAKE.EXE) beschrieben wird.

[MSBuild on the Command Line – C++ (C++: MSBuild in der Befehlszeile)](msbuild-visual-cpp.md)<br/>
Enthält Links zu Artikeln, in denen die Verwendung von msbuild.exe auf der Befehlszeile dargestellt wird.

## <a name="related-sections"></a>Verwandte Abschnitte

[/MD, /MT, /LD (Use run-time library) (/MD, /MT, /LD (Runtimebibliothek verwenden))](reference/md-mt-ld-use-run-time-library.md)<br/>
Beschreibt die Verwendung dieser Compileroptionen für eine Debug- oder Releaselaufzeitbibliothek.

[Compileroptionen](reference/compiler-options.md)<br/>
Enthält Links zu Artikeln, in denen die C- und C++-Compileroptionen sowie CL.exe erläutert werden.

[Linkeroptionen](reference/linker-options.md)<br/>
Enthält Links zu Artikeln, in denen die Linkeroptionen und LINK.EXE dargestellt werden.

[Zusätzliche MSVC-Buildtools](reference/c-cpp-build-tools.md)<br/>
Enthält Links zu den C-/C++-Buildtools, die in Visual Studio enthalten sind.

## <a name="see-also"></a>Siehe auch

[Projekte und Buildsysteme](projects-and-build-systems-cpp.md)
