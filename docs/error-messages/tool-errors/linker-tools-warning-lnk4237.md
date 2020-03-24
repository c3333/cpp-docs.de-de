---
title: Linkertoolwarnung LNK4237
ms.date: 11/04/2016
f1_keywords:
- LNK4237
helpviewer_keywords:
- LNK4237
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
ms.openlocfilehash: aaa26393f1ce76d3e1bc40e5ba4978d1bcdb4fc9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193757"
---
# <a name="linker-tools-warning-lnk4237"></a>Linkertoolwarnung LNK4237

/Subsystem: nativ angegeben beim Importieren aus "dll". Verwenden Sie/Subsystem: Console oder/Subsystem: Windows.

[/Subsystem: Native](../../build/reference/subsystem-specify-subsystem.md) wurde beim Entwickeln einer Windows-Anwendung (Win32) angegeben, die eine oder mehrere der folgenden Aktionen direkt verwendet:

- kernel32.dll

- gdi32. dll

- user32.dll

- eine der msvcrt-\* DLLs.

Beheben Sie diese Warnung, indem Sie nicht **/Subsystem: Native**angeben.
