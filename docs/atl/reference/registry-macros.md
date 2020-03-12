---
title: Registrierungs Makros
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
ms.openlocfilehash: c2a70c15473798ba6eb2ef35e0b7ded395708586
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857142"
---
# <a name="registry-macros"></a>Registrierungs Makros

Diese Makros definieren nützliche Typbibliotheken und Registrierungsfunktionen.

|||
|-|-|
|[_ATL_STATIC_REGISTRY](#_atl_static_registry)|Gibt an, dass der Registrierungscode für das Objekt im Objekt vorliegen soll, um eine Abhängigkeit von ATL zu vermeiden. DLL.|
|[DECLARE_LIBID](#declare_libid)|Bietet eine Möglichkeit für ATL, die *LIBID* der Typbibliothek abzurufen.|
|[DECLARE_NO_REGISTRY](#declare_no_registry)|Vermeidet standardmäßige ATL-Registrierung.|
|[DECLARE_REGISTRY](#declare_registry)|Gibt den Eintrag des Haupt Objekts in der Systemregistrierung ein oder entfernt diesen.|
|[DECLARE_REGISTRY_APPID_RESOURCEID](#declare_registry_appid_resourceid)|Gibt die zum automatischen Registrieren der *AppID*erforderlichen Informationen an.|
|[DECLARE_REGISTRY_RESOURCE](#declare_registry_resource)|Sucht die benannte Ressource und führt das darin ausgeführte Registrierungs Skript aus.|
|[DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid)|Sucht die durch eine ID-Nummer identifizierte Ressource und führt das darin ausgeführte Registrierungs Skript aus.|

## <a name="requirements"></a>Anforderungen

**Header:** Atlcom. h

##  <a name="_atl_static_registry"></a>_ATL_STATIC_REGISTRY

Ein Symbol, das angibt, dass sich der Registrierungscode für das Objekt im Objekt befinden soll, um eine Abhängigkeit von ATL zu vermeiden. DLL.

```
#define _ATL_STATIC_REGISTRY
```

### <a name="remarks"></a>Hinweise

Wenn Sie ATL_STATIC_REGISTRY definieren, sollten Sie den folgenden Code verwenden:

[!code-cpp[NVC_ATL_EventHandlingSample#5](../../atl/codesnippet/cpp/registry-macros_1.cpp)]

##  <a name="declare_libid"></a>DECLARE_LIBID

Bietet eine Möglichkeit für ATL, die *LIBID* der Typbibliothek abzurufen.

```
DECLARE_LIBID( libid )
```

### <a name="parameters"></a>Parameter

*libid*<br/>
Die GUID der Typbibliothek.

### <a name="remarks"></a>Hinweise

Verwenden Sie DECLARE_LIBID in einer `CAtlModuleT`abgeleiteten Klasse.

### <a name="example"></a>Beispiel

Nicht attributierte, vom Assistenten generierte ATL-Projekte haben ein Beispiel für die Verwendung dieses Makros.

##  <a name="declare_no_registry"></a>DECLARE_NO_REGISTRY

Verwenden Sie DECLARE_NO_REGISTRY, wenn Sie eine standardmäßige ATL-Registrierung für die Klasse vermeiden möchten, in der dieses Makro angezeigt wird.

```
DECLARE_NO_REGISTRY()
```

##  <a name="declare_registry"></a>DECLARE_REGISTRY

Gibt die Standard-Klassen Registrierung in der Systemregistrierung ein oder entfernt Sie aus der Systemregistrierung.

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
in Aus Gründen der Abwärtskompatibilität eingeschlossen.

*pid*<br/>
in Ein LPCTSTR, bei dem es sich um einen Versions spezifischen Programm Bezeichner handelt.

*vpid*<br/>
in Ein LPCTSTR, bei dem es sich um einen Versions unabhängigen Programm Bezeichner handelt.

*NID*<br/>
in Ein uint, bei dem es sich um einen Index der Ressourcen Zeichenfolge in der Registrierung handelt, die als Beschreibung des Programms verwendet werden soll.

*flags*<br/>
in Ein DWORD, das das Threading Modell des Programms in der Registrierung enthält. Dies muss einer der folgenden Werte sein: THREADFLAGS_APARTMENT, THREADFLAGS_BOTH oder autprxflag.

### <a name="remarks"></a>Hinweise

Die Standard Registrierung besteht aus der CLSID, der Programm-ID, der Versions unabhängigen Programm-ID, der Beschreibungs Zeichenfolge und dem Thread Modell.

Wenn Sie ein Objekt oder ein Steuerelement mithilfe des ATL-Assistenten zum Hinzufügen von Klassen erstellen, implementiert der Assistent automatisch skriptbasierte Registrierungs Unterstützung und fügt den Dateien das [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) Makro hinzu. Wenn Sie keine skriptbasierte Registrierungs Unterstützung wünschen, müssen Sie dieses Makro durch DECLARE_REGISTRY ersetzen. DECLARE_REGISTRY fügt nur die fünf oben beschriebenen grundlegenden Schlüssel in die Registrierung ein. Sie müssen manuell Code schreiben, um andere Schlüssel in die Registrierung einzufügen.

##  <a name="declare_registry_appid_resourceid"></a>DECLARE_REGISTRY_APPID_RESOURCEID

Gibt die zum automatischen Registrieren der *AppID*erforderlichen Informationen an.

```
DECLARE_REGISTRY_APPID_RESOURCEID(
    resid,
    appid )
```

### <a name="parameters"></a>Parameter

*resid*<br/>
Die Ressourcen-ID der RGS-Datei, die Informationen über die *AppID*enthält.

*appid*<br/>
Ein GUID.

### <a name="remarks"></a>Hinweise

Verwenden Sie DECLARE_REGISTRY_APPID_RESOURCEID in einer `CAtlModuleT`abgeleiteten Klasse.

### <a name="example"></a>Beispiel

Mit dem Assistenten zum Hinzufügen von Klassen Code zu ATL-Projekten hinzugefügte Klassen enthalten ein Beispiel für die Verwendung dieses Makros.

##  <a name="declare_registry_resource"></a>DECLARE_REGISTRY_RESOURCE

Ruft die benannte Ressource mit der Registrierungsdatei ab und führt das Skript aus, um entweder Objekte in die Systemregistrierung einzugeben oder Sie aus der Systemregistrierung zu entfernen.

```
DECLARE_REGISTRY_RESOURCE( x )
```

### <a name="parameters"></a>Parameter

*w*<br/>
in Der Zeichen folgen Bezeichner der Ressource.

### <a name="remarks"></a>Hinweise

Wenn Sie ein Objekt oder ein Steuerelement mithilfe des ATL-Projekt-Assistenten erstellen, implementiert der Assistent automatisch skriptbasierte Registrierungs Unterstützung und fügt das [DECLARE_REGISTRY_RESOURCEID](#declare_registry_resourceid) Makro, das DECLARE_REGISTRY_RESOURCE ähnelt, Ihren Dateien hinzu.

Sie können eine statische Verknüpfung mit der ATL-Registrierungs Komponente (ATL Registry Component, Registrierungs Komponente) für optimierten Registrierungs Zugriff herstellen. Fügen Sie der Datei " *PCH. h* " die folgende Zeile hinzu ("*stdafx. h* " in Visual Studio 2017 und früher), um eine statische Verknüpfung mit dem Registrierungscode zu erhalten:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Wenn ATL Ersatzwerte zur Laufzeit ersetzen soll, geben Sie nicht die DECLARE_REGISTRY_RESOURCE oder DECLARE_REGISTRY_RESOURCEID-Makro an. Erstellen Sie stattdessen ein Array von `_ATL_REGMAP_ENTRIES` Strukturen, wobei jeder Eintrag einen Variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Rufen Sie dann [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) oder [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources) auf, damit das Array übergeben wird. Dadurch werden alle Ersetzungs Werte in den `_ATL_REGMAP_ENTRIES` Strukturen der Registrierungskarte der Registrierungsstelle hinzugefügt.

Weitere Informationen zu ersetzbaren Parametern und zur Skripterstellung finden Sie im Artikel [zur ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente)](../../atl/atl-registry-component-registrar.md).

##  <a name="declare_registry_resourceid"></a>DECLARE_REGISTRY_RESOURCEID

Identisch mit [DECLARE_REGISTRY_RESOURCE](#declare_registry_resource) , mit der Ausnahme, dass es einen vom Assistenten generierten uint verwendet, um die Ressource anstelle eines Zeichen folgen namens zu identifizieren.

```
DECLARE_REGISTRY_RESOURCEID( x )
```

### <a name="parameters"></a>Parameter

*w*<br/>
in Vom Assistenten generierter Bezeichner der Ressource.

### <a name="remarks"></a>Hinweise

Wenn Sie ein Objekt oder ein Steuerelement mithilfe des ATL-Projekt-Assistenten erstellen, implementiert der Assistent automatisch skriptbasierte Registrierungs Unterstützung und fügt der Dateien das DECLARE_REGISTRY_RESOURCEID Makro hinzu.

Sie können eine statische Verknüpfung mit der ATL-Registrierungs Komponente (ATL Registry Component, Registrierungs Komponente) für optimierten Registrierungs Zugriff herstellen. Fügen Sie der Datei " *stdafx. h* " die folgende Zeile hinzu ("*PCH. h* " in Visual Studio 2019 und höher), um eine statische Verknüpfung mit dem Registrierungscode zu erhalten:

[!code-cpp[NVC_ATL_COM#56](../../atl/codesnippet/cpp/registry-macros_2.h)]

Wenn ATL Ersatzwerte zur Laufzeit ersetzen soll, geben Sie nicht die DECLARE_REGISTRY_RESOURCE oder DECLARE_REGISTRY_RESOURCEID-Makro an. Erstellen Sie stattdessen ein Array von `_ATL_REGMAP_ENTRIES` Strukturen, wobei jeder Eintrag einen Variablen Platzhalter enthält, der mit einem Wert gekoppelt ist, um den Platzhalter zur Laufzeit zu ersetzen. Rufen Sie dann [CAtlModule::UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced) oder [CAtlModule::UpdateRegistryFromResourceS](catlmodule-class.md#updateregistryfromresources) auf, damit das Array übergeben wird. Dadurch werden alle Ersetzungs Werte in den `_ATL_REGMAP_ENTRIES` Strukturen der Registrierungskarte der Registrierungsstelle hinzugefügt.

Weitere Informationen zu ersetzbaren Parametern und zur Skripterstellung finden Sie im Artikel [zur ATL-Registrierungs Komponente (Registrierungs Komponente, Registrierungs Komponente)](../../atl/atl-registry-component-registrar.md).

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
