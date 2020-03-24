---
title: Linkertoolfehler LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 8d02743333c02c7cdff3b75e4a16bfecda442fa9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195109"
---
# <a name="linker-tools-error-lnk1201"></a>Linkertoolfehler LNK1201

Fehler beim Schreiben in die Programmdatenbank "Dateiname". auf unzureichenden Speicherplatz, ungültigen Pfad oder unzureichende Berechtigungen überprüfen

Der Link konnte nicht in die Programmdatenbank (PDB) für die Ausgabedatei schreiben.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Die Datei ist beschädigt. Löschen Sie die PDB-Datei, und verknüpfen Sie Sie neu.

1. Nicht genügend Speicherplatz zum Schreiben der Datei.

1. Das Laufwerk ist möglicherweise aufgrund eines Netzwerk Problems nicht verfügbar.

1. Der Debugger ist auf dem Programm aktiv, das Sie verknüpfen möchten.

1. Nicht genügend Heap Speicher.  Weitere Informationen finden Sie unter [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) .
