---
title: C/C++-Präprozessorreferenz
description: Referenz für den Microsoft C/C++ Compiler-Präprozessor in Visual Studio.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e53f7270a71e5e7c3f456be7d55d49eaf352aecb
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040742"
---
# <a name="cc-preprocessor-reference"></a>C/C++-Präprozessorreferenz

Die *C/C++-Präprozessorreferenz* erläutert den Präprozessor, wie er in Microsoft C/C++ implementiert ist. Der Präprozessor führt vorbereitende Vorgänge für C- und C++-Dateien aus, bevor sie an den Compiler übergeben werden. Sie können den Präprozessor verwenden, um Code bedingt zu kompilieren, Dateien einzufügen, Kompilierzeit-Fehlermeldungen anzugeben und computerspezifische Regeln auf Codeabschnitte anzuwenden.

In Visual Studio 2019 ermöglicht die [/experimental: Preprocessor](../build/reference/experimental-preprocessor.md) -Compileroption eine neue Implementierung des Präprozessors. Die neue Implementierung wird noch ausgeführt und wird daher als experimentell angesehen. Er soll schließlich mit C99, C11 und c++ 20 konform sein. Weitere Informationen finden Sie unter [MSVC: Übersicht über den neuen Präprozessor](preprocessor-experimental-overview.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Präprozessor](preprocessor.md)\
Bietet eine Übersicht über die herkömmlichen und neuen konformen Präprozessoren.

[Präprozessordirektiven](../preprocessor/preprocessor-directives.md)\
Beschreibt die Anweisungen, die normalerweise verwendet werden, um das Ändern und Kompilieren von Quellprogrammen in unterschiedlichen Ausführungsumgebungen zu vereinfachen.

[Präprozessoroperatoren](../preprocessor/preprocessor-operators.md)\
Erläutert die vier präprozessorspezifischen Operatoren, die im Kontext der `#define`-Direktive verwendet werden.

[Vordefinierte Makros](../preprocessor/predefined-macros.md)\
Erläutert vordefinierte Makros, die durch die C-und C++-Standards und durch Microsoft C++ festgelegt sind.

[Pragmas](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
Erläutert Pragmas, die jedem Compiler eine Möglichkeit bieten, computer- und betriebssystemspezifische Funktionen bereitzustellen und dabei die Gesamtkompatibilität mit anderen C- und C++-Programmiersprachen beizubehalten.

## <a name="related-sections"></a>Verwandte Abschnitte

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)\
Enthält Referenzmaterial für die Microsoft-Implementierung der Programmiersprache C++.

[C-Programmiersprachen Referenz](../c-language/c-language-reference.md)\
Enthält Referenzmaterial für die Microsoft-Implementierung der Programmiersprache C.

[C/C++-buildverweis](../build/reference/c-cpp-building-reference.md)\
Enthält Links zu Themen, in denen die Verwendung von Compiler- und Linkeroptionen erörtert wird.

[Visual Studio-Projekte C++](../build/creating-and-managing-visual-cpp-projects.md)\
Beschreibt die Benutzeroberfläche in Visual Studio, die Ihnen die Möglichkeit gibt, die Verzeichnisse festzulegen, die das Projektsystem durchsucht, um Dateien für das C++-Projekt zu suchen.
