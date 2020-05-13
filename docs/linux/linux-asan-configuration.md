---
title: Konfigurieren von Linux-Projekten zum Verwenden von AddressSanitizer
description: In diesem Artikel wird beschrieben, wie Sie C++-Linux-Projekte in Visual Studio konfigurieren, um AddressSanitizer verwenden zu können.
ms.date: 06/07/2019
ms.openlocfilehash: 80e9ab46c948f2062391ae723c3425c435bd4507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364313"
---
# <a name="configure-linux-projects-to-use-address-sanitizer"></a>Konfigurieren von Linux-Projekten zum Verwenden von AddressSanitizer

In Visual Studio 2019 Version 16.1 ist die Unterstützung von AddressSanitizer (ASan) in Linux-Projekten integriert. Sie können ASan sowohl für MSBuild-basierte Linux-Projekte als auch für CMake-Projekte aktivieren. Dies funktioniert unter Linux-Remotesystemen und dem Windows-Subsystem für Linux (WSL).

## <a name="about-asan"></a>Informationen zu ASan

ASan ist ein Tool zum Erkennen von Fehlern im Runtimearbeitsspeicher für C/C++, das die folgenden Fehler erkennt:

- Use after free (dangling pointer reference) (Verwenden nach Freigabe; „Hängender Zeiger“-Verweis)
- Heap buffer overflow (Heappufferüberlauf)
- Stack buffer overflow (Stapelpufferüberlauf)
- Use after return (Verwenden nach Rückgabe)
- Use after scope (Verwenden nach Bereich)
- Initialization order bugs (Fehler bei der Initialisierungsreihenfolge)

Wenn ASan einen Fehler erkennt, wird die Ausführung sofort beendet. Wenn Sie im Debugger ein ASan-fähiges Programm ausführen, wird eine Nachricht angezeigt, in der der Fehlertyp, die Speicheradresse und der Speicherort in der Quelldatei beschrieben wird, in dem der Fehler aufgetreten ist:

   ![ASan-Fehlermeldung](media/asan-error.png)

Sie können sich im Debugbereich des Ausgabefensters auch die vollständige ASan-Ausgabe anzeigen lassen (einschließlich Informationen zur Zuordnung/Aufhebung der Zuordnung des beschädigten Arbeitsspeichers).

## <a name="enable-asan-for-msbuild-based-linux-projects"></a>Aktivieren von ASan für MSBuild-basierte Linux-Projekte

> [!NOTE]
> Ab Visual Studio 2019, Version 16.4 wird AddressSanitizer für Linux-Projekte über **Konfigurationseigenschaften** > **C/C++**  > **Address Sanitizer aktivieren** aktiviert.

Klicken Sie mit der rechten Maustaste auf das Projekt im **Projektmappen-Explorer**, und wählen Sie **Eigenschaften** aus, um ASan für MSBuild-basierte Linux-Projekte zu aktivieren. Navigieren Sie dann zu **Konfigurationseigenschaften** > **C/C++**  > **Sanitizer**. ASan ist über Compiler und Linker-Flags aktiviert und erfordert, dass Ihr Projekt noch mal kompiliert wird, um zu funktionieren.

![Aktivieren von ASan für ein MSBuild-Projekt](media/msbuild-asan-prop-page.png)

Navigieren Sie zu **Konfigurationseigenschaften** > **Debuggen** > **AddressSanitizer-Runtimeflags**, um optionale ASan-Runtimeflags zu übergeben. Klicken Sie zum Hinzufügen oder Entfernen von Flags auf die NACH-UNTEN-TASTE.

![Konfigurieren von ASan-Runtimeflags](media/msbuild-asan-runtime-flags.png)

## <a name="enable-asan-for-visual-studio-cmake-projects"></a>Aktivieren von ASan für CMake-Projekte in Visual Studio

Klicken Sie mit der rechten Maustaste auf die Datei „CMakeLists.txt“ im **Projektmappen-Explorer**, und wählen Sie **CMake Settings for Project** (Einstellungen für CMake-Projekt) aus, um ASan für CMake zu aktivieren.

Stellen Sie sicher, dass Sie im linken Bereich des Dialogfelds eine Linux-Konfiguration ausgewählt haben (z. B. **Linux-Debug**):

![Linux-Debugkonfiguration](media/linux-debug-configuration.png)

Die ASan-Optionen finden Sie unter **Allgemein**. Geben Sie die ASan-Runtimeflags im Format „flag=value“ (Flag=Wert) ein, und verwenden Sie dabei Semikolons.

![Linux-Debugkonfiguration](media/cmake-settings-asan-options.png)

## <a name="install-the-asan-debug-symbols"></a>Installieren der ASan-Debugsymbole

Sie müssen auf Ihrem Linux-Remotecomputer oder Ihrer WSL-Installation die Debugsymbole (libasan-dbg) installieren, um die ASan-Diagnose zu aktivieren. Die libasan-dbg-Version, die Sie laden, hängt von der auf Ihrem Linux-Computer installierten GCC-Version ab:

|**ASan-Version**|**GCC-Version**|
| --- | --- |
|libasan0|gcc-4.8|
|libasan2|gcc-5|
|libasan3|gcc-6|
|libasan4|gcc-7|
|libasan5|gcc-8|

Verwenden Sie diesen Befehl, um zu bestimmen, welche GCC-Version Sie besitzen:

```bash
gcc --version
```

Führen Sie das Programm aus, und achten Sie dann auf den Bereich **Debuggen** im **Ausgabefenster**, um die libasan-dbg-Version anzuzeigen, die Sie benötigen. Die geladene ASan-Version entspricht der libasan-dbg-Version, die auf Ihrem Linux-Computer benötigt wird. Sie können **STRG+F** verwenden, um im Fenster nach „libasan“ zu suchen. Wenn Sie beispielsweise „libasan4“ verwenden, wird Ihnen eine Zeile wie diese angezeigt:

```Output
Loaded '/usr/lib/x86_64-linux-gnu/libasan.so.4'. Symbols loaded.
```

Sie können die ASan-Debugbits unter Linux-Distributionen installieren, die „apt“ mit dem folgenden Befehl verwenden: Mit diesem Befehl wird Version 4 installiert:

```bash
sudo apt-get install libasan4-dbg
```

Wenn ASan aktiviert ist, werden Sie oben im Bereich **Debuggen** im **Ausgabefenster** von Visual Studio aufgefordert, die ASan-Debugsymbole zu installieren.
