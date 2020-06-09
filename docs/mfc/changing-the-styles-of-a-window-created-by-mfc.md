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
ms.openlocfilehash: f3fd9f83112737e944d83cf00da685d81fe8b2a7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624951"
---
# <a name="changing-the-styles-of-a-window-created-by-mfc"></a>Ändern der Stile eines mit MFC erstellten Fensters

In seiner Version der `WinMain` Funktion registriert MFC mehrere Standardfenster Klassen für Sie. Da Sie MFC normalerweise nicht bearbeiten `WinMain` , bietet diese Funktion keine Möglichkeit, die MFC-Standardfenster Stile zu ändern. In diesem Artikel wird erläutert, wie Sie die Stile einer solchen vorab registrierten Fenster Klasse in einer vorhandenen Anwendung ändern können.

## <a name="changing-styles-in-a-new-mfc-application"></a><a name="_core_changing_styles_in_a_new_mfc_application"></a>Ändern von Stilen in einer neuen MFC-Anwendung

Wenn Sie Visual C++ 2,0 oder höher verwenden, können Sie die Standardfenster Stile im Anwendungs-Assistenten ändern, wenn Sie die Anwendung erstellen. Auf der Seite Benutzeroberflächen Features des Anwendungs-Assistenten können Sie Stile für das Hauptrahmen Fenster und die untergeordneten MDI-Fenster ändern. Für beide Fenstertypen können Sie die Rahmen Stärke (Thick oder Thin) und eine der folgenden Optionen angeben:

- Ob das Fenster Steuerelemente minimieren oder maximieren soll.

- Gibt an, ob das Fenster anfänglich minimiert, maximiert oder keines von beiden angezeigt wird.

Bei Hauptrahmen Fenstern können Sie auch angeben, ob das Fenster über ein System Menü verfügt. Für untergeordnete MDI-Fenster können Sie angeben, ob das Fenster Splitter Bereiche unterstützt.

## <a name="changing-styles-in-an-existing-application"></a><a name="_core_changing_styles_in_an_existing_application"></a>Ändern von Stilen in einer vorhandenen Anwendung

Wenn Sie in einer vorhandenen Anwendung Fenster Attribute ändern, befolgen Sie stattdessen die Anweisungen im Rest dieses Artikels.

Wenn Sie die standardmäßigen Fenster Attribute ändern möchten, die von einer Framework-Anwendung verwendet werden, die mit dem Anwendungs-Assistenten erstellt wurde, überschreiben Sie [die virtuelle Member-Funktion des Fensters](reference/cwnd-class.md#precreatewindow) . `PreCreateWindow`ermöglicht einer Anwendung den Zugriff auf den Erstellungs Prozess, der normalerweise intern von der [CDocTemplate](reference/cdoctemplate-class.md) -Klasse verwaltet wird. Das Framework ruft `PreCreateWindow` unmittelbar vor dem Erstellen des Fensters auf. Durch Ändern der an bestandenen [Struktur "](/windows/win32/api/winuser/ns-winuser-createstructw) Erstellungs Struktur" `PreCreateWindow` kann die Anwendung die zum Erstellen des Fensters verwendeten Attribute ändern. Um z. b. sicherzustellen, dass ein Fenster keine Beschriftung verwendet, verwenden Sie den folgenden bitweisen Vorgang:

[!code-cpp[NVC_MFCDocView#15](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_1.cpp)]

Die [CTRLBARS](../overview/visual-cpp-samples.md) -Beispielanwendung veranschaulicht diese Vorgehensweise zum Ändern von Fenster Attributen. Je nachdem, was sich in der Anwendung ändert `PreCreateWindow` , kann es erforderlich sein, die Basisklassen Implementierung der Funktion aufzurufen.

In der folgenden Erörterung werden die SDI-und [MDI](#_core_the_mdi_case)-Fälle behandelt.

## <a name="the-sdi-case"></a><a name="_core_the_sdi_case"></a>Der SDI-Fall

In einer Anwendung mit einer einzelnen Dokument Schnittstelle (SDI) ist der Standardfenster Stil im Framework eine Kombination aus den **WS_OVERLAPPEDWINDOW** -und **FWS_ADDTOTITLE** Stilen. **FWS_ADDTOTITLE** ist ein MFC-spezifischer Stil, der das Framework anweist, den Dokumenttitel der Beschriftung des Fensters hinzuzufügen. Um die Fenster Attribute in einer SDI-Anwendung zu ändern, überschreiben Sie die- `PreCreateWindow` Funktion in der von abgeleiteten Klasse `CFrameWnd` (die der Anwendungs-Assistent benennt `CMainFrame` ). Beispiel:

[!code-cpp[NVC_MFCDocViewSDI#11](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_2.cpp)]

Mit diesem Code wird ein Hauptrahmen Fenster erstellt, ohne Schaltflächen zu minimieren und zu maximieren. Das Fenster wird anfänglich auf dem Bildschirm zentriert.

## <a name="the-mdi-case"></a><a name="_core_the_mdi_case"></a>Der MDI-Fall

Es ist etwas mehr Arbeit erforderlich, um den Fenster Stil eines untergeordneten Fensters in einer MDI-Anwendung (Multiple Document Interface) zu ändern. Standardmäßig verwendet eine MDI-Anwendung, die mit dem Anwendungs-Assistenten erstellt wurde, die in MFC definierte [CMDIChildWnd](reference/cmdichildwnd-class.md) -Standardklasse. Um den Fenster Stil eines untergeordneten MDI-Fensters zu ändern, müssen Sie eine neue Klasse von ableiten `CMDIChildWnd` und alle Verweise auf `CMDIChildWnd` in Ihrem Projekt durch Verweise auf die neue Klasse ersetzen. Höchstwahrscheinlich befindet sich der einzige Verweis auf `CMDIChildWnd` in der Anwendung in der Member-Funktion Ihrer Anwendung `InitInstance` .

Der standardmäßige Fenster Stil, der in einer MDI-Anwendung verwendet wird, ist eine Kombination der Stile **WS_CHILD**, **WS_OVERLAPPEDWINDOW**und **FWS_ADDTOTITLE** . Um die Fenster Attribute der untergeordneten Fenster einer MDI-Anwendung zu ändern, überschreiben Sie die [prekreatewindow](reference/cwnd-class.md#precreatewindow) -Funktion in der von abgeleiteten Klasse `CMDIChildWnd` . Beispiel:

[!code-cpp[NVC_MFCDocView#16](codesnippet/cpp/changing-the-styles-of-a-window-created-by-mfc_3.cpp)]

Dieser Code erstellt untergeordnete MDI-Fenster ohne die Schaltfläche maximieren.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Windows-Stile](reference/styles-used-by-mfc.md#window-styles)

- [Rahmen Fenster Stile](frame-window-styles-cpp.md)

- [Fenster Stile](/windows/win32/winmsg/window-styles)

## <a name="see-also"></a>Siehe auch

[Rahmenfensterstile](frame-window-styles-cpp.md)
