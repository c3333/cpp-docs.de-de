---
title: FtmBase-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: d37cdddda8cf8894016ed80b9055fe106b1600f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371513"
---
# <a name="ftmbase-class"></a>FtmBase-Klasse

Stellt ein Freethread-Marshaller-Objekt dar.

## <a name="syntax"></a>Syntax

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [RuntimeClass Class](runtimeclass-class.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

| Name                         | BESCHREIBUNG                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase::FtmBase](#ftmbase) | Initialisiert eine neue Instanz der Klasse `FtmBase`. |

### <a name="public-methods"></a>Öffentliche Methoden

| Name                                                               | BESCHREIBUNG                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase::CreateGlobalInterfaceTable](#createglobalinterfacetable) | Erstellt eine globale Schnittstellentabelle (GIT).                                                                                                                              |
| [FtmBase::DisconnectObject](#disconnectobject)                     | Alle externen Verbindungen werden zwangsweise an ein Objekt freigegeben. Der Server des Objekts ruft die Implementierung dieser Methode vor dem Herunterfahren auf.                |
| [FtmBase::GetMarshalSizeMax](#getmarshalsizemax)                   | Abrufen der Obergrenze für die Anzahl der Bytes, die zum Marshallen des angegebenen Schnittstellenzeigers für das angegebene Objekt erforderlich sind.                                                |
| [FtmBase::GetUnmarshalClass](#getunmarshalclass)                   | Ruft die CLSID ab, die COM verwendet, um die DLL zu finden, die den Code für den entsprechenden Proxy enthält. COM lädt diese DLL, um eine nicht initialisierte Instanz des Proxys zu erstellen. |
| [FtmBase::MarshalInterface](#marshalinterface)                     | Schreibt in einen Stream die Daten, die zum Initialisieren eines Proxyobjekts in einem Clientprozess erforderlich sind.                                                                          |
| [FtmBase::ReleaseMarshalData](#releasemarshaldata)                 | Zerstört ein gemarshalltes Datenpaket.                                                                                                                                    |
| [FtmBase::UnmarshalInterface](#unmarshalinterface)                 | Initialisiert einen neu erstellten Proxy und gibt einen Schnittstellenzeiger auf diesen Proxy zurück.                                                                                    |

### <a name="public-data-members"></a>Öffentliche Datenmember

| Name                                | BESCHREIBUNG                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase::marshaller_](#marshaller) | Enthält einen Verweis auf den Freithread-Marshaller. |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`FtmBase`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** ftm.h

**Namespace:** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>FtmBase::CreateGlobalInterfaceTable

Erstellt eine globale Schnittstellentabelle (GIT).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parameter

*Git*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Zeiger auf eine globale Schnittstellentabelle angezeigt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden `IGlobalInterfaceTable` Sie im `COM Interfaces` Thema im `COM Reference` Unterthema des Themas in der MSDN-Bibliothek.

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>FtmBase::DisconnectObject

Alle externen Verbindungen werden zwangsweise an ein Objekt freigegeben. Der Server des Objekts ruft die Implementierung dieser Methode vor dem Herunterfahren auf.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>Parameter

*dwReserved*<br/>
Für die zukünftige Verwendung reserviert. Muss 0 (null) sein.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>FtmBase::FtmBase

Initialisiert eine neue Instanz der Klasse `FtmBase`.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>FtmBase::GetMarshalSizeMax

Abrufen der Obergrenze für die Anzahl der Bytes, die zum Marshallen des angegebenen Schnittstellenzeigers für das angegebene Objekt erforderlich sind.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Verweis auf den Bezeichner der zu marshallenden Schnittstelle.

*Pv*<br/>
Schnittstellenzeiger, der gemarshallt werden soll; kann NULL sein.

*dwDestContext*<br/>
Zielkontext, in dem die angegebene Schnittstelle nicht gemarshallt werden soll.

Geben Sie einen oder mehrere MSHCTX-Enumerationswerte an.

Derzeit kann das Unmarshaling entweder in einer anderen Wohnung des aktuellen Prozesses (MSHCTX_INPROC) oder in einem anderen Prozess auf demselben Computer wie der aktuelle Prozess auftreten (MSHCTX_LOCAL).

*pvDestContext*<br/>
Reserviert für die zukünftige Verwendung; muss NULL sein.

*mshlflags*<br/>
Flag, das angibt, ob die zu marshallenden Daten an den Clientprozess zurückgesendet werden sollen – der typische Fall – oder in eine globale Tabelle geschrieben werden, wo sie von mehreren Clients abgerufen werden können. Geben Sie einen oder mehrere MSHLFLAGS-Enumerationswerte an.

*pSize*<br/>
Wenn dieser Vorgang abgeschlossen ist, zeigen Sie auf die obere Grenze für die Datenmenge, die in den Marshalling-Stream geschrieben werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_FAIL oder E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>FtmBase::GetUnmarshalClass

Ruft die CLSID ab, die COM verwendet, um die DLL zu finden, die den Code für den entsprechenden Proxy enthält. COM lädt diese DLL, um eine nicht initialisierte Instanz des Proxys zu erstellen.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Verweis auf den Bezeichner der zu marshallenden Schnittstelle.

*Pv*<br/>
Zeiger auf die zu marshallende Schnittstelle; kann NULL sein, wenn der Aufrufer keinen Zeiger auf die gewünschte Schnittstelle hat.

*dwDestContext*<br/>
Zielkontext, in dem die angegebene Schnittstelle nicht gemarshallt werden soll.

Geben Sie einen oder mehrere MSHCTX-Enumerationswerte an.

Das Unmarshaling kann entweder in einer anderen Wohnung des aktuellen Prozesses (MSHCTX_INPROC) oder in einem anderen Prozess auf demselben Computer wie der aktuelle Prozess (MSHCTX_LOCAL) erfolgen.

*pvDestContext*<br/>
Reserviert für die zukünftige Verwendung; muss NULL sein.

*mshlflags*<br/>
Wenn dieser Vorgang abgeschlossen ist, zeigen Sie auf die CLSID, die zum Erstellen eines Proxys im Clientprozess verwendet werden soll.

*pCid*

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>FtmBase::MarshalInterface

Schreibt in einen Stream die Daten, die zum Initialisieren eines Proxyobjekts in einem Clientprozess erforderlich sind.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>Parameter

*pStm*<br/>
Zeiger auf den Stream, der während des Marshallings verwendet werden soll.

*riid*<br/>
Verweis auf den Bezeichner der zu marshallenden Schnittstelle. Diese Schnittstelle muss von der `IUnknown` -Schnittstelle abgeleitet werden.

*Pv*<br/>
Zeiger auf den zu marshallenden Schnittstellenzeiger; kann NULL sein, wenn der Aufrufer keinen Zeiger auf die gewünschte Schnittstelle hat.

*dwDestContext*<br/>
Zielkontext, in dem die angegebene Schnittstelle nicht gemarshallt werden soll.

Geben Sie einen oder mehrere MSHCTX-Enumerationswerte an.

Das Unmarshaling kann in einer anderen Wohnung des aktuellen Prozesses (MSHCTX_INPROC) oder in einem anderen Prozess auf demselben Computer wie der aktuelle Prozess auftreten (MSHCTX_LOCAL).

*pvDestContext*<br/>
Für die zukünftige Verwendung reserviert. Muss 0 (null) sein.

*mshlflags*<br/>
Gibt an, ob die zu marshallenden Daten an den Clientprozess zurückgesendet werden sollen – der typische Fall – oder in eine globale Tabelle geschrieben werden sollen, wo sie von mehreren Clients abgerufen werden können.

### <a name="return-value"></a>Rückgabewert

S_OK Der Schnittstellenzeiger wurde erfolgreich gemarshallt.

E_NOINTERFACE Die angegebene Schnittstelle wird nicht unterstützt.

STG_E_MEDIUMFULL Der Stream ist voll.

E_FAIL Der Vorgang ist fehlgeschlagen.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>FtmBase::marshaller_

Enthält einen Verweis auf den Freithread-Marshaller.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>FtmBase::ReleaseMarshalData

Zerstört ein gemarshalltes Datenpaket.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parameter

*pStm*<br/>
Zeigen Sie auf einen Stream, der das zu zerstörende Datenpaket enthält.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>FtmBase::UnmarshalInterface

Initialisiert einen neu erstellten Proxy und gibt einen Schnittstellenzeiger auf diesen Proxy zurück.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parameter

*pStm*<br/>
Zeiger auf den Stream, von dem aus der Schnittstellenzeiger nicht gemarshallt werden soll.

*riid*<br/>
Verweis auf den Bezeichner der Schnittstelle, die nicht gemarshallt werden soll.

*Ppv*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird die Adresse einer Zeigervariablen, die den in *riid*angeforderten Schnittstellenzeiger empfängt. Wenn dieser Vorgang erfolgreich ist, enthält **ppv* den angeforderten Schnittstellenzeiger der Schnittstelle, die nicht gemarshallt werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_NOINTERFACE oder E_FAIL.
