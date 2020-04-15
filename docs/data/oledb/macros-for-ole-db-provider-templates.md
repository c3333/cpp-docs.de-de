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
ms.openlocfilehash: 5d29b2548102b056a21ebfccb037af3a766788ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369804"
---
# <a name="macros-for-ole-db-provider-templates"></a>Makros für OLE DB-Anbietervorlagen

Die OLE DB Templates Provider-Makros bieten Funktionalität in den folgenden Kategorien:

## <a name="property-set-map-macros"></a>Eigenschaftensatz Kartenmakros

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Markiert den Anfang eines Eigenschaftensatzes.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Markiert den Anfang eines Eigenschaftensatzes.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Markiert den Anfang eines Eigenschaftensatzes, der außerhalb des Bereichs des Anbieters ausgeblendet oder definiert werden kann.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Verkettet Eigenschaftengruppen miteinander.|
|[END_PROPERTY_SET](#end_property_set)|Markiert das Ende eines Eigenschaftensatzes.|
|[END_PROPSET_MAP](#end_propset_map)|Markiert das Ende einer Eigenschaftensatzzuordnung.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Legt eine bestimmte Eigenschaft in einer Eigenschaft fest, die auf einen Standardwert festgelegt ist.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Legt eine bestimmte Eigenschaft in einer Eigenschaft fest, die auf einen von Ihnen bereitgestellten Wert festgelegt ist. Außerdem können Sie Flags und Optionen festlegen.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Legt eine bestimmte Eigenschaft in einer Eigenschaft fest, die auf einen von Ihnen bereitgestellten Wert festgelegt ist.|

## <a name="column-map-macros"></a>Spaltenkartenmakros

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Markiert den Anfang der Karteneinträge der Anbieterspalte.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Markiert das Ende der Karteneinträge der Anbieterspalte.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Sie können den Spaltendatentyp angeben.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Sie können die Spaltengröße, den Datentyp, die Genauigkeit, den Maßstab und die Schemarowset-GUID angeben.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Sie können die Spaltengröße angeben.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Es wird davon ausgegangen, dass es sich bei dem Spaltentyp um eine Zeichenfolge handelt.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Wie PROVIDER_COLUMN_ENTRY_LENGTH, können Sie aber auch den Datentyp und die Größe der Spalte angeben.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird. Es wird davon ausgegangen, dass es sich bei dem Spaltentyp um eine Unicode-Zeichenfolge handelt.|

## <a name="schema-rowset-macros"></a>Schema Rowset-Makros

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Markiert den Anfang einer Schemazuordnung.|
|[END_SCHEMA_MAP](#end_schema_map)|Markiert das Ende einer Schemazuordnung.|
|[SCHEMA_ENTRY](#schema_entry)|Ordnet eine GUID einer Klasse zu.|

## <a name="requirements"></a>Anforderungen

**Header:** „atldb.h“

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Markiert den Anfang einer Eigenschaft, die in einer Eigenschaftensatzzuordnung festgelegt ist.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
[in] Die Eigenschaft GUID.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Markiert den Anfang einer Eigenschaft, die in einer Eigenschaftensatzzuordnung festgelegt ist.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
[in] Die Eigenschaft GUID.

*Flaggen*<br/>
[in] UPROPSET_HIDDEN für Eigenschaftensätze, die Sie nicht verfügbar machen möchten, oder UPROPSET_PASSTHROUGH für einen Anbieter, der Eigenschaften verfügbar macht, die außerhalb des Bereichs des Anbieters definiert sind.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Markiert den Anfang der Karteneinträge für den Eigenschaftensatz.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parameter

*Class*<br/>
[in] Die Klasse, in der dieser Eigenschaftensatz angegeben ist. Ein Eigenschaftensatz kann in den folgenden OLE DB-Objekten angegeben werden:

- [Datenquellenobjekte](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Sitzungsobjekte](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Befehle](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Beispiel

Hier ist eine Beispieleigenschaftssatzzuordnung:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

Dieses Makro kettet Eigenschaftengruppen miteinander.

#### <a name="syntax"></a>Syntax

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parameter

*ChainClass*<br/>
[in] Der Name der Klasse, für die Eigenschaften verkettet werden sollen. Dies ist eine Vom ATL-Projekt-Assistent generierte Klasse, die bereits eine Zuordnung enthält (z. B. eine Sitzungs-, Befehls- oder Datenquellenobjektklasse).

#### <a name="remarks"></a>Bemerkungen

Sie können einen Eigenschaftensatz von einer anderen Klasse mit einer eigenen Klasse verketten und dann direkt von Ihrer Klasse aus auf die Eigenschaften zugreifen.

> [!CAUTION]
> Verwenden Sie dieses Makro sparsam. Eine unsachgemäße Verwendung kann dazu führen, dass ein Consumer die OLE DB-Konformitätstests nicht besteht.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Markiert das Ende eines Eigenschaftensatzes.

#### <a name="syntax"></a>Syntax

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
[in] Die Eigenschaft GUID.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

Markiert das Ende von Eigenschaftensatzzuordnungseinträgen.

#### <a name="syntax"></a>Syntax

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

Stellt eine bestimmte Eigenschaft in einem Eigenschaftensatz dar.

#### <a name="syntax"></a>Syntax

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Parameter

*dwPropID*<br/>
[in] Ein [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) -Wert, der in Verbindung mit dem GUID-Eigenschaftensatz verwendet werden kann, um eine Eigenschaft zu identifizieren.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro legt den Wert der Eigenschaft vom Typ `DWORD` auf einen in ATLDB.H definierten Standardwert fest. Verwenden Sie [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md), um die Eigenschaft auf einen Wert Ihrer Wahl festzulegen. Um die `VARTYPE` und [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) für die Eigenschaft gleichzeitig festzulegen, verwenden Sie [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

Stellt eine bestimmte Eigenschaft in einem Eigenschaftensatz dar.

#### <a name="syntax"></a>Syntax

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Parameter

*dwPropID*<br/>
[in] Ein [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) -Wert, der in Verbindung mit dem GUID-Eigenschaftensatz verwendet werden kann, um eine Eigenschaft zu identifizieren.

*vt*<br/>
[in] Die `VARTYPE` dieses Eigenschaftseintrags. (Definiert in wtypes.h)

*dwFlags*<br/>
[in] Ein [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) -Wert, der diesen Eigenschaftseintrag beschreibt.

*value*<br/>
[in] Der Eigenschaftswert von Typ `DWORD`.

*Optionen*<br/>
Entweder DBPROPOPTIONS_REQUIRED oder DBPROPOPTIONS_SETIFCHEAP. Normalerweise muss ein Anbieter keine *Optionen* festlegen, da er vom Consumer festgelegt wird.

#### <a name="remarks"></a>Bemerkungen

Mit diesem Makro können Sie den Wert der Eigenschaft des Typs `DWORD` sowie Optionen und Flags direkt angeben. Um lediglich einen in ATLDB.H definierten Standardwert für eine Eigenschaft festzulegen, verwenden Sie [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Um einen Wert Ihrer Wahl für eine Eigenschaft festzulegen, verwenden Sie [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

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

Mit diesem Makro können Sie direkt den `DWORD`Eigenschaftswert vom Typ angeben. So legen Sie die eigenschaft auf den in ATLDB definierten Standardwert fest. H, verwenden Sie [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Um den Wert, die Flags und die Optionen für die Eigenschaft festzulegen, verwenden Sie [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Markiert den Anfang der Karteneinträge der Anbieterspalte.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parameter

*theClass*<br/>
[in] Der Name der Klasse, zu der diese Karte gehört.

#### <a name="example"></a>Beispiel

Hier ist eine Beispielanbieter-Spaltenzuordnung:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Markiert das Ende der Karteneinträge der Anbieterspalte.

#### <a name="syntax"></a>Syntax

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Mitglied*<br/>
[in] Die Membervariable `dataClass` in der der Spalte entspricht.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Dbtype*<br/>
[in] Der Datentyp in [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Mitglied*<br/>
[in] Die Membervariable, in `dataClass` der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht die Angabe des Spaltendatentyps.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Flaggen*<br/>
[in] Gibt an, wie Daten zurückgegeben werden. Siehe `dwFlags` beschreibung in [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize*<br/>
[in] Die Spaltengröße.

*Dbtype*<br/>
[in] Gibt den Datentyp des Werts an. Siehe `wType` beschreibung in [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Präzision*<br/>
[in] Gibt die Genauigkeit an, die beim Abrufen von Daten verwendet werden soll, wenn *dbType* DBTYPE_NUMERIC oder DBTYPE_DECIMAL ist. Siehe `bPrecision` beschreibung in [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Skala*<br/>
[in] Gibt die Skalierung an, die beim Abrufen von Daten verwendet werden soll, wenn dbType DBTYPE_NUMERIC oder DBTYPE_DECIMAL ist. Siehe `bScale` beschreibung in [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*guid*<br/>
Eine Schema-Rowset-GUID. Eine Liste der Schemarowsets und deren GUIDs finden Sie unter [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der Referenz des *OLE DB-Programmierers.*

#### <a name="remarks"></a>Bemerkungen

Ermöglicht es Ihnen, die Spaltengröße, den Datentyp, die Genauigkeit, den Maßstab und die Schemarowset-GUID der Spalte anzugeben.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Größe*<br/>
[in] Die Spaltengröße in Bytes.

*Mitglied*<br/>
[in] Die Membervariable, in `dataClass` der die Spaltendaten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht die Angabe der Spaltengröße.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Mitglied*<br/>
[in] Die Membervariable in der Datenklasse, in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, wenn davon ausgegangen wird, dass die Spaltendaten [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85))sind.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Dbtype*<br/>
[in] Der Datentyp in [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Größe*<br/>
[in] Die Spaltengröße in Bytes.

*Mitglied*<br/>
[in] Die Membervariable in der Datenklasse, in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Ähnlich wie [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) können Sie aber auch den Datentyp und die Größe der Spalte angeben.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Stellt eine bestimmte Spalte dar, die vom Anbieter unterstützt wird.

#### <a name="syntax"></a>Syntax

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parameter

*name*<br/>
[in] Der Spaltenname.

*Ordnungszahl*<br/>
[in] Die Spaltennummer. Wenn es sich bei der Spalte nicht um eine Lesezeichenspalte handelt, darf die Spaltennummer nicht 0 sein.

*Mitglied*<br/>
[in] Die Membervariable in der Datenklasse, in der die Daten gespeichert werden.

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, wenn es sich bei den Spaltendaten um eine null beendete Unicode-Zeichenfolge [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Bezeichnet den Anfang einer Schemazuordnung.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parameter

*Schemaclass*<br/>
Die Klasse, die den MAP enthält. In der Regel ist dies die Sitzungsklasse.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Schemarowsets finden Sie unter [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) im Windows SDK.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Bezeichnet das Ende der Schemazuordnung.

#### <a name="syntax"></a>Syntax

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [IDBSchemaRowsetImpl Class](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Ordnet eine GUID einer Klasse zu.

#### <a name="syntax"></a>Syntax

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parameter

*guid*<br/>
Eine Schema-Rowset-GUID. Eine Liste der Schemarowsets und deren GUIDs finden Sie unter [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der Referenz des *OLE DB-Programmierers.*

*rowsetClass*<br/>
Die Klasse, die erstellt wird, um das Schemarowset darzustellen.

#### <a name="remarks"></a>Bemerkungen

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) kann dann die Karte nach einer Liste von GUIDs abfragen oder ein Rowset erstellen, wenn ihm eine GUID angezeigt wird. Das erstellte `IDBSchemaRowsetImpl` Schemarowset ähnelt `CRowsetImpl`einer standardabgeleiteten Klasse, `Execute` es muss jedoch eine Methode mit der folgenden Signatur bereitstellen:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Diese `Execute` Funktion füllt die Daten des Rowsets auf. Der ATL-Projekt-Assistent erstellt, wie in [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) in der *Ole DB-Programmierreferenz*beschrieben, drei anfängliche Schemarowsets im Projekt für jedes der drei obligatorischen OLE DB-Schemas:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

Der Assistent fügt außerdem drei entsprechende Einträge in der Schemazuordnung hinzu. Weitere Informationen zum Erstellen eines Anbieters finden Sie unter [Erstellen eines OLE DB-Vorlagenanbieters.](../../data/oledb/creating-an-ole-db-provider.md)

## <a name="see-also"></a>Siehe auch

[OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Architektur von OLE DB-Anbietervorlagen](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Erstellen eines OLE DB-Anbieters](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Ole DB-Anbietervorlagenreferenz](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Makros für OLE DB-Anbietervorlagen](../../data/oledb/macros-for-ole-db-provider-templates.md)
