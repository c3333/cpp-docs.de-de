---
title: Registrierungsmakros
ms.date: 08/19/2019
f1_keywords:
- atlcom/ATL::_ATL_STATIC_REGISTRY
- atlcom/ATL::DECLARE_LIBID
- atlcom/ATL::DECLARE_NO_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY
- atlcom/ATL::DECLARE_REGISTRY_APPID_RESOURCEID
- atlcom/ATL::DECLARE_REGISTRY_RESOURCE
- atlcom/ATL::DECLARE_REGISTRY_RESOURCEID
helpviewer_keywords:
- registry, ATL macros
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
ms.openlocfilehash: fd012b4300f4cd72cdc9ab363b770ac1dbefa06e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326045"
---
# <a name="registry-macros"></a>Registrierungsmakros

Diese Makros definieren nützliche Typbibliotheks- und Registrierungsfunktionen.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Gibt an, dass sich der Registrierungscode für das Objekt im Objekt befindet, um eine Abhängigkeit von ATL zu vermeiden. Dll.|
|[DECLARE_LIBID](#declare_libid)|Bietet eine Möglichkeit für ATL, das *Libid* der Typbibliothek abzuerhalten.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Vermeidet die standardmäßige ATL-Registrierung.|
|[DECLARE_REGISTRY](#declare_registry)|Betritt oder entfernt den Eintrag des Hauptobjekts in der Systemregistrierung.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Gibt die Informationen an, die zum automatischen Registrieren der *Appid*erforderlich sind.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Sucht die benannte Ressource und führt das Registrierungsskript darin aus.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Sucht die Durch eine ID-Nummer identifizierte Ressource und führt darin das Registrierungsskript aus.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="_atl_static_registry"></a><a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Ein Symbol, das angibt, dass sich der Registrierungscode für ihr Objekt im Objekt befindet, um eine Abhängigkeit von ATL zu vermeiden. Dll.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie ATL_STATIC_REGISTRY definieren, sollten Sie den folgenden Code verwenden:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

## <a name="declare_libid"></a><a name="declare_libid"></a>DECLARE_LIBID

Bietet eine Möglichkeit für ATL, das *Libid* der Typbibliothek abzuerhalten.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parameter

*Libid*<br/>
Die GUID der Typbibliothek.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `CAtlModuleT`DECLARE_LIBID in einer -abgeleiteten Klasse.

### <a name="example"></a>Beispiel

Nicht zugeschriebene, vom Assistenten generierte ATL-Projekte haben ein Beispiel für die Verwendung dieses Makros.

## <a name="declare_no_registry"></a><a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Verwenden Sie DECLARE_NO_REGISTRY, wenn Sie eine standardmäßige ATL-Registrierung für die Klasse vermeiden möchten, in der dieses Makro angezeigt wird.

```
DECLARE_NO_REGISTRY()
```

## <a name="declare_registry"></a><a name="declare_registry"></a>DECLARE_REGISTRY

Gibt die Standardklassenregistrierung in die Systemregistrierung ein oder entfernt sie aus der Systemregistrierung.

```
DECLARE_REGISTRY(
    class,
    pid,
    vpid,
    nid,
    flags )
```

### <a name="parameters"></a>Parameter

*class*<br/>
[in] Für Abwärtskompatibilität enthalten.

*pid*<br/>
[in] Ein LPCTSTR, bei dem es sich um einen versionsspezifischen Programmbezeichner handelt.

*vpid*<br/>
[in] Ein LPCTSTR, bei dem es sich um einen versionsunabhängigen Programmbezeichner handelt.

*Nid*<br/>
[in] Ein UINT, der ein Index der Ressourcenzeichenfolge in der Registrierung ist, die als Beschreibung des Programms verwendet werden soll.

*Flaggen*<br/>
[in] Ein DWORD, das das Threadingmodell des Programms in der Registrierung enthält. Es muss einer der folgenden Werte sein: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH oder AUTPRXFLAG.

### <a name="remarks"></a>Bemerkungen

Die Standardregistrierung besteht aus CLSID, Programm-ID, versionsunabhängiger Programm-ID, Beschreibungszeichenfolge und Threadmodell.

Wenn Sie ein Objekt oder Steuerelement mit dem ATL-Klassen-Assistenten erstellen, implementiert der Assistent automatisch skriptbasierte Registrierungsunterstützung und fügt den Dateien das [DECLARE_REGISTRY_RESOURCEID-Makro](#declare_registry_resourceid) hinzu. Wenn Sie keine skriptbasierte Registrierungsunterstützung wünschen, müssen Sie dieses Makro durch DECLARE_REGISTRY ersetzen. DECLARE_REGISTRY fügt nur die fünf oben beschriebenen Basisschlüssel in die Registrierung ein. Sie müssen manuell Code schreiben, um andere Schlüssel in die Registrierung einzufügen.

## <a name="declare_registry_appid_resourceid"></a><a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Gibt die Informationen an, die zum automatischen Registrieren der *Appid*erforderlich sind.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parameter

*Resid*<br/>
Die Ressourcen-ID der .rgs-Datei, die Informationen über die *appid*enthält.

*Appid*<br/>
Ein GUID.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie `CAtlModuleT`DECLARE_REGISTRY_APPID_RESOURCEID in einer -derived-Klasse.

### <a name="example"></a>Beispiel

Klassen, die ATL-Projekten mit dem Code-Assistenten zum Hinzufügen von Klassen hinzugefügt wurden, haben ein Beispiel für die Verwendung dieses Makros.

## <a name="declare_registry_resource"></a><a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Ruft die benannte Ressource ab, die die Registrierungsdatei enthält, und führt das Skript aus, um Objekte entweder in die Systemregistrierung einzugeben oder sie aus der Systemregistrierung zu entfernen.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Zeichenfolgenbezeichner Ihrer Ressource.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Objekt oder Steuerelement mit dem ATL-Projekt-Assistenten erstellen, implementiert der Assistent automatisch skriptbasierte Registrierungsunterstützung und fügt den Dateien das [DECLARE_REGISTRY_RESOURCEID-Makro](#declare_registry_resourceid) hinzu, das DECLARE_REGISTRY_RESOURCE ähnelt.

Sie können statisch eine Verknüpfung mit der ATL-Registrierungskomponente (Registrar) herstellen, um einen optimierten Registrierungszugriff zu erhalten. Um eine statische Verknüpfung mit dem Registrierungscode herzustellen, fügen Sie der *Datei pch.h* *(stdafx.h* in Visual Studio 2017 und früher) die folgende Zeile hinzu:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Wenn ATL Ersatzwerte zur Laufzeit ersetzen soll, geben Sie nicht die DECLARE_REGISTRY_RESOURCE oder DECLARE_REGISTRY_RESOURCEID-Makros an. Erstellen Sie stattdessen `_ATL_REGMAP_ENTRIES` ein Array von Strukturen, wobei jeder Eintrag einen variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Rufen Sie dann [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) oder [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)auf, das das Array übergibt. Dadurch werden alle Ersetzungswerte in den `_ATL_REGMAP_ENTRIES` Strukturen zur Ersatzkarte des Registrars hinzugefügt.

Weitere Informationen zu austauschbaren Parametern und Skripts finden Sie im Artikel [The ATL Registry Component (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="declare_registry_resourceid"></a><a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Genauso wie [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) außer dass es eine vom Assistenten generierte UINT verwendet, um die Ressource zu identifizieren, und nicht einen Zeichenfolgennamen.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Vom Assistenten generierten Bezeichner Ihrer Ressource.

### <a name="remarks"></a>Bemerkungen

Wenn Sie ein Objekt oder Steuerelement mit dem ATL-Projekt-Assistenten erstellen, implementiert der Assistent automatisch skriptbasierte Registrierungsunterstützung und fügt den Dateien das DECLARE_REGISTRY_RESOURCEID-Makro hinzu.

Sie können statisch eine Verknüpfung mit der ATL-Registrierungskomponente (Registrar) herstellen, um einen optimierten Registrierungszugriff zu erhalten. Um eine statische Verknüpfung mit dem Registrierungscode herzustellen, fügen Sie der Datei *stdafx.h* *(pch.h* in Visual Studio 2019 und höher) die folgende Zeile hinzu:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Wenn ATL Ersatzwerte zur Laufzeit ersetzen soll, geben Sie nicht die DECLARE_REGISTRY_RESOURCE oder DECLARE_REGISTRY_RESOURCEID-Makros an. Erstellen Sie stattdessen `_ATL_REGMAP_ENTRIES` ein Array von Strukturen, wobei jeder Eintrag einen variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Rufen Sie dann [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) oder [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources)auf, das das Array übergibt. Dadurch werden alle Ersetzungswerte in den `_ATL_REGMAP_ENTRIES` Strukturen zur Ersatzkarte des Registrars hinzugefügt.

Weitere Informationen zu austauschbaren Parametern und Skripts finden Sie im Artikel [The ATL Registry Component (Registrar)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
