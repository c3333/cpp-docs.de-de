---
title: 'Ressourcencompiler: Schwerwiegender Fehler RW1025'
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172724"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Ressourcencompiler: Schwerwiegender Fehler RW1025

Nicht genügend Heap Speicher

Überprüfen Sie auf Speicher residente Software, die möglicherweise zu viel Speicherplatz in Anspruch nimmt. Verwenden Sie das CHKDSK-Programm, um herauszufinden, wie viel Arbeitsspeicher Sie besitzen.

Wenn Sie eine umfangreiche Ressourcen Datei erstellen, teilen Sie das Ressourcen Skript in zwei Dateien auf. Nachdem Sie zwei RES-Dateien erstellt haben, verknüpfen Sie Sie mithilfe der MS-DOS-Befehlszeile:

```
copy first.res /b + second.res /b full.res
```
