---
title: Lesen und Verstehen von C++-Code in Visual Studio
description: Verwenden Sie den C++-Code-Editor in Visual Studio, um Ihren Code zu formatieren und zu verstehen.
ms.date: 05/28/2019
ms.openlocfilehash: cd152ffbbd106c6a31a21da35d08b53555047209
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924648"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Lesen und Verstehen von C++-Code in Visual Studio

Der C++-Code-Editor und die IDE in Visual Studio bieten viele Programmierhilfen. Einige sind nur für C++, und einige sind im Wesentlichen für alle Visual Studio-Sprachen identisch. Weitere Informationen über die freigegebenen Features finden Sie unter [Schreiben von Code im Code- und Text-Editor](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Farbliche Kennzeichnung

Visual Studio färbt Syntaxelemente ein, um zwischen Typen von Symbolen zu unterscheiden, z. B. Sprachschlüsselwörter, Typnamen, Namen von Variablen, Funktionsparameter, Zeichenfolgenliterale usw.

![Farbliche Kennzeichnung von Code](../ide/media/code-outline-colorization.png "Farbliche Kennzeichnung in C++")

Nicht verwendeter Code (z. B. Code unter „#if 0“) wird blasser dargestellt.

![Inaktiver Code](../ide/media/inactive-code-cpp.png "Inaktiver Code in C++")

Sie können die Farben anpassen, indem Sie „Fonts“ (Schriftarten) im **Schnellstart** eingeben und **Schriftarten und Farben** auswählen. Scrollen Sie im Dialogfeld **Schriftarten und Farben** nach unten zu dem C-/C++-Optionen, und wählen Sie dann eine benutzerdefinierte Schriftart und/oder Farbe aus.

## <a name="outlining"></a>Gliedern

Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle in einer Quellcodedatei, und wählen Sie **Gliedern** aus, um Codeblöcke und/oder benutzerdefinierte Regionen zu reduzieren oder zu erweitern, um das Durchsuchen nur des für Sie interessanten Codes zu vereinfachen. Weitere Informationen finden Sie unter [Gliedern](/visualstudio/ide/outlining).

![C&#43;&#43; – Gliedern](../ide/media/vs2015_cpp_outlining.png "Gliedern")

Wenn Sie Ihren Cursor vor eine geschweifte Klammer („{“ oder „}“) platzieren, hebt der Editor das zugehörige Gegenstück hervor.

Weitere Gliederungsoptionen finden Sie im Hauptmenü unter **Bearbeiten** > **Gliederung**.

## <a name="line-numbers"></a>Zeilennummern

Sie können Zeilennummern zu Ihrem Projekt hinzufügen, indem Sie **Extras** > **Optionen** > **Text-Editor** > **Alle Sprachen** > **Allgemein** öffnen oder mit **Schnellstart (STRG+Q)** nach „line num“ (Zeilennummern) suchen. Zeilennummern können für alle Sprachen oder nur für spezifische Sprachen festgelegt werden, einschließlich C++.

## <a name="scroll-and-zoom"></a>Scrollen und Vergrößern

Sie können den Editor vergrößern oder verkleinern, indem Sie **STRG** halten und mit dem Mausrad scrollen. Sie können auch die Zoomeinstellung in der unteren linken Ecke nutzen.

![C&#43;&#43; – Zoomsteuerung](../ide/media/zoom-control.png "Zoom-Steuerelement")

Mit dem Scrollleisten- **Code Map-Modus** können Sie schnell scrollen und eine Codedatei durchsuchen, ohne die aktuelle Position zu verlassen. Sie können auf eine beliebige Stelle in der Code Map klicken, um zu dieser zu springen.

![Code Map in C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Code Map")

Geben Sie „map“ in das **Schnellstart** -Suchfeld in der Hauptsymbolleiste ein, und wählen Sie **Use scroll map mode** (Scroll-Code Map-Modus verwenden) aus, um den **Code Map-Modus** zu aktivieren. Weitere Informationen finden Sie unter [Vorgehensweise: Verfolgen von Code durch Anpassen der Scrollleiste](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Wenn der **Code Map-Modus** deaktiviert ist, hebt die Scrollleiste weiterhin die Änderungen hervor, die Sie in der Datei vorgenommen haben. Grün gibt gespeicherte Änderungen an, und Gelb gibt nicht gespeicherte Änderungen an.

## <a name="quick-info-and-parameter-info"></a>QuickInfo und ParameterInfo

Zeigen Sie auf eine beliebige Variable, Funktion oder ein anderes Symbol, um Informationen über dieses zu erhalten, einschließlich der Deklaration und weiteren Kommentare, die davor platziert wurden.

::: moniker range="msvc-160"

![Screenshot der QuickInfo in Visual Studio 2019](../ide/media/quick-info-vs2019.png "QuickInfo")

Die **QuickInfo** enthält einen Link zum **Online suchen**. Öffnen Sie **Extras** > **Optionen** > **Text-Editor** > **C++**  > **Ansicht** , um den Suchanbieter festzulegen.

Wenn Ihr Code einen Fehler aufweist, können Sie auf diesen zeigen. In der **QuickInfo** wird die Fehlermeldung angezeigt. Sie können die Fehlermeldung auch im Fenster „Fehlerliste“ finden.

![QuickInfo bei Fehler](../ide/media/quickinfo-on-error.png "QuickInfo bei Fehler")

::: moniker-end

::: moniker range="<=msvc-150"

![Screenshot der QuickInfo in Visual Studio 2017](../ide/media/quick-info.png "QuickInfo")

Wenn Ihr Code einen Fehler aufweist, können Sie auf diesen zeigen. In der **QuickInfo** wird die Fehlermeldung angezeigt. Sie können die Fehlermeldung auch im Fenster **Fehlerliste** finden.

![QuickInfo bei Fehler](../ide/media/quickinfo-on-error.png "QuickInfo bei Fehler")

::: moniker-end

Wenn Sie eine Funktion aufrufen, zeigt die **ParameterInfo** die Parametertypen und die erwartete Reihenfolge an.

![Parameterinfo in C&#43;&#43;](../ide/media/parameter-info.png "Parameterinformationen")

## <a name="peek-definition"></a>Peek-Definition

Zeigen Sie auf eine Variablen- oder Funktionsdeklaration, klicken Sie mit der rechten Maustaste, und wählen Sie dann **Definition einsehen** aus, um eine Inlineansicht der Definition anzuzeigen, ohne die aktuelle Position zu verlassen. Weitere Informationen finden Sie unter [Peek-Definition (Alt+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C&#43;&#43; – Peek-Definition](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>F1-Hilfe

Platzieren Sie den Cursor in oder direkt hinter einen Typ, ein Schlüsselwort oder einer Funktion, und drücken Sie **F1** , um direkt das entsprechende Referenzthema auf docs.microsoft.com zu öffnen. **F1** funktioniert auch für Elemente in der Fehlerliste und in vielen Dialogfeldern.

## <a name="class-view"></a>Klassenansicht

Die **Klassenansicht** zeigt durchsuchbare Strukturen aller Codesymbole und deren Bereiche sowie über- und untergeordnete Hierarchien pro Projekt an. Sie können in den **Klassenansichtseinstellungen** konfigurieren (klicken Sie hierzu oben im Fenster auf das Zahnradsymbol), was in der **Klassenansicht** angezeigt wird.

![Klassenansicht in C&#43;&#43;](../ide/media/class-view.png "Klassenansicht")

## <a name="generate-graph-of-include-files"></a>Diagramm für Includedateien generieren

Klicken Sie mit der rechten Maustaste auf eine Codedatei im Projekt, und wählen Sie **Diagramm für Includedateien generieren** aus, um ein Diagramm darüber anzuzeigen, welche Dateien in anderen Dateien enthalten sind.

![C&#43;&#43; – Diagramm für Includedateien](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Aufrufhierarchie anzeigen

Klicken Sie mit der rechten Maustaste auf einen beliebigen Funktionsaufruf, und lassen Sie eine rekursive Liste aller Funktionen anzeigen, die er aufruft, sowie aller Funktionen, die ihn aufrufen. Jede Funktion in der Liste kann auf die gleiche Weise erweitert werden. Weitere Informationen finden Sie unter [Aufrufhierarchie](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; – Aufrufhierarchie](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Weitere Informationen

[Schreiben und Umgestalten von Code (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navigate your C++ code base in Visual Studio (Navigieren in Ihrer C++-Codebasis in Visual Studio)](navigate-code-cpp.md)</br>
[Collaborate with Live Share for C++ (Zusammenarbeit über Live Share für C++)](live-share-cpp.md)
