---
title: CDaoFieldInfo-Struktur
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldInfo
helpviewer_keywords:
- DAO (Data Access Objects), Fields collection
- CDaoFieldInfo structure [MFC]
ms.assetid: 91b13e3f-bdb8-440c-86fc-ba4181ea0182
ms.openlocfilehash: 9466386fefc6e5ab8fcf89bf497c1d5219e3e807
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368408"
---
# <a name="cdaofieldinfo-structure"></a>CDaoFieldInfo-Struktur

Die `CDaoFieldInfo` Struktur enthält Informationen zu einem Feldobjekt, das für Datenzugriffsobjekte (DAO) definiert ist.

DAO wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet.

## <a name="syntax"></a>Syntax

```
struct CDaoFieldInfo
{
    CString m_strName;           // Primary
    short m_nType;               // Primary
    long m_lSize;                // Primary
    long m_lAttributes;          // Primary
    short m_nOrdinalPosition;    // Secondary
    BOOL m_bRequired;            // Secondary
    BOOL m_bAllowZeroLength;     // Secondary
    long m_lCollatingOrder;      // Secondary
    CString m_strForeignName;    // Secondary
    CString m_strSourceField;    // Secondary
    CString m_strSourceTable;    // Secondary
    CString m_strValidationRule; // All
    CString m_strValidationText; // All
    CString m_strDefaultValue;   // All
};
```

#### <a name="parameters"></a>Parameter

*m_strName*<br/>
Benennt das Feldobjekt eindeutig. Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

*m_nType*<br/>
Ein Wert, der den Datentyp des Felds angibt. Weitere Informationen finden Sie im Thema "Typeigenschaft" in der DAO-Hilfe. Der Wert dieser Eigenschaft kann einer der folgenden sein:

- `dbBoolean`Ja/Nein, wie TRUE/FALSE

- `dbByte`Byte

- `dbInteger`kurz

- `dbLong`Lange

- `dbCurrency`Währung; siehe MFC-Klasse [COleCurrency](../../mfc/reference/colecurrency-class.md)

- `dbSingle`Einzelnen

- `dbDouble`Doppel

- `dbDate`Datum/Uhrzeit; siehe [MFC-Klasse COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)

- `dbText`Text; siehe MFC-Klasse [CString](../../atl-mfc-shared/reference/cstringt-class.md)

- `dbLongBinary`Lange Binärdatei (OLE-Objekt); Sie sollten die MFC-Klasse [CByteArray](../../mfc/reference/cbytearray-class.md) anstelle der Klasse `CLongBinary` verwenden, da `CByteArray` sie umfangreicher und einfacher zu verwenden ist.

- `dbMemo`Memo; siehe MFC-Klasse`CString`

- `dbGUID`Ein Globally Unique Identifier/Universally Unique Identifier, der bei Remoteprozeduraufrufen verwendet wird. Weitere Informationen finden Sie im Thema "Typeigenschaft" in der DAO-Hilfe.

> [!NOTE]
> Verwenden Sie keine Zeichenfolgendatentypen für Binärdaten. Dies führt dazu, dass Ihre Daten die Unicode/ANSI-Übersetzungsschicht durchlaufen, was zu einem erhöhten Overhead und möglicherweise unerwarteten Übersetzungen führt.

*m_lSize*<br/>
Ein Wert, der die maximale Größe eines DAO-Feldobjekts in Bytes in Bytes angibt, das Text enthält, oder die feste Größe eines Feldobjekts, das Text oder numerische Werte enthält. Weitere Informationen finden Sie im Thema "Size Property" in der DAO-Hilfe. Größen können einer der folgenden Werte sein:

|type|Größe (Byte)|BESCHREIBUNG|
|----------|--------------------|-----------------|
|`dbBoolean`|1 Byte|Ja/Nein (wie True/False)|
|`dbByte`|1|Byte|
|`dbInteger`|2|Integer|
|`dbLong`|4|Long|
|`dbCurrency`|8|Währung ([COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|Single|
|`dbDouble`|8|Double|
|`dbDate`|8|Datum/Uhrzeit ([COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (OLE-Objekt; [CByteArray](../../mfc/reference/cbytearray-class.md); Verwendung statt `CLongBinary`)|
|`dbMemo`|0|Memo ([CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbGUID`|16|Ein Globally Unique Identifier/Universally Unique Identifier, der bei Remoteprozeduraufrufen verwendet wird.|

*m_lAttributes*<br/>
Gibt die Merkmale eines Feldobjekts an, das von einem tabledef-, Recordset-, querydef- oder Indexobjekt enthalten ist. Der zurückgegebene Wert kann eine Summe dieser Konstanten sein, die mit dem C++bitwise-OR (**&#124;**)-Operator erstellt wurde:

- `dbFixedField`Die Feldgröße ist festgelegt (Standard für numerische Felder).

- `dbVariableField`Die Feldgröße ist variabel (nur Textfelder).

- `dbAutoIncrField`Der Feldwert für neue Datensätze wird automatisch in eine eindeutige lange ganze Zahl erhöht, die nicht geändert werden kann. Nur für Microsoft Jet-Datenbanktabellen unterstützt.

- `dbUpdatableField`Der Feldwert kann geändert werden.

- `dbDescending`Das Feld wird in absteigender Reihenfolge (Z - A oder 100 - 0) sortiert (gilt nur für ein Feldobjekt in einer Fields-Auflistung eines Indexobjekts; in MFC sind Indexobjekte selbst in tabledef-Objekten enthalten). Wenn Sie diese Konstante weglassen, wird das Feld in aufsteigender (A - Z oder 0 - 100) Reihenfolge (Standard) sortiert.

Wenn Sie die Einstellung dieser Eigenschaft überprüfen, können Sie den**&** C++-Bitweise-AND-Operator ( ) verwenden, um ein bestimmtes Attribut zu testen. Wenn Sie mehrere Attribute festlegen, können Sie diese kombinieren, indem Sie die entsprechenden Konstanten mit dem Operator bitwise-OR (**&#124;**) kombinieren. Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

*m_nOrdinalPosition*<br/>
Ein Wert, der die numerische Reihenfolge angibt, in der ein Feld durch ein DAO-Feldobjekt relativ zu anderen Feldern dargestellt werden soll. Sie können diese Eigenschaft mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen. Weitere Informationen finden Sie im Thema "OrdinalPosition-Eigenschaft" in der DAO-Hilfe.

*m_bRequired*<br/>
Gibt an, ob ein DAO-Feldobjekt einen Wert ungleich Null erfordert. Wenn diese Eigenschaft TRUE ist, lässt das Feld keinen Nullwert zu. Wenn Required auf FALSE festgelegt ist, kann das Feld Nullwerte sowie Werte enthalten, die die in den Eigenschafteneinstellungen allowZeroLength und ValidationRule angegebenen Bedingungen erfüllen. Weitere Informationen finden Sie im Thema "Erforderliche Eigenschaft" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

*m_bAllowZeroLength*<br/>
Gibt an, ob eine leere Zeichenfolge ("") ein gültiger Wert eines DAO-Feldobjekts mit einem Text- oder Memo-Datentyp ist. Wenn diese Eigenschaft TRUE ist, ist eine leere Zeichenfolge ein gültiger Wert. Sie können diese Eigenschaft auf FALSE festlegen, um sicherzustellen, dass Sie keine leere Zeichenfolge verwenden können, um den Wert eines Felds festzulegen. Weitere Informationen finden Sie im Thema "AllowZeroLength-Eigenschaft" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

*m_lCollatingOrder*<br/>
Gibt die Reihenfolge der Sortierreihenfolge im Text für den Stringvergleich oder die Sortierung an. Weitere Informationen finden Sie im Thema "Anpassen von Windows-Registrierungseinstellungen für den Datenzugriff" in der DAO-Hilfe. Eine Liste der zurückgegebenen möglichen `m_lCollatingOrder` Werte finden Sie im Member der [CDaoDatabaseInfo-Struktur.](../../mfc/reference/cdaodatabaseinfo-structure.md) Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

*m_strForeignName*<br/>
Ein Wert, der in einer Beziehung den Namen des DAO-Feldobjekts in einer fremden Tabelle angibt, das einem Feld in einer Primärtabelle entspricht. Weitere Informationen finden Sie im Thema "ForeignName-Eigenschaft" in der DAO-Hilfe.

*m_strSourceField*<br/>
Gibt den Namen des Felds an, das die ursprüngliche Quelle der Daten für ein DAO-Feldobjekt ist, das von einem tabledef-, Recordset- oder querydef-Objekt enthalten ist. Diese Eigenschaft gibt den ursprünglichen Feldnamen an, der einem Feldobjekt zugeordnet ist. Sie können diese Eigenschaft beispielsweise verwenden, um die ursprüngliche Quelle der Daten in einem Abfragefeld zu bestimmen, dessen Name nicht mit dem Namen des Felds in der zugrunde liegenden Tabelle verknüpft ist. Weitere Informationen finden Sie im Thema "SourceField, SourceTable Properties" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

*m_strSourceTable*<br/>
Gibt den Namen der Tabelle an, die die ursprüngliche Quelle der Daten für ein DAO-Feldobjekt ist, das von einem tabledef-, Recordset- oder querydef-Objekt enthalten ist. Diese Eigenschaft gibt den ursprünglichen Tabellennamen an, der einem Feldobjekt zugeordnet ist. Sie können diese Eigenschaft beispielsweise verwenden, um die ursprüngliche Quelle der Daten in einem Abfragefeld zu bestimmen, dessen Name nicht mit dem Namen des Felds in der zugrunde liegenden Tabelle verknüpft ist. Weitere Informationen finden Sie im Thema "SourceField, SourceTable Properties" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

*m_strValidationRule*<br/>
Ein Wert, der die Daten in einem Feld überprüft, wenn sie geändert oder einer Tabelle hinzugefügt werden. Weitere Informationen finden Sie im Thema "ValidationRule-Eigenschaft" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

Weitere Informationen zu tabledefs `m_strValidationRule` finden Sie im Member der [CDaoTableDefInfo-Struktur.](../../mfc/reference/cdaotabledefinfo-structure.md)

*m_strValidationText*<br/>
Ein Wert, der den Text der Nachricht angibt, die ihre Anwendung anzeigt, wenn der Wert eines DAO-Feldobjekts nicht der Validierungsregel entspricht, die durch die Propertyeinstellung ValidationRule angegeben wird. Weitere Informationen finden Sie im Thema "ValidationText-Eigenschaft" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

*m_strDefaultValue*<br/>
Der Standardwert eines DAO-Feldobjekts. Wenn ein neuer Datensatz erstellt wird, wird die DefaultValue-Eigenschaftseinstellung automatisch als Wert für das Feld eingegeben. Weitere Informationen finden Sie im Thema "DefaultValue-Eigenschaft" in der DAO-Hilfe. Sie können diese Eigenschaft für eine tabledef mit [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield)festlegen.

## <a name="remarks"></a>Bemerkungen

Die Verweise auf Primary, Secondary und All oben geben `GetFieldInfo` an, wie die Informationen von der Memberfunktion in den Klassen [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md#getfieldinfo), [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)und [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)zurückgegeben werden.

Feldobjekte werden nicht durch eine MFC-Klasse dargestellt. Stattdessen enthalten die DAO-Objekte, die MFC-Objekten der folgenden Klassen zugrunde liegen, Auflistungen von Feldobjekten: [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md), [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)und [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md). Diese Klassen stellen Memberfunktionen bereit, um auf einzelne Elemente von Feldinformationen `CDaoFieldInfo` zuzugreifen, `GetFieldInfo` oder Sie können alle auf einmal mit einem Objekt zugreifen, indem Sie die Memberfunktion des enthaltenden Objekts aufrufen.

Neben der Verwendung zum Untersuchen von `CDaoFieldInfo` Objekteigenschaften können Sie auch einen Eingabeparameter zum Erstellen neuer Felder in einer tabledef erstellen. Für diese Aufgabe stehen einfachere Optionen zur Verfügung, aber wenn Sie eine feinere Steuerung wünschen, `CDaoFieldInfo` können Sie die Version von [CDaoTableDef::CreateField](../../mfc/reference/cdaotabledef-class.md#createfield) verwenden, die einen Parameter annimmt.

Informationen, die `GetFieldInfo` von der Memberfunktion (der Klasse, die `CDaoFieldInfo` das Feld enthält) abgerufen werden, werden in einer Struktur gespeichert. Rufen `GetFieldInfo` Sie die Memberfunktion des enthaltenden Objekts auf, in dessen Fields-Auflistung das Feldobjekt gespeichert ist. `CDaoFieldInfo`definiert auch `Dump` eine Memberfunktion in Debugbuilds. Sie können `Dump` den Inhalt eines `CDaoFieldInfo` Objekts absetzen.

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="see-also"></a>Siehe auch

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoTableDef::GetFieldInfo](../../mfc/reference/cdaotabledef-class.md#getfieldinfo)<br/>
[CDaoRecordset::GetFieldInfo](../../mfc/reference/cdaorecordset-class.md#getfieldinfo)<br/>
[CDaoQueryDef::GetFieldInfo](../../mfc/reference/cdaoquerydef-class.md#getfieldinfo)
