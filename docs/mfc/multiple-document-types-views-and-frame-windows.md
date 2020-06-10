---
title: Mehrere Dokumenttypen, Ansichten und Rahmenfenster
ms.date: 11/19/2018
helpviewer_keywords:
- static splitter windows [MFC]
- multiple views [MFC]
- multiple document types [MFC]
- multiple views [MFC], frame windows
- document classes [MFC], multiple
- documents [MFC], multiple types of
- splitter windows [MFC], dynamic
- dynamic splitter windows [MFC]
- windows [MFC], dynamic splitter
- windows [MFC], static splitter
- multiple frame windows [MFC]
- splitter windows [MFC], static
ms.assetid: c6b9e4e0-7c9c-45f1-a804-aeac39c9a128
ms.openlocfilehash: 873903aadc1596fbc56f9a0b0b98dbc5a948113d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619965"
---
# <a name="multiple-document-types-views-and-frame-windows"></a>Mehrere Dokumenttypen, Ansichten und Rahmenfenster

Die Standardbeziehung zwischen einem Dokument, der zugehörigen Ansicht und dem zugehörigen Rahmenfenster wird in [Document/View Creation](document-view-creation.md)(Erstellen von Dokumenten/Ansichten) beschrieben. Viele Anwendungen unterstützen einen einzelnen Dokumenttyp (jedoch möglicherweise mehrere offene Dokumente dieses Typs) mit einer einzelnen Ansicht des Dokuments und nur einem Rahmenfenster pro Dokument. Bei einigen Anwendungen muss jedoch einer oder mehrere dieser Standardwerte geändert werden.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Multiple document types](#_core_multiple_document_types)

- [Mehrere Ansichten](#_core_multiple_views)

- [Multiple frame windows](#_core_multiple_frame_windows)

- [Splitter Fenster](#_core_splitter_windows)

## <a name="multiple-document-types"></a><a name="_core_multiple_document_types"></a>Mehrere Dokumenttypen

Der MFC-Anwendungs-Assistent erstellt eine einzelne Dokumentklasse für Sie. In einigen Fällen müssen Sie jedoch möglicherweise mehr als einen Dokumenttyp unterstützen. Dies gilt beispielsweise dann, wenn Ihre Anwendung sowohl Tabellen- als auch Diagrammdokumente benötigt. Jeder Dokumenttyp wird durch eine eigene Dokumentklasse und möglicherweise auch durch eine eigene Ansichtsklasse repräsentiert. Wenn ein Benutzer den Befehl zum Erstellen einer neuen Datei verwendet, zeigt das Framework ein Dialogfeld an, in dem die unterstützten Dokumenttypen aufgeführt werden. Anschließend wird ein Dokument des vom Benutzer ausgewählten Typs erstellt. Jeder Dokumenttyp wird durch ein eigenes Dokumentvorlagenobjekt verwaltet.

Informationen zum Hinzufügen zusätzlicher Dokumentklassen finden Sie unter [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md). Wählen Sie [CDocument](reference/cdocument-class.md) als Klassentyp, aus dem abgeleitet werden soll, und stellen Sie die erforderlichen Dokumentinformationen bereit. Implementieren Sie danach die Daten der neuen Klasse.

Um das Framework über die zusätzliche Dokumentklasse zu informieren, müssen Sie einen zweiten Aufruf von [AddDocTemplate](reference/cwinapp-class.md#adddoctemplate) in die [InitInstance](reference/cwinapp-class.md#initinstance) -Überschreibung Ihrer Anwendungsklasse einfügen. Weitere Informationen finden Sie unter [Document Templates](document-templates-and-the-document-view-creation-process.md)(Dokumentvorlagen).

## <a name="multiple-views"></a><a name="_core_multiple_views"></a>Mehrere Ansichten

Viele Dokumente benötigen nur eine einzige Ansicht, es ist jedoch möglich, mehr als eine Ansicht für ein einzelnes Dokument zu unterstützen. Um Sie bei der Implementierung mehrerer Ansichten zu unterstützen, verwaltet ein Dokumentobjekt eine Liste der zugehörigen Ansichten und stellt Memberfunktionen zum Hinzufügen und Entfernen von Ansichten bereit. Darüber hinaus stellt das Objekt die Memberfunktion [UpdateAllViews](reference/cdocument-class.md#updateallviews) bereit, um mehrere Ansichten zu informieren, wenn sich die Daten eines Dokuments geändert haben.

MFC unterstützt drei allgemeine Benutzeroberflächen, die mehrere Ansichten des gleichen Dokuments erfordern. Folgende Modelle werden unterstützt:

- Ansichtsobjekte der gleichen Klasse, jeweils in separaten MDI-Dokumentrahmenfenstern (Multiple-Document Interface, Schnittstelle für mehrere Dokumente).

   Möglicherweise müssen Sie ein zweites Rahmenfenster in einem Dokument unterstützen. Ein Benutzer kann den Befehl „Neues Fenster“ verwenden, um einen zweiten Rahmen mit einer Ansicht des gleichen Dokuments zu öffnen, und dann verschiedene Teile dieses Dokuments gleichzeitig in den beiden Rahmen anzeigen. Das Framework unterstützt den Befehl „Neues Fenster“ im Menü „Fenster“ für MDI-Anwendungen, indem das ursprüngliche Rahmenfenster und die Ansicht, das bzw. die mit dem Dokument verknüpft ist, dupliziert werden.

- Ansichtsobjekte der gleichen Klasse im gleichen Dokumentrahmenfenster.

   Splitterfenster teilen den Ansichtsbereich eines einzelnen Dokumentfensters in mehrere separate Ansichten des Dokuments auf. Das Framework erstellt mehrere Ansichtsobjekte aus der gleichen Ansichtsklasse. Weitere Informationen finden Sie unter [Splitterfenster](#_core_splitter_windows).

- Ansichtsobjekte verschiedener Klassen in einem einzelnen Rahmenfenster.

   In diesem Modell, einer Variation des Splitterfensters, nutzen mehrere Ansichten ein einzelnes Rahmenfenster. Diese Ansichten werden aus verschiedenen Klassen erstellt, von denen jede eine andere Möglichkeit zur Anzeige des gleichen Dokuments bietet. Eine Ansicht kann beispielsweise ein Textverarbeitungsdokument im Normalmodus anzeigen, während die andere Ansicht das Dokument im Gliederungsmodus zeigt. Mit einem Splittersteuerelement kann ein Benutzer die relativen Größen der Ansichten anpassen.

Die folgende Abbildung für die Dokumente „a“, „b“ und „c“ zeigt die drei Benutzeroberflächenmodelle in der oben genannten Reihenfolge.

![Mehrere&#45;Anzeigen von Benutzeroberflächen](../mfc/media/vc37a71.gif "Mehrere&#45;Anzeigen von Benutzeroberflächen") <br/>
Benutzeroberflächen mit mehreren Ansichten

Das Framework ermöglicht diese Modelle durch Implementieren des Befehls „Neues Fenster“ und Bereitstellen der Klasse [CSplitterWnd](reference/csplitterwnd-class.md), wie im Abschnitt [Splitterfenster](#_core_splitter_windows)erläutert. Sie können diese Modelle als Ausgangspunkt verwenden und darauf basierend weitere Modelle implementieren. Beispielprogramme für die verschiedenen Konfigurationen von Ansichten, Rahmenfenstern und Aufteilungen finden Sie unter [MFC-Beispiele](../overview/visual-cpp-samples.md#mfc-samples).

Weitere Informationen zu `UpdateAllViews`finden Sie unter [CView](reference/cview-class.md) in der *MFC-Referenz* und im [Scribble-Beispiel](../overview/visual-cpp-samples.md).

## <a name="multiple-frame-windows"></a><a name="_core_multiple_frame_windows"></a>Mehrere Rahmen Fenster

Sie können den Befehl „Neues Fenster“ im Menü „Fenster“ verwenden, damit MDI-Anwendungen ein zweites Rahmenfenster im gleichen Dokument erstellen. Weitere Informationen finden Sie in der Abbildung Benutzeroberflächen mit mehreren Ansichten im ersten Modell.

## <a name="splitter-windows"></a><a name="_core_splitter_windows"></a>Splitter Fenster

In einem Splitterfenster kann das Fenster in zwei oder mehr scrollbare Bereiche unterteilt werden. Ein Splittersteuerelement (auch als Teilungsfeld bezeichnet), das sich im Fensterrahmen neben den Scrollleisten befindet, ermöglicht dem Benutzer, die relativen Größen der Bereiche anzupassen. Jeder Bereich ist eine Ansicht des gleichen Dokuments. In „dynamischen“ Splitterfenstern gehören die Ansichten zur gleichen Klasse, wie in der Abbildung Benutzeroberflächen mit mehreren Ansichten für Dokument „b“ gezeigt. In „statischen“ Splitterfenstern können die Ansichten zu verschiedenen Klassen gehören. Splitterfenster beider Arten werden von der Klasse [CSplitterWnd](reference/csplitterwnd-class.md)unterstützt.

Dynamische Splitterfenster mit Ansichten der gleichen Klasse ermöglichen es dem Benutzer, ein Fenster nach Belieben in mehrere Bereiche zu unterteilen und dann durch diese Bereiche zu scrollen, um verschiedene Teile des Dokuments anzuzeigen. Ein Benutzer kann die Aufteilung des Fensters auch aufheben, um die zusätzlichen Ansichten zu entfernen. Die Splitterfenster, die dem [Scribble-Beispiel](../overview/visual-cpp-samples.md) hinzugefügt wurden, veranschaulichen dies. Dieses Thema beschreibt das Verfahren zum Erstellen von dynamischen Splitterfenstern. Ein dynamisches Splitterfenster wird in der Abbildung Benutzeroberflächen mit mehreren Ansichten für Dokument „b“ gezeigt.

Bei statischen Splitterfenstern mit Ansichten verschiedener Klassen ist das Fenster bereits beim Start in mehrere Bereiche aufgeteilt, die jeweils unterschiedlichen Zwecken dienen. Im Visual C++-Bitmap-Editor beispielsweise zeigt das Bildfenster zwei Bereiche nebeneinander. Der linke Bereich zeigt ein Bild der Bitmap in der tatsächlichen Größe. Der rechte Bereich zeigt eine vergrößerte Ansicht der gleichen Bitmap. Die Bereiche sind durch eine Trennleiste getrennt, die der Benutzer ziehen kann, um die relative Größe der Bereiche zu ändern. Ein statisches Splitterfenster wird in der Abbildung Benutzeroberflächen mit mehreren Ansichten für Dokument „c“ gezeigt.

Weitere Informationen finden Sie unter [CSplitterWnd](reference/csplitterwnd-class.md) in der *MFC-Referenz* und in den [MFC-Beispielen](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Siehe auch

[Dokument-/Ansichtarchitektur](document-view-architecture.md)
