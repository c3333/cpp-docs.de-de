---
title: LINK-Optionen, die über den Compiler gesteuert werden
ms.date: 11/04/2016
helpviewer_keywords:
- LINK tool [C++], compiler-controlled options
- linker [C++], CL compiler control
- linking [C++], affected by CL features
- cl.exe compiler [C++], features that affect linking
- cl.exe compiler [C++], controlling linker
ms.assetid: e4c03896-c99c-4599-8502-e0f4bebe69d0
ms.openlocfilehash: f631d0ebbbd9e60fe5d54aac6fb158461d3f4d38
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440108"
---
# <a name="compiler-controlled-link-options"></a>LINK-Optionen, die über den Compiler gesteuert werden

Der CL-Compiler ruft den Link automatisch auf, sofern Sie nicht die/c-Option angeben. CL bietet eine gewisse Kontrolle über den Linker über Befehlszeilenoptionen und Argumente. In der folgenden Tabelle werden die Features in cl zusammengefasst, die sich auf das Verknüpfen auswirken

|CL-Spezifikation|CL-Aktion, die den Link beeinflusst|
|----------------------|---------------------------------|
|Eine andere Dateinamenerweiterung als. c,. cxx,. cpp oder. def|Übergibt einen Dateinamen als Eingabe an den Link.|
|*Dateiname*. def|Übergibt/DEF:*filename*. def|
|/F-*Nummer*|Übergibt/Stack:*Number*|
|/FD*Dateiname*|Übergibt/PDB:*filename*|
|/FE*Dateiname*|Übergibt/out:*filename*|
|/FM*Dateiname*|Übergibt/Map:*filename*|
|/Gy|Erstellt Paketfunktionen (COMDATs); aktiviert die Verknüpfung auf Funktionsebene.|
|/LD|Übergibt/dll|
|/LDd|Übergibt/dll|
|/link|Übergibt den Rest der Befehlszeile an den Link.|
|/MD oder/MT|Platziert einen Standard Bibliotheksnamen in der obj-Datei.|
|/MDD oder/MTD|Platziert einen Standard Bibliotheksnamen in der obj-Datei. Definiert das Symbol **_DEBUG**|
|/nologo|Übergibt/nologo|
|/Zd|Übergibt/Debug|
|/Zi oder/Z7|Übergibt/Debug|
|/Zl|Lässt den Standard Bibliotheksnamen aus der obj-Datei aus.|

Weitere Informationen finden Sie unter [MSVC-Compileroptionen](compiler-options.md).

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
