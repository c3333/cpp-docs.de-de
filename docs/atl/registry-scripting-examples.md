---
title: Beispiele für Registrierungsskripterstellung
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 7bcdb7076982e2f0bd08f4fd82bb45f21e61ef20
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329329"
---
# <a name="registry-scripting-examples"></a>Beispiele für Registrierungsskripterstellung

Die Skriptbeispiele in diesem Thema veranschaulichen, wie Sie der Systemregistrierung einen Schlüssel hinzufügen, den Registrierungs-COM-Server registrieren und mehrere Analysestrukturen angeben.

## <a name="add-a-key-to-hkey_current_user"></a>Hinzufügen eines Schlüssels zu HKEY_CURRENT_USER

Die folgende Analysestruktur veranschaulicht ein einfaches Skript, das der Systemregistrierung einen einzelnen Schlüssel hinzufügt. Insbesondere fügt das Skript den `MyVeryOwnKey`Schlüssel `HKEY_CURRENT_USER`, zu hinzu. Außerdem wird dem neuen Schlüssel `HowGoesIt` der Standardzeichenfolgenwert zugewiesen:

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Dieses Skript kann einfach wie folgt erweitert werden, um mehrere Unterschlüssel zu definieren:

```
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

Jetzt fügt das Skript einen `HasASubkey`Unterschlüssel , zu hinzu. `MyVeryOwnKey` Zu diesem Unterschlüssel fügt `PrettyCool` er sowohl den `DWORD` Unterschlüssel (mit einem `ANameValue` Standardwert von 55) als auch den benannten Wert (mit einem Zeichenfolgenwert von `WithANamedValue`) hinzu.

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Registrieren des Registrar COM Servers

Das folgende Skript registriert den Registrar COM-Server selbst.

```
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

Zur Laufzeit fügt diese Analysestruktur `ATL.Registrar` den `HKEY_CLASSES_ROOT`Schlüssel zu hinzu. Zu diesem neuen Schlüssel heißt es dann:

- Gibt `ATL Registrar Class` als Standardzeichenfolgenwert des Schlüssels an.

- Fügt `CLSID` als Unterschlüssel hinzu.

- Gibt `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` für `CLSID`an. (Dieser Wert ist die CLSID des `CoCreateInstance`Registrars für die Verwendung mit .)

Da `CLSID` sie freigegeben wurde, sollte sie nicht im Nichtregistermodus entfernt werden. Die Anweisung `NoRemove CLSID`, tut dies, indem sie angibt, dass `CLSID` sie im Registermodus geöffnet und im Nichtregistermodus ignoriert werden soll.

Die `ForceRemove` Anweisung stellt eine Housekeeping-Funktion bereit, indem ein Schlüssel und alle unterschlüsseln Schlüssel entfernt werden, bevor der Schlüssel neu erstellt wird. Dies kann nützlich sein, wenn sich die Namen der Unterschlüssel geändert haben. Überprüft in diesem `ForceRemove` Skriptbeispiel, `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` ob bereits vorhanden ist. Wenn dies `ForceRemove`der Zuspruch erwirkt,

- Löscht alle Unterschlüssel `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` rekursiv.

- Erstellt `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Fügt `ATL Registrar Class` als Standardzeichenfolgenwert für `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`hinzu.

Die Analysestruktur fügt nun zwei `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`neue Unterschlüssel zu hinzu. Der erste `ProgID`Schlüssel , ruft einen Standardzeichenfolgenwert ab, der progID ist. Der zweite `InprocServer32`Schlüssel , , ruft `%MODULE%`einen Standardzeichenfolgenwert ab, der ein Präprozessorwert ist, der im Abschnitt [Using Replaceable Parameters (The Registrar es Preprocessor)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)dieses Artikels erläutert wird. `InprocServer32`ruft auch einen `ThreadingModel`benannten Wert ab, , mit dem Zeichenfolgenwert von `Apartment`.

## <a name="specify-multiple-parse-trees"></a>Angeben mehrerer Parse-Strukturen

Um mehr als eine Analysestruktur in einem Skript anzugeben, platzieren Sie einfach eine Struktur am Ende einer anderen. Das folgende Skript fügt z. `MyVeryOwnKey`B. den Schlüssel `HKEY_CLASSES_ROOT` , `HKEY_CURRENT_USER`zu den Analysestrukturen für beide und :

```
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> In einem Registrarskript ist 4K die maximale Tokengröße. (Ein Token ist ein beliebiges erkennbares Element in der Syntax.) Im vorherigen Skriptbeispiel `HKCR`, `HKEY_CURRENT_USER` `'MyVeryOwnKey'`, `'HowGoesIt'` , und sind alle Token.

## <a name="see-also"></a>Siehe auch

[Erstellen von Registrierungsskripts](../atl/creating-registrar-scripts.md)
