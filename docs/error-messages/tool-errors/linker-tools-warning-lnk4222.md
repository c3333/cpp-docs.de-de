---
title: Linkertoolwarnung LNK4222
ms.date: 11/04/2016
f1_keywords:
- LNK4222
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
ms.openlocfilehash: f74379861ad04142fd78a8e307af165072c9cadd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183032"
---
# <a name="linker-tools-warning-lnk4222"></a>Linkertoolwarnung LNK4222

dem exportierten Symbol ' Symbol ' sollte keine Ordinalzahl zugewiesen werden.

Die folgenden Symbole dürfen nicht nach Ordnungszahl exportiert werden:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllUnregisterServer`

Diese Funktionen befinden sich immer mithilfe `GetProcAddress`. Der Linker warnt über diese Art von Export, weil er zu einem größeren Bild führen könnte. Dies kann vorkommen, wenn der Bereich ihrer ordinalen Exporte mit relativ wenigen Exporten groß ist. Beispiel:

```
EXPORTS
   DllGetClassObject   @1
   MyOtherAPI      @100
```

erfordert 100-Slots in der Export Adress Tabelle mit 98 von Ihnen (2-99) nur "Filler". Andererseits

```
EXPORTS
   DllGetClassObject
   MyOtherAPI      @100
```

erfordert zwei Slots. (Beachten Sie, dass Sie auch mit der Option [/Export](../../build/reference/export-exports-a-function.md) Linker exportieren können.)
