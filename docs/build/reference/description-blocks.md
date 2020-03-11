---
title: Beschreibungsblöcke
description: NMAKE verwendet Beschreibungs Blöcke, um Ziele, Abhängigkeiten und Befehle in einem Makefile zuzuordnen.
ms.date: 10/29/2019
helpviewer_keywords:
- description blocks
- NMAKE program, description blocks
- blocks, description
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
ms.openlocfilehash: fb9cf4400c96b588e8704e972dd29ab27f41cae9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856928"
---
# <a name="description-blocks"></a>Beschreibungsblöcke

Beschreibungs Blöcke bilden den Kern eines Makefile. Sie beschreiben die *Ziele*oder Dateien, die erstellt werden sollen, und Ihre *Abhängigkeiten*, die zum Erstellen der Ziele benötigten Dateien. Ein Beschreibungsblock kann *Befehle*enthalten, die beschreiben, wie die Ziele aus den Abhängigkeiten erstellt werden. Ein Beschreibungsblock ist eine Abhängigkeits Zeile, optional gefolgt von einem Commands-Block:

```makefile
targets... : dependents...
    commands...
```

## <a name="dependency-lines"></a>Abhängigkeits Linien

Eine *Abhängigkeits Linie* gibt ein oder mehrere Ziele und NULL oder mehr abhängige Elemente an. Wenn ein Ziel nicht vorhanden ist oder einen früheren Zeitstempel aufweist als ein abhängiger, führt NMAKE die Befehle im Befehls Block aus. NMAKE führt auch den Befehls Block aus, wenn es sich bei dem Ziel um ein [pseudotarget](pseudotargets.md)handelt. Im folgenden finden Sie ein Beispiel für eine Abhängigkeits Linie:

```makefile
hi_bye.exe : hello.obj goodbye.obj helper.lib
```

In dieser Abhängigkeits Linie ist `hi_bye.exe` das Ziel. Die Abhängigkeiten sind `hello.obj`, `goodbye.obj`und `helper.lib`. Die Abhängigkeits Zeile weist NMAKE an, das Ziel immer dann zu erstellen, wenn `hello.obj`, `goodbye.obj`oder `helper.lib` vor `hi_bye.exe`geändert wurden.

Ein Ziel muss sich am Anfang der Zeile befinden. Sie kann nicht mit Leerzeichen oder Tabstopps eingerückt werden. Verwenden Sie einen Doppelpunkt (`:`), um Ziele von abhängigen Elementen voneinander zu trennen. Leerzeichen oder Tabstopps sind zwischen Zielen, dem Doppelpunkt Trennzeichen (`:`) und abhängigen Elementen zulässig. Wenn Sie die Abhängigkeits Linie aufteilen möchten, verwenden Sie einen umgekehrten Schrägstrich (`\`) nach einem Ziel oder einer abhängigen.

Vor der Ausführung von Befehls Blöcken scannt NMAKE alle Abhängigkeiten und alle anwendbaren Inferenz Regeln, um eine *Abhängigkeits*Struktur zu erstellen. Eine Abhängigkeitsstruktur gibt die Schritte an, die zum vollständigen Aktualisieren des Ziels erforderlich sind. NMAKE prüft rekursiv, ob ein abhängiges selbst ein Ziel in einer anderen Abhängigkeits Liste ist. Nachdem die Abhängigkeitsstruktur erstellt wurde, überprüft NMAKE Zeitstempel. Wenn alle abhängigen Elemente in der Struktur neuer als das Ziel sind, erstellt NMAKE das Ziel.

## <a name="targets"></a>Ziele

Der Targets-Abschnitt einer Abhängigkeits Linie gibt ein oder mehrere Ziele an. Ein Ziel kann ein beliebiger gültiger Dateiname, Verzeichnisname oder [Pseudo Ziel](pseudotargets.md)sein. Trennen Sie mehrere Ziele mithilfe von einem oder mehreren Leerzeichen oder Registerkarten. Ziele beachten nicht die Groß-/Kleinschreibung. Pfade sind mit Dateinamen zulässig. Ein Ziel und sein Pfad dürfen nicht länger als 256 Zeichen sein. Wenn das Ziel, das dem Doppelpunkt vorangestellt ist, ein einzelnes Zeichen ist, verwenden Sie ein Trennzeichen. Andernfalls interpretiert NMAKE die Kombination aus Buchstaben und Doppelpunkt als laufwerkspezifizierer.

### <a name="multiple-targets"></a>Mehrere Ziele

NMAKE wertet mehrere Ziele in einer einzelnen Abhängigkeit aus, als ob Sie in einem separaten Beschreibungsblock angegeben wurden.

Diese Regel ist beispielsweise:

```makefile
bounce.exe leap.exe : jump.obj
   echo Building...
```

wird ausgewertet als:

```makefile
bounce.exe : jump.obj
   echo Building...

leap.exe : jump.obj
   echo Building...
```

### <a name="cumulative-dependencies"></a>Kumulative Abhängigkeiten

Abhängigkeiten sind in einem Beschreibungsblock kumulativ, wenn ein Ziel wiederholt wird.

Beispielsweise dieser Regelsatz,

```makefile
bounce.exe : jump.obj
bounce.exe : up.obj
   echo Building bounce.exe...
```

wird ausgewertet als:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Wenn in einem einzelnen Beschreibungsblock mehrere Ziele in mehreren Abhängigkeits Zeilen vorhanden sind, wertet NMAKE diese aus, als wären Sie in einem separaten Beschreibungsblock angegeben. Allerdings verwenden nur Ziele in der letzten Abhängigkeits Zeile den Commands-Block. NMAKE versucht, eine Rückschluss Regel für die anderen Ziele zu verwenden.

Beispielsweise dieser Regelsatz,

```makefile
leap.exe bounce.exe : jump.obj
bounce.exe climb.exe : up.obj
   echo Building bounce.exe...
```

wird ausgewertet als:

```makefile
leap.exe : jump.obj
# invokes an inference rule

bounce.exe : jump.obj up.obj
   echo Building bounce.exe...

climb.exe : up.obj
   echo Building bounce.exe...
```

### <a name="targets-in-multiple-description-blocks"></a>Ziele in mehreren Beschreibungs Blöcken

Um ein Ziel in mehr als einem Beschreibungsblock mithilfe verschiedener Befehle zu aktualisieren, geben Sie zwei aufeinander folgende Doppelpunkte an (::) zwischen Zielen und abhängigen Elementen.

```makefile
target.lib :: one.asm two.asm three.asm
    ml one.asm two.asm three.asm
    lib target one.obj two.obj three.obj
target.lib :: four.c five.c
    cl /c four.c five.c
    lib target four.obj five.obj
```

### <a name="dependency-side-effects"></a>Auswirkungen auf Abhängigkeiten

Sie können ein Ziel mit einem Doppelpunkt angeben (:) in zwei Abhängigkeits Zeilen an unterschiedlichen Standorten. Wenn Befehle nach nur einer der Zeilen angezeigt werden, interpretiert NMAKE die Abhängigkeiten so, als ob die Zeilen nebeneinander oder kombiniert wären. Es wird keine Rückschluss Regel für die Abhängigkeit aufgerufen, die über keine Befehle verfügt. Stattdessen geht NMAKE davon aus, dass die Abhängigkeiten zu einem Beschreibungsblock gehören, und führt die Befehle aus, die mit der anderen Abhängigkeit angegeben werden. Beachten Sie diese Regelsätze:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
```

wird ausgewertet als:

```makefile
bounce.exe : jump.obj up.obj
   echo Building bounce.exe...
```

Dieser Effekt tritt nicht auf, wenn ein doppelter Doppelpunkt (`::`) verwendet wird. Dies ist beispielsweise der folgende Regelsatz:

```makefile
bounce.exe :: jump.obj
   echo Building bounce.exe...

bounce.exe :: up.obj
```

wird ausgewertet als:

```makefile
bounce.exe : jump.obj
   echo Building bounce.exe...

bounce.exe : up.obj
# invokes an inference rule
```

### <a name="pseudotargets"></a>Pseudo Ziele

Ein *pseudotarget* ist eine Bezeichnung, die anstelle eines Datei namens in einer Abhängigkeits Zeile verwendet wird. Sie wird als Datei interpretiert, die nicht vorhanden ist, und ist daher veraltet. NMAKE geht davon aus, dass der Zeitstempel eines pseudotarget-Elements mit dem letzten seiner abhängigen Elemente identisch ist. Wenn keine abhängigen Elemente angezeigt werden, wird die aktuelle Zeit angenommen. Wenn ein pseudotarget als Ziel verwendet wird, werden seine Befehle immer ausgeführt. Ein als abhängiges verwendetes pseudotarget muss auch als Ziel in einer anderen Abhängigkeit angezeigt werden. Diese Abhängigkeit muss jedoch nicht über einen Commands-Block verfügen.

Pseudotarget-Namen befolgen die Dateiname-Syntax Regeln für Ziele. Wenn der Name jedoch keine Erweiterung hat, kann er den Grenzwert von 8 Zeichen für Dateinamen überschreiten und kann bis zu 256 Zeichen lang sein.

Pseudo Ziele sind nützlich, wenn Sie möchten, dass NMAKE mehr als ein Ziel automatisch erstellt. NMAKE erstellt nur Ziele, die in der Befehlszeile angegeben sind. Wenn kein Befehlszeilen Ziel angegeben ist, wird nur das erste Ziel in der ersten Abhängigkeit in der Makefile erstellt. Sie können NMAKE anweisen, mehrere Ziele zu erstellen, ohne Sie einzeln in der Befehlszeile aufzulisten. Schreiben Sie einen Beschreibungsblock mit einer Abhängigkeit, die ein pseudotarget enthält, und Listen Sie die Ziele auf, die Sie als abhängige Objekte erstellen möchten. Platzieren Sie dann diesen Beschreibungsblock zuerst in der Makefile, oder geben Sie das Pseudo Ziel in der NMAKE-Befehlszeile an.

In diesem Beispiel ist Update ein pseudotarget.

```makefile
UPDATE : *.*
!COPY $** c:\product\release
```

Wenn Update ausgewertet wird, kopiert NMAKE alle Dateien im aktuellen Verzeichnis auf das angegebene Laufwerk und Verzeichnis.

Im folgenden Makefile erstellt der pseudotarget-`all` sowohl `project1.exe` als auch `project2.exe`, wenn entweder `all` oder kein Ziel in der Befehlszeile angegeben ist. Der pseudotarget-`setenv` ändert die lib-Umgebungsvariable, bevor die `.exe` Dateien aktualisiert werden:

```makefile
all : setenv project1.exe project2.exe

project1.exe : project1.obj
    LINK project1;

project2.exe : project2.obj
    LINK project2;

setenv :
    set LIB=\project\lib
```

## <a name="dependents"></a>Abhängigen Elemente

Geben Sie in einer Abhängigkeits Linie 0 (null) oder mehr abhängige Elemente nach dem Doppelpunkt (`:`) oder dem doppelten Doppelpunkt (`::`) an, indem Sie einen beliebigen gültigen Dateinamen oder [Pseudo Ziel](pseudotargets.md)verwenden. Trennen Sie mehrere abhängige Elemente mithilfe von einem oder mehreren Leerzeichen oder Registerkarten. Abhängige Elemente werden nicht zwischen Groß-und Kleinschreibung beachtet. Pfade sind mit Dateinamen zulässig.

### <a name="inferred-dependents"></a>Abhergestellte abhängige Elemente

Neben abhängigen Elementen, die Sie explizit in der Abhängigkeits Zeile auflisten, kann NMAKE eine abherleitet *abhängige Abhängigkeit*annehmen. Eine abgeleitete abhängige Abhängigkeit wird von einer Inferenz Regel abgeleitet und vor expliziten abhängigen Elementen ausgewertet. Wenn eine abherabzurufende abhängige im Vergleich zum Ziel veraltet ist, ruft NMAKE den Befehls Block für die Abhängigkeit auf. Wenn eine abzurufende abhängige nicht vorhanden ist oder im Vergleich zu ihren eigenen abhängigen Elementen veraltet ist, aktualisiert NMAKE zuerst die abzurufende abhängige Abhängigkeit. Weitere Informationen zu abgelegten abhängigen Elementen finden Sie unter [Inferenz Regeln](inference-rules.md).

### <a name="search-paths-for-dependents"></a>Suchpfade für abhängige Elemente

Sie können einen optionalen Suchpfad für jede abhängige angeben. Hier ist die Syntax zum Angeben eines Satzes von zu durchsuchenden Verzeichnissen:

> **{** _Verzeichnis_\[ **;** _Verzeichnis_...] **}** _abhängig_

Umschließen von Verzeichnisnamen in geschweiften Klammern (`{ }`). Trennen Sie mehrere Verzeichnisse durch ein Semikolon (`;`). Es sind keine Leerzeichen oder Tabstopps zulässig. NMAKE sucht nach der abhängigen ersten im aktuellen Verzeichnis und dann in der Liste der Verzeichnisse in der angegebenen Reihenfolge. Sie können ein Makro verwenden, um einen Teil oder einen beliebigen Suchpfad anzugeben. Nur die angegebene abhängige verwendet diesen Suchpfad.

#### <a name="directory-search-path-example"></a>Beispiel für Verzeichnis Suchpfad

Diese Abhängigkeits Linie zeigt, wie eine Verzeichnis Spezifikation für eine Suche erstellt wird:

```makefile
reverse.exe : {\src\omega;e:\repo\backwards}retro.obj
```

Der Ziel `reverse.exe` hat einen abhängigen, `retro.obj`. Die in Klammern eingeschlossene Liste gibt zwei Verzeichnisse an. NMAKE sucht zuerst im aktuellen Verzeichnis nach `retro.obj`. Wenn dies nicht der Fall ist, durchsucht NMAKE das `\src\omega` Verzeichnis und dann das `e:\repo\backwards` Verzeichnis.

## <a name="see-also"></a>Weitere Informationen

[NMAKE-Referenz](nmake-reference.md)
