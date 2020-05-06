---
title: Erweitern von Platzhalterargumenten
ms.date: 11/04/2016
helpviewer_keywords:
- asterisk wildcard
- question mark, wildcard
- expanding wildcard arguments
- wildcards, expanding
ms.assetid: 80a11c4b-0199-420e-a342-cf1d803be5bc
ms.openlocfilehash: f1fb964fe98223fb7187b83c7101027ed1f9cbea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62233808"
---
# <a name="expanding-wildcard-arguments"></a>Erweitern von Platzhalterargumenten

**Microsoft-spezifisch**

Wenn Sie ein C-Programm ausführen, können Sie einen von zwei Platzhaltern – das Fragezeichen (?) und das Sternchen (*) – verwenden, um Dateinamen- und Pfadargumente in der Befehlszeile anzugeben.

Standardmäßig werden Platzhalter in Befehlszeilenargumenten nicht erweitert. Sie können den die normale `argv` -Laderoutine für den Argumentvektor durch eine Version ersetzen, die Platzhalter durch eine Verknüpfung mit der Datei „setargv.obj“ oder der Datei „wsetargv.obj“ erweitert. Wenn das Programm eine `main` -Funktion verwendet, stellen Sie eine Verknüpfung mit „setargv.obj“ her. Wenn das Programm eine `wmain` -Funktion verwendet, stellen Sie eine Verknüpfung mit „wsetargv.obj“ her. Beide weisen das gleiche Verhalten auf.

Um eine Verknüpfung mit „setargv.obj“ oder „wsetargv.obj“ herzustellen, verwenden Sie die **/link** -Option. Zum Beispiel:

**cl example.c /link setargv.obj**

Die Platzhalter werden auf dieselbe Weise wie Betriebssystembefehle erweitert. (Weitere Informationen erhalten Sie im Benutzerhandbuch des Betriebssystems, wenn Sie mit Platzhaltern nicht vertraut sind.)

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Linkoptionen](../c-runtime-library/link-options.md)<br/>
[main-Funktion und Programmausführung](../c-language/main-function-and-program-execution.md)
