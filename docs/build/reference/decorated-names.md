---
title: Ergänzte Namen
ms.date: 09/05/2018
helpviewer_keywords:
- decorated names, definition
- name decoration [C++]
- names [C++], decorated
ms.assetid: a4e9ae8e-b239-4454-b401-4102793cb344
ms.openlocfilehash: 20e7f5855b771caf23217e5c17db50a890e28113
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223849"
---
# <a name="decorated-names"></a>Ergänzte Namen

Funktionen, Daten und Objekte werden in C- und C++-Programmen intern durch ihre ergänzten Namen dargestellt. Ein ergänzte *Name* ist eine codierte Zeichenfolge, die vom Compiler während der Kompilierung eines Objekts, einer Daten-oder Funktionsdefinition erstellt wurde. Er zeichnet Aufrufkonventionen, Typen, Funktionsparameter und sonstige Informationen zusammen mit dem Namen auf. Diese namens Ergänzung, auch bekannt als *Name-Zerlegung*, unterstützt den Linker beim Verknüpfen einer ausführbaren Datei bei der Suche nach den richtigen Funktionen und Objekten.

Die ergänzten Benennungs Konventionen haben sich in verschiedenen Versionen von Visual Studio geändert und können sich auch in verschiedenen Ziel Architekturen unterscheiden. Um ordnungsgemäß mit Quelldateien zu verknüpfen, die mit Visual Studio erstellt wurden, sollten C-und C++-DLLs und-Bibliotheken mit dem gleichen Compilertoolset, den gleichen Flags und der Zielarchitektur kompiliert werden.

> [!NOTE]
> Bibliotheken, die mit Visual Studio 2015 erstellt wurden, können von Anwendungen genutzt werden, die mit Visual Studio 2017 oder Visual Studio 2019 erstellt wurden.

## <a name="using-decorated-names"></a><a name="Using"></a>Verwenden von ergänzten Namen

In der Regel müssen Sie den ergänzten Namen nicht kennen, um Code schreiben zu können, der erfolgreich kompiliert werden kann und richtige Verknüpfungen aufweist. Ergänzte Namen sind ein internes Implementierungsdetail des Compilers und Linkers. Die Tools können den Name in der Regel auch in seiner nicht ergänzten Form behandeln. Ein ergänzter Name ist jedoch manchmal erforderlich, wenn Sie einen Funktionsnamen zum Linker oder anderen Tools angeben. Um zum Beispiel überladene C++-Funktionen, Member von Namespaces, Klassenkonstruktoren, Destruktoren und spezielle Memberfunktionen angeben zu können, müssen Sie den ergänzten Namen verwenden. Weitere Informationen zu den Optionskennzeichnungen und anderen Situationen, in denen ergänzte Namen erforderlich sind, finden Sie in der Dokumentation zu den von Ihnen verwendeten Tools und Optionen.

Wenn Sie den Funktionsnamen, die Klasse, die Aufrufkonvention, den Rückgabetyp oder einen Parameter ändern, ändert sich auch der ergänzte Name. In diesem Fall müssen Sie den neuen ergänzten Namen abrufen und ihn überall dort verwenden, wo der ergänzte Name angegeben ist.

Die Namensergänzung ist auch dann wichtig, wenn eine Verknüpfen mit Code erfolgt, der in einer anderen Programmiersprache geschrieben wurde oder andere Compiler verwendet. Verschiedene Compilern verwenden unterschiedliche Konventionen für die Namensergänzung. Wenn Ihre ausführbare Datei eine Verknüpfung zu Code enthält, der in einer anderen Sprache geschrieben wurde, müssen Sie insbesondere darauf achten, dass die exportierten und importierten Namen und Aufrufkonventionen übereinstimmen. Der assemblysprachencode muss die MSVC-ergänzten Namen und Aufruf Konventionen verwenden, um einen Link zu einem mit MSVC geschriebenen Quellcode zu verknüpfen

## <a name="format-of-a-c-decorated-name"></a><a name="Format"></a>Format eines ergänzten Namens C++

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

## <a name="format-of-a-c-decorated-name"></a><a name="FormatC"></a>Format eines von C ergänzten Namens

Das Format einer Ergänzung für eine C-Funktion hängt von der Aufrufkonvention ab, die in der Deklaration verwendet wird. Dies isst in der folgenden Tabelle dargestellt. Dies ist auch das Ergänzungsformat, das verwendet wird, wenn C++-Code mit einer `extern "C"` Verknüpfung deklariert wird. Die Standard Aufruf Konvention ist **`__cdecl`** . Beachten Sie, dass Funktion in einer 64-Bit-Umgebung nicht ergänzt werden.

|Aufrufkonvention|Dekoration|
|------------------------|----------------|
|**`__cdecl`**|Führender Unterstrich ( **`_`** )|
|**`__stdcall`**|Führender Unterstrich ( **`_`** ) und ein nach gestelltes at-Zeichen ( **`@`** ), gefolgt von der Anzahl der Bytes in der Parameterliste in Dezimal|
|**`__fastcall`**|Vorangestellte und nachfolgende Zeichen ( **`@`** ) gefolgt von einer Dezimalzahl, die die Anzahl der Bytes in der Parameterliste darstellt.|
|**`__vectorcall`**|Zwei nachfolgende @-Zeichen ( **`@@`** ), gefolgt von einer Dezimalzahl von Bytes in der Parameterliste|

## <a name="viewing-decorated-names"></a><a name="Viewing"></a>Anzeigen von ergänzten Namen

Sie erhalten das ergänzte Format eines Symbolnamens, wenn Sie die Quelldatei mit den Daten, dem Objekt oder der Funktionsdefinition bzw. dem Prototypen kompiliert haben. Um ergänzte Namen im Programm zu untersuchen, können Sie eine der folgenden Methoden verwenden:

#### <a name="to-use-a-listing-to-view-decorated-names"></a>Verwenden einer Auflistung zum Anzeigen ergänzter Namen

1. Generieren Sie eine Auflistung, indem Sie die Quelldatei mit den Daten, dem Objekt oder der Funktionsdefinition oder dem Prototyp mit der Compileroption " [Auflisten des Datentyps](fa-fa-listing-file.md) " auf Assembly mit Quellcode (**/FAS**) kompilieren.

   Geben Sie z. b. `cl /c /FAs example.cpp` an einer Developer-Eingabeaufforderung ein, um eine Listen Datei zu generieren, z. b. asm.

2. Suchen Sie in der ausgegebenen Auflistungsdatei die Zeile, die mit „PUBLIC“ beginnt und mit einem Semikolon endet, gefolgt vom nicht ergänzten Daten- oder Funktionsnamen. Das Symbol zwischen „PUBLIC“ und dem Semikolon ist der ergänzte Name.

#### <a name="to-use-dumpbin-to-view-decorated-names"></a>Verwenden von DUMPBIN zum Anzeigen von ergänzten Namen

1. Wenn Sie die exportierten Symbole in einer obj-oder LIB-Datei anzeigen möchten, geben Sie `dumpbin /symbols` `objfile` an einer Developer-Eingabeaufforderung ein.

2. Um das ergänzte Format eines Symbols zu finden, suchen Sie nach dem nicht ergänzten Namen in Klammern. Der ergänzte Name befindet sich in der gleichen Zeile, nach einem Pipe-Zeichen (&#124;) und vor dem nicht ergänzten Namen.

## <a name="viewing-undecorated-names"></a><a name="Undecorated"></a>Anzeigen von nicht ergänzten Namen

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
