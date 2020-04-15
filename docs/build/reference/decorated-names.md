---
title: Ergänzte Namen
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: f6d81029d20d9aaca96ff184f48e94a9ce35d56e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320499"
---
# <a name="decorated-names"></a>Ergänzte Namen

Funktionen, Daten und Objekte werden in C- und C++-Programmen intern durch ihre ergänzten Namen dargestellt. Ein *ergänzter Name* ist eine codierte Zeichenfolge, die vom Compiler während der Kompilierung eines Objekts, einer Daten- oder Funktionsdefinition erstellt wird. Er zeichnet Aufrufkonventionen, Typen, Funktionsparameter und sonstige Informationen zusammen mit dem Namen auf. Diese Namensdekoration, auch bekannt als *Name Mangling*, hilft dem Linker, die richtigen Funktionen und Objekte beim Verknüpfen einer ausführbaren Datei zu finden.

Die dekorierten Namenskonventionen haben sich in verschiedenen Versionen von Visual Studio geändert und können auch in verschiedenen Zielarchitekturen unterschiedlich sein. Um eine korrekte Verknüpfung mit Quelldateien herzustellen, die mithilfe von Visual Studio-, C- und C++-DLLs und -Bibliotheken erstellt wurden, sollten dieselben Compilertoolsets, Flags und Zielarchitekturen verwendet werden.

> [!NOTE]
> Mit Visual Studio 2015 erstellte Bibliotheken können von Anwendungen verwendet werden, die mit Visual Studio 2017 oder Visual Studio 2019 erstellt wurden.

## <a name="using-decorated-names"></a><a name="Using"></a>Verwenden von dekorierten Namen

In der Regel müssen Sie den ergänzten Namen nicht kennen, um Code schreiben zu können, der erfolgreich kompiliert werden kann und richtige Verknüpfungen aufweist. Ergänzte Namen sind ein internes Implementierungsdetail des Compilers und Linkers. Die Tools können den Name in der Regel auch in seiner nicht ergänzten Form behandeln. Ein ergänzter Name ist jedoch manchmal erforderlich, wenn Sie einen Funktionsnamen zum Linker oder anderen Tools angeben. Um zum Beispiel überladene C++-Funktionen, Member von Namespaces, Klassenkonstruktoren, Destruktoren und spezielle Memberfunktionen angeben zu können, müssen Sie den ergänzten Namen verwenden. Weitere Informationen zu den Optionskennzeichnungen und anderen Situationen, in denen ergänzte Namen erforderlich sind, finden Sie in der Dokumentation zu den von Ihnen verwendeten Tools und Optionen.

Wenn Sie den Funktionsnamen, die Klasse, die Aufrufkonvention, den Rückgabetyp oder einen Parameter ändern, ändert sich auch der ergänzte Name. In diesem Fall müssen Sie den neuen ergänzten Namen abrufen und ihn überall dort verwenden, wo der ergänzte Name angegeben ist.

Die Namensergänzung ist auch dann wichtig, wenn eine Verknüpfen mit Code erfolgt, der in einer anderen Programmiersprache geschrieben wurde oder andere Compiler verwendet. Verschiedene Compilern verwenden unterschiedliche Konventionen für die Namensergänzung. Wenn Ihre ausführbare Datei eine Verknüpfung zu Code enthält, der in einer anderen Sprache geschrieben wurde, müssen Sie insbesondere darauf achten, dass die exportierten und importierten Namen und Aufrufkonventionen übereinstimmen. Assemblysprachcode muss die MSVC-namen und Aufrufkonventionen verwenden, um eine Verknüpfung mit Quellcode herzustellen, der mit MSVC geschrieben wurde.

## <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Format eines C++-verzierten Namens

Ein ergänzter Name für eine C++-Funktion enthält die folgenden Informationen:

- Der Funktionsname.

- Die Klasse, dessen Mitglied die Funktion ist, wenn es sich um eine Memberfunktion handelt. Dies kann die Klasse einschließen, die die Klasse umschließt, welche die Funktion enthält usw.

- Der Namespace, zu dem die Funktion gehört, wenn sie Teil eines Namespace ist.

- Die Typen der Funktionsparameter.

- Die Aufrufkonvention.

- Der Rückgabetyp der Funktion.

Die Namen der Funktion und der Klasse werden im ergänzten Namen codiert. Der Rest des ergänzten Namens ist ein Code, der nur für den Compiler und Linker eine interne Bedeutung hat. Es folgen Beispiele für nicht ergänzte und ergänzte Namen in C++.

|Nicht ergänzter Name|Ergänzter Name|
|----------------------|--------------------|
|`int a(char){int i=3;return i;};`|`?a@@YAHD@Z`|
|`void __stdcall b::c(float){};`|`?c@b@@AAGXM@Z`|

## <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Format eines C-verzierten Namens

Das Format einer Ergänzung für eine C-Funktion hängt von der Aufrufkonvention ab, die in der Deklaration verwendet wird. Dies isst in der folgenden Tabelle dargestellt. Dies ist auch das Ergänzungsformat, das verwendet wird, wenn C++-Code mit einer `extern "C"` Verknüpfung deklariert wird. Die Standardaufrufkonvention ist `__cdecl`. Beachten Sie, dass Funktion in einer 64-Bit-Umgebung nicht ergänzt werden.

|Aufrufkonvention|Dekoration|
|------------------------|----------------|
|`__cdecl`|Führender Unterstrich (**_**)|
|`__stdcall`|Führender Unterstrich (**_**) und**\@** ein Trailing bei Vorzeichen ( ), gefolgt von der Anzahl der Bytes in der Parameterliste in Dezimalzahl|
|`__fastcall`|Führenund nachvorn**\@** bei Zeichen ( ), gefolgt von einer Dezimalzahl, die die Anzahl der Bytes in der Parameterliste darstellt|
|`__vectorcall`|Zwei Nachfolgen bei**\@** Zeichen ( ), gefolgt von einer Dezimalzahl von Bytes in der Parameterliste|

## <a name="viewing-decorated-names"></a><a name="Viewing"></a>Anzeigen von dekorierten Namen

Sie erhalten das ergänzte Format eines Symbolnamens, wenn Sie die Quelldatei mit den Daten, dem Objekt oder der Funktionsdefinition bzw. dem Prototypen kompiliert haben. Um ergänzte Namen im Programm zu untersuchen, können Sie eine der folgenden Methoden verwenden:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Verwenden einer Auflistung zum Anzeigen ergänzter Namen

1. Generieren Sie eine Auflistung, indem Sie die Quelldatei kompilieren, die die Daten-, Objekt- oder Funktionsdefinition oder den Prototyp enthält, wobei die Compileroption ["Listendateityp"](fa-fa-listing-file.md) auf Assembly mit Source Code (**/FAs**) festgelegt ist.

   Geben Sie `cl /c /FAs example.cpp` beispielsweise eine Eingabeaufforderung für den Entwicklerbefehl ein, um eine Auflistungsdatei zu generieren, example.asm.

2. Suchen Sie in der ausgegebenen Auflistungsdatei die Zeile, die mit „PUBLIC“ beginnt und mit einem Semikolon endet, gefolgt vom nicht ergänzten Daten- oder Funktionsnamen. Das Symbol zwischen „PUBLIC“ und dem Semikolon ist der ergänzte Name.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Verwenden von DUMPBIN zum Anzeigen von ergänzten Namen

1. Um die exportierten Symbole in einer .obj- oder .lib-Datei anzuzeigen, geben Sie `dumpbin /symbols` `objfile` eine Entwicklereingabeeingabe ein.

2. Um das ergänzte Format eines Symbols zu finden, suchen Sie nach dem nicht ergänzten Namen in Klammern. Der dekorierte Name befindet sich in derselben Zeile, nach einem Rohrzeichen (&#124;) und vor dem nicht dekorierten Namen.

## <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Anzeigen nicht dekorierter Namen

Mit „undname.exe“ können Sie einen ergänzten Namen in das nicht ergänzte Format konvertieren. Dieses Beispiel zeigt, wie dies funktioniert:

```
C:\>undname ?func1@a@@AAEXH@Z
Microsoft (R) C++ Name Undecorator
Copyright (C) Microsoft Corporation. All rights reserved.

Undecoration of :- "?func1@a@@AAEXH@Z"
is :- "private: void __thiscall a::func1(int)"
```

## <a name="see-also"></a>Siehe auch

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)<br/>
[Verwenden von "extern" zur Angabe der Verknüpfung](../../cpp/using-extern-to-specify-linkage.md)
