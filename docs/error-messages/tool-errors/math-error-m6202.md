---
title: Mathematischer Fehler M6202
ms.date: 11/04/2016
f1_keywords:
- M6202
helpviewer_keywords:
- M6202
ms.assetid: 4d17045f-c6dc-4705-9512-e9af12c35fb4
ms.openlocfilehash: b8a3a4ab87a410c4cee8f7e4a1a0517c169d0364
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173659"
---
# <a name="math-error-m6202"></a>Mathematischer Fehler M6202

"Function": _SING Fehler

Ein Argument für die angegebene Funktion war ein Singular Wert für diese Funktion. Die-Funktion ist für dieses Argument nicht definiert.

Dieser Fehler Ruft die `_matherr`-Funktion mit dem Funktionsnamen, den Argumenten und dem Fehlertyp auf. Sie können die `_matherr`-Funktion umschreiben, um die Behandlung bestimmter Fehler in der Lauf Zeit-Gleit Komma Zeit anzupassen.
