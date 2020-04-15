---
title: LIB-Eingabedateien
ms.date: 11/04/2016
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: de81f79eecf3fc73c02894747f4b97cb107cf892
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328232"
---
# <a name="lib-input-files"></a>LIB-Eingabedateien

Die von LIB erwarteten Eingabedateien hängen vom Modus ab, in dem sie verwendet werden, wie in der folgenden Tabelle dargestellt.

|Mode|Eingabe|
|----------|-----------|
|Standard (Erstellen oder Ändern einer Bibliothek)|COFF-Objektdateien (.obj), COFF-Bibliotheken (.lib), OMF-Objektdateien (.obj) (.obj)|
|Extrahieren eines Elements mit /EXTRACT|COFF-Bibliothek (.lib)|
|Erstellen einer Exportdatei und Importbibliothek mit /DEF|Modul-Definition (.def) Datei, COFF-Objekt (.obj) Dateien, COFF-Bibliotheken (.lib), 32-Bit-OMF-Objekt (.obj) Dateien|

> [!NOTE]
> OMF-Bibliotheken, die von der 16-Bit-Version von LIB erstellt wurden, können nicht als Eingabe für die 32-Bit-Version von LIB verwendet werden.

## <a name="see-also"></a>Siehe auch

[Übersicht über LIB](overview-of-lib.md)
