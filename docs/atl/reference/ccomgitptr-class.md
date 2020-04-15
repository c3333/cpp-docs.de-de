---
title: CComGITPtr-Klasse
ms.date: 11/04/2016
f1_keywords:
- CComGITPtr
- ATLBASE/ATL::CComGITPtr
- ATLBASE/ATL::CComGITPtr::CComGITPtr
- ATLBASE/ATL::CComGITPtr::Attach
- ATLBASE/ATL::CComGITPtr::CopyTo
- ATLBASE/ATL::CComGITPtr::Detach
- ATLBASE/ATL::CComGITPtr::GetCookie
- ATLBASE/ATL::CComGITPtr::Revoke
- ATLBASE/ATL::CComGITPtr::m_dwCookie
helpviewer_keywords:
- CComGITPtr class
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
ms.openlocfilehash: 230eeb1577189d2057e530e1df8ef99c611fb32b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327839"
---
# <a name="ccomgitptr-class"></a>CComGITPtr-Klasse

Diese Klasse stellt Methoden für den Umgang mit Schnittstellenzeigern und der globalen Schnittstellentabelle (GIT) bereit.

## <a name="syntax"></a>Syntax

```
template <class T>
class CComGITPtr
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Schnittstellenzeigers, der im GIT gespeichert werden soll.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComGITPtr::CComGITPtr](#ccomgitptr)|Der Konstruktor.|
|[CComGITPtr::'CComGITPtr](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComGITPtr::Anfügen](#attach)|Rufen Sie diese Methode auf, um den Schnittstellenzeiger in der globalen Schnittstellentabelle (GIT) zu registrieren.|
|[CComGITPtr::CopyTo](#copyto)|Rufen Sie diese Methode auf, um die Schnittstelle aus der globalen Schnittstellentabelle (GIT) in den übergebenen Zeiger zu kopieren.|
|[CComGITPtr::Detach](#detach)|Rufen Sie diese Methode auf, `CComGITPtr` um die Zuordnung der Schnittstelle vom Objekt zu trennen.|
|[CComGITPtr::GetCookie](#getcookie)|Rufen Sie diese Methode auf, um das Cookie vom `CComGITPtr` Objekt zurückzugeben.|
|[CComGITPtr::Widerrufen](#revoke)|Rufen Sie diese Methode auf, um die Schnittstelle aus der globalen Schnittstellentabelle (GIT) zu entfernen.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComGITPtr::operator DWORD](#operator_dword)|Gibt das Cookie `CComGITPtr` aus dem Objekt zurück.|
|[CComGITPtr::Operator =](#operator_eq)|Zuweisungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComGITPtr::m_dwCookie](#m_dwcookie)|Das Cookie.|

## <a name="remarks"></a>Bemerkungen

Objekte, die den Freithread-Marshaller aggregieren und Schnittstellenzeiger verwenden müssen, die von anderen Objekten abgerufen werden, müssen zusätzliche Schritte ausführen, um sicherzustellen, dass die Schnittstellen ordnungsgemäß gemarshallt sind. In der Regel umfasst dies das Speichern der Schnittstellenzeiger im GIT und das Abrufen des Zeigers aus dem GIT bei jeder Verwendung. Die `CComGITPtr` Klasse wird bereitgestellt, um Ihnen bei der Verwendung von Im GIT gespeicherten Schnittstellenzeigern zu helfen.

> [!NOTE]
> Die globale Schnittstellentabellenfunktion ist nur unter Windows 95 mit DCOM Version 1.1 und höher, Windows 98, Windows NT 4.0 mit Service Pack 3 und höher und Windows 2000 verfügbar.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlbase.h

## <a name="ccomgitptrattach"></a><a name="attach"></a>CComGITPtr::Anfügen

Rufen Sie diese Methode auf, um den Schnittstellenzeiger in der globalen Schnittstellentabelle (GIT) zu registrieren.

```
HRESULT Attach(T* p) throw();

HRESULT Attach(DWORD dwCookie) throw();
```

### <a name="parameters"></a>Parameter

*P*<br/>
Der Schnittstellenzeiger, der dem GIT hinzugefügt werden soll.

*dwCookie*<br/>
Das Cookie, das zum Identifizieren des Schnittstellenzeigers verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds tritt ein Assertionsfehler auf, wenn der GIT ungültig ist oder wenn das Cookie gleich NULL ist.

## <a name="ccomgitptrccomgitptr"></a><a name="ccomgitptr"></a>CComGITPtr::CComGITPtr

Der Konstruktor.

```
CComGITPtr() throw();
CComGITPtr(T* p);
CComGITPtr(const CComGITPtr& git);
explicit CComGITPtr(DWORD dwCookie) throw();
CComGITPtr(CComGITPtr&& rv);
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Ein Schnittstellenzeiger, der in der globalen Schnittstellentabelle (GIT) gespeichert werden soll.

*Git*<br/>
[in] Ein Verweis auf `CComGITPtr` ein vorhandenes Objekt.

*dwCookie*<br/>
[in] Ein Cookie, das zum Identifizieren des Schnittstellenzeigers verwendet wird.

*Rv*<br/>
[in] Das `CComGITPtr` Quellobjekt, aus dem Daten verschoben werden sollen.

### <a name="remarks"></a>Bemerkungen

Erstellt ein `CComGITPtr` neues Objekt, optional `CComGITPtr` mit einem vorhandenen Objekt.

Der Konstruktor, der *rv* verwendet, ist ein Verschiebungskonstruktor. Die Daten werden von der Quelle *rv*verschoben und dann *rv* gelöscht.

## <a name="ccomgitptrccomgitptr"></a><a name="dtor"></a>CComGITPtr::'CComGITPtr

Der Destruktor.

```
~CComGITPtr() throw();
```

### <a name="remarks"></a>Bemerkungen

Entfernt die Schnittstelle aus der globalen Schnittstellentabelle (Global Interface Table, GIT) mit [CComGITPtr::Revoke](#revoke).

## <a name="ccomgitptrcopyto"></a><a name="copyto"></a>CComGITPtr::CopyTo

Rufen Sie diese Methode auf, um die Schnittstelle aus der globalen Schnittstellentabelle (GIT) in den übergebenen Zeiger zu kopieren.

```
HRESULT CopyTo(T** pp) const throw();
```

### <a name="parameters"></a>Parameter

*Pp*<br/>
Der Zeiger, der die Schnittstelle empfangen soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die Schnittstelle aus dem GIT wird in den übergebenen Zeiger kopiert. Der Zeiger muss vom Aufrufer freigegeben werden, wenn er nicht mehr benötigt wird.

## <a name="ccomgitptrdetach"></a><a name="detach"></a>CComGITPtr::Detach

Rufen Sie diese Methode auf, `CComGITPtr` um die Zuordnung der Schnittstelle vom Objekt zu trennen.

```
DWORD Detach() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt das Cookie `CComGITPtr` aus dem Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Es liegt am Aufrufer, die Schnittstelle aus dem GIT zu entfernen, indem [CComGITPtr::Revoke verwendet](#revoke)wird.

## <a name="ccomgitptrgetcookie"></a><a name="getcookie"></a>CComGITPtr::GetCookie

Rufen Sie diese Methode auf, um das Cookie vom `CComGITPtr` Objekt zurückzugeben.

```
DWORD GetCookie() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt das Cookie zurück.

### <a name="remarks"></a>Bemerkungen

Das Cookie ist eine Variable, die verwendet wird, um eine Schnittstelle und ihren Speicherort zu identifizieren.

## <a name="ccomgitptrm_dwcookie"></a><a name="m_dwcookie"></a>CComGITPtr::m_dwCookie

Das Cookie.

```
DWORD m_dwCookie;
```

### <a name="remarks"></a>Bemerkungen

Das Cookie ist eine Membervariable, die verwendet wird, um eine Schnittstelle und ihren Speicherort zu identifizieren.

## <a name="ccomgitptroperator-"></a><a name="operator_eq"></a>CComGITPtr::Operator =

Der Zuweisungsoperator.

```
CComGITPtr& operator= (T* p);
CComGITPtr& operator= (const CComGITPtr& git);
CComGITPtr& operator= (DWORD dwCookie);
CComGITPtr& operator= (CComGITPtr&& rv);
```

### <a name="parameters"></a>Parameter

*P*<br/>
[in] Ein Zeiger auf eine Schnittstelle.

*Git*<br/>
[in] Ein Verweis `CComGITPtr` auf ein Objekt.

*dwCookie*<br/>
[in] Ein Cookie, das zum Identifizieren des Schnittstellenzeigers verwendet wird.

*Rv*<br/>
[in] Der `CComGITPtr` zum Verschieben von Daten.

### <a name="return-value"></a>Rückgabewert

Gibt das `CComGITPtr` aktualisierte Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Weist einem `CComGITPtr` Objekt einen neuen Wert zu, entweder aus einem vorhandenen Objekt oder aus einem Verweis auf eine globale Schnittstellentabelle.

## <a name="ccomgitptroperator-dword"></a><a name="operator_dword"></a>CComGITPtr::operator DWORD

Gibt das dem `CComGITPtr` Objekt zugeordnete Cookie zurück.

```
operator DWORD() const;
```

### <a name="remarks"></a>Bemerkungen

Das Cookie ist eine Variable, die verwendet wird, um eine Schnittstelle und ihren Speicherort zu identifizieren.

## <a name="ccomgitptrrevoke"></a><a name="revoke"></a>CComGITPtr::Widerrufen

Rufen Sie diese Methode auf, um die aktuelle Schnittstelle aus der globalen Schnittstellentabelle (GIT) zu entfernen.

```
HRESULT Revoke() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Entfernt die Schnittstelle aus dem GIT.

## <a name="see-also"></a>Siehe auch

[Freethreaded Marshaller](../../atl/atl-and-the-free-threaded-marshaler.md)<br/>
[Zugriff auf Schnittstellen in den Wohnungen](/windows/win32/com/accessing-interfaces-across-apartments)<br/>
[Verwendung der globalen Schnittstellentabelle](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)
