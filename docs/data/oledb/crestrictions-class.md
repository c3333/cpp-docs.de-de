---
title: CRestrictions-Klasse
ms.date: 11/04/2016
f1_keywords:
- ATL::CRestrictions
- CRestrictions
- ATL.CRestrictions
- CRestrictions.Open
- ATL::CRestrictions::Open
- ATL.CRestrictions.Open
- CRestrictions::Open
helpviewer_keywords:
- CRestrictions class
- Open method
ms.assetid: 0aaa2364-641c-4318-b110-7446aada4b4f
ms.openlocfilehash: a380f1ba00dcc444099f186071b7d55c9db71291
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88844963"
---
# <a name="crestrictions-class"></a>CRestrictions-Klasse

Eine generische Klasse, die Ihnen das Festlegen von Einschränkungen für Schemarowsets ermöglicht.

## <a name="syntax"></a>Syntax

```cpp
template <class T, short nRestrictions, const GUID* pguid>
class CRestrictions :
   public CSchemaRowset <T, nRestrictions>
```

### <a name="parameters"></a>Parameter

*T*<br/>
Die für den-Accessor verwendete-Klasse.

*neinschränkungen*<br/>
Die Anzahl der Einschränkungs Spalten für das Schemarowset.

*pguid*<br/>
Ein Zeiger auf die GUID für das Schema.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Atldbsch. h

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

| Name | Beschreibung |
|-|-|
|[Öffnen](#open)|Gibt ein Resultset gemäß den vom Benutzer bereitgestellten Einschränkungen zurück.|

## <a name="crestrictionsopen"></a><a name="open"></a> "Krestrictions:: Open"

Gibt ein Resultset gemäß den vom Benutzer bereitgestellten Einschränkungen zurück.

### <a name="syntax"></a>Syntax

```cpp
HRESULT Open(const CSession& session,
   LPCTSTR lpszParam 1 = NULL,
   LPCTSTR lpszParam 2 = NULL,
   LPCTSTR lpszParam 3 = NULL,
   LPCTSTR lpszParam 4 = NULL,
   LPCTSTR lpszParam 5 = NULL,
   LPCTSTR lpszParam 6 = NULL,
   LPCTSTR lpszParam 7 = NULL,
   bool bBind = true);
```

#### <a name="parameters"></a>Parameter

*Sitzung*<br/>
in Gibt ein vorhandenes Sitzungs Objekt an, mit dem eine Verbindung mit der Datenquelle hergestellt wird.

*lpszparam*<br/>
in Gibt die Einschränkungen für das Schemarowset an.

*bbind*<br/>
in Gibt an, ob die Spalten Zuordnung automatisch gebunden werden soll. Der Standardwert ist **`true`** . Dadurch wird die Spalten Zuordnung automatisch gebunden. Wenn Sie *bbind* auf festlegen, wird **`false`** die automatische Bindung der Spalten Zuordnung verhindert, sodass Sie die Bindung manuell vornehmen können. (Manuelle Bindung ist für OLAP-Benutzer besonders interessant.)

### <a name="return-value"></a>Rückgabewert

Einer der HRESULT-Standardwerte.

### <a name="remarks"></a>Bemerkungen

Für ein Schemarowset können maximal sieben Einschränkungen angegeben werden.

Informationen zu den definierten Einschränkungen der einzelnen [Schemarowsets finden Sie unter IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) .

## <a name="see-also"></a>Weitere Informationen

[OLE DB-Consumervorlagen](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referenz zu OLE DB Consumervorlagen](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Schemarowset-Klassen und typedef-Klassen](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)
