---
title: Schwerwiegender Fehler C1049
description: Beschreibt den schwerwiegenden Compilerfehler C1049, ein ungültiges numerisches Argument und erläutert, wie es aufgelöst werden kann.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: 9b3cbe5d081e32680e5408fc4a6ddcd932db77a2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503271"
---
# <a name="fatal-error-c1049"></a>Schwerwiegender Fehler C1049

> Ungültiges numerisches Argument „*value*“.

Der CL.EXE-Befehlszeilen Parser hat einen *Wert* gefunden, in dem ein numerisches Argument erwartet wurde.

Ein C1049-Fehler kann auftreten, wenn der Compiler kein numerisches Argument für eine dieser Compileroptionen finden kann:

[/constexpr: Tiefe](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr: Rückverfolgung](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr: Schritte](../../build/reference/constexpr-control-constexpr-evaluation.md)

Befehlszeilen-Compileroptionen, die ein numerisches Argument erwarten `Command line error D8004` , können auch,, `Command line error D8021` `Command line warning D9002` , oder melden `Command line warning D9014` `Command line warning D9024` .

Um diesen Fehler zu beheben, überprüfen Sie die Befehlszeile auf falsch platzierte oder fehlende Argumente. Stellen Sie sicher, dass keine unerwarteten Leerzeichen zwischen Optionen und Argumenten vorhanden sind. Die letzte Befehlszeile kann von Makros, Umgebungsvariablen oder anderen buildsystemvorgängen generiert werden. Daher ist es wichtig, sich die tatsächliche Befehlszeile anzusehen, die an den Compiler übermittelt wurde.

- In Befehls Dateien oder Makefiles können Sie einen **Echo** -Befehl verwenden, um die tatsächliche Befehlszeile zu melden.

- Öffnen Sie in Visual Studio das Dialogfeld **Eigenschaften Seiten** des Projekts. Ändern Sie auf der Seite **Konfigurations Eigenschaften**  >  **C/C++**  >  **Allgemein** die Eigenschaft **Start Banner unterdrücken** in **Nein**. Klicken Sie auf **OK**, um die Änderungen zu speichern. Das **Ausgabe** Fenster zeigt nun die Befehlszeile an, wenn Sie direkt nach der Copyright Linie erstellen.

Andere Buildsysteme verfügen möglicherweise über Protokolldateien oder ausführliche Optionen, um die tatsächlich verwendeten Befehle anzuzeigen. Weitere Informationen finden Sie in der Dokumentation des Buildsystems.
