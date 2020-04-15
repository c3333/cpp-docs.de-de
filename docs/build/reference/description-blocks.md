---
title: Beschreibungsblöcke
description: NMAKE verwendet Beschreibungsblöcke, um Ziele, Abhängigkeiten und Befehle in einer Makefile zuzuordnen.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: e4e80b59d3d30b3b34c55b40d337ef5c078e6404
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322264"
---
# <a name="description-blocks"></a>Beschreibungsblöcke

Beschreibungsblöcke bilden den Kern eines Makefiles. Sie beschreiben die *ziele*, oder Dateien zu erstellen, und ihre *Abhängigkeiten*, die Dateien benötigt, um die Ziele zu erstellen. Ein Beschreibungsblock kann *Befehle*enthalten, die beschreiben, wie die Ziele aus den Abhängigkeiten erstellt werden. Ein Beschreibungsblock ist eine Abhängigkeitszeile, optional gefolgt von einem Befehlsblock:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Abhängigkeitslinien

Eine *Abhängigkeitsposition* gibt ein oder mehrere Ziele und null oder mehr abhängige Elemente an. Wenn ein Ziel nicht vorhanden ist oder einen früheren Zeitstempel als ein abhängiger hat, führt NMAKE die Befehle im Befehlsblock aus. NMAKE führt auch den Befehlsblock aus, wenn das Ziel ein [Pseudoziel](pseudotargets.md)ist. Hier ist eine Beispielabhängigkeitszeile:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

In dieser Abhängigkeitslinie `hi_bye.exe` ist das Ziel. Die Abhängigkeiten `hello.obj`sind `goodbye.obj`, `helper.lib`und . Die Abhängigkeitszeile weist NMAKE `hello.obj`an, das Ziel immer dann zu erstellen, wenn , `goodbye.obj`oder `helper.lib` in jüngerer Zeit als `hi_bye.exe`geändert wurde.

Ein Ziel muss sich am Anfang der Zeile begeben. Es kann nicht mit Leerzeichen oder Registerkarten eingerückt werden. Verwenden Sie`:`einen Doppelpunkt ( ), um Ziele von abhängigen Zielen zu trennen. Zwischen Zielen, dem Doppelpunkttrennzeichen (`:`) und abhängigen Zeichen sind Leerzeichen oder Registerkarten zulässig. Um die Abhängigkeitslinie aufzuteilen,`\`verwenden Sie einen umgekehrten Schrägstrich ( ) nach einem Ziel oder abhängig.

Vor der Ausführung von Befehlsblöcken scannt NMAKE alle Abhängigkeiten und alle anwendbaren Rückschlussregeln, um eine *Abhängigkeitsstruktur*zu erstellen. Eine Abhängigkeitsstruktur gibt die Schritte an, die zum vollständigen Aktualisieren des Ziels erforderlich sind. NMAKE überprüft rekursiv, ob ein Abhängiger selbst ein Ziel in einer anderen Abhängigkeitsliste ist. Nachdem die Abhängigkeitsstruktur erstellt wurde, überprüft NMAKE Zeitstempel. Wenn abhängige Elemente in der Struktur neuer als das Ziel sind, erstellt NMAKE das Ziel.

## <a name="targets"></a><a name="targets"></a>Ziele

Der Zielabschnitt einer Abhängigkeitszeile gibt ein oder mehrere Ziele an. Ein Ziel kann ein beliebiger gültiger Dateiname, Verzeichnisname oder [Pseudoziel](pseudotargets.md)sein. Trennen Sie mehrere Ziele, indem Sie einen oder mehrere Leerzeichen oder Registerkarten verwenden. Bei Zielen wird die Groß-/Kleinschreibung nicht berücksichtigt. Pfade sind mit Dateinamen zulässig. Ein Ziel und sein Pfad dürfen 256 Zeichen nicht überschreiten. Wenn das Ziel, das dem Doppelpunkt vorangeht, ein einzelnes Zeichen ist, verwenden Sie ein Trennfeld. Andernfalls interpretiert NMAKE die Buchstaben-Kolon-Kombination als Laufwerkbezeichner.

### <a name="multiple-targets"></a><a name="multiple-targets"></a>Mehrere Ziele

NMAKE wertet mehrere Ziele in einer einzelnen Abhängigkeit aus, als ob jedes in einem separaten Beschreibungsblock angegeben wäre.

Diese Regel lautet z. B.:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

wird bewertet als:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a><a name="cumulative-dependencies"></a>Kumulative Abhängigkeiten

Abhängigkeiten sind in einem Beschreibungsblock kumulativ, wenn ein Ziel wiederholt wird.

Diese Regelreihe ist z. B.

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

wird bewertet als:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Wenn Sie mehrere Ziele in mehreren Abhängigkeitszeilen in einem einzigen Beschreibungsblock haben, wertet NMAKE diese aus, als ob sie in einem separaten Beschreibungsblock angegeben wären. Allerdings verwenden nur Ziele in der letzten Abhängigkeitszeile den Befehlsblock. NMAKE versucht, eine Rückschlussregel für die anderen Ziele zu verwenden.

Diese Regelreihe ist z. B.

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

wird bewertet als:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a><a name="targets-in-multiple-description-blocks"></a>Ziele in mehreren Beschreibungsblöcken

Um ein Ziel in mehr als einem Beschreibungsblock mit verschiedenen Befehlen zu aktualisieren, geben Sie zwei aufeinander folgende Doppelpunkte an (::) zwischen Zielen und abhängigen Personen.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a><a name="dependency-side-effects"></a>Abhängigkeits-Nebenwirkungen

Sie können ein Ziel mit einem Doppelpunkt (:) in zwei Abhängigkeitslinien an verschiedenen Positionen. Wenn Befehle nur nach einer der Zeilen angezeigt werden, interpretiert NMAKE die Abhängigkeiten so, als ob die Zeilen nebeneinander oder kombiniert wären. Es ruft keine Rückschlussregel für die Abhängigkeit auf, die keine Befehle hat. Stattdessen geht NMAKE davon aus, dass die Abhängigkeiten zu einem Beschreibungsblock gehören, und führt die mit der anderen Abhängigkeit angegebenen Befehle aus. Berücksichtigen Sie diesen Regelsatz:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

wird bewertet als:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Dieser Effekt tritt nicht auf,`::`wenn ein Doppelpunkt ( ) verwendet wird. Dieser Regelsatz:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

wird bewertet als:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a><a name="pseudotargets"></a>Pseudoziele

Ein *Pseudoziel* ist eine Bezeichnung, die anstelle eines Dateinamens in einer Abhängigkeitszeile verwendet wird. Sie wird als Datei interpretiert, die nicht vorhanden ist und daher veraltet ist. NMAKE geht davon aus, dass der Zeitstempel eines Pseudoziels mit dem neuesten aller abhängigen Elemente identisch ist. Wenn es keine abhängigen Elemente hat, wird die aktuelle Zeit angenommen. Wenn ein Pseudoziel als Ziel verwendet wird, werden seine Befehle immer ausgeführt. Ein Pseudoziel, das als abhängiger Wert verwendet wird, muss auch als Ziel in einer anderen Abhängigkeit angezeigt werden. Diese Abhängigkeit muss jedoch keinen Befehlsblock haben.

Pseudotarget-Namen folgen den Syntaxregeln für Denknamen für Ziele. Wenn der Name jedoch keine Erweiterung hat, kann er die 8-Stellige Grenze für Dateinamen überschreiten und bis zu 256 Zeichen lang sein.

Pseudoziele sind nützlich, wenn NMAKE automatisch mehr als ein Ziel erstellen soll. NMAKE erstellt nur Ziele, die in der Befehlszeile angegeben sind. Wenn kein Befehlszeilenziel angegeben ist, wird nur das erste Ziel in der ersten Abhängigkeit in der Makefile erstellt. Sie können NMAKE anweisen, mehrere Ziele zu erstellen, ohne sie einzeln in der Befehlszeile aufzulisten. Schreiben Sie einen Beschreibungsblock mit einer Abhängigkeit, die ein Pseudoziel enthält, und listen Sie die Ziele auf, die Sie erstellen möchten, als abhängige Ziele. Platzieren Sie dann diesen Beschreibungsblock zuerst in der Makefile, oder geben Sie das Pseudoziel in der NMAKE-Befehlszeile an.

In diesem Beispiel ist UPDATE ein Pseudoziel.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Wenn UPDATE ausgewertet wird, kopiert NMAKE alle Dateien im aktuellen Verzeichnis in das angegebene Laufwerk und Verzeichnis.

In der folgenden Makefile `all` wird `project1.exe` das `project2.exe` Pseudoziel sowohl erstellt als auch, wenn in der Befehlszeile entweder `all` oder kein Ziel angegeben ist. Das Pseudoziel `setenv` ändert die LIB-Umgebungsvariable, bevor die `.exe` Dateien aktualisiert werden:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a><a name="dependents"></a>Angehörige

Geben Sie in einer Abhängigkeitszeile null oder`:`mehr abhängige`::`Elemente nach dem Doppelpunkt ( ) oder Doppelpunkt ( ) mit einem beliebigen gültigen Dateinamen oder [Pseudoziel](pseudotargets.md)an. Trennen Sie mehrere abhängige Elemente, indem Sie einen oder mehrere Leerzeichen oder Registerkarten verwenden. Abhängige sind nicht groß. Pfade sind mit Dateinamen zulässig.

### <a name="inferred-dependents"></a><a name="inferred-dependents"></a>Abgeleitete abhängige Personen

Zusammen mit abhängigen Personen, die Sie explizit in der Abhängigkeitszeile auflisten, kann NMAKE eine *abgeleitete abhängige*annehmen. Eine abgeleitete abhängige Regel wird von einer Rückschlussregel abgeleitet und vor expliziten abhängigen Werten ausgewertet. Wenn eine abgeleitete abhängige Abhängigkeit im Vergleich zu ihrem Ziel veraltet ist, ruft NMAKE den Befehlsblock für die Abhängigkeit auf. Wenn eine abgeleitete abhängige Person nicht vorhanden ist oder im Vergleich zu ihren eigenen abhängigen Abhängigkeiten veraltet ist, aktualisiert NMAKE zuerst die abgeleitete abhängige. Weitere Informationen zu abgeleiteten abhängigen Personen finden Sie unter [Rückschlussregeln](inference-rules.md).

### <a name="search-paths-for-dependents"></a><a name="search-paths-for-dependents"></a>Suchpfade für abhängige Personen

Sie können einen optionalen Suchpfad für jeden abhängigen Pfad angeben. Hier ist die Syntax, um einen Satz von Verzeichnissen anzugeben, die gesucht werden sollen:

> Verzeichnis **;** _directory_ **{**\[ _Verzeichnis_...] **•**_abhängig_

Schließen Sie Verzeichnisnamen in`{ }`geschweifte Klammern ein ( ). Trennen Mehrerer Verzeichnisse mit einem`;`Semikolon ( ). Es sind keine Leerzeichen oder Registerkarten zulässig. NMAKE sucht zuerst im aktuellen Verzeichnis und dann in der Liste der Verzeichnisse in der angegebenen Reihenfolge nach dem abhängigen. Sie können ein Makro verwenden, um einen Teil oder den gesamten Suchpfad anzugeben. Nur die angegebene abhängige verwendet diesen Suchpfad.

#### <a name="directory-search-path-example"></a>Beispiel für den Verzeichnissuchpfad

In dieser Abhängigkeitszeile wird gezeigt, wie eine Verzeichnisspezifikation für eine Suche erstellt wird:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

Das `reverse.exe` Ziel hat `retro.obj`eine abhängige , . Die mit Klammern eingeschlossene Liste gibt zwei Verzeichnisse an. NMAKE sucht `retro.obj` zuerst im aktuellen Verzeichnis. Wenn es nicht vorhanden ist, durchsucht `\src\omega` NMAKE das `e:\repo\backwards` Verzeichnis und dann das Verzeichnis.

## <a name="see-also"></a>Siehe auch

[NMAKE Reference (NMAKE-Referenz)](nmake-reference.md)
