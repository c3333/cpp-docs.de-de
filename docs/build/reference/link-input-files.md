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
ms.openlocfilehash: aec71d4622821618f377953d36a9676e2233eefc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328201"
---
# <a name="link-input-files"></a>LINK-Eingabedateien

Sie stellen den Linker mit Dateien bereit, die Objekte, Import- und Standardbibliotheken, Ressourcen, Moduldefinitionen und Befehlseingaben enthalten. LINK verwendet keine Dateierweiterungen, um Annahmen über den Inhalt einer Datei zu treffen. Stattdessen untersucht LINK jede Eingabedatei, um zu bestimmen, um welche Art von Datei es sich handelt.

Objektdateien in der Befehlszeile werden in der Reihenfolge verarbeitet, in der sie in der Befehlszeile angezeigt werden. Bibliotheken werden auch in Derbefehlszeilenreihenfolge durchsucht, mit der folgenden Einschränkung: Symbole, die beim Einziehen einer Objektdatei aus einer Bibliothek nicht aufgelöst werden, werden zuerst in dieser Bibliothek und dann in den folgenden Bibliotheken über die Befehlszeile und [/DEFAULTLIB (Standardbibliothek angeben)](defaultlib-specify-default-library.md) Direktiven und dann in allen Bibliotheken am Anfang der Befehlszeile gesucht.

> [!NOTE]
> LINK akzeptiert kein Semikolon (oder ein anderes Zeichen) mehr als Beginn eines Kommentars in Antwortdateien und Bestelldateien. Semikolons werden nur als Beginn von Kommentaren in Moduldefinitionsdateien (.def) erkannt.

LINK verwendet die folgenden Arten von Eingabedateien:

- [.obj-Dateien](dot-obj-files-as-linker-input.md)

- [.netmodule Dateien](netmodule-files-as-linker-input.md)

- [.lib-Dateien](dot-lib-files-as-linker-input.md)

- [.exp Dateien](dot-exp-files-as-linker-input.md)

- [DEF-Dateien](dot-def-files-as-linker-input.md)

- [.pdb Dateien](dot-pdb-files-as-linker-input.md)

- [.res-Dateien](dot-res-files-as-linker-input.md)

- [.exe-Dateien](dot-exe-files-as-linker-input.md)

- [.txt-Dateien](dot-txt-files-as-linker-input.md)

- [.ilk-Dateien](dot-ilk-files-as-linker-input.md)

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)
