---
title: Rahmenfensterstile (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: 3c22944537370a44aee1af1cf71281264ed4969b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626453"
---
# <a name="frame-window-styles-c"></a>Rahmenfensterstile (C++)

Die Rahmen Fenster, die Sie mit dem Framework erhalten, eignen sich für die meisten Programme, Sie können jedoch zusätzliche Flexibilität erzielen, indem Sie die erweiterten Funktionen [prekreatewindow](reference/cwnd-class.md#precreatewindow) und die globale MFC-Funktion [AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass)verwenden. `PreCreateWindow`ist eine Member-Funktion von `CWnd` .

Wenn Sie die **WS_HSCROLL** -und **WS_VSCROLL** Stile auf das Hauptrahmen Fenster anwenden, werden Sie stattdessen auf das **MdiClient** -Fenster angewendet, damit Benutzer einen Bildlauf im **MdiClient** -Bereich durchführen können.

Wenn das **FWS_ADDTOTITLE** Stilbit des Fensters festgelegt ist (standardmäßig), teilt die Ansicht dem Rahmen Fenster mit, welcher Titel in der Titelleiste des Fensters auf der Grundlage des Dokument namens der Ansicht angezeigt werden soll.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- Verwalten von untergeordneten [MDI-Fenstern (MdiClient)](managing-mdi-child-windows.md), das Fenster in einem MDI-Frame, der die untergeordneten MDI-Fenster enthält

- [Ändern der Stile eines mit MFC erstellten Fensters](changing-the-styles-of-a-window-created-by-mfc.md)

- [Fenster Stile](reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Siehe auch

[Rahmenfenster](frame-windows.md)
