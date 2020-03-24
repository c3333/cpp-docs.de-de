---
title: 'NMAKE: Schwerwiegender Fehler U1051'
ms.date: 11/04/2016
f1_keywords:
- U1051
helpviewer_keywords:
- U1051
ms.assetid: fede5cd5-dac3-47b7-b86d-e1acfb78699f
ms.openlocfilehash: 9c6b939c97f993e42049677292374377d825d474
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193679"
---
# <a name="nmake-fatal-error-u1051"></a>NMAKE: Schwerwiegender Fehler U1051

nicht genügend Arbeitsspeicher

NMAKE verfügte nicht über genügend Arbeitsspeicher, einschließlich des virtuellen Speichers, da das Makefile zu groß oder komplex war.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Freigeben von Speicherplatz auf dem Datenträger.

1. Vergrößern Sie die Größe der Windows NT-Auslagerungs Datei oder der Windows-Auslagerungs Datei.

1. Wenn nur ein Teil der Makefile-Datei verwendet wird, teilen Sie das Makefile-Element in separate Dateien auf, oder verwenden Sie **! , Wenn** Vorverarbeitungs Direktiven den Betrag begrenzen müssen, der von NMAKE verarbeitet werden muss. Der **! If** -Direktiven enthalten **! Wenn**, `!IFDEF`, **! Ifndef**, **! Andernfalls wenn**, **! Else** `IFDEF`und **! Andernfalls `IFNDEF`.**
