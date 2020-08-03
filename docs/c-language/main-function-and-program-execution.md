---
title: main-Funktion und Programmausführung
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: f2419820fb6018613fe3fae39194584076121898
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211787"
---
# <a name="main-function-and-program-execution"></a>main-Funktion und Programmausführung

Jedes C-Programm verfügt über eine primäre Funktion (main), die mit **main** benannt werden muss. Wenn der Code dem Unicode-Programmiermodell entspricht, können Sie die Breitzeichenversion von **main**, **wmain**, verwenden. Die **main**-Funktion ist der Ausgangspunkt für die Programmausführung. Es steuert in der Regel die Programmausführung durch Verweisen der Aufrufe an andere Funktionen im Programm. Ein Programm hält normalerweise die Ausführung am Ende von **main** an, obwohl es an anderen Punkten im Programm aus mehreren Gründen beendet werden kann. Manchmal sollten Sie u. U. die Beendigung eines Programms erzwingen, wenn ein bestimmter Fehler erkannt wird. Verwenden Sie dazu die **exit**-Funktion. Weitere Informationen und ein Beispiel für die Verwendung der [exit](../c-runtime-library/reference/exit-exit-exit.md)-Funktion finden Sie in der *Laufzeitbibliotheksreferenz*.

## <a name="syntax"></a>Syntax

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Hinweise

Funktionen innerhalb des Quellprogramms führen eine oder mehrere bestimmte Aufgaben aus. Die **main**-Funktion ruft diese Funktionen auf, um die jeweiligen Aufgaben auszuführen. Wenn **main** eine andere Funktion aufruft, übergibt sie die Ablaufsteuerung an die Funktion, sodass die Ausführung bei der ersten Anweisung in der Funktion beginnt. Eine Funktion gibt die Steuerung an **main** zurück, wenn eine **`return`** -Anweisung ausgeführt wird, oder wenn das Ende der Funktion erreicht ist.

Sie können beliebige Funktionen, einschließlich **main** mit Parametern deklarieren. Der Begriff "Parameter" oder "formaler Parameter" bezieht sich auf den Bezeichner, der einen Wert empfängt, der an eine Funktion übergeben wird. Informationen zum Übergeben von Argumenten an Parameter finden Sie unter [Parameter](../c-language/parameters.md). Wenn eine Funktion eine andere Funktion aufruft, empfängt die aufgerufene Funktion Werte für ihre Parameter von der aufrufenden Funktion. Diese Werte werden als „Argumente“ bezeichnet. Sie können formale Parameter für **main** so deklarieren, dass es mit diesem Format Argumente in der Befehlszeile empfangen kann:

Wenn Sie Informationen an die **main**-Funktion übergeben möchten, werden die Parameter in der Regel `argc` und `argv` genannt, obwohl der C-Compiler diese Namen nicht benötigt. Die Typen für `argc` und `argv` werden von der Programmiersprache C definiert. Normalerweise wird bei Übergabe eines dritten Parameters an **main** der betreffende Parameter `envp` benannt. Beispiele weiter unten in diesem Abschnitt beschrieben, wie diese drei Parameter verwendet werden können, um auf Befehlszeilenargumente zuzugreifen. Diese Parameter werden in den folgenden Abschnitten erläutert.

Eine Beschreibung der Breitzeichenversion von **main** finden Sie unter [Verwenden von wmain](../c-language/using-wmain.md).

## <a name="see-also"></a>Siehe auch

[main-Funktion und Befehlszeilenargumente (C++)](../cpp/main-function-command-line-args.md)\
[Analysieren von C-Befehlszeilenargumenten](../c-language/parsing-c-command-line-arguments.md)
