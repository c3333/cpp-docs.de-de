---
title: /clr (Common Language Runtime-Kompilierung)
description: Verwenden Sie die Microsoft C++-Compileroption/clr, um C++/CLI-und C++-Code als verwalteten Code zu kompilieren.
ms.date: 10/25/2020
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
ms.openlocfilehash: b4634b63e58344893d99e2217e57693a2c169f66
ms.sourcegitcommit: faecabcdd12ff53eb79dc0df193fc3567f2f037c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92639093"
---
# <a name="clr-common-language-runtime-compilation"></a>`/clr` (Common Language Runtime-Kompilierung)

Ermöglicht Anwendungen und Komponenten, Funktionen aus der Common Language Runtime (CLR) zu verwenden.

## <a name="syntax"></a>Syntax

> **`/clr`**\[**`:`**_Optionen_ ]

## <a name="arguments"></a>Argumente

*Optionen*\
Eines oder mehrere der folgenden durch Trennzeichen getrennten Argumente.

- Keine

   Ohne Optionen werden **`/clr`** von Metadaten für die Anwendung erstellt. Die Metadaten können von anderen CLR-Anwendungen genutzt werden, und ermöglichen, dass eine Anwendung Typen und Daten in den Metadaten anderer CLR-Komponenten nutzt. Weitere Informationen finden Sie unter [Gemischte (native und verwaltete) Assemblys](../../dotnet/mixed-native-and-managed-assemblies.md).

- **`pure`**

   **`/clr:pure` ist veraltet** . Die Option wurde in Visual Studio 2017 und höher entfernt. Es wird empfohlen, dass Sie Code, der reines MSIL sein muss, nach C# portieren.

- **`safe`**

   **`/clr:safe` ist veraltet** . Die Option wurde in Visual Studio 2017 und höher entfernt. Es wird empfohlen, dass Sie Code, der sicheres MSIL sein muss, nach C# portieren.

- **`noAssembly`**

   **`/clr:noAssembly` ist veraltet** . Verwenden Sie stattdessen [ `/LN` (MSIL-Modul erstellen)](ln-create-msil-module.md) .

   Weist den Compiler an, ein Assemblymanifest nicht in die Ausgabedatei einzufügen. Standardmäßig ist die **`noAssembly`** Option nicht wirksam.

   Ein verwaltetes Programm, das keine Assemblymetadaten im Manifest hat, wird als *Modul* bezeichnet. Die **`noAssembly`** Option kann nur zum Entwickeln eines Moduls verwendet werden. Wenn Sie mit und kompilieren [`/c`](c-compile-without-linking.md) **`/clr:noAssembly`** , geben Sie die [`/NOASSEMBLY`](noassembly-create-a-msil-module.md) Option in der Linkerphase ein, um ein Modul zu erstellen.

   Vor Visual Studio 2005 **`/clr:noAssembly`** erforderlich **`/LD`** . **`/LD`** wird jetzt impliziert, wenn Sie angeben **`/clr:noAssembly`** .

- **`initialAppDomain`**

   Ermöglicht die Ausführung einer C++/CLI-Anwendung in Version 1 der CLR.  Eine Anwendung, die mithilfe von kompiliert **`initialAppDomain`** wird, sollte nicht von einer Anwendung verwendet werden, die ASP.NET verwendet, da Sie in Version 1 der CLR nicht unterstützt wird.

- **`nostdlib`**

   Weist den Compiler an, das Standardverzeichnis zu ignorieren *`\clr`* . Der Compiler erzeugt Fehler, wenn Sie mehrere Versionen einer DLL einschließen, z. b. System.dll. Mit dieser Option können Sie angeben, welches Framework während der Kompilierung verwendet werden soll.

## <a name="remarks"></a>Hinweise

Verwalteter Code ist Code, der überprüft und von der CLR verwaltet werden kann. Verwalteter Code kann auf verwaltete Objekte zugreifen. Weitere Informationen finden Sie unter [ `/clr ` Einschränkungen](clr-restrictions.md).

Informationen zum Entwickeln von Anwendungen, die verwaltete Typen in C++ definieren und verwenden, finden Sie unter [Komponenten Erweiterungen für laufzeitplattformen](../../extensions/component-extensions-for-runtime-platforms.md).

Eine mit kompilierte Anwendung **`/clr`** kann verwaltete Daten enthalten.

Informationen zum Aktivieren des Debuggens für eine verwaltete Anwendung finden [ `/ASSEMBLYDEBUG` Sie unter (DebuggableAttribute hinzufügen)](assemblydebug-add-debuggableattribute.md).

Auf dem Heap der Garbage Collection werden nur CLR-Typen instanziiert. Weitere Informationen finden Sie unter [Klassen und Strukturen](../../extensions/classes-and-structs-cpp-component-extensions.md). Um eine Funktion in systemeigenem Code zu kompilieren, verwenden Sie das `unmanaged` -Pragma. Weitere Informationen finden [ `managed` `unmanaged` Sie unter. ](../../preprocessor/managed-unmanaged.md)

Standardmäßig **`/clr`** ist nicht wirksam. Wenn **`/clr`** wirksam ist, **`/MD`** ist auch wirksam. Weitere Informationen finden Sie unter [ `/MD` , `/MT` , `/LD` (Run-Time Bibliothek verwenden)](md-mt-ld-use-run-time-library.md). **`/MD`** stellt sicher, dass die dynamisch verknüpften Multithread-Versionen der Lauf Zeit Routinen aus den Standard Header Dateien ausgewählt werden. Multithreading ist für die verwaltete Programmierung erforderlich, da der CLR-Garbage Collector Finalizer in einem Hilfsthread ausführt.

Wenn Sie mit kompilieren **`/c`** , können Sie mithilfe der Linkeroption den CLR-Typ der resultierenden Ausgabedatei angeben [`/CLRIMAGETYPE`](clrimagetype-specify-type-of-clr-image.md) .

**`/clr`** impliziert **`/EHa`** , und **`/EH`** es werden keine weiteren Optionen für unterstützt **`/clr`** . Weitere Informationen finden Sie unter [ `/EH` (Ausnahme Behandlungsmodell)](eh-exception-handling-model.md).

Informationen zum Bestimmen des CLR-Bildtyps einer Datei finden Sie unter [`/CLRHEADER`](clrheader.md) .

Alle an einen bestimmten Aufruf des Linkers über gebenden Module müssen mithilfe derselben Lauf Zeit Bibliotheks-Compileroption ( **`/MD`** oder) kompiliert werden **`/LD`** .

Verwenden [`/ASSEMBLYRESOURCE`](assemblyresource-embed-a-managed-resource.md) Sie die Linkeroption, um eine Ressource in eine Assembly einzubetten. [`/DELAYSIGN`](delaysign-partially-sign-an-assembly.md)mit den [`/KEYCONTAINER`](keycontainer-specify-a-key-container-to-sign-an-assembly.md) Optionen, und Linkeroptionen können [`/KEYFILE`](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) Sie auch anpassen, wie eine Assembly erstellt wird.

Wenn **`/clr`** verwendet wird, `_MANAGED` wird das Symbol als 1 definiert. Weitere Informationen finden Sie unter [vordefinierte Makros](../../preprocessor/predefined-macros.md).

Die globalen Variablen in einer systemeigenen Objektdatei werden zuerst initialisiert (während `DllMain` die ausführbare Datei eine dll ist), und anschließend werden die globalen Variablen im verwalteten Abschnitt initialisiert (bevor verwalteter Code ausgeführt wird). [`#pragma init_seg`](../../preprocessor/init-seg.md) wirkt sich nur auf die Reihenfolge der Initialisierung in den verwalteten und nicht verwalteten Kategorien aus.

### <a name="metadata-and-unnamed-classes"></a>Metadaten und unbenannte Klassen

Unbenannte Klassen erscheinen in Metadaten unter Namen wie  `$UnnamedClass$<crc-of-current-file-name>$<index>$` , wobei `<index>` eine sequenzielle Anzahl der unbenannten Klassen in der Kompilierung ist. Im folgenden Codebeispiel wird z. B. eine unbenannte Klasse in den Metadaten generiert.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

Mithilfe von ildasm.exe können Sie Metadaten anzeigen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Legen Sie die Dropdown Liste **Konfiguration** auf **alle Konfigurationen** fest, und legen Sie die Dropdown Liste **Plattform** auf **alle Plattformen** fest.

1. Wählen Sie die Seite Erweiterte **Konfigurations Eigenschaften** aus  >  **Advanced** .

1. Ändern Sie die Eigenschaft **Common Language Runtime-Unterstützung** . Klicken Sie auf **OK** , um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-CompilerCommand-Line Syntax](compiler-command-line-syntax.md)
