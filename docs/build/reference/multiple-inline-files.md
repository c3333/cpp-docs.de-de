---
title: Mehrere Inlinedateien
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 71f17ff6717e717693facb21b4a4341a040b14c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320590"
---
# <a name="multiple-inline-files"></a>Mehrere Inlinedateien

Ein Befehl kann mehr als eine Inlinedatei erstellen.

## <a name="syntax"></a>Syntax

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Hinweise

Geben Sie für jede Datei eine oder mehrere Textzeilen Inline gefolgt von einer schließenden-Zeile, die das Trennzeichen enthält. Beginnen Sie mit der zweiten Datei Text in der Zeile nach der begrenzenden Zeile für die erste Datei.

## <a name="see-also"></a>Siehe auch

[Inlinedateien in einem Makefile](inline-files-in-a-makefile.md)
