---
title: ATL-Registrierungsstelle und Analyse Strukturen
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: ff74ff879e757a569232ff19244d3f7598063465
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040287"
---
# <a name="understanding-parse-trees"></a>Grundlegendes zu Analyse Strukturen

Sie können in Ihrem Registrierungs Skript eine oder mehrere Analyse Strukturen definieren, wobei jede Analyse Struktur die folgende Form aufweist:

> \<root key>{\<registry expression>}+

Dabei gilt Folgendes:

> \<root key> :: = HKEY_CLASSES_ROOT \| HKEY_CURRENT_USER \|\
> &emsp;HKEY_LOCAL_MACHINE \| HKEY_USERS \|\
> &emsp;HKEY_PERFORMANCE_DATA \| HKEY_DYN_DATA \|\
> &emsp;HKEY_CURRENT_CONFIG \| HKCR \| HKCU \|\
> &emsp;HKLM \| HKU \| hkpd \| HKDD \| HKCC

> \<registry expression>::= \<Add Key> \|\<Delete Key>

> \<Add Key>:: = \[ **ForceRemove** \| **NoRemove** \| **Val**] \<Key Name> [ \<Key Value> ] [{ \<Add Key> }]

> \<Delete Key> :: = **Löschen**\<Key Name>

> \<Key Name> ::= **'**\<AlphaNumeric>+**'**

> \<AlphaNumeric> :: = *beliebiges Zeichen nicht NULL, d. h. ASCII 0*

> \<Key Value> ::= \<Key Type>\<Key Name>

> \<Key Type> :: = **s** \| **d**

> \<Key Value> ::= **'**\<AlphaNumeric>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT` und `HKCR` sind äquivalent, `HKEY_CURRENT_USER` und `HKCU` sind gleichwertig, usw.

Eine Analyse Struktur kann der mehrere Schlüssel und Unterschlüssel hinzufügen \<root key> . Dabei wird das Handle eines unter Schlüssels geöffnet, bis der Parser die Analyse aller seiner Unterschlüssel abgeschlossen hat. Diese Vorgehensweise ist effizienter als die Funktionsweise eines einzelnen Schlüssels, wie im folgenden Beispiel gezeigt:

```rgs
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

Hier wird die Registrierungsstelle anfänglich geöffnet (erstellt) `HKEY_CLASSES_ROOT\MyVeryOwnKey` . Anschließend wird angezeigt, dass `MyVeryOwnKey` über einen Unterschlüssel verfügt. Anstatt den Schlüssel zu zu schließen `MyVeryOwnKey` , behält die Registrierungsstelle das Handle bei und wird `HasASubKey` mit diesem übergeordneten Handle geöffnet (erstellt). (Die Systemregistrierung kann langsamer sein, wenn kein übergeordnetes Handle geöffnet ist.) Daher `HKEY_CLASSES_ROOT\MyVeryOwnKey` ist das Öffnen und anschließende öffnen `HasASubKey` mit `MyVeryOwnKey` als übergeordnetes Element schneller als das Öffnen `MyVeryOwnKey` , schließen `MyVeryOwnKey` und öffnen `MyVeryOwnKey\HasASubKey` .

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Registrierungs Skripts](../atl/creating-registrar-scripts.md)
