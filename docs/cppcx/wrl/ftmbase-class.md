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
ms.openlocfilehash: f28a850c365bc9a75d8e5b100e5e5cc0a1c5dc10
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404563"
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

Weitere Informationen finden Sie unter [runtimeclass-Klasse](runtimeclass-class.md).

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

| Name                         | BESCHREIBUNG                                        |
| ---------------------------- | -------------------------------------------------- |
| [Ftmbase:: ftmbase](#ftmbase) | Initialisiert eine neue Instanz der `FtmBase`-Klasse. |

### <a name="public-methods"></a>Öffentliche Methoden

| name                                                               | BESCHREIBUNG                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Ftmbase:: kreateglobalinterfaketable](#createglobalinterfacetable) | Erstellt eine globale Schnittstellen Tabelle (git).                                                                                                                              |
| [Ftmbase::D isconnectobject](#disconnectobject)                     | Erzwingt die Freigabe aller externen Verbindungen zu einem Objekt. Der Server des-Objekts ruft vor dem Herunterfahren die Implementierung dieser Methode des Objekts auf.                |
| [Ftmbase:: GetMarshalSizeMax](#getmarshalsizemax)                   | Gibt die obere Grenze für die Anzahl von Bytes an, die zum Mars Hallen des angegebenen Schnittstellen Zeigers für das angegebene Objekt benötigt werden.                                                |
| [Ftmbase:: GetUnmarshalClass](#getunmarshalclass)                   | Ruft die CLSID ab, die com verwendet, um die dll zu suchen, die den Code für den entsprechenden Proxy enthält. COM lädt diese DLL, um eine nicht initialisierte Instanz des Proxys zu erstellen. |
| [Ftmbase:: MarshalInterface](#marshalinterface)                     | Schreibt die Daten, die zum Initialisieren eines Proxy Objekts in einem Client Prozess erforderlich sind, in einen Stream.                                                                          |
| [Ftmbase:: ReleaseMarshalData](#releasemarshaldata)                 | Zerstört ein gemarshalltes Datenpaket.                                                                                                                                    |
| [Ftmbase:: UnmarshalInterface](#unmarshalinterface)                 | Initialisiert einen neu erstellten Proxy und gibt einen Schnittstellen Zeiger auf diesen Proxy zurück.                                                                                    |

### <a name="public-data-members"></a>Öffentliche Datenmember

| Name                                | BESCHREIBUNG                                       |
| ----------------------------------- | ------------------------------------------------- |
| [Ftmbase:: marshaller_](#marshaller) | Enthält einen Verweis auf den freien Thread-Mars Haller. |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`FtmBase`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** FTM. h

**Namespace:** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a>Ftmbase:: kreateglobalinterfaketable

Erstellt eine globale Schnittstellen Tabelle (git).

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>Parameter

*git*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Zeiger auf eine globale Schnittstellen Tabelle.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [`IGlobalInterfaceTable`](https://docs.microsoft.com/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable).

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a>Ftmbase::D isconnectobject

Erzwingt die Freigabe aller externen Verbindungen zu einem Objekt. Der Server des-Objekts ruft vor dem Herunterfahren die Implementierung dieser Methode des Objekts auf.

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

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a>Ftmbase:: ftmbase

Initialisiert eine neue Instanz der `FtmBase`-Klasse.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a>Ftmbase:: GetMarshalSizeMax

Gibt die obere Grenze für die Anzahl von Bytes an, die zum Mars Hallen des angegebenen Schnittstellen Zeigers für das angegebene Objekt benötigt werden.

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
Verweis auf den Bezeichner der Schnittstelle, die gemarshallt werden soll.

*teuren*<br/>
Der Schnittstellen Zeiger, der gemarshallt werden soll. kann NULL sein.

*dwdestcontext*<br/>
Ziel Kontext, in dem die angegebene Schnittstelle aus dem Marshalling entfernt werden soll.

Geben Sie mindestens einen mshctx-Enumerationswert an.

Zurzeit kann das Marshalling entweder in einem anderen Apartment des aktuellen Prozesses (MSHCTX_INPROC) oder in einem anderen Prozess auf demselben Computer wie der aktuelle Prozess (MSHCTX_LOCAL) erfolgen.

*pvdestcontext*<br/>
Für zukünftige Verwendung reserviert. muss NULL sein.

*mshlflags*<br/>
Flag, das angibt, ob die zu gemarshallten Daten zurück an den Client Prozess übertragen werden sollen – der typische Fall – oder in eine globale Tabelle geschrieben werden, wo Sie von mehreren Clients abgerufen werden kann. Geben Sie mindestens einen mshlflags-Enumerationswert an.

*Psize*<br/>
Wenn dieser Vorgang abgeschlossen ist, Zeiger auf die obere Grenze der Datenmenge, die in den marshallingstream geschrieben werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_FAIL oder E_NOINTERFACE.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a>Ftmbase:: GetUnmarshalClass

Ruft die CLSID ab, die com verwendet, um die dll zu suchen, die den Code für den entsprechenden Proxy enthält. COM lädt diese DLL, um eine nicht initialisierte Instanz des Proxys zu erstellen.

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
Verweis auf den Bezeichner der Schnittstelle, die gemarshallt werden soll.

*teuren*<br/>
Zeiger auf die-Schnittstelle, die gemarshallt werden soll. kann NULL sein, wenn der Aufrufer nicht über einen Zeiger auf die gewünschte Schnittstelle verfügt.

*dwdestcontext*<br/>
Ziel Kontext, in dem die angegebene Schnittstelle aus dem Marshalling entfernt werden soll.

Geben Sie mindestens einen mshctx-Enumerationswert an.

Das Marshalling kann entweder in einem anderen Apartment des aktuellen Prozesses (MSHCTX_INPROC) oder in einem anderen Prozess auf demselben Computer wie der aktuelle Prozess (MSHCTX_LOCAL) erfolgen.

*pvdestcontext*<br/>
Für zukünftige Verwendung reserviert. muss NULL sein.

*mshlflags*<br/>
Wenn dieser Vorgang abgeschlossen ist, Zeiger auf die CLSID, die zum Erstellen eines Proxys im Client Prozess verwendet werden soll.

*pCid*

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls S_FALSE.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a>Ftmbase:: MarshalInterface

Schreibt die Daten, die zum Initialisieren eines Proxy Objekts in einem Client Prozess erforderlich sind, in einen Stream.

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

*pstm*<br/>
Zeiger auf den Stream, der beim Marshalling verwendet werden soll.

*riid*<br/>
Verweis auf den Bezeichner der Schnittstelle, die gemarshallt werden soll. Diese Schnittstelle muss von der `IUnknown` -Schnittstelle abgeleitet werden.

*teuren*<br/>
Zeiger auf den Schnittstellen Zeiger, der gemarshallt werden soll. kann NULL sein, wenn der Aufrufer nicht über einen Zeiger auf die gewünschte Schnittstelle verfügt.

*dwdestcontext*<br/>
Ziel Kontext, in dem die angegebene Schnittstelle aus dem Marshalling entfernt werden soll.

Geben Sie mindestens einen mshctx-Enumerationswert an.

Das Marshalling kann in einem anderen Apartment des aktuellen Prozesses (MSHCTX_INPROC) oder in einem anderen Prozess auf demselben Computer wie der aktuelle Prozess (MSHCTX_LOCAL) erfolgen.

*pvdestcontext*<br/>
Für die zukünftige Verwendung reserviert. Muss 0 (null) sein.

*mshlflags*<br/>
Gibt an, ob die zu gemarshallten Daten zurück an den Client Prozess übertragen werden sollen – der typische Fall – oder in eine globale Tabelle geschrieben werden, wo Sie von mehreren Clients abgerufen werden kann.

### <a name="return-value"></a>Rückgabewert

, S_OK der Schnittstellen Zeiger erfolgreich gemarshallt wurde.

E_NOINTERFACE die angegebene Schnittstelle nicht unterstützt wird.

STG_E_MEDIUMFULL der Stream voll ist.

E_FAIL Vorgang ist fehlgeschlagen.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a>Ftmbase:: marshaller_

Enthält einen Verweis auf den freien Thread-Mars Haller.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a>Ftmbase:: ReleaseMarshalData

Zerstört ein gemarshalltes Datenpaket.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>Parameter

*pstm*<br/>
Zeiger auf einen Stream, der das zu zerstörende Datenpaket enthält.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a>Ftmbase:: UnmarshalInterface

Initialisiert einen neu erstellten Proxy und gibt einen Schnittstellen Zeiger auf diesen Proxy zurück.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>Parameter

*pstm*<br/>
Ein Zeiger auf den Stream, aus dem der Schnittstellen Zeiger nicht gemarshallt werden soll.

*riid*<br/>
Verweis auf den Bezeichner der Schnittstelle, die gemarshallt werden soll.

*PPV*<br/>
Wenn dieser Vorgang abgeschlossen ist, die Adresse einer Zeiger Variablen, die den in *riid*angeforderten Schnittstellen Zeiger empfängt. Wenn dieser Vorgang erfolgreich ist, enthält **PPV* den angeforderten Schnittstellen Zeiger der Schnittstelle, die gemarshallt werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_NOINTERFACE oder E_FAIL.
