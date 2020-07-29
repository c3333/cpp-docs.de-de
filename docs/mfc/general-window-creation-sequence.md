---
title: Allgemeine Ablauffolge bei der Fenstererstellung
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 63b5e0131642692d9372c148827a583f19114fb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223160"
---
# <a name="general-window-creation-sequence"></a>Allgemeine Ablauffolge bei der Fenstererstellung

Wenn Sie ein eigenes Fenster erstellen, z. b. ein untergeordnetes Fenster, verwendet das Framework denselben Prozess wie das unter Erstellen von [Dokumenten/Ansichten](document-view-creation.md).

Alle von MFC bereitgestellten Fenster Klassen verwenden die [zweistufige Konstruktion](one-stage-and-two-stage-construction-of-objects.md). Dies bedeutet, dass beim Aufrufen des C++ **`new`** -Operators der Konstruktor ein C++-Objekt zuordnet und initialisiert, jedoch kein entsprechendes Windows-Fenster erstellt. Dies erfolgt anschließend durch Aufrufen der [Create](reference/cwnd-class.md#create) Member-Funktion des Window-Objekts.

Die `Create` Member-Funktion bewirkt, dass das Windows-Fenster `HWND` in das öffentliche Datenmember des C++-Objekts [m_hWnd](reference/cwnd-class.md#m_hwnd)speichert. `Create`bietet umfassende Flexibilität gegenüber den Erstellungs Parametern. Vor dem Aufrufen von kann es ratsam sein `Create` , eine Fenster Klasse mit der globalen Funktion [AfxRegisterWndClass](reference/application-information-and-management.md#afxregisterwndclass) zu registrieren, um das Symbol und die Klassen Stile für den Frame festzulegen.

Bei Frame Fenstern können Sie die [LoadFrame](reference/cframewnd-class.md#loadframe) -Member-Funktion anstelle von verwenden `Create` . `LoadFrame`macht das Windows-Fenster mit weniger Parametern. Er ruft viele Standardwerte aus Ressourcen ab, einschließlich der Beschriftung, des Symbols, der Zugriffstasten Tabelle und des Menüs des Frames.

> [!NOTE]
> Ihr Symbol, die Zugriffstasten Tabelle und die Menü Ressourcen müssen über eine gemeinsame Ressourcen-ID verfügen, z. b. **IDR_MAINFRAME**, damit Sie von LoadFrame geladen werden können.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Fensterobjekte](window-objects.md)

- [Fenster "Klassen" wird registriert.](registering-window-classes.md)

- [Zerstören von Fensterobjekten](destroying-window-objects.md)

- [Erstellen von Dokumentrahmenfenstern](creating-document-frame-windows.md)

## <a name="see-also"></a>Siehe auch

[Erstellen von Fenstern](creating-windows.md)
