---
title: 'Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler'
description: Veranschaulicht, wie die Codeanalyse mit Microsoft C++ in Visual Studio verwendet wird.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: fe9b3775199b2a18cf940b99e87852350f1fbea9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370213"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie C/C++-Code auf potenzielle Codefehler analysiert wird. Es verwendet die Codeanalysetools für C/C++-Code.

In dieser exemplarischen Vorgehensweise finden Sie:

- Führen Sie die Codeanalyse für systemeigenen Code aus.
- Analysieren Sie Codefehlerwarnungen.
- Behandeln Sie die Warnung als Fehler.
- Kommentieren Sie den Quellcode, um die Codefehleranalyse zu verbessern.

## <a name="prerequisites"></a>Voraussetzungen

- Eine Kopie des [CppDemo-Beispiels](../code-quality/demo-sample.md).
- Grundlegendes Verständnis von C/C++.

## <a name="run-code-analysis-on-native-code"></a>Ausführen der Codeanalyse für systemeigenen Code

### <a name="to-run-code-defect-analysis-on-native-code"></a>So führen Sie die Codefehleranalyse für systemeigenen Code aus

::: moniker range=">=vs-2019"

1. Öffnen Sie die CppDemo-Lösung in Visual Studio.

     Die CppDemo-Lösung füllt jetzt den **Projektmappen-Explorer**.

1. Wählen Sie im Menü **Erstellen** die Option **Lösung neu erstellen**aus.

     Die Lösung erstellt ohne Fehler oder Warnungen.

1. Wählen Sie im **Projektmappen-Explorer**das CodeDefects-Projekt aus.

1. Wählen Sie im Menü **Projekt** **Eigenschaften**aus.

     Das Dialogfeld **CodeDefects Property Pages** wird angezeigt.

1. Wählen Sie die Eigenschaftenseite **Codeanalyse** aus.

1. Ändern Sie die **Eigenschaft Codeanalyse für Build aktivieren** in **Ja**. Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Erstellen Sie das CodeDefects-Projekt neu.

     Codeanalysewarnungen werden im Fenster **Fehlerliste** angezeigt.

::: moniker-end

::: moniker range="<=vs-2017"

1. Öffnen Sie die CppDemo-Lösung in Visual Studio.

     Die CppDemo-Lösung füllt jetzt den **Projektmappen-Explorer**.

1. Wählen Sie im Menü **Erstellen** die Option **Lösung neu erstellen**aus.

     Die Lösung erstellt ohne Fehler oder Warnungen.

     > [!NOTE]
     > In Visual Studio 2017 wird möglicherweise `E1097 unknown attribute "no_init_all"` eine falsche Warnung im IntelliSense-Modul angezeigt. Sie können diese Warnung problemlos ignorieren.

1. Wählen Sie im **Projektmappen-Explorer**das CodeDefects-Projekt aus.

1. Wählen Sie im Menü **Projekt** **Eigenschaften**aus.

     Das Dialogfeld **CodeDefects Property Pages** wird angezeigt.

1. Wählen Sie die Eigenschaftenseite **Codeanalyse** aus.

1. Aktivieren Sie das Kontrollkästchen **Codeanalyse unter Build aktivieren.** Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Erstellen Sie das CodeDefects-Projekt neu.

     Codeanalysewarnungen werden im Fenster **Fehlerliste** angezeigt.

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>So analysieren Sie Codefehlerwarnungen

1. Wählen Sie im Menü **Ansicht** **Die Option Fehlerliste**aus.

     Dieses Menüelement ist möglicherweise nicht sichtbar. Dies hängt vom Entwicklerprofil ab, das Sie in Visual Studio ausgewählt haben. Möglicherweise müssen Sie im Menü **Ansicht** auf **andere Windows** zeigen und dann **Fehlerliste**auswählen.

1. Doppelklicken Sie im Fenster **Fehlerliste** auf die folgende Warnung:

     C6230: Implizite Umwandlung zwischen semantisch unterschiedlichen Typen: Verwendung von HRESULT in einem booleschen Kontext.

     Der Code-Editor zeigt die Zeile an, die die Warnung innerhalb der Funktion `bool ProcessDomain()`verursacht hat. Diese Warnung gibt `HRESULT` an, dass eine in einer "if"-Anweisung verwendet wird, in der ein boolesches Ergebnis erwartet wird. Es ist in der Regel `S_OK` ein Fehler, denn wenn das HRESULT von einer Funktion zurückgegeben wird, zeigt es Erfolg an, aber wenn es in einen booleschen Wert konvertiert wird, wird es in `false`ausgewertet.

1. Korrigieren Sie diese `SUCCEEDED` Warnung mithilfe des `true` Makros, das in den Zeitpunkt konvertiert wird, an dem ein `HRESULT` Rückgabewert auf Erfolg hinweist. Ihr Code sollte dem folgenden Code ähneln:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. Doppelklicken Sie in der **Fehlerliste**auf die folgende Warnung:

     C6282: Falscher Operator: Zuweisung einer Konstante im booleschen Kontext. Erwägen Sie stattdessen die Verwendung von '=='.

1. Korrigieren Sie diese Warnung, indem Sie die Gleichheit testen. Ihr Code sollte dem folgenden Code ähnlich aussehen:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Korrigieren Sie die verbleibenden C6001-Warnungen `j` in der **Fehlerliste,** indem Sie sie initialisieren `i` und auf 0.

1. Erstellen Sie das CodeDefects-Projekt neu.

     Das Projekt erstellt ohne Warnungen oder Fehler.

## <a name="correct-source-code-annotation-warnings"></a>Korrigieren von Quellcodeanmerkungswarnungen

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>So aktivieren Sie die Quellcodeanmerkungswarnungen in annotation.c

::: moniker range=">=vs-2019"

1. Wählen Sie im Projektprojektprojekt Projekt Annotations aus.

1. Wählen Sie im Menü **Projekt** **Eigenschaften**aus.

     Das Dialogfeld **Annotations Property Pages** wird angezeigt.

1. Wählen Sie die Eigenschaftenseite **Codeanalyse** aus.

1. Ändern Sie die **Eigenschaft Codeanalyse für Build aktivieren** in **Ja**. Klicken Sie auf **OK**, um die Änderungen zu speichern.

::: moniker-end

::: moniker range="<=vs-2017"

1. Wählen Sie im Projektprojektprojekt Projekt Annotations aus.

1. Wählen Sie im Menü **Projekt** **Eigenschaften**aus.

     Das Dialogfeld **Annotations Property Pages** wird angezeigt.

1. Wählen Sie die Eigenschaftenseite **Codeanalyse** aus.

1. Aktivieren Sie das Kontrollkästchen **Codeanalyse unter Build aktivieren.** Klicken Sie auf **OK**, um die Änderungen zu speichern.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>So korrigieren Sie die Quellcodeanmerkungswarnungen in annotation.c

1. Erstellen Sie das Annotations-Projekt neu.

1. Wählen Sie im Menü **Erstellen** die Option **Codeanalyse für Anmerkungen**ausführen aus.

1. Doppelklicken Sie in der **Fehlerliste**auf die folgende Warnung:

     C6011: Verweis auf NULL-Zeiger 'newNode'.

     Diese Warnung weist darauf hin, dass der Aufrufer den Rückgabewert nicht überprüft. In diesem Fall kann `AllocateNode` ein Aufruf an einen NULL-Wert zurückgeben. Siehe die Headerdatei annotations.h für `AllocateNode`die Funktionsdeklaration für .

1. Der Cursor befindet sich an der Position in der Datei annotations.cpp, an der die Warnung aufgetreten ist.

1. Um diese Warnung zu korrigieren, verwenden Sie eine "if"-Anweisung, um den Rückgabewert zu testen. Ihr Code sollte dem folgenden Code ähneln:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Erstellen Sie das Annotations-Projekt neu.

     Das Projekt erstellt ohne Warnungen oder Fehler.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Verwenden von Quellcodeanmerkungen, um weitere Probleme zu ermitteln

### <a name="to-use-source-code-annotation"></a>So verwenden Sie Quellcodeanmerkungen

1. Kommentieren Sie formale Parameter und den `AddTail` Rückgabewert der Funktion, um anzugeben, dass die Zeigerwerte null sein können:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.

1. Doppelklicken Sie in der **Fehlerliste**auf die folgende Warnung:

     C6011: Verweis auf NULL-Zeiger 'Knoten'.

     Diese Warnung gibt an, dass der an die Funktion übergebene Knoten möglicherweise NULL ist.

1. Um diese Warnung zu korrigieren, verwenden Sie eine 'if'-Anweisung am Anfang der Funktion, um den übergebenen Wert zu testen. Ihr Code sollte dem folgenden Code ähneln:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.

     Das Projekt wird nun ohne Warnungen oder Fehler erstellt.

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Analysieren von verwaltetem Code für Codefehler](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Codeanalyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
