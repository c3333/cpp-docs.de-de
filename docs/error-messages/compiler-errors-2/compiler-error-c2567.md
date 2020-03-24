---
title: Compilerfehler C2567
ms.date: 11/04/2016
f1_keywords:
- C2567
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
ms.openlocfilehash: 921992c678c1de0b74f99f544173478ebe809b2c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177455"
---
# <a name="compiler-error-c2567"></a>Compilerfehler C2567

die Metadaten in "file" können nicht geöffnet werden. die Datei wurde möglicherweise gelöscht oder verschoben.

Eine Metadatendatei, auf die in der Quelle (mit `#using`) verwiesen wurde, wurde vom Compiler-Back-End-Prozess nicht im selben Verzeichnis gefunden wie der Compiler-Front-End-Prozess. Weitere Informationen finden Sie unter [#using-Direktive](../../preprocessor/hash-using-directive-cpp.md) .

C2567 kann verursacht werden, wenn Sie eine Kompilierung mit **/c** auf einem Computer durchführen und dann versuchen, eine Link-Zeit Codegenerierung auf einem anderen Computer durchzuführen. Weitere Informationen finden Sie unter [/LTCG (Link-Time Code Generation)](../../build/reference/ltcg-link-time-code-generation.md)).

Es kann auch darauf hindeuten, dass der Computer nicht mehr über genügend Arbeitsspeicher verfügt.

Um diesen Fehler zu beheben, stellen Sie sicher, dass sich die Metadatendatei für alle Phasen des Buildprozesses in demselben Verzeichnis Speicherort befindet.
