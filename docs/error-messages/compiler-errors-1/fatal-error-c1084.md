---
title: Schwerwiegender Fehler C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: 649686857000b2bee469f0e3ec551d49717c1d7b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204073"
---
# <a name="fatal-error-c1084"></a>Schwerwiegender Fehler C1084

Lesen der Dateityp-Datei 'Datei' nicht möglich: Meldung

Dieser Fehler ist im Allgemeinen das Ergebnis eines fehlgeschlagenen internen System-API-Aufrufs durch den Compiler. Die Meldung, die angezeigt wird, wenn dieser Fehler auftritt, wird oft entweder von [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) oder von [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage)generiert.

Mit den folgenden Schritten können Sie C1084 möglicherweise beheben:

- Stellen Sie sicher, dass die angegebene Datei existiert.

- Stellen Sie sicher, dass die geeigneten Berechtigungen festgelegt sind, um auf die angegebene Datei zuzugreifen.

- Stellen Sie sicher, dass die Befehlszeilen Syntax den in der [compilerbefehlszeilensyntax](../../build/reference/compiler-command-line-syntax.md)beschriebenen Regeln entspricht.

- Stellen Sie sicher, dass die Umgebungsvariablen " **tmp** " und " **Temp** " ordnungsgemäß festgelegt sind, sowie die entsprechenden Berechtigungen, um auf die Verzeichnisse zuzugreifen, auf die diese Umgebungsvariablen verweisen. Stellen Sie außerdem sicher, dass die Laufwerke, auf die die Umgebungsvariablen " **tmp** " und " **Temp** " verweisen, ausreichend freien Speicherplatz enthalten.

- Wenn die Meldung „Ungültige Dateinummer“ enthält, wurde die angegebene Datei möglicherweise im Vordergrund geschlossen, während sie im Hintergrund kompiliert wurde.

Führen Sie nach der Durchführung der obigen Diagnose einen bereinigten Build aus.
