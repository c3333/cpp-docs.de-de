---
title: C/C++-Präprozessorreferenz
description: Referenz für den Microsoft C/C++ Compiler-Präprozessor in Visual Studio.
ms.date: 09/10/2020
helpviewer_keywords:
- preprocessor
- preprocessor, reference overview
ms.assetid: e4a52843-7016-4f6d-8b40-cb1ace18f805
ms.openlocfilehash: e72146d8b88f5a4bffcaaa121f6851d740ec948b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075633"
---
# <a name="cc-preprocessor-reference"></a>C/C++-Präprozessorreferenz

Die *C/C++-Präprozessorreferenz* erläutert den Präprozessor, wie er in Microsoft C/C++ implementiert ist. Der Präprozessor führt vorbereitende Vorgänge für C- und C++-Dateien aus, bevor sie an den Compiler übergeben werden. Sie können den Präprozessor verwenden, um Code bedingt zu kompilieren, Dateien einzufügen, Kompilierzeit-Fehlermeldungen anzugeben und computerspezifische Regeln auf Codeabschnitte anzuwenden.

In Visual Studio 2019 bietet die [/Zc: präprocessor](../build/reference/zc-preprocessor.md) -Compileroption einen vollständig kompatiblen C11-und C17-Präprozessor. Dies ist die Standardeinstellung, wenn Sie das-Compilerflag `/std:c11` oder verwenden `/std:c17` .

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
