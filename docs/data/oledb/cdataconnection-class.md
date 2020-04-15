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
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368618"
---
# <a name="cdataconnection-class"></a>CDataConnection-Klasse

Verwaltet die Verbindung mit der Datenquelle.

## <a name="syntax"></a>Syntax

```cpp
class CDataConnection
```

## <a name="requirements"></a>Anforderungen

**Header:** atldbcli.h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[CDataConnection](#cdataconnection)|Konstruktor. Instanziiert und initialisiert `CDataConnection` ein Objekt.|
|[Kopieren](#copy)|Erstellt eine Kopie einer vorhandenen Datenverbindung.|
|[Öffnen](#open)|Öffnet eine Verbindung zu einer Datenquelle mithilfe einer Initialisierungszeichenfolge.|
|[OpenNewSession](#opennewsession)|Öffnet eine neue Sitzung für die aktuelle Verbindung.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Betreiber BOOL](#op_bool)|Bestimmt, ob die aktuelle Sitzung geöffnet ist oder nicht.|
|[Operator bool](#op_bool_ole)|Bestimmt, ob die aktuelle Sitzung geöffnet ist oder nicht.|
|[Operator CDataSource&](#op_cdata_amp)|Gibt einen Verweis `CDataSource` auf das enthaltene Objekt zurück.|
|[Operator CDataSource*](#op_cdata_star)|Gibt einen Zeiger auf `CDataSource` das enthaltene Objekt zurück.|
|[Operator CSession&](#op_csession_amp)|Gibt einen Verweis `CSession` auf das enthaltene Objekt zurück.|
|[Operator-CSession*](#op_csession_star)|Gibt einen Zeiger auf `CSession` das enthaltene Objekt zurück.|

## <a name="remarks"></a>Bemerkungen

`CDataConnection`Ist eine nützliche Klasse zum Erstellen von Clients, da sie die erforderlichen Objekte (Datenquelle und Sitzung) und einige der Arbeit kapselt, die Sie beim Herstellen einer Verbindung mit einer Datenquelle leisten müssen

Ohne `CDataConnection`müssen Sie ein `CDataSource` Objekt erstellen, die [OpenFromInitializationString-Methode](../../data/oledb/cdatasource-openfrominitializationstring.md) aufrufen, dann eine Instanz eines [CSession-Objekts](../../data/oledb/csession-class.md) erstellen, `Open`die [Open-Methode](../../data/oledb/csession-open.md) aufrufen, dann ein [CCommand-Objekt](../../data/oledb/ccommand-class.md) erstellen und seine * Methoden aufrufen.

Mit `CDataConnection`müssen Sie nur ein Verbindungsobjekt erstellen, es eine Initialisierungszeichenfolge übergeben und dann diese Verbindung verwenden, um Befehle zu öffnen. Wenn Sie ihre Verbindung mit der Datenbank wiederholt verwenden möchten, ist es `CDataConnection` eine gute Idee, die Verbindung offen zu halten, und bietet eine bequeme Möglichkeit, dies zu tun.

> [!NOTE]
> Wenn Sie eine Datenbankanwendung erstellen, die mehrere Sitzungen verarbeiten muss, müssen Sie [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)verwenden.

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection::CDataConnection

Instanziiert und initialisiert `CDataConnection` ein Objekt.

### <a name="syntax"></a>Syntax

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parameter

*Ds*<br/>
[in] Ein Verweis auf eine vorhandene Datenverbindung.

### <a name="remarks"></a>Bemerkungen

Die erste Außerkraftsetzung `CDataConnection` erstellt ein neues Objekt mit Standardeinstellungen.

Die zweite Außerkraftsetzung `CDataConnection` erstellt ein neues Objekt mit Einstellungen, die dem von Ihnen angegebenen Datenverbindungsobjekt entsprechen.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection::Kopieren

Erstellt eine Kopie einer vorhandenen Datenverbindung.

### <a name="syntax"></a>Syntax

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parameter

*Ds*<br/>
[in] Ein Verweis auf eine vorhandene Datenverbindung, die kopiert werden soll.

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection::Öffnen

Öffnet eine Verbindung zu einer Datenquelle mithilfe einer Initialisierungszeichenfolge.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parameter

*szInitString*<br/>
[in] Die Initialisierungszeichenfolge für die Datenquelle.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection::OpenNewSession

Öffnet eine neue Sitzung mit der Datenquelle des aktuellen Verbindungsobjekts.

### <a name="syntax"></a>Syntax

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parameter

*session*<br/>
[Ein/Aus] Ein Verweis auf das neue Sitzungsobjekt.

### <a name="remarks"></a>Bemerkungen

Die neue Sitzung verwendet das enthaltene Datenquellenobjekt des aktuellen Verbindungsobjekts als übergeordnetes Objekt und kann auf dieselben Informationen wie die Datenquelle zugreifen.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection::operator BOOL

Bestimmt, ob die aktuelle Sitzung geöffnet ist oder nicht.

### <a name="syntax"></a>Syntax

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt **den WERT BOOL** (MFC typedef) zurück. **TRUE** bedeutet, dass die aktuelle Sitzung geöffnet ist. **FALSE** bedeutet, dass die aktuelle Sitzung geschlossen ist.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection::operator bool (OLE DB)

Bestimmt, ob die aktuelle Sitzung geöffnet ist oder nicht.

### <a name="syntax"></a>Syntax

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen **bool-Wert** (C++-Datentyp) zurück. **true** bedeutet, dass die aktuelle Sitzung geöffnet ist; **false** bedeutet, dass die aktuelle Sitzung geschlossen wird.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection::operator CDataSource&amp;

Gibt einen Verweis `CDataSource` auf das enthaltene Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen `CDataSource` Verweis auf das enthaltene Objekt zurück, sodass Sie ein `CDataConnection` Objekt übergeben können, für das ein `CDataSource` Verweis erwartet wird.

### <a name="example"></a>Beispiel

Wenn Sie über eine `func` Funktion (z. `CDataSource` B. unten) verfügen, die einen Verweis verwendet, können `CDataSource&` Sie stattdessen ein `CDataConnection` Objekt übergeben.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection::operator CDataSource*

Gibt einen Zeiger auf `CDataSource` das enthaltene Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Zeiger `CDataSource` auf das enthaltene `CDataConnection` Objekt `CDataSource` zurück, sodass Sie ein Objekt übergeben können, bei dem ein Zeiger erwartet wird.

Ein Verwendungsbeispiel finden Sie unter [Operator CDataSource&.](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection::operator CSession&amp;

Gibt einen Verweis `CSession` auf das enthaltene Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen `CSession` Verweis auf das enthaltene Objekt zurück, sodass Sie ein `CDataConnection` Objekt übergeben können, für das ein `CSession` Verweis erwartet wird.

### <a name="example"></a>Beispiel

Wenn Sie über eine `func` Funktion (z. `CSession` B. unten) verfügen, die einen Verweis verwendet, können `CSession&` Sie stattdessen ein `CDataConnection` Objekt übergeben.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection::operator CSession*

Gibt einen Zeiger auf `CSession` das enthaltene Objekt zurück.

### <a name="syntax"></a>Syntax

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Bemerkungen

Dieser Operator gibt einen Zeiger `CSession` auf das enthaltene `CDataConnection` Objekt `CSession` zurück, sodass Sie ein Objekt übergeben können, bei dem ein Zeiger erwartet wird.

### <a name="example"></a>Beispiel

Ein Anwendungsbeispiel finden Sie unter [Operator CSession&.](../../data/oledb/cdataconnection-operator-csession-amp.md)

## <a name="see-also"></a>Siehe auch

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Ole DB Consumer Templates Referenz](../../data/oledb/ole-db-consumer-templates-reference.md)
