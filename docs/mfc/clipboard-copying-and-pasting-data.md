---
title: 'Zwischenablage: Daten kopieren und einfügen'
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard, copying data to
- Clipboard, pasting
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
ms.openlocfilehash: 74348dd3e790cceada9aafd718464694997316ed
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374570"
---
# <a name="clipboard-copying-and-pasting-data"></a>Zwischenablage: Daten kopieren und einfügen

In diesem Thema wird die minimale Arbeit beschrieben, die zum Implementieren des Kopierens in die Zwischenablage in der OLE-Anwendung und zum Einfügen aus der Zwischenablage erforderlich ist. Es wird empfohlen, die [OLE-Themen (Data Objects and Data Sources)](../mfc/data-objects-and-data-sources-ole.md) zu lesen, bevor Sie fortfahren.

Bevor Sie entweder kopieren oder einfügen können, müssen Sie zunächst Funktionen bereitstellen, um die Optionen Kopieren, Ausschneiden und Einfügen im Menü Bearbeiten zu behandeln.

## <a name="copying-or-cutting-data"></a><a name="_core_copying_or_cutting_data"></a>Kopieren oder Ausschneiden von Daten

#### <a name="to-copy-data-to-the-clipboard"></a>So kopieren Sie Daten in die Zwischenablage

1. Bestimmen Sie, ob es sich bei den zu kopierenden Daten um systemeigene Daten oder um ein eingebettetes oder verknüpftes Element handelt.

   - Wenn die Daten eingebettet oder verknüpft sind, `COleClientItem` erhalten Sie einen Zeiger auf das ausgewählte Objekt.

   - Wenn die Daten systemanisch sind und die Anwendung `COleServerItem` ein Server ist, erstellen Sie ein neues Objekt, das von den ausgewählten Daten abgeleitet wurde. Andernfalls erstellen `COleDataSource` Sie ein Objekt für die Daten.

1. Rufen Sie die `CopyToClipboard` Memberfunktion des ausgewählten Elements auf.

1. Wenn der Benutzer einen Ausschneiden-Vorgang anstelle eines Kopiervorgangs ausgewählt hat, löschen Sie die ausgewählten Daten aus der Anwendung.

Ein Beispiel für diese Sequenz `OnEditCut` finden `OnEditCopy` Sie in den MFC OLE-Beispielprogrammen [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md). Beachten Sie, dass in diesen Beispielen ein Zeiger auf die aktuell ausgewählten Daten beibehalten wird, sodass Schritt 1 bereits abgeschlossen ist.

## <a name="pasting-data"></a><a name="_core_pasting_data"></a>Einfügen von Daten

Das Einfügen von Daten ist komplizierter als das Kopieren, da Sie das Format auswählen müssen, das beim Einfügen der Daten in die Anwendung verwendet werden soll.

#### <a name="to-paste-data-from-the-clipboard"></a>So fügen Sie Daten aus der Zwischenablage ein

1. Implementieren `OnEditPaste` Sie in ihrer Ansichtsklasse, um Benutzer zu behandeln, die die Option Einfügen aus dem Menü Bearbeiten auswählen.

1. Erstellen `OnEditPaste` Sie in `COleDataObject` der Funktion `AttachClipboard` ein Objekt, und rufen Sie seine Memberfunktion auf, um dieses Objekt mit den Daten in der Zwischenablage zu verknüpfen.

1. Rufen `COleDataObject::IsDataAvailable` Sie an, um zu überprüfen, ob ein bestimmtes Format verfügbar ist.

   Alternativ können Sie `COleDataObject::BeginEnumFormats` nach anderen Formaten suchen, bis Sie eines finden, das für Ihre Anwendung am besten geeignet ist.

1. Führen Sie das Einfügen des Formats aus.

Ein Beispiel dafür, wie dies funktioniert, finden Sie in der Implementierung der `OnEditPaste` Memberfunktionen in den Ansichtsklassen, die in den MFC-OLE-Beispielprogrammen [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md)definiert sind.

> [!TIP]
> Der Hauptvorteil der Trennung des Einfügevorgangs in seine eigene Funktion besteht darin, dass derselbe Einfügecode verwendet werden kann, wenn Daten während eines Drag-and-Drop-Vorgangs in der Anwendung abgelegt werden. Wie in OCLIENT und HIERSVR kann Ihre `OnDrop` Funktion auch aufrufen `DoPasteItem`und den Code wiederverwenden, der zum Implementieren von Paste-Vorgängen geschrieben wurde.

Informationen zur Behandlung der Option Spezial einfügen im Menü Bearbeiten finden Sie im Thema [Dialogfelder in OLE](../mfc/dialog-boxes-in-ole.md).

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Hinzufügen anderer Formate](../mfc/clipboard-adding-other-formats.md)

- [OLE-Datenobjekte und Datenquellen und gleichmäßige Datenübertragung](../mfc/data-objects-and-data-sources-ole.md)

- [Drag &amp; Drop (OLE)](../mfc/drag-and-drop-ole.md)

- [OLE](../mfc/ole-background.md)

## <a name="see-also"></a>Siehe auch

[Zwischenablage: Verwenden des OLE-Zwischenablagemechanismus](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)
