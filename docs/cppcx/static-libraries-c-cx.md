---
title: Statische Bibliotheken (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 3c4bfd28b805903a2e596ef6d648ff31b0b8261c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358112"
---
# <a name="static-libraries-ccx"></a>Statische Bibliotheken (C++/CX)

Eine statische Bibliothek, die in einer UWP-App (Universelle Windows-Plattform) verwendet wird, kann ISO-Standard-C++-Code enthalten, einschließlich STL-Typen, sowie Aufrufe von Win32-APIs, die nicht von der Windows-Runtime-App-Plattform ausgeschlossen sind. Eine statische Bibliothek verwendet Windows-Runtime-Komponenten und kann Windows-Runtime-Komponenten mit bestimmten Einschränkungen erstellen.

## <a name="creating-static-libraries"></a>Erstellen von statischen Bibliotheken

Die Anweisungen zum Erstellen eines neuen Projekts hängen davon ab, welche Version von Visual Studio Sie installiert haben. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="vs-2019"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>So erstellen Sie eine statische UWP-Bibliothek in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld **Sprache** auf **C++** fest, legen Sie **Plattform** auf **Windows**fest, und legen Sie **den Projekttyp** auf **UWP**fest.

1. Wählen Sie in der gefilterten Liste der Projekttypen **Statische Bibliothek (Universelles Windows - C++/CX)** und dann **Weiter**aus. Geben Sie dem Projekt auf der nächsten Seite einen Namen, und geben Sie ggf. den Projektspeicherort an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Projekt zu erstellen.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>So erstellen Sie eine statische UWP-Bibliothek in Visual Studio 2017 oder Visual Studio 2015

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus. Wählen Sie unter **Visual C++** > **Windows Universal** Statische Bibliothek **(Universelles Windows)** aus.

1. Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie dann **Eigenschaften**aus. Legen Sie im Dialogfeld **Eigenschaften** auf der Seite **Konfigurationseigenschaften** > **C/C++** **"Windows-Runtime-Erweiterung** auf **Ja (/ZW)** fest.

::: moniker-end

Wenn Sie eine neue statische Bibliothek kompilieren und einen Aufruf einer Win32-API tätigen, die für UWP-Apps ausgeschlossen ist, löst der Compiler den Fehler C3861, "Identifier not found" aus. Informationen zur Suche nach einer alternativen Methode, die für die Windows-Runtime unterstützt wird, finden Sie unter [Alternativen zu Windows-APIs in UWP-Apps](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Wenn Sie einer UWP-App-Lösung ein statisches C++-Bibliotheksprojekt hinzufügen, müssen Sie möglicherweise die Eigenschafteneinstellungen des Bibliotheksprojekts aktualisieren, sodass die UWP-Supporteigenschaft auf **Ja**festgelegt ist. Ohne diese Einstellung wird der Code erstellt und verknüpft, aber es tritt ein Fehler auf, wenn Sie versuchen, die App für den Microsoft Store zu überprüfen. Die statische Bibliothek sollte mit den gleichen Compilereinstellungen wie das Projekt kompiliert werden, in dem sie verwendet werden.

Wenn Sie eine statische Bibliothek nutzen, die öffentliche `ref` -Klassen, öffentliche Schnittstellenklassen oder öffentliche Wertklassen erstellt, gibt der Linker folgende Warnung aus:

> **Warnung LNK4264:** Archivierung der mit /ZW kompilierten Objektdatei in einer statischen Bibliothek; Beachten Sie, dass beim Erstellen von Windows-Runtime-Typen keine Verknüpfung mit einer statischen Bibliothek empfohlen wird, die Windows-Runtime-Metadaten enthält.

Sie können die Warnung nur dann ignorieren, wenn die statische Bibliothek keine Windows-Runtime-Komponenten erzeugt, die außerhalb der Bibliothek selbst verbraucht werden. Wenn die Bibliothek keine Komponenten verwendet, die sie definiert, kann der Linker die Implementierung optimieren, obwohl die öffentlichen Metadaten die Typinformationen enthalten. Das bedeutet, dass öffentliche Komponenten in einer statischen Bibliothek kompiliert, aber nicht zur Laufzeit aktiviert werden. Aus diesem Grund muss jede Windows-Runtime-Komponente, die für den Verbrauch durch andere Komponenten oder Apps vorgesehen ist, in einer Dynamic-Link-Bibliothek (DLL) implementiert werden.

## <a name="see-also"></a>Siehe auch

[Threading und Marshaling](../cppcx/threading-and-marshaling-c-cx.md)
