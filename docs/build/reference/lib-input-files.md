---
title: LIB-Eingabedateien
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 209ba04ea43116b39f28b0790b7a1e2b3fb5ccd7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439449"
---
# <a name="lib-input-files"></a>LIB-Eingabedateien

Welche Eingabedateien von lib erwartet werden, hängt vom Modus ab, in dem Sie verwendet wird, wie in der folgenden Tabelle dargestellt.

|Mode|Eingabe|
|----------|-----------|
|Standard (aufbauen oder Ändern einer Bibliothek)|COFF-Objektdateien (OBJ-Dateien), COFF-Bibliotheken (. lib), 32-Bit-Objektmodell Format (obj)-Dateien|
|Extrahieren eines Members mit/Extract|COFF-Bibliothek (. lib)|
|Entwickeln einer Exportdatei und Importieren einer Bibliothek mit/DEF|Modul Definitionsdatei (. def), COFF-Objektdateien (OBJ-Dateien), COFF-Bibliotheken (. lib), 32-Bit-OMF-Objektdateien (obj)|

> [!NOTE]
>  OMF-Bibliotheken, die von der 16-Bit-Version von LIB erstellt wurden, können nicht als Eingabe für die 32-Bit-Version von lib verwendet werden.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über LIB](overview-of-lib.md)
