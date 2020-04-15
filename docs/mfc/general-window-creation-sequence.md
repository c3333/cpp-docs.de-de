---
title: Allgemeine Ablauffolge bei der Fenstererstellung
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364272"
---
# <a name="general-window-creation-sequence"></a>Allgemeine Ablauffolge bei der Fenstererstellung

Wenn Sie ein eigenes Fenster erstellen, z. B. ein untergeordnetes Fenster, verwendet das Framework in etwa den gleichen Prozess wie unter [Dokument-/Ansichtserstellung](../mfc/document-view-creation.md)beschrieben.

Alle von MFC angebotenen Fensterklassen verfügen über [eine zweistufige Konstruktion.](../mfc/one-stage-and-two-stage-construction-of-objects.md) Das heißt, während eines Aufrufs des **neuen** C++-Operators ordnet und initialisiert der Konstruktor ein C++-Objekt, erstellt jedoch kein entsprechendes Windows-Fenster. Dies geschieht anschließend, indem Sie die [Memberfunktion Erstellen](../mfc/reference/cwnd-class.md#create) des Fensterobjekts aufrufen.

Die `Create` Memberfunktion erstellt das Windows-Fenster und speichert es `HWND` im öffentlichen Datenmember des C++-Objekts [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create`bietet volle Flexibilität über die Erstellungsparameter. Vor `Create`dem Aufruf können Sie eine Fensterklasse mit der globalen Funktion [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) registrieren, um das Symbol und die Klassenstile für den Frame festzulegen.

Für Rahmenfenster können Sie die [LoadFrame-Memberfunktion](../mfc/reference/cframewnd-class.md#loadframe) anstelle von `Create`verwenden. `LoadFrame`macht das Windows-Fenster mit weniger Parametern. Es ruft viele Standardwerte aus Ressourcen ab, einschließlich Beschriftung, Symbol, Beschleunigertabelle und Menü des Frames.

> [!NOTE]
> Das Symbol, die Beschleunigertabelle und die Menüressourcen müssen über eine gemeinsame Ressourcen-ID verfügen, z. B. **IDR_MAINFRAME**, damit sie von LoadFrame geladen werden können.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Fensterobjekte](../mfc/window-objects.md)

- [Registrieren des Fensters "Klassen"](../mfc/registering-window-classes.md)

- [Zerstören von Fensterobjekten](../mfc/destroying-window-objects.md)

- [Erstellen von Dokumentrahmenfenstern](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von Fenstern](../mfc/creating-windows.md)
