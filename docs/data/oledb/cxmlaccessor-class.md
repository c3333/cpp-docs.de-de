---
title: CXMLAccessor-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211041"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor-Klasse

Ermöglicht Ihnen den Zugriff auf Datenquellen als Zeichen folgen Daten, wenn Sie das Schema des Datenspeicher (zugrunde liegende Struktur) nicht kennen.

## <a name="syntax"></a>Syntax

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**: atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Methoden

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Ruft die Spalten Informationen ab.|
|[GetXMLRowData](#getxmlrowdata)|Ruft den gesamten Inhalt einer Tabelle nach Zeilen ab.|

## <a name="remarks"></a>Bemerkungen

`CXMLAccessor` unterscheidet sich jedoch von `CDynamicStringAccessorW` darin, dass alle Daten, auf die aus dem Datenspeicher zugegriffen wird, als XML-formatierte (markierte) Daten konvertiert werden. Dies ist besonders nützlich für die Ausgabe von XML-fähigen Webseiten. Die Namen der XML-Tags entsprechen den Spaltennamen des Daten Stores so nah wie möglich.

Verwenden Sie `CDynamicAccessor` Methoden, um Spalten Informationen zu erhalten. Mit diesen Spalten Informationen können Sie einen Accessor dynamisch zur Laufzeit erstellen.

Die Spalten Informationen werden in einem Puffer gespeichert, der von dieser Klasse erstellt und verwaltet wird. Abrufen von Spalten Informationen mithilfe von [GetXMLColumnData](#getxmlcolumndata) oder Abrufen von Spaltendaten nach Zeilen mithilfe von [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Beispiel

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor:: GetXMLColumnData

Ruft die Spaltentypen Informationen einer Tabelle als XML-formatierte Zeichen folgen Daten nach Spalte ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parameter

*stroutput*<br/>
vorgenommen Ein Verweis auf einen Zeichen folgen Puffer, der die abzurufenden Spaltentyp Informationen enthält. Die Zeichenfolge wird mit XML-Tagnamen formatiert, die den Spaltennamen des Daten Stores entsprechen.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Im folgenden wird gezeigt, wie die Spaltentypen Informationen in XML formatiert werden. `type` gibt den Datentyp der Spalte an. Beachten Sie, dass die Datentypen auf OLE DB Datentypen basieren, nicht auf der Datenbank, auf die zugegriffen wird.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor:: GetXMLRowData

Ruft den gesamten Inhalt einer Tabelle als XML-formatierte Zeichen folgen Daten nach Zeile ab.

### <a name="syntax"></a>Syntax

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parameter

*stroutput*<br/>
vorgenommen Ein Verweis auf einen Puffer, der die abzurufenden Tabellendaten enthält. Die Daten werden als Zeichen folgen Daten mit XML-Tagnamen formatiert, die den Spaltennamen des Daten Stores entsprechen.

*bappend*<br/>
in Ein boolescher Wert, der angibt, ob am Ende der Ausgabedaten eine Zeichenfolge angefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Im folgenden wird gezeigt, wie die Zeilendaten in XML formatiert werden. `DATA` unten sind die Zeilendaten dargestellt. Verwenden Sie Move-Methoden, um zur gewünschten Zeile zu wechseln.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz der OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor-Klasse](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor-Klasse](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor-Klasse](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor-Klasse](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA-Klasse](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW-Klasse](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor-Klasse](../../data/oledb/cmanualaccessor-class.md)
