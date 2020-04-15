---
title: CCriticalSection-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCriticalSection
- AFXMT/CCriticalSection
- AFXMT/CCriticalSection::CCriticalSection
- AFXMT/CCriticalSection::Lock
- AFXMT/CCriticalSection::Unlock
- AFXMT/CCriticalSection::m_sect
helpviewer_keywords:
- CCriticalSection [MFC], CCriticalSection
- CCriticalSection [MFC], Lock
- CCriticalSection [MFC], Unlock
- CCriticalSection [MFC], m_sect
ms.assetid: f776f74b-5b0b-4f32-9c13-2b8e4a0d7b2b
ms.openlocfilehash: d79199a332f6930619e6b4995b04bc590b6ea580
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369361"
---
# <a name="ccriticalsection-class"></a>CCriticalSection-Klasse

Stellt einen "kritischen Abschnitt" dar – ein Synchronisierungsobjekt, das einem Thread gleichzeitig den Zugriff auf eine Ressource oder einen Codeabschnitt ermöglicht.

## <a name="syntax"></a>Syntax

```
class CCriticalSection : public CSyncObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCriticalSection::CCriticalSection](#ccriticalsection)|Erstellt ein `CCriticalSection`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCriticalSection::Sperren](#lock)|Verwenden Sie diese `CCriticalSection` Datei, um Zugriff auf das Objekt zu erhalten.|
|[CCriticalSection::Entsperren](#unlock)|Gibt das `CCriticalSection`-Objekt frei.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCriticalSection::operator CRITICAL_SECTION*](#operator_critical_section_star)|Ruft einen Zeiger auf das interne CRITICAL_SECTION Objekt ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCriticalSection::m_sect](#m_sect)|Ein CRITICAL_SECTION Objekt.|

## <a name="remarks"></a>Bemerkungen

Kritische Abschnitte sind nützlich, wenn jeweils nur ein Thread Daten oder eine andere gesteuerte Ressource ändern darf. Das Hinzufügen von Knoten zu einer verknüpften Liste ist z. B. ein Prozess, der jeweils nur von einem Thread zugelassen werden sollte. Durch die `CCriticalSection` Verwendung eines Objekts zum Steuern der verknüpften Liste kann jeweils nur ein Thread auf die Liste zugreifen.

> [!NOTE]
> Die Funktionalität `CCriticalSection` der Klasse wird durch ein tatsächliches Win32-CRITICAL_SECTION-Objekt bereitgestellt.

Kritische Abschnitte werden anstelle von Mutexen (siehe [CMutex](../../mfc/reference/cmutex-class.md)) verwendet, wenn die Geschwindigkeit kritisch ist und die Ressource nicht über Prozessgrenzen hinweg verwendet wird.

Es gibt zwei Methoden `CCriticalSection` für die Verwendung eines Objekts: Standalone und eingebettet in eine Klasse.

- Eigenständige Methode Um ein eigenständiges `CCriticalSection` Objekt zu `CCriticalSection` verwenden, erstellen Sie das Objekt, wenn es benötigt wird. Sperren Sie das Objekt nach einer erfolgreichen Rückgabe vom Konstruktor explizit mit einem Aufruf von [Lock](#lock). Rufen Sie [Unlock](#unlock) auf, wenn Sie mit dem Zugriff auf den kritischen Abschnitt fertig sind. Diese Methode ist zwar für jemanden, der Ihren Quellcode liest, zwar klarer, ist jedoch fehleranfälliger, da Sie daran denken müssen, den kritischen Abschnitt vor und nach dem Zugriff zu sperren und zu entsperren.

   Eine besser vorzuziehende Methode ist die Verwendung der [CSingleLock-Klasse.](../../mfc/reference/csinglelock-class.md) Es hat `Lock` auch `Unlock` eine und Methode, aber Sie müssen sich keine Gedanken über das Entsperren der Ressource machen, wenn eine Ausnahme auftritt.

- Eingebettete Methode Sie können eine Klasse auch `CCriticalSection`für mehrere Threads freigeben, indem Sie der Klasse einen -typ-Datenmember hinzufügen und den Datenmember bei Bedarf sperren.

Weitere Informationen zur `CCriticalSection` Verwendung von Objekten finden Sie im Artikel [Multithreading: Verwenden der Synchronisierungsklassen](../../parallel/multithreading-how-to-use-the-synchronization-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CCriticalSection`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmt.h

## <a name="ccriticalsectionccriticalsection"></a><a name="ccriticalsection"></a>CCriticalSection::CCriticalSection

Erstellt ein `CCriticalSection`-Objekt.

```
CCriticalSection();
```

### <a name="remarks"></a>Bemerkungen

Um auf ein `CCriticalSection` Objekt zuzugreifen oder es freizugeben, erstellen Sie ein [CSingleLock-Objekt](../../mfc/reference/csinglelock-class.md) und rufen die [Mitgliedsfunktionen Sperren](../../mfc/reference/csinglelock-class.md#lock) und [Entsperren](../../mfc/reference/csinglelock-class.md#unlock) auf. Wenn `CCriticalSection` das Objekt eigenständig verwendet wird, rufen Sie die [Unlock-Memberfunktion](#unlock) auf, um es freizugeben.

Wenn der Konstruktor den erforderlichen Systemspeicher nicht zuweisen kann, wird automatisch eine Speicherausnahme (vom Typ [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) ausgelöst.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CCriticalSection::Lock](#lock).

## <a name="ccriticalsectionlock"></a><a name="lock"></a>CCriticalSection::Sperren

Rufen Sie diese Memberfunktion auf, um Zugriff auf das Objekt des kritischen Abschnitts zu erhalten.

```
BOOL Lock();
BOOL Lock(DWORD dwTimeout);
```

### <a name="parameters"></a>Parameter

*dwTimeout*<br/>
`Lock`ignoriert diesen Parameterwert.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Funktion erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

`Lock`ist ein blockierender Aufruf, der erst zurückgegeben wird, wenn das Objekt des kritischen Abschnitts signalisiert wird (verfügbar wird).

Wenn zeitliche Wartezeiten erforderlich sind, können Sie ein `CCriticalSection` [CMutex-Objekt](../../mfc/reference/cmutex-class.md) anstelle eines Objekts verwenden.

Wenn `Lock` der erforderliche Systemspeicher nicht zugewiesen werden kann, wird automatisch eine Speicherausnahme (vom Typ [CMemoryException](../../mfc/reference/cmemoryexception-class.md)) ausgelöst.

### <a name="example"></a>Beispiel

In diesem Beispiel wird der Ansatz für verschachtelte kritische `_strShared` Abschnitte veranschaulicht, `CCriticalSection` indem der Zugriff auf eine freigegebene Ressource (das statische Objekt) mithilfe eines freigegebenen Objekts gesteuert wird. Die `SomeMethod` Funktion veranschaulicht die sichere Aktualisierung einer freigegebenen Ressource.

[!code-cpp[NVC_MFC_Utilities#11](../../mfc/codesnippet/cpp/ccriticalsection-class_1.h)]

## <a name="ccriticalsectionm_sect"></a><a name="m_sect"></a>CCriticalSection::m_sect

Enthält ein kritisches Abschnittsobjekt, das von allen `CCriticalSection` Methoden verwendet wird.

```
CRITICAL_SECTION m_sect;
```

## <a name="ccriticalsectionoperator-critical_section"></a><a name="operator_critical_section_star"></a>CCriticalSection::operator CRITICAL_SECTION*

Ruft ein CRITICAL_SECTION Objekt ab.

```
operator CRITICAL_SECTION*();
```

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um einen Zeiger auf das interne CRITICAL_SECTION Objekt abzurufen.

## <a name="ccriticalsectionunlock"></a><a name="unlock"></a>CCriticalSection::Entsperren

Gibt `CCriticalSection` das Objekt für die Verwendung durch einen anderen Thread frei.

```
BOOL Unlock();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CCriticalSection` ungleich Null, wenn das Objekt im Besitz des Threads war und die Freigabe erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn `CCriticalSection` der eigenständig verwendet `Unlock` wird, muss sofort nach Abschluss der Verwendung der Ressource aufgerufen werden, die vom kritischen Abschnitt gesteuert wird. Wenn ein [CSingleLock-Objekt](../../mfc/reference/csinglelock-class.md) `CCriticalSection::Unlock` verwendet wird, wird es `Unlock` von der Memberfunktion des Sperrobjekts aufgerufen.

### <a name="example"></a>Beispiel

  Siehe beispielfür [CCriticalSection::Lock](#lock).

## <a name="see-also"></a>Siehe auch

[CSyncObject-Klasse](../../mfc/reference/csyncobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMutex-Klasse](../../mfc/reference/cmutex-class.md)
