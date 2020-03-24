---
title: Linkertoolfehler LNK1140
ms.date: 11/04/2016
f1_keywords:
- LNK1140
helpviewer_keywords:
- LNK1140
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
ms.openlocfilehash: 845c796ee9611e921e2fd1707b9bb956ab62a5ac
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195265"
---
# <a name="linker-tools-error-lnk1140"></a>Linkertoolfehler LNK1140

zu viele Module für die Programmdatenbank; Verknüpfung mit/PDB: None

Das Projekt enthält mehr als 4096 Module.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Relink mithilfe von [/PDB: None](../../build/reference/pdb-use-program-database.md).

1. Kompilieren Sie einige Module ohne Debuginformationen.

1. Reduzieren Sie die Anzahl der Module.
