---
title: Linkertoolfehler LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 7c00fb32e4b36eff119195efbb34d536d80df6a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183656"
---
# <a name="linker-tools-error-lnk1277"></a>Linkertoolfehler LNK1277

Objektdaten Satz wurde in PGD (Dateiname) nicht gefunden.

Bei Verwendung von " [/LTCG: PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md)" unterscheidet sich der Pfad einer der Eingaben "Input. lib", "Def" oder ". obj" von dem Pfad, in dem Sie während "/LTCG: PGINSTRUMENT" gefunden wurden. Dies kann durch eine Änderung in der LIB-Umgebungsvariablen nach/LTCG: PGINSTRUMENT erläutert werden. Der vollständige Pfad zu den Eingabedateien wird in der PGD-Datei gespeichert.

/LTCG: pgoptimiert erfordert, dass die Eingaben mit der/LTCG: PGINSTRUMENT-Phase identisch sind.

Um diese Warnung zu beheben, führen Sie einen der folgenden Schritte aus:

- Führen Sie/LTCG: PGINSTRUMENT aus, wiederholen Sie alle Testläufe, und führen Sie/LTCG: pgoptimiert aus.

- Ändern Sie die lib-Umgebungsvariable in das, was Sie beim Ausführen von/LTCG: PGINSTRUMENT war.

Es wird nicht empfohlen, Linkertoolfehler LNK1277 mit/LTCG: PGUPDATE zu umgehen.
