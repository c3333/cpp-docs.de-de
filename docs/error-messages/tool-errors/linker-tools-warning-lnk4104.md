---
title: Linkertoolwarnung LNK4104
ms.date: 11/04/2016
f1_keywords:
- LNK4104
helpviewer_keywords:
- LNK4104
ms.assetid: ca6728db-d616-419a-a570-65e8445c6079
ms.openlocfilehash: 604dccf01b3dffc0060546bebf19d64c16ebf965
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193965"
---
# <a name="linker-tools-warning-lnk4104"></a>Linkertoolwarnung LNK4104

der Export des Symbols ' Symbol ' muss privat sein.

Die `symbol` kann eine der folgenden sein:

- `DllCanUnloadNow`

- `DllGetClassObject`

- `DllGetClassFactoryFromClassString`

- `DllGetDocumentation`

- `DllInitialize`

- `DllInstall`

- `DllRegisterServer`

- `DllRegisterServerEx`

- `DllRegisterServerExW`

- `DllUnload`

- `DllUnregisterServer`

- `RasCustomDeleteEntryNotify`

- `RasCustomDial`

- `RasCustomDialDlg`

- `RasCustomEntryDlg`

Diese Warnung wird ausgegeben, wenn Sie eine Import Bibliothek für eine DLL-Datei entwickeln und eine der obigen Funktionen exportieren, ohne Sie in der Modul Definitionsdatei als privat anzugeben. Im Allgemeinen werden diese Funktionen nur zur Verwendung durch OLE exportiert. Wenn Sie Sie in der Import Bibliothek platzieren, kann dies zu ungewöhnlichen Verhalten führen, wenn ein Programm, das mit der Bibliothek verknüpft ist, fälschlicherweise Aufrufe an Sie sendet. Weitere Informationen zum Schlüsselwort "private" finden Sie unter [Exporte](../../build/reference/exports.md).
