---
title: Ändern der Stile eines mit MFC erstellten Fensters
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- WS_OVERLAPPEDWINDOW macro [MFC]
- single document interface (SDI), changing window attributes
- MDI [MFC], window styles
- windows [MFC], MFC
- child windows [MFC], styles
- MFC, windows
- CFrameWnd class [MFC], window styles
- CREATESTRUCT macro [MFC]
- CMDIChildWnd class [MFC], changing window styles
- multidocument interface style
- PreCreateWindow method [MFC], window styles
- single document interface (SDI), style
- default window style
- defaults [MFC], window style
- PreCreateWindow method [MFC], changing window styles
- CMainFrame class [MFC]
- styles [MFC], windows
ms.assetid: 77fa4f03-96b4-4687-9ade-41e46f7e4b0a
ms.openlocfilehash: 221092eb25a4f044cda5b379d6774659d9e9d2d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374593"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Ändern der Stile eines mit MFC erstellten Fensters

In seiner Version `WinMain` der Funktion registriert MFC mehrere Standardfensterklassen für Sie. Da Sie normalerweise keine MFC-Funktionen `WinMain`bearbeiten, haben Sie mit dieser Funktion keine Möglichkeit, die MFC-Standardfensterstile zu ändern. In diesem Artikel wird erläutert, wie Sie die Stile einer solchen vorregistrierten Fensterklasse in einer vorhandenen Anwendung ändern können.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Ändern von Stilen in einer neuen MFC-Anwendung

Wenn Sie Visual C++ 2.0 oder höher verwenden, können Sie beim Erstellen der Anwendung die Standardfensterstile im Anwendungs-Assistenten ändern. Auf der Seite Benutzeroberflächenfeatures des Anwendungs-Assistenten können Sie Stile für das Hauptrahmenfenster und die untergeordneten MDI-Fenster ändern. Für beide Fenstertypen können Sie die Rahmendicke (dick oder dünn) und eine der folgenden Optionen angeben:

- Gibt an, ob das Fenster Steuerelemente minimieren oder maximieren hat.

- Gibt an, ob das Fenster zunächst minimiert, maximiert oder nicht angezeigt wird.

Für Hauptrahmenfenster können Sie auch angeben, ob das Fenster über ein Systemmenü verfügt. Für untergeordnete MDI-Fenster können Sie angeben, ob das Fenster Splitterbereiche unterstützt.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Ändern von Stilen in einer vorhandenen Anwendung

Wenn Sie Fensterattribute in einer vorhandenen Anwendung ändern, befolgen Sie stattdessen die Anweisungen im Rest dieses Artikels.

Um die Standardfensterattribute zu ändern, die von einer Frameworkanwendung verwendet werden, die mit dem Anwendungs-Assistenten erstellt wurde, überschreiben Sie die virtuelle [Memberfunktion PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) des Fensters. `PreCreateWindow`ermöglicht einer Anwendung den Zugriff auf den Erstellungsprozess, der normalerweise intern von der [CDocTemplate-Klasse](../mfc/reference/cdoctemplate-class.md) verwaltet wird. Das Framework `PreCreateWindow` ruft kurz vor dem Erstellen des Fensters auf. Durch Ändern der [CREATESTRUCT-Struktur,](/windows/win32/api/winuser/ns-winuser-createstructw) die an `PreCreateWindow`übergeben wird, kann Ihre Anwendung die Attribute ändern, die zum Erstellen des Fensters verwendet werden. Um beispielsweise sicherzustellen, dass ein Fenster keine Beschriftung verwendet, verwenden Sie den folgenden bitweisen Vorgang:

[!code-cpp[NVC_MFCDocView#15](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

Die [Beispielanwendung STRGBARS](../overview/visual-cpp-samples.md) veranschaulicht diese Technik zum Ändern von Fensterattributen. Je nachdem, was `PreCreateWindow`ihre Anwendung in ändert, kann es erforderlich sein, die Basisklassenimplementierung der Funktion aufzurufen.

Die folgende Diskussion behandelt den Fall SDI und den [MDI-Fall](#_core_the_mdi_case).

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>Der Fall SDI

In einer SDI-Anwendung (Single Document Interface) ist der Standardfensterstil im Framework eine Kombination aus **WS_OVERLAPPEDWINDOW** und **FWS_ADDTOTITLE** Formatvorlagen. **FWS_ADDTOTITLE** ist ein MFC-spezifischer Stil, der das Framework anweist, den Dokumenttitel der Beschriftung des Fensters hinzuzufügen. Um die Fensterattribute in einer SDI-Anwendung `PreCreateWindow` zu ändern, `CFrameWnd` überschreiben Sie die `CMainFrame`Funktion in Ihrer Klasse, die von (von der der Anwendungs-Assistenten bezeichnet) abgeleitet wurde. Beispiel:

[!code-cpp[NVC_MFCDocViewSDI#11](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Dieser Code erstellt ein Hauptrahmenfenster ohne Schaltflächen Minimieren und Maximieren und ohne einen großen Rahmen. Das Fenster wird zunächst auf dem Bildschirm zentriert.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>Der MDI-Fall

Es ist etwas mehr Arbeit erforderlich, um den Fensterstil eines untergeordneten Fensters in einer MDI-Anwendung (Multiple Document Interface) zu ändern. Standardmäßig verwendet eine mit dem Anwendungs-Assistenten erstellte MDI-Anwendung die in MFC definierte Standardklasse [CMDIChildWnd.](../mfc/reference/cmdichildwnd-class.md) Um den Fensterstil eines untergeordneten MDI-Fensters zu `CMDIChildWnd` ändern, müssen `CMDIChildWnd` Sie eine neue Klasse ableiten und alle Verweise in Ihrem Projekt durch Verweise auf die neue Klasse ersetzen. Wahrscheinlich befindet sich der `CMDIChildWnd` einzige Verweis in der Anwendung `InitInstance` in der Memberfunktion Ihrer Anwendung.

Der In einer MDI-Anwendung verwendete Standardfensterstil ist eine Kombination aus den Stilen **WS_CHILD**, **WS_OVERLAPPEDWINDOW**und **FWS_ADDTOTITLE.** Um die Fensterattribute der untergeordneten Fenster einer MDI-Anwendung zu ändern, überschreiben `CMDIChildWnd`Sie die [PreCreateWindow-Funktion](../mfc/reference/cwnd-class.md#precreatewindow) in Ihrer Klasse, die von abgeleitet ist. Beispiel:

[!code-cpp[NVC_MFCDocView#16](../mfc/codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Dieser Code erstellt untergeordnete MDI-Fenster ohne Schaltfläche Maximieren.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Windows-Stile](../mfc/reference/styles-used-by-mfc.md#window-styles)

- [Rahmenfensterstile](../mfc/frame-window-styles-cpp.md)

- [Fensterstile](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Siehe auch

[Rahmenfensterstile](../mfc/frame-window-styles-cpp.md)
