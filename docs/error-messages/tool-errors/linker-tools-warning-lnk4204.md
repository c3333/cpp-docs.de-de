---
title: Linkertoolwarnung LNK4204
ms.date: 11/04/2016
f1_keywords:
- LNK4204
helpviewer_keywords:
- LNK4204
ms.assetid: 14adda20-0cbe-407b-90f6-9f81c93530e2
ms.openlocfilehash: 98c53c9b998e9bd544c1cc72bd2b0c3fd2b0a418
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193861"
---
# <a name="linker-tools-warning-lnk4204"></a>Linkertoolwarnung LNK4204

im Dateinamen fehlen Debuginformationen für das Verweis Modul; Objekt wird verknüpft, als ob keine Debuginformationen

Die PDB-Datei hat eine fehlerhafte Signatur. Der Linker verknüpft das Objekt weiterhin ohne Debuginformationen. Möglicherweise möchten Sie die Objektdatei mit der [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) -Option neu kompilieren.

Linkertoolwarnung LNK4204 kann auftreten, wenn einige der Objekte in der Bibliothek auf eine Datei verweisen, die nicht mehr vorhanden ist. Dies kann bei der Neuerstellung der Lösung vorkommen, z. b. eine Objektdatei wird möglicherweise gelöscht und aufgrund eines Kompilierungs Fehlers nicht neu erstellt. Kompilieren Sie in diesem Fall entweder mit **/Z7**oder **/FD**, um die Objekte so zu aktualisieren, dass Sie auf eine einzelne Datei pro Bibliothek verweisen (Dies ist nicht der Standardname der PDB-Datei).  Weitere Informationen finden Sie unter [/Fd (Programmdatenbank-Dateiname)](../../build/reference/fd-program-database-file-name.md).  Stellen Sie sicher, dass die PDB-Datei bei jeder Aktualisierung im Quell Code Verwaltungssystem mit der Bibliothek gespeichert wird.
