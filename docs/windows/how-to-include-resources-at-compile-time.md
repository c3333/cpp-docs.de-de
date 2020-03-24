---
title: 'Gewusst wie: einschließen von Ressourcen zur KompilierC++Zeit ()'
ms.date: 02/14/2019
f1_keywords:
- vs.resvw.resource.including
- vc.resvw.resource.including
- vc.editors.resourceincludes
helpviewer_keywords:
- comments [C++], compiled files
- resources [C++], including at compile time
- projects [C++], including resources
- '#include directive'
- include directive (#include)
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
- directories [C++], specifying include paths for resources
- include files [C++], specifying for resources
- resources [C++], including in projects
- symbols [C++], finding
- resources [C++], searching for symbols
ms.assetid: 357e93c2-0a29-42f9-806f-882f688b8924
ms.openlocfilehash: e931a0246340e81049df6ed0f8e26a4b91b570c7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215191"
---
# <a name="how-to-include-resources-at-compile-time-c"></a>Gewusst wie: einschließen von Ressourcen zur KompilierC++Zeit ()

Standardmäßig befinden sich alle Ressourcen in einer Ressourcen Skriptdatei (. RC), es gibt jedoch viele Gründe, Ressourcen in einer anderen Datei als der RC-Hauptdatei zu platzieren:

- Zum Hinzufügen von Kommentaren zu Ressourcen Anweisungen, die beim Speichern der RC-Datei nicht gelöscht werden.

- Zum Einbeziehen von Ressourcen, die bereits entwickelt und getestet wurden und keine weiteren Änderungen erfordern. Alle Dateien, die enthalten sind, aber keine RC-Erweiterung haben, können nicht von den Ressourcen-Editoren bearbeitet werden.

- Zum Einschließen von Ressourcen, die von verschiedenen Projekten verwendet werden, oder die Teil eines Quell Code Versionskontrollsystems sind. Diese Ressourcen müssen an einem zentralen Ort vorhanden sein, an dem sich Änderungen auf alle Projekte auswirken.

- Zum Einschließen von Ressourcen (z. b. RCDATA-Ressourcen), die ein benutzerdefiniertes Format aufweisen. RCDATA-Ressourcen haben besondere Anforderungen, wenn Sie einen Ausdruck nicht als Wert für das `nameID` Feld verwenden können.

Wenn Sie Abschnitte in Ihren vorhandenen RC-Dateien haben, die eine dieser Bedingungen erfüllen, platzieren Sie diese Abschnitte in einer oder mehreren separaten RC-Dateien, und fügen Sie Sie in das Projekt ein, indem Sie das Dialogfeld " **Ressourcenincludes** " verwenden.

## <a name="resource-includes"></a>Ressourcenincludes

Sie können dem Projekt zum Zeitpunkt der Kompilierung Ressourcen aus anderen Dateien hinzufügen, indem Sie Sie im Feld **Kompilierzeit Direktiven** im Dialogfeld **Ressourcenincludes** auflisten. Verwenden Sie das Dialogfeld **Ressourcenincludes** , um die normale Arbeits Anordnung der Projektumgebung zu ändern, in der alle Ressourcen in der Project. RC-Datei gespeichert werden, und alle [Symbole](../windows/symbols-resource-identifiers.md) in `Resource.h`.

Um zu beginnen, öffnen Sie das Dialogfeld " **Ressourcenincludes** ", indem Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf eine RC-Datei klicken, " **Ressource enthält** " und die folgenden Eigenschaften beachten:

| Eigenschaft | BESCHREIBUNG |
|---|---|
| **Symbol Header Datei** | Ermöglicht das Ändern des Namens der Header Datei, in der Symbol Definitionen für Ihre Ressourcen Dateien gespeichert werden.<br/><br/>Weitere Informationen finden Sie unter [Ändern der Namen von Symbol Headerdateien](../windows/changing-the-names-of-symbol-header-files.md). |
| **Schreibgeschützte Symbol Direktiven** | Ermöglicht das Einschließen von Header Dateien, die Symbole enthalten, die nicht geändert werden sollen.<br/><br/>Beispielsweise Symbol Dateien, die für andere Projekte freigegeben werden sollen. Dies kann auch MFC. h-Dateien einschließen. Weitere Informationen finden Sie unter [einschließen gemeinsamer (Schreib geschützter) oder berechneter Symbole](../windows/including-shared-read-only-or-calculated-symbols.md). |
| **Kompilierzeit Direktiven** | Ermöglicht das Einschließen von Ressourcen Dateien, die separat von den Ressourcen in der Hauptressourcen Datei erstellt und bearbeitet werden, Kompilierzeit Direktiven (z. b. die Direktiven, die Ressourcen bedingt enthalten) enthalten oder Ressourcen in einem benutzerdefinierten Format enthalten.<br/><br/>Sie können auch das **Feld Kompilierzeit Direktiven** verwenden, um Standard-MFC-Ressourcen Dateien einzuschließen. |

> [!NOTE]
> Einträge in diesen Textfeldern werden in der RC-Datei angezeigt, die durch `TEXTINCLUDE 1`, `TEXTINCLUDE 2`bzw. `TEXTINCLUDE 3` gekennzeichnet ist. Weitere Informationen finden Sie unter [TN035: Verwenden mehrerer Ressourcen Dateien und Header Dateien mit Visual C++ ](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Sobald Änderungen an ihrer Ressourcen Datei über das Dialogfeld " **Ressourcen enthält** " vorgenommen werden, müssen Sie die *RC* -Datei schließen und erneut öffnen, damit die Änderungen wirksam werden.

### <a name="to-include-resources-in-your-project-at-compile-time"></a>So beziehen Sie Ressourcen In Ihr Projekt zum Zeitpunkt der Kompilierung ein

1. Platzieren Sie die Ressourcen in einer Ressourcenskriptdatei mit einem eindeutigen Dateinamen. Verwenden Sie *ProjectName. RC*nicht, da dies der Name der Datei ist, die für die Hauptressourcen Skriptdatei verwendet wird.

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources) mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **Ressource enthält**.

1. Fügen Sie im Feld **Kompilierzeit Direktiven** die [#include](../preprocessor/hash-include-directive-c-cpp.md) -Compilerdirektive hinzu, um die neue Ressourcen Datei in der Hauptressourcen Datei in der Entwicklungsumgebung einzubeziehen.

Die Ressourcen in Dateien, die auf diese Weise eingeschlossen werden, werden nur zur Kompilierzeit Teil der ausführbaren Datei und können nicht bearbeitet oder geändert werden, wenn Sie an der Haupt-RC-Datei Ihres Projekts arbeiten. Enthaltene RC-Dateien müssen separat geöffnet werden, und alle Dateien, die ohne die RC-Erweiterung enthalten sind, können nicht von den Ressourcen-Editoren bearbeitet werden.

### <a name="to-specify-include-directories-for-a-specific-resource-rc-file"></a>So geben Sie Includeverzeichnisse für eine bestimmte Ressourcen Datei (RC-Datei) an

1. Klicken Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie **Eigenschaften**.

1. Wählen Sie im linken Bereich den Knoten **Ressourcen** aus, und geben Sie in der Eigenschaft **Zusätzliche Includeverzeichnisse** weitere Includeverzeichnisse an.

### <a name="to-find-symbols-in-resources"></a>So suchen Sie Symbole in Ressourcen

1. Wechseln Sie zu Menü **Bearbeiten** > [Symbol suchen](/visualstudio/ide/go-to).

   > [!TIP]
   > Um [reguläre Ausdrücke](/visualstudio/ide/using-regular-expressions-in-visual-studio) in der Suche zu verwenden, wählen Sie im Menü **Bearbeiten** anstelle von **Symbol**suchen die Option [in Dateien suchen](/visualstudio/ide/reference/find-command) aus. Aktivieren Sie das Kontrollkästchen **reguläre Ausdrücke verwenden** im [Dialogfeld Suchen](/visualstudio/ide/finding-and-replacing-text) , und wählen Sie **im Feld Suchen** nach einen regulären Such Ausdruck aus der Dropdown Liste aus. Wenn Sie einen Ausdruck aus dieser Liste auswählen, wird dieser als Suchtext **im Feld Suchen** nach ersetzt.

1. Wählen Sie im Feld **Suchen** nach eine vorherige Such Zeichenfolge aus der Dropdown Liste aus, oder geben Sie die gewünschte Zugriffstaste ein, z. b. `ID_ACCEL1`.

1. Wählen Sie **eine der Suchoptionen aus** , und klicken Sie auf **weiter suchen**.

> [!NOTE]
> Die Suche nach Symbolen in Zeichenfolgen-, Zugriffstasten- oder Binärressourcen wird nicht unterstützt.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcendateien](../windows/resource-files-visual-studio.md)<br/>
[Vorgehensweise: Erstellen von Ressourcen](../windows/how-to-create-a-resource-script-file.md)<br/>
[Gewusst wie: Verwalten von Ressourcen](../windows/how-to-copy-resources.md)<br/>
