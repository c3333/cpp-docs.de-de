---
title: Reservierte Wörter
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171150"
---
# <a name="reserved-words"></a>Reservierte Wörter

Die folgenden Wörter sind vom Linker reserviert. Diese Namen können nur in [Modul Definitions Anweisungen](module-definition-dot-def-files.md) als Argumente verwendet werden, wenn der Name in doppelte Anführungszeichen ("") eingeschlossen ist.

||||
|-|-|-|
|**Apploader**<sup>1</sup>|**InitInstance**<sup>2</sup>|**Vorab laden**|
|**Sock**|**Iopl**|**Private**|
|**Ordnung**|**Bibliothek**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**Menden**|**Loadoncall1**<sup>1</sup>|**Rein**<sup>1</sup>|
|**Vorrats**|**Longnames**<sup>2</sup>|**ReadOnly**|
|**BESCHREIBUNG**|**Verschieb**Bare<sup>1</sup>|**ReadWrite**|
|**DEV386**|**Kann**<sup>1</sup>|**Realmode**<sup>1</sup>|
|**Entfernbare**|**Mehr**|**Bewohnten**|
|**Schem**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**nur ausführen**|**Newfiles**<sup>2</sup>|**Strecken**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**Vergeben**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**Genu**|
|**EXETYPE**|**Noname**|**Gänger**|
|**EXPORTE**|**Nicht konform**<sup>1</sup>|**STACKSIZE**|
|**Korrigiert**<sup>1</sup>|**Nicht verwerfbar**|**STUB**|
|**Funktionen**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**Nicht freigegebene**|**Windowapi**|
|**Importiert**|**Notwindowcompat**<sup>1</sup>|**Windows compat**|
|**Impure**<sup>1</sup>|**Gütern**|**Windows**|
|**INCLUDE**<sup>2</sup> einschließen|**Alt**<sup>1</sup>||

<sup>1</sup> der Linker gibt eine Warnung ("ignoriert") aus, wenn dieser Begriff auftritt. Allerdings ist das Wort immer noch reserviert.

<sup>2</sup> der Linker ignoriert dieses Wort, gibt jedoch keine Warnung aus.

## <a name="see-also"></a>Weitere Informationen

- [MSVC-Linkerreferenz](linking.md)
- [MSVC-Linkeroptionen](linker-options.md)
