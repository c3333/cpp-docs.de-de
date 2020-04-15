---
title: Auswählen des Formats von .netmodule-Eingabedateien
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320571"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>Auswählen des Formats von .netmodule-Eingabedateien

Eine MSIL .obj-Datei (kompiliert mit [/clr](clr-common-language-runtime-compilation.md)) kann auch als .netmodule-Datei verwendet werden.  .obj-Dateien enthalten Metadaten und systemeigene Symbole.  .netmodules enthalten nur Metadaten.

Sie können eine MSIL .obj-Datei über die Compileroption /addmodule an jeden anderen Visual Studio-Compiler übergeben (beachten Sie jedoch, dass die .obj-Datei Teil der resultierenden Assembly wird und mit der Assembly ausgeliefert werden muss).  Beispielsweise verfügen Visual C- und Visual Basic über die Compileroption /addmodule.

> [!NOTE]
> In den meisten Fällen müssen Sie dem Linker die .obj-Datei aus der Kompilierung übergeben, die das .net-Modul erstellt hat.  Das Übergeben einer .dll- oder .netmodule MSIL-Moduldatei an den Linker kann zu LNK1107 führen.

.obj-Dateien, zusammen mit den zugehörigen .h-Dateien, auf die Sie über #include in der Quelle verweisen, ermöglichen es C++-Anwendungen, die systemeigenen Typen im Modul zu verwenden, während in einer .netmodule-Datei nur die verwalteten Typen von einer C++-Anwendung verwendet werden können.  Wenn Sie versuchen, eine .obj-Datei an #using zu übergeben, sind keine Informationen zu systemeigenen Typen verfügbar. #include stattdessen die .obj-Datei der .h-Datei.

Andere Visual Studio-Compiler können nur verwaltete Typen aus einem Modul verwenden.

Verwenden Sie Folgendes, um zu bestimmen, ob Sie ein .netmodule oder eine .obj-Datei als Moduleingabe für den MSVC-Linker verwenden müssen:

- Wenn Sie mit einem anderen Visual Studio-Compiler als Visual C++ erstellen, erstellen Sie ein .netmodule, und verwenden Sie das .netmodule als Eingabe für den Linker.

- Wenn Sie den MSVC-Compiler zum Erstellen von Modulen verwenden und die Module zum Erstellen einer anderen Version als einer Bibliothek verwendet werden, verwenden Sie die vom Compiler erstellten .obj-Dateien als Moduleingabe für den Linker. verwenden Sie die .netmodule-Datei nicht als Eingabe.

- Wenn Ihre Module zum Erstellen einer systemeigenen (nicht verwalteten) Bibliothek verwendet werden, verwenden Sie .obj-Dateien als Moduleingabe für den Linker und generieren Sie eine .lib-Bibliotheksdatei.

- Wenn Ihre Module zum Erstellen einer verwalteten Bibliothek verwendet werden und alle Moduleingaben für den Linker überprüfbar sind (produziert mit /clr:safe), verwenden Sie .obj-Dateien als Moduleingabe für den Linker und generieren Sie eine .dll (Assembly) oder .netmodule (Modul) Bibliotheksdatei.

- Wenn Ihre Module zum Erstellen einer verwalteten Bibliothek verwendet werden und ein oder mehrere Module, die in den Linker eingegeben werden, mit just /clr erstellt werden, verwenden Sie .obj-Dateien als Moduleingabe für den Linker und generieren Sie eine .dll (Assembly).  Wenn Sie verwaltete Typen aus der Bibliothek verfügbar machen möchten und wenn Sie auch möchten, dass C++-Anwendungen die systemeigenen Typen in der Bibliothek verwenden, besteht Ihre Bibliothek aus den .obj-Dateien für die Bibliothekskomponentenmodule (Sie möchten auch die .h-Dateien für jedes Modul versenden, damit sie mit #include aus dem Quellcode referenziert werden können).

## <a name="see-also"></a>Siehe auch

[.NETMODULE-Dateien als Eingabe für den Linker](netmodule-files-as-linker-input.md)
