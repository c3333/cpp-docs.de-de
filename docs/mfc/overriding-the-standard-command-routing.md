---
title: Überschreiben des Standardbefehlsroutings
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 680b185f8d68a834862bc0fe14bf6e7984effd65
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617724"
---
# <a name="overriding-the-standard-command-routing"></a>Überschreiben des Standardbefehlsroutings

In seltenen Fällen, in denen Sie eine Variation des Standard Framework-Routings implementieren müssen, können Sie diese überschreiben. Die Idee besteht darin, das Routing in einer oder mehreren Klassen zu ändern, indem in diesen Klassen außer Kraft gesetzt wird `OnCmdMsg` . Gehen Sie so vor:

- In der-Klasse, die die Reihenfolge der Übergabe an ein nicht standardmäßiges-Objekt unterbricht.

- Im neuen nicht standardmäßigen Objekt oder in den Befehls Zielen kann es wiederum Befehle an übergeben.

Wenn Sie ein neues Objekt in das Routing einfügen, muss die Klasse eine Befehls Zielklasse sein. Stellen Sie in den über schreibenden Versionen von `OnCmdMsg` sicher, dass Sie die zu über schreibende Version verwenden. Beispiele finden Sie in der Member-Funktion von [OnCmdMsg](reference/ccmdtarget-class.md#oncmdmsg) der `CCmdTarget` -Klasse in der *MFC-Referenz* und in den-Versionen in Klassen wie `CView` und `CDocument` im bereitgestellten Quellcode.

## <a name="see-also"></a>Siehe auch

[So ruft das Framework einen Handler auf](how-the-framework-calls-a-handler.md)
