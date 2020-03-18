---
title: 'Exemplarische Vorgehensweise: analysierenC++ von C/Code auf Fehler'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: 5fbdf9e223b3c1e1b8664de2018381958c458f45
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467066"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Exemplarische Vorgehensweise: analysierenC++ von C/Code auf Fehler

In dieser exemplarischen Vorgehensweise wird veranschaulicht,C++ wie c/Code mit dem Code Analysetool für C/C++ Code auf potenzielle Code Fehler analysiert wird.

- Ausführen der Code Analyse für nativen Code.
- Analysieren von Code Fehler Warnungen.
- Behandeln Sie die Warnung als Fehler.
- Kommentieren Sie den Quellcode, um die Code Fehleranalyse zu verbessern.

## <a name="prerequisites"></a>Voraussetzungen

- Eine Kopie des [Demo](../code-quality/demo-sample.md)Beispiels.
- Grundlegendes Verständnis von CC++/.

### <a name="to-run-code-defect-analysis-on-native-code"></a>So führen Sie die Code Fehleranalyse für nativen Code aus

1. Öffnen Sie die Demo Projekt Mappe in Visual Studio.

     Die Demo Lösung füllt nun **Projektmappen-Explorer**auf.

1. Klicken Sie im Menü **Build** auf **Projektmappe neu erstellen**.

     Die Lösung wird ohne Fehler oder Warnungen erstellt.

1. Wählen Sie in **Projektmappen-Explorer**das Projekt codemängel aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Codedefekte-Eigenschaften Seiten** wird angezeigt.

1. Klicken Sie auf **Codeanalyse**.

1. Aktivieren Sie das Kontrollkästchen **Code Analyse fürC++ C/on-Build aktivieren** .

1. Erstellen Sie das Projekt "codemängel" neu.

     Code Analyse Warnungen werden in der **Fehlerliste**angezeigt.

### <a name="to-analyze-code-defect-warnings"></a>So analysieren Sie Code Fehler Warnungen

1. Klicken Sie im Menü **Ansicht** auf **Fehlerliste**.

     Abhängig vom Entwickler Profil, das Sie in Visual Studio ausgewählt haben, müssen Sie möglicherweise im Menü **Ansicht** auf **andere Fenster** zeigen und dann auf **Fehlerliste**klicken.

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warning C6230: Implizite Umwandlung zwischen semantisch unterschiedlichen Typen: HRESULT wird in einem Boolean-Kontext verwendet.

     Im Code-Editor wird die Zeile, die die Warnung verursacht hat, im `bool ProcessDomain()`der Funktion angezeigt. Diese Warnung gibt an, dass eine `HRESULT` in einer if-Anweisung verwendet wird, in der ein boolesches Ergebnis erwartet wird.  Dies ist in der Regel ein Fehler, weil der `S_OK` HRESULT von der Funktion zurückgegeben wird, auf Erfolg hinweist, bei der Konvertierung in einen booleschen Wert jedoch zu `false`.

1. Korrigieren Sie diese Warnung, indem Sie das `SUCCEEDED`-Makro verwenden, das in `true` konvertiert, wenn ein `HRESULT` Rückgabewert Erfolg angibt. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warning C6282: Falscher Operator: Zuweisung zu konstanter im Test Kontext. Was = = beabsichtigt?

1. Korrigieren Sie diese Warnung, indem Sie auf Gleichheit testen. Der Code sollte in etwa wie der folgende Code aussehen:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>So behandeln Sie die Warnung als Fehler

1. Fügen Sie in der Datei Bug. cpp am Anfang der Datei die folgende `#pragma`-Anweisung hinzu, um die Warnung C6001 als Fehler zu behandeln:

   ```cpp
   #pragma warning (error: 6001)
   ```

1. Erstellen Sie das Projekt "codemängel" neu.

     Im **Fehlerliste**wird C6001 jetzt als Fehler angezeigt.

1. Korrigieren Sie die verbleibenden zwei C6001-Fehler im **Fehlerliste** , indem Sie `i` initialisieren und auf 0 `j`.

1. Erstellen Sie das Projekt "codemängel" neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>So korrigieren Sie die Warnungen der Quell Code Anmerkung in der Anmerkung. c

1. Wählen Sie in Projektmappen-Explorer das Projekt Annotations aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Annotations-Eigenschaften Seiten** wird angezeigt.

1. Klicken Sie auf **Codeanalyse**.

1. Aktivieren Sie das Kontrollkästchen **Code Analyse fürC++ C/on-Build aktivieren** .

1. Erstellen Sie das Projekt Annotations neu.

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warnung C6011: dereferenzierender NULL-Zeiger "newNode".

     Diese Warnung weist darauf hin, dass der Aufrufer den Rückgabewert nicht überprüfen konnte. In diesem Fall kann ein Rückruf von " **Zuordnungs-Ode** " einen NULL-Wert zurückgeben (Weitere Informationen finden Sie in der Annotations. h-Header Datei für die Funktionsdeklaration für "zustellerode")

1. Öffnen Sie die Datei "Annotations. cpp".

1. Um diese Warnung zu korrigieren, verwenden Sie eine if-Anweisung, um den Rückgabewert zu testen. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Erstellen Sie das Projekt Annotations neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

### <a name="to-use-source-code-annotation"></a>So verwenden Sie die Quell Code Anmerkung

1. Kommentieren Sie formale Parameter und den Rückgabewert der Funktion `AddTail`, um anzugeben, dass die Zeiger Werte möglicherweise NULL sind:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Projekt zum erneuten Erstellen von Anmerkungen.

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     Warnung C6011: dereferenzierender NULL-Zeiger "Node".

     Diese Warnung gibt an, dass der an die Funktion eingegebene Knoten NULL sein kann, und gibt die Nummer der Zeile an, in der die Warnung ausgelöst wurde.

1. Um diese Warnung zu korrigieren, verwenden Sie eine if-Anweisung am Anfang der Funktion, um den bestandenen Wert zu testen. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Projekt zum erneuten Erstellen von Anmerkungen.

     Das Projekt wird jetzt ohne Warnungen oder Fehler erstellt.

## <a name="see-also"></a>Weitere Informationen

Exemplarische Vorgehensweise [: Analysieren von verwaltetem Code auf Code Fehler](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Code Analyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
