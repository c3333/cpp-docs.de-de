---
title: 'NMAKE: Schwerwiegender Fehler U1100'
description: 'Eine Beschreibung der Ursache von Microsoft NMAKE: Schwerwiegender Fehler U1100.'
ms.date: 07/17/2020
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: f908514469a6c9fdb53df3b2bded1b30bddc5a41
ms.sourcegitcommit: 00af3df3331854b23693ee844e5e7c10c8b05a90
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/20/2020
ms.locfileid: "86491387"
---
# <a name="nmake-fatal-error-u1100"></a>NMAKE: Schwerwiegender Fehler U1100

> das Makro "*Makro Name*" ist im Kontext der Batch Regel "*rule-Name*" unzulässig.

NMAKE generiert diesen Fehler, wenn der Befehls Block einer Batch Modus-Regel direkt oder indirekt auf ein spezielles Datei Makro verweist, das nicht ist `$<` .

`$<`ist das einzige zulässige Makro für Regeln im Batch Modus.

Weitere Informationen zu NMAKE-Makros in Batch Regeln finden Sie unter [besondere NMAKE-Makros](../../build/reference/special-nmake-macros.md).
