---
title: 'NMAKE: Warnung U4011'
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193146"
---
# <a name="nmake-warning-u4011"></a>NMAKE: Warnung U4011

' target ': nicht alle abhängigen Elemente sind verfügbar. Ziel nicht erstellt

Eine Abhängigkeit vom angegebenen Ziel ist entweder nicht vorhanden oder veraltet, und ein Befehl zum Aktualisieren der abhängigen hat einen Exitcode ungleich NULL zurückgegeben. Die/K-Option hat NMAKE angewiesen, die Verarbeitung nicht verknüpftes Teile des Builds fortzusetzen und einen Exitcode 1 auszugeben, wenn die NMAKE-Sitzung abgeschlossen ist.

Dieser Warnung wird eine Warnung vorangestellt [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) für jede abhängige, die nicht erstellt oder aktualisiert werden konnte.
