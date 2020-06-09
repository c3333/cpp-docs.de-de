---
title: Binär-Editor (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 955cce012ac30c3413d7d458e263643d0aefa711
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615351"
---
# <a name="binary-editor-c"></a>Binär-Editor (C++)

> [!CAUTION]
> Das Bearbeiten von Ressourcen, wie Dialogfeldern, Bildern oder Menüs im **binären Editor** , ist gefährlich. Eine falsche Bearbeitung kann zu einer Beschädigung der Ressource führen, sodass sie anschließend im systemeigenen Editor nicht mehr einsetzbar ist.

Der **Binäre Editor** ermöglicht es Ihnen, beliebige Ressourcen auf Binär Ebene im Hexadezimal-oder ASCII-Format zu bearbeiten. Außerdem können Sie mit dem [Suchbefehl](/visualstudio/ide/reference/find-command) ASCII-Zeichenfolgen oder hexadezimale Bytes suchen. Verwenden Sie den **Binär-Editor** nur, wenn Sie benutzerdefinierte Ressourcen oder Ressourcentypen anzeigen oder geringfügige Änderungen vornehmen müssen, die nicht von der Visual Studio-Umgebung unterstützt werden. Der **Binäre Editor** ist in Express-Editionen nicht verfügbar.

- Um den **Binär-Editor** für eine neue Datei zu öffnen, navigieren Sie zu Menu **File**  >  **New**  >  **File**, wählen Sie den Dateityp aus, den Sie bearbeiten möchten, und wählen Sie dann den Dropdown Pfeil neben der Schaltfläche **Öffnen** aus, und wählen Sie mit Binär- **Open With**  >  **Editor**öffnen aus.

- Um den **Binär-Editor** für eine vorhandene Datei zu öffnen, navigieren Sie zu Menü **Datei**  >  **Open**  >  **Datei**öffnen, wählen Sie die Datei aus, die Sie bearbeiten möchten, und wählen Sie dann den Dropdown Pfeil neben der Schaltfläche **Öffnen** aus, und wählen Sie mit Binär- **Open With**  >  **Editor**öffnen aus.

   ![Binär-Editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Binärdaten für ein Dialogfeld, das im **Binär-Editor** angezeigt wird

Nur bestimmte ASCII-Werte werden im **Binär-Editor** dargestellt (0x20 bis 0x7E). Erweiterte Zeichen werden als Zeiträume im rechten Bereich des ASCII-Werts im Binär- **Editor**angezeigt. Die druckbaren Zeichen sind die ASCII-Werte 32 bis 126.

> [!TIP]
> Wenn Sie den **binären Editor**verwenden, können Sie in vielen Fällen mit der rechten Maustaste klicken, um ein Kontextmenü mit Ressourcen spezifischen Befehlen anzuzeigen. Welche Befehle verfügbar sind, hängt von dem Element ab, auf das Sie mit dem Cursor zeigen. Wenn Sie z. b. mit der rechten Maustaste klicken, während Sie mit den ausgewählten hexadezimal Werten auf den **Binär-Editor** zeigen, werden im Kontextmenü die Befehle zum **Ausschneiden**, **Kopieren**und **Einfügen** angezeigt.

## <a name="how-to"></a>Vorgehensweise

Der **Binäre Editor** ermöglicht Ihnen Folgendes:

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>So öffnen Sie eine Windows-Desktopressource zur Binärbearbeitung

1. Wählen Sie in der [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)die bestimmte Ressourcendatei aus, die Sie bearbeiten möchten.

1. Klicken Sie mit der rechten Maustaste auf die Ressource, und wählen Sie **Binärdaten öffnen**

> [!NOTE]
> Wenn Sie das **Ressourcenansicht** Fenster verwenden, um eine Ressource in einem Format zu öffnen, das von Visual Studio nicht erkannt wird (z. b. RCDATA oder eine benutzerdefinierte Ressource), wird die Ressource automatisch im **Binär-Editor**geöffnet.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>So öffnen Sie eine verwaltete Ressource für die Binärbearbeitung

1. Wählen Sie in **Projektmappen-Explorer**die gewünschte Ressourcen Datei aus, die Sie bearbeiten möchten.

1. Klicken Sie mit der rechten Maustaste auf die Ressource, und wählen Sie **Öffnen mit**

1. Wählen Sie im Dialogfeld **Öffnen mit** den **Binär-Editor**aus.

> [!NOTE]
> Sie können die [Bild](image-editor-for-icons.md) Bearbeitung und den **Binär-Editor** verwenden, um mit Ressourcen Dateien in verwalteten Projekten zu arbeiten. Bei den zu bearbeitenden verwalteten Ressourcen muss es sich um verknüpfte Ressourcen handeln. Das Bearbeiten eingebetteter Ressourcen wird von den Visual Studio-Ressourcen-Editoren nicht unterstützt.

### <a name="to-edit-a-resource"></a>So bearbeiten Sie eine Ressource

Wenn Sie den **Binär-Editor** für eine Ressource verwenden möchten, die bereits in einem anderen Editor-Fenster bearbeitet wird, schließen Sie zuerst das andere Editor Fenster.

1. Wählen Sie das Byte aus, das Sie bearbeiten möchten.

   Mit der **Tab** -Taste wird der Fokus zwischen den Hexadezimal-und ASCII-Abschnitten des **Binär-Editors**verschoben. Sie können die Bild- **auf** -und Bild- **ab** -Taste verwenden, um jeweils einen Bildschirm durch die Ressource zu navigieren.

1. Geben Sie den neuen Wert ein.

   Der Wert ändert sich sofort in den hexadezimalen und ASCII-Abschnitten, und der Fokus wechselt auf den nächsten Wert in der Zeile.

> [!NOTE]
> Der **Binäre Editor** nimmt Änderungen automatisch an, wenn Sie den Editor schließen.

### <a name="to-find-binary-data"></a>So suchen Sie Binärdaten

Sie können entweder ASCII-Zeichen folgen oder hexadezimale Bytes suchen. Wenn Sie z. b. " *Hello*" finden möchten, können Sie entweder die Zeichenfolge *Hello* oder den Hexadezimalwert *48 65 6C 6C 6f*suchen.

1. Wechseln Sie zu Menü **Bearbeiten**  >  [Suchen](/visualstudio/ide/reference/find-command).

1. Wählen Sie im Feld **Suchen** nach eine vorherige Such Zeichenfolge aus der Dropdown Liste aus, oder geben Sie die Daten ein, die Sie suchen möchten.

1. Wählen Sie **eine der Suchoptionen aus** , und klicken Sie auf **weiter suchen**.

### <a name="to-create-a-new-custom-or-data-resource"></a>So erstellen Sie eine neue benutzerdefinierte oder Datenressource

Sie können eine neue benutzerdefinierte Ressource oder Daten Ressource erstellen, indem Sie die Ressource mithilfe der Datei Syntax des normalen Ressourcen Skripts (RC) in einer separaten Datei platzieren und diese Datei dann einschließen, indem Sie in **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt klicken und **Ressourcen einschließen**auswählen.

1. [Erstellen Sie eine RC-Datei](how-to-create-a-resource-script-file.md) , die die benutzerdefinierte oder Datenressource enthält.

   Sie können benutzerdefinierte Daten in einer RC-Datei als in Anführungszeichen eingeschlossene nullterminierte Zeichenfolgen oder als ganze Zahlen im dezimalen, hexadezimalen oder oktalen Format eingeben.

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf die RC-Datei Ihres Projekts, und wählen Sie **Ressource enthält**.

1. Geben Sie im Feld **Kompilierzeit Direktiven** eine-Anweisung ein, die `#include` den Namen der Datei mit der benutzerdefinierten Ressource enthält, z. b.:

    ```cpp
    #include mydata.rc
    ```

   Achten Sie auf die korrekte Syntax und Rechtschreibung Ihrer Eingaben. Der Inhalt des Felds **Kompilierzeit Direktiven** wird in die Ressourcen Skriptdatei genau so eingefügt, wie Sie Sie eingeben.

1. Wählen Sie **OK** aus, um Ihre Änderungen aufzuzeichnen.

Eine weitere Möglichkeit zum Erstellen einer benutzerdefinierten Ressource ist das Importieren einer externen Datei als benutzerdefinierte Ressource. Weitere Informationen finden Sie unter Gewusst [wie: Verwalten von Ressourcen](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Das Erstellen neuer benutzerdefinierter oder Datenressourcen erfordert Win32.

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Siehe auch

[Ressourcen-Editoren](resource-editors.md)
