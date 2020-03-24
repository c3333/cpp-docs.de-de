---
title: Linkertoolfehler LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195135"
---
# <a name="linker-tools-error-lnk1200"></a>Linkertoolfehler LNK1200

Fehler beim Lesen der Programmdatenbank "Dateiname".

Die Programmdatenbank (PDB) konnte nicht gelesen werden.

Dieser Fehler kann durch eine Beschädigung der Datei verursacht werden.

Wenn `filename` PDB für eine Objektdatei ist, kompilieren Sie die Objektdatei mithilfe von [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)neu.

Wenn `filename` die PDB-Datei für die Haupt Ausgabedatei ist und dieser Fehler während eines inkrementellen Links aufgetreten ist, löschen Sie die PDB, und setzen Sie den Link
