---
title: C++-Beispielprojekt für die Codeanalyse
description: Erstellen einer Beispiellösung für die Verwendung in der exemplarischen Vorgehensweise für Die Codeanalyse für Microsoft C++ in Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: c2a1b8c80b7e7aebd1f1530c66ade5859b392028
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372061"
---
# <a name="sample-c-project-for-code-analysis"></a>C++-Beispielprojekt für die Codeanalyse

Die folgenden Verfahren zeigen Ihnen, wie Sie das Beispiel für [die exemplarische Vorgehensweise erstellen: Analysieren sie C/C++-Code für Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md). Mithilfe dieser Prozeduren wird Folgendes erstellt:

- Eine Visual Studio-Lösung mit dem Namen *CppDemo*.

- Ein statisches Bibliotheksprojekt mit dem Namen *CodeDefects*.

- Ein *statisches Bibliotheksprojekt*mit dem Namen Annotations .

Die Prozeduren stellen zudem den Code für den Header und die *.cpp*-Dateien für die statischen Bibliotheken bereit.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der CppDemo-Projektmappe und des CodeDefects-Projekts

::: moniker range=">=vs-2019"

1. Öffnen Sie Visual Studio, und wählen **Sie Erstellen eines neuen Projekts** aus.

1. Ändern Sie im **Dialogfeld Erstellen eines neuen Projekts** den Sprachfilter in **C++**.

1. Wählen Sie **den Windows-Desktop-Assistenten** aus, und wählen Sie die Schaltfläche **Weiter** aus.

1. Geben Sie auf der Seite **Konfigurieren der neuen Projektseite** im Textfeld **Projektname** *CodeDefects*ein.

1. Geben Sie im Textfeld **Lösungsname** *CppDemo*ein.

1. Wählen Sie **Erstellen**.

1. Ändern Sie im Dialogfeld **Windows Desktop Project** den **Anwendungstyp** in **Statische Bibliothek (.lib).**

1. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus.

1. Wählen Sie **OK,** um die Projektmappe und das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

1. Öffnen Sie Visual Studio. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

1. Wählen Sie im Dialogfeld **Neues Projekt** **Visual C++** > **Windows Desktop**aus.

1. Wählen Sie **den Windows-Desktop-Assistenten**aus.

1. Geben Sie im Textfeld **Name** *CodeDefects ein.*

1. Geben Sie im Textfeld **Lösungsname** *CppDemo*ein.

1. Wählen Sie **OK**.

1. Ändern Sie im Dialogfeld **Windows Desktop Project** den **Anwendungstyp** in **Statische Bibliothek (.lib).**

1. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus.

1. Wählen Sie **OK,** um die Projektmappe und das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

1. Öffnen Sie Visual Studio. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt**aus.

1. Wählen Sie im Dialogfeld **Neues Projekt** Die Option **Vorlagen** > **Visual C++** > **Win32**aus.

1. Wählen Sie **Win32 Console Application**.

1. Geben Sie im Textfeld **Name** *CodeDefects ein.*

1. Geben Sie im Textfeld **Lösungsname** *CppDemo*ein.

1. Wählen Sie **OK**.

1. Wählen Sie im Dialogfeld **Win32 Application Wizard** die Schaltfläche **Weiter** aus.

1. Ändern Sie den **Anwendungstyp** in **Statische Bibliothek**.

1. Unter **Zusätzliche Optionen**die Option **Vorkompilierter Header**aufklicken.

1. Wählen Sie **Fertig stellen** aus, um die Projektmappe und das Projekt zu erstellen.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Hinzufügen der Kopf- und Quelldatei zum CodeDefects-Projekt

1. Erweitern Sie im Projektmappen-Explorer **CodeDefects**.

1. Klicken Sie mit der rechten Maustaste, um das Kontextmenü für **Headerdateien**zu öffnen. Wählen Sie**Neues Element** **hinzufügen** > .

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Visual **C++** > **Code**aus, und wählen Sie dann Header **Datei (.h)** aus.

1. Geben Sie im Bearbeitungsfeld **Name** *Bug.h*ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

1. Wählen Sie im Bearbeitungsfenster für *Bug.h*den Inhalt aus und löschen Sie ihn.

1. Kopieren Sie den folgenden Code und fügen Sie ihn im Editor in der Datei *Bug.h* ein.

    ```cpp
    #pragma once

    #include <windows.h>

    // Function prototypes
    bool CheckDomain(wchar_t const *);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste, um das Kontextmenü für **Quelldateien**zu öffnen. Wählen Sie**Neues Element** **hinzufügen** > .

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)**.

1. Geben Sie im Bearbeitungsfeld **Name** *Bug.cpp*ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

1. Kopieren Sie den folgenden Code und fügen Sie ihn im Editor in der Datei *Bug.cpp* ein.

    ```cpp
    #include "Bug.h"

    // the user account
    wchar_t g_userAccount[USER_ACCOUNT_LEN] = { L"domain\\user" };
    int len = 0;

    bool CheckDomain(wchar_t const* domain)
    {
        return (wcsnlen_s(domain, USER_ACCOUNT_LEN) > 0);
    }

    HRESULT ReadUserAccount()
    {
        return S_OK;
    }

    bool ProcessDomain()
    {
        wchar_t* domain = new wchar_t[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == L'\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != L'\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = L'\0';
            }
            // Process domain string
            bool result = CheckDomain(domain);

            delete[] domain;
            return result;
        }
        return false;
    }

    int path_dependent(int n)
    {
        int i;
        int j;
        if (n == 0)
            i = 1;
        else
            j = 1;
        return i + j;
    }
    ```

1. Wählen Sie in der Menüleiste **Datei** > **speichern alle**aus.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Hinzufügen des Annotations-Projekts und Konfigurieren dieses Projekts als statische Bibliothek

::: moniker range=">=vs-2019"

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **CppDemo,** um das Kontextmenü zu öffnen. Wählen Sie**Neues Projekt** **hinzufügen** > aus .

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Option Windows Desktop **Wizard**aus, und wählen Sie dann die Schaltfläche **Weiter** aus.

1. Geben Sie auf der Seite **Konfigurieren der neuen Projektseite** im Textfeld **Projektname** *Anmerkungen*ein, und wählen Sie dann **Erstellen**aus.

1. Ändern Sie im Dialogfeld **Windows Desktop Project** den **Anwendungstyp** in **Statische Bibliothek (.lib).**

1. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus.

1. Wählen Sie **OK,** um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2017"

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **CppDemo,** um das Kontextmenü zu öffnen. Wählen Sie**Neues Projekt** **hinzufügen** > aus .

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Option Visual **C++** > **Windows Desktop**aus.

1. Wählen Sie **den Windows-Desktop-Assistenten**aus.

1. Geben Sie im Textfeld **Name** *Anmerkungen*ein, und wählen Sie dann **OK**aus.

1. Ändern Sie im Dialogfeld **Windows Desktop Project** den **Anwendungstyp** in **Statische Bibliothek (.lib).**

1. Wählen Sie unter **Zusätzliche Optionen**die Option **Leeres Projekt**aus.

1. Wählen Sie **OK,** um das Projekt zu erstellen.

::: moniker-end

::: moniker range="vs-2015"

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **CppDemo,** um das Kontextmenü zu öffnen. Wählen Sie**Neues Projekt** **hinzufügen** > aus .

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Option Visual **C++** > **Win32**aus.

1. Wählen Sie **Win32 Console Application**.

1. Geben Sie im Textfeld **Name** *Anmerkungen*ein.

1. Wählen Sie **OK**.

1. Wählen Sie im Dialogfeld **Win32 Application Wizard** die Schaltfläche **Weiter** aus.

1. Ändern Sie den **Anwendungstyp** in **Statische Bibliothek**.

1. Unter **Zusätzliche Optionen**die Option **Vorkompilierter Header**aufklicken.

1. Wählen Sie **Fertig stellen** aus, um das Projekt zu erstellen.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Hinzufügen der Headerdatei und Quelldatei zum Annotations-Projekt

1. Erweitern Sie im Projektmappen-Explorer **Anmerkungen**.

1. Klicken Sie mit der rechten Maustaste, um das Kontextmenü für **Headerdateien** unter **Anmerkungen**zu öffnen. Wählen Sie**Neues Element** **hinzufügen** > .

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Option Visual **C++** > **Code**aus, und wählen Sie dann Header **Datei (.h)** aus.

1. Geben Sie im Bearbeitungsfeld **Name** *annotations.h*ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

1. Wählen Sie im Bearbeitungsfenster für *annotations.h*den Inhalt aus und löschen Sie ihn.

1. Kopieren Sie den folgenden Code, und fügen Sie ihn im Editor in der Datei *annotations.h* ein.

    ```cpp
    #pragma once
    #include <sal.h>

    struct LinkedList
    {
        struct LinkedList* next;
        int data;
    };

    typedef struct LinkedList LinkedList;

    _Ret_maybenull_ LinkedList* AllocateNode();
    ```

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste, um das Kontextmenü für **Quelldateien** unter **Anmerkungen**zu öffnen. Wählen Sie**Neues Element** **hinzufügen** > .

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)**.

1. Geben Sie im Bearbeitungsfeld **Name** *annotations.cpp*ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

1. Kopieren Sie den folgenden Code, und fügen Sie ihn im Editor in der Datei *annotations.cpp* ein.

    ```cpp
    #include "annotations.h"
    #include <malloc.h>

    _Ret_maybenull_ LinkedList* AllocateNode()
    {
        LinkedList* result = static_cast<LinkedList*>(malloc(sizeof(LinkedList)));
        return result;
    }

    LinkedList* AddTail(LinkedList* node, int value)
    {
        // finds the last node
        while (node->next != nullptr)
        {
            node = node->next;
        }

        // appends the new node
        LinkedList* newNode = AllocateNode();
        newNode->data = value;
        newNode->next = 0;
        node->next = newNode;

        return newNode;
    }
    ```

1. Wählen Sie in der Menüleiste **Datei** > **speichern alle**aus.

Die Projektmappe ist jetzt fertig und sollte ohne Fehler erstellt werden.

::: moniker range="vs-2017"

> [!NOTE]
> In Visual Studio 2017 wird möglicherweise `E1097 unknown attribute "no_init_all"` eine falsche Warnung im IntelliSense-Modul angezeigt. Sie können diese Warnung problemlos ignorieren.

::: moniker-end
