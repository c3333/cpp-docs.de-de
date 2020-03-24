---
title: 'NMAKE: Schwerwiegender Fehler U1056'
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: 10131e518fa608292fff58672ede36390bcd665b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182902"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE: Schwerwiegender Fehler U1056

Der Befehlsprozessor wurde nicht gefunden.

Der Befehlsprozessor befand sich nicht in dem Pfad, der in den **COMSPEC** -oder **path** -Umgebungsvariablen angegeben ist.

NMAKE verwendet Command.com oder cmd. EXE als Befehlsprozessor beim Ausführen von Befehlen. Er sucht zuerst nach dem Befehlsprozessor in dem Pfad, der in **COMSPEC**festgelegt ist. Wenn **COMSPEC** nicht vorhanden ist, durchsucht NMAKE die unter **path**angegebenen Verzeichnisse.
