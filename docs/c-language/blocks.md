---
title: Blöcke
ms.date: 11/04/2016
helpviewer_keywords:
- function definitions, blocks in code
- blocks
- compound statements
- statements, compound
ms.assetid: be231a92-c712-464e-ae25-a4becb20f7f5
ms.openlocfilehash: 4f308864e6e85f74e40d9c9df200a0254fea366a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325909"
---
# <a name="blocks"></a>Blöcke

Eine Sequenz von Deklarationen, Definitionen und Anweisungen, die in geschweiften Klammern ( **{ }** ) eingeschlossen sind, wird als „Block“ bezeichnet. Bei C gibt es zwei Arten von Blöcken. Die „Verbundanweisung“ bestehend aus mindestens einer Anweisung (siehe [Die Verbundanweisung](../c-language/compound-statement-c.md)) ist eine Art von Block. Der andere, die „Funktionsdefinition“, besteht aus einer Verbundanweisung (dem Text der Funktion) und dem zugeordneten „Header“ (dem Funktionsnamen, dem Rückgabetyp und den formalen Parametern). Ein Block in anderen Blöcken wird als "geschachtelt" bezeichnet.

Beachten Sie, dass, während alle Verbundanweisungen in geschweiften Klammern eingeschlossen sind, nicht alles, was innerhalb der geschweiften Klammern eingeschlossen ist, eine Verbundanweisung bildet. Beispielsweise können die Spezifikationen von Array-, Struktur- oder Enumerationselementen zwar innerhalb der geschweiften Klammern angezeigt werden, sie sind jedoch keine Verbundanweisungen.

## <a name="see-also"></a>Siehe auch

[Quelldateien und Quellprogramme](../c-language/source-files-and-source-programs.md)
