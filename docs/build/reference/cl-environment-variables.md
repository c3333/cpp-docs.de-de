---
title: CL-Umgebungsvariablen
ms.date: 06/06/2019
helpviewer_keywords:
- INCLUDE environment variable
- cl.exe compiler, environment variables
- LIBPATH environment variable
- environment variables, CL compiler
ms.assetid: 2606585b-a681-42ee-986e-1c9a2da32108
ms.openlocfilehash: 4d6b1982b1e544459a025d6cb7bee75666e7130e
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440245"
---
# <a name="cl-environment-variables"></a>CL-Umgebungsvariablen

Das CL-Tool verwendet die folgenden Umgebungsvariablen:

- CL und \_CL_, sofern definiert. Das CL-Tool stellt den Befehlszeilen Argumenten die Optionen und Argumente voran, die in der CL-Umgebungsvariablen definiert sind, und fügt die in \_CL_ definierten Optionen und Argumente vor der Verarbeitung an.

- Schließen Sie ein, das auf das Unterverzeichnis \include Ihrer Visual Studio-Installation verweisen muss.

- LIBPATH gibt Verzeichnisse an, in denen nach Metadatendateien gesucht wird, auf die mit [#using](../../preprocessor/hash-using-directive-cpp.md)verwiesen wird. Weitere Informationen zu LIBPATH finden Sie unter [#using](../../preprocessor/hash-using-directive-cpp.md).

Sie können die CL-oder \_CL_-Umgebungsvariable mithilfe der folgenden Syntax festlegen:

> Set cl = [[*Option*]... [*Datei*]...] [/Link *Link-opt* ...] \
> Set \_cl\_= [*Option*]... [*Datei*]...] [/Link *Link-opt* ...]

Ausführliche Informationen zu den Argumenten für die Umgebungsvariablen cl und \_CL_ finden Sie unter [MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md).

Sie können diese Umgebungsvariablen verwenden, um die Dateien und Optionen zu definieren, die Sie am häufigsten verwenden. Verwenden Sie dann die Befehlszeile, um der CL weitere Dateien und Optionen für bestimmte Zwecke zu übergeben. Die Umgebungsvariablen cl und \_CL_ sind auf 1024 Zeichen beschränkt (Befehlszeilen-Eingabe Limit).

Sie können die [/D](d-preprocessor-definitions.md) -Option nicht verwenden, um ein Symbol zu definieren, das ein Gleichheitszeichen ( **=** ) verwendet. Stattdessen können Sie das Nummern Zeichen ( **#** ) für ein Gleichheitszeichen verwenden. Auf diese Weise können Sie die CL-oder \_CL_ Umgebungsvariablen verwenden, um Präprozessorkonstanten mit expliziten Werten zu definieren, z. –. `/DDEBUG#1`, `DEBUG=1`zu definieren.

Weitere Informationen finden Sie unter [Festlegen von Umgebungsvariablen](../setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="examples"></a>Beispiele

Der folgende Befehl ist ein Beispiel für das Festlegen der CL-Umgebungsvariablen:

> Legen Sie cl =/Zp2/Ox/I\INCLUDE\MYINCLS \lib\binmodefest. OBJ

Wenn die CL-Umgebungsvariable festgelegt ist und Sie `CL INPUT.C` in der Befehlszeile eingeben, wird der effektive Befehl zu:

> CL/Zp2/Ox/I\INCLUDE\MYINCLS \lib\binmode. obj-Eingabe. Scher

Im folgenden Beispiel wird verursacht, dass ein unformatierter CL-Befehl die Quelldateien „FILE1.c“ und „FILE2.c“ kompiliert. Anschließend werden die Objektdateien „FILE1.obj“, „FILE2.obj“ und „FILE3.obj“ verknüpft.

> Legen Sie cl = file1 fest. C file2. Scher
> Legen Sie \_CL_ = datei3 fest. OBJ
> CL

Diese Umgebungsvariablen bewirken, dass der Rückruf von cl denselben Effekt wie die folgende Befehlszeile hat:

> CL file1. C file2. C datei3. OBJ

## <a name="see-also"></a>Weitere Informationen

[Festlegen von Compileroptionen](compiler-command-line-syntax.md) \
[MSVC-Compileroptionen](compiler-options.md)
