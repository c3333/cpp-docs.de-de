---
title: 'Gewusst wie: Verwalten von RessourcenC++()'
ms.date: 02/14/2019
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
- vc.resvw.resource.changing
- vb.xmldesigner.data
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], moving between files
- resources [C++], copying
- resource files [C++], copying or moving resources between
- resource files [C++], tiling
- .rc files [C++], copying resources between
- rc files [C++], copying resources between
- Language property [C++]
- .resx files [C++], editing
- resource files [C++], editing
- resx files [C++], editing
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
ms.openlocfilehash: 718de310bc4fb0cb0072065bc4e7b7adadb182aa
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426576"
---
# <a name="how-to-manage-resources-c"></a>Gewusst wie: Verwalten von RessourcenC++()

## <a name="copy-and-edit-resources"></a>Kopieren und Bearbeiten von Ressourcen

Sie können Ressourcen aus einer Datei in eine andere Datei kopieren, ohne Sie zu ändern oder die Sprache oder Bedingung einer Ressource während des Kopiervorgangs zu ändern.

Sie können problemlos Ressourcen aus einer vorhandenen Ressource oder ausführbaren Datei in die aktuelle Ressourcen Datei kopieren. Um Ressourcen zu kopieren, öffnen Sie beide Dateien, die Ressourcen gleichzeitig enthalten, und ziehen Sie Elemente aus einer Datei in eine andere Datei, oder kopieren und fügen Sie zwischen den beiden Dateien ein. Diese Methode funktioniert für Ressourcen Skriptdateien (. RC) und Ressourcen Vorlagen Dateien (. rct) und als ausführbare Dateien (. exe).

> [!NOTE]
> Visual C++ enthält Beispiel Ressourcen Dateien, die Sie in ihrer eigenen Anwendung verwenden können. Weitere Informationen finden Sie unter [ClipArt: allgemeine Ressourcen](https://github.com/Microsoft/VCSamples).

Sie können die Ressourcen Dateien im Projekt (**Ressourcenansicht**) und in den eigenständigen RC-Dateien, die in Dokument Fenstern geöffnet sind, nicht per Drag & Drop, kopieren, Ausschneiden oder einfügen. Dies kann in früheren Versionen des Produkts der Fall sein. Verwenden Sie nur die Drag & Drop-Methode zwischen RC-Dateien, die außerhalb des Projekts geöffnet sind.

### <a name="to-copy-resources"></a>So kopieren Sie Ressourcen

1. Öffnen Sie beide Ressourcendateien eigenständig. (Siehe [Verwenden von Ressourcen Skriptdateien](how-to-create-a-resource-script-file.md#use-resource-script-files)). Öffnen Sie z. b. *Quelle1. RC* und *Source2. RC*.

1. In der ersten RC-Datei:

   - Verwenden der Drag-and-Drop-Methode

      1. Wählen Sie die Ressource aus, die Sie kopieren möchten. Wählen Sie z. b *. in Quelle1. RC* **IDD_DIALOG1**aus.

      1. Halten Sie die **STRG** -Taste gedrückt, und ziehen Sie die Ressource in die zweite RC-Datei. Ziehen Sie z. b. **IDD_DIALOG1** von *Quelle1. RC* nach *Source2. RC*.

         > [!TIP]
         > Wenn Sie die Ressource ziehen, ohne die **STRG** -Taste gedrückt halten, wird die Ressource verschoben, anstatt Sie zu kopieren.

   - Methode zum Kopieren und Einfügen verwenden

      1. Klicken Sie mit der rechten Maustaste auf die Ressource, die Sie kopieren möchten (z *. b. Quelle1. RC*), und wählen Sie **Kopieren**.

      1. Klicken Sie mit der rechten Maustaste auf die Ressourcen Datei, in die Sie die Ressource einfügen möchten (z *. b. Source2. RC*), und wählen Sie **Einfügen**aus.

> [!NOTE]
> Um Konflikte mit Symbolnamen oder Werten in der vorhandenen Datei zu vermeiden, C++ kann Visual den Symbolwert oder den Symbolnamen und den Wert der übertragenen Ressource ändern, wenn Sie ihn in die neue Datei kopieren.

Beim Kopieren in eine Ressource können Sie ihre Sprachen- und/oder Bedingungseigenschaft ändern.

- Die Sprache einer Ressource gibt die Sprache an, die von [FindResource](/windows/win32/api/winbase/nf-winbase-findresourcea) verwendet wird, um die Ressource zu identifizieren, für die Sie sich interessieren. Ressourcen können Unterschiede für jede Sprache aufweisen, die sich nicht auf Text bezieht, z. b. Beschleuniger, die möglicherweise nur auf einer japanischen Tastatur oder einer Bitmap funktionieren, die nur für lokalisierte chinesische Builds geeignet wäre.

- Die Bedingung einer Ressource stellt ein definiertes Symbol dar, das eine Bedingung angibt, unter der diese bestimmte Ressourcenkopie zu verwenden ist.

Die Sprache und Bedingung einer Ressource werden in Klammern nach dem Namen der Ressource im Fenster **Arbeitsbereich** angezeigt. Hier verwendet die Ressource mit dem Namen `IDD_AboutBox` `Finnish` als Sprache, und Ihre Bedingung ist `XX33`:

```cpp
IDD_AboutBox (Finnish - XX33)
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>So kopieren Sie eine vorhandene Ressource und ändern die Sprache oder Bedingung

Klicken Sie in der *RC* -Datei oder im [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources) Fenster mit der rechten Maustaste auf die Ressource, die Sie kopieren möchten, und wählen Sie **Kopie einfügen**aus. Legen Sie dann Folgendes fest:

- Wählen Sie im Listenfeld **Sprache** die Sprache aus.

- Geben Sie im Feld **Bedingung** die Bedingung ein.

### <a name="to-edit-resources"></a>So bearbeiten Sie Ressourcen

Verwaltete Ressourcen Dateien (RESX) sind XML-Dateien. Wenn Sie dem Projekt im Dialogfeld **Neues Element hinzufügen** eine verwaltete Ressourcen Datei hinzufügen, wird standardmäßig der **verwaltete Ressourcen-Editor** geöffnet.

## <a name="import-and-export-resources"></a>Importieren und Exportieren von Ressourcen

Sie können grafische Ressourcen (Bitmaps, Symbole, Cursor und Symbolleisten), HTML-Dateien und benutzerdefinierte Ressourcen für die Verwendung in Visual C++ importieren. Sie können dieselben Dateitypen aus einem Visual Studio C++ -Projekt in getrennte Dateien exportieren, die außerhalb der Entwicklungsumgebung verwendet werden können.

> [!NOTE]
> Ressourcentypen wie Acceleratoren, Dialogfelder und Zeichen folgen Tabellen können nicht importiert oder exportiert werden, da Sie keine eigenständigen Dateitypen sind.

### <a name="to-import-a-resource-into-the-resource-script-file"></a>So importieren Sie eine Ressource in die Ressourcen Skriptdatei

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources) klicken Sie mit der rechten Maustaste auf den Knoten der Ressourcen Skriptdatei (RC-Datei), der Sie eine Ressource hinzufügen möchten, und wählen Sie **importieren**aus.

1. Suchen Sie den Dateinamen der Bitmap (BMP), das Symbol (. ico), den Cursor (. cur), die HTML-Datei (. htm) oder eine andere zu importierende Datei, und wählen Sie ihn aus.

1. Wählen Sie **OK** aus, um die Ressource der Ressourcen Skriptdatei hinzuzufügen.

> [!NOTE]
> Der Import Vorgang funktioniert unabhängig davon, welcher Ressourcentyp Sie ausgewählt haben. Die importierte Ressource wird dem richtigen Knoten dieses Ressourcentyps automatisch hinzugefügt.

### <a name="to-export-a-resource-for-use-outside-of-visual-c"></a>So exportieren Sie eine Ressource für die Verwendung außerhalb des visuellen ElementsC++

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die Ressource, die Sie exportieren möchten, und wählen Sie **exportieren**aus. Sie können den aktuellen Dateinamen übernehmen oder einen neuen eingeben.

1. Navigieren Sie zu dem Ordner, in dem Sie die Datei speichern möchten, und wählen Sie **exportieren**aus.

## <a name="requirements"></a>Voraussetzungen

Win32

## <a name="see-also"></a>Siehe auch

[Ressourcendateien](../windows/resource-files-visual-studio.md)<br/>
[Vorgehensweise: Erstellen von Ressourcen](../windows/how-to-create-a-resource-script-file.md)<br/>
[Vorgehensweise: Einfügen von Ressourcen zur Kompilierungszeit](../windows/how-to-include-resources-at-compile-time.md)<br/>