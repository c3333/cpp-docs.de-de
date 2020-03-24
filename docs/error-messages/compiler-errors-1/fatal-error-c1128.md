---
title: Schwerwiegender Fehler C1128
ms.date: 11/04/2016
f1_keywords:
- C1128
helpviewer_keywords:
- C1128
ms.assetid: 6f9580fd-ecef-48be-9780-dcf666704279
ms.openlocfilehash: 64671c9abe8ed1375df1e91ca7509e6a597366ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203634"
---
# <a name="fatal-error-c1128"></a>Schwerwiegender Fehler C1128

Anzahl der Abschnitte überschreitet Objektdateiformatgrenze: Kompilieren mit /bigobj

Eine OBJ-Datei hat die Anzahl der zulässigen Abschnitte überschritten. Hierbei handelt es sich um eine Formatbeschränkung für COFF-Objektdateien.

Das Erreichen dieser Abschnitts Einschränkung kann das Ergebnis der Verwendung von [/Gy](../../build/reference/gy-enable-function-level-linking.md) und eines Debugbuilds sein. **/Gy** bewirkt, dass Funktionen in Ihre eigenen COMDAT-Abschnitte gelangen. Ein Debugbuild enthält für jede COMDAT-Funktion einen Abschnitt mit Debuginformationen.

C1128 kann auch durch die Verwendung zu vieler Inlinefunktionen verursacht werden.

Um diesen Fehler zu beheben, teilen Sie die Quelldatei in mehrere Quell Code Dateien, kompilieren Sie ohne **/Gy**, oder kompilieren Sie mit [/bigobj (erhöhen Sie die Anzahl der Abschnitte in. Obj-Datei)](../../build/reference/bigobj-increase-number-of-sections-in-dot-obj-file.md).  Wenn Sie nicht mit **/Gy**kompilieren, müssen Sie die Optimierungen einzeln angeben, da **/O2** und **/O1** beide **/Gy**implizieren.

Kompilieren Sie nach Möglichkeit ohne Debuginformationen.

Möglicherweise benötigen Sie außerdem spezifische Vorlageninstanziierungen in separaten Quellcodedateien, anstatt sie vom Compiler ausgeben zu lassen.

Beim Portieren von Code wird C1128 wahrscheinlich zuerst angezeigt, wenn der x64-Compiler verwendet wird, und vieles später mit dem x86-Compiler. x64 enthält mindestens vier Abschnitte, die jeder von Ihnen kompilierten **/Gy** zugeordnet sind, oder Inline aus Vorlagen oder Klassen Inline: Code, pData und Debuginformationen und möglicherweise XData.  Bei X86 ist der pdata-Abschnitt nicht vorhanden.
