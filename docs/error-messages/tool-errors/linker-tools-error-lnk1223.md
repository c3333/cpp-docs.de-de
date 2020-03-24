---
title: Linkertoolfehler LNK1223
ms.date: 11/04/2016
f1_keywords:
- LNK1223
helpviewer_keywords:
- LNK1223
ms.assetid: c4728c36-daee-462f-a1c7-8733dcdec88e
ms.openlocfilehash: 9c9d4c7224a7e65775354a86bd34fa9ea1b074af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195031"
---
# <a name="linker-tools-error-lnk1223"></a>Linkertoolfehler LNK1223

Ungültige oder beschädigte Datei: Datei enthält unzulässige .pdata-Beiträge

Bei RISC-Plattformen, die Pdata verwenden, wird dieser Fehler auftreten, wenn der Compiler einen .pdata-Abschnitt mit unsortierten Einträgen ausgegeben hat.

Um dieses Problem zu beheben, kompilieren Sie die Kompilierung ohne [/GL (gesamte Programm Optimierung)](../../error-messages/tool-errors/linker-tools-error-lnk1223.md) . Leere Funktionsbodys können in einigen Fällen diesen Fehler auch verursacht.
