---
title: Makros und globale Funktionen für OLE-Consumervorlagen
ms.date: 02/11/2019
f1_keywords:
- ATL.AtlTraceErrorRecords
- ATL::AtlTraceErrorRecords
- AtlTraceErrorRecords
- BEGIN_ACCESSOR
- BEGIN_ACCESSOR_MAP
- END_ACCESSOR
- END_ACCESSOR_MAP
- BEGIN_COLUMN_MAP
- BLOB_ENTRY
- BLOB_ENTRY_LENGTH
- BLOB_ENTRY_LENGTH_STATUS
- BLOB_ENTRY_STATUS
- BLOB_NAME
- BLOB_NAME_LENGTH
- BLOB_NAME_LENGTH_STATUS
- BLOB_NAME_STATUS
- BOOKMARK_ENTRY
- COLUMN_ENTRY
- COLUMN_ENTRY_EX
- COLUMN_ENTRY_LENGTH
- COLUMN_ENTRY_LENGTH_STATUS
- COLUMN_ENTRY_PS
- COLUMN_ENTRY_PS_LENGTH
- COLUMN_ENTRY_PS_LENGTH_STATUS
- COLUMN_ENTRY_PS_STATUS
- COLUMN_ENTRY_STATUS
- COLUMN_ENTRY_TYPE
- COLUMN_ENTRY_TYPE_SIZE
- COLUMN_NAME
- COLUMN_NAME_EX
- COLUMN_NAME_LENGTH
- COLUMN_NAME_LENGTH_STATUS
- COLUMN_NAME_PS
- COLUMN_NAME_PS_LENGTH
- COLUMN_NAME_PS_LENGTH_STATUS
- COLUMN_NAME_PS_STATUS
- COLUMN_NAME_STATUS
- COLUMN_NAME_TYPE
- COLUMN_NAME_TYPE_PS
- COLUMN_NAME_TYPE_SIZE
- COLUMN_NAME_TYPE_STATUS
- END_COLUMN_MAP
- DEFINE_COMMAND
- DEFINE_COMMAND_EX
- BEGIN_PARAM_MAP
- END_PARAM_MAP
- SET_PARAM_TYPE
helpviewer_keywords:
- OLE DB consumer templates, macros
- macros, OLE DB consumer template
- AtlTraceErrorRecords function
- BEGIN_ACCESSOR macro, syntax
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR_MAP macro
- END_ACCESSOR macro
- END_ACCESSOR_MAP macro
- BEGIN_COLUMN_MAP macro
- BLOB_ENTRY macro
- BLOB_ENTRY_LENGTH macro
- BLOB_ENTRY_LENGTH_STATUS macro
- BLOB_ENTRY_STATUS macro
- BLOB_NAME macro
- BLOB_NAME_LENGTH macro
- BLOB_NAME_LENGTH_STATUS macro
- BLOB_NAME_STATUS macro
- BOOKMARK_ENTRY macro
- COLUMN_ENTRY macro
- COLUMN_ENTRY_EX macro
- COLUMN_ENTRY_LENGTH macro
- COLUMN_ENTRY_LENGTH_STATUS macro
- COLUMN_ENTRY_PS macro
- COLUMN_ENTRY_PS_LENGTH macro
- COLUMN_ENTRY_PS_LENGTH_STATUS macro
- COLUMN_ENTRY_PS_STATUS macro
- COLUMN_ENTRY_STATUS macro
- COLUMN_ENTRY_TYPE macro
- COLUMN_ENTRY_TYPE_SIZE macro
- COLUMN_NAME macro
- COLUMN_NAME_EX macro
- COLUMN_NAME_LENGTH macro
- COLUMN_NAME_LENGTH_STATUS macro
- COLUMN_NAME_PS macro
- COLUMN_NAME_PS_LENGTH macro
- COLUMN_NAME_PS_LENGTH_STATUS macro
- COLUMN_NAME_PS_STATUS macro
- COLUMN_NAME_STATUS macro
- COLUMN_NAME_TYPE macro
- COLUMN_NAME_TYPE_PS macro
- COLUMN_NAME_TYPE_SIZE macro
- COLUMN_NAME_TYPE_STATUS macro
- END_COLUMN_MAP macro
- DEFINE_COMMAND macro
- DEFINE_COMMAND_EX macro
- BEGIN_PARAM_MAP macro
- END_PARAM_MAP macro
- SET_PARAM_TYPE macro
ms.assetid: 8765eb7b-32dd-407c-bacf-8890ef959837
ms.openlocfilehash: 60f642366589bb13b15665331a81d440322eb13f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504040"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makros und globale Funktionen für OLE-Consumervorlagen

Die OLE DB Consumer-Vorlagen enthalten die folgenden Makros und globalen Funktionen:

## <a name="global-functions"></a>Globale Funktionen

| Name | Beschreibung |
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Sichert OLE DB Fehler Datensatzinformationen auf dem dumpgerät, wenn ein Fehler zurückgegeben wird.|

## <a name="accessor-map-macros"></a>Accessor-Zuordnungs Makros

| Name | Beschreibung |
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Markiert den Anfang eines accessoreintrags.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Markiert den Beginn der Accessor-Zuordnungseinträge.|
|[END_ACCESSOR](#end_accessor)|Markiert das Ende eines accessoreintrags.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Markiert das Ende der Accessor-Zuordnungs Einträge.|

## <a name="column-map-macros"></a>Spalten Zuordnungs Makros

| Name | Beschreibung |
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Markiert den Anfang der Spalten Zuordnungs Einträge in der Benutzerdaten Satz-Klasse.|
|[BLOB_ENTRY](#blob_entry)|Wird verwendet, um eine Binary Large Object (BLOB) zu binden.|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Gibt die Länge der BLOB-Datenspalte an.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Meldet die Länge und den Status der BLOB-Datenspalte.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Meldet den Status der BLOB-Datenspalte.|
|[BLOB_NAME](#blob_name)|Wird verwendet, um eine Binary Large Object anhand des Spaltennamens zu binden.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Gibt die Länge der BLOB-Datenspalte an.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Meldet die Länge und den Status der BLOB-Datenspalte.|
|[BLOB_NAME_STATUS](#blob_name_status)|Meldet den Status der BLOB-Datenspalte.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Stellt einen Lesezeichen Eintrag für das Rowset dar. Ein Lesezeichen Eintrag ist eine besondere Art von Spalten Eintrag.|
|[COLUMN_ENTRY](#column_entry)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank dar.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt die Parameter *Typ*, *Länge*, *Genauigkeit* *, dezimal*stellen und *Status* .|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt die *length* -Variable.|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt *Status* -und *Längen* Parameter.|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt *Genauigkeit* und *Skalierungs* Parameter.|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt die *Längen* Variablen, die *Genauigkeit* und die *Skalierungs* Parameter.|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt *Status* -und *Längen* Variablen, *Parameter für* *Genauigkeit* und Dezimalstellen.|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt die Parameter *Status* Variable, *Genauigkeit* und *Skala* .|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt die *Status* Variable.|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank dar. Unterstützt *Typparameter* .|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt *Type* -und *size* -Parameter.|
|[COLUMN_NAME](#column_name)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar.|
|[COLUMN_NAME_EX](#column_name_ex)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Datentyp, Größe, Genauigkeit, Dezimalstellen, Spaltenlänge und Spalten Status.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe der Spaltenlänge.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Spaltenlänge und-Status.|
|[COLUMN_NAME_PS](#column_name_ps)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Genauigkeit und Skalierung.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Genauigkeit, Skalierung und Spaltenlänge.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Genauigkeit, Dezimalstellen, Spaltenlänge und Spalten Status.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Genauigkeit, Skalierung und Spalten Status.|
|[COLUMN_NAME_STATUS](#column_name_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe des Spalten Status.|
|[COLUMN_NAME_TYPE](#column_name_type)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe des Datentyps.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Datentyp, Genauigkeit und Skalierung.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe von Datentyp und Größe.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe des Datentyps und des Spalten Status.|
|[END_COLUMN_MAP](#end_column_map)|Markiert das Ende der Spalten Zuordnungs Einträge.|

## <a name="command-macros"></a>Befehls Makros

| Name | Beschreibung |
|-|-|
|[DEFINE_COMMAND](#define_command)|Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand](../../data/oledb/ccommand-class.md) -Klasse verwendet wird. Akzeptiert nur Zeichen folgen Typen, die dem angegebenen Anwendungstyp (ANSI oder Unicode) entsprechen. Es wird empfohlen, anstelle von DEFINE_COMMAND [DEFINE_COMMAND_EX](#define_command_ex) zu verwenden.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand](../../data/oledb/ccommand-class.md) -Klasse verwendet wird. Unterstützt ANSI-und Unicode-Anwendungen.|

## <a name="parameter-map-macros"></a>Parameter Zuordnungs Makros

| Name | Beschreibung |
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Markiert den Anfang der Parameter Zuordnungs Einträge in der Benutzerdaten Satz-Klasse.|
|[END_PARAM_MAP](#end_param_map)|Markiert das Ende der Parameter Zuordnungs Einträge.|
|[SET_PARAM_TYPE](#set_param_type)|Gibt COLUMN_ENTRY Makros an, die dem SET_PARAM_TYPE-Makro als Eingabe, Ausgabe oder Eingabe/Ausgabe folgen.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a> AtlTraceErrorRecords

Sichert OLE DB Fehler Datensatzinformationen auf dem dumpgerät, wenn ein Fehler zurückgegeben wird.

#### <a name="syntax"></a>Syntax

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parameter

*Bauherr*<br/>
in Ein HRESULT, das von einer OLE DB consumertemplate-Member-Funktion zurückgegeben wird.

#### <a name="remarks"></a>Bemerkungen

Wenn Sie nicht S_OK ist *, werden* `AtlTraceErrorRecords` OLE DB Fehler Datensatzinformationen von auf das dumpgerät (die Registerkarte **Debuggen** des Ausgabe Fensters oder einer Datei) Abbilder. Die Fehler Datensatzinformationen, die vom Anbieter abgerufen werden, enthalten die Zeilennummer, die Quelle, die Beschreibung, die Hilfedatei, den Kontext und die GUID für jeden Fehler Daten Satz Eintrag. `AtlTraceErrorRecords` sichert diese Informationen nur in Debugbuilds. In Releasebuilds handelt es sich um einen leeren Stub, der optimiert wird. Weitere Informationen finden Sie unter [CDBErrorInfo-Klasse](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a> BEGIN_ACCESSOR

Markiert den Anfang eines accessoreintrags.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parameter

*num*<br/>
in Die Null-Offset-Zahl für den Accessor in dieser accessorzuordnung.

*Bauto*<br/>
in Gibt an, ob dieser Accessor ein automatischer Accessor oder ein manueller Accessor ist. Wenn **`true`** der Wert ist, ist der Accessor Auto **`false`** . wenn, ist der Accessor manuell. Ein automatischer Accessor bedeutet, dass Daten bei Verschiebungs Vorgängen für Sie abgerufen werden.

#### <a name="remarks"></a>Bemerkungen

Bei mehreren Accessoren für ein Rowset müssen Sie BEGIN_ACCESSOR_MAP angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Das BEGIN_ACCESSOR_MAP-Makro wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_ACCESSOR_MAP](#begin_accessor_map).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a> BEGIN_ACCESSOR_MAP

Markiert den Beginn der Accessor-Zuordnungseinträge.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parameter

*x*<br/>
[in] Der Name der Benutzerdatensatzklasse.

*num*<br/>
[in] Die Anzahl der Accessoren in dieser Accessorzuordnung.

#### <a name="remarks"></a>Bemerkungen

Bei mehreren Accessoren für ein Rowset müssen Sie BEGIN_ACCESSOR_MAP am Anfang angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Die accessorzuordnung wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

Wenn es nur einen Accessor im Benutzerdatensatz gibt, verwenden Sie das Makro [BEGIN_COLUMN_MAP](#begin_column_map).

#### <a name="example"></a>Beispiel

```cpp
class CArtistsAccessor
{
public:
// Data Elements
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];
   short m_nAge;

// Output binding map
BEGIN_ACCESSOR_MAP(CArtistsAccessor, 2)
   BEGIN_ACCESSOR(0, true)
      COLUMN_ENTRY(1, m_szFirstName)
      COLUMN_ENTRY(2, m_szLastName)
   END_ACCESSOR()
   BEGIN_ACCESSOR(1, false) // Not an auto accessor
      COLUMN_ENTRY(3, m_nAge)
   END_ACCESSOR()
END_ACCESSOR_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsAccessor, L" \
   SELECT \
      FirstName, \
      LastName, \
      Age \
      FROM Artists")
};
```

### <a name="end_accessor"></a><a name="end_accessor"></a> END_ACCESSOR

Markiert das Ende eines accessoreintrags.

#### <a name="syntax"></a>Syntax

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Bemerkungen

Für mehrere Accessoren in einem Rowset müssen Sie BEGIN_ACCESSOR_MAP angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Das BEGIN_ACCESSOR_MAP-Makro wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_ACCESSOR_MAP](#begin_accessor_map).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a> END_ACCESSOR_MAP

Markiert das Ende der Accessor-Zuordnungs Einträge.

#### <a name="syntax"></a>Syntax

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Bemerkungen

Für mehrere Accessoren in einem Rowset müssen Sie BEGIN_ACCESSOR_MAP angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Das BEGIN_ACCESSOR_MAP-Makro wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_ACCESSOR_MAP](#begin_accessor_map).

### <a name="begin_column_map"></a><a name="begin_column_map"></a> BEGIN_COLUMN_MAP

Kennzeichnet den Anfang eines Spaltenzuordnungseintrags.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parameter

*x*<br/>
[in] Der Name der Benutzerdatensatzklasse, abgeleitet aus `CAccessor`.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro wird im Fall eines einzelnen Accessors in einem Rowset verwendet. Wenn Sie über mehrere Accessoren in einem Rowset verfügen, verwenden Sie [BEGIN_ACCESSOR_MAP](#begin_accessor_map).

Das BEGIN_COLUMN_MAP-Makro wird mit dem END_COLUMN_MAP-Makro abgeschlossen. Dieses Makro wird verwendet, wenn nur ein Accessor im Benutzerdatensatz erforderlich ist.

Spalten entsprechen den Feldern in dem Rowset, das Sie binden möchten.

#### <a name="example"></a>Beispiel

Hier sehen Sie ein Beispiel für eine Spalten- und Parameterzuordnung:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a> BLOB_ENTRY

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parameter

*nordinon*<br/>
in Die Spaltennummer.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a> BLOB_ENTRY_LENGTH

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_ENTRY](#blob_entry), mit der Ausnahme, dass dieses Makro auch die Länge der BLOB-Spalte in Bytes erhält.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parameter

*nordinon*<br/>
in Die Spaltennummer.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
vorgenommen Die (tatsächliche) Länge der BLOB-Spalte in Bytes.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a> BLOB_ENTRY_LENGTH_STATUS

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_ENTRY](#blob_entry), mit der Ausnahme, dass dieses Makro auch die Länge und den Status der BLOB-Spalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY_LENGTH_STATUS(
    nOrdinal,
    IID,
    flags,
    data,
    length,
    status )
```

#### <a name="parameters"></a>Parameter

*nordinon*<br/>
in Die Spaltennummer.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
vorgenommen Die (tatsächliche) Länge der BLOB-Spalte in Bytes.

*status*<br/>
vorgenommen Der Status der BLOB-Datenspalte.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a> BLOB_ENTRY_STATUS

Wird mit BEGIN_COLUMN_MAP oder BEGIN_ACCESSOR_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_ENTRY](#blob_entry), mit der Ausnahme, dass dieses Makro auch den Status der BLOB-Spalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parameter

*nordinon*<br/>
in Die Spaltennummer.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*status*<br/>
vorgenommen Der Status des BLOB-Felds.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a> BLOB_NAME

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_ENTRY](#blob_entry), mit der Ausnahme, dass dieses Makro einen Spaltennamen anstelle einer Spaltennummer annimmt.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie unter [wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a> BLOB_NAME_LENGTH

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_NAME](#blob_name), mit der Ausnahme, dass dieses Makro auch die Länge der BLOB-Datenspalte in Bytes erhält.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
vorgenommen Die (tatsächliche) Länge der BLOB-Spalte in Bytes.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a> BLOB_NAME_LENGTH_STATUS

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_NAME](#blob_name), mit der Ausnahme, dass dieses Makro auch die Länge und den Status der BLOB-Datenspalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
vorgenommen Die (tatsächliche) Länge der BLOB-Spalte in Bytes.

*status*<br/>
vorgenommen Der Status des BLOB-Felds.

### <a name="blob_name_status"></a><a name="blob_name_status"></a> BLOB_NAME_STATUS

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um eine Binary Large Object ([BLOB](/previous-versions/windows/desktop/ms711511(v=vs.85))) zu binden. Vergleichbar mit [BLOB_NAME](#blob_name), mit der Ausnahme, dass dieses Makro auch den Status der BLOB-Datenspalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*IID*<br/>
in Eine Schnittstellen-GUID, z `IDD_ISequentialStream` . b., die zum Abrufen des BLOBs verwendet wird.

*flags*<br/>
in Speichermodusflags, wie vom OLE-strukturiertem Speichermodell definiert (z `STGM_READ` . b.).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*status*<br/>
vorgenommen Der Status des BLOB-Felds.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a> BOOKMARK_ENTRY

Bindet die Lesezeichen Spalte.

#### <a name="syntax"></a>Syntax

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parameter

*variable*<br/>
in Die Variable, die an die Lesezeichen Spalte gebunden werden soll.

#### <a name="example"></a>Beispiel

```cpp
class CArtistsBookmark
{
public:
// Data Elements
   CBookmark<4> m_bookmark;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

// Output binding map
BEGIN_COLUMN_MAP(CArtistsBookmark)
   BOOKMARK_ENTRY(m_bookmark)
   COLUMN_ENTRY(1, m_nAge)
   COLUMN_ENTRY(2, m_szFirstName)
   COLUMN_ENTRY(3, m_szLastName)
END_COLUMN_MAP()

   void GetRowsetProperties(CDBPropSet* pPropSet)
   {
      pPropSet->AddProperty(DBPROP_BOOKMARKS, true);
   }

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsBookmark, L" \
   SELECT \
      Age, \
      FirstName, \
      LastName \
      FROM Artists")
};
```

Weitere Informationen finden Sie unter [Verwenden von Lesezeichen](using-bookmarks.md) und [CBookmark-Klasse](../../data/oledb/cbookmark-class.md).

### <a name="column_entry"></a><a name="column_entry"></a> COLUMN_ENTRY

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Das COLUMN_ENTRY-Makro wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie in den Beispielen in den Makro Themen [BEGIN_COLUMN_MAP](#begin_column_map) und [BEGIN_ACCESSOR_MAP](#begin_accessor_map).

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a> COLUMN_ENTRY_EX

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*wType*<br/>
in Der-Datentyp.

*nlength*<br/>
in Die Datengröße in Bytes.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit, die beim Daten Einsatz verwendet werden soll, und *wType* ist `DBTYPE_NUMERIC` . Andernfalls wird dieser Parameter ignoriert.

*nskala*<br/>
in Die beim Daten-und *wType* zu verwendende Skala ist `DBTYPE_NUMERIC` oder `DBTYPE_DECIMAL` .

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Das COLUMN_ENTRY_EX-Makro wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

#### <a name="example"></a>Beispiel

Siehe [BOOKMARK_ENTRY](#bookmark_entry).

### <a name="column_entry_length"></a><a name="column_entry_length"></a> COLUMN_ENTRY_LENGTH

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer, beginnend mit einer. Lesezeichen entspricht der Spalte 0 (null).

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro unterstützt die *length* -Variable. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a> COLUMN_ENTRY_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, wenn Sie Längen-und Statusvariablen unterstützen möchten. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a> COLUMN_ENTRY_PS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht es Ihnen, die Genauigkeit und die Dezimal sind der Spalte anzugeben, die Sie binden möchten. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a> COLUMN_ENTRY_PS_LENGTH

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer, beginnend mit einer. Lesezeichen entspricht der Spalte 0 (null).

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht es Ihnen, die Genauigkeit und die Dezimal sind der Spalte anzugeben, die Sie binden möchten. Dieses Makro unterstützt die *length* -Variable. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a> COLUMN_ENTRY_PS_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht es Ihnen, die Genauigkeit und die Dezimal sind der Spalte anzugeben, die Sie binden möchten. Verwenden Sie dieses Makro, wenn Sie Längen-und Statusvariablen unterstützen möchten. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a> COLUMN_ENTRY_PS_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Ermöglicht es Ihnen, die Genauigkeit und die Dezimal sind der Spalte anzugeben, die Sie binden möchten. Dieses Makro unterstützt die *Status* Variable. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_status"></a><a name="column_entry_status"></a> COLUMN_ENTRY_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parameter

Weitere Informationen finden Sie unter [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*.

*nordinon*<br/>
in Die Spaltennummer.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro unterstützt die *Status* Variable. Sie wird an den folgenden Stellen verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_entry_type"></a><a name="column_entry_type"></a> COLUMN_ENTRY_TYPE

Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt *Typparameter* .

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parameter

*nordinon*<br/>
in Die Spaltennummer.

*wType*<br/>
in Datentyp des Spalten Eintrags.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro ist eine spezialisierte Variante des [COLUMN_ENTRY](#column_entry) -Makros, das eine Möglichkeit zum Angeben des Datentyps bereitstellt.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a> COLUMN_ENTRY_TYPE_SIZE

Stellt eine Bindung an die jeweilige Spalte in der Datenbank dar. Unterstützt *Type* -und *size* -Parameter.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parameter

*nordinon*<br/>
in Die Spaltennummer.

*wType*<br/>
in Datentyp des Spalten Eintrags.

*nlength*<br/>
in Größe des Spalten Eintrags in Bytes.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro ist eine spezialisierte Variante des [COLUMN_ENTRY](#column_entry) -Makros, das eine Möglichkeit zum Angeben von Datengröße und-Typ bereitstellt.

### <a name="column_name"></a><a name="column_name"></a> COLUMN_NAME

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [COLUMN_ENTRY](#column_entry), mit der Ausnahme, dass dieses Makro den Spaltennamen anstelle der Spaltennummer annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Die COLUMN_NAME_ *-Makros werden an denselben Stellen wie [COLUMN_ENTRY](#column_entry)verwendet:

- Zwischen den [BEGIN_COLUMN_MAP](#begin_column_map) -und [END_COLUMN_MAP](#end_column_map) -Makros.

- Zwischen den [BEGIN_ACCESSOR](#begin_accessor) -und [END_ACCESSOR](#end_accessor) -Makros.

- Zwischen den [BEGIN_PARAM_MAP](#begin_param_map) -und [END_PARAM_MAP](#end_param_map) -Makros.

### <a name="column_name_ex"></a><a name="column_name_ex"></a> COLUMN_NAME_EX

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch Datentyp, Größe, Genauigkeit, Dezimalstellen, Spaltenlänge und Spalten Status annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*wType*<br/>
in Der-Datentyp.

*nlength*<br/>
in Die Datengröße in Bytes.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit, die beim Daten Einsatz verwendet werden soll, und *wType* ist `DBTYPE_NUMERIC` . Andernfalls wird dieser Parameter ignoriert.

*nskala*<br/>
in Die beim Daten-und *wType* zu verwendende Skala ist `DBTYPE_NUMERIC` oder `DBTYPE_DECIMAL` .

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_length"></a><a name="column_name_length"></a> COLUMN_NAME_LENGTH

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch Spaltenlänge annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a> COLUMN_NAME_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch Spaltenlänge und Spalten Status annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_ps"></a><a name="column_name_ps"></a> COLUMN_NAME_PS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch Genauigkeit und Skalierung erfordert.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a> COLUMN_NAME_PS_LENGTH

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch Genauigkeit, Skalierung und Spaltenlänge annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a> COLUMN_NAME_PS_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch Genauigkeit, Dezimalstellen, Spaltenlänge und Spalten Status annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*length*<br/>
in Die Variable, die an die Spaltenlänge gebunden werden soll.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a> COLUMN_NAME_PS_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch die Genauigkeit, den Skalierungs-und Spalten Status annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*nskala*<br/>
in Die Skala der Spalte, die Sie binden möchten.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_status"></a><a name="column_name_status"></a> COLUMN_NAME_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch den Spalten Status annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_type"></a><a name="column_name_type"></a> COLUMN_NAME_TYPE

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch den Datentyp annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*wType*<br/>
in Der-Datentyp.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a> COLUMN_NAME_TYPE_PS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch den Datentyp, die Genauigkeit und die Skalierung annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*wType*<br/>
in Der-Datentyp.

*ngenauigkeit*<br/>
in Die maximale Genauigkeit, die beim Daten Einsatz verwendet werden soll, und *wType* ist `DBTYPE_NUMERIC` . Andernfalls wird dieser Parameter ignoriert.

*nskala*<br/>
in Die beim Daten-und *wType* zu verwendende Skala ist `DBTYPE_NUMERIC` oder `DBTYPE_DECIMAL` .

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a> COLUMN_NAME_TYPE_SIZE

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch den Datentyp und die Größe annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*wType*<br/>
in Der-Datentyp.

*nlength*<br/>
in Die Datengröße in Bytes.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a> COLUMN_NAME_TYPE_STATUS

Stellt eine Bindung für das Rowset für die jeweilige Spalte im Rowset dar. Vergleichbar mit [column_name](#column_name), mit der Ausnahme, dass dieses Makro auch den Datentyp und den Spalten Status annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
in Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein "L" vor dem Namen einfügen, z. b `L"MyColumn"` .:.

*wType*<br/>
in Der-Datentyp.

*status*<br/>
in Die Variable, die an den Spalten Status gebunden werden soll.

*data*<br/>
in Der entsprechende Datenmember im Benutzerdaten Satz.

#### <a name="remarks"></a>Bemerkungen

Informationen dazu, wo die COLUMN_NAME_ *-Makros verwendet werden, finden Sie unter [column_name](#column_name) .

### <a name="end_column_map"></a><a name="end_column_map"></a> END_COLUMN_MAP

Markiert das Ende der Spalten Zuordnungs Einträge.

#### <a name="syntax"></a>Syntax

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Bemerkungen

Es wird mit einem einzelnen Accessor für ein Rowset verwendet. Das BEGIN_COLUMN_MAP-Makro wird mit dem END_COLUMN_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_COLUMN_MAP](#begin_column_map).

### <a name="define_command"></a><a name="define_command"></a> DEFINE_COMMAND

Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand](../../data/oledb/ccommand-class.md) -Klasse verwendet wird. Akzeptiert nur Zeichen folgen Typen, die dem angegebenen Anwendungstyp (ANSI oder Unicode) entsprechen.

> [!NOTE]
> Es wird empfohlen, anstelle von DEFINE_COMMAND [DEFINE_COMMAND_EX](#define_command_ex) zu verwenden.

#### <a name="syntax"></a>Syntax

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name der Benutzerdaten Satz-Klasse (Command).

*szCommand*<br/>
in Die Befehls Zeichenfolge, die verwendet wird, um das Rowset zu erstellen, wenn [CCommand](../../data/oledb/ccommand-class.md)verwendet wird.

#### <a name="remarks"></a>Bemerkungen

Die angegebene Befehls Zeichenfolge wird als Standard verwendet, wenn Sie in der [CCommand:: Open](./ccommand-class.md#open) -Methode keinen Befehls Text angeben.

Dieses Makro akzeptiert ANSI-Zeichen folgen, wenn Sie die Anwendung als ANSI erstellen, oder Unicode-Zeichen folgen, wenn Sie die Anwendung als Unicode erstellen. Es wird empfohlen, [DEFINE_COMMAND_EX](#define_command_ex) anstelle von DEFINE_COMMAND zu verwenden, da die frühere Unicode-Zeichen folgen akzeptiert, unabhängig vom Typ der ANSI-oder Unicode-Anwendung.

#### <a name="example"></a>Beispiel

Siehe [BOOKMARK_ENTRY](#bookmark_entry).

### <a name="define_command_ex"></a><a name="define_command_ex"></a> DEFINE_COMMAND_EX

Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand](../../data/oledb/ccommand-class.md) -Klasse verwendet wird. Unterstützt Unicode-und ANSI-Anwendungen.

#### <a name="syntax"></a>Syntax

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parameter

*x*<br/>
in Der Name der Benutzerdaten Satz-Klasse (Command).

*wszcommand*<br/>
in Die Befehls Zeichenfolge, die verwendet wird, um das Rowset zu erstellen, wenn [CCommand](../../data/oledb/ccommand-class.md)verwendet wird.

#### <a name="remarks"></a>Bemerkungen

Die angegebene Befehls Zeichenfolge wird als Standard verwendet, wenn Sie in der [CCommand:: Open](./ccommand-class.md#open) -Methode keinen Befehls Text angeben.

Dieses Makro akzeptiert Unicode-Zeichen folgen, unabhängig vom Anwendungstyp. Dieses Makro wird als [DEFINE_COMMAND](#define_command) bevorzugt, da es Unicode und ANSI-Anwendungen unterstützt.

#### <a name="example"></a>Beispiel

Siehe [BOOKMARK_ENTRY](#bookmark_entry).

### <a name="begin_param_map"></a><a name="begin_param_map"></a> BEGIN_PARAM_MAP

Markiert den Anfang der Parameter Zuordnungs Einträge.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parameter

*x*<br/>
[in] Der Name der Benutzerdatensatzklasse.

#### <a name="remarks"></a>Bemerkungen

Parameter werden von- [Befehlen](/previous-versions/windows/desktop/ms724608(v=vs.85))verwendet.

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für das [BEGIN_COLUMN_MAP](#begin_column_map) -Makro.

### <a name="end_param_map"></a><a name="end_param_map"></a> END_PARAM_MAP

Markiert das Ende der Parameter Zuordnungs Einträge.

#### <a name="syntax"></a>Syntax

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für das [BEGIN_PARAM_MAP](#begin_param_map) -Makro.

### <a name="set_param_type"></a><a name="set_param_type"></a> SET_PARAM_TYPE

Gibt COLUMN_ENTRY Makros an, die den SET_PARAM_TYPE Makro Eingabe,-Ausgabe oder-Eingabe/-Ausgabe folgen.

#### <a name="syntax"></a>Syntax

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parameter

*type*<br/>
[in] Der für den Parameter festzulegende Typ.

#### <a name="remarks"></a>Bemerkungen

Anbieter unterstützen nur Parametereingabe-/-ausgabetypen, die von der zugrunde liegenden Datenquelle unterstützt werden. Der Typ ist eine Kombination aus einem oder mehreren `DBPARAMIO` Werten (siehe [DBBINDING-Strukturen](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *OLE DB-Programmier Referenz*):

- `DBPARAMIO_NOTPARAM` Der-Accessor hat keine Parameter. In der Regel legen Sie `eParamIO` diesen Wert in zeilenaccessoren fest, um den Benutzer daran zu erinnern, dass Parameter ignoriert werden.

- `DBPARAMIO_INPUT` Ein Eingabeparameter.

- `DBPARAMIO_OUTPUT` Ein Output-Parameter.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT` Der-Parameter ist ein Eingabe-und ein Output-Parameter.

#### <a name="example"></a>Beispiel

```cpp
class CArtistsProperty
{
public:
   short m_nReturn;
   short m_nAge;
   TCHAR m_szFirstName[21];
   TCHAR m_szLastName[31];

BEGIN_PARAM_MAP(CArtistsProperty)
   SET_PARAM_TYPE(DBPARAMIO_OUTPUT)
   COLUMN_ENTRY(1, m_nReturn)
   SET_PARAM_TYPE(DBPARAMIO_INPUT)
   COLUMN_ENTRY(2, m_nAge)
END_PARAM_MAP()

BEGIN_COLUMN_MAP(CArtistsProperty)
   COLUMN_ENTRY(1, m_szFirstName)
   COLUMN_ENTRY(2, m_szLastName)
END_COLUMN_MAP()

   HRESULT OpenDataSource()
   {
      CDataSource _db;
      _db.Open();
      return m_session.Open(_db);
   }

   void CloseDataSource()
   {
      m_session.Close();
   }

   CSession m_session;

   DEFINE_COMMAND_EX(CArtistsProperty, L" \
      { ? = SELECT Age FROM Artists WHERE Age < ? }")
};
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="see-also"></a>Weitere Informationen

[Makros und globale Funktionen für OLE DB Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
