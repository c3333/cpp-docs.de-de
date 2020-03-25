---
title: Aktualisieren einer Spalte, wenn eine andere Tabelle einen Verweis auf die Zeile enthält
ms.date: 10/24/2018
helpviewer_keywords:
- rowsets, column updates
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
ms.openlocfilehash: 95cddfd5f030c7bd8d1220cf040de4bc5a883226
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209481"
---
# <a name="updating-a-column-when-another-table-contains-a-reference-to-the-row"></a>Aktualisieren einer Spalte, wenn eine andere Tabelle einen Verweis auf die Zeile enthält

Einige Anbieter können erkennen, welche Spalten in der Zeile geändert werden, aber viele Anbieter können dies nicht tun. Folglich kann das Aktualisieren einer Spalte zu einem Fehler führen, wenn ein Verweis auf die Zeile vorhanden ist, die Sie aktualisieren möchten. Um dieses Problem zu beheben, erstellen Sie einen separaten Accessor, der nur die Spalten enthält, die Sie ändern möchten. Übergeben Sie die Nummer dieses Accessors an `SetData`.

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Zugriffsmethoden](../../data/oledb/using-accessors.md)
