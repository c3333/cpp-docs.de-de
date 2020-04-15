---
title: Verwenden austauschbarer Parameter (ATL-Registrar)
ms.date: 11/04/2016
helpviewer_keywords:
- '%MODULE%'
ms.assetid: 0b376994-84a6-4967-8d97-8c01dfc94efe
ms.openlocfilehash: 2474db2de384baa9113ed39aef4d3d9c9048903d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329233"
---
# <a name="using-replaceable-parameters-the-registrar39s-preprocessor"></a>Verwenden austauschbarer Parameter (Der Registrar&#39;-Präprozessor)

Ersetzbare Parameter ermöglichen es dem Client eines Registrars, Laufzeitdaten anzugeben. Zu diesem Thema verwaltet der Registrar eine Ersatzzuordnung, in die er die Werte eingibt, die den austauschbaren Parametern in Ihrem Skript zugeordnet sind. Der Registrar macht diese Einträge zur Laufzeit.

## <a name="using-module"></a><a name="_atl_using_.25.module.25"></a>Verwenden von %MODULE%

Der [ATL-Steuerelement-Assistent](../atl/reference/atl-control-wizard.md) generiert `%MODULE%`automatisch ein Skript, das verwendet. ATL verwendet diesen austauschbaren Parameter für den tatsächlichen Speicherort der DLL oder EXE Ihres Servers.

## <a name="concatenating-run-time-data-with-script-data"></a>Verconcenierende Laufzeitdaten mit Skriptdaten

Eine weitere Verwendung des Präprozessors besteht darin, Laufzeitdaten mit Skriptdaten zu verketten. Angenommen, es wird ein Eintrag benötigt, der einen vollständigen`, 1`Pfad zu einem Modul mit der Zeichenfolge " " enthält, die am Ende angehängt ist. Definieren Sie zunächst die folgende Erweiterung:

```
'MySampleKey' = s '%MODULE%, 1'
```

Bevor Sie dann eine der in [Aufrufen von Skripts](../atl/invoking-scripts.md)aufgeführten Skriptverarbeitungsmethoden aufrufen, fügen Sie der Karte einen Ersatz hinzu:

[!code-cpp[NVC_ATL_Utilities#113](../atl/codesnippet/cpp/using-replaceable-parameters-the-registrar-s-preprocessor_1.cpp)]

Während der Analyse des Skripts `'%MODULE%, 1'` wird `c:\mycode\mydll.dll, 1`der Registrar auf erweitert.

> [!NOTE]
> In einem Registrarskript ist 4K die maximale Tokengröße. (Ein Token ist ein beliebiges erkennbares Element in der Syntax.) Dazu gehören Token, die vom Präprozessor erstellt oder erweitert wurden.

> [!NOTE]
> Um Ersatzwerte zur Laufzeit zu ersetzen, entfernen Sie den Aufruf im Skript an das [DECLARE_REGISTRY_RESOURCE](../atl/reference/registry-macros.md#declare_registry_resource) oder [DECLARE_REGISTRY_RESOURCEID](../atl/reference/registry-macros.md#declare_registry_resourceid) Makro. Ersetzen Sie sie stattdessen `UpdateRegistry` durch Ihre eigene Methode, [die CAtlModule::UpdateRegistryFromResourceD](../atl/reference/catlmodule-class.md#updateregistryfromresourced) oder [CAtlModule::UpdateRegistryFromResourceS](../atl/reference/catlmodule-class.md#updateregistryfromresources)aufruft, und übergeben Sie Ihr Array von _ATL_REGMAP_ENTRY Strukturen. Ihr Array von _ATL_REGMAP_ENTRY muss mindestens einen Eintrag haben, der auf 'NULL,NULL' festgelegt ist, und dieser Eintrag sollte immer der letzte Eintrag sein. Andernfalls wird beim Aufruf ein `UpdateRegistryFromResource` Zugriffsverletzungsfehler generiert.

> [!NOTE]
> Beim Erstellen eines Projekts, das eine ausführbare Datei ausgibt, fügt ATL automatisch Anführungszeichen um den zur Laufzeit erstellten Pfadnamen mit dem Registrierungsskriptparameter **%MODULE%** hinzu. Wenn der Pfadname nicht die Anführungszeichen enthalten soll, verwenden Sie stattdessen den neuen Parameter **%MODULE_RAW%.**
>
> Beim Erstellen eines Projekts, das eine DLL ausgibt, fügt ATL dem Pfadnamen keine Anführungszeichen hinzu, wenn **%MODULE%** oder **%MODULE_RAW %** verwendet wird.

## <a name="see-also"></a>Siehe auch

[Erstellen von Registrierungsskripts](../atl/creating-registrar-scripts.md)
