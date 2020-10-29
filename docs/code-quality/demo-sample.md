---
title: C++-Beispielprojekt für die Codeanalyse
description: Erstellen einer Beispiellösung für die Verwendung in der exemplarischen Vorgehensweise für die Code Analyse für Microsoft C++ in Visual Studio.
ms.date: 04/14/2020
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: dd4fe67c05200ccc2865bc7c48b1f5047d77565e
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924628"
---
# <a name="sample-c-project-for-code-analysis"></a>C++-Beispielprojekt für die Codeanalyse

In den folgenden Verfahren wird gezeigt, wie Sie das Beispiel für Exemplarische Vorgehensweise [: Analysieren von C/C++-Code auf Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)erstellen. Mithilfe dieser Prozeduren wird Folgendes erstellt:

- Eine Visual Studio-Projekt Mappe mit dem Namen *CppDemo* .

- Ein statisches Bibliotheksprojekt mit dem Namen *Codedefekte* .

- Ein statisches Bibliotheksprojekt mit dem Namen " *Anmerkungen* ".

Die Prozeduren stellen zudem den Code für den Header und die *.cpp* -Dateien für die statischen Bibliotheken bereit.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der CppDemo-Projektmappe und des CodeDefects-Projekts

::: moniker range=">=msvc-160"

1. Öffnen Sie Visual Studio, und wählen Sie **Neues Projekt erstellen** aus.

1. Ändern Sie im Dialogfeld **Neues Projekt erstellen** den Sprachfilter in **C++** .

1. Wählen Sie **Windows-Desktop-Assistent** aus, und klicken Sie auf **weiter** .

1. Geben Sie auf der Seite **Neues Projekt konfigurieren** im Textfeld **Projektname** die Zeichen folgen *Code Fehler* ein.

1. Geben Sie im Textfeld Projektmappenname den **Namen** *CppDemo* ein.

1. Wählen Sie **Erstellen** aus.

1. Ändern Sie im Dialogfeld **Windows-Desktop Projekt** den **Anwendungstyp** in **statische Bibliothek (. lib)** .

1. Wählen Sie unter **Zusätzliche Optionen** die Option **Leeres Projekt** aus.

1. Wählen Sie **OK** , um die Projekt Mappe und das Projekt zu erstellen.

::: moniker-end

::: moniker range="msvc-150"

1. Öffnen Sie Visual Studio. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt** .

1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Visual C++** > **Windows-Desktop** aus.

1. Wählen Sie **Windows-Desktop-Assistent** .

1. Geben Sie im Textfeld **Name den Namen** *Code Fehler* ein.

1. Geben Sie im Textfeld Projektmappenname den **Namen** *CppDemo* ein.

1. Klicken Sie auf **OK** .

1. Ändern Sie im Dialogfeld **Windows-Desktop Projekt** den **Anwendungstyp** in **statische Bibliothek (. lib)** .

1. Wählen Sie unter **Zusätzliche Optionen** die Option **Leeres Projekt** aus.

1. Wählen Sie **OK** , um die Projekt Mappe und das Projekt zu erstellen.

::: moniker-end

::: moniker range="msvc-140"

1. Öffnen Sie Visual Studio. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt** .

1. Wählen Sie im Dialogfeld **Neues Projekt** die Option **Vorlagen** > **Visual C++** > **Win32** aus.

1. Wählen Sie **Win32-Konsolenanwendung** aus.

1. Geben Sie im Textfeld **Name den Namen** *Code Fehler* ein.

1. Geben Sie im Textfeld Projektmappenname den **Namen** *CppDemo* ein.

1. Klicken Sie auf **OK** .

1. Wählen Sie im Dialogfeld **Win32-Anwendungs-Assistent** die Schaltfläche **weiter** aus.

1. Ändern Sie den **Anwendungstyp** in **statische Bibliothek** .

1. Deaktivieren Sie unter **zusätzliche Optionen die Option** **vorkompilierter Header** .

1. Wählen Sie **Fertig** stellen aus, um Projekt Mappe und Projekt zu erstellen.

::: moniker-end

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Hinzufügen der Kopf- und Quelldatei zum CodeDefects-Projekt

1. Erweitern Sie in Projektmappen-Explorer den Eintrag **codemängel** .

1. Klicken Sie mit der rechten Maustaste, um das Kontextmenü für **Header Dateien** zu öffnen. Wählen **Add** Sie  >  **Neues Element** hinzufügen aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** **Visual C++**  >  **Code** aus, und wählen Sie dann **Header Datei (. h)** aus.

1. Geben Sie im Bearbeitungsfeld **Name den Namen** *Bug. h* ein, und klicken Sie dann auf die Schaltfläche **Hinzufügen** .

1. Wählen Sie im Bearbeitungsfenster für " *Bug. h* " den Inhalt aus, und löschen Sie ihn.

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

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste, um das Kontextmenü für **Quelldateien** zu öffnen. Wählen **Add** Sie  >  **Neues Element** hinzufügen aus.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)** .

1. Geben Sie im Bearbeitungsfeld **Name den Namen** *Bug. cpp* ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

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

1. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern** .

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Hinzufügen des Annotations-Projekts und Konfigurieren dieses Projekts als statische Bibliothek

::: moniker range=">=msvc-160"

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **CppDemo** , um das Kontextmenü zu öffnen. Wählen **Add** Sie  >  **Neues Projekt** hinzufügen aus.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** die Option **Windows-Desktop-Assistent** aus, und klicken Sie dann auf die Schaltfläche **weiter** .

1. Geben Sie auf der Seite **Neues Projekt konfigurieren** im Textfeld **Projektname** die Zeichen *Anmerkungen* ein, und wählen Sie dann **Erstellen** aus.

1. Ändern Sie im Dialogfeld **Windows-Desktop Projekt** den **Anwendungstyp** in **statische Bibliothek (. lib)** .

1. Wählen Sie unter **Zusätzliche Optionen** die Option **Leeres Projekt** aus.

1. Klicken Sie auf **OK** , um das Projekt zu erstellen.

::: moniker-end

::: moniker range="msvc-150"

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **CppDemo** , um das Kontextmenü zu öffnen. Wählen **Add** Sie  >  **Neues Projekt** hinzufügen aus.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** **Visual C++** > **Windows-Desktop** aus.

1. Wählen Sie **Windows-Desktop-Assistent** .

1. Geben Sie im Textfeld **Name den Namen** *Anmerkungen* ein, und klicken Sie dann auf **OK** .

1. Ändern Sie im Dialogfeld **Windows-Desktop Projekt** den **Anwendungstyp** in **statische Bibliothek (. lib)** .

1. Wählen Sie unter **Zusätzliche Optionen** die Option **Leeres Projekt** aus.

1. Klicken Sie auf **OK** , um das Projekt zu erstellen.

::: moniker-end

::: moniker range="msvc-140"

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf **CppDemo** , um das Kontextmenü zu öffnen. Wählen **Add** Sie  >  **Neues Projekt** hinzufügen aus.

1. Wählen Sie im Dialogfeld **Neues Projekt hinzufügen** **Visual C++** > **Win32** aus.

1. Wählen Sie **Win32-Konsolenanwendung** aus.

1. Geben Sie im Textfeld **Name den Namen** *Anmerkungen* ein.

1. Klicken Sie auf **OK** .

1. Wählen Sie im Dialogfeld **Win32-Anwendungs-Assistent** die Schaltfläche **weiter** aus.

1. Ändern Sie den **Anwendungstyp** in **statische Bibliothek** .

1. Deaktivieren Sie unter **zusätzliche Optionen die Option** **vorkompilierter Header** .

1. Klicken Sie auf **Fertig stellen** , um das Projekt zu erstellen.

::: moniker-end

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Hinzufügen der Headerdatei und Quelldatei zum Annotations-Projekt

1. Erweitern Sie in Projektmappen-Explorer den Knoten **Anmerkungen** .

1. Klicken Sie mit der rechten Maustaste, um das Kontextmenü für **Header Dateien** **unter Anmerkungen zu öffnen.** Wählen **Add** Sie  >  **Neues Element** hinzufügen aus.

1. Wählen Sie im Dialogfeld **Neues Element hinzufügen** **Visual C++**  >  **Code** aus, und wählen Sie dann **Header Datei (. h)** aus.

1. Geben Sie im Bearbeitungsfeld **Name den Namen** *Annotations. h* ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

1. Wählen Sie im Bearbeitungsfenster für " *Annotations. h* " den Inhalt aus, und löschen Sie ihn.

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

1. Klicken Sie in Projektmappen-Explorer mit der rechten Maustaste, um das Kontextmenü für **Quelldateien** unter **Anmerkungen** zu öffnen. Wählen **Add** Sie  >  **Neues Element** hinzufügen aus.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)** .

1. Geben Sie im Bearbeitungsfeld **Name den Namen** *Annotations. cpp* ein, und wählen Sie dann die Schaltfläche **Hinzufügen** aus.

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

1. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern** .

Die Projektmappe ist jetzt fertig und sollte ohne Fehler erstellt werden.

::: moniker range="msvc-150"

> [!NOTE]
> In Visual Studio 2017 wird möglicherweise eine falsche Warnung `E1097 unknown attribute "no_init_all"` in der IntelliSense-Engine angezeigt. Sie können diese Warnung problemlos ignorieren.

::: moniker-end
