---
title: Workerarchetype
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: 2e57c575ed778184cf319bb84e61f585fcfa2111
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509340"
---
# <a name="worker-archetype"></a>Workerarchetype

Klassen *, die dem workerarchetype* entsprechen, stellen den Code bereit, mit dem Arbeitsaufgaben in einem Thread Pool verarbeitet werden.

**Implementierung**

Um eine Klasse zu implementieren, die diesem Archetype entspricht, muss die-Klasse die folgenden Funktionen bereitstellen:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Initialize](#initialize)|Wird aufgerufen, um das Worker-Objekt zu initialisieren, bevor Anforderungen an [Execute](#execute)übermittelt werden.|
|[Ausführen](#execute)|Wird aufgerufen, um ein Arbeits Element zu verarbeiten.|
|[Terminate](#terminate)|Wird aufgerufen, um die Initialisierung des workerobjekts aufzurufen, nachdem alle Anforderungen an [Execute](#execute)übermittelt wurden.|

|Typedef|BESCHREIBUNG|
|-------------|-----------------|
|[RequestType](#requesttype)|Eine typedef für den Typ der Arbeitsaufgabe, die von der Worker-Klasse verarbeitet werden kann.|

Eine typische *Worker* -Klasse sieht wie folgt aus:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Vorhandene Implementierungen**

Diese Klassen entsprechen diesem Archetyp:

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[Cnonstatus-Worker](../../atl/reference/cnonstatelessworker-class.md)|Empfängt Anforderungen aus dem Thread Pool und übergibt sie an ein Workerobjekt, das für jede Anforderung erstellt und zerstört wird.|

**Verwenden Sie**

Diese Vorlagen Parameter erwarten, dass die Klasse diesem Archetype entspricht:

|Parametername|Verwendet von|
|--------------------|-------------|
|*Arbeiter*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Arbeiter*|[Cnonstatus-Worker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlutil. h

## <a name="execute"></a>Workerarchetype:: Execute

Wird aufgerufen, um ein Arbeits Element zu verarbeiten.

```
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parameter

*Anforderung*<br/>
Das zu verarbeitende Arbeits Element. Das Arbeits Element hat denselben Typ wie `RequestType`.

*pvworkerparam*<br/>
Ein benutzerdefinierter Parameter, der von der Worker-Klasse verstanden wird. Wird auch an `WorkerArchetype::Initialize` und `Terminate`übermittelt.

*poverlt*<br/>
Ein Zeiger auf die [über](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) Lapp Ende Struktur, die verwendet wird, um die Warteschlange zu erstellen, in der die Arbeitselemente in die Warteschlange

## <a name="initialize"></a>Workerarchetype:: Initialize

Wird aufgerufen, um das Worker-Objekt zu initialisieren, bevor Anforderungen an `WorkerArchetype::Execute`übermittelt werden.

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parameter

*pvParam*<br/>
Ein benutzerdefinierter Parameter, der von der Worker-Klasse verstanden wird. Wird auch an `WorkerArchetype::Terminate` und `WorkerArchetype::Execute`übermittelt.

### <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg TRUE zurück, bei einem Fehler false.

## <a name="requesttype"></a>Workerarchetype:: RequestType

Eine typedef für den Typ der Arbeitsaufgabe, die von der Worker-Klasse verarbeitet werden kann.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Bemerkungen

Dieser Typ muss als erster Parameter von `WorkerArchetype::Execute` verwendet werden und muss in der Lage sein, in eine und aus einer ULONG_PTR umgewandelt zu werden.

## <a name="terminate"></a>Workerarchetype:: beenden

Wird aufgerufen, um die Initialisierung des workerobjekts aufzurufen, nachdem alle Anforderungen an `WorkerArchetype::Execute`).

```
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parameter

*pvParam*<br/>
Ein benutzerdefinierter Parameter, der von der Worker-Klasse verstanden wird. Wird auch an `WorkerArchetype::Initialize` und `WorkerArchetype::Execute`übermittelt.

## <a name="see-also"></a>Weitere Informationen

[Konzepte](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)
