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
ms.openlocfilehash: 8b898990672f590f6047eef6fdfd1ed7eecb3f92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369824"
---
# <a name="macros-and-global-functions-for-ole-db-consumer-templates"></a>Makros und globale Funktionen für OLE-Consumervorlagen

Die OLE DB Consumer Templates enthalten die folgenden Makros und globalen Funktionen:

## <a name="global-functions"></a>Globale Funktionen

|||
|-|-|
|[AtlTraceErrorRecords](#atltraceerrorrecords)|Dumpt OLE DB Error Record-Informationen auf das Dumpgerät aus, wenn ein Fehler zurückgegeben wird.|

## <a name="accessor-map-macros"></a>Accessor Map Makros

|||
|-|-|
|[BEGIN_ACCESSOR](#begin_accessor)|Markiert den Anfang eines Accessoreintrags.|
|[BEGIN_ACCESSOR_MAP](#begin_accessor_map)|Markiert den Beginn der Accessor-Zuordnungseinträge.|
|[END_ACCESSOR](#end_accessor)|Markiert das Ende eines Accessoreintrags.|
|[END_ACCESSOR_MAP](#end_accessor_map)|Markiert das Ende der Accessorkarteneinträge.|

## <a name="column-map-macros"></a>Spaltenkartenmakros

|||
|-|-|
|[BEGIN_COLUMN_MAP](#begin_column_map)|Markiert den Anfang der Spaltenzuordnungseinträge in der Benutzerdatensatzklasse.|
|[BLOB_ENTRY](#blob_entry)|Wird verwendet, um ein binäres großes Objekt (BLOB) zu binden.|
|[BLOB_ENTRY_LENGTH](#blob_entry_length)|Meldet die Länge der BLOB-Datenspalte.|
|[BLOB_ENTRY_LENGTH_STATUS](#blob_entry_length_status)|Meldet die Länge und den Status der BLOB-Datenspalte.|
|[BLOB_ENTRY_STATUS](#blob_entry_status)|Meldet den Status der BLOB-Datenspalte.|
|[BLOB_NAME](#blob_name)|Wird verwendet, um ein binäres großes Objekt nach Spaltennamen zu binden.|
|[BLOB_NAME_LENGTH](#blob_name_length)|Meldet die Länge der BLOB-Datenspalte.|
|[BLOB_NAME_LENGTH_STATUS](#blob_name_length_status)|Meldet die Länge und den Status der BLOB-Datenspalte.|
|[BLOB_NAME_STATUS](#blob_name_status)|Meldet den Status der BLOB-Datenspalte.|
|[BOOKMARK_ENTRY](#bookmark_entry)|Stellt einen Lesezeicheneintrag im Rowset dar. Ein Lesezeicheneintrag ist eine spezielle Art von Spalteneintrag.|
|[COLUMN_ENTRY](#column_entry)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank dar.|
|[COLUMN_ENTRY_EX](#column_entry_ex)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *Typ-, Längen-,* *Präzisions-,* *Skalierungs-* und *Statusparameter.* *length*|
|[COLUMN_ENTRY_LENGTH](#column_entry_length)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt die *Längenvariable.*|
|[COLUMN_ENTRY_LENGTH_STATUS](#column_entry_length_status)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *Status-* und *Längenparameter.*|
|[COLUMN_ENTRY_PS](#column_entry_ps)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *Präzisions-* und *Skalierungsparameter.*|
|[COLUMN_ENTRY_PS_LENGTH](#column_entry_ps_length)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *length* die Längenvariablen-, *Präzisions-* und *Skalierungsparameter.*|
|[COLUMN_ENTRY_PS_LENGTH_STATUS](#column_entry_ps_length_status)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *Status-* und *Längenvariablen,* *Genauigkeits-* und *Skalierungsparameter.*|
|[COLUMN_ENTRY_PS_STATUS](#column_entry_ps_status)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *status* die Statusvariablen-, *Genauigkeits-* und *Skalierungsparameter.*|
|[COLUMN_ENTRY_STATUS](#column_entry_status)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt die *Statusvariable.*|
|[COLUMN_ENTRY_TYPE](#column_entry_type)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank dar. Unterstützt *typparameter.*|
|[COLUMN_ENTRY_TYPE_SIZE](#column_entry_type_size)|Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *Typ-* und *Größenparameter.*|
|[Column_name](#column_name)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar.|
|[COLUMN_NAME_EX](#column_name_ex)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation von Datentyp, Größe, Genauigkeit, Skalierung, Spaltenlänge und Spaltenstatus.|
|[COLUMN_NAME_LENGTH](#column_name_length)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation der Spaltenlänge.|
|[COLUMN_NAME_LENGTH_STATUS](#column_name_length_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation der Spaltenlänge und des Status.|
|[COLUMN_NAME_PS](#column_name_ps)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation von Präzision und Skalierung.|
|[COLUMN_NAME_PS_LENGTH](#column_name_ps_length)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation von Genauigkeit, Skalierung und Spaltenlänge.|
|[COLUMN_NAME_PS_LENGTH_STATUS](#column_name_ps_length_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation von Genauigkeit, Skalierung, Spaltenlänge und Spaltenstatus.|
|[COLUMN_NAME_PS_STATUS](#column_name_ps_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation von Genauigkeit, Skalierung und Spaltenstatus.|
|[COLUMN_NAME_STATUS](#column_name_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Angabe des Spaltenstatus.|
|[COLUMN_NAME_TYPE](#column_name_type)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation des Datentyps.|
|[COLUMN_NAME_TYPE_PS](#column_name_type_ps)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation von Datentyp, Genauigkeit und Skalierung.|
|[COLUMN_NAME_TYPE_SIZE](#column_name_type_size)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation des Datentyps und der Datengröße.|
|[COLUMN_NAME_TYPE_STATUS](#column_name_type_status)|Stellt eine Bindung an eine bestimmte Spalte in der Datenbank nach Namen dar. Unterstützt die Spezifikation des Datentyps und des Spaltenstatus.|
|[END_COLUMN_MAP](#end_column_map)|Markiert das Ende der Spaltenzuordnungseinträge.|

## <a name="command-macros"></a>Befehlsmakros

|||
|-|-|
|[DEFINE_COMMAND](#define_command)|Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand-Klasse](../../data/oledb/ccommand-class.md) verwendet wird. Akzeptiert nur Zeichenfolgentypen, die dem angegebenen Anwendungstyp entsprechen (ANSI oder Unicode). Es wird empfohlen, [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) anstelle von DEFINE_COMMAND zu verwenden.|
|[DEFINE_COMMAND_EX](#define_command_ex)|Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand-Klasse](../../data/oledb/ccommand-class.md) verwendet wird. Unterstützt ANSI- und Unicode-Anwendungen.|

## <a name="parameter-map-macros"></a>Parameter-Map-Makros

|||
|-|-|
|[BEGIN_PARAM_MAP](#begin_param_map)|Markiert den Anfang der Parameterzuordnungseinträge in der Benutzerdatensatzklasse.|
|[END_PARAM_MAP](#end_param_map)|Markiert das Ende der Parameterzuordnungseinträge.|
|[SET_PARAM_TYPE](#set_param_type)|Gibt COLUMN_ENTRY Makros an, die dem SET_PARAM_TYPE Makro als Eingabe, Ausgabe oder Eingabe/Ausgabe folgen.|

### <a name="atltraceerrorrecords"></a><a name="atltraceerrorrecords"></a>AtlTraceErrorRecords

Dumpt OLE DB Error Record-Informationen auf das Dumpgerät aus, wenn ein Fehler zurückgegeben wird.

#### <a name="syntax"></a>Syntax

```cpp
inline void AtlTraceErrorRecords(HRESULT hrErr = S_OK);
```

#### <a name="parameters"></a>Parameter

*hErr*<br/>
[in] Ein HRESULT, das von einer OLE DB Consumer Template-Memberfunktion zurückgegeben wird.

#### <a name="remarks"></a>Bemerkungen

Wenn *hErr* nicht `AtlTraceErrorRecords` S_OK ist, werden OLE DB Error Record-Informationen auf das Dumpgerät (die **Registerkarte Debug** des Ausgabefensters oder eine Datei) ausgedumpt. Die Vom Anbieter abgerufenen Fehlerdatensatzinformationen umfassen Zeilennummer, Quelle, Beschreibung, Hilfedatei, Kontext und GUID für jeden Fehlerdatensatzeintrag. `AtlTraceErrorRecords`übergibt diese Informationen nur in Debugbuilds. In Release-Builds handelt es sich um einen leeren Stub, der optimiert wird. Weitere Informationen finden Sie unter [CDBErrorInfo-Klasse](../../data/oledb/cdberrorinfo-class.md).

### <a name="begin_accessor"></a><a name="begin_accessor"></a>BEGIN_ACCESSOR

Markiert den Anfang eines Accessoreintrags.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_ACCESSOR(num, bAuto)
```

#### <a name="parameters"></a>Parameter

*num*<br/>
[in] Die Null-Offset-Nummer für den Accessor in dieser Accessor-Map.

*bAuto*<br/>
[in] Gibt an, ob es sich bei diesem Accessor um einen automatischen oder manuellen Accessor handelt. Wenn **true**, ist der Accessor auto; wenn **false**, ist der Accessor manuell. Ein automatischer Accessor bedeutet, dass Daten für Sie bei Verschiebungsvorgängen abgerufen werden.

#### <a name="remarks"></a>Bemerkungen

Bei mehreren Accessoren in einem Rowset müssen Sie BEGIN_ACCESSOR_MAP angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Das BEGIN_ACCESSOR_MAP Makro wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_accessor_map"></a><a name="begin_accessor_map"></a>BEGIN_ACCESSOR_MAP

Markiert den Beginn der Accessor-Zuordnungseinträge.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_ACCESSOR_MAP(x, num)
```

#### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Benutzerdatensatzklasse.

*num*<br/>
[in] Die Anzahl der Accessoren in dieser Accessorzuordnung.

#### <a name="remarks"></a>Bemerkungen

Bei mehreren Accessoren in einem Rowset müssen Sie BEGIN_ACCESSOR_MAP am Anfang angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Die Accessor-Map wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

Wenn es nur einen Accessor im Benutzerdatensatz gibt, verwenden Sie das Makro [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

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

### <a name="end_accessor"></a><a name="end_accessor"></a>END_ACCESSOR

Markiert das Ende eines Accessoreintrags.

#### <a name="syntax"></a>Syntax

```cpp
END_ACCESSOR()
```

#### <a name="remarks"></a>Bemerkungen

Für mehrere Accessoren in einem Rowset müssen Sie BEGIN_ACCESSOR_MAP angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Das BEGIN_ACCESSOR_MAP Makro wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="end_accessor_map"></a><a name="end_accessor_map"></a>END_ACCESSOR_MAP

Markiert das Ende der Accessorkarteneinträge.

#### <a name="syntax"></a>Syntax

```cpp
END_ACCESSOR_MAP()
```

#### <a name="remarks"></a>Bemerkungen

Für mehrere Accessoren in einem Rowset müssen Sie BEGIN_ACCESSOR_MAP angeben und das BEGIN_ACCESSOR-Makro für jeden einzelnen Accessor verwenden. Das BEGIN_ACCESSOR-Makro wird mit dem END_ACCESSOR-Makro abgeschlossen. Das BEGIN_ACCESSOR_MAP Makro wird mit dem END_ACCESSOR_MAP-Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

### <a name="begin_column_map"></a><a name="begin_column_map"></a>BEGIN_COLUMN_MAP

Kennzeichnet den Anfang eines Spaltenzuordnungseintrags.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_COLUMN_MAP(x)
```

#### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Benutzerdatensatzklasse, abgeleitet aus `CAccessor`.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro wird im Fall eines einzelnen Accessors in einem Rowset verwendet. Wenn Sie über mehrere Accessoren in einem Rowset verfügen, verwenden Sie [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md).

Das BEGIN_COLUMN_MAP Makro wird mit dem END_COLUMN_MAP Makro abgeschlossen. Dieses Makro wird verwendet, wenn nur ein Accessor im Benutzerdatensatz erforderlich ist.

Spalten entsprechen den Feldern in dem Rowset, das Sie binden möchten.

#### <a name="example"></a>Beispiel

Hier sehen Sie ein Beispiel für eine Spalten- und Parameterzuordnung:

<!--[!CODE [NVC_OLEDB_Consumer#16](../codesnippet/vs_snippets_cpp/nvc_oledb_consumer#16)]  -->

### <a name="blob_entry"></a><a name="blob_entry"></a>BLOB_ENTRY

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY(nOrdinal, IID, flags, data)
```

#### <a name="parameters"></a>Parameter

*nOrdinal*<br/>
[in] Die Spaltennummer.

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="example"></a>Beispiel

Siehe [Wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length"></a><a name="blob_entry_length"></a>BLOB_ENTRY_LENGTH

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich [wie BLOB_ENTRY](../../data/oledb/blob-entry.md), mit der Ausnahme, dass dieses Makro auch die Länge in Bytes der BLOB-Spalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY_LENGTH(nOrdinal, IID, flags, data, length)
```

#### <a name="parameters"></a>Parameter

*nOrdinal*<br/>
[in] Die Spaltennummer.

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[out] Die (tatsächliche) Länge in Bytes der BLOB-Spalte.

#### <a name="example"></a>Beispiel

Siehe [Wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_length_status"></a><a name="blob_entry_length_status"></a>BLOB_ENTRY_LENGTH_STATUS

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich [wie BLOB_ENTRY](../../data/oledb/blob-entry.md), mit der Ausnahme, dass dieses Makro auch die Länge und den Status der BLOB-Spalte abruft.

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

*nOrdinal*<br/>
[in] Die Spaltennummer.

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[out] Die (tatsächliche) Länge in Bytes der BLOB-Spalte.

*Status*<br/>
[out] Der Status der BLOB-Datenspalte.

#### <a name="example"></a>Beispiel

Siehe [Wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_entry_status"></a><a name="blob_entry_status"></a>BLOB_ENTRY_STATUS

Wird mit BEGIN_COLUMN_MAP oder BEGIN_ACCESSOR_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich wie [BLOB_ENTRY](../../data/oledb/blob-entry.md), mit der Ausnahme, dass dieses Makro auch den Status der BLOB-Spalte erhält.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_ENTRY_STATUS(nOrdinal, IID, flags, data, status)
```

#### <a name="parameters"></a>Parameter

*nOrdinal*<br/>
[in] Die Spaltennummer.

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*Status*<br/>
[out] Der Status des BLOB-Feldes.

#### <a name="example"></a>Beispiel

Siehe [Wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name"></a><a name="blob_name"></a>BLOB_NAME

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich [wie BLOB_ENTRY](../../data/oledb/blob-entry.md), mit der Ausnahme, dass dieses Makro einen Spaltennamen anstelle einer Spaltennummer verwendet.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME(pszName, IID, flags, data )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="example"></a>Beispiel

Siehe [Wie kann ich ein BLOB abrufen?](../../data/oledb/retrieving-a-blob.md).

### <a name="blob_name_length"></a><a name="blob_name_length"></a>BLOB_NAME_LENGTH

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich [wie BLOB_NAME](../../data/oledb/blob-name.md), mit der Ausnahme, dass dieses Makro auch die Länge in Bytes der BLOB-Datenspalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME_LENGTH(pszName, IID, flags, data, length )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[out] Die (tatsächliche) Länge in Bytes der BLOB-Spalte.

### <a name="blob_name_length_status"></a><a name="blob_name_length_status"></a>BLOB_NAME_LENGTH_STATUS

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich [wie BLOB_NAME](../../data/oledb/blob-name.md), mit der Ausnahme, dass dieses Makro auch die Länge und den Status der BLOB-Datenspalte abruft.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME_LENGTH_STATUS(pszName, IID, flags, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[out] Die (tatsächliche) Länge in Bytes der BLOB-Spalte.

*Status*<br/>
[out] Der Status des BLOB-Feldes.

### <a name="blob_name_status"></a><a name="blob_name_status"></a>BLOB_NAME_STATUS

Wird mit BEGIN_COLUMN_MAP und END_COLUMN_MAP verwendet, um ein binäres großes Objekt ([BLOB )](/previous-versions/windows/desktop/ms711511(v=vs.85))zu binden. Ähnlich wie [BLOB_NAME](../../data/oledb/blob-name.md), mit der Ausnahme, dass dieses Makro auch den Status der BLOB-Datenspalte erhält.

#### <a name="syntax"></a>Syntax

```cpp
BLOB_NAME_STATUS(pszName, IID, flags, data, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*IID*<br/>
[in] Schnittstellen-GUID, `IDD_ISequentialStream`z. B. , die zum Abrufen des BLOB verwendet wird.

*Flaggen*<br/>
[in] Speichermodus-Flags gemäß der Definition durch das OLE `STGM_READ`Structured Storage-Modell (z. B. ).

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*Status*<br/>
[out] Der Status des BLOB-Feldes.

### <a name="bookmark_entry"></a><a name="bookmark_entry"></a>BOOKMARK_ENTRY

Bindet die Lesezeichenspalte.

#### <a name="syntax"></a>Syntax

```cpp
BOOKMARK_ENTRY(variable)
```

#### <a name="parameters"></a>Parameter

*Variable*<br/>
[in] Die Variable, die an die Lesezeichenspalte gebunden werden soll.

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

### <a name="column_entry"></a><a name="column_entry"></a>Column_entry

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY(nOrdinal, data)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Das COLUMN_ENTRY Makro wird an den folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

#### <a name="example"></a>Beispiel

Sehen Sie sich die Beispiele in den Makrothemen [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) und [BEGIN_ACCESSOR_MAP](../../data/oledb/begin-accessor-map.md)an.

### <a name="column_entry_ex"></a><a name="column_entry_ex"></a>COLUMN_ENTRY_EX

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_EX(nOrdinal, wType, nLength, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*wType*<br/>
[in] Der Datentyp.

*nLänge*<br/>
[in] Die Datengröße in Bytes.

*nPräzision*<br/>
[in] Die maximale Genauigkeit, die beim Abrufen `DBTYPE_NUMERIC`von Daten und *wType* verwendet werden kann, ist . Andernfalls wird dieser Parameter ignoriert.

*Nscale*<br/>
[in] Die Skalierung, die beim Abrufen `DBTYPE_NUMERIC` von `DBTYPE_DECIMAL`Daten und *wType* verwendet werden soll, ist oder .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Das COLUMN_ENTRY_EX Makro wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

#### <a name="example"></a>Beispiel

Siehe [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="column_entry_length"></a><a name="column_entry_length"></a>COLUMN_ENTRY_LENGTH

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_LENGTH(nOrdinal, data, length)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer, beginnend mit einer. Lesezeichen entspricht Spalte Null.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro unterstützt die *Längenvariable.* Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_length_status"></a><a name="column_entry_length_status"></a>COLUMN_ENTRY_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_LENGTH_STATUS(nOrdinal, data, length, status)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Verwenden Sie dieses Makro, wenn Sie Längen- und Statusvariablen unterstützen möchten. Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps"></a><a name="column_entry_ps"></a>COLUMN_ENTRY_PS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS(nOrdinal, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Hier können Sie die Genauigkeit und skalierung der Spalte angeben, die Sie binden möchten. Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_length"></a><a name="column_entry_ps_length"></a>COLUMN_ENTRY_PS_LENGTH

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS_LENGTH(nOrdinal, nPrecision, nScale, data, length)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer, beginnend mit einer. Lesezeichen entspricht Spalte Null.

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Hier können Sie die Genauigkeit und skalierung der Spalte angeben, die Sie binden möchten. Dieses Makro unterstützt die *Längenvariable.* Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_length_status"></a><a name="column_entry_ps_length_status"></a>COLUMN_ENTRY_PS_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS_LENGTH_STATUS(nOrdinal, nPrecision, nScale, data, length, status)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Hier können Sie die Genauigkeit und skalierung der Spalte angeben, die Sie binden möchten. Verwenden Sie dieses Makro, wenn Sie Längen- und Statusvariablen unterstützen möchten. Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_ps_status"></a><a name="column_entry_ps_status"></a>COLUMN_ENTRY_PS_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_PS_STATUS(nOrdinal, nPrecision, nScale, data, status)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Hier können Sie die Genauigkeit und skalierung der Spalte angeben, die Sie binden möchten. Dieses Makro unterstützt die *Statusvariable.* Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_status"></a><a name="column_entry_status"></a>COLUMN_ENTRY_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte in der Datenbank dar.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_STATUS(nOrdinal, data, status)
```

#### <a name="parameters"></a>Parameter

Siehe [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Referenz des OLE DB-Programmierers*.

*nOrdinal*<br/>
[in] Die Spaltennummer.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro unterstützt die *Statusvariable.* Es wird an folgenden Stellen verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_entry_type"></a><a name="column_entry_type"></a>COLUMN_ENTRY_TYPE

Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *typparameter.*

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_TYPE (nOrdinal, wType, data)
```

#### <a name="parameters"></a>Parameter

*nOrdinal*<br/>
[in] Die Spaltennummer.

*wType*<br/>
[in] Datentyp des Spalteneintrags.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro ist eine spezielle Variante des [COLUMN_ENTRY](../../data/oledb/column-entry.md) Makros, das eine Möglichkeit zur Angabe des Datentyps bereitstellt.

### <a name="column_entry_type_size"></a><a name="column_entry_type_size"></a>COLUMN_ENTRY_TYPE_SIZE

Stellt eine Bindung an die bestimmte Spalte in der Datenbank dar. Unterstützt *Typ-* und *Größenparameter.*

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_ENTRY_TYPE_SIZE(nOrdinal, wType, nLength, data)
```

#### <a name="parameters"></a>Parameter

*nOrdinal*<br/>
[in] Die Spaltennummer.

*wType*<br/>
[in] Datentyp des Spalteneintrags.

*nLänge*<br/>
[in] Größe des Spalteneintrags in Bytes.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Dieses Makro ist eine [COLUMN_ENTRY](../../data/oledb/column-entry.md) spezialisierte Variante des COLUMN_ENTRY-Makros, das eine Möglichkeit bietet, Datengröße und -typ anzugeben.

### <a name="column_name"></a><a name="column_name"></a>Column_name

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_ENTRY](../../data/oledb/column-entry.md), mit der Ausnahme, dass dieses Makro den Spaltennamen anstelle der Spaltennummer verwendet.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME(pszName, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Die COLUMN_NAME_*-Makros werden an den gleichen Stellen wie [COLUMN_ENTRY](../../data/oledb/column-entry.md)verwendet:

- Zwischen [den BEGIN_COLUMN_MAP-](../../data/oledb/begin-column-map.md) und END_COLUMN_MAP-Makros. [END_COLUMN_MAP](../../data/oledb/end-column-map.md)

- Zwischen [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) und [END_ACCESSOR](../../data/oledb/end-accessor.md) Makros.

- Zwischen [den BEGIN_PARAM_MAP-](../../data/oledb/begin-param-map.md) und END_PARAM_MAP-Makros. [END_PARAM_MAP](../../data/oledb/end-param-map.md)

### <a name="column_name_ex"></a><a name="column_name_ex"></a>COLUMN_NAME_EX

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Datentyp, Größe, Genauigkeit, Maßstab, Spaltenlänge und Spaltenstatus übernimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_EX(pszName, wType, nLength, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*wType*<br/>
[in] Der Datentyp.

*nLänge*<br/>
[in] Die Datengröße in Bytes.

*nPräzision*<br/>
[in] Die maximale Genauigkeit, die beim Abrufen `DBTYPE_NUMERIC`von Daten und *wType* verwendet werden kann, ist . Andernfalls wird dieser Parameter ignoriert.

*Nscale*<br/>
[in] Die Skalierung, die beim Abrufen `DBTYPE_NUMERIC` von `DBTYPE_DECIMAL`Daten und *wType* verwendet werden soll, ist oder .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_length"></a><a name="column_name_length"></a>COLUMN_NAME_LENGTH

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich wie [COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Spaltenlänge hat.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_LENGTH(pszName, data, length)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_length_status"></a><a name="column_name_length_status"></a>COLUMN_NAME_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Spaltenlänge und Spaltenstatus annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_LENGTH_STATUS(pszName, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps"></a><a name="column_name_ps"></a>COLUMN_NAME_PS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich wie [COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Präzision und Skalierung erfordert.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS(pszName, nPrecision, nScale, data )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps_length"></a><a name="column_name_ps_length"></a>COLUMN_NAME_PS_LENGTH

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Genauigkeit, Skalierung und Spaltenlänge benötigt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS_LENGTH(pszName, nPrecision, nScale, data, length )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps_length_status"></a><a name="column_name_ps_length_status"></a>COLUMN_NAME_PS_LENGTH_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Genauigkeit, Skalierung, Spaltenlänge und Spaltenstatus annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS_LENGTH_STATUS(pszName, nPrecision, nScale, data, length, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*length*<br/>
[in] Die Variable, die an die Spaltenlänge gebunden werden soll.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_ps_status"></a><a name="column_name_ps_status"></a>COLUMN_NAME_PS_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Genauigkeit, Skalierung und Spaltenstatus annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_PS_STATUS(pszName, nPrecision, nScale, data, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*nPräzision*<br/>
[in] Die maximale Genauigkeit der Spalte, die Sie binden möchten.

*Nscale*<br/>
[in] Der Maßstab der Spalte, die Sie binden möchten.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_status"></a><a name="column_name_status"></a>COLUMN_NAME_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch den Spaltenstatus annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_STATUS(pszName, data, status )
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type"></a><a name="column_name_type"></a>COLUMN_NAME_TYPE

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich wie [COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch den Datentyp annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE(pszName, wType, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*wType*<br/>
[in] Der Datentyp.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type_ps"></a><a name="column_name_type_ps"></a>COLUMN_NAME_TYPE_PS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Datentyp, Genauigkeit und Skalierung benötigt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE_PS(pszName, wType, nPrecision, nScale, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*wType*<br/>
[in] Der Datentyp.

*nPräzision*<br/>
[in] Die maximale Genauigkeit, die beim Abrufen `DBTYPE_NUMERIC`von Daten und *wType* verwendet werden kann, ist . Andernfalls wird dieser Parameter ignoriert.

*Nscale*<br/>
[in] Die Skalierung, die beim Abrufen `DBTYPE_NUMERIC` von `DBTYPE_DECIMAL`Daten und *wType* verwendet werden soll, ist oder .

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type_size"></a><a name="column_name_type_size"></a>COLUMN_NAME_TYPE_SIZE

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich wie [COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Datentyp und -größe annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE_SIZE(pszName, wType, nLength, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*wType*<br/>
[in] Der Datentyp.

*nLänge*<br/>
[in] Die Datengröße in Bytes.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="column_name_type_status"></a><a name="column_name_type_status"></a>COLUMN_NAME_TYPE_STATUS

Stellt eine Bindung für das Rowset für die bestimmte Spalte im Rowset dar. Ähnlich [wie COLUMN_NAME](../../data/oledb/column-name.md), mit der Ausnahme, dass dieses Makro auch Datentyp und Spaltenstatus annimmt.

#### <a name="syntax"></a>Syntax

```cpp
COLUMN_NAME_TYPE_STATUS(pszName, wType, status, data)
```

#### <a name="parameters"></a>Parameter

*pszName*<br/>
[in] Ein Zeiger auf den Spaltennamen. Der Name muss eine Unicode-Zeichenfolge sein. Sie können dies erreichen, indem Sie ein 'L' `L"MyColumn"`vor den Namen setzen, z. B.: .

*wType*<br/>
[in] Der Datentyp.

*Status*<br/>
[in] Die Variable, die an den Spaltenstatus gebunden werden soll.

*Daten*<br/>
[in] Das entsprechende Datenelement im Benutzerdatensatz.

#### <a name="remarks"></a>Bemerkungen

Weitere Informationen dazu, wo die COLUMN_NAME_*-Makros verwendet werden, finden Sie [in COLUMN_NAME.](../../data/oledb/column-name.md)

### <a name="end_column_map"></a><a name="end_column_map"></a>END_COLUMN_MAP

Markiert das Ende der Spaltenzuordnungseinträge.

#### <a name="syntax"></a>Syntax

```cpp
END_COLUMN_MAP()
```

#### <a name="remarks"></a>Bemerkungen

Es wird mit einem einzelnen Accessor in einem Rowset verwendet. Das BEGIN_COLUMN_MAP Makro wird mit dem END_COLUMN_MAP Makro abgeschlossen.

#### <a name="example"></a>Beispiel

Siehe [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md).

### <a name="define_command"></a><a name="define_command"></a>DEFINE_COMMAND

Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand-Klasse](../../data/oledb/ccommand-class.md) verwendet wird. Akzeptiert nur Zeichenfolgentypen, die dem angegebenen Anwendungstyp entsprechen (ANSI oder Unicode).

> [!NOTE]
> Es wird empfohlen, [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) anstelle von DEFINE_COMMAND zu verwenden.

#### <a name="syntax"></a>Syntax

```cpp
DEFINE_COMMAND(x, szCommand)
```

#### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Benutzerdatensatzklasse (Befehlsklasse).

*szCommand*<br/>
[in] Die Befehlszeichenfolge, die verwendet wird, um das Rowset zu erstellen, wenn [CCommand verwendet](../../data/oledb/ccommand-class.md)wird.

#### <a name="remarks"></a>Bemerkungen

Die von Ihnen angegebene Befehlszeichenfolge wird als Standard verwendet, wenn Sie keinen Befehlstext in der [CCommand::Open-Methode](../../data/oledb/ccommand-open.md) angeben.

Dieses Makro akzeptiert ANSI-Zeichenfolgen, wenn Sie Ihre Anwendung als ANSI- oder Unicode-Zeichenfolgen erstellen, wenn Sie Ihre Anwendung als Unicode erstellen. Es wird empfohlen, [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) anstelle von DEFINE_COMMAND zu verwenden, da erstere Unicode-Zeichenfolgen akzeptiert, unabhängig vom ANSI- oder Unicode-Anwendungstyp.

#### <a name="example"></a>Beispiel

Siehe [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="define_command_ex"></a><a name="define_command_ex"></a>DEFINE_COMMAND_EX

Gibt den Befehl an, der verwendet wird, um das Rowset zu erstellen, wenn die [CCommand-Klasse](../../data/oledb/ccommand-class.md) verwendet wird. Unterstützt Unicode- und ANSI-Anwendungen.

#### <a name="syntax"></a>Syntax

```cpp
DEFINE_COMMAND_EX(x, wszCommand)
```

#### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Benutzerdatensatzklasse (Befehlsklasse).

*wszCommand*<br/>
[in] Die Befehlszeichenfolge, die verwendet wird, um das Rowset zu erstellen, wenn [CCommand verwendet](../../data/oledb/ccommand-class.md)wird.

#### <a name="remarks"></a>Bemerkungen

Die von Ihnen angegebene Befehlszeichenfolge wird als Standard verwendet, wenn Sie keinen Befehlstext in der [CCommand::Open-Methode](../../data/oledb/ccommand-open.md) angeben.

Dieses Makro akzeptiert Unicode-Zeichenfolgen, unabhängig vom Anwendungstyp. Dieses Makro wird [DEFINE_COMMAND](../../data/oledb/define-command.md) bevorzugt, da es Unicode sowie ANSI-Anwendungen unterstützt.

#### <a name="example"></a>Beispiel

Siehe [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).

### <a name="begin_param_map"></a><a name="begin_param_map"></a>BEGIN_PARAM_MAP

Markiert den Anfang der Parameterzuordnungseinträge.

#### <a name="syntax"></a>Syntax

```cpp
BEGIN_PARAM_MAP(x)
```

#### <a name="parameters"></a>Parameter

*X*<br/>
[in] Der Name der Benutzerdatensatzklasse.

#### <a name="remarks"></a>Bemerkungen

Parameter werden von [Befehlen](/previous-versions/windows/desktop/ms724608(v=vs.85))verwendet.

#### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_COLUMN_MAP](../../data/oledb/begin-column-map.md) das BEGIN_COLUMN_MAP-Makro.

### <a name="end_param_map"></a><a name="end_param_map"></a>END_PARAM_MAP

Markiert das Ende der Parameterzuordnungseinträge.

#### <a name="syntax"></a>Syntax

```cpp
END_PARAM_MAP()
```

#### <a name="example"></a>Beispiel

Siehe Beispiel für [BEGIN_PARAM_MAP](../../data/oledb/begin-param-map.md) das BEGIN_PARAM_MAP-Makro.

### <a name="set_param_type"></a><a name="set_param_type"></a>SET_PARAM_TYPE

Gibt COLUMN_ENTRY Makros an, die der SET_PARAM_TYPE Makroeingabe, -ausgabe oder -ausgabe folgen.

#### <a name="syntax"></a>Syntax

```cpp
SET_PARAM_TYPE(type)
```

#### <a name="parameters"></a>Parameter

*type*<br/>
[in] Der für den Parameter festzulegende Typ.

#### <a name="remarks"></a>Bemerkungen

Anbieter unterstützen nur Parametereingabe-/-ausgabetypen, die von der zugrunde liegenden Datenquelle unterstützt werden. Der Typ ist eine Kombination `DBPARAMIO` aus einem oder mehreren Werten (siehe [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)) in der *Ole DB Programmer-Referenz):*

- `DBPARAMIO_NOTPARAM`Der Accessor hat keine Parameter. In der `eParamIO` Regel legen Sie diesen Wert in Zeilenaccessoren fest, um den Benutzer daran zu erinnern, dass Parameter ignoriert werden.

- `DBPARAMIO_INPUT`Ein Eingabeparameter.

- `DBPARAMIO_OUTPUT`Ein Ausgabeparameter.

- `DBPARAMIO_INPUT | DBPARAMIO_OUTPUT`Der Parameter ist sowohl ein Eingabe- als auch ein Ausgabeparameter.

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

## <a name="requirements"></a>Anforderungen

**Header:** atldbcli.h

## <a name="see-also"></a>Siehe auch

[Makros und globale Funktionen für OLE DB-Consumervorlagen](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)<br/>
[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ole DB Consumer Templates Referenz](../../data/oledb/ole-db-consumer-templates-reference.md)
