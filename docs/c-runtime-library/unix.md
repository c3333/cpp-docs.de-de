---
title: UNIX
description: Richtlinien zum Portieren Ihres Programms auf UNIX.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: 07f5ffeec8696ded5880c45ed2ea1a5107bee48c
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590146"
---
# <a name="unix"></a>UNIX

Wenn Sie Ihre Programme nach UNIX portieren möchten, befolgen Sie folgende Richtlinien:

- Entfernen Sie keine Header Dateien aus dem sys-Unterverzeichnis. Sie können die sys-Header Dateien nur an eine andere Stelle platzieren, wenn Sie nicht beabsichtigen, ihre Programme nach UNIX zu transportieren.

- Verwenden Sie die UNIX-kompatiblen Pfadtrennzeichen in Routinen, die Zeichenfolgen für Pfade und Dateinamen als Argumente annehmen. UNIX unterstützt für diesen Zweck nur den Schrägstrich (/), Win32-Betriebssysteme unterstützen jedoch sowohl den umgekehrten Schrägstrich ( \\ ) als auch den Schrägstrich (/). Diese Dokumentation verwendet UNIX-kompatible Schrägstriche als Pfad Trennzeichen in- `#include` Anweisungen, z. b.. (Die Befehlsshell des Windows-Betriebssystems (CMD.EXE) unterstützt jedoch nicht den Schrägstrich in Befehlen, die an der Eingabeaufforderung eingegeben werden.)

- Verwenden Sie Pfade und Dateinamen, die in UNIX ordnungsgemäß funktionieren, wobei die Groß-/Kleinschreibung beachtet wird. Beim FAT-Dateisystem (File Allocation Table) in Win32-Betriebssystemen wird die Groß-/Kleinschreibung nicht beachtet. Das NTFS-Dateisystem behält die Groß-/Kleinschreibung für Verzeichnis Auflistungen bei

> [!NOTE]
>  In dieser Version von Visual C++ wurden UNIX-Kompatibilitätsinformationen aus den Beschreibungen der Funktionen entfernt.

## <a name="see-also"></a>Weitere Informationen

[Kompatibilität](../c-runtime-library/compatibility.md)
