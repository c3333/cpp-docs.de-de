---
title: Schwerwiegender Fehler C1382
ms.date: 11/04/2016
f1_keywords:
- C1382
helpviewer_keywords:
- C1382
ms.assetid: 7a100f8c-3179-4927-a2f1-98de4c753850
ms.openlocfilehash: 6ed70a81c4ae2028d09b694f325f83454e99a587
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203098"
---
# <a name="fatal-error-c1382"></a>Schwerwiegender Fehler C1382

die PCH-Datei "file" wurde seit dem Generieren von "obj" neu erstellt. Erstellen Sie dieses Objekt neu.

Bei Verwendung von [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)hat der Compiler eine PCH-Datei erkannt, die neuer als eine cil. obj-Datei ist, die darauf verweist. Die Informationen in der Datei "cil. obj" sind veraltet. Erstellen Sie das-Objekt neu.

C1382 kann auch auftreten, wenn Sie mit **/Yc**kompilieren, aber auch mehrere Quell Code Dateien an den Compiler übergeben.  Verwenden Sie zum Auflösen von nicht **/Yc** , wenn Sie mehrere Quell Code Dateien an den Compiler übergeben.  Weitere Informationen finden Sie unter [/Yc (Vorkompilierte Header Datei erstellen)](../../build/reference/yc-create-precompiled-header-file.md).
