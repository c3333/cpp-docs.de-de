---
title: Zusammenarbeit mit Live Share für C++ in Visual Studio
description: Verwenden Sie Live Share für C++ in Visual Studio, um Code in Echtzeit zu bearbeiten und zu teilen.
ms.date: 05/24/2019
ms.openlocfilehash: 60830ad6c6b98f644e1c3ddb2e78fbf7397ae919
ms.sourcegitcommit: 59b7c18703d1ffd66827db0e2eeece490d3d8789
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2020
ms.locfileid: "90684520"
---
# <a name="collaborate-using-live-share-for-c"></a>Zusammenarbeiten mithilfe von Live Share für C++

In Visual Studio 2019 und Visual Studio Code können Sie **Live Share** für die Zusammenarbeit an C++-Projekten in Echtzeit verwenden. Mit **Live Share** kann eine andere Person Ihren Code bearbeiten und debuggen ohne Ihr Projekt oder die zugehörigen Abhängigkeiten zu installieren. Die Bearbeitungen des Anderen werden angezeigt, und jede Bearbeitung wird mit dem Namen der Person markiert, die die Veränderung vorgenommen hat.

![C&#43;&#43; – Live Share-Bearbeitung](../ide/media/live-share-edit-cpp.png "Live Share-Bearbeitung in C++")

## <a name="live-share-host-and-guests"></a>Live Share-Gastgeber und -Gäste

In einer Live Share-Sitzung gibt es einen Gastgeber und mindestens einen Gast. Sowohl der Gastgeber als auch die Gäste können entweder Visual Studio oder Visual Studio Code verwenden. Ein Visual Studio 2019-Gastgeber unter Windows kann nun Inhalte mit einem Visual Studio Code-Gast unter Linux teilen.

Der Gastgeber bietet dem Gast alles, was dieser benötigt, um produktiv zu sein. Gäste müssen nicht über den Quellcode, Compiler, externe Abhängigkeiten oder die gleichen installierten Komponenten verfügen.

Der Gastgeber und die Gäste können diese IntelliSense-Funktionen verwenden:

- Memberliste
- Parameterhilfe
- QuickInfo
- Debuggen/Breakpoints
- Alle Verweise suchen
- Gehe zu Definition
- Symbolsuche (STRG+T)
- Markieren von Verweisen
- Diagnose/Fehler/Wellenlinien

![C&#43;&#43; Live Share-Debuggen](../ide/media/live-share-debug-cpp.png "Live Share-Debuggen in C++")

## <a name="start-and-end-a-live-share-session"></a>Starten und Beenden einer Live Share-Sitzung

Klicken Sie oben rechts auf die Schaltfläche „Freigeben“ oder auf **Datei** > **Start Collaboration Session** (Zusammenarbeitssitzung starten), um eine Live Share-Sitzung in Visual Studio zu starten. Daraufhin wird ein Link generiert, den Sie mit Ihren Projektmitarbeitern teilen können.

![Kleiner Screenshot der Schaltfläche „Live Share“](../ide/media/live-share-button-cpp.png "Schaltfläche „Live Share“")

Wählen Sie zum Beenden einer Sitzung **End Collaboration Session** (Zusammenarbeitssitzung beenden) in der Dropdownliste **Freigabe** aus.

![Screenshot der Dropdownliste „Freigabe“, in der die Option zum Beenden der Zusammenarbeitssitzung hervorgehoben ist](../ide/media/live-share-end-session-cpp.png "Schaltfläche „Live Share“")

## <a name="for-more-information"></a>Weitere Informationen finden Sie unter

Weitere Informationen zu **Live Share** in Visual Studio finden Sie unter [What is Visual Studio Live Share? (Was ist Visual Studio Live Share)](/visualstudio/liveshare/). Weitere Informationen zu Live Share in Visual Studio Code finden Sie unter [Live Share](https://marketplace.visualstudio.com/items?itemName=ms-vsliveshare.vsliveshare).

## <a name="see-also"></a>Weitere Informationen

[Schreiben und Umgestalten von Code (C++)](writing-and-refactoring-code-cpp.md)</br>
[Navigate your C++ code base in Visual Studio (Navigieren in Ihrer C++-Codebasis in Visual Studio)](navigate-code-cpp.md)</br>
[Read and understand C++ code (Lesen und Verstehen von C++-Code)](read-and-understand-code-cpp.md)</br>
