---
title: try-except-Anweisung (C)
description: Microsoft C/C++ implementiert die strukturierte Ausnahmebehandlung (Structured Exception Handling, SEH) über eine Spracherweiterung für die try-except-Anweisung.
ms.date: 08/24/2020
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: e327150431fef3384f2b98940939444b2e6d96ea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898726"
---
# <a name="try-except-statement-c"></a>try-except-Anweisung (C)

**Microsoft-spezifisch**

Die `try-except`-Anweisung ist eine Microsoft-Erweiterung zur Programmiersprache C, mit deren Hilfe Anwendungen bei Ereignissen, die normalerweise zur Beendigung eines Programms führen, die Steuerung des Programms übernehmen können. Diese Ereignisse werden als Ausnahmen bezeichnet, und der Mechanismus, der die Ausnahmen behandelt, wird als strukturierte Ausnahmebehandlung bezeichnet.

Ausnahmen können hardware-oder softwarebasiert sein. Auch wenn Anwendungen nach Hardware- oder Softwareausnahmen möglicherweise nicht vollständig wiederhergestellt werden können, ermöglicht die strukturierte Ausnahmebehandlung das Anzeigen und Protokollieren von Fehlerinformationen. So lässt sich der interne Zustand der Anwendung ermitteln, um das Problem zu diagnostizieren. Dies ist besonders hilfreich bei vorübergehend auftretenden Problemen, die sich nicht ohne Weiteres reproduzieren lassen.

## <a name="syntax"></a>Syntax

> *`try-except-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__except (`**  *`expression`*  **`)`** *`compound-statement`*

Die Verbundanweisung nach der **`__try`** -Klausel ist der *geschützte Abschnitt*. Die Verbundanweisung nach der **`__except`** -Klausel ist der *Ausnahmehandler*. Der Handler gibt eine Reihe von Aktionen an, die ausgeführt werden, wenn während der Ausführung des geschützten Abschnitts eine Ausnahme ausgelöst wird. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Wenn während der Ausführung des geschützten Bereichs keine Ausnahme auftritt, wird die Ausführung mit der Anweisung nach der **`__except`** -Klausel fortgesetzt.

1. Wenn während der Ausführung des geschützten Abschnitts oder in einer vom geschützten Abschnitt aufgerufenen Routine eine Ausnahme auftritt, wird der **`__except`** -Ausdruck ausgewertet. Der Rückgabewert bestimmt, wie die Ausnahme behandelt wird. Es gibt drei mögliche Werte:

   - `EXCEPTION_CONTINUE_SEARCH`: Die Ausnahme wird nicht erkannt. Fahren Sie fort, im Stapel nach einem Handler zu suchen, zuerst nach enthaltenen `try-except`-Anweisungen, dann nach Handlern mit der nächst höheren Priorität.

   - `EXCEPTION_CONTINUE_EXECUTION`: Die Ausnahme wird erkannt, aber verworfen. Fortsetzen der Ausführung an der Stelle, an der die Ausnahme aufgetreten ist.

   - `EXCEPTION_EXECUTE_HANDLER` Die Ausnahme wird erkannt. Übertragen Sie die Steuerung an den Ausnahmehandler, indem Sie die **`__except`** -Verbundanweisung ausführen und anschließend die Ausführung an dem Punkt fortsetzen, an dem die Ausnahme aufgetreten ist.

Da der **`__except`** -Ausdruck als C-Ausdruck ausgewertet wird, ist er auf einen einzelnen Wert, den bedingten Ausdrucksoperator oder den Kommaoperator beschränkt. Wenn eine erweiterte Verarbeitung erforderlich ist, kann der Ausdruck eine Routine aufrufen, die einen der drei Werte zurückgibt, die oben aufgelistet sind.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit C- und C++-Quelldateien. Sie wurde jedoch nicht speziell für C++ entwickelt. Für portierbare C++-Programme sollte die C++-Ausnahmebehandlung anstelle der strukturierten Ausnahmebehandlung verwendet werden. Der C++-Ausnahmebehandlungsmechanismus ist außerdem viel flexibler, da er Ausnahmen eines beliebigen Typs behandeln kann. Weitere Informationen finden Sie unter [Ausnahmebehandlung](../cpp/exception-handling-in-visual-cpp.md) in der *C++-Sprachreferenz*.

Jede Routine in einer Anwendung kann einen eigenen Ausnahmehandler aufweisen. Der **`__except`** -Ausdruck wird im Bereich des **`__try`** -Blocks ausgeführt. Er kann auf alle dort deklarierten lokalen Variablen zugreifen.

Das Schlüsselwort **`__leave`** ist innerhalb eines `try-except`-Anweisungsblocks gültig. Der Zweck von **`__leave`** besteht darin, zum Ende des `try-except`-Blocks zu springen. Die Ausführung wird nach dem Ende des Ausnahmehandlers fortgesetzt. Zwar kann dasselbe Ergebnis mit einer **`goto`** -Anweisung erzielt werden, eine **`goto`** -Anweisung verursacht jedoch eine Stapelentladung. Die **`__leave`** -Anweisung ist effizienter, weil sie keine Stapelentladung verursacht.

Die Beendigung einer `try-except`-Anweisung unter Verwendung der Laufzeitfunktion `longjmp` gilt als nicht ordnungsgemäße Beendigung. Es ist nicht zulässig, in eine **`__try`** -Anweisung zu springen, wohingegen das Herausspringen aus einer solchen zulässig ist. Der Ausnahmehandler wird nicht aufgerufen, wenn ein Prozess während der Ausführung einer `try-except`-Anweisung beendet wird.

## <a name="example"></a>Beispiel

Hier sehen Sie ein Beispiel für einen Ausnahmehandler und einen Beendigungshandler. Weitere Informationen zu Beendigungshandlern finden Sie unter [`try-finally`-Anweisung (C)](../c-language/try-finally-statement-c.md).

```C
.
.
.
puts("hello");
__try {
   puts("in try");
   __try {
      puts("in try");
      RAISE_AN_EXCEPTION();
   } __finally {
      puts("in finally");
   }
} __except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ) {
   puts("in except");
}
puts("world");
```

Hier sehen Sie ist die Ausgabe des Beispiels mit Kommentaren:

```Output
hello
in try              /* fall into try                        */
in try              /* fall into nested try                 */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**ENDE der Microsoft-spezifischen Informationen**

## <a name="see-also"></a>Siehe auch

[`try-except`-Anweisung (C++)](../cpp/try-except-statement.md)
