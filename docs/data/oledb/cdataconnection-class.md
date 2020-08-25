---
title: CDataConnection-Klasse
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: 118b8d09b90899eca0f257e319aabbefd92f359f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838399"
---
# <a name="cdataconnection-class"></a>CDataConnection-Klasse

Verwaltet die Verbindung mit der Datenquelle.

## <a name="syntax"></a>Syntax

```cpp
class CDataConnection
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[CDataConnection](#cdataconnection)|Konstruktor. Instanziiert und initialisiert ein- `CDataConnection` Objekt.|
|[Kopieren](#copy)|Erstellt eine Kopie einer vorhandenen Datenverbindung.|
|[Öffnen](#open)|Öffnet eine Verbindung mit einer Datenquelle mithilfe einer Initialisierungs Zeichenfolge.|
|[OpenNewSession](#opennewsession)|Öffnet eine neue Sitzung für die aktuelle Verbindung.|

### <a name="operators"></a>Operatoren

| Name | Beschreibung |
|-|-|
|[Operator bool](#op_bool)|Bestimmt, ob die aktuelle Sitzung geöffnet ist.|
|[Operator bool](#op_bool_ole)|Bestimmt, ob die aktuelle Sitzung geöffnet ist.|
|[CDataSource-Operator&](#op_cdata_amp)|Gibt einen Verweis auf das enthaltene- `CDataSource` Objekt zurück.|
|[Operator CDataSource *](#op_cdata_star)|Gibt einen Zeiger auf das enthaltene- `CDataSource` Objekt zurück.|
|[Operator CSession-&](#op_csession_amp)|Gibt einen Verweis auf das enthaltene- `CSession` Objekt zurück.|
|[Operator-CSession*](#op_csession_star)|Gibt einen Zeiger auf das enthaltene- `CSession` Objekt zurück.|

## <a name="remarks"></a>Bemerkungen

`CDataConnection` ist eine nützliche Klasse zum Erstellen von Clients, da Sie erforderliche Objekte (Datenquelle und Sitzung) und einige der Aufgaben kapselt, die Sie beim Herstellen einer Verbindung mit einer Datenquelle ausführen müssen.

Ohne `CDataConnection` müssen Sie ein-Objekt erstellen `CDataSource` , seine [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) -Methode aufzurufen, dann eine Instanz eines [CSession](../../data/oledb/csession-class.md) -Objekts erstellen, seine [Open](../../data/oledb/csession-open.md) -Methode aufzurufen und dann ein [CCommand](../../data/oledb/ccommand-class.md) -Objekt erstellen und seine *-Methoden aufzurufen `Open` .

Mit `CDataConnection` müssen Sie nur ein Verbindungs Objekt erstellen, ihm eine Initialisierungs Zeichenfolge übergeben und dann diese Verbindung zum Öffnen der Befehle verwenden. Wenn Sie die Verbindung mit der Datenbank wiederholt verwenden möchten, empfiehlt es sich, die Verbindung offen zu halten, und `CDataConnection` bietet eine bequeme Möglichkeit, dies zu erreichen.

> [!NOTE]
> Wenn Sie eine Datenbankanwendung erstellen, die mehrere Sitzungen verarbeiten muss, müssen Sie [opennewsession](../../data/oledb/cdataconnection-opennewsession.md)verwenden.

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a> Cdataconnetction:: cdataconnetction

Instanziiert und initialisiert ein- `CDataConnection` Objekt.

### <a name="syntax"></a>Syntax

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parameter

*DS*<br/>
in Ein Verweis auf eine vorhandene Datenverbindung.

### <a name="remarks"></a>Bemerkungen

Beim ersten überschreiben wird ein neues- `CDataConnection` Objekt mit Standardeinstellungen erstellt.

Die zweite außer Kraft Setzung erstellt ein neues- `CDataConnection` Objekt mit Einstellungen, die dem von Ihnen angegebenen Daten Verbindungs Objekt entsprechen.

## <a name="cdataconnectioncopy"></a><a name="copy"></a> Cdataconnetction:: Copy

Erstellt eine Kopie einer vorhandenen Datenverbindung.

### <a name="syntax"></a>Syntax

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parameter

*DS*<br/>
in Ein Verweis auf eine vorhandene Datenverbindung, die kopiert werden soll.

## <a name="cdataconnectionopen"></a><a name="open"></a> Cdataconnetction:: Open

Öffnet eine Verbindung mit einer Datenquelle mithilfe einer Initialisierungs Zeichenfolge.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parameter

*szinitstring*<br/>
in Die Initialisierungs Zeichenfolge für die Datenquelle.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a> Cdataconnetction:: opennewsession

Öffnet eine neue Sitzung mithilfe der Datenquelle des aktuellen Verbindungs Objekts.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parameter

*Sitzung*<br/>
[in/out] Ein Verweis auf das neue Session-Objekt.

### <a name="remarks"></a>Bemerkungen

Die neue Sitzung verwendet das enthaltene Datenquellen Objekt des aktuellen Verbindungs Objekts als übergeordnetes Element und kann auf alle Informationen zugreifen, die von der Datenquelle verwendet werden.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standard.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a> Cdataconnetction:: Operator bool

Bestimmt, ob die aktuelle Sitzung geöffnet ist.

### <a name="syntax"></a>Syntax

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen **booleschen** Wert (MFC-typedef) zurück. " **True** " bedeutet, dass die aktuelle Sitzung geöffnet ist. **False** bedeutet, dass die aktuelle Sitzung geschlossen wird.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a> Cdataconnetction:: Operator bool (OLE DB)

Bestimmt, ob die aktuelle Sitzung geöffnet ist.

### <a name="syntax"></a>Syntax

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen- **`bool`** Wert (C++ Data Type) zurück. **`true`** bedeutet, dass die aktuelle Sitzung geöffnet ist. **`false`** bedeutet, dass die aktuelle Sitzung geschlossen wird.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a> Cdataconnetction:: Operator CDataSource&amp;

Gibt einen Verweis auf das enthaltene- `CDataSource` Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Verweis auf das enthaltene `CDataSource` Objekt zurück, sodass Sie ein-Objekt übergeben können, `CDataConnection` in dem ein `CDataSource` Verweis erwartet wird.

### <a name="example"></a>Beispiel

Wenn Sie über eine Funktion verfügen (z. b. `func` unten), die einen `CDataSource` Verweis annimmt, können Sie stattdessen verwenden, `CDataSource&` um ein-Objekt zu übergeben `CDataConnection` .

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a> Cdataconnetction:: Operator CDataSource *

Gibt einen Zeiger auf das enthaltene- `CDataSource` Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Zeiger auf das enthaltene `CDataSource` Objekt zurück, sodass Sie ein-Objekt übergeben können, `CDataConnection` in dem ein `CDataSource` Zeiger erwartet wird.

Ein Verwendungs Beispiel finden Sie unter [Operator CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) .

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a> Cdataconnetction:: Operator CSession&amp;

Gibt einen Verweis auf das enthaltene- `CSession` Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Verweis auf das enthaltene `CSession` Objekt zurück, sodass Sie ein-Objekt übergeben können, `CDataConnection` in dem ein `CSession` Verweis erwartet wird.

### <a name="example"></a>Beispiel

Wenn Sie über eine Funktion verfügen (z. b. `func` unten), die einen `CSession` Verweis annimmt, können Sie stattdessen verwenden, `CSession&` um ein-Objekt zu übergeben `CDataConnection` .

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a> Cdataconnetction:: Operator CSession *

Gibt einen Zeiger auf das enthaltene- `CSession` Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Zeiger auf das enthaltene `CSession` Objekt zurück, sodass Sie ein-Objekt übergeben können, `CDataConnection` in dem ein `CSession` Zeiger erwartet wird.

### <a name="example"></a>Beispiel

Ein Verwendungs Beispiel finden Sie unter [Operator CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md) .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)
