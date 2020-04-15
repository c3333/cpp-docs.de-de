---
title: CSettingsStoreSP-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::CSettingsStoreSP
- AFXSETTINGSSTORE/CSettingsStoreSP::Create
- AFXSETTINGSSTORE/CSettingsStoreSP::SetRuntimeClass
helpviewer_keywords:
- CSettingsStoreSP [MFC], CSettingsStoreSP
- CSettingsStoreSP [MFC], Create
- CSettingsStoreSP [MFC], SetRuntimeClass
ms.assetid: bcd37f40-cfd4-4d17-a5ce-3bfabe995dcc
ms.openlocfilehash: 9e22184a4081762a3d505645752e514315146981
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318454"
---
# <a name="csettingsstoresp-class"></a>CSettingsStoreSP-Klasse

Die `CSettingsStoreSP` Klasse ist eine Hilfsklasse, mit der Sie Instanzen der [CSettingsStore-Klasse](../../mfc/reference/csettingsstore-class.md)erstellen können.

## <a name="syntax"></a>Syntax

```
class CSettingsStoreSP
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSettingsStoreSP::CSettingsStoreSP](#csettingsstoresp)|Erstellt ein `CSettingsStoreSP`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSettingsStoreSP::Erstellen](#create)|Erstellt eine Instanz einer Klasse, `CSettingsStore`die von abgeleitet wird.|
|[CSettingsStoreSP::SetRuntimeClass](#setruntimeclass)|Legt die Laufzeitklasse fest. Die `Create` Methode verwendet die Laufzeitklasse, um zu bestimmen, welche Objektklasse erstellt werden soll.|

### <a name="data-members"></a>Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|`m_dwUserData`|Benutzerdefinierte Benutzerdaten, die `CSettingsStoreSP` im Objekt gespeichert sind. Sie geben diese Daten im `CSettingsStoreSP` Konstruktor des Objekts an.|
|`m_pRegistry`|Das `CSettingsStore`-derived-Objekt, das von der `Create` Methode erstellt wird.|

## <a name="remarks"></a>Bemerkungen

Sie können `CSettingsStoreSP` die Klasse verwenden, um alle MFC-Registrierungsvorgänge an andere Speicherorte umzuleiten, z. B. eine XML-Datei oder eine Datenbank. Gehen Sie dazu folgendermaßen vor:

1. Erstellen Sie eine `CMyStore`Klasse (z. `CSettingsStore`B.), und leiten Sie sie von ab.

1. Verwenden Sie [DECLARE_DYNCREATE](run-time-object-model-services.md#declare_dyncreate) und [IMPLEMENT_DYNCREATE](run-time-object-model-services.md#implement_dyncreate) Makros mit Ihrer benutzerdefinierten `CSettingsStore` Klasse, um die dynamische Erstellung zu ermöglichen.

1. Überschreiben Sie die virtuellen `Read` `Write` Funktionen und implementieren Sie die und Funktionen in Ihrer benutzerdefinierten Klasse. Implementieren Sie alle anderen Funktionen zum Lesen und Schreiben von Daten an Den gewünschten Speicherort.

1. Rufen `CSettingsStoreSP::SetRuntimeClass` Sie in Ihrer Anwendung einen Zeiger auf die [CRuntimeClass-Struktur](../../mfc/reference/cruntimeclass-structure.md) auf, die Sie von Ihrer Klasse erhalten haben.

Immer wenn das Framework in der Regel auf die Registrierung zugreift, wird es ihre benutzerdefinierte Klasse dynamisch instanziiert und zum Lesen oder Schreiben von Daten verwendet.

`CSettingsStoreSP::SetRuntimeClass`verwendet eine globale statische Variable. Daher ist jeweils nur ein benutzerdefinierter Speicher verfügbar.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxsettingsstore.h

## <a name="csettingsstorespcreate"></a><a name="create"></a>CSettingsStoreSP::Erstellen

Erstellt eine neue Instanz eines Objekts, das von der [CSettingsStore-Klasse](../../mfc/reference/csettingsstore-class.md)abgeleitet wird.

```
CSettingsStore& CSettingsStoreSP Create(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>Parameter

*bAdmin*<br/>
[in] Ein boolescher Parameter, `CSettingsStore` der bestimmt, ob ein Objekt im Administratormodus erstellt wird.

*bReadOnly*<br/>
[in] Ein boolescher Parameter, `CSettingsStore` der bestimmt, ob ein Objekt für den schreibgeschützten Zugriff erstellt wird.

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf `CSettingsStore` das neu erstellte Objekt.

### <a name="remarks"></a>Bemerkungen

Sie können die Methode [CSettingsStoreSP::SetRuntimeClass](#setruntimeclass) verwenden, `CSettingsStoreSP::Create` um zu bestimmen, welcher Objekttyp erstellt wird. Standardmäßig erstellt diese Methode `CSettingsStore` ein Objekt.

Wenn Sie `CSettingsStore` ein Objekt im Administratormodus erstellen, wird der Standardspeicherort für den gesamten Registrierungszugriff HKEY_LOCAL_MACHINE. Andernfalls wird der Standardspeicherort für den gesamten Registrierungszugriff HKEY_CURRENT_USER.

Wenn *bAdmin* TRUE ist, muss die Anwendung über Administratorrechte verfügen. Andernfalls schlägt sie fehl, wenn versucht wird, auf die Registrierung zuzugreifen.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird `Create` veranschaulicht, `CSettingsStoreSP` wie die Methode der Klasse verwendet wird.

[!code-cpp[NVC_MFC_RibbonApp#33](../../mfc/reference/codesnippet/cpp/csettingsstoresp-class_1.cpp)]

## <a name="csettingsstorespcsettingsstoresp"></a><a name="csettingsstoresp"></a>CSettingsStoreSP::CSettingsStoreSP

Erstellt ein [CSettingsStoreSP-Klassenobjekt.](../../mfc/reference/csettingsstoresp-class.md)

```
CSettingsStoreSP::CSettingsStoreSP(DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*dwUserData*<br/>
[in] Benutzerdefinierte Daten, `CSettingsStoreSP` die das Objekt speichert.

### <a name="remarks"></a>Bemerkungen

Das `CSettingsStoreSP` Objekt speichert die Daten aus *dwUserData* in der geschützten Membervariablen `m_dwUserData`.

## <a name="csettingsstorespsetruntimeclass"></a><a name="setruntimeclass"></a>CSettingsStoreSP::SetRuntimeClass

Legt die Laufzeitklasse fest. Die Methode [CSettingsStoreSP::Create](#create) verwendet die Laufzeitklasse, um zu bestimmen, welcher Objekttyp erstellt werden soll.

```
static BOOL __stdcall CSettingsStoreSP::SetRuntimeClass(CRuntimeClass* pRTI);
```

### <a name="parameters"></a>Parameter

*pRTI*<br/>
[in] Ein Zeiger auf die Laufzeitklasseninformationen für eine Klasse, die von der [CSettingsStore-Klasse](../../mfc/reference/csettingsstore-class.md)abgeleitet wurde.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich; FALSE, wenn die von *pRTI* `CSettingsStore`identifizierte Klasse nicht von abgeleitet ist.

### <a name="remarks"></a>Bemerkungen

Sie können die [CSettingsStoreSP-Klasse](../../mfc/reference/csettingsstoresp-class.md) verwenden, um Klassen von `CSettingsStore`abzuleiten. Verwenden Sie `SetRuntimeClass` die Methode, wenn Sie Objekte einer `CSettingsStore`benutzerdefinierten Klasse erstellen möchten, die von abgeleitet wird.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CSettingsStore-Klasse](../../mfc/reference/csettingsstore-class.md)
