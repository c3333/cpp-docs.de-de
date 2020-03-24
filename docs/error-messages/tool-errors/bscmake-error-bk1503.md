---
title: BSCMAKE-Fehler BK1503
ms.date: 11/04/2016
f1_keywords:
- BK1503
helpviewer_keywords:
- BK1503
ms.assetid: e6582344-b91e-486f-baf3-4f9028d83c3b
ms.openlocfilehash: e0f05b3979024cb053394c51fa9337197b5de7bf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197859"
---
# <a name="bscmake-error-bk1503"></a>BSCMAKE-Fehler BK1503

in Datei "Dateiname" kann nicht geschrieben werden [: Reason]

BSCMAKE kombiniert die SBR-Dateien, die während der Kompilierung generiert werden, in einer Browser Datenbank. Wenn die resultierende Browser Datenbank 64 MB überschreitet oder wenn die Anzahl der Eingabedateien (. SBR) 4092 überschreitet, wird dieser Fehler ausgegeben.

Wenn das Problem durch mehr als 4092. SBR-Dateien verursacht wird, müssen Sie die Anzahl der Eingabedateien reduzieren. In Visual Studio kann dies durch das [/fr](../../build/reference/fr-fr-create-dot-sbr-file.md) Ihres gesamten Projekts erreicht werden. Anschließend wird eine Datei auf Datei Basis erneut überprüft.

Wenn das Problem durch eine BSC-Datei mit einer Größe von mehr als 64 MB verursacht wird, verringert sich die Anzahl der SBR-Dateien als Eingabe, um die Größe der resultierenden BSC-Datei zu verringern. Außerdem kann die Menge der Browseinformationen durch die Verwendung der/EM (Erweiterte Symbole ausschließen),/El (lokale Variablen ausschließen) und/es (Ausschließen von System Dateien) reduziert werden.

## <a name="see-also"></a>Weitere Informationen

[BSCMAKE-Optionen](../../build/reference/bscmake-options.md)
