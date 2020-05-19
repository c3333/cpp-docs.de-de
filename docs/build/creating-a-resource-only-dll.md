---
title: Erstellen einer DLL als reine Ressource
description: Erfahren Sie, wie Sie eine DLL in Visual Studio als reine Ressource erstellen.
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821342"
---
# <a name="creating-a-resource-only-dll"></a>Erstellen einer DLL als reine Ressource

Eine reine Ressourcen-DLL ist eine DLL, die ausschließlich Ressourcen enthält, z. B. Symbole, Bitmaps, Zeichenfolgen und Dialogfelder. Die Verwendung einer reinen Ressourcen-DLL bietet eine gute Möglichkeit, dieselben Ressourcen von mehreren Programmen gemeinsam nutzen zu lassen. Sie stellt zudem eine gute Möglichkeit dar, eine Anwendung mit Ressourcen bereitzustellen, die in verschiedene Sprachen lokalisiert wurden. Weitere Informationen finden Sie unter [Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](localized-resources-in-mfc-applications-satellite-dlls.md).

## <a name="create-a-resource-only-dll"></a>Erstellen einer DLL als reine Ressource

Zum Erstellen einer DLL als reine Ressource erstellen Sie ein neues Windows-DLL-Projekt (nicht MFC) und fügen dem Projekt die Ressourcen hinzu:

::: moniker range="vs-2015"

1. Klicken Sie im Dialogfeld **Neues Projekt** auf **Win32-Projekt**. Geben Sie den Projekt- und Projektmappennamen ein, und klicken Sie auf **OK**.

1. Klicken Sie im **Win32-Anwendungs-Assistenten** auf **Anwendungseinstellungen**. Wählen Sie einen **Anwendungstyp** der **DLL** aus. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus. Klicken Sie auf **Fertig stellen**, um Ihr Projekt zu erstellen.

1. Erstellen Sie ein neues Ressourcenskript, das die Ressourcen für die DLL (z. B. eine Zeichenfolge oder ein Menü) enthält. Speichern Sie die Datei `.rc`.

1. Wählen Sie im Menü **Projekt** die Option **Vorhandenes Element hinzufügen** aus, und fügen Sie dann die neue `.rc`-Datei in das Projekt ein.

1. Legen Sie die Linkeroption [/NOENTRY](reference/noentry-no-entry-point.md) fest. `/NOENTRY` verhindert, dass der Linker einen Verweis auf `_main` in die DLL einfügt. Diese Option ist erforderlich, um eine reine Ressourcen-DLL zu erstellen.

1. Erstellen Sie die DLL.

::: moniker-end
::: moniker range=">=vs-2017"

1. Klicken Sie im Dialogfeld **Neues Projekt** auf **Windows-Desktopassistent** und dann auf **Weiter**. Geben Sie auf der Seite **Neues Projekt konfigurieren** den Projekt- und Projektmappennamen ein, und klicken Sie dann auf **Erstellen**.

1. Wählen Sie im Dialogfeld **Windows-Desktopprojekt** einen **Anwendungstyp** der **Dynamic Link Library** aus. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus. Klicken Sie auf **OK**, um das Projekt zu erstellen.

1. Erstellen Sie ein neues Ressourcenskript, das die Ressourcen für die DLL (z. B. eine Zeichenfolge oder ein Menü) enthält. Speichern Sie die Datei `.rc`.

1. Wählen Sie im Menü **Projekt** die Option **Vorhandenes Element hinzufügen** aus, und fügen Sie dann die neue `.rc`-Datei in das Projekt ein.

1. Legen Sie die Linkeroption [/NOENTRY](reference/noentry-no-entry-point.md) fest. `/NOENTRY` verhindert, dass der Linker einen Verweis auf `_main` in die DLL einfügt. Diese Option ist erforderlich, um eine reine Ressourcen-DLL zu erstellen.

1. Erstellen Sie die DLL.

::: moniker-end

## <a name="use-a-resource-only-dll"></a>Verwenden einer DLL als reine Ressource

Die Anwendung, die die reine Ressourcen-DLL verwendet, sollte [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md) oder eine ähnliche Funktion aufrufen, um eine explizite Verknüpfung mit der DLL zu erstellen. Rufen Sie für den Zugriff auf die Ressourcen die generischen Funktionen `FindResource` und `LoadResource` auf, die mit jeder Art von Ressource funktionieren. Alternativ dazu können Sie auch eine der folgenden ressourcenspezifischen Funktionen aufrufen:

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

Die Anwendung sollte `FreeLibrary` aufrufen, sobald die Ressourcen nicht mehr benötigt werden.

## <a name="see-also"></a>Siehe auch

[Working with Resource Files (Arbeiten mit Ressourcendateien)](../windows/working-with-resource-files.md)\
[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)
