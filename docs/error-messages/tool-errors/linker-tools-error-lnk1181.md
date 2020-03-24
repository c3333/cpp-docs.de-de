---
title: Linkertoolfehler LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: d2b28af52a2ca2263a7bad77c8c69242396ff2b4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195252"
---
# <a name="linker-tools-error-lnk1181"></a>Linkertoolfehler LNK1181

Eingabedatei "Dateiname" kann nicht geöffnet werden.

Der Linker konnte `filename` nicht finden, weil er nicht vorhanden ist oder der Pfad nicht gefunden wurde.

Einige häufige Fehlerursache LNK1181 sind:

- auf `filename` wird als zusätzliche Abhängigkeit von der Linker-Zeile verwiesen, die Datei ist jedoch nicht vorhanden.

- Eine **/LIBPATH** -Anweisung, die das Verzeichnis angibt, das `filename` enthält.

Stellen Sie sicher, dass alle Dateien, auf die in der Linker-Zeile verwiesen wird, auf dem System vorhanden sind  Stellen Sie außerdem sicher, dass eine **/LIBPATH** -Anweisung für jedes Verzeichnis vorhanden ist, das eine Linker-abhängige Datei enthält.

Weitere Informationen finden Sie unter [lib-Dateien als Eingabe](../../build/reference/dot-lib-files-as-linker-input.md)für den Linker.

Eine weitere mögliche Ursache für LNK1181 besteht darin, dass ein langer Dateiname mit eingebetteten Leerzeichen nicht in Anführungszeichen eingeschlossen ist.  In diesem Fall erkennt der Linker nur einen Dateinamen bis zum ersten Leerzeichen und übernimmt dann die Dateierweiterung ". obj".  Die Lösung für diese Situation besteht darin, den langen Dateinamen (Pfad und Dateiname) in Anführungszeichen einzuschließen.

Das Kompilieren mit der/P-Option [(Vorverarbeitung in eine Datei)](../../build/reference/p-preprocess-to-a-file.md) kann zu LNK1181 führen, da diese Option die Erstellung von obj-Dateien unterdrückt.

## <a name="see-also"></a>Weitere Informationen

[/LIBPATH (Zusätzlicher Libpath-Pfad)](../../build/reference/libpath-additional-libpath.md)
