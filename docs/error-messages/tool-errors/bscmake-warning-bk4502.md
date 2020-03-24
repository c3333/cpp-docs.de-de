---
title: BSCMAKE-Warnung BK4502
ms.date: 11/04/2016
f1_keywords:
- BK4502
helpviewer_keywords:
- BK4502
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
ms.openlocfilehash: 1c5204239909e579fa93006e245e3841b7fb64eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197456"
---
# <a name="bscmake-warning-bk4502"></a>BSCMAKE-Warnung BK4502

abgeschnitten. SBR-Datei "Dateiname" nicht im Dateinamen

Eine SBR-Datei der Länge 0 (null), die ursprünglich nicht Teil der BSC-Datei war, wurde während eines Updates angegeben.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Falscher Dateiname angegeben.

1. Die Datei wurde gelöscht. (Fehler [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) Ergebnisse.)

1. Die Datei ist beschädigt, und für einen vollständigen Build ist BSCMAKE erforderlich.
