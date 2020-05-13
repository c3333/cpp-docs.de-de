---
title: Regeln und Einschränkungen für dllimport/dllexport
ms.date: 11/04/2016
helpviewer_keywords:
- dllexport attribute [C++], limitations and rules
- dllimport attribute [C++], limitations and rules
- dllexport attribute [C++]
ms.assetid: 274b735f-ab9c-4b07-8d0e-fdb65d664634
ms.openlocfilehash: cc83a43fd09299710585fa104dbd4dc847036c68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62158422"
---
# <a name="rules-and-limitations-for-dllimportdllexport"></a>Regeln und Einschränkungen für dllimport/dllexport

**Microsoft-spezifisch**

- Wenn Sie eine Funktion ohne das **dllimport**- oder `dllexport`-Attribut deklarieren, wird die Funktion nicht als Teil der DLL-Schnittstelle betrachtet. Daher muss die Definition der Funktion in diesem Modul oder in einem anderen Modul desselben Programms vorhanden sein. Damit die Funktion Teil der DLL-Schnittstelle wird, müssen Sie die Definition der Funktion im anderen Modul als `dllexport` deklarieren. Andernfalls wird ein Linkerfehler generiert, wenn der Client erstellt wird.

- Wenn ein einzelnes Modul im Programm sowohl **dllimport**- als auch `dllexport`-Deklarationen für die gleiche Funktion enthält, hat das `dllexport`-Attribut Vorrang vor dem **dllimport**-Attribut. Es wird jedoch eine Compilerwarnung ausgegeben. Zum Beispiel:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllExport void func1( void );   /* Warning; dllexport */
                                       /* takes precedence. */

    ```

- Sie können keinen statischen Datenzeiger mit der Adresse eines Datenobjekts, das mit dem **dllimport**-Attribut deklariert wird, initialisieren. Durch folgenden Code werden z. B. Fehler verursacht:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport int i;
       .
       .
       .
       int *pi = &i;                           /* Error */

       void func2()
       {
          static int *pi = &i;                   /* Error */
       }

    ```

- Das Initialisieren eines statischen Funktionszeigers mit der Adresse einer Funktion, die mit **dllimport** deklariert ist, legt den Zeiger auf die Adresse des DLL-Importthunks (ein Codestub, der die Steuerung an die Funktion übergibt) anstatt auf die Adresse der Funktion fest. Diese Zuweisung generiert keine Fehlermeldung:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void
       .
       .
       .
       static void ( *pf )( void ) = &func1;   /* No Error */

       void func2()
       {
          static void ( *pf )( void ) = &func1;  /* No Error */
       }

    ```

- Da ein Programm, das das Attribut `dllexport` in der Deklaration des Objekts enthält, die Definition für dieses Objekt bereitstellen muss, können Sie einen globalen oder lokalen statischen Funktionszeiger mit der Adresse der `dllexport`-Funktion initialisieren. Ebenso können Sie einen globalen oder lokalen statischen Datenzeiger mit der Adresse eines `dllexport`-Datenobjekts initialisieren. Zum Beispiel:

    ```
    #define DllImport   __declspec( dllimport )
    #define DllExport   __declspec( dllexport )

       DllImport void func1( void );
       DllImport int i;

       DllExport void func1( void );
       DllExport int i;
       .
       .
       .
       int *pi = &i;                            /* Okay */
       static void ( *pf )( void ) = &func1;    /* Okay */

       void func2()
       {
          static int *pi = i;                     /* Okay */
          static void ( *pf )( void ) = &func1;   /* Okay */
       }

    ```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Import- und Exportfunktionen einer DLL](../c-language/dll-import-and-export-functions.md)
