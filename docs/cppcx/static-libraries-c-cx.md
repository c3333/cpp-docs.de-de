---
title: Statische Bibliotheken (C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 756f8d2c1af2c6be414ad39b4a96fa6cc7ccfb02
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924718"
---
# <a name="static-libraries-ccx"></a>Statische Bibliotheken (C++/CX)

Eine statische Bibliothek, die in einer universelle Windows-Plattform-app (UWP) verwendet wird, kann ISO-Standard-C++-Code, einschließlich STL-Typen, und auch Aufrufe von Win32-APIs enthalten, die nicht von der Windows-Runtime App-Plattform ausgeschlossen werden. Eine statische Bibliothek nutzt Windows-Runtime Komponenten und kann Windows-Runtime Komponenten mit bestimmten Einschränkungen erstellen.

## <a name="creating-static-libraries"></a>Erstellen von statischen Bibliotheken

Die Anweisungen zum Erstellen eines neuen Projekts variieren abhängig von der installierten Version von Visual Studio. Um die Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen, verwenden Sie das Auswahlsteuerelement **Version** . Es befindet sich am Anfang des Inhaltsverzeichnisses auf dieser Seite.

::: moniker range="msvc-160"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>So erstellen Sie eine statische UWP-Bibliothek in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei**  > **Neu**  > **Projekt** , um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie am oberen Rand des Dialog Felds  **Sprache** auf **C++** , legen Sie **Platform** auf **Windows** fest, und legen Sie **Projekttyp** auf **UWP** fest.

1. Wählen Sie in der gefilterten Liste der Projekttypen **statische Bibliothek (universelle Windows-C++/CX)** aus, und klicken Sie dann auf **weiter** . Geben Sie auf der nächsten Seite dem Projekt einen Namen, und geben Sie den Speicherort des Projekts an, wenn dies gewünscht ist.

1. Klicken Sie auf die Schaltfläche **Erstellen** , um das Projekt zu erstellen.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>So erstellen Sie eine statische UWP-Bibliothek in Visual Studio 2017 oder Visual Studio 2015

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt** . Wählen Sie unter **Visual C++**  >  **universelle** Windows- **Bibliothek statische Bibliothek (universelle Windows)** aus.

1. Öffnen Sie im **Projektmappen-Explorer** das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften** aus. Legen Sie im Dialogfeld **Eigenschaften** auf der Seite **Konfigurations Eigenschaften**  >  **C/C++** den Wert **Windows-Runtime Erweiterung** verwenden auf **Ja (/ZW)** fest.

::: moniker-end

Wenn Sie eine neue statische Bibliothek kompilieren und eine Win32-API aufzurufen, die für UWP-apps ausgeschlossen ist, gibt der Compiler den Fehler C3861 "Identifier nicht gefunden" aus. Eine alternative Methode, die für die Windows-Runtime unterstützt wird, finden Sie unter [Alternativen zu Windows-APIs in UWP-apps](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Wenn Sie einer UWP-App-Projekt Mappe ein statisches C++-Bibliotheksprojekt hinzufügen, müssen Sie möglicherweise die Eigenschaften Einstellungen des Bibliotheks Projekts aktualisieren, damit die Eigenschaft UWP-Unterstützung auf **Ja** festgelegt ist. Ohne diese Einstellung wird der Code erstellt und verknüpft, aber es tritt ein Fehler auf, wenn Sie versuchen, die APP für die Microsoft Store zu überprüfen. Die statische Bibliothek sollte mit den gleichen Compilereinstellungen wie das Projekt kompiliert werden, in dem sie verwendet werden.

Wenn Sie eine statische Bibliothek nutzen, die öffentliche `ref` -Klassen, öffentliche Schnittstellenklassen oder öffentliche Wertklassen erstellt, gibt der Linker folgende Warnung aus:

> **Warnung LNK4264:** Archivieren der mit/ZW kompilierten Objektdatei in eine statische Bibliothek; Beachten Sie, dass es beim Erstellen von Windows-Runtime Typen nicht empfohlen wird, eine Verknüpfung mit einer statischen Bibliothek zu erstellen, die Windows-Runtime Metadaten enthält.

Sie können die Warnung nur gefahrlos ignorieren, wenn die statische Bibliothek keine Windows-Runtime Komponenten erzeugt, die außerhalb der Bibliothek selbst genutzt werden. Wenn die Bibliothek keine Komponenten verwendet, die sie definiert, kann der Linker die Implementierung optimieren, obwohl die öffentlichen Metadaten die Typinformationen enthalten. Das bedeutet, dass öffentliche Komponenten in einer statischen Bibliothek kompiliert, aber nicht zur Laufzeit aktiviert werden. Aus diesem Grund müssen alle Windows-Runtime Komponenten, die für die Nutzung durch andere Komponenten oder apps vorgesehen sind, in einer Dynamic Link Library (dll) implementiert werden.

## <a name="see-also"></a>Siehe auch

[Threading und Marshalling](../cppcx/threading-and-marshaling-c-cx.md)
