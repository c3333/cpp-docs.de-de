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
ms.openlocfilehash: a58b9c97d5683423a0f81f6b5424f19f987943bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318549"
---
# <a name="cruntimeclass-structure"></a>CRuntimeClass-Struktur

Jede von `CObject` ihnen abgeleitete `CRuntimeClass` Klasse ist einer Struktur zugeordnet, die Sie verwenden können, um Informationen über ein Objekt oder seine Basisklasse zur Laufzeit abzuerhalten.

## <a name="syntax"></a>Syntax

```
struct CRuntimeClass
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRuntimeClass::CreateObject](#createobject)|Erstellt ein Objekt während der Laufzeit.|
|[CRuntimeClass::FromName](#fromname)|Erstellt ein Objekt während der Laufzeit unter Verwendung des bekannten Klassennamens.|
|[CRuntimeClass::IsDerivedVon](#isderivedfrom)|Bestimmt, ob die Klasse von der angegebenen Klasse abgeleitet wird.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRuntimeClass::m_lpszClassName](#m_lpszclassname)|Der Name der Klasse.|
|[CRuntimeClass::m_nObjectSize](#m_nobjectsize)|Die Größe des Objekts in Bytes.|
|[CRuntimeClass::m_pBaseClass](#m_pbaseclass)|Ein Zeiger auf `CRuntimeClass` die Struktur der Basisklasse.|
|[CRuntimeClass::m_pfnCreateObject](#m_pfncreateobject)|Ein Zeiger auf die Funktion, die das Objekt dynamisch erstellt.|
|[CRuntimeClass::m_pfnGetBaseClass](#m_pfngetbaseclass)|Gibt `CRuntimeClass` die Struktur zurück (nur verfügbar, wenn dynamisch verknüpft).|
|[CRuntimeClass::m_wSchema](#m_wschema)|Die Schemanummer der Klasse.|

## <a name="remarks"></a>Bemerkungen

`CRuntimeClass`ist eine Struktur und hat daher keine Basisklasse.

Die Möglichkeit, die Klasse eines Objekts zur Laufzeit zu bestimmen, ist nützlich, wenn eine zusätzliche Typprüfung von Funktionsargumenten erforderlich ist oder wenn Sie zweckgebundenen Code basierend auf der Klasse eines Objekts schreiben müssen. Laufzeitklasseninformationen werden von der C++-Sprache nicht direkt unterstützt.

`CRuntimeClass`enthält Informationen zum zugehörigen C++-Objekt, z. B. einen Zeiger auf die `CRuntimeClass` Basisklasse und den ASCII-Klassennamen der verknüpften Klasse. Diese Struktur implementiert auch verschiedene Funktionen, die zum dynamischen Erstellen von Objekten verwendet werden können, indem der Objekttyp mithilfe eines bekannten Namens angegeben und bestimmt wird, ob die zugehörige Klasse von einer bestimmten Klasse abgeleitet wird.

Weitere Informationen zur `CRuntimeClass`Verwendung finden Sie im Artikel [Zugriff auf Laufzeitklasseninformationen](../../mfc/accessing-run-time-class-information.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CRuntimeClass`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cruntimeclasscreateobject"></a><a name="createobject"></a>CRuntimeClass::CreateObject

Rufen Sie diese Funktion auf, um die angegebene Klasse während der Laufzeit dynamisch zu erstellen.

```
CObject* CreateObject();

static CObject* PASCAL CreateObject(LPCSTR lpszClassName);

static CObject* PASCAL CreateObject(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Der bekannte Name der zu erstellenden Klasse.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Objekt oder NULL, wenn der Klassenname nicht gefunden wird oder nicht genügend Arbeitsspeicher zum Erstellen des Objekts vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Von Klassen `CObject` abgeleitete Klassen können die dynamische Erstellung unterstützen, d. h. die Möglichkeit, ein Objekt einer angegebenen Klasse zur Laufzeit zu erstellen. Dokument-, Ansichts- und Rahmenklassen sollten beispielsweise die dynamische Erstellung unterstützen. Weitere Informationen zur dynamischen `CreateObject` Erstellung und zum Member finden Sie unter [CObject Class](../../mfc/using-cobject.md) und [CObject Class: Specify levels of Functionality](../../mfc/specifying-levels-of-functionality.md).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassfromname"></a><a name="fromname"></a>CRuntimeClass::FromName

Rufen Sie diese `CRuntimeClass` Funktion auf, um die Struktur abzurufen, die dem bekannten Namen zugeordnet ist.

```
static CRuntimeClass* PASCAL FromName(LPCSTR lpszClassName);

static CRuntimeClass* PASCAL FromName(LPCWSTR lpszClassName);
```

### <a name="parameters"></a>Parameter

*lpszClassName*<br/>
Der vertraute Name einer `CObject`Klasse, die von abgeleitet ist.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CRuntimeClass` ein Objekt, der dem Namen entspricht, der in *lpszClassName*übergeben wird. Die Funktion gibt NULL zurück, wenn kein übereinstimmender Klassenname gefunden wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#17](../../mfc/codesnippet/cpp/cruntimeclass-structure_1.cpp)]

## <a name="cruntimeclassisderivedfrom"></a><a name="isderivedfrom"></a>CRuntimeClass::IsDerivedVon

Rufen Sie diese Funktion auf, um zu bestimmen, ob die aufrufende Klasse von der im *Parameter pBaseClass* angegebenen Klasse abgeleitet ist.

```
BOOL IsDerivedFrom(const CRuntimeClass* pBaseClass) const;
```

### <a name="parameters"></a>Parameter

*pBaseClass*<br/>
Der vertraute Name einer `CObject`Klasse, die von abgeleitet ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn `IsDerivedFrom` der Klassenaufruf von `CRuntimeClass` der Basisklasse abgeleitet wird, deren Struktur als Parameter angegeben ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Die Beziehung wird bestimmt, indem man von der Klasse des Members die Kette abgeleiteter Klassen bis nach oben "geht". Diese Funktion gibt FALSE nur zurück, wenn keine Übereinstimmung für die Basisklasse gefunden wird.

> [!NOTE]
> Um die `CRuntimeClass` Struktur zu verwenden, müssen Sie die IMPLEMENT_DYNAMIC, IMPLEMENT_DYNCREATE oder IMPLEMENT_SERIAL Makro in die Implementierung der Klasse einschließen, für die Sie Laufzeitobjektinformationen abrufen möchten.

Weitere Informationen zur `CRuntimeClass`Verwendung finden Sie im Artikel [CObject Class: Accessing Run-Time Class Information](../../mfc/accessing-run-time-class-information.md).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCObjectSample#18](../../mfc/codesnippet/cpp/cruntimeclass-structure_2.cpp)]

## <a name="cruntimeclassm_lpszclassname"></a><a name="m_lpszclassname"></a>CRuntimeClass::m_lpszClassName

Eine null-terminierte Zeichenfolge, die den ASCII-Klassennamen enthält.

### <a name="remarks"></a>Bemerkungen

Dieser Name kann verwendet werden, um eine `FromName` Instanz der Klasse mithilfe der Memberfunktion zu erstellen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_nobjectsize"></a><a name="m_nobjectsize"></a>CRuntimeClass::m_nObjectSize

Die Größe des Objekts in Bytes.

### <a name="remarks"></a>Bemerkungen

Wenn das Objekt über Datenmember verfügt, die auf zugewiesenen Speicher verweisen, ist die Größe dieses Speichers nicht enthalten.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pbaseclass"></a><a name="m_pbaseclass"></a>CRuntimeClass::m_pBaseClass

Wenn Ihre Anwendung statisch mit MFC verknüpft ist, enthält `CRuntimeClass` dieser Datenmember einen Zeiger auf die Struktur der Basisklasse.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung dynamisch mit der MFC-Bibliothek verknüpft ist, finden Sie weitere [Informationen unter m_pfnGetBaseClass](#m_pfngetbaseclass).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_pfncreateobject"></a><a name="m_pfncreateobject"></a>CRuntimeClass::m_pfnCreateObject

Ein Funktionszeiger auf den Standardkonstruktor, der ein Objekt Ihrer Klasse erstellt.

### <a name="remarks"></a>Bemerkungen

Dieser Zeiger ist nur gültig, wenn die Klasse die dynamische Erstellung unterstützt. Andernfalls gibt die Funktion NULL zurück.

## <a name="cruntimeclassm_pfngetbaseclass"></a><a name="m_pfngetbaseclass"></a>CRuntimeClass::m_pfnGetBaseClass

Wenn Ihre Anwendung die MFC-Bibliothek als freigegebene DLL verwendet, `CRuntimeClass` verweist dieser Datenmember auf eine Funktion, die die Struktur der Basisklasse zurückgibt.

### <a name="remarks"></a>Bemerkungen

Wenn Ihre Anwendung statisch mit der MFC-Bibliothek verknüpft ist, finden Sie weitere Informationen [unter m_pBaseClass](#m_pbaseclass).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="cruntimeclassm_wschema"></a><a name="m_wschema"></a>CRuntimeClass::m_wSchema

Die Schemanummer ( -1 für nicht serialisierbare Klassen).

### <a name="remarks"></a>Bemerkungen

Weitere Informationen zu Schemanummern [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) finden Sie im IMPLEMENT_SERIAL-Makro.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [IsDerivedFrom](#isderivedfrom).

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CObject::GetRuntimeClass](../../mfc/reference/cobject-class.md#getruntimeclass)<br/>
[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)<br/>
[RUNTIME_CLASS](run-time-object-model-services.md#runtime_class)<br/>
[IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)<br/>
[IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate)<br/>
[IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial)
