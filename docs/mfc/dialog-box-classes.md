---
title: Dialogfeldklassen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.dialog
helpviewer_keywords:
- property sheet classes
- dialog box classes
- OLE common dialog classes
- common dialog classes [MFC]
- tab dialog boxes
ms.assetid: db75da23-4eff-4c6c-beae-79cf046fbce9
ms.openlocfilehash: 2399b27fc081dcc810277079729b0e62ef80d603
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616939"
---
# <a name="dialog-box-classes"></a>Dialogfeldklassen

`CDialog`Die Klasse und die abgeleiteten Klassen kapseln die Dialogfeld Funktionalität. Da ein Dialogfeld eine besondere Art von Fenster ist, `CDialog` wird von abgeleitet `CWnd` . Leiten Sie die Dialogfeld Klassen von ab, `CDialog` oder verwenden Sie eine der allgemeinen Dialogfeld Klassen für Standard Dialogfelder, z. b. Öffnen oder Speichern einer Datei, drucken, Auswählen einer Schriftart oder Farbe, Initiieren eines Such-und Ersetzungs Vorgangs oder Ausführen verschiedener OLE-bezogener Vorgänge.

[CDialog](reference/cdialog-class.md)<br/>
Die Basisklasse für alle Dialogfelder, sowohl modale als auch nicht modale.

[CDataExchange](reference/cdataexchange-class.md)<br/>
Stellt Datenaustausch-und Validierungs Informationen für Dialogfelder bereit.

## <a name="common-dialogs"></a>Allgemeine Dialogfelder

Diese Dialogfeld Klassen kapseln die allgemeinen Windows-Dialogfelder. Sie stellen einfach zu verwendende Implementierungen komplizierter Dialogfelder bereit.

[CCommonDialog](reference/ccommondialog-class.md)<br/>
Basisklasse für alle allgemeinen Dialogfelder.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Stellt ein Standard Dialogfeld zum Öffnen oder Speichern einer Datei bereit.

[CColorDialog](reference/ccolordialog-class.md)<br/>
Stellt ein Standard Dialogfeld für die Auswahl einer Farbe bereit.

[CFontDialog](reference/cfontdialog-class.md)<br/>
Stellt ein Standard Dialogfeld zum Auswählen einer Schriftart bereit.

[CFindReplaceDialog](reference/cfindreplacedialog-class.md)<br/>
Stellt ein Standard Dialogfeld für einen Such-und Ersetzungs Vorgang bereit.

[CPrintDialog](reference/cprintdialog-class.md)<br/>
Stellt ein Standard Dialogfeld zum Drucken einer Datei bereit.

[CPrintDialogEx](reference/cprintdialogex-class.md)<br/>
Stellt ein Windows-Druckeigenschaften Blatt bereit.

[CPageSetupDialog](reference/cpagesetupdialog-class.md)<br/>
Kapselt die Dienste, die vom Windows-Dialogfeld "Common Page Setup" bereitgestellt werden, mit zusätzlicher Unterstützung für das Festlegen und Ändern von Druck Rändern

## <a name="ole-common-dialogs"></a>Allgemeine OLE-Dialogfelder

OLE fügt Windows mehrere allgemeine Dialogfelder hinzu. Diese Klassen kapseln die OLE-allgemeinen Dialogfelder.

[COleDialog](reference/coledialog-class.md)<br/>
Wird vom Framework verwendet, um allgemeine Implementierungen für alle OLE-Dialogfelder zu enthalten. Alle Dialogfeld Klassen in der Benutzeroberflächen Kategorie werden von dieser Basisklasse abgeleitet. `COleDialog`kann nicht direkt verwendet werden.

[COleInsertDialog](reference/coleinsertdialog-class.md)<br/>
Zeigt das Dialogfeld Objekt einfügen, die Standardbenutzer Oberfläche für das Einfügen von neuen OLE-verknüpften oder eingebetteten Elementen an.

[COlePasteSpecialDialog](reference/colepastespecialdialog-class.md)<br/>
Zeigt das Dialogfeld "spezielles einfügen" an, die Standardbenutzer Oberfläche für die Implementierung des Befehls "speziellen einfügen".

[COleLinksDialog](reference/colelinksdialog-class.md)<br/>
Zeigt das Dialogfeld Links bearbeiten an, der Standardbenutzer Oberfläche zum Ändern von Informationen zu verknüpften Elementen.

[COleChangeIconDialog](reference/colechangeicondialog-class.md)<br/>
Zeigt das Dialogfeld Symbol ändern, die Standardbenutzer Oberfläche zum Ändern des Symbols an, das einem OLE Embedded-oder verknüpften Element zugeordnet ist.

[COleConvertDialog](reference/coleconvertdialog-class.md)<br/>
Zeigt das Dialogfeld Konvertieren an, die Standardbenutzer Oberfläche zum Konvertieren von OLE-Elementen von einem Typ in einen anderen.

[COlePropertiesDialog](reference/colepropertiesdialog-class.md)<br/>
Kapselt das allgemeine Windows-OLE-Eigenschaften Dialogfeld. Allgemeine OLE-Eigenschaften (Dialogfelder) bieten eine einfache Möglichkeit zum Anzeigen und Ändern der Eigenschaften eines OLE-Dokument Elements auf eine Weise, die mit Windows-Standards konsistent ist.

[COleUpdateDialog](reference/coleupdatedialog-class.md)<br/>
Zeigt das Dialogfeld Aktualisieren an, die Standardbenutzer Oberfläche zum Aktualisieren aller Links in einem Dokument. Das Dialogfeld enthält eine Statusanzeige, die angibt, wie die Aktualisierung der Aktualisierung abgeschlossen werden soll.

[COleChangeSourceDialog](reference/colechangesourcedialog-class.md)<br/>
Zeigt das Dialogfeld Quelle ändern an, die Standardbenutzer Oberfläche zum Ändern des Ziels oder der Quelle eines Links.

[COleBusyDialog](reference/colebusydialog-class.md)<br/>
Zeigt die Dialogfelder Server ausgelastet und Server reagiert nicht an, der Standardbenutzer Oberfläche für die Verarbeitung von Aufrufen von ausgelasteten Anwendungen. Wird normalerweise automatisch von der [colemessagefilter](reference/colemessagefilter-class.md) -Implementierung angezeigt.

## <a name="property-sheet-classes"></a>Eigenschaften Blatt Klassen

Mithilfe der Eigenschaften Blatt Klassen können Ihre Anwendungen Eigenschaften Blätter verwenden, die auch als Dialogfelder im Registerkarten Format bezeichnet werden. Eigenschaften Blätter sind eine effiziente Möglichkeit, eine große Anzahl von Steuerelementen in einem einzelnen Dialogfeld zu organisieren.

[CPropertyPage](reference/cpropertypage-class.md)<br/>
Stellt die einzelnen Seiten innerhalb eines Eigenschaften Blatts bereit. Leiten Sie `CPropertyPage` für jede Seite, die dem Eigenschaften Blatt hinzugefügt werden soll, eine Klasse von ab.

[CPropertySheet](reference/cpropertysheet-class.md)<br/>
Stellt den Frame für mehrere Eigenschaften Seiten bereit. Leiten Sie die Eigenschaften Blatt Klasse von ab `CPropertySheet` , um die Eigenschaften Blätter schnell zu implementieren.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
Zeigt die Eigenschaften eines OLE-Steuer Elements in einer grafischen Benutzeroberfläche ähnlich einem Dialogfeld an.

## <a name="html-based-dialog-classes"></a>HTML-basierte Dialog Feld Klassen

[CDHtmlDialog](reference/cdhtmldialog-class.md)<br/>
Wird verwendet, um Dialogfelder zu erstellen, die Ihre Benutzeroberfläche mit HTML anstelle von Dialogfeld Ressourcen implementieren.

[CMultiPageDHtmlDialog](reference/cmultipagedhtmldialog-class.md)<br/>
Zeigt mehrere HTML-Seiten sequenziell an und behandelt die Ereignisse auf jeder Seite.

## <a name="related-classes"></a>Verwandte Klassen

Diese Klassen sind keine Dialogfelder pro SE, Sie verwenden jedoch Dialogfeld Vorlagen und haben ein Großteil des Verhaltens von Dialogfeldern.

[CDialogBar](reference/cdialogbar-class.md)<br/>
Eine Steuerleiste, die auf einer Dialogfeld Vorlage basiert.

[CFormView](reference/cformview-class.md)<br/>
Eine scrollansicht, deren Layout in einer Dialogfeld Vorlage definiert ist. Leiten Sie eine Klasse von ab `CFormView` , um eine Benutzeroberfläche zu implementieren, die auf einer Dialogfeld Vorlage basiert.

[CDaoRecordView](reference/cdaorecordview-class.md)<br/>
Stellt eine Formularansicht bereit, die direkt mit einem DAO-Recordset-Objekt (Data Access Object) verbunden ist. Wie alle Formular Ansichten basiert eine `CDaoRecordView` auf einer Dialogfeld Vorlage.

[CRecordView](reference/crecordview-class.md)<br/>
Stellt eine direkt mit einem Open Database Connectivity (ODBC)-Recordset-Objekt verbundene Formularansicht bereit. Wie alle Formular Ansichten basiert eine `CRecordView` auf einer Dialogfeld Vorlage.

[CPrintInfo](reference/cprintinfo-structure.md)<br/>
Eine-Struktur, die Informationen zu einem Druck-oder Druckvorschau Auftrag enthält. Wird von der Druck Architektur von [CView](reference/cview-class.md)verwendet.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)
