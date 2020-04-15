---
title: Festlegen der C++-Codierungseinstellungen in Visual Studio
ms.description: Customize C++ formatting, colors, layout, line numbers, and menus in the Visual Studio IDE.
ms.topic: overview
ms.date: 09/27/2019
ms.openlocfilehash: e3a665ead7a314b343ec3320e95b189f83a38a47
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365389"
---
# <a name="set-your-c-coding-preferences-in-visual-studio"></a>Festlegen der C++-Codierungseinstellungen in Visual Studio

Sie können Ihre C++-Codierung bequemer, produktiver und angenehmer gestalten, indem Sie Visual Studio personalisieren. Ihre Möglichkeiten:

- Passen Sie die Menüs und Symbolleisten an.
- Ordnen Sie das Fensterlayout an.
- Legen Sie Farbthemen fest.
- Geben Sie C++-Formatierungsregeln an, einschließlich mehrerer ClangFormat-Formatvorlagen.
- Erstellen Sie benutzerdefinierte Tastenkombinationen.

Sie können Ihre Einstellungen auf mehreren Computern synchronisieren, mehrere Sätze von Voreinstellungen erstellen und speichern und für Teamkollegen freigeben. Sie können Erweiterungen aus dem Visual Studio Marketplace installieren, sodass Sie zusätzliche Optionen zum Anpassen des Verhaltens erhalten. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="arrange-window-layout"></a>Fensterlayout anordnen

Innerhalb des Visual Studio-Fensters wird der Bereich in das Hauptmenü, die Symbolleiste, den Code-Editor (oder das Dokumentfenster) und Die Toolfenster (z. B. Projektmappen-Explorer und Fehlerliste) unterteilt. Einige Fenster überlappen sich an der gleichen Position. Beispielsweise haben Projektmappen-Explorer, Klassenansicht, Ressourcenansicht und Quellcodeverwaltungs-Explorer alle dieselbe Standardposition. Sie wechseln zwischen ihnen, indem Sie die Registerkarten am unteren Rand des Rahmens auswählen. Um zwei oder mehr dieser Fenster gleichzeitig sichtbar zu machen, ziehen Sie einfach eines von ihnen durch die Titelleiste an eine neue Position. Sie können es an einen der Visual Studio-Hauptfensterrahmen andocken oder es schweben lassen.

Der folgende Screenshot zeigt, wie das **Team Explorer-Fenster** von seiner Standardposition an eine neue, angedockte Position auf der linken Seite des Codeeditors gezogen wird. Der blau schattierte Bereich zeigt an, wo das Fenster platziert wird, wenn die Maustaste freigegeben wird.

![Screenshot des Visual Studio Team Explorer-Fensters, wobei die Layoutänderung hervorgehoben ist](media/window-layout-move-team-explorer.png)

Im Dokumentfenster ist jede geöffnete Datei in einem Tabbed-Frame enthalten. Sie können diese Registerkarten wie Inseis pro-Mann schweben oder sperren. Weitere Informationen finden Sie unter Anpassen von [Fensterlayouts in Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

Um alle Toolfenster auszublenden und das Code-Editor-Fenster zu maximieren, **drücken** + Sie Alt**Shift** + **Enter,** um *den Vollbildmodus*umzuschalten.

## <a name="set-c-coding-styles-and-formatting"></a>Festlegen von C++-Codierungsstilen und Formatierungen

Sie können viele einzelne Codeformatierungsoptionen angeben, z. B. Einzugs- und geschweifte Positionen. Gehen Sie dazu > zu **Werkzeugoptionen** > **Options** > **Texteditor** > **C/C++****Formatierung** (oder geben Sie **Strg + Q** ein und suchen Sie nach "Formatierung"). Alternativ können Sie einen der [ClangFormat-Stile](https://clang.llvm.org/docs/ClangFormat.html) (oder Ihren eigenen benutzerdefinierten ClangFormat-Stil) angeben.

![Screenshot der ClangFormat-Optionen](media/clang-format-ide.png)

Weitere Informationen zu allen Formatierungsoptionen finden Sie unter [Optionen, Texteditor, C/C++, Formatierung](/visualstudio/ide/reference/options-text-editor-c-cpp-formatting).

## <a name="set-the-color-theme"></a>Festlegen des Farbdesigns

Um einen hellen oder dunklen Hintergrund festzulegen, geben Sie **Strg + Q** ein und suchen Sie nach "Farbthema". Sie können diese auch finden, indem Sie zu **Tools** > **Options** > **Environment**gehen und Farbe **Thema**auswählen.

![Screenshot von Farbthemen](media/tools-options-color-theme.png)

Zum Beispiel ist hier das dunkle Thema:

![Screenshot von Visual Studio mit dunklem Farbdesign](media/tools-options-dark-theme.png)

## <a name="customize-code-colorization"></a>Anpassen der Codefarbgebung

In Visual Studio 2019 können Sie aus drei vordefinierten *Farbschemata*wählen. Diese geben an, wie Codeelemente im Editor koloriert werden. Um ein Design auszuwählen, gehen Sie zu **Tools** > **Options** > **Text Editor** > **C/C++** > **View**, und wählen Sie **Farbschema**:

![Screenshot der C++-Farbschemaoptionen mit hervorgehobener](media/color-schemes.png)

Im Farbschema **Visual Studio 2017**sind die meisten Codeelemente einfach schwarz. Im **erweiterten** Farbschema werden Funktionen, lokale Variablen, Makros und andere Elemente koloriert. Im Schema **"Erweitert" (Globals vs. Members)** werden globale Funktionen und Variablen so koloriert, dass sie mit Klassenmitgliedern kontrastiert werden. Der Standardmodus ist **Enhanced**, und es sieht wie folgt aus:

![Screenshot des erweiterten Farbschemas](media/color-scheme-enhanced.png)

Unabhängig davon, welches Design oder Farbschema aktiv ist, können Sie die Schriftart und Farben für einzelne Codeelemente anpassen. Um dies zu tun, gehen Sie zu **Tools** > **Options** > **Environment** > **Fonts and Colors** (oder geben Sie **Strg + Q** ein und suchen Sie nach "Fonts"). Scrollen Sie in der Liste der Anzeigeelemente nach unten, bis die C++-Optionen angezeigt werden.

![Screenshot der C++-Schriftart- und Farboptionen](media/tools-options-cpp-colors.png)

Farben, die Sie hier festlegen, überschreiben die für die Farbschemata definierten Werte. Wenn Sie zu den Standardfarben für das Farbschema zurückkehren möchten, legen Sie die Farbe wieder auf **Standard**fest.

## <a name="customize-the-toolbars"></a>Anpassen der Symbolleisten

Die Symbolleisten bieten eine bequeme Möglichkeit, Befehle mit einem einzigen Klick auszugeben, anstatt die Menüs oder Tastenkombinationen zu verwenden. Visual Studio enthält einen Standardsatz von Symbolleisten. Für die standardmäßige C++-Entwicklung sind die nützlichsten Symbolleisten wahrscheinlich Standard,Text Editor, Build, Debug, Source Control und Compare Files. Für die Windows-Entwicklung sind der Dialog-Editor und der Bild-Editor nützlich, um Dialogfelder und Bearbeitungssymbole zu erstellen.

Zeigen Sie mit der Maus auf die Symbole in der Symbolleiste, um zu sehen, welcher Befehl er darstellt:

![Screenshot von Symbolsymbolen der Symbolleiste mit Beispielen für Befehlsinformationen, die auf der Mauszeiger verfügbar sind](media/toolbar-mouse-hover.png)

Sie können Befehle hinzufügen oder entfernen oder eine benutzerdefinierte Symbolleiste erstellen, indem Sie den Abwärtspfeil auswählen. Um die Symbolleiste an eine neue Position zu verschieben, ziehen Sie sie durch die gepunktete Leiste auf der linken Seite.

![Screenshot der Symbolleiste mit hervorgehobenem Pfeil und gepunkteter Leiste](media/toolbar-move-edit.png).

Weitere Informationen finden Sie unter [Gewusst wie: Anpassen von Menüs und Symbolleisten in Visual Studio](/visualstudio/ide/how-to-customize-menus-and-toolbars-in-visual-studio).

## <a name="show-or-hide-line-numbers"></a>Ein- oder Ausblenden von Zeilennummern

Sie können angeben, ob Zeilennummern links von den Editorfenstern angezeigt werden. Wählen Sie unter **Optionen**unter **C/C++** die Option **Allgemein**aus. Wählen Sie im Abschnitt **Einstellungen** **Zeilennummern**aus, je nach Ihren Vorlieben.

![Screenshot der allgemeinen Optionen mit hervorgehobenen Zeilennummern](media/tools-options-line-numbers.png)

## <a name="create-keyboard-shortcuts"></a>Erstellen von Tastenkombinationen

Viele Befehle in Visual Studio verfügen über *Tastenkombinationen*, Tastenkombinationen mit den Tasten Strg, Alt und Umschalttaste. Sie können diese Tastenkombinationen ändern oder eigene Tastenkombinationen in Visual Studio erstellen. Wechseln**Environment** > Sie zu **Umgebungstastatur für** > **Tools-Optionen** > (oder geben Sie **Strg + Q** ein, und suchen Sie nach "Shortcuts").**Keyboard** Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).
