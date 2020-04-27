---
title: Skripterstellung für die Registrierung
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: 0e225ce28309aa619fd9436d8f4b93e60544e86c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168747"
---
# <a name="registry-scripting-examples"></a>Skripterstellung für die Registrierung

Die Skript Beispiele in diesem Thema veranschaulichen, wie Sie der Systemregistrierung einen Schlüssel hinzufügen, den Registrierungsstellen-com-Server registrieren und mehrere Analyse Strukturen angeben.

## <a name="add-a-key-to-hkey_current_user"></a>Fügen Sie einen Schlüssel zu HKEY_CURRENT_USER

In der folgenden Analyse Struktur wird ein einfaches Skript veranschaulicht, das der Systemregistrierung einen einzelnen Schlüssel hinzufügt. Insbesondere fügt das Skript den Schlüssel, `MyVeryOwnKey`, hinzu. `HKEY_CURRENT_USER` Außerdem wird dem neuen Schlüssel der standardmäßige `HowGoesIt` Zeichen folgen Wert zugewiesen:

```rgs
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

Dieses Skript kann problemlos erweitert werden, um mehrere Unterschlüssel wie folgt zu definieren:

```rgs
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

Nun fügt das Skript einen Unterschlüssel, `HasASubkey`, hinzu. `MyVeryOwnKey` Für diesen Unterschlüssel `PrettyCool` werden sowohl der Unterschlüssel (mit dem Standard `DWORD` Wert 55) als auch der benannte Wert `ANameValue` (mit dem Zeichen folgen Wert `WithANamedValue`) hinzugefügt.

## <a name="register-the-registrar-com-server"></a><a name="_atl_register_the_registrar_com_server"></a>Registrierungs-com-Server registrieren

Mit dem folgenden Skript wird der Registrierungs Registrierungs-com-Server selbst registriert.

```rgs
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

Zur Laufzeit fügt diese Analyse Struktur den `ATL.Registrar` Schlüssel hinzu. `HKEY_CLASSES_ROOT` Zu diesem neuen Schlüssel wird Folgendes angezeigt:

- Gibt `ATL Registrar Class` als standardmäßigen Zeichen folgen Wert des Schlüssels an.

- Fügt `CLSID` als Unterschlüssel hinzu.

- Gibt `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` für `CLSID`an. (Dieser Wert ist die CLSID der Registrierungsstelle für die `CoCreateInstance`Verwendung mit.)

Da `CLSID` freigegeben ist, sollte es nicht im Unregister-Modus entfernt werden. Die-Anweisung `NoRemove CLSID`führt dies durch, indem angegeben `CLSID` wird, dass im Register Modus geöffnet und im Unregister-Modus ignoriert werden soll.

Die `ForceRemove` -Anweisung stellt eine Funktion zum Überschreiben bereit, indem ein Schlüssel und alle seine untergeordneten Schlüssel entfernt werden, bevor der Schlüssel neu erstellt wird. Dies kann hilfreich sein, wenn sich die Namen der Unterschlüssel geändert haben. In diesem Skript Beispiel prüft `ForceRemove` , ob `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` bereits vorhanden ist. Wenn dies der Fall `ForceRemove`ist,:

- Löscht `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` und alle zugehörigen Unterschlüssel rekursiv.

- Wird neu erstellt `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`.

- Fügt `ATL Registrar Class` als Standard Zeichen folgen Wert für `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`hinzu.

In `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`der Analyse Struktur werden nun zwei neue Unterschlüssel hinzugefügt. Der erste Schlüssel, `ProgID`, Ruft einen Standard-Zeichen folgen Wert ab, der die ProgID ist. Der zweite Schlüssel, `InprocServer32`, Ruft einen Standard Zeichen folgen Wert `%MODULE%`ab, der ein Präprozessorwert ist, der im Abschnitt unter [Verwendung von ersetzbaren Parametern (dem Präprozessor der Registrierungsstelle)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)in diesem Artikel erläutert wird. `InprocServer32`Ruft auch einen benannten Wert `ThreadingModel`mit dem Zeichen folgen Wert ab. `Apartment`

## <a name="specify-multiple-parse-trees"></a>Angeben mehrerer Analyse Strukturen

Um mehr als eine Analyse Struktur in einem Skript anzugeben, platzieren Sie einfach eine Struktur am Ende einer anderen. Das folgende Skript fügt z. b. den Schlüssel `MyVeryOwnKey`,, den Analyse Strukturen für `HKEY_CLASSES_ROOT` und `HKEY_CURRENT_USER`hinzu:

```rgs
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
> In einem Registrierungs Skript ist 4K die maximale Tokengröße. (Ein Token ist ein beliebiges erkennbares Element in der Syntax.) Im `HKCR`vorherigen Beispiel `HKEY_CURRENT_USER` `'MyVeryOwnKey'`für die Skripterstellung sind,, `'HowGoesIt'` und alle Token.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen von Registrierungs Skripts](../atl/creating-registrar-scripts.md)
