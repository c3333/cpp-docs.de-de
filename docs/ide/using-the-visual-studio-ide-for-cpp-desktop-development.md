---
title: Verwenden der Visual Studio-IDE für C++-Desktopentwicklung
ms.date: 04/25/2019
helpviewer_keywords:
- IDE [C++]
- Visual Studio IDE [C++]
ms.assetid: d985c230-8e81-49d6-92be-2db9cac8d023
ms.openlocfilehash: 082aa353d3046d9c9b20669e075e200c96017bce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371763"
---
# <a name="using-the-visual-studio-ide-for-c-desktop-development"></a>Verwenden der Visual Studio-IDE für C++-Desktopentwicklung

Die Visual Studio-IDE bietet eine Reihe von Features, die Ihnen beim Verwalten großer und kleiner Codeprojekte, beim Schreiben und Umgestalten des Codes und beim Ermitteln und Korrigieren von Fehlern helfen, indem sowohl statische Analyse und leistungsstarke Debugtools verwendet werden. Diese Artikelreihe begleitet Sie bei der Ausführung der Schritte zum Verwalten Ihrer Projekte, zum Schreiben, Testen und Debuggen Ihres Codes und zum Bereitstellen auf einem anderen Computer.

## <a name="prerequisites"></a>Voraussetzungen

Installieren Sie Visual Studio, falls Sie das noch nicht getan haben. Downloadlinks und eine kurze Anleitung finden Sie unter [Installieren der C++-Unterstützung in Visual Studio](../build/vscpp-step-0-installation.md). Weitere Informationen zur allgemeinen Installation von Visual Studio sowie Ratschläge zur Problembehandlung finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio). Achten Sie darauf, die Workload **Desktopentwicklung mit C++** auszuwählen, um den C++-Compiler, C++-Tools und C++-Bibliotheken bei der Installation von Visual Studio einzuschließen. Diese werden nicht standardmäßig installiert.

Diese exemplarischen Vorgehensweisen setzen voraus, dass Sie Visual Studio und die für die Windows-Desktopentwicklung erforderlichen C++-Komponenten installiert haben. Außerdem wird davon ausgegangen, dass Sie die Grundlagen der C++-Sprache verstehen. Wenn Sie C++ lernen müssen, stehen Ihnen viele Bücher und Webressourcen zur Verfügung. Die Seite [Get Started (Erste Schritte)](https://isocpp.org/get-started) der Standard-C++-Foundation-Website ist ein guter Startpunkt.

Installieren Sie Visual Studio, falls Sie das noch nicht getan haben. In der Regel wird die Verwendung von Visual Studio 2019 unbedingt empfohlen, auch wenn Sie dann Ihren Code mithilfe des Visual Studio 2017- oder Visual Studio 2015-Compilers kompilieren müssen. Weitere Informationen finden Sie unter [Use native multi-targeting in Visual Studio to build old projects (Verwenden der nativen Festlegung von Zielversionen in Visual Studio, um alte Projekte zu erstellen)](../porting/use-native-multi-targeting.md).

**Installation von Visual Studio 2019**

Sie können Visual Studio 2019 auf der [Visual Studio-Website „Downloads“](https://www.visualstudio.com/downloads/) herunterladen. Achten Sie darauf, dass die C++-Entwicklungstools in der Installation von Visual Studio enthalten sind, da sie nicht standardmäßig installiert werden. Weitere Informationen über das Installieren von Visual Studio finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio).

**Installieren von Visual Studio 2017**

Sie können Visual Studio 2017 auf der [Visual Studio-Website für Downloads älterer Versionen](https://www.visualstudio.com/vs/older-downloads/) herunterladen. Achten Sie darauf, dass die C++-Entwicklungstools in der Installation von Visual Studio enthalten sind, da sie nicht standardmäßig installiert werden. Weitere Informationen über das Installieren von Visual Studio finden Sie unter [Installieren von Visual Studio](/visualstudio/install/install-visual-studio). Um die Anweisungen für Visual Studio 2017 anzuzeigen, legen Sie das Visual **Studio-Versionsauswahlsteuerelement** auf Visual Studio 2017 fest. Sie befindet sich oben im Inhaltsverzeichnis auf der Seite.

**Installieren von Visual Studio 2015**

Auf der Seite [Downloads älterer Versionen von Visual Studio](https://www.visualstudio.com/vs/older-downloads/) können Sie Visual Studio 2015 herunterladen. Führen Sie das Setupprogramm aus, klicken Sie auf **Benutzerdefinierte Installation**, und wählen Sie die C++-Komponente aus.

Sobald die Visual Studio-Installation abgeschlossen ist, können Sie anfangen.

## <a name="get-started"></a>Erste Schritte

Arbeiten Sie sich der Reihe nach durch diese Themen, um C++-Apps mit der Visual Studio-IDE zu erstellen. Jedes Thema baut auf das vorherige auf:

- [Exemplarische Vorgehensweise: Arbeiten mit Projekten und Lösungen (C++)](walkthrough-working-with-projects-and-solutions-cpp.md)

- [Exemplarische Vorgehensweise: Erstellen eines Projekts (C++)](walkthrough-building-a-project-cpp.md)

- [Exemplarische Vorgehensweise: Testen eines Projekts (C++)](walkthrough-testing-a-project-cpp.md)

- [Exemplarische Vorgehensweise: Debuggen eines Projekts (C++)](walkthrough-debugging-a-project-cpp.md)

- [Exemplarische Vorgehensweise: Bereitstellen des Programms (C++)](walkthrough-deploying-your-program-cpp.md)

## <a name="next-steps"></a>Nächste Schritte

Sobald Sie diese exemplarischen Vorgehensweisen abgeschlossen haben, sind Sie bereit, mit dem Erstellen Ihrer eigenen Projekte anzufangen. Weitere Informationen und Ressourcen zur C++-Entwicklung finden Sie unter [C++ in Visual Studio](../overview/visual-cpp-in-visual-studio.md).

## <a name="see-also"></a>Siehe auch

[Erste Schritte bei der Entwicklung in Visual Studio](/visualstudio/ide/get-started-developing-with-visual-studio)
