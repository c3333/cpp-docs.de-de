---
title: 'NMAKE: Schwerwiegender Fehler U1095'
ms.date: 11/04/2016
f1_keywords:
- U1095
helpviewer_keywords:
- U1095
ms.assetid: a392582b-06db-4568-9c13-450293a4fbda
ms.openlocfilehash: 55c7ca7d237655b7e20406e7f28e5b2471bdec53
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193458"
---
# <a name="nmake-fatal-error-u1095"></a>NMAKE: Schwerwiegender Fehler U1095

die Erweiterte Befehlszeile "CommandLine" ist zu lang.

Nach der Makro Erweiterung hat die angegebene Befehlszeile den Grenzwert für die Länge der Befehlszeilen für das Betriebssystem überschritten.

MS-DOS lässt bis zu 128 Zeichen in einer Befehlszeile zu.

Wenn der Befehl für ein Programm gilt, das Befehlszeilen Eingaben aus einer Datei akzeptieren kann, ändern Sie den Befehl, und geben Sie Eingaben entweder aus einer Datei auf einem Datenträger oder aus einer Inline Datei an. Link und lib akzeptieren z. b. Eingaben aus einer Antwortdatei.
