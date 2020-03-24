---
title: BSCMAKE-Warnung BK4504
ms.date: 11/04/2016
f1_keywords:
- BK4504
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
ms.openlocfilehash: 57858827439ac8cc11e3718d7a484124ae8a6d74
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197443"
---
# <a name="bscmake-warning-bk4504"></a>BSCMAKE-Warnung BK4504

die Datei enthält zu viele Verweise. Weitere Verweise aus dieser Quelle werden ignoriert.

Die CPP-Datei enthält mehr als 64.000 Symbol Verweise. Wenn in BSCMAKE 64.000 Verweise in einer Datei gefunden wurden, werden alle weiteren Verweise ignoriert.

Um das Problem zu beheben, teilen Sie die Datei entweder in zwei oder mehr Dateien auf, die jeweils weniger als 64.000 Symbol Verweise enthalten, oder verwenden Sie die `#pragma component(browser)` Präprozessordirektive, um Symbole einzuschränken, die für bestimmte Verweise generiert werden. Weitere Informationen finden Sie unter [Component](../../preprocessor/component.md).
