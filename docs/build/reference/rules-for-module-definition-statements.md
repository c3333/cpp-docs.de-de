---
title: Regeln für Moduldefinitionsanweisungen
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: f6269ad2d5bf3952e485f2ca5e5d1f411c5f1e0c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318510"
---
# <a name="rules-for-module-definition-statements"></a>Regeln für Moduldefinitionsanweisungen

Die folgenden Syntaxregeln gelten für alle Anweisungen in einer DEF-Datei. Andere Regeln, die für bestimmte Anweisungen gelten, werden mit jeder Anweisung beschrieben.

- Anweisungen, Attribut-Schlüsselwörter und Benutzer angegebenen Bezeichner werden Groß-/Kleinschreibung beachtet.

- Lange Dateinamen mit Leerzeichen oder ein Semikolon (;) muss in Anführungszeichen (") eingeschlossen werden.

- Verwenden Sie eine oder mehrere Leerzeichen, Tabstopps oder neue Zeilenumbruchzeichen, um ein Anweisungsschlüsselwort von den Argumenten zu trennen und Anweisungen voneinander zu trennen. Ein Doppelpunkt (:)) oder Gleichheitszeichen (=), der kennzeichnet ein Argument von 0 (null) oder mehr Leerzeichen, Tabulatoren oder Zeilenvorschubzeichen umgeben ist.

- Ein **Namen** oder **Bibliothek** Anweisungen, wenn verwendet, müssen vor stehen alle anderen Anweisungen.

- Die **Abschnitte** und **EXPORTE** Anweisungen können mehr als einmal in der DEF-Datei angezeigt. Jede Anweisung dauert mehrere Spezifikationen, die durch eine oder mehrere Leerzeichen, Tabstopps oder neue Zeilenumbruchzeichen getrennt werden müssen. Das Anweisungsschlüsselwort muss vor der ersten Spezifikation einmal angezeigt werden und vor jeder zusätzliche Spezifikation wiederholt werden kann.

- Mehrere Anweisungen haben eine entsprechende Verknüpfung-Befehlszeilenoption. Die Beschreibung der entsprechenden LINK-Option für Weitere Informationen finden Sie.

- Kommentare in der DEF-Datei festgelegt werden, durch ein Semikolon (;) am Anfang jeder Kommentarzeile. Ein Kommentar kann nicht dieselbe Leitung mit einer Anweisung, aber sie können zwischen Spezifikationen in einer mehrzeiligen Anweisung angezeigt werden. (**Abschnitte** und **EXPORTE** mehrzeilige Anweisungen sind.)

- Numerische Argumente werden in der Basis 10 angegeben oder im Hexadezimalformat.

- Wenn ein Argument entspricht einer [reserviertes Wort](reserved-words.md), muss er in doppelte Anführungszeichen (") gesetzt werden.

## <a name="see-also"></a>Siehe auch

[Moduldefinitionsdateien (.Def)](module-definition-dot-def-files.md)
