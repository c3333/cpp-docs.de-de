---
title: C++-Beispielprojekt für die Codeanalyse
ms.date: 11/04/2016
ms.topic: sample
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
ms.openlocfilehash: 1966e9cec5825ae37728bbf28c0f21ff4eed62fc
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467220"
---
# <a name="sample-c-project-for-code-analysis"></a>C++-Beispielprojekt für die Codeanalyse

In den folgenden Vorgehensweisen wird veranschaulicht, wie Sie das Beispiel für Exemplarische Vorgehensweise [: Analysieren von C/C++ Code auf Fehler](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)erstellen. Mithilfe dieser Prozeduren wird Folgendes erstellt:

- Eine Visual Studio-Projektmappe namens „CppDemo“

- Ein statisches Bibliotheksprojekt namens „CodeDefects“

- Ein statisches Bibliotheksprojekt namens „Annotations“

Die Prozeduren stellen zudem den Code für den Header und die *.cpp*-Dateien für die statischen Bibliotheken bereit.

## <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>Erstellen der CppDemo-Projektmappe und des CodeDefects-Projekts

1. Öffnen Sie Visual Studio, und wählen Sie **Neues Projekt erstellen** aus.

1. Ändern Sie den Sprachfilter in **C++** .

1. Wählen Sie **Leeres Projekt** aus und klicken Sie auf **Weiter**.

1. Geben Sie im Textfeld **Projektname** **CodeDefects** ein.

1. Geben Sie im Textfeld **Projektmappenname** **CppDemo** ein.

1. Klicken Sie auf **Erstellen**

## <a name="configure-the-codedefects-project-as-a-static-library"></a>Konfigurieren des CodeDefects-Projekts als statische Bibliothek

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **CodeDefects**, und klicken Sie dann auf **Eigenschaften**.

1. Erweitern Sie **Konfigurationseigenschaften**, und klicken Sie dann auf **Allgemein**.

1. Ändern Sie in der Liste **Allgemein** die Option **Konfigurationstyp** in **Statische Bibliothek (.lib)** .

1. Ändern Sie in der Liste **Erweitert** die **Zieldateierweiterung** in **.lib**.

## <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>Hinzufügen der Kopf- und Quelldatei zum CodeDefects-Projekt

1. Erweitern Sie im Projektmappen-Explorer **CodeDefects**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **Headerdatei (.h)** .

1. Geben Sie im Feld **Name** die Bezeichnung **Bug.h** ein, und klicken Sie dann auf **Hinzufügen**.

1. Kopieren Sie den folgenden Code und fügen Sie ihn im Editor in der Datei *Bug.h* ein.

    ```cpp
    #pragma once

    #include <windows.h>

    // These functions are consumed by the sample
    // but are not defined. This project cannot be linked!
    bool CheckDomain(LPCTSTR);
    HRESULT ReadUserAccount();

    // These constants define the common sizes of the
    // user account information throughout the program
    const int USER_ACCOUNT_LEN = 256;
    const int ACCOUNT_DOMAIN_LEN = 128;
    ```

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **C++-Datei (.cpp)** .

1. Geben Sie im Feld **Name** die Bezeichnung **Bug.cpp** ein, und klicken Sie dann auf **Hinzufügen**.

1. Kopieren Sie den folgenden Code und fügen Sie ihn im Editor in der Datei *Bug.cpp* ein.

    ```cpp
    #include "Bug.h"

    // the user account
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = {};
    int len = 0;

    bool ProcessDomain()
    {
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];
        // ReadUserAccount gets a 'domain\user' input from
        //the user into the global 'g_userAccount'
        if (ReadUserAccount())
        {
            // Copies part of the string prior to the '\'
            // character onto the 'domain' buffer
            for (len = 0; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != L'\0'); len++)
            {
                if (g_userAccount[len] == '\\')
                {
                    // Stops copying on the domain and user separator ('\')
                    break;
                }
                domain[len] = g_userAccount[len];
            }
            if ((len = ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
            {
                // '\' was not found. Invalid domain\user string.
                delete[] domain;
                return false;
            }
            else
            {
                domain[len] = '\0';
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

1. Klicken Sie auf das Menü **Datei** und dann auf **Alle speichern**.

## <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>Hinzufügen des Annotations-Projekts und Konfigurieren dieses Projekts als statische Bibliothek

1. Klicken Sie im Projektmappen-Explorer auf **CppDemo**, zeigen Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Projekt**.

1. Ändern Sie im Dialogfeld **Neues Projekt hinzufügen** den Sprachfilter in **C++** , wählen Sie **Leeres Projekt** aus und klicken Sie auf **Weiter**.

1. Geben Sie im Textfeld **Projektname** den Namen **Annotations** ein, und klicken Sie dann auf **Erstellen**.

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Annotations**, und klicken Sie dann auf **Eigenschaften**.

1. Erweitern Sie **Konfigurationseigenschaften**, und klicken Sie dann auf **Allgemein**.

1. Ändern Sie in der Liste **Allgemein** die Option **Konfigurationstyp** und klicken Sie dann auf **Statische Bibliothek (.lib)** .

1. Wählen Sie in der Liste **Erweitert** den Text in der Spalte neben **Zieldateierweiterung** aus, und geben Sie dann **.lib** ein.

## <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>Hinzufügen der Headerdatei und Quelldatei zum Annotations-Projekt

1. Erweitern Sie im Projektmappen-Explorer **Annotations**, klicken Sie mit der rechten Maustaste auf **Headerdateien**, klicken Sie auf **Hinzufügen**, und klicken Sie dann auf **Neues Element**.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Headerdatei (.h)** .

1. Geben Sie im Feld **Name** den **annotations.h** ein, und klicken Sie dann auf **Hinzufügen**.

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

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf **Quelldateien**, zeigen Sie auf **Neu**, und klicken Sie anschließend auf **Neues Element**.

1. Klicken Sie im Dialogfeld **Neues Element hinzufügen** auf **Code** und dann auf **C++-Datei (.cpp)** .

1. Geben Sie im Feld **Name** den **annotations.cpp** ein, und klicken Sie dann auf **Hinzufügen**.

1. Kopieren Sie den folgenden Code, und fügen Sie ihn im Editor in der Datei *annotations.cpp* ein.

    ```cpp
    #include "annotations.h"

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

1. Klicken Sie auf das Menü **Datei** und dann auf **Alle speichern**.

Die Projektmappe ist jetzt fertig und sollte ohne Fehler erstellt werden.
