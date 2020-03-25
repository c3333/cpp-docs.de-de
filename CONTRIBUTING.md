---
ms.openlocfilehash: e2b88bb1c60c97c9f63caacfb98ba87e0443e799
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509440"
---
# <a name="contributing"></a>Beitragen

Vielen Dank für Ihr Interesse und Ihre Bereitschaft, an der Visual C++-Dokumentation mitzuwirken!

In diesem Thema wird die grundsätzliche Vorgehensweise beschrieben, wie Inhalte zur [Visual C++-Dokumentationswebsite](https://docs.microsoft.com/cpp) hinzugefügt oder aktualisiert werden können.

In diesem Thema werden folgende Punkte behandelt:

* [Mitwirkungsprozess](#process-for-contributing)
* [Verhaltensregeln](#dos-and-donts)
* [Erstellen der Dokumente](#building-the-docs)
* [Mitwirken an Beispielen](#contributing-to-samples)
* [Lizenzvereinbarung für Mitwirkende](#contributor-license-agreement)

## <a name="process-for-contributing"></a>Mitwirkungsprozess

**Schritt 1:** Öffnen Sie ein Problem (Ticket), in dem Sie sowohl den Artikel beschreiben, den Sie schreiben möchten, als auch, wie er mit vorhandenem Inhalt zusammenhängt.
Der Inhalt im Ordner **docs** ist in Abschnitte unterteilt, die nach Inhaltsbereichen (z. B. Debugger) strukturiert sind. Versuchen Sie, den richtigen Ordner für Ihren neuen Inhalt zu ermitteln. Warten Sie auf Feedback zu Ihrem Vorschlag.

Für kleine Änderungen können Sie diesen ersten Schritt überspringen.

**Schritt 2:** Forken Sie das `MicrosoftDocs/cpp-docs`-Repository.

**Schritt 3:** Erstellen Sie ein `branch` für Ihren Artikel.

**Schritt 4:** Schreiben Sie Ihren Artikel.

Wenn es sich um ein neues Thema handelt, können Sie diese [Vorlagendatei](./styleguide/template.md) als Ausgangspunkt verwenden. Sie enthält die Richtlinien zum Schreiben und erläutert auch die Metadaten, die für jeden Artikel erforderlich sind (z. B. Informationen zum Autor).

Navigieren Sie zu dem Ordner, welcher der Stelle im Inhaltsverzeichnis entspricht, die Sie in Schritt 1 für Ihren Artikel festgelegt haben.
Dieser Ordner enthält die Markdowndateien für alle Artikel in diesem Abschnitt. Erstellen Sie ggf. einen neuen Ordner für die Dateien mit Ihrem Inhalt.

Wenn Sie Bilder und andere statische Ressourcen haben, fügen Sie diese zum Unterordner `media` hinzu. Wenn Sie einen neuen Ordner für Inhalte erstellen, fügen Sie diesem neuen Ordner einen „media“-Ordner hinzu.

Achten Sie darauf, die richtige Markdownsyntax einzuhalten. Weitere Informationen finden Sie im [Styleguide](./styleguide/template.md).

### <a name="example-structure"></a>Beispielstruktur

```
docs
    /standard-library
        wstring-convert-class.md
        /media
            wstring-conversion.png
```

**Schritt 5:** Übermitteln Sie einen Pull Request (PR) von Ihrem Branch an `MicrosoftDocs/cpp-docs/master`.

Wenn sich Ihr PR auf ein vorhandenes Problem bezieht, fügen Sie der Commit-Nachricht oder PR-Beschreibung das Schlüsselwort `Fixes #Issue_Number` hinzu, damit das Problem automatisch geschlossen werden kann, wenn der PR eingebunden wird. Weitere Informationen finden Sie unter [Closing issues via commit messages](https://help.github.com/articles/closing-issues-via-commit-messages/) (Schließen von Tickets mithilfe von Commit-Nachrichten).

Das Visual Studio-Team überprüft Ihren PR und teilt Ihnen mit, ob die Änderung in Ordnung geht oder ob für die Genehmigung noch weitere Aktualisierungen/Änderungen erforderlich sind.

**Schritt 6:** Nehmen Sie, wie mit dem Team besprochen, alle erforderlichen Aktualisierungen in Ihrem Branch vor.

Nachdem das Feedback angewendet und die Änderung als in Ordnung eingestuft wurde, führen die Verwalter Ihren PR mit dem Master-Branch zusammen.

In einem bestimmten Rhythmus übertragen wir alle Commits mithilfe von Push aus dem Master-Branch in den Live-Branch. Dann können Sie Ihren Beitrag live auf [docs.microsoft.com](https://docs.microsoft.com/cpp/) sehen.

## <a name="dos-and-donts"></a>Verhaltensregeln

Es folgt eine kurze Liste mit Anleitungsregeln, die Sie beachten sollten, wenn Sie an der .NET-Dokumentation mitwirken.

- **NEIN**: Überraschen Sie uns nicht mit umfangreichen Pull Requests. Eröffnen Sie stattdessen ein Ticket, und starten Sie eine Diskussion, damit wir uns auf eine Richtung einigen können, bevor Sie sehr viel Zeit investieren.
- **JA** Lesen Sie den [Styleguide](./styleguide/template.md) und die Richtlinien bezüglich [Sprache und Schreibstil](./styleguide/voice-tone.md).
- **JA** Verwenden Sie die [Vorlagendatei](./styleguide/template.md) als Ausgangspunkt für Ihre Arbeit.
- **JA** Erstellen Sie einen separaten Branch in Ihrer Verzweigung, bevor Sie an den Artikeln arbeiten.
- **JA** Folgen Sie dem [GitHub-Flow-Workflow](https://guides.github.com/introduction/flow/).
- **JA** Schreiben Sie häufig Blogs und Tweets (oder was auch immer) über Ihre Beiträge!

> [!NOTE]
> Sie stellen möglicherweise fest, dass sich derzeit einige der Themen nicht nach allen hier und im [Styleguide](./styleguide/template.md) definierten Richtlinien richten. Wir arbeiten daran, auf der gesamten Website Konsistenz zu erzielen. Überprüfen Sie in der Liste [open issues](https://github.com/MicrosoftDocs/cpp-docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) die offenen Tickets, die wir derzeit für dieses spezielle Ziel verfolgen.

## <a name="building-the-docs"></a>Erstellen der Dokumente

Die Dokumentation wird in [GitHub Flavored Markdown](https://help.github.com/categories/writing-on-github/) geschrieben und mit [DocFX](https://dotnet.github.io/docfx/) und anderen internen Veröffentlichungs-/Erstellungstools erstellt. Sie wird in [docs.microsoft.com](https://docs.microsoft.com/) gehostet.

Wenn Sie die Dokumente lokal erstellen möchten, müssen Sie [DocFX](https://dotnet.github.io/docfx/) installieren, wobei die neueste Versionen am besten geeignet ist.

Es gibt mehrere Möglichkeiten, DocFX zu verwenden, und die meisten dieser Möglichkeiten sind unter [Getting Started with DocFX](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html) beschrieben. In den folgenden Anweisungen wird die [befehlszeilenbasierte](https://dotnet.github.io/docfx/tutorial/docfx_getting_started.html#2-use-docfx-as-a-command-line-tool) Version des Tools verwendet. Wenn Sie mit anderen Möglichkeiten vertraut sind, die unter dem obigen Link aufgeführt sind, können Sie diese verwenden.

**Hinweis**: Derzeit ist für DocFX das .NET Framework für Windows oder Mono (für Linux oder macOS) erforderlich. Es ist geplant, dies zukünftig in .NET Core zu portieren.

Sie können die resultierende Website lokal über einen integrierten Webserver erstellen und in der Vorschau anzeigen. Navigieren Sie zum Ordner `cpp-docs\docs` auf Ihrem Computer, und geben Sie den folgenden Befehl ein:

> docfx -t default --serve

Hiermit wird die lokale Vorschau für [localhost:8080](http://localhost:8080) gestartet. Sie können dann die Änderungen anzeigen, indem Sie zu `http://localhost:8080/[path]` wechseln, z. B. `http://localhost:8080/cpp/visual-cpp-in-visual-studio.html`.

**Hinweis:** Die lokale Vorschau enthält derzeit keine Designs, sodass deren Aussehen und Verhalten momentan nicht mit dem in der Dokumentationswebsite identisch ist. Wir arbeiten daran, diesen Zustand zu beseitigen. Für eingebettete Videos, Hinweise und angefügte Dokumente (die in der Vorschau nicht zu sehen sind) verwenden wir benutzerdefinierte Erweiterungen.

## <a name="contributing-to-samples"></a>Mitwirken an Beispielen

Fügen Sie erforderlichen Beispielcode beim jetzigen Stand als Inlinecodeblöcke in Ihren Artikel ein. Das Repository hat einen `codesnippets`-Ordner, dieser ist aber noch nicht für öffentliche Beiträge geeignet.

## <a name="contributor-license-agreement"></a>Lizenzvereinbarung für Mitwirkende

Sie müssen die [Lizenzvereinbarung für Mitwirkende (Contribution License Agreement, CLA)](LICENSE) unterzeichnen, bevor Ihr Pull Request zusammengeführt wird. Dies ist eine einmalige Anforderung für Projekte auf docs.microsoft.com. Auf Wikipedia erfahren Sie mehr über [Contributor License Agreements (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement).

Sie brauchen die Vereinbarung nicht vorab zu unterzeichnen. Sie können Ihren Pull Request wie gewohnt klonen, verzweigen und übermitteln. Beim Erstellen Ihres Pull Requests wird dieser von einem CLA-Bot klassifiziert. Wenn die Änderung geringfügig ist (z. B. Korrigieren eines Tippfehlers), wird der Pull Request mit der Bezeichnung „CLA-not-required“ versehen. Andernfalls wird er als „CLA-required“ klassifiziert. Nachdem Sie das CLA unterzeichnet haben, werden die aktuellen und alle zukünftigen Pull Requests mit der Bezeichnung „CLA-signed“ versehen.
