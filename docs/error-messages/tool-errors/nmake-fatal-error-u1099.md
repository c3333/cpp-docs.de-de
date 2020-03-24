---
title: 'NMAKE: Schwerwiegender Fehler U1099'
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: c963180059a48d9aa0b09103df1ed54f82b8a2f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193393"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE: Schwerwiegender Fehler U1099

Stapelüberlauf

Das verarbeitete Makefile war für die aktuelle Stapel Zuordnung in NMAKE zu komplex. NMAKE hat eine Zuordnung von 0x3000 (12K).

Um die Stapel Zuordnung von NMAKE zu erhöhen, führen Sie das Hilfsprogramm [(EDITBIN/Stack](../../build/reference/stack.md) mit einer größeren Stapel Option aus:

**(EDITBIN/Stack: Reserve NMAKE. Speichert**

Where *Reserve* ist eine Zahl, die größer als die aktuelle Stapel Zuordnung in NMAKE ist.
