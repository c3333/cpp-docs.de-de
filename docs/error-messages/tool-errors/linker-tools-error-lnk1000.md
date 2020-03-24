---
title: Linkertoolfehler LNK1000
ms.date: 06/18/2018
f1_keywords:
- LNK1000
helpviewer_keywords:
- LNK1000
ms.assetid: 86421b9a-460a-4285-8dce-9b8257d78122
ms.openlocfilehash: 48b976f6e996d0e076849dc9b20b4cedd47dfbcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195421"
---
# <a name="linker-tools-error-lnk1000"></a>Linkertoolfehler LNK1000

> Unbekannter Fehler. Lesen Sie die Dokumentation zu den technischen Supportoptionen

Beachten Sie die Umstände des Fehlers, versuchen Sie, das Problem zu isolieren, und erstellen Sie einen reproduzierbaren Testfall. Informationen dazu, wie Sie diese Fehler untersuchen und melden, finden Sie unter [melden eines Problems mit dem C++ visuellen Toolset oder der Dokumentation](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Dieser Fehler wird möglicherweise angezeigt, wenn Sie Standard Header Dateien (z. b. Windows. h) und ihre eigenen Dateien kombinieren. Fügen Sie zuerst einen vorkompilierten Header (sofern vorhanden) und dann die Standard Header ein, gefolgt von ihren eigenen Header Dateien.
