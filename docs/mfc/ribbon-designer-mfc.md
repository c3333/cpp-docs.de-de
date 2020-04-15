---
title: Menüband-Designer (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 8b66ff0f19392eb1685f8632a3fc4d9e90094304
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372805"
---
# <a name="ribbon-designer-mfc"></a>Menüband-Designer (MFC)

Mit dem Menüband-Designer können Sie Menübänder in MFC-Anwendungen erstellen und anpassen. Ein Menüband ist ein Element der Benutzeroberfläche (UI), auf dem Befehle in logischen Gruppen organisiert werden. Diese Gruppen werden auf separaten Registerkarten in einem Streifen entlang des oberen Fensterrahmens angezeigt. Das Menüband ersetzt die Menü- und Symbolleisten. Mit einem Menüband kann die Benutzerfreundlichkeit von Anwendungen erheblich verbessert werden. Weitere Informationen finden Sie unter [Bänder](/windows/win32/uxguide/cmd-ribbons). Die folgende Abbildung zeigt ein Menüband.

![MFC-Menüband - Ressourcensteuerung](../mfc/media/ribbon_no_callouts.png "MFC-Menüband - Ressourcensteuerung")

In früheren Versionen von Visual Studio mussten Multifunktionsleisten durch Schreiben von Code erstellt werden, der die MFC-Multifunktionsleistenklassen wie [CMFCRibbonBar Class](../mfc/reference/cmfcribbonbar-class.md)verwendet. In Visual Studio 2010 und höher bietet der Multifunktionsleisten-Designer eine alternative Methode zum Erstellen von Bändern. Zunächst erstellen Sie ein Menüband als Ressource und passen es an. Dann laden Sie die Menübandressource vom Code in der MFC-Anwendung. Sie können Menübandressourcen und MFC-Menübandklassen sogar zusammen verwenden. Zum Beispiel können Sie eine Menübandressource erstellen und ihr dann mithilfe von Code zur Laufzeit programmgesteuert mehr Elemente hinzufügen.

## <a name="understanding-the-ribbon-designer"></a>Der Menüband-Designer

Mit dem Menüband-Designer wird das Menüband als Ressource erstellt und gespeichert. Wenn Sie eine Menübandressource erstellen, werden vom Menüband-Designer die folgenden drei Aktionen ausgeführt:

- Hinzufügen eines Eintrags im Projektressourcen-Definitionsskript (*.rc) Im folgenden Beispiel ist IDR_RIBBON der eindeutige Name, der die Multifunktionsleistenressource identifiziert, RT_RIBBON_XML der Ressourcentyp und multiribbon.mfcribbon-ms der Name der Ressourcendatei ist.

```cpp
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Hinzufügen der Definitionen von Befehls-IDs zur "resource.h"

```
#define IDR_RIBBON            307
```

- Eine Menübandressourcendatei (*.mfcribbon-ms), die den XML-Code enthält, mit dem die Schaltflächen des Menübands, die Steuerelemente und Attribute im Menüband definiert werden, wird erstellt. Änderungen, die im Menüband-Designer am Menüband vorgenommen werden, werden in der Ressourcendatei als XML gespeichert. Das folgende Codebeispiel zeigt einen \*Teil des Inhalts einer .mfcribbon-ms-Datei:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Um die Multifunktionsleistenressource in Ihrer MFC-Anwendung zu verwenden, laden Sie die Ressource, indem Sie [CMFCRibbonBar::LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource)aufrufen.

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Erstellen eines Menübands mit dem Menüband-Designer

Dies sind die zwei Möglichkeiten, dem MFC-Projekt eine Menübandressource hinzuzufügen:

- Erstellen einer MFC-Anwendung und konfigurieren des MFC-Projekt-Assistenten zum Erstellen des Menübands. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Erstellen einer Multifunktionsleistenanwendung mithilfe von MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- Erstellen Sie in einem vorhandenen MFC-Projekt eine Menübandressource und laden Sie sie. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Aktualisieren der MFC-Scribble-Anwendung (Teil 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md).

Wenn das Projekt bereits über ein manuell codiertes Menüband verfügt, können Sie das vorhandene Menüband mit MFC Funktionen in eine Menübandressource konvertieren. Weitere Informationen finden Sie unter [Gewusst wie: Konvertieren einer vorhandenen MFC-Multifunktionsleiste in eine Multifunktionsleistenressource](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md).

> [!NOTE]
> Menübänder können nicht in Anwendungen erstellt werden, die auf Dialogfeldern basieren. Weitere Informationen finden Sie unter [Anwendungstyp, MFC-Anwendungs-Assistent](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Anpassen von Menübändern

Um ein Menüband im Menüband-Designer zu öffnen, doppelklicken Sie in der Ressourcenansicht auf die Menübandressource. Im Designer können Sie dem Menüband, der Anwendungsschaltfläche oder der Symbolleiste für den Schnellzugriff Elemente hinzufügen, entfernen und anpassen. Sie können auch Ereignisse, z. B. Klickereignisse einer Schaltfläche und Menüereignisse, mit einer Methode in der Anwendung verknüpfen.

Die folgende Abbildung zeigt die verschiedenen Komponenten im Menüband-Designer.

![MFC-Menüband-Designer](../mfc/media/ribbon_designer.png "MFC-Menüband-Designer")

- **Toolbox:** Enthält Steuerelemente, die auf die Designeroberfläche gezogen werden können.

- **Designer-Oberfläche:** Enthält die visuelle Darstellung der Menübandressource.

- ** [Klassen-Assistent](reference/mfc-class-wizard.md):** Listet die Attribute des Elements auf, das auf der Designeroberfläche ausgewählt ist.

- **Fenster Ressourcenansicht:** Zeigt die Ressourcen an, die Multifunktionsleistenressourcen in Ihrem Projekt enthalten.

- **Toolbar für den Multifunktionsleisten-Editor:** Enthält Befehle, mit denen Sie eine Vorschau des Menübands anzeigen und das visuelle Design ändern können.

In den folgenden Themen wird die Verwendung der Funktionen im Menüband-Designer beschrieben:

- [Vorgehensweise: Anpassen der Anwendungsschaltfläche](../mfc/how-to-customize-the-application-button.md)

- [Gewusst wie: Anpassen der Symbolleiste für den Schnellzugriff](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Gewusst wie: Hinzufügen von Menüband-Steuerelementen und Ereignishandlern](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Gewusst wie: Laden einer Menübandressource aus einer MFC-Anwendung](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definitionen von Menübandelementen

![Menüband-MFC](../mfc/media/ribbon.png "Menüband-MFC")

- **Anwendungstaste:** Die Schaltfläche, die in der oberen linken Ecke eines Menübands angezeigt wird. Die Anwendungsschaltfläche ersetzt das Datei-Menü und ist sichtbar, wenn das Menüband minimiert wird. Wenn auf die Schaltfläche geklickt wird, wird ein Menü mit einer Liste von Befehlen angezeigt.

- **Quick Access Symbolleiste:** Eine kleine, anpassbare Symbolleiste, die häufig verwendete Befehle anzeigt.

- **Kategorie**: Die logische Gruppierung, die den Inhalt einer Multifunktionsleisten-Registerkarte darstellt.

- **Kategorie-Standard-Schaltfläche:** Die Schaltfläche, die auf dem Menüband angezeigt wird, wenn das Menüband minimiert wird. Wenn auf die Schaltfläche geklickt wird, erscheint die Kategorie als Menü neu.

- **Panel:** Ein Bereich der Multifunktionsleistenleiste, in dem eine Gruppe verwandter Steuerelemente angezeigt wird. In jeder Menübandkategorie ist mindestens ein Menübandbereich enthalten.

- **Bandelemente:** Steuerungen in den Bedienfeldern, z. B. Schaltflächen und Kombinationsboxen. Die verschiedenen Steuerelemente, die in einem Menüband gehostet werden können, finden Sie unter [RibbonGadgets Sample: Ribbon Gadgets Application](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Siehe auch

[Benutzeroberflächenelemente](../mfc/user-interface-elements-mfc.md)<br/>
[Arbeiten mit Ressourcendateien](../windows/working-with-resource-files.md)
