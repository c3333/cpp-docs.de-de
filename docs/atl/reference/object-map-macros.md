---
title: Objektzuordnungsmakros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326212"
---
# <a name="object-map-macros"></a>Objektzuordnungsmakros

Diese Makros definieren Objektzuordnungen und Einträge.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Ermöglicht das Angeben der Textbeschreibung eines Klassenobjekts, die in die Objektzuordnung eingegeben wird.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Gibt ein ATL-Objekt in die Objektzuordnung ein, aktualisiert die Registrierung und erstellt eine Instanz des Objekts.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Ermöglicht es Ihnen, anzugeben, dass das Objekt registriert und initialisiert werden sollte, jedoch nicht extern über `CoCreateInstance` erstellbar sein sollte.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Ermöglicht das Angeben einer Textbeschreibung für ihr Klassenobjekt.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parameter

*X*<br/>
[in] Die Beschreibung des Klassenobjekts.

### <a name="remarks"></a>Bemerkungen

ATL gibt diese Beschreibung über das [OBJECT_ENTRY_AUTO-Makro](#object_entry_auto) in die Objektzuordnung ein.

DECLARE_OBJECT_DESCRIPTION implementiert `GetObjectDescription` eine Funktion, mit der Sie die [CComCoClass::GetObjectDescription-Methode](ccomcoclass-class.md#getobjectdescription) überschreiben können.

Die `GetObjectDescription` Funktion wird `IComponentRegistrar::GetComponents`von aufgerufen. `IComponentRegistrar`ist eine Automatisierungsschnittstelle, mit der Sie einzelne Komponenten in einer DLL registrieren und aufheben können. Wenn Sie ein Component-Registrar-Objekt mit dem ATL-Projekt-Assistenten erstellen, implementiert der Assistent die `IComponentRegistrar` Schnittstelle automatisch. `IComponentRegistrar`wird in der Regel von Microsoft Transaction Server verwendet.

Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Gibt ein ATL-Objekt in die Objektzuordnung ein, aktualisiert die Registrierung und erstellt eine Instanz des Objekts.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
[in] Die CLSID einer COM-Klasse, die von der C++-Klasse namens *class*implementiert wurde.

*class*<br/>
[in] Der Name der C++-Klasse, die die COM-Klasse implementiert, die durch *clsid*dargestellt wird.

### <a name="remarks"></a>Bemerkungen

Objekt-Eintragsmakros befinden sich im globalen Gültigkeitsbereich des Projekts, um Unterstützung für die Registrierung, Initialisierung und Erstellung einer neuen Klasse bereitzustellen.

OBJECT_ENTRY_AUTO gibt die Funktionszeiger der Creator-Klasse und `CreateInstance` der Class-Factory-Erstellerklassenfunktionen für dieses Objekt in die automatisch generierte ATL-Objektzuordnung ein. Wenn [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) aufgerufen wird, aktualisiert es die Systemregistrierung für jedes Objekt in der Objektzuordnung.

In der folgenden Tabelle wird beschrieben, wie die der Objektzuordnung hinzugefügten Informationen aus der Klasse abgerufen werden, die als zweiter Parameter für dieses Makro angegeben ist.

|Informationen für|Erhalten von|
|---------------------|-------------------|
|COM-Registrierung|[Registrierungsmakros](../../atl/reference/registry-macros.md)|
|Klassenfabrikerstellung|[Klassenfabrikmakros](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Erstellen einer Instanz|[Aggregationsmakros](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Komponentenkategorieerfassung|[Kategorie Makros](../../atl/reference/category-macros.md)|
|Initialisierung und Bereinigung auf Klassenebene|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Ermöglicht es Ihnen, anzugeben, dass das Objekt registriert und initialisiert werden sollte, jedoch nicht extern über `CoCreateInstance` erstellbar sein sollte.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
[in] Die CLSID einer COM-Klasse, die von der C++-Klasse namens *class*implementiert wurde.

*class*<br/>
[in] Der Name der C++-Klasse, die die COM-Klasse implementiert, die durch *clsid*dargestellt wird.

### <a name="remarks"></a>Bemerkungen

Objekt-Eintragsmakros befinden sich im globalen Gültigkeitsbereich des Projekts, um Unterstützung für die Registrierung, Initialisierung und Erstellung einer neuen Klasse bereitzustellen.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO können Sie angeben, dass ein Objekt registriert und initialisiert werden soll (weitere Informationen `CoCreateInstance`finden Sie unter [OBJECT_ENTRY_AUTO),](#object_entry_auto) es sollte jedoch nicht über erstellt werden.

## <a name="see-also"></a>Siehe auch

[Makros](../../atl/reference/atl-macros.md)
