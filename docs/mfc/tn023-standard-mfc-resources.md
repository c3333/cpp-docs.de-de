---
title: 'TN023: MFC-Standardressourcen'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- TN023
- standard resources
ms.assetid: 60af8415-c576-4c2f-a711-ca5da0b9a1f2
ms.openlocfilehash: 90e7b9b7c354ba919c3dee279725b4498bea57ff
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370383"
---
# <a name="tn023-standard-mfc-resources"></a>TN023: MFC-Standardressourcen

In diesem Hinweis werden die Standardressourcen beschrieben, die von der MFC-Bibliothek bereitgestellt und benötigt werden.

## <a name="standard-resources"></a>Standardressourcen

MFC bietet zwei Kategorien vordefinierter Ressourcen, die Sie in Ihrer Anwendung verwenden können: ClipArt-Ressourcen und Standardframeworkressourcen.

ClipArt-Ressourcen sind zusätzliche Ressourcen, von denen das Framework nicht abhängig ist, die Sie der Benutzeroberfläche Ihrer Anwendung hinzufügen möchten. Die folgenden ClipArt-Ressourcen sind im MFC General-Beispiel [CLIPART](../overview/visual-cpp-samples.md)enthalten:

- Common.rc: Eine einzelne Datei mit Ressourcen, die enthält:

  - Eine große Sammlung von Symbolen, die eine Vielzahl von Geschäfts- und Datenverarbeitungsaufgaben darstellen.

  - Mehrere gängige Cursor (siehe auch Afxres.rc).

  - Eine Symbolleisten-Bitmap, die mehrere Symbolleistenschaltflächen enthält.

  - Die Bitmap- und Symbolressourcen, die von Commdlg.dll verwendet werden.

- Indicate.rc: Enthält Zeichenfolgenressourcen für die Statusleisten-Schlüsselstatusindikatoren, z. B. "CAP" für Caps Lock.

- Prompts.rc: Enthält Menü-Eingabeaufforderungszeichenfolgenressourcen für jeden vordefinierten Befehl, z. B. "Erstellen eines neuen Dokuments" für ID_FILE_NEW.

- Commdlg.rc: Eine Visual C++-kompatible .rc-Datei, die die standardmäßigen COMMDLG-Dialogvorlagen enthält.

Standardframeworkressourcen sind Ressourcen mit AFX-definierten IDs, von denen der Framework für interne Implementierungen abhängt. Sie müssen diese AFX-definierten Ressourcen nur selten ändern. In diesem Artikel sollten Sie das unten beschriebene Verfahren befolgen.

Die folgenden Frameworkressourcen sind im Verzeichnis MFC-INCLUDE enthalten:

- Afxres.rc: Gemeinsame Ressourcen, die vom Framework verwendet werden.

- Afxprint.rc: Druckspezifische Ressourcen.

- Afxolecl.rc: Ressourcen, die für OLE-Clientanwendungen spezifisch sind.

- Afxolev.rc: Ressourcen, die für vollständige OLE-Serveranwendungen spezifisch sind.

## <a name="using-clip-art-resources"></a>Verwenden von ClipArt-Ressourcen

#### <a name="to-use-a-clip-art-binary-resource"></a>So verwenden Sie eine Binärressource für ClipArt

1. Öffnen Sie die Ressourcendatei Ihrer Anwendung in Visual C++.

1. Öffnen Sie Common.rc. Diese Datei enthält alle binären ClipArt-Ressourcen. Dies kann einige Zeit in Anspruch nehmen, da die Datei Common.rc kompiliert wird.

1. Halten Sie STRG gedrückt, während Sie die Ressourcen, die Sie von Common.rc verwenden möchten, in die Ressourcendatei Ihrer Anwendung ziehen.

Um andere ClipArt-Ressourcen zu verwenden, führen Sie die gleichen Schritte aus. Der einzige Unterschied ist, dass Sie die entsprechende .rc-Datei anstelle von Common.rc öffnen.

> [!NOTE]
> Achten Sie darauf, Ressourcen nicht unbeabsichtigt dauerhaft aus Common.rc zu verschieben. Wenn Sie die STRG-Taste gedrückt halten, während Sie Ressourcen ziehen, erstellen Sie eine Kopie. Wenn Sie STRG während des Ziehens nicht gedrückt halten, werden die Ressourcen verschoben. Wenn Sie befürchten, dass Sie versehentlich Änderungen an der Datei Common.rc vorgenommen haben, klicken Sie auf "Nein", wenn Sie gefragt werden, ob die Änderungen in Common.rc gespeichert werden sollen.

> [!NOTE]
> Die .rc-Ressourcendateien haben eine spezielle TEXTINCLUDE-Ressource, die Sie daran hindert, versehentlich über den Standard-.rc-Dateien zu speichern.

### <a name="customizing-standard-framework-resources"></a>Anpassen von Standardframeworkressourcen

Standardframeworkressourcen werden in der Regel in einer Anwendung mithilfe des Befehls #include in der Ressourcendatei einer Anwendung enthalten. AppWizard generiert eine Ressourcendatei. Diese Datei enthält die entsprechenden Standardframeworkressourcen, je nachdem, welche AppWizard-Optionen Sie auswählen. Sie können überprüfen, hinzufügen oder entfernen, welche Ressourcen enthalten sind, indem Sie die Kompilierungszeitdirektiven ändern. Öffnen Sie dazu das **Menü Ressourcen,** und wählen Sie **"Einschließen"** aus. Sehen Sie sich das Bearbeitungselement "Compile-Time Directives" an. Beispiel:

```
#include "afxres.rc"
#include "afxprint.rc"
```

Der häufigste Fall beim Anpassen von Standardframeworkressourcen besteht darin, zusätzliche Includes für Drucken, OLE Client und OLE Server-Unterstützung hinzuzufügen oder zu entfernen.

In einigen seltenen Fällen möchten Sie möglicherweise den Inhalt der Standardframeworkressourcen für Ihre jeweilige Anwendung anpassen und nicht nur die gesamte Datei hinzufügen und entfernen. Die folgenden Schritte zeigen, wie Sie die enthaltenen Ressourcen einschränken können:

##### <a name="to-customize-the-contents-of-a-standard-resource-file"></a>So passen Sie den Inhalt einer Standardressourcendatei an

1. Öffnen Sie die Ressourcendatei in Visual C++.

1. Entfernen Sie mit dem Befehl `#include` Ressourcensatz-Includes die für die Standard-..rc-Datei, die Sie anpassen möchten. Entfernen Sie beispielsweise die `#include "afxprint.rc"` Zeile, um die Symbolleiste für die Druckvorschau anzupassen.

1. Öffnen Sie die entsprechenden Standardressourcendateien in MFC-INCLUDE. Im Folgenden zu dem vorherigen Beispiel in diesem Thema lautet die entsprechende Datei MFC-Include-Aafxprint.rc

1. Kopieren Sie alle Ressourcen aus der Standard-.-.rc-Datei in Ihre Anwendungsressourcendatei.

1. Ändern Sie die Kopie der Standardressourcen in der Anwendungsressourcendatei.

> [!NOTE]
> Ändern Sie die Ressourcen nicht direkt in den Standard-..rc-Dateien. Dadurch werden die Ressourcen geändert, die in jeder Anwendung verfügbar sind, nicht nur in der, an der Sie gerade arbeiten.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
