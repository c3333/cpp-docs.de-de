---
title: 'Ressourcencompiler: Schwerwiegender Fehler RC1052'
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: ad0fe23b20870610c5979d6ad85fce55b4e506d3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182555"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Ressourcencompiler: Schwerwiegender Fehler RC1052

Compilerlimit: zu tief geschachtelte #if-oder #ifdef Blöcke

Die maximal zulässige Schachtelungstiefe für `#if`- und `#ifdef`-Anweisungen wird vom Programm überschritten.

Dieser Fehler kann durch Includedateien, die diese Präprozessordirektiven verwenden, verursacht werden.

Um dieses Problem zu beheben, verringern Sie die Anzahl der geschachtelten `#if`- und `#ifdef`-Anweisungen in der Ressourcendatei. Wenn das Problem durch Header-Dateien verursacht wird, die in der Ressourcendatei enthalten sind, verringern Sie die Anzahl der geschachtelten `#if` und `#ifdef`-Anweisungen in den Headerdateien. Wenn dies nicht möglich ist, sollten Sie eine neue Headerdatei in Ihrer Ressourcendatei mit dem Präprozessor auf vorhandenen eingeschlossenen Headerdateien erstellen und einschließen. Weitere Informationen finden Sie in der Compileroption [/P (Vorverarbeitung in eine Datei)](../../build/reference/p-preprocess-to-a-file.md) .
