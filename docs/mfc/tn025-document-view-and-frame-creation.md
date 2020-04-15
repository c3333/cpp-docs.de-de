---
title: 'TN025: Dokument-, Ansicht- und Frame-Erstellung'
ms.date: 11/04/2016
f1_keywords:
- vc.creation
helpviewer_keywords:
- documents [MFC], view and frame creation
- TN025
ms.assetid: 09254d72-6e1d-43db-80e9-693887dbeda2
ms.openlocfilehash: 2fdabdcb1a87d4a5661348588d49303290c966ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370370"
---
# <a name="tn025-document-view-and-frame-creation"></a>TN025: Dokument-, Ansicht- und Frame-Erstellung

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

Dieser Hinweis beschreibt die Erstellungs- und Besitzprobleme für WinApps, DocTemplates, Dokumente, Frames und Ansichten.

## <a name="winapp"></a>Winapp

Es gibt `CWinApp` ein Objekt im System.

Es wird statisch konstruiert und durch die interne `WinMain`Implementierung von des Frameworks initialisiert. Sie müssen `CWinApp` ableiten, um etwas Nützliches zu tun (Ausnahme: MFC-Erweiterungs-DLLs sollten keine `CWinApp` Instanz haben – stattdessen wird die `DllMain` Initialisierung durchgeführt).

Das `CWinApp` eine Objekt besitzt eine Liste von `CPtrList`Dokumentvorlagen (a ). Es gibt eine oder mehrere Dokumentvorlagen pro Anwendung. DocTemplates werden normalerweise aus der Ressourcendatei (d. `CWinApp::InitInstance`h. einem Zeichenfolgenarray) in geladen.

```
pTemplate = new CDocTemplate(IDR_MYDOCUMENT, ...);

AddDocTemplate(pTemplate);
```

Das `CWinApp` eine Objekt besitzt alle Rahmenfenster in der Anwendung. Das Hauptrahmenfenster für die Anwendung `CWinApp::m_pMainWnd`sollte in gespeichert werden; In der *m_pMainWnd* Regel `InitInstance` legen Sie m_pMainWnd in der Implementierung fest, wenn Sie AppWizard es nicht für Sie tun lassen. Für Single Document Interface (SDI) dient `CFrameWnd` dies als Hauptanwendungsrahmenfenster sowie als einziges Dokumentrahmenfenster. Bei Multi Document Interface (MDI) handelt es `CMDIFrameWnd`sich um einen MDI-Frame (Klasse `CFrameWnd`), der als Hauptanwendungsrahmenfenster dient, das alle untergeordneten Dateien enthält. Jedes untergeordnete Fenster `CMDIChildWnd` ist von `CFrameWnd`Klasse (abgeleitet von ) und dient als eines von potenziell vielen Dokumentrahmenfenstern.

## <a name="doctemplates"></a>DocTemplates

Der `CDocTemplate` ist der Ersteller und Manager von Dokumenten. Sie besitzt die Dokumente, die sie erstellt. Wenn Ihre Anwendung den unten beschriebenen ressourcenbasierten Ansatz verwendet, `CDocTemplate`muss sie nicht von ableiten.

Bei einer SDI-Anwendung `CSingleDocTemplate` verfolgt die Klasse ein geöffnetes Dokument. Für eine MDI-Anwendung `CMultiDocTemplate` führt die `CPtrList`Klasse eine Liste (a ) aller aktuell geöffneten Dokumente, die aus dieser Vorlage erstellt wurden. `CDocTemplate::AddDocument`und `CDocTemplate::RemoveDocument` stellen Sie die funktionen des virtuellen Elements zum Hinzufügen oder Entfernen eines Dokuments aus der Vorlage bereit. `CDocTemplate`ist ein `CDocument` Freund von, so `CDocument::m_pDocTemplate` dass wir den geschützten Zurück-Zeiger so einstellen können, dass er auf die Doc-Vorlage zurückzeigt, die das Dokument erstellt hat.

`CWinApp`behandelt die `OnFileOpen` Standardimplementierung, die wiederum alle Doc-Vorlagen abfragt. Die Implementierung umfasst die Suche nach bereits geöffneten Dokumenten und die Entscheidung, in welchem Format neue Dokumente geöffnet werden sollen.

`CDocTemplate`verwaltet die UI-Bindung für Dokumente und Frames.

`CDocTemplate`hält die Anzahl der unbenannten Dokumente.

## <a name="cdocument"></a>CDocument

A `CDocument` ist im `CDocTemplate`Besitz einer .

Dokumente verfügen über eine Liste der `CView`derzeit geöffneten Ansichten `CPtrList`(abgeleitet von ), die das Dokument anzeigen (a ).

Dokumente erstellen/zerstören die Ansichten nicht, aber sie werden nach ihrer Erstellung miteinander verbunden. Wenn ein Dokument geschlossen wird (d. h. über Datei/Schließen), werden alle angehängten Ansichten geschlossen. Wenn die letzte Ansicht eines Dokuments geschlossen wird (d. h. Fenster/Schließen), wird das Dokument geschlossen.

Die `CDocument::AddView` `RemoveView` Schnittstelle wird verwendet, um die Ansichtsliste zu verwalten. `CDocument`ist ein `CView` Freund von, `CView::m_pDocument` so dass wir den hinteren Zeiger setzen können.

## <a name="cframewnd"></a>CFrameWnd

A `CFrameWnd` (auch als Frame bezeichnet) spielt die gleiche Rolle wie in `CFrameWnd` MFC 1.0, aber jetzt ist die Klasse so konzipiert, dass sie in vielen Fällen verwendet wird, ohne eine neue Klasse abzuleiten. Die abgeleiteten Klassen `CMDIFrameWnd` und `CMDIChildWnd` sind auch erweitert, so dass viele Standardbefehle bereits implementiert sind.

Der `CFrameWnd` ist für das Erstellen von Fenstern im Clientbereich des Rahmens verantwortlich. Normalerweise gibt es ein Hauptfenster, das den Clientbereich des Rahmens füllt.

Bei einem MDI-Frame-Fenster wird der Clientbereich mit dem MDICLIENT-Steuerelement gefüllt, das wiederum das übergeordnete Element aller MDI-Child-Rahmenfenster ist. Bei einem SDI-Frame-Fenster oder einem MDI-Child-Rahmenfenster wird `CView`der Clientbereich in der Regel mit einem -abgeleiteten Fensterobjekt gefüllt. Im Fall `CSplitterWnd`von wird der Clientbereich der `CSplitterWnd` Ansicht mit dem `CView`Fensterobjekt gefüllt, und die -abgeleiteten Fensterobjekte `CSplitterWnd`(eines pro geteiltem Bereich) werden als untergeordnete Fenster des erstellt.

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)
