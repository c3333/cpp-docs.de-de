---
title: Linkertoolwarnung LNK4105
ms.date: 11/04/2016
f1_keywords:
- LNK4105
helpviewer_keywords:
- LNK4105
ms.assetid: 6c7bebf4-4ea6-4533-a6ed-e563d43abbd7
ms.openlocfilehash: 655a6dfde77984cd0c941ec0d8abb0c4d099c80f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183292"
---
# <a name="linker-tools-warning-lnk4105"></a>Linkertoolwarnung LNK4105

Es wurde kein Argument mit der Option "Option" angegeben. ignorierende Option

Diese Warnung tritt nur dann auf, wenn die [/LIBPATH](../../build/reference/libpath-additional-libpath.md) -Option festgelegt ist. Wenn mit dieser Option kein Verzeichnis angegeben wird, ignoriert der Linker die Option und generiert diese Warnmeldung.

Wenn Sie die vorhandenen Umgebungs Bibliotheks Einstellungen nicht außer Kraft setzen müssen, entfernen Sie die/LIBPATH-Option in der Befehlszeile des Linkers. Wenn Sie einen alternativen Suchpfad für Bibliotheken verwenden möchten, geben Sie den alternativen Pfad nach der/LIBPATH-Option an.

## <a name="example"></a>Beispiel

```
link /libpath:c:\filepath\lib bar.obj
```

würde den Linker anweisen, nach den erforderlichen Bibliotheken in `c:\filepath\lib` zu suchen, bevor er an den Standard Speicherorten sucht.
