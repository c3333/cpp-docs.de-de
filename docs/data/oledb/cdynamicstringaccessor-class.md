---
title: CDynamicStringAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: 891c80a7c21fd046fba393b494ed6d84f731db6f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498670"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor-Klasse

Ermöglicht den Zugriff auf eine Datenquelle, wenn Sie das Datenbankschema (die zugrunde liegende Struktur der Datenbank) nicht kennen.

## <a name="syntax"></a>Syntax

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: atldbcli. h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[GetString](#getstring)|Ruft die angegebenen Spaltendaten als Zeichenfolge ab.|
|[SetString](#setstring)|Legt die angegebenen Spaltendaten als Zeichenfolge fest.|

## <a name="remarks"></a>Bemerkungen

Während [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) Daten im vom Anbieter gemeldeten systemeigenen Format anfordert, `CDynamicStringAccessor` fordert der Anbieter alle Daten, auf die aus dem Datenspeicher zugegriffen wird, als Zeichen folgen Daten an. Dies ist besonders nützlich für einfache Aufgaben, bei denen keine Berechnung von Werten im Datenspeicher erforderlich ist, z. b. das Anzeigen oder Drucken der Inhalte des Daten Stores.

Der systemeigene Typ der Spaltendaten im Datenspeicher spielt keine Rolle. solange der Anbieter die Datenkonvertierung unterstützen kann, werden die Daten im Zeichen folgen Format bereitgestellt. Wenn der Anbieter die Konvertierung des systemeigenen Datentyps in eine Zeichenfolge nicht unterstützt (was nicht häufig der Fall ist), gibt der anfordernde-Befehl den Success-Wert DB_S_ERRORSOCCURED zurück, und der Status der entsprechenden Spalte weist auf ein Konvertierungs Problem mit DBSTATUS_E_CANTCONVERTVALUE hin.

Verwenden `CDynamicStringAccessor` Sie Methoden zum Abrufen von Spalten Informationen. Mit diesen Spalten Informationen können Sie einen Accessor dynamisch zur Laufzeit erstellen.

Die Spalten Informationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Rufen Sie mithilfe von [GetString](#getstring)Daten aus dem Puffer ab, oder speichern Sie Sie mithilfe von [SetString](#setstring)im Puffer.

Eine Erläuterung und Beispiele für die Verwendung der dynamischen [Accessorklassen finden Sie unter Verwenden dynamischer Accessoren](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a> CDynamicStringAccessor:: GetString

Ruft die angegebenen Spaltendaten als Zeichenfolge ab.

### <a name="syntax"></a>Syntax

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der Wert 0 verweist ggf. auf die Lesezeichen Spalte.

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Zeichen folgen Wert, der aus der angegebenen Spalte abgerufen wird. Der Wert ist vom Typ `BaseType` . Dies ist abhängig davon, ob _UNICODE definiert ist, **char** oder **WCHAR** . Gibt NULL zurück, wenn die angegebene Spalte nicht gefunden wurde.

### <a name="remarks"></a>Bemerkungen

Das zweite Überschreibungs Formular nimmt den Spaltennamen als ANSI-Zeichenfolge an. Das dritte Überschreibungs Formular nimmt den Spaltennamen als Unicode-Zeichenfolge an.

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a> CDynamicStringAccessor:: SetString

Legt die angegebenen Spaltendaten als Zeichenfolge fest.

### <a name="syntax"></a>Syntax

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>Parameter

*ncolumn*<br/>
in Die Spaltennummer. Die Spalten Nummern beginnen mit 1. Der besondere Wert 0 bezieht sich auf die Lesezeichen Spalte, falls vorhanden.

*pcolumnname*<br/>
in Ein Zeiger auf eine Zeichenfolge, die den Spaltennamen enthält.

*data*<br/>
in Ein Zeiger auf die Zeichen folgen Daten, die in die angegebene Spalte geschrieben werden sollen.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Zeichen folgen Wert, auf den die angegebene Spalte festgelegt werden soll. Der Wert ist vom Typ `BaseType` . Dies ist abhängig davon, ob _UNICODE definiert ist, **char** oder **WCHAR** .

### <a name="remarks"></a>Bemerkungen

Das zweite Überschreibungs Formular übernimmt den Spaltennamen als ANSI-Zeichenfolge, und das dritte Überschreibungs Formular nimmt den Spaltennamen als Unicode-Zeichenfolge an.

Wenn _SECURE_ATL für einen Wert ungleich 0 (null) definiert ist, wird ein Lauf zeitassertionsfehler generiert, wenn die Eingabe *Daten* Zeichenfolge länger als die maximal zulässige Länge der Datenspalte ist, auf die verwiesen wird. Andernfalls wird die Eingabe Zeichenfolge abgeschnitten, wenn Sie länger als die maximal zulässige Länge ist.

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor-Klasse](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor-Klasse](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor-Klasse](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor-Klasse](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA-Klasse](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW-Klasse](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor-Klasse](../../data/oledb/cxmlaccessor-class.md)
