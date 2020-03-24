---
title: BSCMAKE-Fehler BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: b272a12e1d729e33794b550c911fd2e56f1af006
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197794"
---
# <a name="bscmake-error-bk1506"></a>BSCMAKE-Fehler BK1506

Datei "Dateiname" kann nicht geöffnet werden [: Reason]

BSCMAKE kann die Datei nicht öffnen.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Die Datei ist von einem anderen Prozess gesperrt. Wenn `reason` besagt, dass die **Berechtigung verweigert**wurde, wird die Datei möglicherweise vom Browser verwendet. Schließen Sie das Fenster durchsuchen, und wiederholen Sie den Build.

1. Ein vollständiger Datenträger.

1. Ein Hardwarefehler.

1. Die angegebene Ausgabedatei hat denselben Namen wie ein vorhandenes Unterverzeichnis.
