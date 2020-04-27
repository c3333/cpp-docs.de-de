---
title: ATL-Registrierungsstelle und Analyse Strukturen
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: de2cea9b0e7b7c62236f708f9aa8217eaa5df51d
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168695"
---
# <a name="understanding-parse-trees"></a>Grundlegendes zu Analyse Strukturen

Sie können in Ihrem Registrierungs Skript eine oder mehrere Analyse Strukturen definieren, wobei jede Analyse Struktur die folgende Form aufweist:

> \<Stamm Schlüssel> {\<Registrierungs Ausdruck>} und höher

Dabei gilt Folgendes:

> \<Root Key>:: = HKEY_CLASSES_ROOT | HKEY_CURRENT_USER | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_LOCAL_MACHINE | HKEY_USERS | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKEY_CURRENT_CONFIG | HKCR | HKCU | \
> &nbsp;&nbsp;&nbsp;&nbsp;HKLM | HKU | Hkpd | HKDD | HKCC

> \<Registrierungs Ausdruck>:: = \<Key> hinzufügen | \<Schlüssel> löschen

> \<Add Key>:: = [**ForceRemove** | **NoRemove** | **Val**]\<Key Name> [\<Key Value>] [{\<Add Key>}]

> \<Delete Key>:: = **Delete**\<Key Name>

> \<Schlüssel Name>:: = **'**\<alphanumerisches>+**'**

> \<Alphanumerische>:: = *beliebiges Zeichen ungleich NULL, d. h. ASCII 0*

> \<Schlüsselwert>:: = \<Schlüsseltyp \<>Schlüssel Name>

> \<Schlüsseltyp>:: = **s** | **d**

> \<Schlüsselwert>:: = **'**\<alphanumerisches>**'**

> [!NOTE]
> `HKEY_CLASSES_ROOT`und `HKCR` sind gleichwertig. `HKEY_CURRENT_USER` und `HKCU` sind gleichwertig. Und so weiter.

Eine Analyse Struktur kann dem \<Stamm Schlüssel> mehrere Schlüssel und Unterschlüssel hinzufügen. Dabei wird das Handle eines unter Schlüssels geöffnet, bis der Parser die Analyse aller seiner Unterschlüssel abgeschlossen hat. Diese Vorgehensweise ist effizienter als die Funktionsweise eines einzelnen Schlüssels, wie im folgenden Beispiel gezeigt:

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

Hier wird die Registrierungsstelle anfänglich geöffnet ( `HKEY_CLASSES_ROOT\MyVeryOwnKey`erstellt). Anschließend wird angezeigt, `MyVeryOwnKey` dass über einen Unterschlüssel verfügt. Anstatt den Schlüssel zu zu schließen `MyVeryOwnKey`, behält die Registrierungsstelle das Handle bei und wird mit `HasASubKey` diesem übergeordneten Handle geöffnet (erstellt). (Die Systemregistrierung kann langsamer sein, wenn kein übergeordnetes Handle geöffnet ist.) Daher ist das `HKEY_CLASSES_ROOT\MyVeryOwnKey` öffnen und anschließende `HasASubKey` öffnen `MyVeryOwnKey` mit als übergeordnetes Element schneller als `MyVeryOwnKey`das Öffnen `MyVeryOwnKey`, schließen und öffnen `MyVeryOwnKey\HasASubKey`.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen von Registrierungs Skripts](../atl/creating-registrar-scripts.md)
