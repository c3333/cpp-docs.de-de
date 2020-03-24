---
title: Schwerwiegender Fehler C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 6ad00eb3d95e9f09d4f84daefb7e2a87fd1a3abf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203358"
---
# <a name="fatal-error-c1305"></a>Schwerwiegender Fehler C1305

Die Profildatenbank 'PDG-Datei' wird für eine andere Architektur verwendet.

Eine PGD-Datei, die aus dem/LTCG: PGINSTRUMENT-Vorgang für eine andere Plattform generiert wurde, wurde an [/LTCG: pgoptimiert](../../build/reference/ltcg-link-time-code-generation.md) übergeben. [Profil gesteuerte Optimierungen](../../build/profile-guided-optimizations.md) sind für x86-und x64-Plattformen verfügbar. Eine mit einer /LTCG:PGINSTRUMENT-Operation für eine bestimmte Plattform erzeugte PGD-Datei ist jedoch ungültig als Eingabe für eine /LTCG:PGOPTIMIZE-Operation für eine andere Plattform.

Um diesen Fehler zu beheben, geben Sie eine mit /LTCG:PGINSTRUMENT erstellte PGD-Datei nur an /LTCG:PGOPTIMIZE für dieselbe Plattform weiter.
