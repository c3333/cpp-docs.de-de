---
title: Allgemeine Regeln und Einschränkungen
ms.date: 11/04/2016
ms.assetid: 6c48902d-4259-4761-95d4-e421d69aa050
ms.openlocfilehash: 8d21f627f461dce90af93ca5c1af8c4a28098539
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213410"
---
# <a name="general-rules-and-limitations"></a>Allgemeine Regeln und Einschränkungen

**Microsoft-spezifisch**

- Wenn Sie eine Funktion oder ein Objekt ohne das-Attribut oder das-Attribut deklarieren **`dllimport`** **`dllexport`** , wird die Funktion oder das Objekt nicht als Teil der DLL-Schnittstelle betrachtet. Daher muss die Definition der Funktion oder des Objekts in diesem Modul oder in einem anderen Modul desselben Programms vorhanden sein. Um die Funktion oder das Objekt Teil der DLL-Schnittstelle zu machen, müssen Sie die Definition der Funktion oder des Objekts im anderen Modul als deklarieren **`dllexport`** . Andernfalls wird ein Linkerfehler generiert.

   Wenn Sie eine Funktion oder ein Objekt mit dem-Attribut deklarieren **`dllexport`** , muss die Definition in einem Modul desselben Programms angezeigt werden. Andernfalls wird ein Linkerfehler generiert.

- Wenn ein einzelnes Modul im Programm sowohl **`dllimport`** -als auch- **`dllexport`** Deklarationen für dieselbe Funktion oder dasselbe Objekt enthält, hat das **`dllexport`** Attribut Vorrang vor dem **`dllimport`** Attribut. Es wird jedoch eine Compilerwarnung ausgegeben. Zum Beispiel:

    ```cpp
    __declspec( dllimport ) int i;
    __declspec( dllexport ) int i;   // Warning; inconsistent;
                                     // dllexport takes precedence.
    ```

- In C++ können Sie einen global deklarierten oder statischen lokalen Datenzeiger oder mit der Adresse eines Datenobjekts, das mit dem- **`dllimport`** Attribut deklariert wurde, initialisieren, wodurch ein Fehler in C generiert wird. Außerdem können Sie einen statischen lokalen Funktionszeiger mit der Adresse einer Funktion initialisieren, die mit dem-Attribut deklariert wurde **`dllimport`** . In C legt eine solche Zuweisung den Zeiger auf die Adresse des DLL-Importthunks (ein Codestub, der die Steuerung an die Funktion übergibt) anstatt auf die Adresse der Funktion fest. In C++ wird der Zeiger auf die Adresse der Funktion festgelegt. Beispiel:

    ```cpp
    __declspec( dllimport ) void func1( void );
    __declspec( dllimport ) int i;

    int *pi = &i;                             // Error in C
    static void ( *pf )( void ) = &func1;     // Address of thunk in C,
                                              // function in C++

    void func2()
    {
       static int *pi = &i;                  // Error in C
       static void ( *pf )( void ) = &func1; // Address of thunk in C,
                                             // function in C++
    }
    ```

   Da ein Programm, das das **`dllexport`** Attribut in der Deklaration eines Objekts enthält, jedoch die Definition für das Objekt an einer beliebigen Stelle im Programm bereitstellen muss, können Sie einen globalen oder lokalen statischen Funktionszeiger mit der Adresse einer Funktion initialisieren **`dllexport`** . Auf ähnliche Weise können Sie einen globalen oder lokalen statischen Datenzeiger mit der Adresse eines **`dllexport`** Datenobjekts initialisieren. Zum Beispiel generiert der folgende Code keine Fehler in C oder C++:

    ```cpp
    __declspec( dllexport ) void func1( void );
    __declspec( dllexport ) int i;

    int *pi = &i;                              // Okay
    static void ( *pf )( void ) = &func1;      // Okay

    void func2()
    {
        static int *pi = &i;                   // Okay
        static void ( *pf )( void ) = &func1;  // Okay
    }
    ```

- Wenn Sie **`dllexport`** auf eine reguläre Klasse anwenden, die über eine Basisklasse verfügt, die nicht als gekennzeichnet ist **`dllexport`** , generiert der Compiler C4275.

   Der Compiler generiert dieselbe Warnung, wenn die Basisklasse eine Spezialisierung einer Klassenvorlage ist. Um dieses Problem zu umgehen, markieren Sie die Basisklasse mit **`dllexport`** . Das Problem bei der Spezialisierung einer Klassen Vorlage besteht darin, dass Sie das platzieren können **`__declspec(dllexport)`** . Sie dürfen die Klassen Vorlage nicht markieren. Instanziieren Sie stattdessen explizit die Klassen Vorlage, und markieren Sie diese explizite Instanziierung mit **`dllexport`** . Beispiel:

    ```cpp
    template class __declspec(dllexport) B<int>;
    class __declspec(dllexport) D : public B<int> {
    // ...
    ```

   Diese Problemumgehung funktioniert nicht, wenn das Vorlagenargument die ableitende Klasse ist. Beispiel:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

   Da es sich hierbei um ein gängiges Muster mit Vorlagen handelt, hat der Compiler die Semantik von geändert, **`dllexport`** Wenn er auf eine Klasse angewendet wird, die über eine oder mehrere Basisklassen verfügt, und wenn mindestens eine der Basisklassen eine Spezialisierung einer Klassen Vorlage ist. In diesem Fall gilt der Compiler implizit **`dllexport`** für die Spezialisierungs Klassen Vorlagen. Sie können folgende Aktionen ausführen und keine Warnung erhalten:

    ```cpp
    class __declspec(dllexport) D : public B<D> {
    // ...
    ```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
