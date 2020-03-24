---
title: Erstellen einer MFC-Anwendung im Webbrowserstil
ms.date: 06/25/2018
f1_keywords:
- vc.appwiz.mfcweb.project
helpviewer_keywords:
- MFC, Web applications
- Web browsers, creating from MFC architecture
- Web browsers
- Web applications [MFC], creating
ms.assetid: 257f8c03-33c3-428c-832e-0b70aff6168d
ms.openlocfilehash: e02e928f65ab4cd918e730135abc62ed3237decf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215123"
---
# <a name="creating-a-web-browser-style-mfc-application"></a>Erstellen einer MFC-Anwendung im Webbrowserstil

Eine Webbrowser-Anwendung kann auf Informationen aus dem Internet (z. b. html-oder aktive Dokumente), ein Intranet sowie Ordner im lokalen Dateisystem und in einem Netzwerk zugreifen. Durch das Ableiten der Ansichts Klasse der Anwendung aus [CHtmlView](../../mfc/reference/chtmlview-class.md)machen Sie die Anwendung effektiv zu einem Webbrowser, indem Sie die Ansicht mit dem Webbrowser-Steuerelement bereitstellen.

## <a name="to-create-a-web-browser-application-based-on-the-mfc-documentview-architecture"></a>So erstellen Sie eine Webbrowser Anwendung, die auf der MFC-Dokument-/Ansichtarchitektur basiert

1. Befolgen Sie die Anweisungen unter [Erstellen einer MFC-Anwendung](../../mfc/reference/creating-an-mfc-application.md).

1. Stellen Sie auf der Seite [Anwendungstyp](../../mfc/reference/application-type-mfc-application-wizard.md) des MFC-Anwendungs-Assistenten sicher, dass das Feld **Dokument-/sichtsarchitektur** ausgewählt ist. (Sie können entweder **ein einzelnes Dokument** oder **mehrere Dokumente**auswählen, aber keine **Dialog**Felder.)

1. Verwenden Sie auf der Seite [generierte Klassen überprüfen](../../mfc/reference/generated-classes-mfc-application-wizard.md) das Dropdown Menü **Basisklasse** , um `CHtmlView`auszuwählen.

1. Wählen Sie alle anderen Optionen aus, die in die Skeleton-Anwendung integriert werden sollen.

1. Klicken Sie auf **Fertig stellen**.

Das WebBrowser-Steuerelement unterstützt das Browsen durch Hyperlinks und die Uniform Resource Locator Navigation (URL). Das-Steuerelement verwaltet eine Verlaufs Liste, die es dem Benutzer ermöglicht, zuvor durchsuchte Websites, Ordner und Dokumente vorwärts und rückwärts zu suchen. Das-Steuerelement behandelt direkt die Navigation, Hyperlinks, Verlaufs Listen, Favoriten und Sicherheit. Anwendungen können das WebBrowser-Steuerelement als aktiven Dokument Container verwenden, um auch aktive Dokumente zu hosten. Daher können umfangreich formatierte Dokumente, wie z. b. Microsoft Excel-Kalkulations Tabellen oder Word-Dokumente, direkt im Webbrowser-Steuerelement geöffnet und bearbeitet werden. Das WebBrowser-Steuerelement ist auch ein ActiveX-Steuerelement Container, der beliebige ActiveX-Steuerelemente hosten kann

> [!NOTE]
> Das WebBrowser-ActiveX-Steuerelement (und somit `CHtmlView`) ist nur für Anwendungen verfügbar, die unter Windows-Versionen ausgeführt werden, in denen Internet Explorer 4,0 oder höher installiert ist.

Da `CHtmlView` einfach das Microsoft Webbrowser-Steuerelement implementiert, ist die Unterstützung für das Drucken nicht wie andere [CView](../../mfc/reference/cview-class.md)-abgeleitete Klassen. Stattdessen implementiert das WebBrowser-Steuerelement die Benutzeroberfläche des Druckers und druckt. Das Ergebnis ist, dass `CHtmlView` die Seitenansicht nicht unterstützt, und das Framework bietet keine anderen Druck Unterstützungsfunktionen an: z. b. [CView:: OnPreparePrinting](../../mfc/reference/cview-class.md#onprepareprinting), [CView:: OnBeginPrinting](../../mfc/reference/cview-class.md#onbeginprinting)und [CView:: OnEndPrinting](../../mfc/reference/cview-class.md#onendprinting), die in anderen MFC-Anwendungen verfügbar sind.

`CHtmlView` fungiert als Wrapper für das WebBrowser-Steuerelement, das der Anwendung eine Ansicht für eine Web-oder eine HTML-Seite bietet. Der Assistent erstellt eine außer Kraft setzung für die [OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate) -Funktion in der Ansichts Klasse und stellt einen Navigations Link zur C++ Microsoft Visual-Website bereit:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    Navigate2(_T("http://www.docs.microsoft.com/"),
        NULL,
        NULL);
}
```

Sie können diese Website durch einen eigenen ersetzen, oder Sie können die [loadfromresource](../../mfc/reference/chtmlview-class.md#loadfromresource) -Member-Funktion verwenden, um eine HTML-Seite zu öffnen, die sich im Ressourcen Skript des Projekts als Standard Inhalt für die Ansicht befindet. Beispiel:

```cpp
void CWebView::OnInitialUpdate()
{
    CHtmlView::OnInitialUpdate();

    // TODO: This code navigates to a popular spot on the web.
    // Change the code to go where you'd like.
    LoadFromResource(IDR_HTML1);
}
```

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel-MFCIE](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/internet)<br/>
[MFC-Anwendungs-Assistent](../../mfc/reference/mfc-application-wizard.md)<br/>
[Festlegen der Compiler- und Buildeigenschaften](../../build/working-with-project-properties.md)<br/>
[Eigenschaftenseiten](../../build/reference/property-pages-visual-cpp.md)<br/>
[Festlegen der Compiler- und Buildeigenschaften](../../build/working-with-project-properties.md)
