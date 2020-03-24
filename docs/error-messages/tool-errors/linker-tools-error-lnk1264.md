---
title: Linkertoolfehler LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 00041e677ac7b69df9981551ee3b6cc18f9eb33d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183760"
---
# <a name="linker-tools-error-lnk1264"></a>Linkertoolfehler LNK1264

/LTCG: PGINSTRUMENT angegeben, aber es ist keine Codegenerierung erforderlich. Instrumentation fehlgeschlagen

**/LTCG: PGINSTRUMENT** wurde angegeben, aber es wurden keine OBJ-Dateien gefunden, die mit [/GL](../../build/reference/gl-whole-program-optimization.md)kompiliert wurden. Die Instrumentierung kann nicht ausgeführt werden, und der Link ist fehlgeschlagen. Es muss mindestens eine OBJ-Datei in der Befehlszeile vorhanden sein, die mit **/GL** kompiliert wird, damit die Instrumentierung erfolgen kann.

Die Profil gesteuerte Optimierung (PGO) ist nur in 64-Bit-Compilern verfügbar.
