---
title: CLongBinary-Klasse
ms.date: 11/04/2016
f1_keywords:
- CLongBinary
- AFXDB_/CLongBinary
- AFXDB_/CLongBinary::CLongBinary
- AFXDB_/CLongBinary::m_dwDataLength
- AFXDB_/CLongBinary::m_hData
helpviewer_keywords:
- CLongBinary class [MFC]
ms.assetid: f4320059-aeb4-4ee5-bc2b-25f19d898ef5
ms.openlocfilehash: 1ce1daba90f3a1dad4b9627082d63f1b3405eab4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370137"
---
# <a name="clongbinary-class"></a>CLongBinary-Klasse

Vereinfacht die Verwendung sehr großen Binärdatenobjekte (oft "BLOBs" oder "Binary Large Objects" genannt) in einer Datenbank.

## <a name="syntax"></a>Syntax

```
class CLongBinary : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CLongBinary::CLongBinary](#clongbinary)|Erstellt ein `CLongBinary`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CLongBinary::m_dwDataLength](#m_dwdatalength)|Enthält die tatsächliche Größe in Bytes des Datenobjekts, dessen Handle in `m_hData`gespeichert ist.|
|[CLongBinary::m_hData](#m_hdata)|Enthält ein Windows HGLOBAL-Handle für das eigentliche Bildobjekt.|

## <a name="remarks"></a>Bemerkungen

Beispielsweise kann ein Datensatzfeld in einer SQL-Tabelle eine Bitmap enthalten, die ein Bild darstellt. Ein `CLongBinary` Objekt speichert ein solches Objekt und verfolgt seine Größe.

> [!NOTE]
> Im Allgemeinen ist es jetzt besser, [CByteArray](../../mfc/reference/cbytearray-class.md) in Verbindung mit der [DFX_Binary-Funktion](record-field-exchange-functions.md#dfx_binary) zu verwenden. Sie können `CLongBinary`immer noch `CByteArray` verwenden, bieten aber im Allgemeinen mehr Funktionalität unter Win32, `CByteArray`da es nicht mehr die Größenbeschränkung gibt, die mit 16-Bit auftritt. Diese Empfehlung gilt für die Programmierung mit Data Access Objects (DAO) sowie Open Database Connectivity (ODBC).

Um ein `CLongBinary` Objekt zu verwenden, deklarieren Sie einen Felddatenmember des Typs `CLongBinary` in Ihrer Recordset-Klasse. Dieser Member ist ein eingebetteter Member der Recordset-Klasse und wird beim Aufbau des Recordsets erstellt. Nachdem `CLongBinary` das Objekt erstellt wurde, lädt der RFX-Mechanismus (Datensatzfeldaustausch) das Datenobjekt aus einem Feld im aktuellen Datensatz in der Datenquelle und speichert es beim Aktualisieren des Datensatzes wieder im Datensatz. RFX fragt die Datenquelle nach der Größe des binären großen Objekts ab, reserviert Speicher dafür (über `CLongBinary` das Datenelement des Objekts) `m_hData` und speichert ein `HGLOBAL` Handle für die Daten in `m_hData`. RFX speichert auch die tatsächliche Größe `m_dwDataLength` des Datenobjekts im Datenelement. Arbeiten Sie mit den `m_hData`Daten im Objekt über mit den gleichen Techniken, `HGLOBAL` die Sie normalerweise verwenden würden, um die in einem Windows-Handle gespeicherten Daten zu bearbeiten.

Wenn Sie Ihr Recordset `CLongBinary` zerstören, wird das eingebettete Objekt ebenfalls `HGLOBAL` zerstört, und sein Destruktor weist das Datenhandle auf.

Weitere Informationen zu großen Objekten `CLongBinary`und der Verwendung von finden Sie in den Artikeln [Recordset (ODBC)](../../data/odbc/recordset-odbc.md) und [Recordset: Working with Large Data Items (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CLongBinary`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxdb_.h

## <a name="clongbinaryclongbinary"></a><a name="clongbinary"></a>CLongBinary::CLongBinary

Erstellt ein `CLongBinary`-Objekt.

```
CLongBinary();
```

## <a name="clongbinarym_dwdatalength"></a><a name="m_dwdatalength"></a>CLongBinary::m_dwDataLength

Speichert die tatsächliche Größe der im HGLOBAL-Handle `m_hData`in gespeicherten Daten in Bytes.

```
SQLULEN m_dwDataLength;
```

### <a name="remarks"></a>Bemerkungen

Diese Größe kann kleiner sein als die Größe des Speicherblocks, der für die Daten reserviert ist. Rufen Sie die Win32 [GLobalSize-Funktion](/windows/win32/api/winbase/nf-winbase-globalsize) auf, um die zugewiesene Größe abzurufen.

## <a name="clongbinarym_hdata"></a><a name="m_hdata"></a>CLongBinary::m_hData

Speichert ein Windows HGLOBAL-Handle für die tatsächlichen binären großen Objektdaten.

```
HGLOBAL m_hData;
```

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)
