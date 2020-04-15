---
title: Hinzufügen neuer Funktionen mit Code-Assistenten (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: ab0bf802221bcf3f93469f27f29f86c95877a407
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365334"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Hinzufügen neuer Funktionen mit Code-Assistenten (C++)

Nachdem Sie ein Projekt erstellt haben, sollten Sie Funktionen zum Projekt hinzufügen oder diese ändern. Dazu zählt das Erstellen neuer Klassen, das Hinzufügen von neuen Memberfunktionen und -variablen sowie das Hinzufügen von Automatisierungsmethoden und -eigenschaften. Die Code-Assistenten wurden dafür entwickelt, diese Aktionen auszuführen.

> [!NOTE]
> Die folgenden nur selten verwendeten Code-Assistenten werden in Visual Studio 2019 entfernt. Die Entfernung dieser Assistenten wirkt sich nicht auf die allgemeine Unterstützung für Active Template Library (ATL) und Microsoft Foundation Classes (MFC) aus. Beispielcode für diese Technologien ist in der Microsoft-Dokumentation und im VCSamples-GitHub-Repository archiviert.

- ATL COM+ 1.0 Komponenten-Assistent
- ATL-Assistent für Active Server Pages-Komponenten
- ATL-OLE DB-Anbieter-Assistent
- ATL-Eigenschaftenseiten-Assistent
- ATL-OLE DB-Consumer-Assistent
- MFC-ODBC-Consumer
- MFC-Klasse aus ActiveX-Steuerelement
- MFC-Klasse aus Typbibliothek

> [!NOTE]
> Sie können Meldungshandler und Zuordnungsmeldungen zu diesen hinzufügen und virtuelle MFC-Funktionen mithilfe des [MFC-Klassen-Assistenten](../mfc/reference/mfc-class-wizard.md) überschreiben.

## <a name="accessing-c-code-wizards"></a>Zugreifen auf C++-Code-Assistenten

Es gibt drei Stellen, über die Sie auf C++-Code-Assistenten zugreifen können:

- Im Menü **Projekt** ermöglicht der Befehl **Neues Element hinzufügen** das Erstellen des Dialogfelds `Add New Item`. Mit diesem können Sie neue Dateien zu Ihrem Projekt hinzufügen. Durch den Befehl **Klasse hinzufügen** wird das Dialogfeld [Klasse hinzufügen](../ide/add-class-dialog-box.md) angezeigt, das den Assistenten für jeden Klassentyp anzeigt, den Sie zu Ihrem Projekt hinzufügen können. Verwenden Sie für MFC-Klassen den [MFC-Klassen-Assistenten](../mfc/reference/mfc-class-wizard.md). Durch den Befehl **Ressource hinzufügen** wird das Dialogfeld [Ressource hinzufügen](../windows/add-resource-dialog-box.md) angezeigt, in dem Sie eine Ressource erstellen oder eine Ressource auswählen können, die zu Ihrem Projekt hinzugefügt werden soll.

   Wenn Sie eine Klasse oder eine Schnittstelle in Ihrem Projekt in der Klassenansicht hervorheben, zeigt das Menü **Projekt** ebenfalls folgende Befehle an:

  - **Schnittstelle implementieren** (nur über eine Steuerelementklasse)

  - **Funktion hinzufügen**

  - **Variable hinzufügen**

  - **Verbindungspunkt hinzufügen** (nur ATL-Klassen)

  - **Methode hinzufügen** (nur über eine Schnittstelle)

  - **Eigenschaft hinzufügen** (nur über eine Schnittstelle)

  - **Ereignis hinzufügen** (nur über eine Steuerelementklasse)

- Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf einen beliebigen Ordner, und klicken Sie im Kontextmenü auf **Hinzufügen**, um neue oder vorhandene Dateien, weitere Ordner, Elemente, Klassen, Ressourcen oder Webverweise zum Projekt hinzuzufügen.

- Klicken Sie im Fenster [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) mit der rechten Maustaste auf den entsprechenden Knoten, und klicken Sie im Kontextmenü auf **Hinzufügen**, um Funktionen, Variablen, Klassen, Eigenschaften, Methoden, Ereignisse, Schnittstellen, Verbindungspunkte oder anderen Code zu Ihrem Projekt hinzuzufügen.

   > [!NOTE]
   > Visual Studio stellt keinen Assistenten dafür bereit, Schnittstellen zu einem Projekt hinzuzufügen. Sie können Schnittstellen zu einem ATL-Projekt oder zu einem [MFC-Projekt](../mfc/reference/adding-atl-support-to-your-mfc-project.md) hinzufügen, indem Sie mithilfe des [ATL-Assistenten für einfache Objekte](../atl/reference/atl-simple-object-wizard.md) ein einfaches Objekt hinzufügen. Öffnen Sie alternativ die IDL-Datei des Projekts, und erstellen Sie die Schnittstelle, indem Sie Folgendes eingeben:

    ```IDL
    interface IMyInterface {
    };
    ```

   Weitere Informationen finden Sie unter [Implementing an Interface (Implementieren einer Schnittstelle)](../ide/implementing-an-interface-visual-cpp.md) und [Adding Objects and Controls to an ATL Project (Hinzufügen von Objekten und Steuerelementen zu einem ATL-Projekt)](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

   |Zugriff auf den Code-Assistenten über|BESCHREIBUNG|
   |-----------------------------|-----------------|
   |Neues Element hinzufügen|Die Code-Assistenten zum Hinzufügen neuer Elemente fügen Quelldateien zu Ihrem Projekt hinzu. Bei Bedarf werden zusätzliche Verzeichnisse erstellt, die die Dateien dort enthalten, wo die Build-Engine des Projekts diese erwartet. Folgende Code-Assistenten sind über das Symbol „Element hinzufügen“ verfügbar:<br /><br />– C++-Quelldateien hinzufügen (.cpp, .h, .idl, .rc, .srf, .def, .rgs)<br />– Webentwicklungsdateien hinzufügen (.html, .asp, .css, .xml)<br />– Hilfsprogrammdateien und Ressourcendateien hinzufügen (.bmp, .cur, .ico, .rct, .sql, .txt)<br /><br />Diese Code-Assistenten fordern in der Regel keine Informationen von Ihnen an, sondern fügen eine Datei zur Entwicklungsstruktur hinzu. Sie können die Datei im Eigenschaftenfenster neu benennen.|
   |Projektmappen-Explorer|Die Code-Assistenten, die über den Projektmappen-Explorer verfügbar sind, hängen davon ab, wo sich der Fokus Ihres Cursors befindet, wenn Sie mit der rechten Maustaste auf ein Element klicken. Wenn die Option **Hinzufügen** nicht angezeigt wird, wenn Sie mit der rechten Maustaste auf ein Element klicken, bewegen Sie Ihren Cursor in der Entwicklungsstruktur eine Ebene nach oben, und wiederholen Sie den Vorgang. Der Code-Assistent fügt zusätzlichen Code unabhängig davon, wo Ihr Cursor sich befindet, immer an der entsprechenden Stelle in der Entwicklungsstruktur ein. Folgende Code-Assistenten sind über den Projektmappen-Explorer verfügbar:<br /><br />– Klasse hinzufügen (öffnet das Dialogfeld **Klasse hinzufügen**, das die neuen Code-Assistenten enthält)<br />– Ressource hinzufügen (Optionen: „Neu“, „Importieren“ oder „Benutzerdefiniert“)<br />– Webverweis hinzufügen|
   |Klassenansicht|Die Code-Assistenten, die über die Klassenansicht verfügbar sind, hängen davon ab, wo sich der Fokus Ihres Cursors befindet, wenn Sie mit der rechten Maustaste auf ein Element klicken. Wenn die Option **Hinzufügen** nicht angezeigt wird, wenn Sie mit der rechten Maustaste auf ein Element klicken, bewegen Sie Ihren Cursor in der Klassenstruktur eine Ebene nach oben, und wiederholen Sie den Vorgang. Der Code-Assistent fügt zusätzlichen Code unabhängig davon, wo Ihr Cursor sich befindet, immer an der entsprechenden Stelle in der Entwicklungsstruktur ein. Folgende Code-Assistenten sind über die Klassenansicht verfügbar:<br /><br />- [Memberfunktion hinzufügen](../ide/adding-a-member-function-visual-cpp.md)<br />- [Membervariable hinzufügen](../ide/adding-a-member-variable-visual-cpp.md)<br />- [Klasse hinzufügen](../ide/adding-a-class-visual-cpp.md).<br />- [Schnittstelle implementieren](../ide/implement-interface-wizard.md) (nur über eine Steuerelementklasse)<br />- [Verbindungspunkt hinzufügen](../ide/implement-connection-point-wizard.md) (nur ATL-Klasse)<br />- [Methode hinzufügen](../ide/add-method-wizard.md) (nur über eine Schnittstelle)<br />- [Eigenschaft hinzufügen](../ide/names-add-property-wizard.md) (nur über eine Schnittstelle)<br />- [Ereignis hinzufügen](../ide/add-event-wizard.md) (nur über eine Steuerelementklasse)<br /><br />Die Auswahl „Klasse hinzufügen“ öffnet das Dialogfeld **Klasse hinzufügen**, über das Sie auf alle neuen Code-Assistenten zum Hinzufügen von Klassen zugreifen können.|

## <a name="see-also"></a>Siehe auch

[Overriding a Virtual Function (Überschreiben einer virtuellen Funktion)](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Navigieren in C++-Code in Visual Studio](../ide/navigate-code-cpp.md)<br>
[C++-Projektvorlagen](../build/reference/visual-cpp-project-types.md)<br>
[Für Visual Studio C++-Projekte erstellte Dateitypen](../build/reference/file-types-created-for-visual-cpp-projects.md)
