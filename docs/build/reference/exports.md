---
title: EXPORTS
ms.date: 09/07/2018
f1_keywords:
- EXPORTS
helpviewer_keywords:
- EXPORTS .def file statement
ms.assetid: dbcd7579-b855-44c4-bd27-931e157657f7
ms.openlocfilehash: 9ede0d3b53c975298dea3d1331bc0fb00ac246b2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328258"
---
# <a name="exports"></a>EXPORTS

Führt einen Abschnitt mit mindestens einer Exportdefinition ein, die die exportierten Namen oder Ordinalzahlen von Funktionen oder Daten angibt. Jede Definition muss sich in einer separaten Zeile befinden.

```DEF
EXPORTS
   definition
```

## <a name="remarks"></a>Bemerkungen

Die erste *Definition* kann sich in `EXPORTS` derselben Zeile wie das Schlüsselwort oder in einer nachfolgenden Zeile befinden. Die .DEF-Datei kann eine oder mehrere `EXPORTS`-Anweisungen enthalten.

Die Syntax für eine *Exportdefinition* lautet:

> *Eintragsname*\[__=__*internal_name*|*other_module.exported_name*] \[ **\@** _Ordinal_ \[ **NONAME**] ] \[ \[ **PRIVATE**] | \[ **DATEN**] ]

*eintragsname* ist der Funktions- oder Variablenname, den Sie exportieren möchten. Dies ist erforderlich. Wenn sich der Von Ihnen exportierte Name vom Namen in der DLL unterscheidet, geben Sie den Namen des Exports in der DLL mithilfe *internal_name an.* Wenn Ihre DLL beispielsweise eine Funktion `func1` exportiert und Sie möchten, dass Aufrufer sie als `func2` verwenden, würden Sie Folgendes angeben:

```DEF
EXPORTS
   func2=func1
```

Wenn der Name, den Sie exportieren, aus einem anderen Modul stammt, geben Sie den Namen des Exports in der DLL mithilfe *von other_module.exported_name*an. Wenn Ihre DLL beispielsweise eine Funktion `other_module.func1` exportiert und Sie möchten, dass Aufrufer sie als `func2` verwenden, würden Sie Folgendes angeben:

```DEF
EXPORTS
   func2=other_module.func1
```

Wenn der Von Ihnen exportierte Name von einem anderen Modul stammt, das von Ordinal exportiert wird, geben Sie die Ordinalorale des Exports in der DLL mithilfe *other_module*an. __#__ *ordinal*. Wenn Ihre DLL z. B. eine Funktion aus dem anderen Modul exportiert, in dem sie `func2`ordinal 42 ist, und Sie möchten, dass Aufrufer sie als verwenden, geben Sie Folgendes an:

```DEF
EXPORTS
   func2=other_module.#42
```

Da der MSVC-Compiler die Namensdekoration für C++-Funktionen *internal_name* verwendet, müssen Sie `extern "C"` entweder den ergänzten Namen internal_name verwenden oder die exportierten Funktionen mithilfe des Quellcodes definieren. Der Compiler schmückt auch C-Funktionen, die die [__stdcall](../../cpp/stdcall.md) Aufrufkonvention mit einem Unterstrich (\_)\@Präfix und einem Suffix verwenden, das aus dem at-Zeichen ( ) gefolgt von der Anzahl der Bytes (dezimal) in der Argumentliste besteht.

Um die vom Compiler erstellten namenerstellten Namen zu finden, verwenden Sie das [DUMPBIN-Tool](dumpbin-reference.md) oder die [Linker/MAP-Option.](map-generate-mapfile.md) Die ergänzten Namen sind compilerspezifisch. Wenn Sie die ergänzten Namen in der .DEF-Datei exportieren, müssen die ausführbaren Dateien, die zur DLL verknüpfen, ebenfalls mit derselben Version des Compilers erstellt werden. Damit wird sichergestellt, dass die ergänzten Namen im Aufrufer den exportierten Namen in der .DEF-Datei entsprechen.

Sie können \@ *Ordinal* verwenden, um anzugeben, dass eine Zahl und nicht der Funktionsname in die Exporttabelle der DLL übergeht. Viele Windows-DLLs exportieren Ordinalzahlen, um Legacycode zu unterstützen. Es war üblich, Ordinalzahlen in 16-Bit-Windows-Code zu verwenden, weil das dazu beitragen kann, die Größe einer DLL zu minimieren. Es wird nicht empfohlen, Funktionen nach Ordinal zu exportieren, es sei denn, die Clients Ihrer DLL benötigen sie für Legacy-Support. Da die .LIB-Datei die Zuordnung zwischen der Ordinalzahl und der Funktion enthält, können Sie den Funktionsnamen verwenden, wie Sie es normalerweise in Projekten tun würden, die die DLL verwenden.

Mithilfe des **NONAME** optionalen NONAME-Schlüsselworts können Sie nur nach Ordinal exportieren und die Größe der Exporttabelle in der resultierenden DLL reduzieren. Wenn Sie jedoch [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) für die DLL verwenden möchten, müssen Sie die Ordnung kennen, da der Name ungültig ist.

Das optionale Schlüsselwort **PRIVATE** verhindert, dass *der Eintragsname* in die von LINK generierte Importbibliothek aufgenommen wird. Es wirkt sich nicht auf den Export des ebenfalls von LINK generierten Image aus.

Das optionale Schlüsselwort **DATA** gibt an, dass ein Export Daten und kein Code ist. Das folgende Beispiel zeigt, wie Sie eine Datenvariable namens `exported_global` exportieren könnten:

```DEF
EXPORTS
   exported_global DATA
```

Es gibt vier Möglichkeiten für das Exportieren einer Definition, aufgelistet in empfohlener Reihenfolge:

1. Das [Schlüsselwort __declspec(dllexport)](../../cpp/dllexport-dllimport.md) im Quellcode

1. Eine `EXPORTS`-Anweisung in einer .DEF-Datei

1. Eine [/EXPORT-Spezifikation](export-exports-a-function.md) in einem LINK-Befehl

1. Eine [Kommentardirektive](../../preprocessor/comment-c-cpp.md) im Quellcode des `#pragma comment(linker, "/export: definition ")`Formulars . Das folgende Beispiel zeigt eine #pragma Kommentardirektivum vor einer Funktionsdeklaration, wobei `PlainFuncName` der nicht dekorierte Name `_PlainFuncName@4` der Funktion ist:

    ```cpp
    #pragma comment(linker, "/export:PlainFuncName=_PlainFuncName@4")
    BOOL CALLBACK PlainFuncName( Things * lpParams)
    ```

Die #pragma-Direktive ist nützlich, wenn Sie einen nicht dekorierten Funktionsnamen exportieren müssen und je nach Buildkonfiguration unterschiedliche Exporte haben (z. B. in 32-Bit- oder 64-Bit-Builds).

Alle vier Methoden können im selben Programm verwendet werden. Wenn LINK ein Programm erstellt, das Exporte enthält, wird auch eine Importbibliothek erstellt, es sei denn, im Build wird eine .EXP-Datei verwendet.

Hier ist ein Beispiel für einen EXPORTS-Abschnitt:

```DEF
EXPORTS
   DllCanUnloadNow      @1          PRIVATE
   DllWindowName = WindowName       DATA
   DllGetClassObject    @4 NONAME   PRIVATE
   DllRegisterServer    @7
   DllUnregisterServer
```

Wenn Sie eine Variable aus einer DLL über dien .DEF-Datei exportieren, müssen Sie `__declspec(dllexport)` nicht in der Variable angeben. Sie müssen jedoch in jeder Datei, die die DLL verwendet, immer noch `__declspec(dllimport)` in der Deklaration der Daten verwenden.

## <a name="see-also"></a>Siehe auch

[Regeln für Moduldefinitionsanweisungen](rules-for-module-definition-statements.md)
