---
title: Befehlszeilenfehler D8016
ms.date: 11/04/2016
f1_keywords:
- D8016
helpviewer_keywords:
- D8016
ms.assetid: eec51312-7471-4f92-94b2-d517cafc8ef5
ms.openlocfilehash: 1bdef16b14488be86aff880db7c049f4bcddcdb5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196962"
---
# <a name="command-line-error-d8016"></a>Befehlszeilenfehler D8016

die Befehlszeilenoptionen "Option1" und "option2" sind nicht kompatibel.

Die Befehlszeilenoptionen können nicht gleichzeitig angegeben werden.

Überprüfen Sie die Umgebungsvariablen (z. b. cl) auf Options Spezifikationen.

**/CLR** impliziert **/EHa**, und Sie können keine andere **/eh** -Compileroption mit **/CLR**angeben. Weitere Informationen finden Sie unter [/clr (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md).

Sie können D8016 nach dem Aktualisieren eines Visual C++ 6,0-Projekts erhalten: der Prozess des Projekt Update-Assistenten aktiviert möglicherweise **/RTC** für jede Quell Code Datei im Projekt, die die **/RTC** -Einstellung für das Projekt überschreibt.  Um das Problem zu beheben, ändern Sie die **/RTC** -Einstellung für jede Quell Code Datei im Projekt in die Standardeinstellung. Dies bedeutet, dass die Projekteinstellung für **/RTC** für jede Datei wirksam ist.

Weitere Informationen zum Ändern der Einstellung der **/RTC** -Eigenschaft finden Sie unter [/RTC (Lauf Zeit Fehlerüberprüfungen)](../../build/reference/rtc-run-time-error-checks.md) .
