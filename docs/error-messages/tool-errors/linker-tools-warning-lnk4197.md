---
title: Linkertoolwarnung LNK4197
ms.date: 09/05/2018
f1_keywords:
- LNK4197
helpviewer_keywords:
- LNK4197
ms.assetid: 8a976fd7-a74b-4c83-ab66-a9e7d7073c4a
ms.openlocfilehash: 92702864a00455e4b70f00dfc9988bfb754e2e64
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183279"
---
# <a name="linker-tools-warning-lnk4197"></a>Linkertoolwarnung LNK4197

> Export "Export*Name*" mehrmals angegeben; erste Spezifikation wird verwendet

Ein Export wird auf mehrere verschiedene Arten angegeben. Der Linker verwendet die erste Spezifikation und ignoriert den Rest.

Wenn Sie die C-Lauf Zeit Bibliothek neu erstellen, können Sie diese Meldung ignorieren.

Wenn ein Export genau gleich mehrmals angegeben wird, gibt der Linker keine Warnung aus.

Beispielsweise würde der folgende Inhalt einer DEF-Datei diese Warnung verursachen:

```
EXPORTS
   functioname      NONAME
   functioname      @10
```

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Dieser Fehler kann eine der folgenden Ursachen haben:

1. Derselbe Export wird in der Befehlszeile (durch Export:) angegeben. und in der DEF-Datei.

2. Derselbe Export wird zweimal in der DEF-Datei mit unterschiedlichen Attributen aufgelistet.
