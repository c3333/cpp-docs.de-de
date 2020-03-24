---
title: Schwerwiegender Fehler C1902
ms.date: 11/04/2016
f1_keywords:
- C1902
helpviewer_keywords:
- C1902
ms.assetid: 2dc066cc-fcb1-4725-8bcb-9f44dd0905b7
ms.openlocfilehash: 10a411dfc942498a98959d9a23cb42dfb93cf2ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202825"
---
# <a name="fatal-error-c1902"></a>Schwerwiegender Fehler C1902

nicht übereinstimmender Programmdatenbank-Manager. Überprüfen Sie die Installation.

Eine Programm Datenbankdatei (. pdb) wurde mit einer neueren Version von Mspdb*xxx*. dll erstellt, als die, die der Compiler auf Ihrem System gefunden hat. Dieser Fehler weist normalerweise darauf hin, dass "mspdbsrv. exe" oder "mspdbcore. dll" fehlen oder andere Versionen als "Mspdb*xxx*. dll" aufweisen. (Der *xxx* -Platzhalter in der Datei "Mspdb*xxx*. dll" ändert sich bei jeder Produktversion. In Visual Studio 2015 lautet der Dateiname beispielsweise Version von mspdb140. dll.)

Stellen Sie sicher, dass die Versionen von "mspdbsrv. exe", "mspdbcore. dll" und "Mspdb*xxx*. dll" auf dem System installiert sind. Stellen Sie sicher, dass nicht übereinstimmende Versionen nicht in das Verzeichnis kopiert wurden, das die Compilertools und Verknüpfungs Tools für Ihre Zielplattform enthält. Beispielsweise können Sie die Dateien kopiert haben, damit Sie das Compiler-oder Link Tool über die Eingabeaufforderung aufrufen können, ohne die Umgebungsvariable **path** entsprechend festzulegen.
