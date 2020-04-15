---
title: Stapelverarbeitungsregeln
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- NMAKE program, inference rules
- batch-mode inference rules in NMAKE
ms.assetid: 0650b547-ef19-4455-9bba-fa567dcf88f2
ms.openlocfilehash: 38402e7b8a937cebb823ce13fa1ac01fc1099878
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328408"
---
# <a name="batch-mode-rules"></a>Stapelverarbeitungsregeln

```
{frompath}.fromext{topath}.toext::
   commands
```

Batchmodus-Rückschlussregeln stellen nur einen Aufruf der Rückschlussregel bereit, wenn N-Befehle diese Rückschlussregel durchlaufen. Ohne Batchmodus-Rückschlussregeln müssten N-Befehle aufgerufen werden. N ist die Anzahl der abhängigen Elemente, die die Rückschlussregel auslösen.

Makefiles, die Batchmodus-Einschlussregeln enthalten, müssen NMAKE Version 1.62 oder höher verwenden. Um die NMAKE-Version zu überprüfen, führen Sie das _NMAKE_VER Makro mit NMAKE Version 1.62 oder höher aus. Dieses Makro gibt eine Zeichenfolge zurück, die die Visual C++-Produktversion darstellt.

Der einzige syntaktische Unterschied zur Standard-Rückschlussregel besteht darin, dass die Batchmodus-Inferenzregel mit einem Doppelpunkt (::) beendet wird.

> [!NOTE]
> Das aufgerufene Tool muss in der Lage sein, mehrere Dateien zu verarbeiten. Die Batchmodus-Rückschlussregel muss `$<` als Makro verwendet werden, um auf abhängige Dateien zuzugreifen.

Die Batchmodus-Rückschlussregeln können den Buildprozess beschleunigen. Es ist schneller, Dateien im Batch an den Compiler zu übermitteln, da der Compilertreiber nur einmal aufgerufen wird. Beispielsweise führt der C- und C++-Compiler eine bessere Leistung bei der Verarbeitung einer Gruppe von Dateien, da er während des Prozesses speicherresident bleiben kann.

Das folgende Beispiel zeigt, wie Batchmodus-Rückschlussregeln verwendet werden:

```
#
# sample makefile to illustrate batch-mode inference rules
#
O = .
S = .
Objs = $O/foo1.obj $O/foo2.obj $O/foo2.obj $O/foo3.obj $O/foo4.obj
CFLAGS = -nologo

all : $(Objs)

!ifdef NOBatch
{$S}.cpp{$O}.obj:
!else
{$S}.cpp{$O}.obj::
!endif
   $(CC) $(CFLAGS) -Fd$O\ -c $<

$(Objs) :

#end of makefile
```

NMAKE erzeugt die folgende Ausgabe ohne Batch-Modus-Inferenzregeln:

```
E:\tmp> nmake -f test.mak -a NOBatch=1

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.
        cl -nologo -Fd.\ -c .\foo1.cpp
foo1.cpp
        cl -nologo -Fd.\ -c .\foo2.cpp
foo2.cpp
        cl -nologo -Fd.\ -c .\foo3.cpp
foo3.cpp
        cl -nologo -Fd.\ -c .\foo4.cpp
foo4.cpp
```

NMAKE liefert das folgende Ergebnis mit den Batch-Modus-Inferenzregeln:

```
E:\tmp> nmake -f test.mak -a

Microsoft (R) Program Maintenance Utility   Version 7.00.0000
Copyright (C) Microsoft Corp 1988-2001. All rights reserved.

        cl -nologo -Fd.\ -c .\foo1.cpp .\foo2.cpp .\foo3.cpp .\foo4.cpp
foo1.cpp
foo2.cpp
foo3.cpp
foo4.cpp
Generating Code...
```

## <a name="see-also"></a>Siehe auch

[Rückschlussregeln](inference-rules.md)
