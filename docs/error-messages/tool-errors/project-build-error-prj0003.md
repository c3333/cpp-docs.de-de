---
title: Projektbuildfehler PRJ0003
ms.date: 11/04/2016
f1_keywords:
- PRJ0003
helpviewer_keywords:
- PRJ0003
ms.assetid: fc5a84bb-c6d3-41d6-8dd6-475455820778
ms.openlocfilehash: 59028c6d886630ef7db115a2ea93327669b2fcfd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192925"
---
# <a name="project-build-error-prj0003"></a>Projektbuildfehler PRJ0003

> Fehler beim Erzeugen der*Befehlszeile*.

Der *Befehlszeilen* Befehl, der aus der Eingabe im Dialogfeld **Eigenschaften Seiten** gebildet wurde, hat einen Fehlercode zurückgegeben, im **Ausgabe** Fenster werden jedoch keine Informationen angezeigt.

Mögliche Ursachen für diesen Fehler sind:

- Ihr Projekt hängt von ATL-Server ab. Ab Visual Studio 2008 ist ATL Server nicht mehr als Teil von Visual Studio enthalten, sondern wurde als frei gegebenes Quell Projekt auf CodePlex veröffentlicht. Informationen zum Herunterladen des ATL-Server Quellcodes und der Tools finden Sie in der [ATL-Server Bibliothek und](https://go.microsoft.com/fwlink/p/?linkid=81979)in den Tools.

- Geringe Systemressourcen. Schließen Sie einige Anwendungen, um dieses Problem zu beheben.

- Unzureichende Sicherheits Berechtigungen. Stellen Sie sicher, dass Sie über ausreichende Sicherheits Berechtigungen verfügen.

- Die in **VC + +-Verzeichnissen** angegebenen ausführbaren Pfade enthalten nicht den Pfad für das Tool, das Sie ausführen möchten. Weitere Informationen finden Sie unter [Set Compiler and Build Properties](../../build/working-with-project-properties.md) .

- Für Makefile-Projekte fehlt ein Befehl, der entweder über die **Buildbefehlszeile** oder über die **Befehlszeile Rebuild**erstellt werden kann.

## <a name="see-also"></a>Weitere Informationen

[Projektbuildfehler und -warnungen (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
