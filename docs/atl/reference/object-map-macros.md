---
title: Objekt Zuordnungs Makros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 73dc924527bac8499adefab3d0d6b51afa500a5a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863185"
---
# <a name="object-map-macros"></a>Objekt Zuordnungs Makros

Diese Makros definieren Objekt Zuordnungen und Einträge.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Ermöglicht es Ihnen, die Textbeschreibung eines Klassen Objekts anzugeben, das in der Objekt Zuordnung eingegeben wird.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Gibt ein ATL-Objekt in die Objekt Zuordnung ein, aktualisiert die Registrierung und erstellt eine Instanz des-Objekts.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Ermöglicht es Ihnen, anzugeben, dass das Objekt registriert und initialisiert werden sollte, jedoch nicht extern über `CoCreateInstance` erstellbar sein sollte.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atlcom. h

##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Ermöglicht es Ihnen, eine Textbeschreibung für das Klassenobjekt anzugeben.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parameter

*x*<br/>
in Die Beschreibung des Klassen Objekts.

### <a name="remarks"></a>Bemerkungen

ATL gibt diese Beschreibung über das [OBJECT_ENTRY_AUTO](#object_entry_auto) -Makro in die Objekt Zuordnung ein.

DECLARE_OBJECT_DESCRIPTION implementiert eine `GetObjectDescription`-Funktion, die Sie verwenden können, um die [CComCoClass:: getobjectdescription](ccomcoclass-class.md#getobjectdescription) -Methode zu überschreiben.

Die `GetObjectDescription`-Funktion wird von `IComponentRegistrar::GetComponents`aufgerufen. `IComponentRegistrar` ist eine Automatisierungsschnittstelle, mit der Sie einzelne Komponenten in einer DLL registrieren und deren Registrierung aufheben können. Wenn Sie ein komponentenregistrierungs Objekt mit dem ATL-Projekt-Assistenten erstellen, wird die `IComponentRegistrar`-Schnittstelle automatisch vom Assistenten implementiert. `IComponentRegistrar` wird in der Regel von Microsoft Transaction Server verwendet.

Weitere Informationen zum ATL-Projekt-Assistenten finden Sie im Artikel [Erstellen eines ATL-Projekts](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Gibt ein ATL-Objekt in die Objekt Zuordnung ein, aktualisiert die Registrierung und erstellt eine Instanz des-Objekts.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
in Die CLSID einer com-Klasse, die von C++ der Klasse namens *Class*implementiert wird.

*class*<br/>
in Der Name der C++ Klasse, die die durch *CLSID*dargestellte com-Klasse implementiert.

### <a name="remarks"></a>Bemerkungen

Objekt-Eintragsmakros befinden sich im globalen Gültigkeitsbereich des Projekts, um Unterstützung für die Registrierung, Initialisierung und Erstellung einer neuen Klasse bereitzustellen.

OBJECT_ENTRY_AUTO gibt die Funktionszeiger der Klasse Creator und Class-Factory Creator `CreateInstance` Funktionen für dieses Objekt in die automatisch generierte ATL-Objekt Zuordnung ein. Wenn [catlcommodule:: RegisterServer](catlcommodule-class.md#registerserver) aufgerufen wird, aktualisiert es die Systemregistrierung für jedes Objekt in der Objekt Zuordnung.

In der folgenden Tabelle wird beschrieben, wie die der Objekt Zuordnung hinzugefügten Informationen aus der Klasse abgerufen werden, die als zweiter Parameter für dieses Makro angegeben wird.

|Informationen zu|Abgerufen von|
|---------------------|-------------------|
|COM-Registrierung|[Registrierungsmakros](../../atl/reference/registry-macros.md)|
|Erstellung der Klassenfactory|[Klassenfactory-Makros](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Erstellen einer Instanz|[Aggregations Makros](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registrierung der Komponenten Kategorie|[Kategorie-Makros](../../atl/reference/category-macros.md)|
|Initialisierung und Bereinigung auf Klassenebene|[Objectmain](ccomobjectrootex-class.md#objectmain)|

##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Ermöglicht es Ihnen, anzugeben, dass das Objekt registriert und initialisiert werden sollte, jedoch nicht extern über `CoCreateInstance` erstellbar sein sollte.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parameter

*CLSID*<br/>
in Die CLSID einer com-Klasse, die von C++ der Klasse namens *Class*implementiert wird.

*class*<br/>
in Der Name der C++ Klasse, die die durch *CLSID*dargestellte com-Klasse implementiert.

### <a name="remarks"></a>Bemerkungen

Objekt-Eintragsmakros befinden sich im globalen Gültigkeitsbereich des Projekts, um Unterstützung für die Registrierung, Initialisierung und Erstellung einer neuen Klasse bereitzustellen.

Mit OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO können Sie angeben, dass ein Objekt registriert und initialisiert werden soll (Weitere Informationen finden Sie unter [OBJECT_ENTRY_AUTO](#object_entry_auto) ), aber es sollte nicht über `CoCreateInstance`erstellbar sein.

## <a name="see-also"></a>Weitere Informationen

[Makros](../../atl/reference/atl-macros.md)
