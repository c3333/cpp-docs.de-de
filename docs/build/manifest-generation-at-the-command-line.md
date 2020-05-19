---
title: Manifestgenerierung über die Befehlszeile
ms.date: 11/04/2016
helpviewer_keywords:
- manifests [C++]
- manifest tool (mt.exe)
ms.assetid: fc2ff255-82b1-4c44-af76-8405c5850292
ms.openlocfilehash: 381406213422e286dd9aba26adcdbd6caff7bfe3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493204"
---
# <a name="manifest-generation-at-the-command-line"></a>Manifestgenerierung über die Befehlszeile

Beim Erstellen von C- und C++-Anwendungen über die Befehlszeile mithilfe von nmake oder ähnlichen Tools wird das Manifest generiert, nachdem der Linker alle Objektdateien verarbeitet und die endgültige Binärdatei erstellt hat. Der Linker erfasst die in den Objektdateien gespeicherten Assemblyinformationen und fasst sie in einer endgültigen Manifestdatei zusammen. Standardmäßig generiert der Linker eine Datei namens *binary_name*.*extension*.manifest, die die endgültige Binärdatei beschreibt. Der Linker bettet die Manifestdatei nicht in die Binärdatei ein und kann das Manifest nur als externe Datei generieren. Es gibt mehrere Möglichkeiten, ein Manifest in die endgültige Binärdatei einzubetten, z. B. mit dem [Manifesttool (mt.exe)](/windows/win32/sbscs/mt-exe) oder durch Kompilieren des Manifests in eine Ressourcendatei. Beachten Sie, dass beim Einbetten eines Manifests in die endgültige Binärdatei bestimmte Regeln befolgt werden müssen, um Features wie inkrementelles Verknüpfen, Signieren sowie Bearbeiten und Fortfahren zu aktivieren. Diese und andere Möglichkeiten werden in [ Einbetten eines Manifests in eine C-/C++-Anwendung](how-to-embed-a-manifest-inside-a-c-cpp-application.md) in Bezug auf das Erstellen über die Befehlszeile diskutiert.

## <a name="see-also"></a>Siehe auch

[Manifeste](/windows/win32/sbscs/manifests)<br/>
[/INCREMENTAL (Inkrementell verknüpfen)](reference/incremental-link-incrementally.md)<br/>
[Assemblys mit starken Namen (Assemblysignierung) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)<br/>
[Bearbeiten und Fortfahren](/visualstudio/debugger/edit-and-continue)<br/>
[Manifestgenerierung für C/C++-Programme](understanding-manifest-generation-for-c-cpp-programs.md)<br/>
