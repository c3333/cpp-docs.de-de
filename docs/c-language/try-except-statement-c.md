---
title: try-except-Anweisung (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: 2ca5299a5ab20b8985a520f25bb654ead0c25e2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349743"
---
# <a name="try-except-statement-c"></a>try-except-Anweisung (C)

**Microsoft Specific**

Die **try-except**-Anweisung ist eine Microsoft-Erweiterung zur Programmiersprache C, mit deren Hilfe Anwendungen bei Ereignissen, die normalerweise zur Beendigung eines Programms führen, die Steuerung des Programms übernehmen können. Diese Ereignisse werden als Ausnahmen bezeichnet, und der Mechanismus, der die Ausnahmen behandelt, wird als strukturierte Ausnahmebehandlung bezeichnet.

Ausnahmen können entweder hardware- oder softwarebasiert sein. Auch wenn Anwendungen nicht von Hardware- oder Softwareausnahmen vollständig wiederhergestellt werden können, kann die strukturierte Ausnahmebehandlung das Anzeigen von Fehlerinformationen ermöglichen und den internen Zustand der Anwendung abfangen, um das Problem zu diagnostizieren. Dies ist besonders hilfreich bei zeitweilig auftretenden Problemen, die nicht leicht reproduziert werden können.

## <a name="syntax"></a>Syntax

*try-except-statement*: **__try**  *compound-statement*

**__except (**  *Ausdruck*  **)**  *zusammengesetzte Anweisung*

Die Verbundanweisung nach der `__try`-Klausel ist der abgesicherte Abschnitt. Die Verbundanweisung nach der `__except`-Klausel ist der Ausnahmehandler. Der Handler gibt eine Reihe von Aktionen an, die abgerufen werden, wenn eine Ausnahme während der Ausführung des geschützten Abschnitts ausgelöst wird. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Wenn keine Ausnahme während der Ausführung des geschützten Bereichs auftritt, wird die Ausführung mit der Anweisung nach der `__except`-Klausel fortgesetzt.

1. Wenn während der Ausführung des geschützten Abschnitts oder in einer Routine, die der geschützte Abschnitt aufruft, eine Ausnahme auftritt, wird der `__except`-Ausdruck ausgewertet, und der Rückgabewert bestimmt, wie die Ausnahme verarbeitet wird. Es gibt drei Werte:

   `EXCEPTION_CONTINUE_SEARCH` Ausnahme wurde nicht erkannt. Fahren Sie fort, im Stapel nach einem Handler zu suchen, zuerst nach enthaltenen **try-except**-Anweisungen, dann nach Handlern mit der nächst höheren Priorität.

   `EXCEPTION_CONTINUE_EXECUTION` Ausnahme wird erkannt, wird jedoch geschlossen. Fortsetzen der Ausführung an der Stelle, an der die Ausnahme aufgetreten ist.

   `EXCEPTION_EXECUTE_HANDLER` Ausnahme wurde erkannt. Übertragen Sie die Steuerung an den Ausnahmehandler, indem Sie die `__except`-Verbundanweisung ausführen und anschließend die Ausführung an dem Punkt fortsetzen, an dem die Ausnahme aufgetreten ist.

Da der `__except`-Ausdruck als C-Ausdruck ausgewertet wird, wird er auf einen Einzelwert beschränkt, den Operator des bedingten Ausdrucks oder den Komma-Operator. Wenn eine erweiterte Verarbeitung erforderlich ist, kann der Ausdruck eine Routine aufrufen, die einen der drei Werte zurückgibt, die oben aufgelistet sind.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit C- und C++-Quelldateien. Sie ist jedoch nicht speziell für C++ entwickelt. Sie können sicherstellen, dass der Code portabler ist, indem Sie die C++-Ausnahmebehandlung verwenden. Der C++-Ausnahmebehandlungsmechanismus ist außerdem viel flexibler, da er Ausnahmen eines beliebigen Typs behandeln kann.

> [!NOTE]
> Für C++-Programme sollte die C++-Ausnahmebehandlung anstelle der strukturierten Ausnahmebehandlung verwendet werden. Weitere Informationen finden Sie unter [Ausnahmebehandlung](../cpp/exception-handling-in-visual-cpp.md) in *C++-Sprachreferenz*.

Jede Routine in einer Anwendung kann einen eigenen Ausnahmehandler aufweisen. Der `__except`-Ausdruck wird im Bereich des `__try`-Rumpfes ausgeführt. Dies bedeutet, dass alle lokalen Variablen verfügbar sind, die dort deklariert wurden.

Das `__leave`-Schlüsselwort ist innerhalb eines **try-except**-Anweisungsblocks gültig. Der Effekt von `__leave` besteht darin, zum Ende des **try-except**-Blocks zu springen. Die Ausführung wird nach dem Ende des Ausnahmehandlers fortgesetzt. Obwohl das gleiche Ergebnis mit einer `goto`-Anweisung erreicht werden kann, verursacht eine `goto`-Anweisung eine Stapelentladung. Die `__leave`-Anweisung ist effizienter, da sie keine Stapelentladung verursacht.

Eine **try-except**-Anweisung unter Verwendung der `longjmp`-Laufzeitfunktion zu beenden, wird als nicht ordnungsgemäße Beendigung angesehen. Es ist nicht zulässig, in eine `__try`-Anweisung zu springen, wohingegen das Herausspringen aus einer solchen zulässig ist. Der Ausnahmehandler wird nicht aufgerufen, wenn ein Vorgang in der Mitte der Ausführung einer **try-except**-Anweisung beendet wird.

## <a name="example"></a>Beispiel

Nachfolgend erhalten Sie ein Beispiel für einen Ausnahmehandler und einen Beendigungshandler. Weitere Informationen zu Beendigungshandlern finden Sie unter [try-finally-Anweisung](../c-language/try-finally-statement-c.md).

```
.
.
.
puts("hello");
__try{
   puts("in try");
   __try{
      puts("in try");
      RAISE_AN_EXCEPTION();
   }__finally{
      puts("in finally");
   }
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){
   puts("in except");
}
puts("world");
```

Dies ist die Ausgabe des Beispiels. Rechts wurde ein Kommentar hinzugefügt:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**END Microsoft Spezifisch**

## <a name="see-also"></a>Siehe auch

[try-except-Anweisung](../cpp/try-except-statement.md)
