---
title: Schwerwiegender Fehler C1352
ms.date: 11/04/2016
f1_keywords:
- C1352
helpviewer_keywords:
- C1352
ms.assetid: d044e8b0-b6ef-4d57-8eb5-6254071be707
ms.openlocfilehash: 07bd0f28e35dd2992ca537dbe744d756cc2afe80
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203124"
---
# <a name="fatal-error-c1352"></a>Schwerwiegender Fehler C1352

Ungültige oder beschädigte MSIL in "Funkion"-Funktion aus Modul "Datei".

Eine NETMODULE-Datei wurde an den Compiler übergeben, aber der Compiler hat eine Beschädigung in der Datei erkannt.  Bitten Sie die Person, die die NETMODULE-Datei erstellt hat, diese zu überprüfen.

Der Compiler überprüft NETMODULE-Dateien nicht auf alle Arten von Beschädigung.  Er prüft jedoch, ob alle Steuerelementpfade in einer Funktion eine return-Anweisung enthalten.

Weitere Informationen finden Sie unter [NETMODULE-Dateien als Eingabe für den Linker](../../build/reference/netmodule-files-as-linker-input.md).
