---
title: 'TN022: Implementieren von Standardbefehlen'
ms.date: 11/04/2016
f1_keywords:
- vc.commands
helpviewer_keywords:
- ID_PREV_PANE command [MFC]
- ID_APP_EXIT command [MFC]
- ID_NEXT_PANE command [MFC]
- ID_INDICATOR_REC command [MFC]
- ID_WINDOW_SPLIT command [MFC]
- ID_FILE_PRINT_PREVIEW command [MFC]
- ID_WINDOW_CASCADE command [MFC]
- ID_FILE_CLOSE command [MFC]
- ID_FILE_SAVE_COPY_AS command [MFC]
- ID_WINDOW_ARRANGE command [MFC]
- ID_EDIT_FIND command [MFC]
- ID_FILE_OPEN command [MFC]
- ID_FILE_PAGE_SETUP command [MFC]
- ID_OLE_VERB_FIRST command [MFC]
- ID_EDIT_UNDO command [MFC]
- ID_EDIT_CLEAR command [MFC]
- ID_INDICATOR_CAPS command [MFC]
- ID_HELP_INDEX command [MFC]
- commands [MFC], standard
- ID_FILE_PRINT_SETUP command [MFC]
- ID_DEFAULT_HELP command [MFC]
- ID_INDICATOR_SCRL command [MFC]
- ID_FILE_PRINT command [MFC]
- ID_INDICATOR_OVR command [MFC]
- ID_INDICATOR_KANA command [MFC]
- ID_EDIT_COPY command [MFC]
- ID_EDIT_REDO command [MFC]
- ID_EDIT_PASTE command [MFC]
- ID_OLE_INSERT_NEW command [MFC]
- ID_OLE_EDIT_LINKS command [MFC]
- ID_EDIT_PASTE_SPECIAL command [MFC]
- ID_INDICATOR_EXT command [MFC]
- ID_HELP_USING command [MFC]
- standard commands
- ID_VIEW_STATUS_BAR command [MFC]
- ID_FILE_SAVE_AS command [MFC]
- ID_EDIT_CLEAR_ALL command [MFC]
- ID_WINDOW_NEW command [MFC]
- ID_CONTEXT_HELP command [MFC]
- ID_EDIT_REPLACE command [MFC]
- ID_WINDOW_TILE_HORZ command [MFC]
- ID_APP_ABOUT command [MFC]
- TN022
- ID_VIEW_TOOLBAR command [MFC]
- ID_HELP command [MFC]
- ID_WINDOW_TILE_VERT command [MFC]
- ID_EDIT_CUT command [MFC]
- ID_FILE_UPDATE command [MFC]
- ID_EDIT_REPEAT command [MFC]
- ID_FILE_SAVE command [MFC]
- ID_EDIT_PASTE_LINK command [MFC]
- ID_EDIT_SELECT_ALL command [MFC]
- ID_FILE_NEW command [MFC]
- ID_INDICATOR_NUM command
ms.assetid: a7883b46-23f7-4870-ac3a-804aed9258b5
ms.openlocfilehash: 5c7041f40c7e30592f642d29d9d02812a9596864
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370397"
---
# <a name="tn022-standard-commands-implementation"></a>TN022: Implementieren von Standardbefehlen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt die Standardbefehlsimplementierungen von MFC 2.0. Lesen Sie zunächst [technische Anmerkung 21,](../mfc/tn021-command-and-message-routing.md) da sie die Mechanismen beschreibt, die zum Implementieren vieler Standardbefehle verwendet werden.

Diese Beschreibung setzt Kenntnisse der MFC-Architekturen, APIs und gängigen Programmierpraxis voraus. Dokumentierte sowie nicht dokumentierte "nur Implementierungs"-APIs werden beschrieben. Dies ist kein Ort, um mehr über die Funktionen oder das Programmieren in MFC zu erfahren. Ausführlichere Informationen zu dokumentierten APIs finden Sie unter Visual C++.

## <a name="the-problem"></a>Problemstellung

MFC definiert viele Standardbefehls-IDs in der Headerdatei AFXRES. H. Die Frameworkunterstützung für diese Befehle variiert. Wenn Sie verstehen, wo und wie die Frameworkklassen mit diesen Befehlen umgehen, werden Sie nicht nur zeigen, wie das Framework intern funktioniert, sondern sie bieten auch nützliche Informationen zum Anpassen der Standardimplementierungen und bei einigen Techniken zum Implementieren Ihrer eigenen Befehlshandler.

## <a name="contents-of-this-technical-note"></a>Inhalt dieses technischen Hinweises

Jede Befehls-ID wird in zwei Abschnitten beschrieben:

- Der Titel: der symbolische Name der Befehls-ID (z. B. ID_FILE_SAVE), gefolgt vom Zweck des Befehls (z. B. "speichert das aktuelle Dokument"), getrennt durch einen Doppelpunkt.

- Ein oder mehrere Absätze, in denen beschrieben wird, welche Klassen den Befehl implementieren und was die Standardimplementierung bewirkt

Die meisten Standardbefehlsimplementierungen sind in der Basisklassen-Nachrichtenzuordnung des Frameworks vorverdrahtet. Es gibt einige Befehlsimplementierungen, die eine explizite Verdrahtung in der abgeleiteten Klasse erfordern. Diese werden unter "Hinweis" beschrieben. Wenn Sie in AppWizard die richtigen Optionen ausgewählt haben, werden diese Standardhandler für Sie in der generierten Skelettanwendung verbunden.

## <a name="naming-convention"></a>Benennungskonvention

Standardbefehle folgen einer einfachen Namenskonvention, die Wir nach Möglichkeit verwenden sollten. Die meisten Standardbefehle befinden sich an Standardstellen in der Menüleiste einer Anwendung. Der symbolische Name des Befehls beginnt mit "ID_", gefolgt vom Standard-Popupmenünamen, gefolgt vom Namen des Menüelements. Der symbolische Name ist im Großbuchstaben mit Unterstrich Wortumbrüche. Für Befehle, die keine Standardmenüelementnamen haben, wird ein logischer Befehlsname definiert, beginnend mit "ID_" (z. B. ID_NEXT_PANE).

Wir verwenden das Präfix "ID_", um Befehle anzugeben, die an Menüelemente, Symbolleistenschaltflächen oder andere Befehlsbenutzeroberflächenobjekte gebunden werden sollen. Befehlshandler, die "ID_"-Befehle verarbeiten, sollten die ON_COMMAND- und ON_UPDATE_COMMAND_UI-Mechanismen der MFC-Befehlsarchitektur verwenden.

Es wird empfohlen, das Standardpräfix "IDM_" für Menüelemente zu verwenden, die nicht der Befehlsarchitektur folgen und menüspezifischen Code benötigen, um sie zu aktivieren und zu deaktivieren. Natürlich sollte die Anzahl der menüspezifischen Befehle klein sein, da die Befolgschaft der MFC-Befehlsarchitektur nicht nur Befehlshandler leistungsfähiger macht (da sie mit Symbolleisten arbeiten), sondern auch den Befehlshandlercode wiederverwendbar macht.

## <a name="id-ranges"></a>ID-Bereiche

Weitere Informationen zur Verwendung von ID-Bereichen in MFC finden Sie im [Technischen Hinweis 20.](../mfc/tn020-id-naming-and-numbering-conventions.md)

MFC-Standardbefehle liegen im Bereich von 0xE000 bis 0xEFFF. Bitte verlassen Sie sich nicht auf die spezifischen Werte dieser IDs, da sie in zukünftigen Versionen der Bibliothek geändert werden können.

Ihre Anwendung sollte ihre Befehle im Bereich 0x8000 bis 0xDFFF definieren.

## <a name="standard-command-ids"></a>Standardbefehls-IDs

Für jede Befehls-ID gibt es eine Standard-Eingabeaufforderungszeichenfolge für Die Nachrichten, die in der Datei PROMPTS gefunden werden kann. Rc. Die Zeichenfolgen-ID für diese Menüaufforderung muss mit der Befehls-ID identisch sein.

- ID_FILE_NEW Erstellt ein neues/leeres Dokument.

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CWinApp::OnFileNew`implementiert diesen Befehl je nach Anzahl der Dokumentvorlagen in der Anwendung unterschiedlich. Wenn nur ein `CDocTemplate` `CWinApp::OnFileNew` dokument dieses Typs erstellt wird, wird ein neues Dokument dieses Typs sowie der richtige Frame und die Ansichtsklasse erstellt.

   Wenn mehr als `CDocTemplate`eine `CWinApp::OnFileNew` vorhanden ist, wird der Benutzer mit einem Dialogfeld (AFX_IDD_NEWTYPEDLG) aufgefordert, mit dem er auswählen kann, welcher Dokumenttyp verwendet werden soll. Die `CDocTemplate` ausgewählte wird zum Erstellen des Dokuments verwendet.

   Eine häufige Anpassung von ID_FILE_NEW besteht darin, eine andere und grafischere Auswahl von Dokumenttypen bereitzustellen. In diesem Fall können `CMyApp::OnFileNew` Sie Ihre eigene implementieren und `CWinApp::OnFileNew`in Ihrer Nachrichtenzuordnung anstelle von platzieren. Es ist nicht erforderlich, die Basisklassenimplementierung aufzurufen.

   Eine weitere häufige Anpassung von ID_FILE_NEW besteht darin, einen separaten Befehl zum Erstellen eines Dokuments jedes Typs bereitzustellen. In diesem Fall sollten Sie neue Befehls-IDs definieren, z. B. ID_FILE_NEW_CHART und ID_FILE_NEW_SHEET.

- ID_FILE_OPEN Öffnet ein vorhandenes Dokument.

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CWinApp::OnFileOpen`hat eine sehr einfache `CWinApp::DoPromptFileName` Implementierung `CWinApp::OpenDocumentFile` des Aufrufs gefolgt von der Datei oder dem Pfadnamen der datei zu öffnen. Die `CWinApp` Implementierungsroutine `DoPromptFileName` ruft das standardmäßige FileOpen-Dialogfeld auf und füllt es mit den Dateierweiterungen aus den aktuellen Dokumentvorlagen.

   Eine häufige Anpassung von ID_FILE_OPEN besteht darin, das Dialogfeld FileOpen anzupassen oder zusätzliche Dateifilter hinzuzufügen. Die empfohlene Methode zum Anpassen besteht darin, die Standardimplementierung durch `CWinApp::OpenDocumentFile` Ein eigenes FileOpen-Dialogfeld zu ersetzen und den Datei- oder Pfadnamen des Dokuments aufzurufen. Es ist nicht erforderlich, die Basisklasse aufzurufen.

- ID_FILE_CLOSE Schließt das aktuell geöffnete Dokument.

   `CDocument::OnFileClose`ruft `CDocument::SaveModified` auf, um den Benutzer aufzufordern, das `OnCloseDocument`Dokument zu speichern, wenn es geändert wurde, und ruft dann auf. Die gesamte Abschlusslogik, einschließlich der Zerstörung `OnCloseDocument` des Dokuments, erfolgt in der Routine.

    > [!NOTE]
    >  ID_FILE_CLOSE wirkt anders als eine WM_CLOSE Nachricht oder ein SC_CLOSE Systembefehl, der an das Dokumentrahmenfenster gesendet wird. Beim Schließen eines Fensters wird das Dokument nur geschlossen, wenn dies das letzte Rahmenfenster ist, in dem das Dokument angezeigt wird. Wenn Sie das Dokument mit ID_FILE_CLOSE schließen, wird nicht nur das Dokument geschlossen, sondern alle Rahmenfenster, in denen das Dokument angezeigt wird.

- ID_FILE_SAVE Speichert das aktuelle Dokument.

   Die Implementierung verwendet eine `CDocument::DoSave` Hilfsroutine, `OnFileSave` die `OnFileSaveAs`sowohl für als auch für verwendet wird. Wenn Sie ein Dokument speichern, das zuvor nicht gespeichert wurde (d. h. es hat keinen Pfadnamen, wie im Fall `OnFileSave` von FileNew), oder das aus einem schreibgeschützten Dokument gelesen wurde, verhält sich die Logik wie der Befehl ID_FILE_SAVE_AS und fordert den Benutzer auf, einen neuen Dateinamen bereitzustellen. Der eigentliche Prozess des Öffnens der Datei und `OnSaveDocument`des Speicherns erfolgt über die virtuelle Funktion .

   Es gibt zwei häufige Gründe, ID_FILE_SAVE anzupassen. Für Dokumente, die nicht gespeichert werden, entfernen Sie einfach die ID_FILE_SAVE Menüelemente und Symbolleistenschaltflächen aus der Benutzeroberfläche. Stellen Sie außerdem sicher, dass Sie Ihr `CDocument::SetModifiedFlag`Dokument niemals verschmutzt haben (d. h. nie aufrufen), und das Framework wird niemals dazu führen, dass das Dokument gespeichert wird. Definieren Sie für Dokumente, die an einem anderen Ort als einer Datenträgerdatei gespeichert werden, einen neuen Befehl für diesen Vorgang.

   Im Fall eines `COleServerDoc`wird ID_FILE_SAVE sowohl für das Speichern von Dateien (für normale Dokumente) als auch für die Dateiaktualisierung (für eingebettete Dokumente) verwendet.

   Wenn Ihre Dokumentdaten in einzelnen Datenträgerdateien gespeichert sind, Sie `CDocument` jedoch nicht die standardmäßige `CDocument::OnSaveDocument` Serialisierungsimplementierung verwenden möchten, sollten Sie anstelle von `OnFileSave`überschreiben.

- ID_FILE_SAVE_AS Speichert das aktuelle Dokument unter einem anderen Dateinamen.

   Die `CDocument::OnFileSaveAs` Implementierung verwendet `CDocument::DoSave` dieselbe Hilfsroutine wie `OnFileSave`. Der `OnFileSaveAs` Befehl wird genauso behandelt wie ID_FILE_SAVE, wenn die Dokumente vor dem Speichern keinen Dateinamen hatten. `COleServerDoc::OnFileSaveAs`implementiert die Logik zum Speichern einer normalen Dokumentdatendatei oder zum Speichern eines Serverdokuments, das ein OLE-Objekt darstellt, das in eine andere Anwendung eingebettet ist, als separate Datei.

   Wenn Sie die Logik ID_FILE_SAVE anpassen, sollten Sie ID_FILE_SAVE_AS wahrscheinlich auf ähnliche Weise anpassen, oder die Funktionsweise von "Speichern unter" gilt möglicherweise nicht für Ihr Dokument. Sie können das Menüelement aus der Menüleiste entfernen, wenn es nicht benötigt wird.

- ID_FILE_SAVE_COPY_AS Speichert ein aktuelles Dokument unter einem neuen Namen.

   Die `COleServerDoc::OnFileSaveCopyAs` Implementierung ist `CDocument::OnFileSaveAs`sehr ähnlich zu , mit der Ausnahme, dass das Dokumentobjekt nach dem Speichern nicht an die zugrunde liegende Datei "angefügt" ist. Das heißt, wenn das Speicherdokument vor dem Speichern "modifiziert" wurde, wird es immer noch "modifiziert". Darüber hinaus hat dieser Befehl keine Auswirkungen auf den Pfadnamen oder Titel, der im Dokument gespeichert ist.

- ID_FILE_UPDATE benachrichtigt den Container, um ein eingebettetes Dokument zu speichern.

   Die `COleServerDoc::OnUpdateDocument` Implementierung weist den Container einfach darauf hin, dass die Einbettung gespeichert werden soll. Der Container ruft dann die entsprechenden OLE-APIs auf, um das eingebettete Objekt zu speichern.

- ID_FILE_PAGE_SETUP Ruft ein anwendungsspezifisches Seiteneinrichtungs-/Layoutdialogfeld auf.

   Derzeit gibt es keinen Standard für dieses Dialogfeld, und das Framework hat keine Standardimplementierung dieses Befehls.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_FILE_PRINT_SETUP Rufen Sie das standardmäßige Dialogfeld Drucksetup auf.

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   Dieser Befehl ruft das Standardmäßige Drucksetup-Dialogfeld auf, mit dem der Benutzer die Drucker- und Druckeinstellungen für mindestens dieses Dokument oder höchstens alle Dokumente in dieser Anwendung anpassen kann. Sie müssen die Systemsteuerung verwenden, um die Standarddruckereinstellungen für das gesamte System zu ändern.

   `CWinApp::OnFilePrintSetup`hat eine sehr einfache `CPrintDialog` Implementierung, `CWinApp::DoPrintDialog` die ein Objekt erstellt und die Implementierungsfunktion aufruft. Dadurch wird die Standarddruckereinrichtung der Anwendung festgelegt.

   Das Anpassen dieses Befehls ist häufig die Möglichkeit, Druckereinstellungen pro Dokument zu ermöglichen, die beim Speichern mit dem Dokument gespeichert werden sollen. Dazu `CDocument` sollten Sie ihrer Klasse einen Messagemap-Handler `CPrintDialog` hinzufügen, der ein Objekt erstellt, es mit den entsprechenden Druckerattributen `CPrintDialog::DoModal`(in der Regel *hDevMode* und *hDevNames)* initialisiert, die aufruft und die geänderten Druckereinstellungen speichert. Für eine robuste Implementierung sollten Sie `CWinApp::DoPrintDialog` sich die Implementierung `CWinApp::UpdatePrinterSelection` von zur Erkennung von Fehlern und zum Umgang mit sinnvollen Standardeinstellungen und nachverfolgen systemweiten Druckeränderungen ansehen.

- ID_FILE_PRINT Standarddruck des aktuellen Dokuments

    > [!NOTE]
    >  Sie müssen diese `CView`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   Mit diesem Befehl wird das aktuelle Dokument oder korrekt erweiterbar, der Druckvorgang gestartet, bei dem das Standarddruckdialogfeld aufzurufen und die Druckmaschine ausgeführt wird.

   `CView::OnFilePrint`implementiert diesen Befehl und die Hauptdruckschleife. Es ruft `CView::OnPreparePrinting` die virtuelle Eingabeaufforderung des Benutzers mit dem Druckdialog auf. Anschließend wird der Ausgangs-DC vorbereitet, um zum Drucker zu gelangen, der `StartDoc` Druckfortschrittsdialog (AFX_IDD_PRINTDLG) wird angezeigt und der Escape-Vorgang an den Drucker gesendet. `CView::OnFilePrint`enthält auch die Hauptseiten-orientierte Druckschleife. Für jede Seite ruft `CView::OnPrepareDC` sie das `StartPage` Virtuelle auf, `CView::OnPrint` gefolgt von einem Escape- und Aufruf des virtuellen für diese Seite. Wenn die sende Zeit abgeschlossen ist, wird das virtuelle `CView::OnEndPrinting` Feld aufgerufen, und das Dialogfeld für den Druckfortschritt wird geschlossen.

   Die MFC-Druckarchitektur wurde entwickelt, um auf viele verschiedene Arten für den Druck und die Druckvorschau zu binden. Normalerweise finden Sie `CView` die verschiedenen überschreibbaren Funktionen für alle seitenorientierten Druckaufgaben geeignet. Nur bei einer Anwendung, die den Drucker für die nicht seitenorientierte Ausgabe verwendet, sollten Sie die Notwendigkeit finden, die ID_FILE_PRINT Implementierung zu ersetzen.

- ID_FILE_PRINT_PREVIEW Geben Sie den Druckvorschaumodus für das aktuelle Dokument ein.

    > [!NOTE]
    >  Sie müssen diese `CView`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CView::OnFilePrintPreview`startet den Druckvorschaumodus, indem die `CView::DoPrintPreview`dokumentierte Hilfsfunktion aufgerufen wird. `CView::DoPrintPreview`ist das Hauptmodul für die Druckvorschauschleife, ebenso wie `OnFilePrint` das Hauptmodul für die Druckschleife.

   Der Druckvorschauvorgang kann auf verschiedene Weise angepasst werden, indem verschiedene Parameter an `DoPrintPreview`übergeben werden. Weitere Informationen finden Sie in [Technical Note 30](../mfc/tn030-customizing-printing-and-print-preview.md), in dem einige Details der Druckvorschau erläutert und wie Sie sie anpassen können.

- ID_FILE_MRU_FILE1... FILE16 Ein Bereich von Befehls-IDs für die **Datei-MRU-Liste**.

   `CWinApp::OnUpdateRecentFileMenu`ist ein Updatebefehls-UI-Handler, der eine der erweiterten Anwendungen des ON_UPDATE_COMMAND_UI-Mechanismus ist. In Ihrer Menüressource müssen Sie nur ein einzelnes Menüelement mit ID-ID_FILE_MRU_FILE1 definieren. Dieser Menüpunkt bleibt zunächst deaktiviert.

   Wenn die MRU-Liste wächst, werden der Liste weitere Menüelemente hinzugefügt. Die `CWinApp` Standardimplementierung entspricht standardmäßig dem Standardlimit der vier zuletzt verwendeten Dateien. Sie können die Standardeinstellung ändern, indem Sie mit einem größeren oder kleineren Wert aufrufen. `CWinApp::LoadStdProfileSettings` Die MRU-Liste wird in der Anwendung gespeichert. INI-Datei. Die Liste wird beim Aufrufen `InitInstance` `LoadStdProfileSettings`von in die Funktion Ihrer Anwendung geladen und beim Beenden der Anwendung gespeichert. Der BENUTZERbenutzer benutzerui MRU konvertiert auch absolute Pfade in relative Pfade zur Anzeige im Dateimenü.

   `CWinApp::OnOpenRecentFile`ist der ON_COMMAND-Handler, der den eigentlichen Befehl ausführt. Es erhält einfach den Dateinamen aus `CWinApp::OpenDocumentFile`der MRU-Liste und ruft auf, was die ganze Arbeit des Öffnens der Datei und der Aktualisierung der MRU-Liste macht.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_EDIT_CLEAR Löscht die aktuelle Auswahl

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses `CEdit::Clear`Befehls mithilfe bereit. Der Befehl ist deaktiviert, wenn keine aktuelle Auswahl vorhanden ist.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_CLEAR_ALL Löscht das gesamte Dokument.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden. Eine Beispielimplementierung finden Sie im MFC-Tutorial-Beispiel [SCRIBBLE.](../overview/visual-cpp-samples.md)

- ID_EDIT_COPY Kopiert die aktuelle Auswahl in die Zwischenablage.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, der den aktuell `CEdit::Copy`ausgewählten Text als CF_TEXT mit kopiert. Der Befehl ist deaktiviert, wenn keine aktuelle Auswahl vorhanden ist.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_CUT Schneidet die aktuelle Auswahl in die Zwischenablage.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, der den aktuell `CEdit::Cut`markierten Text in die Zwischenablage schneidet, indem CF_TEXT verwendet wird. Der Befehl ist deaktiviert, wenn keine aktuelle Auswahl vorhanden ist.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_FIND Beginnt den Findvorgang, ruft das moduslose Find-Dialogfeld auf.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, `OnEditFindReplace` die die Implementierungshilfsfunktion aufruft, um die vorherigen Einstellungen zum Suchen/Ersetzen in privaten Implementierungsvariablen zu verwenden und zu speichern. Die `CFindReplaceDialog` Klasse wird verwendet, um das moduslose Dialogfeld zu verwalten, um den Benutzer aufzufragen.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_PASTE Fügt den aktuellen Inhalt der Zwischenablage ein.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, mit dem die `CEdit::Paste`aktuellen Zwischenablagedaten kopiert werden, die den markierten Text mithilfe ersetzen. Der Befehl ist deaktiviert, wenn keine **CF_TEXT** in der Zwischenablage vorhanden ist.

   `COleClientDoc`stellt nur einen Updatebefehl-UI-Handler für diesen Befehl bereit. Wenn die Zwischenablage kein einbettbares OLE-Element/-Objekt enthält, wird der Befehl deaktiviert. Sie sind dafür verantwortlich, den Handler für den eigentlichen Befehl zu schreiben, um das eigentliche Einfügen zu tun. Wenn Ihre OLE-Anwendung auch andere Formate einfügen kann, sollten Sie ihren eigenen Updatebefehls-UI-Handler in der Ansicht oder im Dokument bereitstellen (d. h. irgendwo zuvor `COleClientDoc` im Befehlszielrouting).

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

   Verwenden Sie `COleClientItem::CanPaste`zum Ersetzen der Standard-OLE-Implementierung .

- ID_EDIT_PASTE_LINK Fügt einen Link aus dem aktuellen Inhalt der Zwischenablage ein.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `COleDocument`stellt nur einen Updatebefehl-UI-Handler für diesen Befehl bereit. Wenn die Zwischenablage kein verklinkbares OLE-Element/-Objekt enthält, wird der Befehl deaktiviert. Sie sind dafür verantwortlich, den Handler für den eigentlichen Befehl zu schreiben, um das eigentliche Einfügen zu tun. Wenn Ihre OLE-Anwendung auch andere Formate einfügen kann, sollten Sie ihren eigenen Updatebefehls-UI-Handler in der Ansicht oder im Dokument bereitstellen (d. h. irgendwo zuvor `COleDocument` im Befehlszielrouting).

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

   Verwenden Sie `COleClientItem::CanPasteLink`zum Ersetzen der Standard-OLE-Implementierung .

- ID_EDIT_PASTE_SPECIAL Fügt den aktuellen Inhalt der Zwischenablage mit Optionen ein.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren. MFC stellt dieses Dialogfeld nicht bereit.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_REPEAT Wiederholt den letzten Vorgang.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, um den letzten Findvorgang zu wiederholen. Die privaten Implementierungsvariablen für den letzten Find werden verwendet. Der Befehl ist deaktiviert, wenn ein Suchen nicht versucht werden kann.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_REPLACE Beginnt den Ersetzungsvorgang, ruft das moduslose Ersetzungsdialogfeld auf.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, `OnEditFindReplace` die die Implementierungshilfsfunktion aufruft, um die vorherigen Einstellungen zum Suchen/Ersetzen in privaten Implementierungsvariablen zu verwenden und zu speichern. Die `CFindReplaceDialog` Klasse wird verwendet, um das moduslose Dialogfeld zu verwalten, in dem der Benutzer aufgefordert wird.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_SELECT_ALL Wählt das gesamte Dokument aus.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses Befehls bereit, der den gesamten Text im Dokument auswählt. Der Befehl ist deaktiviert, wenn kein Text ausgewählt werden kann.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_UNDO den letzten Vorgang auftut.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   `CEditView`stellt eine Implementierung dieses `CEdit::Undo`Befehls mithilfe von bereit. Der Befehl ist `CEdit::CanUndo` deaktiviert, wenn FALSE zurückgegeben wird.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_EDIT_REDO Den letzten Vorgang wird erneut durchgeführt.

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für jede -abgeleitete Klasse implementieren.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_WINDOW_NEW Öffnet ein weiteres Fenster im aktiven Dokument.

   `CMDIFrameWnd::OnWindowNew`implementiert diese leistungsstarke Funktion, indem sie die Dokumentvorlage des aktuellen Dokuments verwendet, um einen anderen Rahmen zu erstellen, der eine andere Ansicht des aktuellen Dokuments enthält.

   Wie die meisten MDI-Menübefehle (Multiple Document Interface) ist der Befehl deaktiviert, wenn kein aktives untergeordnetes MDI-Fenster vorhanden ist.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen. Wenn Sie einen Befehl bereitstellen möchten, der zusätzliche Ansichten oder Framefenster erstellt, sollten Sie wahrscheinlich besser Ihren eigenen Befehl erfinden. Sie können den `CMDIFrameWnd::OnWindowNew` Code aus klonen und in den bestimmten Frame und Ansichtsklassen Ihrer Gelieben ändern.

- ID_WINDOW_ARRANGE Ordnet Symbole am unteren Rand eines MDI-Fensters an.

   `CMDIFrameWnd`implementiert diesen Standard-MDI-Befehl in `OnMDIWindowCmd`einer Implementierungshilfsfunktion . Dieser Hilfshelfer ordnet Befehls-IDs MDI-Windows-Nachrichten zu und kann daher viel Code freigeben.

   Wie die meisten MDI-Fenstermenübefehle ist der Befehl deaktiviert, wenn kein aktives untergeordnetes MDI-Fenster vorhanden ist.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_WINDOW_CASCADE Cascades-Fenster, damit sie sich überlappen.

   `CMDIFrameWnd`implementiert diesen Standard-MDI-Befehl in `OnMDIWindowCmd`einer Implementierungshilfsfunktion . Dieser Hilfshelfer ordnet Befehls-IDs MDI-Windows-Nachrichten zu und kann daher viel Code freigeben.

   Wie die meisten MDI-Fenstermenübefehle ist der Befehl deaktiviert, wenn kein aktives untergeordnetes MDI-Fenster vorhanden ist.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_WINDOW_TILE_HORZ Fenster horizontal.

   Dieser Befehl wird `CMDIFrameWnd` in genau wie ID_WINDOW_CASCADE implementiert, außer dass eine andere MDI-Windows-Nachricht für den Vorgang verwendet wird.

   Sie sollten die Standardkachelausrichtung für Ihre Anwendung auswählen. Sie können dies tun, indem Sie die ID für das Menüelement Fenster "Kachel" in ID_WINDOW_TILE_HORZ oder ID_WINDOW_TILE_VERT ändern.

- ID_WINDOW_TILE_VERT Kachelfenster vertikal.

   Dieser Befehl wird `CMDIFrameWnd` in genau wie ID_WINDOW_CASCADE implementiert, außer dass eine andere MDI-Windows-Nachricht für den Vorgang verwendet wird.

   Sie sollten die Standardkachelausrichtung für Ihre Anwendung auswählen. Sie können dies tun, indem Sie die ID für das Menüelement Fenster "Kachel" in ID_WINDOW_TILE_HORZ oder ID_WINDOW_TILE_VERT ändern.

- ID_WINDOW_SPLIT Tastaturschnittstelle zum Splitter.

   `CView`behandelt diesen Befehl `CSplitterWnd` für die Implementierung. Wenn die Ansicht Teil eines Splitterfensters ist, wird `CSplitterWnd::DoKeyboardSplit`dieser Befehl an die Implementierungsfunktion delegiert. Dadurch wird der Splitter in einen Modus versetzt, der es Tastaturbenutzern ermöglicht, ein Splitterfenster aufzuteilen oder aufzuteilen.

   Dieser Befehl ist deaktiviert, wenn sich die Ansicht nicht in einem Splitter befindet.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_APP_ABOUT Ruft das Dialogfeld Über auf.

   Es gibt keine Standardimplementierung für die About-Box einer Anwendung. Die von AppWizard erstellte Standardanwendung erstellt eine benutzerdefinierte Dialogfeldklasse für Ihre Anwendung und verwendet sie als Info-Feld. AppWizard schreibt auch den trivialen Befehlshandler, der diesen Befehl verarbeitet und das Dialogfeld aufruft.

   Sie implementieren diesen Befehl fast immer.

- ID_APP_EXIT beenden Sie die Anwendung.

   `CWinApp::OnAppExit`behandelt diesen Befehl, indem eine WM_CLOSE Nachricht an das Hauptfenster der Anwendung gesendet wird. Das standardmäßige Herunterfahren der Anwendung (Eingabeaufforderung für schmutzige Dateien `CFrameWnd` usw.) wird von der Implementierung behandelt.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen. Es `CWinApp::SaveAllModified` wird `CFrameWnd` empfohlen, die Abschließende Logik zu überschreiben oder zu schließen.

   Wenn Sie diesen Befehl implementieren möchten, wird empfohlen, diese Befehls-ID zu verwenden.

- ID_HELP_INDEX Listet Hilfethemen aus auf. HLP-Datei.

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CWinApp::OnHelpIndex`behandelt diesen Befehl, indem `CWinApp::WinHelp`er trivial aufruft.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_HELP_USING Zeigt Hilfe zur Verwendung der Hilfe an.

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CWinApp::OnHelpUsing`behandelt diesen Befehl, indem `CWinApp::WinHelp`er trivial aufruft.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_CONTEXT_HELP wechselt in den UMSCHALT-F1-Hilfemodus.

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CWinApp::OnContextHelp`behandelt diesen Befehl, indem der Hilfemoduscursor festgelegt wird, eine modale Schleife eingibt und darauf wartet, dass der Benutzer ein Fenster auswählt, in dem Hilfe angezeigt wird. Weitere Informationen zur MFC-Hilfe-Implementierung finden Sie im [Technischen Hinweis 28.](../mfc/tn028-context-sensitive-help-support.md)

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_HELP Gibt Hilfe zum aktuellen Kontext

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   `CWinApp::OnHelp`behandelt diesen Befehl, indem der richtige Hilfekontext für den aktuellen Anwendungskontext ab. Dies behandelt einfache F1-Hilfe, Hilfe in Meldungsfeldern und so weiter. Weitere Informationen zur MFC-Hilfeimplementierung finden Sie im [Technischen Hinweis 28.](../mfc/tn028-context-sensitive-help-support.md)

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_DEFAULT_HELP Zeigt Standardhilfe für Kontext an

    > [!NOTE]
    >  Sie müssen diese `CWinApp`Verbindung mit der Nachrichtenzuordnung Ihrer -abgeleiteten Klasse herstellen, um diese Funktionalität zu aktivieren.

   Dieser Befehl wird normalerweise `CWinApp::OnHelpIndex`zugeordnet.

   Ein anderer Befehlshandler kann bereitgestellt werden, wenn eine Unterscheidung zwischen der Standardhilfe und dem Hilfeindex gewünscht wird.

- ID_NEXT_PANE Geht zum nächsten Bereich

   `CView`behandelt diesen Befehl `CSplitterWnd` für die Implementierung. Wenn die Ansicht Teil eines Splitterfensters ist, wird `CSplitterWnd::OnNextPaneCmd`dieser Befehl an die Implementierungsfunktion delegiert. Dadurch wird die aktive Ansicht in den nächsten Bereich im Splitter verschoben.

   Dieser Befehl ist deaktiviert, wenn sich die Ansicht nicht in einem Splitter befindet oder kein nächster Bereich vorhanden ist.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_PREV_PANE Geht zum vorherigen Bereich

   `CView`behandelt diesen Befehl `CSplitterWnd` für die Implementierung. Wenn die Ansicht Teil eines Splitterfensters ist, wird `CSplitterWnd::OnNextPaneCmd`dieser Befehl an die Implementierungsfunktion delegiert. Dadurch wird die aktive Ansicht in den vorherigen Bereich im Splitter verschoben.

   Dieser Befehl ist deaktiviert, wenn sich die Ansicht nicht in einem Splitter befindet oder kein vorheriger Bereich vorhanden ist.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_OLE_INSERT_NEW Fügt ein neues OLE-Objekt ein

   Derzeit gibt es keine Standardimplementierung für diesen Befehl. Sie müssen dies `CView`für die -abgeleitete Klasse implementieren, um ein neues OLE-Element/Objekt bei der aktuellen Auswahl einzufügen.

   Alle OLE-Clientanwendungen sollten diesen Befehl implementieren. AppWizard erstellt mit der OLE-Option eine `OnInsertObject` Skelettimplementierung von in Ihrer Ansichtsklasse, die Sie abschließen müssen.

   Eine vollständige Implementierung dieses Befehls finden Sie im [OCLIENT-Beispiel](../overview/visual-cpp-samples.md) für MFC OLE.

- ID_OLE_EDIT_LINKS Edits OLE-Links

   `COleDocument`behandelt diesen Befehl mithilfe der von MFC bereitgestellten Implementierung des Standarddialogfelds ole-Links. Auf die Implementierung dieses Dialogfelds wird über die `COleLinksDialog` Klasse zugegriffen. Wenn das aktuelle Dokument keine Verknüpfungen enthält, wird der Befehl deaktiviert.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_OLE_VERB_FIRST... LAST Ein ID-Bereich für OLE-Verben

   `COleDocument`verwendet diesen Befehls-ID-Bereich für die Verben, die vom aktuell ausgewählten OLE-Element/Objekt unterstützt werden. Dies muss ein Bereich sein, da ein bestimmtes OLE-Element/Objekttyp null oder mehr benutzerdefinierte Verben unterstützen kann. Im Menü Ihrer Anwendung sollten Sie ein Menüelement mit der ID ID_OLE_VERB_FIRST. Wenn das Programm ausgeführt wird, wird das Menü mit dem entsprechenden Menü verb Beschreibung (oder Pop-up-Menü mit vielen Verben) aktualisiert. Die Verwaltung des OLE-Menüs `AfxOleSetEditMenu`wird von behandelt, die im Befehlsbefehl UI-Handler für diesen Befehl ausgeführt wird.

   Es gibt keine expliziten Befehlshandler für die Behandlung jeder Befehls-ID in diesem Bereich. `COleDocument::OnCmdMsg`wird überschrieben, um alle Befehls-IDs in diesem Bereich abzufangen, sie in Null-basierte Verbnummern umzuwandeln und den Server für dieses Verb zu starten (mit `COleClientItem::DoVerb`).

   Eine Anpassung oder andere Verwendung dieses Befehls-ID-Bereichs wird nicht empfohlen.

- ID_VIEW_TOOLBAR Schaltet die Symbolleiste ein und aus

   `CFrameWnd`behandelt diesen Befehl und den befehlsorientierten UI-Handler, um den sichtbaren Status der Symbolleiste umzuschalten. Die Symbolleiste muss ein untergeordnetes Fenster des Rahmens mit der untergeordneten Fenster-ID von AFX_IDW_TOOLBAR sein. Der Befehlshandler schaltet tatsächlich die Sichtbarkeit des Symbolleistenfensters um. `CFrameWnd::RecalcLayout`wird verwendet, um das Rahmenfenster mit der Symbolleiste in ihrem neuen Zustand neu zu zeichnen. Der befehlsorientierte UI-Handler überprüft das Menüelement, wenn die Symbolleiste sichtbar ist.

   Die Anpassung dieses Befehlshandlers wird nicht empfohlen. Wenn Sie zusätzliche Symbolleisten hinzufügen möchten, sollten Sie den Befehlshandler und den befehls-befehlsui-Handler für diesen Befehl klonen und ändern.

- ID_VIEW_STATUS_BAR Schaltet die Statusleiste ein und aus

   Dieser Befehl wird `CFrameWnd` in genau wie ID_VIEW_TOOLBAR implementiert, außer dass eine andere untergeordnete Fenster-ID (AFX_IDW_STATUS_BAR) verwendet wird.

## <a name="update-only-command-handlers"></a>Nur Update-Befehlshandler

Mehrere Standardbefehls-IDs werden als Indikatoren in Statusleisten verwendet. Diese verwenden denselben Mechanismus für die Benutzeroberfläche, um ihren aktuellen visuellen Status während der Laufzeit der Anwendung anzuzeigen. Da sie vom Benutzer nicht ausgewählt werden können (d. h., Sie können einen Statusleistenbereich nicht übertragen), macht es keinen Sinn, einen ON_COMMAND Handler für diese Befehls-IDs zu haben.

- ID_INDICATOR_CAPS : CAP-Sperranzeige.

- ID_INDICATOR_NUM : NUM-Sperranzeige.

- ID_INDICATOR_SCRL : SCRL-Sperranzeige.

- ID_INDICATOR_KANA : KANA-Sperranzeige (gilt nur für japanische Systeme).

Alle drei werden in `CFrameWnd::OnUpdateKeyIndicator`implementiert, einem Implementierungshelfer, der die Befehls-ID verwendet, um dem entsprechenden virtuellen Schlüssel zuzuordnen. Eine gemeinsame Implementierung aktiviert oder deaktiviert (für Statusbereiche `CCmdUI` deaktiviert = kein Text), je nachdem, ob der entsprechende virtuelle Schlüssel derzeit gesperrt ist.

Die Anpassung dieses Befehlshandlers wird nicht empfohlen.

- ID_INDICATOR_EXT : EXTended Select-Indikator.

- ID_INDICATOR_OVR : OVeRstrike-Anzeige.

- ID_INDICATOR_REC : RECording-Anzeige.

Derzeit gibt es keine Standardimplementierung für diese Indikatoren.

Wenn Sie sich für die Implementierung dieser Indikatoren entscheiden, empfehlen wir Ihnen, diese Indikator-IDs zu verwenden und die Reihenfolge der Indikatoren in Ihrer Statusleiste beizubehalten (d. h. in dieser Reihenfolge: EXT, CAP, NUM, SCRL, OVR, REC).

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
