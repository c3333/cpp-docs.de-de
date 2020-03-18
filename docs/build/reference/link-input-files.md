---
title: LINK-Eingabedateien
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], LINK
- module definition files
- resources [C++], linker files
- LINK tool [C++], input files
- module definition files, linker files
- input files [C++], LINK
- linker [C++], input files
- import libraries [C++], linker files
- command input to linker files [C++]
ms.assetid: bb26fcc5-509a-4620-bc3e-b6c6e603a412
ms.openlocfilehash: 25d8e20903a97186e2c32a079fd74ece3626b7fa
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439342"
---
# <a name="link-input-files"></a>LINK-Eingabedateien

Sie stellen dem Linker Dateien bereit, die Objekte, Import-und Standardbibliotheken, Ressourcen, Modul Definitionen und Befehlseingaben enthalten. Der Link verwendet keine Dateierweiterungen, um Annahmen über den Inhalt einer Datei zu treffen. Stattdessen prüft Link jede Eingabedatei, um zu bestimmen, welche Art von Datei Sie ist.

Objektdateien in der Befehlszeile werden in der Reihenfolge verarbeitet, in der Sie in der Befehlszeile angezeigt werden. Bibliotheken werden in der Befehlszeilen Reihenfolge ebenfalls durchsucht, wobei die folgenden Einschränkungen vorliegen: Symbole, die beim Einbinden einer Objektdatei aus einer Bibliothek nicht aufgelöst werden, werden zuerst in dieser Bibliothek gesucht, und dann die folgenden Bibliotheken aus den Befehlszeilen-und/DEFAULTLIB-Direktiven [(Standardbibliothek angeben)](defaultlib-specify-default-library.md) und dann an alle Bibliotheken am Anfang der Befehlszeile.

> [!NOTE]
>  Der Link akzeptiert nicht mehr ein Semikolon (oder ein anderes Zeichen) als Anfang eines Kommentars in Antwort Dateien und Bestell Dateien. Semikolons werden nur als Anfang von Kommentaren in Modul Definitions Dateien (. def) erkannt.

Link verwendet die folgenden Typen von Eingabedateien:

- [. obj-Dateien](dot-obj-files-as-linker-input.md)

- [NETMODULE-Dateien](netmodule-files-as-linker-input.md)

- [lib-Dateien](dot-lib-files-as-linker-input.md)

- [EXP-Dateien](dot-exp-files-as-linker-input.md)

- [DEF-Dateien](dot-def-files-as-linker-input.md)

- [PDB-Dateien](dot-pdb-files-as-linker-input.md)

- [res-Dateien](dot-res-files-as-linker-input.md)

- [exe-Dateien](dot-exe-files-as-linker-input.md)

- [txt-Dateien](dot-txt-files-as-linker-input.md)

- [. ILK-Dateien](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
