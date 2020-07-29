---
title: 'Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler'
description: Veranschaulicht, wie die Code Analyse mit Microsoft C++ in Visual Studio verwendet wird.
ms.date: 04/14/2020
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.openlocfilehash: 65da18f5f6d1972276f1cb8e306e82314282e40a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227711"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Exemplarische Vorgehensweise: Analysieren von C/C++-Code auf Fehler

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie C/C++-Code auf potenzielle Code Fehler analysieren. Es verwendet die Code Analysetools für C/C++-Code.

In dieser exemplarischen Vorgehensweise gehen Sie wie folgt vor:

- Ausführen der Code Analyse für nativen Code.
- Analysieren von Code Fehler Warnungen.
- Behandeln Sie die Warnung als Fehler.
- Kommentieren Sie den Quellcode, um die Code Fehleranalyse zu verbessern.

## <a name="prerequisites"></a>Voraussetzungen

- Eine Kopie des [CppDemo](../code-quality/demo-sample.md)-Beispiels.
- Grundlegendes Verständnis von C/C++.

## <a name="run-code-analysis-on-native-code"></a>Ausführen der Code Analyse für nativen Code

### <a name="to-run-code-defect-analysis-on-native-code"></a>So führen Sie die Code Fehleranalyse für nativen Code aus

::: moniker range=">=vs-2019"

1. Öffnen Sie die CppDemo-Projekt Mappe in Visual Studio.

     Die CppDemo-Lösung füllt nun **Projektmappen-Explorer**auf.

1. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **neu erstellen**aus.

     Die Lösung wird ohne Fehler oder Warnungen erstellt.

1. Wählen Sie in **Projektmappen-Explorer**das Projekt codemängel aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Codedefekte-Eigenschaften Seiten** wird angezeigt.

1. Wählen Sie die Eigenschaften Seite **Code Analyse** aus.

1. Ändern Sie die Eigenschaft **Code Analyse für Build aktivieren** in **Ja**. Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Erstellen Sie das Projekt "codemängel" neu.

     Code Analyse Warnungen werden im Fenster **Fehlerliste** angezeigt.

::: moniker-end

::: moniker range="<=vs-2017"

1. Öffnen Sie die CppDemo-Projekt Mappe in Visual Studio.

     Die CppDemo-Lösung füllt nun **Projektmappen-Explorer**auf.

1. Wählen Sie im Menü **Erstellen** die Option Projekt Mappe **neu erstellen**aus.

     Die Lösung wird ohne Fehler oder Warnungen erstellt.

     > [!NOTE]
     > In Visual Studio 2017 wird möglicherweise eine falsche Warnung `E1097 unknown attribute "no_init_all"` in der IntelliSense-Engine angezeigt. Sie können diese Warnung problemlos ignorieren.

1. Wählen Sie in **Projektmappen-Explorer**das Projekt codemängel aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Codedefekte-Eigenschaften Seiten** wird angezeigt.

1. Wählen Sie die Eigenschaften Seite **Code Analyse** aus.

1. Aktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** . Klicken Sie auf **OK**, um die Änderungen zu speichern.

1. Erstellen Sie das Projekt "codemängel" neu.

     Code Analyse Warnungen werden im Fenster **Fehlerliste** angezeigt.

::: moniker-end

### <a name="to-analyze-code-defect-warnings"></a>So analysieren Sie Code Fehler Warnungen

1. Wählen Sie im Menü **Ansicht** die Option **Fehlerliste**aus.

     Dieses Menü Element ist möglicherweise nicht sichtbar. Dies hängt von dem Entwickler Profil ab, das Sie in Visual Studio ausgewählt haben. Möglicherweise müssen Sie auf **andere Fenster** im Menü **Ansicht** zeigen und dann auf **Fehlerliste**klicken.

1. Doppelklicken Sie im Fenster **Fehlerliste** auf die folgende Warnung:

     C6230: Implizite Umwandlung zwischen semantisch unterschiedlichen Typen: HRESULT wird in einem Boolean-Kontext verwendet.

     Der Code-Editor zeigt die Zeile an, die die Warnung in der Funktion verursacht hat `bool ProcessDomain()` . Diese Warnung gibt an, dass eine- `HRESULT` Anweisung in einer if-Anweisung verwendet wird, in der ein boolesches Ergebnis erwartet wird. Dies ist in der Regel ein Fehler, denn wenn das `S_OK` HRESULT von einer Funktion zurückgegeben wird, gibt es einen Erfolg an, aber wenn es in einen booleschen Wert konvertiert wird, wird es als ausgewertet **`false`** .

1. Korrigieren Sie diese Warnung, indem Sie das- `SUCCEEDED` Makro verwenden, das in konvertiert wird, **`true`** Wenn ein `HRESULT` Rückgabewert einen Erfolg angibt. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (SUCCEEDED(ReadUserAccount()))
   ```

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     C6282: Falscher Operator: Zuweisung einer Konstanten im booleschen Kontext. Verwenden Sie stattdessen "= =".

1. Korrigieren Sie diese Warnung, indem Sie auf Gleichheit testen. Der Code sollte in etwa wie der folgende Code aussehen:

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
   ```

1. Korrigieren Sie die verbleibenden C6001-Warnungen im **Fehlerliste** `i` , indem `j` Sie und auf 0 (null) initialisieren.

1. Erstellen Sie das Projekt "codemängel" neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

## <a name="correct-source-code-annotation-warnings"></a>Korrekte Warnungen der Quell Code Anmerkung

### <a name="to-enable-the-source-code-annotation-warnings-in-annotationc"></a>So aktivieren Sie die Warnungen der Quell Code Anmerkung in der Anmerkung. c

::: moniker range=">=vs-2019"

1. Wählen Sie in Projektmappen-Explorer das Projekt Annotations aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Annotations-Eigenschaften Seiten** wird angezeigt.

1. Wählen Sie die Eigenschaften Seite **Code Analyse** aus.

1. Ändern Sie die Eigenschaft **Code Analyse für Build aktivieren** in **Ja**. Klicken Sie auf **OK**, um die Änderungen zu speichern.

::: moniker-end

::: moniker range="<=vs-2017"

1. Wählen Sie in Projektmappen-Explorer das Projekt Annotations aus.

1. Klicken Sie im Menü **Projekt** auf **Eigenschaften**.

     Das Dialogfeld **Annotations-Eigenschaften Seiten** wird angezeigt.

1. Wählen Sie die Eigenschaften Seite **Code Analyse** aus.

1. Aktivieren Sie das Kontrollkästchen **Code Analyse bei Build aktivieren** . Klicken Sie auf **OK**, um die Änderungen zu speichern.

::: moniker-end

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>So korrigieren Sie die Warnungen der Quell Code Anmerkung in der Anmerkung. c

1. Erstellen Sie das Projekt Annotations neu.

1. Wählen Sie im Menü **Erstellen** die Option **Code Analyse für Anmerkungen ausführen aus**.

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     C6011: dereferenzierender NULL-Zeiger "newNode".

     Diese Warnung weist darauf hin, dass der Aufrufer den Rückgabewert nicht überprüfen konnte. In diesem Fall kann ein-Rückruf `AllocateNode` einen NULL-Wert zurückgeben. Weitere Informationen zur Funktionsdeklaration für finden Sie in der Annotations. h-Header Datei `AllocateNode` .

1. Der Cursor befindet sich an der Position in der Datei "Annotations. cpp", in der die Warnung aufgetreten ist.

1. Um diese Warnung zu korrigieren, verwenden Sie eine if-Anweisung, um den Rückgabewert zu testen. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   LinkedList* newNode = AllocateNode();
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

1. Erstellen Sie das Projekt Annotations neu.

     Das Projekt wird ohne Warnungen oder Fehler erstellt.

## <a name="use-source-code-annotation-to-discover-more-issues"></a>Verwenden Sie die Quell Code Anmerkung, um weitere Probleme zu ermitteln.

### <a name="to-use-source-code-annotation"></a>So verwenden Sie die Quell Code Anmerkung

1. Kommentieren Sie formale Parameter und den Rückgabewert der Funktion `AddTail` , um anzugeben, dass die Zeiger Werte möglicherweise NULL sind:

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

1. Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.

1. Doppelklicken Sie im **Fehlerliste**auf die folgende Warnung:

     C6011: dereferenzierender NULL-Zeiger "Node".

     Diese Warnung gibt an, dass der an die Funktion eingeführte Knoten NULL sein kann.

1. Um diese Warnung zu korrigieren, verwenden Sie eine if-Anweisung am Anfang der Funktion, um den bestandenen Wert zu testen. Der Code sollte dem folgenden Code ähneln:

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

1. Wählen Sie im Menü **Build** die Option **Codeanalyse für Lösung ausführen** aus.

     Das Projekt wird jetzt ohne Warnungen oder Fehler erstellt.

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Analysieren von verwaltetem Code auf Code Fehler](/visualstudio/code-quality/walkthrough-analyzing-managed-code-for-code-defects)\
[Codeanalyse für C/C++](../code-quality/code-analysis-for-c-cpp-overview.md)
