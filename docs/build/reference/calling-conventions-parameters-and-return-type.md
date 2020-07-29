---
title: Aufrufkonventionen, Parameter und Rückgabetyp
ms.date: 02/13/2019
helpviewer_keywords:
- calling conventions, helper functions
- helper functions, calling conventions
- helper functions, return types
ms.assetid: 0ffa4558-6005-4803-be95-7a8ec8837660
ms.openlocfilehash: 8813bab0cb55aa57792d0031433d96eefb095da4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223914"
---
# <a name="calling-conventions-parameters-and-return-type"></a>Aufrufkonventionen, Parameter und Rückgabetyp

Die Hilfsroutine hat den folgenden Prototyp:

```
FARPROC WINAPI __delayLoadHelper2(
    PCImgDelayDescr pidd,
    FARPROC * ppfnIATEntry
);
```

### <a name="parameters"></a>Parameter

*pidd*<br/>
Ein **`const`** Zeiger auf einen `ImgDelayDescr` , der die Offsets der verschiedenen Import bezogenen Daten, einen Zeitstempel für Bindungs Informationen und einen Satz von Attributen enthält, die weitere Informationen über den deskriptorinhalt bereitstellen. Zurzeit gibt es nur ein Attribut, `dlattrRva` , das angibt, dass die Adressen im Deskriptor relative virtuelle Adressen sind. Weitere Informationen finden Sie in den Deklarationen in " *Delta. h*".

Informationen zur Definition der `PCImgDelayDescr` Struktur finden Sie unter [Struktur-und Konstantendefinitionen](structure-and-constant-definitions.md).

*ppatniatentry*<br/>
Ein Zeiger auf den Slot in der verzögert Load Import Address Table (IAT), der mit der Adresse der importierten Funktion aktualisiert wird. Die Hilfsroutine muss denselben Wert speichern, den Sie an diesen Speicherort zurückgibt.

## <a name="expected-return-values"></a>Erwartete Rückgabewerte

Wenn die Funktion erfolgreich ist, gibt sie die Adresse der importierten Funktion zurück.

Wenn die Funktion fehlschlägt, wird eine Ausnahme ausgelöst und 0 zurückgegeben. Es können drei Ausnahmetypen ausgelöst werden:

- Ein ungültiger Parameter, was passiert, wenn die Attribute in `pidd` nicht korrekt angegeben werden.

- `LoadLibrary` ist in der angegebenen DLL fehlgeschlagen.

- Fehlschlagen von `GetProcAddress`.

Sie sind dafür verantwortlich, diese Ausnahmen zu behandeln.

## <a name="remarks"></a>Bemerkungen

Die Aufruf Konvention für die Hilfsfunktion ist **`__stdcall`** . Der Typ des Rückgabewerts ist nicht relevant, daher wird FARPROC verwendet. Diese Funktion hat eine C-Bindung.

Der Rückgabewert für die Hilfsfunktion für das verzögerte Laden muss im übergegebenen Funktionszeigerspeicherort gespeichert werden, es sei denn, Sie möchten, dass Ihre Hilfsfunktion als Benachrichtigungshook verwendet wird. In diesem Fall ist Ihr Code dafür verantwortlich, den entsprechenden Funktionszeiger zum Zurückgeben zu finden. Der vom Linker generierte Thunkcode übernimmt dann diesen Rückgabewert als reales Ziel für den Importvorgang und springt direkt dorthin.

## <a name="sample"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie eine einfache Hookfunktion implementieren.

```C
FARPROC WINAPI delayHook(unsigned dliNotify, PDelayLoadInfo pdli)
{
    switch (dliNotify) {
        case dliStartProcessing :

            // If you want to return control to the helper, return 0.
            // Otherwise, return a pointer to a FARPROC helper function
            // that will be used instead, thereby bypassing the rest
            // of the helper.

            break;

        case dliNotePreLoadLibrary :

            // If you want to return control to the helper, return 0.
            // Otherwise, return your own HMODULE to be used by the
            // helper instead of having it call LoadLibrary itself.

            break;

        case dliNotePreGetProcAddress :

            // If you want to return control to the helper, return 0.
            // If you choose you may supply your own FARPROC function
            // address and bypass the helper's call to GetProcAddress.

            break;

        case dliFailLoadLib :

            // LoadLibrary failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_MOD_NOT_FOUND) and exit.
            // If you want to handle the failure by loading an alternate
            // DLL (for example), then return the HMODULE for
            // the alternate DLL. The helper will continue execution with
            // this alternate DLL and attempt to find the
            // requested entrypoint via GetProcAddress.

            break;

        case dliFailGetProc :

            // GetProcAddress failed.
            // If you don't want to handle this failure yourself, return 0.
            // In this case the helper will raise an exception
            // (ERROR_PROC_NOT_FOUND) and exit.
            // If you choose you may handle the failure by returning
            // an alternate FARPROC function address.

            break;

        case dliNoteEndProcessing :

            // This notification is called after all processing is done.
            // There is no opportunity for modifying the helper's behavior
            // at this point except by longjmp()/throw()/RaiseException.
            // No return value is processed.

            break;

        default :

            return NULL;
    }

    return NULL;
}

/*
and then at global scope somewhere
const PfnDliHook __pfnDliNotifyHook2 = delayHook;
*/
```

## <a name="see-also"></a>Siehe auch

[Grundlegendes zur Hilfsfunktion](understanding-the-helper-function.md)
