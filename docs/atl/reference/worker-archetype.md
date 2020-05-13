---
title: Worker Archetype
ms.date: 11/04/2016
helpviewer_keywords:
- Worker archetype
ms.assetid: 834145cd-09d3-4149-bc99-620e1871cbfb
ms.openlocfilehash: c9ed9b30b94a8debe133bc213c12063750bfb15a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747348"
---
# <a name="worker-archetype"></a>Worker Archetype

Klassen, die dem *Workerarchetyp* entsprechen, stellen den Code zum Verarbeiten von Arbeitsaufgaben bereit, die in der Warteschlange eines Threadpools stehen.

**Implementierung**

Um eine Klasse zu implementieren, die diesem Archetyp entspricht, muss die Klasse die folgenden Features bereitstellen:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Initialize](#initialize)|Wird aufgerufen, um das Workerobjekt zu initialisieren, bevor Anforderungen an [Execute](#execute)übergeben werden.|
|[Ausführen](#execute)|Wird aufgerufen, um eine Arbeitsaufgabe zu verarbeiten.|
|[Terminate](#terminate)|Wird aufgerufen, um das Workerobjekt zu entinitialisieren, nachdem alle Anforderungen an [Execute](#execute)übergeben wurden.|

|Typedef|BESCHREIBUNG|
|-------------|-----------------|
|[Requesttype](#requesttype)|Eine typedef für den Typ der Arbeitsaufgabe, die von der Arbeitskraftklasse verarbeitet werden kann.|

Eine typische *Workerklasse* sieht wie folgt aus:

[!code-cpp[NVC_ATL_Utilities#137](../../atl/codesnippet/cpp/worker-archetype_1.cpp)]

**Vorhandene Implementierungen**

Diese Klassen entsprechen diesem Archetyp:

|Klasse|BESCHREIBUNG|
|-----------|-----------------|
|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|Empfängt Anforderungen aus dem Threadpool und gibt sie an ein Workerobjekt weiter, das für jede Anforderung erstellt und zerstört wird.|

**Verwenden Sie**

Diese Vorlagenparameter erwarten, dass die Klasse diesem Archetyp entspricht:

|Parametername|Verwendet von|
|--------------------|-------------|
|*Worker*|[CThreadPool](../../atl/reference/cthreadpool-class.md)|
|*Worker*|[CNonStatelessWorker](../../atl/reference/cnonstatelessworker-class.md)|

### <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlutil.h

## <a name="workerarchetypeexecute"></a><a name="execute"></a>WorkerArchetype::Ausführen

Wird aufgerufen, um eine Arbeitsaufgabe zu verarbeiten.

```cpp
void Execute(
    RequestType request,
    void* pvWorkerParam,
    OVERLAPPED* pOverlapped);
```

#### <a name="parameters"></a>Parameter

*Anforderung*<br/>
Die zu verarbeitende Arbeitsaufgabe. Die Arbeitsaufgabe hat den `RequestType`gleichen Typ wie .

*pvWorkerParam*<br/>
Ein benutzerdefinierter Parameter, der von der Workerklasse verstanden wird. Auch an `WorkerArchetype::Initialize` `Terminate`und übergeben.

*pOverlapped*<br/>
Ein Zeiger auf die [OVERLAPPED-Struktur,](/windows/win32/api/minwinbase/ns-minwinbase-overlapped) die zum Erstellen der Warteschlange verwendet wird, in der Arbeitsaufgaben in die Warteschlange eingereiht wurden.

## <a name="workerarchetypeinitialize"></a><a name="initialize"></a>WorkerArchetype::Initialisieren

Wird aufgerufen, um das Workerobjekt zu `WorkerArchetype::Execute`initialisieren, bevor Anforderungen an übergeben werden.

```
BOOL Initialize(void* pvParam) throw();
```

#### <a name="parameters"></a>Parameter

*pvParam*<br/>
Ein benutzerdefinierter Parameter, der von der Workerklasse verstanden wird. Auch an `WorkerArchetype::Terminate` `WorkerArchetype::Execute`und übergeben.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg, FALSE bei Fehler zurück.

## <a name="workerarchetyperequesttype"></a><a name="requesttype"></a>WorkerArchetype::RequestType

Eine typedef für den Typ der Arbeitsaufgabe, die von der Arbeitskraftklasse verarbeitet werden kann.

```
typedef MyRequestType RequestType;
```

### <a name="remarks"></a>Bemerkungen

Dieser Typ muss als erster `WorkerArchetype::Execute` Parameter von und von einem ULONG_PTR verwendet werden und muss in der Lage sein, es zu umwerfen.

## <a name="workerarchetypeterminate"></a><a name="terminate"></a>WorkerArchetype::Beenden

Wird aufgerufen, um das Workerobjekt zu entinitialisieren, nachdem alle Anforderungen an `WorkerArchetype::Execute`übergeben wurden.

```cpp
void Terminate(void* pvParam) throw();
```

#### <a name="parameters"></a>Parameter

*pvParam*<br/>
Ein benutzerdefinierter Parameter, der von der Workerklasse verstanden wird. Auch an `WorkerArchetype::Initialize` `WorkerArchetype::Execute`und übergeben.

## <a name="see-also"></a>Weitere Informationen

[Konzepte](../../atl/active-template-library-atl-concepts.md)<br/>
[ATL-COM-Desktop-Komponenten](../../atl/atl-com-desktop-components.md)
