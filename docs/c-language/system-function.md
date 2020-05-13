---
title: Systemfunktion
ms.date: 11/04/2016
helpviewer_keywords:
- system function
ms.assetid: 0786ccdc-20cd-4d96-b3d8-3230507c3066
ms.openlocfilehash: e37de4e084de6727cf2858117945fd162f6b0d63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345122"
---
# <a name="system-function"></a>Systemfunktion

**ANSI 4.10.4.5** Die Inhalte und der Ausführmodus der Zeichenfolge durch die **system**-Funktion

Die **system**-Funktion führt einen internen Betriebssystembefehl oder eine EXE-, COM- (CMD in Windows NT) oder BAT-Datei aus einem C-Programm und nicht aus der Befehlszeile aus.

Die Systemfunktion durchsucht den Befehlsinterpreter, der in der Regel CMD.EXE im Windows NT-Betriebssystem oder COMMAND.COM in Windows ist. Die Systemfunktion gibt die Argumentzeichenfolge anschließend an den Befehlsinterpreter weiter.

Weitere Informationen finden Sie unter [system, _wsystem](../c-runtime-library/reference/system-wsystem.md).

## <a name="see-also"></a>Siehe auch

[Bibliotheksfunktionen](../c-language/library-functions.md)
