---
title: CDaoException-Klasse
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: fcbd88e8a9ef632b61096ac2577d7a1a7094d4b5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231844"
---
# <a name="cdaoexception-class"></a>CDaoException-Klasse

Stellt eine Ausnahmebedingung dar, die von MFC-Datenbankklassen in Bezug auf Datenzugriffsobjekte (DAOs) ausgelöst wird. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird.

## <a name="syntax"></a>Syntax

```
class CDaoException : public CException
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoException:: CDaoException](#cdaoexception)|Erstellt ein `CDaoException`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoException:: GetErrorCount](#geterrorcount)|Gibt die Anzahl der Fehler in der Fehlersammlung der Datenbank-Engine zurück.|
|[CDaoException:: GetErrorInfo](#geterrorinfo)|Gibt Fehlerinformationen zu einem bestimmten Fehler Objekt in der Fehler Auflistung zurück.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoException:: m_nAfxDaoError](#m_nafxdaoerror)|Enthält einen erweiterten Fehlercode für jeden Fehler in den MFC-DAO-Klassen.|
|[CDaoException:: m_pErrorInfo](#m_perrorinfo)|Ein Zeiger auf ein [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) -Objekt, das Informationen zu einem DAO-Fehler Objekt enthält.|
|[CDaoException:: m_scode](#m_scode)|Der [SCODE](#m_scode) -Wert, der dem Fehler zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Die-Klasse enthält öffentliche Datenmember, die Sie verwenden können, um die Ursache der Ausnahme zu bestimmen. `CDaoException`Objekte werden von den Element Funktionen der DAO-Datenbankklassen erstellt und ausgelöst.

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassen Namen haben das Präfix "CDAO". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Im Allgemeinen sind die MFC-Klassen, die auf DAO basieren, besser geeignet als die MFC-Klassen auf der Grundlage von ODBC. die DAO-basierten Klassen können über Ihre eigene Datenbank-Engine auf Daten zugreifen, auch über ODBC-Treiber. Die DAO-basierten Klassen unterstützen auch DDL-Vorgänge (Data Definition Language), wie z. b. das Hinzufügen von Tabellen über die Klassen, ohne DAO direkt aufrufen zu müssen. Informationen zu Ausnahmen, die von den ODBC-Klassen ausgelöst werden, finden Sie unter [CDBException](../../mfc/reference/cdbexception-class.md).

Sie können im Bereich eines [catch](../../mfc/reference/exception-processing.md#catch) -Ausdrucks auf Ausnahme Objekte zugreifen. Sie können auch `CDaoException` Objekte aus Ihrem eigenen Code mit der globalen [afxthrowdaoexception](../../mfc/reference/exception-processing.md#afxthrowdaoexception) -Funktion auslösen.

In MFC werden alle DAO-Fehler als Ausnahmen vom Typ ausgedrückt `CDaoException` . Wenn Sie eine Ausnahme dieses Typs abgefangen haben, können Sie mithilfe `CDaoException` von Element Funktionen Informationen aus den in der Fehlersammlung der Datenbank-Engine gespeicherten DAO-Fehler Objekten abrufen. Wenn jeder Fehler auftritt, werden mindestens ein Fehler Objekt in die Fehler Auflistung eingefügt. (Normalerweise enthält die Auflistung nur ein Fehler Objekt. Wenn Sie eine ODBC-Datenquelle verwenden, erhalten Sie wahrscheinlich mehrere Fehler Objekte.) Wenn ein anderer DAO-Vorgang einen Fehler generiert, wird die Fehler Auflistung gelöscht, und das neue Fehler Objekt wird in die Fehler Auflistung eingefügt. DAO-Vorgänge, für die kein Fehler generiert wird, haben keine Auswirkung auf die Fehler Auflistung.

Informationen zu DAO-Fehlercodes finden Sie in der Datei daoerr. Micha. Weitere Informationen finden Sie im Thema "Abfang Bare Datenzugriffs Fehler" in der DAO-Hilfe.

Weitere Informationen zur Ausnahmebehandlung im allgemeinen oder zu `CDaoException` Objekten finden Sie in den Artikeln [Ausnahmebehandlung (MFC)](../../mfc/exception-handling-in-mfc.md) und [Ausnahmen: Daten Bank Ausnahmen](../../mfc/exceptions-database-exceptions.md). Der zweite Artikel enthält Beispielcode, der die Ausnahmebehandlung in DAO veranschaulicht.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaoexceptioncdaoexception"></a><a name="cdaoexception"></a>CDaoException:: CDaoException

Erstellt ein `CDaoException`-Objekt.

```
CDaoException();
```

### <a name="remarks"></a>Bemerkungen

Normalerweise erstellt das Framework Ausnahme Objekte, wenn der Code eine Ausnahme auslöst. Sie müssen selten ein Ausnahme Objekt explizit erstellen. Wenn Sie einen `CDaoException` aus dem eigenen Code auslösen möchten, können Sie die globale Funktion [afxthrowdaoexception](../../mfc/reference/exception-processing.md#afxthrowdaoexception)aufzurufen.

Möglicherweise möchten Sie jedoch explizit ein Exception-Objekt erstellen, wenn Sie über die DAO-Schnittstellen Zeiger, die die MFC-Klassen Kapseln, direkte Aufrufe an DAO tätigen. In diesem Fall müssen Sie möglicherweise Fehlerinformationen von DAO abrufen. Angenommen, in DAO tritt ein Fehler auf, wenn Sie über die DAO-Datenbankschnittstelle eine DAO-Methode für die Datenbanksammlung eines Arbeitsbereichs aufzurufen.

##### <a name="to-retrieve-the-dao-error-information"></a>So rufen Sie die DAO-Fehlerinformationen ab

1. Konstruieren Sie ein `CDaoException`-Objekt.

1. Aufrufen der [GetErrorCount](#geterrorcount) -Member-Funktion des Exception-Objekts, um zu bestimmen, wie viele Fehler Objekte in der Fehlersammlung der Datenbank-Engine vorliegen. (Normalerweise nur eine, es sei denn, Sie verwenden eine ODBC-Datenquelle.)

1. Rufen Sie die [GetErrorInfo](#geterrorinfo) -Member-Funktion des Exception-Objekts auf, um jeweils ein bestimmtes Fehler Objekt nach Index in der Auflistung über das Exception-Objekt abzurufen. Betrachten Sie das Ausnahme Objekt als Proxy für ein DAO-Fehler Objekt.

1. Überprüfen Sie die aktuelle [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) -Struktur, die `GetErrorInfo` im [m_pErrorInfo](#m_perrorinfo) Datenmember zurückgibt. Seine Member stellen Informationen zum DAO-Fehler bereit.

1. Bei einer ODBC-Datenquelle wiederholen Sie bei Bedarf die Schritte 3 und 4, um weitere Fehler Objekte zu erhalten.

1. Wenn Sie das Ausnahme Objekt auf dem Heap erstellt haben, können Sie es mit dem Operator löschen, **`delete`** Wenn Sie fertig sind.

Weitere Informationen zur Behandlung von Fehlern in den MFC-DAO-Klassen finden Sie im Artikel [Ausnahmen: Daten Bank Ausnahmen](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptiongeterrorcount"></a><a name="geterrorcount"></a>CDaoException:: GetErrorCount

Rufen Sie diese Member-Funktion auf, um die Anzahl von DAO-Fehler Objekten in der Fehlersammlung der Datenbank-Engine abzurufen.

```
short GetErrorCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der DAO-Fehler Objekte in der Fehlersammlung der Datenbank-Engine.

### <a name="remarks"></a>Bemerkungen

Diese Informationen dienen zum Durchlaufen der Fehler Auflistung, um jedes der DAO-Fehler Objekte in der Auflistung abzurufen. Rufen Sie die [GetErrorInfo](#geterrorinfo) -Member-Funktion auf, um ein Fehler Objekt anhand des Indexes oder der DAO-Fehlernummer abzurufen.

> [!NOTE]
> Normalerweise ist nur ein Fehler Objekt in der Fehler Auflistung vorhanden. Wenn Sie jedoch mit einer ODBC-Datenquelle arbeiten, können mehrere vorhanden sein.

## <a name="cdaoexceptiongeterrorinfo"></a><a name="geterrorinfo"></a>CDaoException:: GetErrorInfo

Gibt Fehlerinformationen zu einem bestimmten Fehler Objekt in der Fehler Auflistung zurück.

```cpp
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index der Fehlerinformationen in der Fehlersammlung der Datenbank-Engine für die Suche nach Index.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Member-Funktion auf, um die folgenden Arten von Informationen über die Ausnahme abzurufen:

- Fehlercode

- `Source`

- BESCHREIBUNG

- Hilfedatei

- Hilfe Kontext

`GetErrorInfo`speichert die Informationen im Datenmember des Ausnahme Objekts `m_pErrorInfo` . Eine kurze Beschreibung der zurückgegebenen Informationen finden Sie unter [m_pErrorInfo](#m_perrorinfo). Wenn Sie eine Ausnahme vom Typ abfangen `CDaoException` , die von MFC ausgelöst wird, `m_pErrorInfo` wird der Member bereits ausgefüllt. Wenn Sie DAO direkt aufzurufen, müssen Sie die Member-Funktion des Exception-Objekts `GetErrorInfo` selbst zum Auffüllen aufzurufen `m_pErrorInfo` . Eine ausführlichere Beschreibung finden Sie in der [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) -Struktur.

Weitere Informationen zu DAO-Ausnahmen und Beispielcode finden Sie im Artikel [Ausnahmen: Daten Bank Ausnahmen](../../mfc/exceptions-database-exceptions.md).

## <a name="cdaoexceptionm_nafxdaoerror"></a><a name="m_nafxdaoerror"></a>CDaoException:: m_nAfxDaoError

Enthält einen erweiterten MFC-Fehlercode.

### <a name="remarks"></a>Bemerkungen

Dieser Code wird in Fällen bereitgestellt, in denen eine bestimmte Komponente der MFC-DAO-Klassen rot ist.

Mögliche Werte:

- NO_AFX_DAO_ERROR der letzte Vorgang hat nicht zu einem erweiterten MFC-Fehler geführt. Der Vorgang hat jedoch möglicherweise andere Fehler von DAO oder OLE erzeugt, daher sollten Sie [m_pErrorInfo](#m_perrorinfo) und möglicherweise [m_scode](#m_scode)überprüfen.

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC konnte die Microsoft Jet-Datenbank-Engine nicht initialisieren. OLE konnte möglicherweise nicht initialisiert werden, oder es konnte keine Instanz des DAO-Datenbank-Engine-Objekts erstellt werden. Diese Probleme deuten in der Regel auf eine fehlerhafte Installation von DAO oder OLE hin.

- AFX_DAO_ERROR_DFX_BIND eine Adresse, die in einem DAO-Daten Satz Feld Austausch (DFX)-Funktions Aufrufsatz verwendet wird, ist nicht vorhanden oder ungültig (die Adresse wurde nicht zum Binden von Daten verwendet). Möglicherweise haben Sie in einem DFX-Befehl eine ungültige Adresse übermittelt, oder die Adresse ist zwischen DFX-Vorgängen ungültig.

- AFX_DAO_ERROR_OBJECT_NOT_OPEN Sie versucht haben, ein Recordset basierend auf einem QueryDef-oder Tabledef-Objekt zu öffnen, das sich nicht in einem geöffneten Zustand befand.

## <a name="cdaoexceptionm_perrorinfo"></a><a name="m_perrorinfo"></a>CDaoException:: m_pErrorInfo

Enthält einen Zeiger auf eine- `CDaoErrorInfo` Struktur, die Informationen über das DAO-Fehler Objekt bereitstellt, das Sie zuletzt durch Aufrufen von [GetErrorInfo](#geterrorinfo)abgerufen haben.

### <a name="remarks"></a>Bemerkungen

Dieses Objekt enthält die folgenden Informationen:

|CDaoErrorInfo-Member|Information|Bedeutung|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|Fehlercode|Der DAO-Fehlercode|
|`m_strSource`|`Source`|Der Name des Objekts oder der Anwendung, das ursprünglich den Fehler generiert hat.|
|`m_strDescription`|BESCHREIBUNG|Eine beschreibende Zeichenfolge, die dem Fehler zugeordnet ist.|
|`m_strHelpFile`|Hilfedatei|Ein Pfad zu einer Windows-Hilfedatei, in der der Benutzerinformationen zum Problem erhalten kann.|
|`m_lHelpContext`|Hilfe Kontext|Die Kontext-ID für ein Thema in der DAO-Hilfedatei.|

Ausführliche Informationen zu den Informationen, die im- `CDaoErrorInfo` Objekt enthalten sind, finden Sie in der [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md) -Struktur.

## <a name="cdaoexceptionm_scode"></a><a name="m_scode"></a>CDaoException:: m_scode

Enthält einen Wert vom Typ `SCODE` , der den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Dies ist ein OLE-Code. Dieser Wert muss nur selten verwendet werden, da in fast allen Fällen spezifischere MFC-oder DAO-Fehlerinformationen in den anderen Datenmembern verfügbar sind `CDaoException` .

Informationen zu SCODE finden Sie im Thema [Struktur der OLE-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK. Der SCODE-Datentyp wird dem HRESULT-Datentyp zugeordnet.

## <a name="see-also"></a>Weitere Informationen

[CException-Klasse](../../mfc/reference/cexception-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CException-Klasse](../../mfc/reference/cexception-class.md)
