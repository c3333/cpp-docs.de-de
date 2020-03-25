---
title: Schwerwiegender Fehler C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 76492be7abab6deb740f1670b85274b8c296c783
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203891"
---
# <a name="fatal-error-c1091"></a>Schwerwiegender Fehler C1091

Compilerlimit: Die Zeichenfolge überschreitet die Länge um "Länge" Bytes.

Eine Zeichenfolgekonstante hat die aktuelle Grenze für die Länge von Zeichenfolgen überschritten.

Teilen Sie ggf. die statische Zeichenfolge in zwei (oder mehr) Variablen auf und verwenden Sie [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) , um das Ergebnis im Rahmen der Deklaration oder während der Laufzeit zusammenzuführen.
