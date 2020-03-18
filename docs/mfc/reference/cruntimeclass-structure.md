---
title: CRuntimeClass-Struktur
ms.date: 11/04/2016
f1_keywords:
- CRuntimeClass
helpviewer_keywords:
- CRuntimeClass structure [MFC]
- dynamic class information [MFC]
- runtime [MFC], class information
- run-time class [MFC], CRuntimeClass structure
ms.assetid: de62b6ef-90d4-420f-8c70-f58b36976a2b
ms.openlocfilehash: 92979a10c18d9759e0ecc9f0785e56a97c0f0642
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426786"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass-Struktur

Jede Klasse, die von `CObject` abgeleitet ist, ist mit einer `CRuntimeClass` Struktur verknüpft, die Sie zum Abrufen von Informationen zu einem Objekt oder seiner Basisklasse zur Laufzeit verwenden können.

## <a name="syntax"></a>Syntax

```
struct CRuntimeClass
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CRuntimeClass:: erkreateobject](#createobject)|Erstellt ein-Objekt zur Laufzeit.|
|[CRuntimeClass:: FromName](#fromname)|Erstellt ein-Objekt zur Laufzeit unter Verwendung des vertrauten Klassen namens.|
|[CRuntimeClass:: IsDerivedFrom](#isderivedfrom)|Bestimmt, ob die Klasse von der angegebenen Klasse abgeleitet ist.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CRuntimeClass:: m_lpszClassName](#m_lpszclassname)|Der Name der Klasse.|
|[CRuntimeClass:: m_nObjectSize](#m_nobjectsize)|Die Größe des Objekts in Bytes.|
|[CRuntimeClass:: m_pBaseClass](#m_pbaseclass)|Ein Zeiger auf die `CRuntimeClass` Struktur der Basisklasse.|
|[CRuntimeClass:: m_pfnCreateObject](#m_pfncreateobject)|Ein Zeiger auf die Funktion, die das Objekt dynamisch erstellt.|
|[CRuntimeClass:: m_pfnGetBaseClass](#m_pfngetbaseclass)|Gibt die `CRuntimeClass` Struktur zurück (nur verfügbar, wenn dynamisch verknüpft).|
|[CRuntimeClass:: m_wSchema](#m_wschema)|Die Schema Nummer der-Klasse.|

## <a name="remarks"></a>Hinweise

`CRuntimeClass` ist eine Struktur, die daher nicht über eine Basisklasse verfügt.

Die Möglichkeit, die Klasse eines Objekts zur Laufzeit zu bestimmen, ist nützlich, wenn eine zusätzliche Typüberprüfung von Funktions Argumenten erforderlich ist oder wenn Sie speziellen Code basierend auf der Klasse eines Objekts schreiben müssen. Lauf Zeit Klassen Informationen werden nicht direkt von der C++ Sprache unterstützt.

`CRuntimeClass` stellt Informationen über das verbundene C++ Objekt bereit, z. b. einen Zeiger auf den `CRuntimeClass` der Basisklasse und den ASCII-Klassennamen der verknüpften Klasse. Diese Struktur implementiert auch verschiedene Funktionen, die verwendet werden können, um dynamisch Objekte zu erstellen, den Objekttyp unter Verwendung eines vertrauten namens anzugeben und zu bestimmen, ob die verknüpfte Klasse von einer bestimmten Klasse abgeleitet ist.

Weitere Informationen zur Verwendung von `CRuntimeClass`finden Sie im Artikel [zugreifen auf Lauf Zeit Klassen Informationen](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CRuntimeClass`

## <a name="requirements"></a>Voraussetzungen

**Header:** afx.h

##  <a name="createobject"></a>CRuntimeClass:: erkreateobject

Rufen Sie diese Funktion auf, um die angegebene Klasse dynamisch während der Laufzeit zu erstellen.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Der vertraute Name der zu erstellenden Klasse.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Objekt oder NULL, wenn der Klassenname nicht gefunden wurde oder nicht genügend Arbeitsspeicher vorhanden ist, um das Objekt zu erstellen.

### <a name="remarks"></a>Hinweise

Von `CObject` abgeleitete Klassen können die dynamische Erstellung unterstützen. Dies ist die Möglichkeit, ein Objekt einer angegebenen Klasse zur Laufzeit zu erstellen. Die Klassen "Document", "View" und "Frame" sollten beispielsweise die dynamische Erstellung unterstützen. Weitere Informationen zur dynamischen Erstellung und zum `CreateObject`-Member finden Sie unter [CObject Class](../../mfc/using-cobject.md) und [CObject Class: Angeben von Funktionsebenen](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsDerivedFrom](#isderivedfrom).

##  <a name="fromname"></a>CRuntimeClass:: FromName

Rufen Sie diese Funktion auf, um die `CRuntimeClass`-Struktur abzurufen, die dem vertrauten Namen zugeordnet ist.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Der vertraute Name einer Klasse, die von `CObject`abgeleitet ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CRuntimeClass`-Objekt, das dem Namen entspricht, der in *lpszClassName*übergeben wird. Die-Funktion gibt NULL zurück, wenn kein entsprechender Klassenname gefunden wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

##  <a name="isderivedfrom"></a>CRuntimeClass:: IsDerivedFrom

Rufen Sie diese Funktion auf, um zu bestimmen, ob die aufrufende Klasse von der im *pbaseclass* -Parameter angegebenen Klasse abgeleitet ist.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parameter

*pbaseclass*<br/>
Der vertraute Name einer Klasse, die von `CObject`abgeleitet ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Klasse, die `IsDerivedFrom` aufrufen, von der Basisklasse abgeleitet wird, deren `CRuntimeClass` Struktur als Parameter angegeben wird. andernfalls false.

### <a name="remarks"></a>Hinweise

Die Beziehung wird durch "Walking" aus der Klasse des Members nach oben in der Kette der abgeleiteten Klassen nach oben festgelegt. Diese Funktion gibt nur dann false zurück, wenn keine Entsprechung für die Basisklasse gefunden wurde.

> [!NOTE]
>  Wenn Sie die `CRuntimeClass` Struktur verwenden möchten, müssen Sie das IMPLEMENT_DYNAMIC-, IMPLEMENT_DYNCREATE-oder IMPLEMENT_SERIAL-Makro in die-Implementierung der-Klasse einschließen, für die Sie die Laufzeitobjekt Informationen abrufen möchten.

Weitere Informationen zur Verwendung von `CRuntimeClass`finden Sie im Artikel [CObject-Klasse: Zugreifen auf Lauf Zeit Klassen Informationen](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

##  <a name="m_lpszclassname"></a>CRuntimeClass:: m_lpszClassName

Eine mit NULL endenden Zeichenfolge, die den ASCII-Klassennamen enthält.

### <a name="remarks"></a>Hinweise

Dieser Name kann verwendet werden, um mithilfe der `FromName` Member-Funktion eine Instanz der-Klasse zu erstellen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsDerivedFrom](#isderivedfrom).

##  <a name="m_nobjectsize"></a>CRuntimeClass:: m_nObjectSize

Die Größe des-Objekts in Bytes.

### <a name="remarks"></a>Hinweise

Wenn das-Objekt über Datenmember verfügt, die auf zugeordneten Arbeitsspeicher zeigen, ist die Größe dieses Speichers nicht inbegriffen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pbaseclass"></a>CRuntimeClass:: m_pBaseClass

Wenn die Anwendung statisch mit MFC verknüpft ist, enthält dieser Datenmember einen Zeiger auf die `CRuntimeClass` Struktur der Basisklasse.

### <a name="remarks"></a>Hinweise

Wenn die Anwendung dynamisch mit der MFC-Bibliothek verknüpft ist, finden Sie weitere Informationen unter [m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsDerivedFrom](#isderivedfrom).

##  <a name="m_pfncreateobject"></a>CRuntimeClass:: m_pfnCreateObject

Ein Funktionszeiger auf den Standardkonstruktor, der ein Objekt der Klasse erstellt.

### <a name="remarks"></a>Hinweise

Dieser Zeiger ist nur gültig, wenn die-Klasse die dynamische Erstellung unterstützt. Andernfalls gibt die Funktion NULL zurück.

##  <a name="m_pfngetbaseclass"></a>CRuntimeClass:: m_pfnGetBaseClass

Wenn Ihre Anwendung die MFC-Bibliothek als freigegebene DLL verwendet, verweist dieser Datenmember auf eine Funktion, die die `CRuntimeClass` Struktur der Basisklasse zurückgibt.

### <a name="remarks"></a>Hinweise

Wenn Ihre Anwendung statisch mit der MFC-Bibliothek verknüpft ist, finden Sie weitere Informationen unter [m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsDerivedFrom](#isderivedfrom).

##  <a name="m_wschema"></a>CRuntimeClass:: m_wSchema

Die Schema Nummer (-1 für nicht serialisierbare Klassen).

### <a name="remarks"></a>Hinweise

Weitere Informationen zu Schema Nummern finden Sie im [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) -Makro.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObject:: getruntimeclass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
