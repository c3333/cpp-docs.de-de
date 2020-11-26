---
title: Anpassen der C-Befehlszeilenverarbeitung
description: Unterdrücken von `main`-Funktionsargumenten und Behandlung von Umgebungsparametern im Runtimestartcode.
ms.date: 11/19/2020
helpviewer_keywords:
- _spawn functions
- command line, processing
- command-line processing
- startup code, customizing command-line processing
- environment, environment-processing routine
- _setargv function
- command line, processing arguments
- suppressing environment processing
- _exec function
ms.openlocfilehash: fc306172491cd401caeecb3c87c0711f8b4ef911
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483294"
---
# <a name="customizing-c-command-line-processing"></a>Anpassen der C-Befehlszeilenverarbeitung

Wenn das Programm keine Befehlszeilenargumente akzeptiert, können Sie die Routine zur Befehlszeilenverarbeitung unterdrücken, um ein wenig Speicherplatz zu sparen. Um ihre Verwendung zu unterdrücken, schließen Sie die *`noarg.obj`* -Datei (sowohl für `main` als auch für `wmain`) in Ihre **`/link`** -Compileroptionen oder **`LINK`** -Befehlszeile ein.

Ebenso können Sie die interne Routine zur Umgebungsverarbeitung unterdrücken, wenn Sie nie über das *`envp`* -Argument auf die Umgebungstabelle zugreifen. Um ihre Verwendung zu unterdrücken, schließen Sie die *`noenv.obj`* -Datei (sowohl für `main` als auch für `wmain`) in Ihre **`/link`** -Compileroptionen oder **`LINK`** -Befehlszeile ein.

Weitere Informationen zu den Optionen für den Runtimestartlinker finden Sie unter [Linkoptionen](../c-runtime-library/link-options.md).

Das Programm ruft möglicherweise die `spawn`- oder `exec`-Gruppe von Routinen in der C-Laufzeitbibliothek auf. Wenn dies der Fall ist, sollten Sie die Routine zur Umgebungsverarbeitung nicht unterdrücken, da diese Routine verwendet wird, um eine Umgebung aus dem übergeordneten Prozess an den untergeordneten Prozess zu übergeben.

## <a name="see-also"></a>Weitere Informationen

[`main`-Funktion und Programmausführung](../c-language/main-function-and-program-execution.md)\
[Linkoptionen](../c-runtime-library/link-options.md).
