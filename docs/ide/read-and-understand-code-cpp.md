---
title: Lesen und Verstehen von C++-Code in Visual Studio
description: Verwenden Sie den C++-Code-Editor in Visual Studio, um Ihren Code zu formatieren und zu verstehen.
ms.date: 05/28/2019
ms.openlocfilehash: 9ed0a20fb73e4cc976392bc5e5f698f9658a0b48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377302"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Lesen und Verstehen von C++-Code in Visual Studio

Der C++-Code-Editor und die IDE in Visual Studio bieten viele Programmierhilfen. Einige sind nur für C++, und einige sind im Wesentlichen für alle Visual Studio-Sprachen identisch. Weitere Informationen über die freigegebenen Features finden Sie unter [Schreiben von Code im Code- und Text-Editor](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Farbliche Kennzeichnung

Visual Studio färbt Syntaxelemente ein, um zwischen Typen von Symbolen zu unterscheiden, z. B. Sprachschlüsselwörter, Typnamen, Namen von Variablen, Funktionsparameter, Zeichenfolgenliterale usw.

![Farbliche Kennzeichnung von Code](../ide/media/code-outline-colorization.png "C++-Farbgebung")

Nicht verwendeter Code (z. B. Code unter „#if 0“) wird blasser dargestellt.

![Inaktiver Code](../ide/media/inactive-code-cpp.png "Inaktiver C++-Code")

Sie können die Farben anpassen, indem Sie „Fonts“ (Schriftarten) im **Schnellstart** eingeben und **Schriftarten und Farben** auswählen. Scrollen Sie im Dialogfeld **Schriftarten und Farben** nach unten zu dem C-/C++-Optionen, und wählen Sie dann eine benutzerdefinierte Schriftart und/oder Farbe aus.

## <a name="outlining"></a>Gliedern

Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in einer Quellcodedatei, und wählen Sie **Gliedern** aus, um Codeblöcke und/oder benutzerdefinierte Regionen zu reduzieren oder zu erweitern, um das Durchsuchen nur des für Sie interessanten Codes zu vereinfachen. Weitere Informationen finden Sie unter [Gliedern](/visualstudio/ide/outlining).

![C&#43;&#43; -Gliederung](../ide/media/vs2015_cpp_outlining.png "Gliedern")

Wenn Sie Ihren Cursor vor eine geschweifte Klammer („{“ oder „}“) platzieren, hebt der Editor das zugehörige Gegenstück hervor.

Weitere Gliederungsoptionen finden Sie unter**Umgliederung** **bearbeiten** > im Hauptmenü.

## <a name="line-numbers"></a>Zeilennummern

Sie können Ihrem Projekt Zeilennummern hinzufügen, indem Sie zu **Tools** > **Options** > **Text Editor** > **All Languages** > **General** gehen oder mit Quick **Launch (Strg + Q)** nach "line num" suchen. Zeilennummern können für alle Sprachen oder nur für spezifische Sprachen festgelegt werden, einschließlich C++.

## <a name="scroll-and-zoom"></a>Scrollen und Vergrößern

Sie können den Editor vergrößern oder verkleinern, indem Sie **STRG** halten und mit dem Mausrad scrollen. Sie können auch die Zoomeinstellung in der unteren linken Ecke nutzen.

![C&#43;&#43; Zoom-Steuerung](../ide/media/zoom-control.png "Zoom-Steuerelement")

Mit dem Scrollleisten-**Code Map-Modus** können Sie schnell scrollen und eine Codedatei durchsuchen, ohne die aktuelle Position zu verlassen. Sie können auf eine beliebige Stelle in der Code Map klicken, um zu dieser zu springen.

![Codemap in C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Code Map")

Um den **Kartenmodus**zu aktivieren, geben Sie "Map" in das **Schnellstart-Suchfeld** in der Hauptsymbolleiste ein und wählen **Scrollkartenmodus verwenden**aus. Weitere Informationen finden Sie unter [Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Wenn der **Code Map-Modus** deaktiviert ist, hebt die Scrollleiste weiterhin die Änderungen hervor, die Sie in der Datei vorgenommen haben. Grün gibt gespeicherte Änderungen an, und Gelb gibt nicht gespeicherte Änderungen an.

## <a name="quick-info-and-parameter-info"></a>QuickInfo und ParameterInfo

Zeigen Sie auf eine beliebige Variable, Funktion oder ein anderes Symbol, um Informationen über dieses zu erhalten, einschließlich der Deklaration und weiteren Kommentare, die davor platziert wurden.

::: moniker range="vs-2019"

![Schnelle Informationen in C&#43;&#43;](../ide/media/quick-info-vs2019.png "QuickInfo")

Die **QuickInfo** enthält einen Link zum **Online suchen**.  > Wechseln Sie zur Texteditor-C++-Ansicht**C++** > **View** **"Tools****Options** > **Text Editor",** > um den Suchanbieter anzugeben.

Wenn Ihr Code einen Fehler aufweist, können Sie auf diesen zeigen. In der **QuickInfo** wird die Fehlermeldung angezeigt. Sie können die Fehlermeldung auch im Fenster „Fehlerliste“ finden.

![Schnelle Info zum Fehler](../ide/media/quickinfo-on-error.png "Schnelle Info zum Fehler")

::: moniker-end

::: moniker range="<=vs-2017"

![Schnelle Informationen in C&#43;&#43;](../ide/media/quick-info.png "QuickInfo")

Wenn Ihr Code einen Fehler aufweist, können Sie auf diesen zeigen. In der **QuickInfo** wird die Fehlermeldung angezeigt. Sie können die Fehlermeldung auch im Fenster **Fehlerliste** finden.

![Schnelle Info zum Fehler](../ide/media/quickinfo-on-error.png "Schnelle Info zum Fehler")

::: moniker-end

Wenn Sie eine Funktion aufrufen, zeigt die **ParameterInfo** die Parametertypen und die erwartete Reihenfolge an.

![Parameterinfo in C&#43;&#43;](../ide/media/parameter-info.png "Parameterinfo")

## <a name="peek-definition"></a>Peek-Definition

Zeigen Sie auf eine Variablen- oder Funktionsdeklaration, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Definition einsehen** aus, um eine Inlineansicht der Definition anzuzeigen, ohne die aktuelle Position zu verlassen. Weitere Informationen finden Sie unter [Peek-Definition (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C&#43;&#43; Peek Definition](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>F1-Hilfe

Platzieren Sie den Cursor auf oder nach einem beliebigen Typ, Schlüsselwort oder Funktion und drücken Sie **F1,** um direkt zum entsprechenden Referenzthema auf docs.microsoft.com zu gehen. **F1** funktioniert auch für Elemente in der Fehlerliste und in vielen Dialogfeldern.

## <a name="class-view"></a>Klassenansicht

Die **Klassenansicht** zeigt durchsuchbare Strukturen aller Codesymbole und deren Bereiche sowie über- und untergeordnete Hierarchien pro Projekt an. Sie können in den **Klassenansichtseinstellungen** konfigurieren (klicken Sie hierzu oben im Fenster auf das Zahnradsymbol), was in der **Klassenansicht** angezeigt wird.

![Klassenansicht in C&#43;&#43;](../ide/media/class-view.png "Klassenansicht")

## <a name="generate-graph-of-include-files"></a>Diagramm für Includedateien generieren

Klicken Sie mit der rechten Maustaste auf eine Codedatei im Projekt, und wählen Sie **Diagramm für Includedateien generieren** aus, um ein Diagramm darüber anzuzeigen, welche Dateien in anderen Dateien enthalten sind.

![C&#43;&#43; Diagramm von Include-Dateien](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Aufrufhierarchie anzeigen

Klicken Sie mit der rechten Maustaste auf einen beliebigen Funktionsaufruf, und lassen Sie eine rekursive Liste aller Funktionen anzeigen, die er aufruft, sowie aller Funktionen, die ihn aufrufen. Jede Funktion in der Liste kann auf die gleiche Weise erweitert werden. Weitere Informationen finden Sie unter [Aufrufhierarchie](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; Aufrufhierarchie](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Weitere Informationen

[Schreiben und Umgestalten von Code (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navigieren in C++-Code in Visual Studio](navigate-code-cpp.md)</br>
[Collaborate with Live Share for C++ (Zusammenarbeit über Live Share für C++)](live-share-cpp.md)
