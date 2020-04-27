---
title: Verwenden von ersetzbaren Parametern (ATL-Registrierungsstelle)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: debbccea5836fa63282b62ff87573160069fb169
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168682"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Verwenden von verteilbaren Parametern (der Registrierungsstelle&#39;s-Präprozessor)

Ersetzbare Parameter ermöglichen es dem Client der Registrierungsstelle, Laufzeitdaten anzugeben. Zu diesem Zweck behält die Registrierungsstelle eine Ersatz Zuordnung bei, in die Sie die Werte eingibt, die den ersetzbaren Parametern in Ihrem Skript zugeordnet sind. Diese Einträge werden von der Registrierungsstelle zur Laufzeit erstellt.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Verwenden von% Module%

Der [ATL-Steuer](../atl/reference/atl-control-wizard.md) Element-Assistent generiert automatisch ein `%MODULE%`Skript, das verwendet. ATL verwendet diesen ersetzbaren Parameter für den tatsächlichen Speicherort der DLL oder exe-Datei des Servers.

## <a name="concatenating-run-time-data-with-script-data"></a>Verketten von Laufzeitdaten mit Skript Daten

Eine weitere Verwendung des Präprozessors ist die Verkettung von Laufzeitdaten mit Skript Daten. Angenommen, ein Eintrag ist erforderlich, der einen vollständigen Pfad zu einem Modul enthält, an dem die`, 1`Zeichenfolge "" am Ende angefügt ist. Definieren Sie zunächst die folgende Erweiterung:

```rgs
'MySampleKey' = s '%MODULE%, 1'
```

Fügen Sie dann vor dem Aufrufen einer der Skript Verarbeitungsmethoden, die unter [aufrufen](../atl/invoking-scripts.md)von Skripts aufgelistet sind, einen Ersatz für die Karte hinzu:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Während der Skript Verarbeitung wird die Registrierungsstelle zu `'%MODULE%, 1'` `c:\mycode\mydll.dll, 1`erweitert.

> [!NOTE]
> In einem Registrierungs Skript ist 4K die maximale Tokengröße. (Ein Token ist ein beliebiges erkennbares Element in der Syntax.) Dies schließt Token ein, die vom Präprozessor erstellt oder erweitert wurden.

> [!NOTE]
> Wenn Sie Ersatzwerte zur Laufzeit ersetzen möchten, entfernen Sie den Aufruf im Skript für das [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) -oder [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) -Makro. Ersetzen Sie ihn stattdessen durch ihre eigene `UpdateRegistry` Methode, die "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" "" [_ATL_REGMAP_ENTRY, "](../atl/reference/catlmodule-class.md#updateregistryfromresources)| [Module](../atl/reference/catlmodule-class.md#updateregistryfromresourced) : Das Array von _ATL_REGMAP_ENTRY muss mindestens einen Eintrag aufweisen, der auf {NULL, NULL} festgelegt ist, und dieser Eintrag sollte immer der letzte Eintrag sein. Andernfalls wird ein Zugriffs Verletzungs Fehler generiert, wenn `UpdateRegistryFromResource` aufgerufen wird.

> [!NOTE]
> Beim Erstellen eines Projekts, das eine ausführbare Datei ausgibt, fügt ATL dem Pfadnamen, der zur Laufzeit erstellt wurde, automatisch Anführungszeichen mit dem Skript Parameter **% Module%** -Registrierungsstelle hinzu. Wenn Sie nicht möchten, dass der Pfadname die Anführungszeichen enthält, verwenden Sie stattdessen den neuen **% MODULE_RAW%** -Parameter.
>
> Beim Entwickeln eines Projekts, das eine DLL ausgibt, fügt ATL dem Pfadnamen keine Anführungszeichen hinzu, wenn **% Module%** oder **% MODULE_RAW%** verwendet wird.

## <a name="see-also"></a>Weitere Informationen:

[Erstellen von Registrierungs Skripts](../atl/creating-registrar-scripts.md)
