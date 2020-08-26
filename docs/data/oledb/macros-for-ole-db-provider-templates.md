---
title: Makros für OLE DB-Anbietervorlagen
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: 53ea92c2eece31829a7554c0f9accf2e56d727a9
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840725"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makros für OLE DB-Anbietervorlagen

Die OLE DB Vorlagen-Anbieter Makros bieten Funktionen in den folgenden Kategorien:

## <a name="property-set-map-macros"></a>Eigenschaften Satz-Zuordnungs Makros

| Name | BESCHREIBUNG |
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Markiert den Anfang eines Eigenschaften Satzes.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Markiert den Anfang eines Eigenschaften Satzes.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Markiert den Anfang eines Eigenschaften Satzes, der ausgeblendet oder außerhalb des Bereichs des Anbieters definiert werden kann.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Verkettet Eigenschaften Gruppen.|
|[END_PROPERTY_SET](#end_property_set)|Markiert das Ende eines Eigenschaften Satzes.|
|[END_PROPSET_MAP](#end_propset_map)|Markiert das Ende einer Eigenschaften Satz Zuordnung.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Legt eine bestimmte Eigenschaft in einer Eigenschaft fest, die auf einen Standardwert festgelegt ist.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Legt eine bestimmte Eigenschaft in einer Eigenschaft fest, die auf einen von Ihnen bereitgestellten Wert festgelegt ist. Ermöglicht Ihnen außerdem das Festlegen von Flags und Optionen.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Legt eine bestimmte Eigenschaft in einer Eigenschaft fest, die auf einen von Ihnen bereitgestellten Wert festgelegt ist.|

## <a name="column-map-macros"></a>Spalten Zuordnungs Makros

| Name | BESCHREIBUNG |
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Markiert den Anfang der Karten Einträge für die Anbieter Spalte.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Markiert das Ende der Zuordnungs Einträge für die Anbieter Spalte.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Sie können den Datentyp der Spalte angeben.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Sie können die Größe, den Datentyp, die Genauigkeit, die Skala und die Schemarowset-GUID der Spalte angeben.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Sie können die Spaltengröße angeben.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Es wird angenommen, dass der Spaltentyp eine Zeichenfolge ist.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Wie PROVIDER_COLUMN_ENTRY_LENGTH, aber auch die Angabe des Datentyps der Spalte sowie der Größe ermöglicht.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Es wird angenommen, dass der Spaltentyp eine Unicode-Zeichenfolge ist.|

## <a name="schema-rowset-macros"></a>Schemarowsetmakros

| Name | BESCHREIBUNG |
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Markiert den Anfang einer Schema Zuordnung.|
|[END_SCHEMA_MAP](#end_schema_map)|Markiert das Ende einer Schema Zuordnung.|
|[SCHEMA_ENTRY](#schema_entry)|Ordnet eine GUID einer Klasse zu.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** „atldb.h“

### <a name="begin_property_set"></a><a name="begin_property_set"></a> BEGIN_PROPERTY_SET

Markiert den Anfang einer Eigenschaft, die in einer Eigenschaften Satz Zuordnung festgelegt ist.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Die Eigenschafts-GUID.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX

Markiert den Anfang einer Eigenschaft, die in einer Eigenschaften Satz Zuordnung festgelegt ist.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Die Eigenschafts-GUID.

*flags*<br/>
in UPROPSET_HIDDEN für alle Eigenschaften Sätze, die Sie nicht verfügbar machen möchten, oder UPROPSET_PASSTHROUGH für einen Anbieter, der Eigenschaften verfügbar macht, die außerhalb des Bereichs des Anbieters definiert sind.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a> BEGIN_PROPSET_MAP

Markiert den Anfang der Eigenschaften Satz-Zuordnungs Einträge.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parameter

*Klasse*<br/>
in Die Klasse, in der dieser Eigenschaften Satz angegeben ist. Ein Eigenschaften Satz kann in den folgenden OLE DB Objekten angegeben werden:

- [Datenquellen Objekte](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Sitzungs Objekte](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Befehle](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Beispiel

Hier sehen Sie eine Beispiel-Eigenschaften Satz Zuordnung:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a> CHAIN_PROPERTY_SET

Dieses Makro verkettet Eigenschaften Gruppen.

#### <a name="syntax"></a>Syntax

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parameter

*Chainclass*<br/>
in Der Name der Klasse, für die Eigenschaften verkettet werden sollen. Dies ist eine Klasse, die vom ATL-Projekt-Assistenten generiert wird, der bereits eine Karte (z. b. eine Sitzung, einen Befehl oder eine Datenquellen-Objektklasse) enthält.

#### <a name="remarks"></a>Bemerkungen

Sie können einen Eigenschaften Satz von einer anderen Klasse mit ihrer eigenen Klasse verketten und dann direkt von der Klasse aus auf die Eigenschaften zugreifen.

> [!CAUTION]
> Verwenden Sie dieses Makro sparsam. Eine nicht ordnungsgemäße Verwendung kann bewirken, dass ein Consumer die OLE DB Konformitätstests nicht bestanden hat.

### <a name="end_property_set"></a><a name="end_property_set"></a> END_PROPERTY_SET

Markiert das Ende eines Eigenschaften Satzes.

#### <a name="syntax"></a>Syntax

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
in Die Eigenschafts-GUID.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a><a name="end_propset_map"></a> END_PROPSET_MAP

Markiert das Ende von Eigenschaften Satz-Zuordnungs Einträgen.

#### <a name="syntax"></a>Syntax

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a><a name="property_info_entry"></a> PROPERTY_INFO_ENTRY

Stellt eine bestimmte Eigenschaft in einem Eigenschaftensatz dar.

#### <a name="syntax"></a>Syntax

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Parameter

*dwPropID*<br/>
[in] Ein [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) -Wert, der in Verbindung mit dem GUID-Eigenschaftensatz verwendet werden kann, um eine Eigenschaft zu identifizieren.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro legt den Wert der Eigenschaft vom Typ `DWORD` auf einen in ATLDB.H definierten Standardwert fest. Verwenden Sie [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md), um die Eigenschaft auf einen Wert Ihrer Wahl festzulegen. `VARTYPE`Verwenden Sie [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md), um und [dbpropflags](/previous-versions/windows/desktop/ms724342(v=vs.85)) für die Eigenschaft gleichzeitig festzulegen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX

Stellt eine bestimmte Eigenschaft in einem Eigenschaftensatz dar.

#### <a name="syntax"></a>Syntax

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Parameter

*dwPropID*<br/>
[in] Ein [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) -Wert, der in Verbindung mit dem GUID-Eigenschaftensatz verwendet werden kann, um eine Eigenschaft zu identifizieren.

*vt*<br/>
[in] Die `VARTYPE` dieses Eigenschaftseintrags. (In Wtypes. h definiert)

*dwFlags*<br/>
[in] Ein [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) -Wert, der diesen Eigenschaftseintrag beschreibt.

*value*<br/>
[in] Der Eigenschaftswert von Typ `DWORD`.

*options*<br/>
Entweder DBPROPOPTIONS_REQUIRED oder DBPROPOPTIONS_SETIFCHEAP. Normalerweise müssen von einem Anbieter keine *Optionen* festgelegt werden, da er vom Consumer festgelegt wird.

#### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie den Wert der Eigenschaft des Typs `DWORD` sowie Optionen und Flags direkt angeben. Um lediglich einen in ATLDB.H definierten Standardwert für eine Eigenschaft festzulegen, verwenden Sie [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Um einen Wert Ihrer Wahl für eine Eigenschaft festzulegen, verwenden Sie [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE

Stellt eine bestimmte Eigenschaft in einem Eigenschaftensatz dar.

#### <a name="syntax"></a>Syntax

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>Parameter

*dwPropID*<br/>
[in] Ein [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) -Wert, der in Verbindung mit dem GUID-Eigenschaftensatz verwendet werden kann, um eine Eigenschaft zu identifizieren.

*value*<br/>
[in] Der Eigenschaftswert von Typ `DWORD`.

#### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie den Eigenschafts Wert des Typs direkt angeben `DWORD` . , Um die-Eigenschaft auf den in Atldb definierten Standardwert festzulegen. H, [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md)verwenden. Verwenden Sie [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md), um den Wert, die Flags und die Optionen für die Eigenschaft festzulegen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP

Markiert den Anfang der Karten Einträge für die Anbieter Spalte.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parameter

*spiegeln*<br/>
in Der Name der Klasse, zu der diese Zuordnung gehört.

#### <a name="example"></a>Beispiel

Im folgenden finden Sie eine Beispiel-Karten Spalten Zuordnung:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP

Markiert das Ende der Zuordnungs Einträge für die Anbieter Spalte.

#### <a name="syntax"></a>Syntax

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*Kollege*<br/>
in Die Element Variable in `dataClass` , die der Spalte entspricht.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*DbType*<br/>
in Der Datentyp in [DbType](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Kollege*<br/>
in Die Element Variable in `dataClass` , in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht das Angeben des Spalten Datentyps.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*flags*<br/>
in Gibt an, wie Daten zurückgegeben werden. Weitere Informationen finden Sie unter `dwFlags` [DBBINDING-Strukturen](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colsize*<br/>
in Die Spaltengröße.

*DbType*<br/>
in Gibt den Datentyp des Werts an. Weitere Informationen finden Sie unter `wType` [DBBINDING-Strukturen](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*precision*<br/>
in Gibt die Genauigkeit an, die bei der Datenbeschaffung verwendet werden soll, wenn *DbType* DBTYPE_NUMERIC oder DBTYPE_DECIMAL ist. Weitere Informationen finden Sie unter `bPrecision` [DBBINDING-Strukturen](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*scale*<br/>
in Gibt die Skala an, die beim Daten Bedarf verwendet werden soll, wenn DbType DBTYPE_NUMERIC oder DBTYPE_DECIMAL ist. Weitere Informationen finden Sie unter `bScale` [DBBINDING-Strukturen](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*guid*<br/>
Eine GUID für das Schemarowset. Eine Liste der Schemarowsets und ihrer GUIDs finden Sie unter [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB Programmierer-Referenz* .

#### <a name="remarks"></a>Bemerkungen

Ermöglicht das Angeben der Größe, des Datentyps, der Genauigkeit, der Skala und der Schemarowset-GUID der Spalte.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*size*<br/>
in Die Spaltengröße in Byte.

*Kollege*<br/>
in Die Member-Variable in `dataClass` , die die Spaltendaten speichert.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht es Ihnen, die Spaltengröße anzugeben.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*Kollege*<br/>
in Die Member-Variable in der Datenklasse, in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, wenn davon ausgegangen wird, dass die Spaltendaten [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))werden.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*DbType*<br/>
in Der Datentyp in [DbType](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*size*<br/>
in Die Spaltengröße in Byte.

*Kollege*<br/>
in Die Member-Variable in der Datenklasse, in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Ähnlich wie [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) aber auch die Angabe des Datentyps der Spalte sowie der Größe ermöglicht.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
in Der Spaltenname.

*Ordnungszahl*<br/>
in Die Spaltennummer. Die Spaltennummer darf nicht 0 sein, es sei denn, die Spalte ist eine Lesezeichen Spalte.

*Kollege*<br/>
in Die Member-Variable in der Datenklasse, in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, wenn die Spaltendaten eine NULL-terminierte Unicode-Zeichenfolge [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP

Bezeichnet den Anfang einer Schema Zuordnung.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parameter

*SchemaClass*<br/>
Die Klasse, die die Zuordnung enthält. In der Regel ist dies die Session-Klasse.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu [Schemarowsets finden Sie unter IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) im Windows SDK.

### <a name="end_schema_map"></a><a name="end_schema_map"></a> END_SCHEMA_MAP

Bezeichnet das Ende der Schema Zuordnung.

#### <a name="syntax"></a>Syntax

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [idbschemarowabtimpl-Klasse](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a> SCHEMA_ENTRY

Ordnet eine GUID einer Klasse zu.

#### <a name="syntax"></a>Syntax

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
Eine GUID für das Schemarowset. Eine Liste der Schemarowsets und ihrer GUIDs finden Sie unter [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB Programmierer-Referenz* .

*rowsetClass*<br/>
Die Klasse, die erstellt wird, um das Schemarowset darzustellen.

#### <a name="remarks"></a>Bemerkungen

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) kann dann die Zuordnung nach einer Liste von GUIDs Abfragen, oder es kann ein Rowset erstellt werden, wenn ihm eine GUID zugewiesen ist. Das-Schemarowset `IDBSchemaRowsetImpl` ist vergleichbar mit einer von `CRowsetImpl` abgeleiteten Standardklasse, mit der Ausnahme, dass Sie eine- `Execute` Methode mit der folgenden Signatur bereitstellen muss:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Diese `Execute` Funktion füllt die Rowsetdaten auf. Der ATL-Projekt-Assistent erstellt, wie in [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *OLE DB Programmierer-Referenz*beschrieben, drei anfängliche Schemarowsets im Projekt für jedes der drei obligatorischen OLE DB Schemas:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

Der Assistent fügt außerdem drei zugehörige Einträge in der Schema Zuordnung hinzu. Weitere Informationen zur Verwendung des Assistenten zum Erstellen eines Anbieters finden Sie unter [Erstellen eines OLE DB Vorlagen Anbieters](../../data/oledb/creating-an-ole-db-provider.md) .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur der OLE DB-Anbieter Vorlage](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Erstellen eines OLE DB Anbieters](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referenz zu OLE DB Anbieter Vorlagen](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Makros für OLE DB Anbieter Vorlagen](../../data/oledb/macros-for-ole-db-provider-templates.md)
