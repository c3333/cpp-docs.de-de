---
title: IRegistrar-Schnittstelle
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: e347bdba1656a53cd705123a26650dad50d3892f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857141"
---
# <a name="iregistrar-interface"></a>IRegistrar-Schnittstelle

Diese Schnittstelle ist in atliface. h definiert und wird intern von den Element Funktionen von " [UpdateRegistryFromResource](catlmodule-class.md#updateregistryfromresourced)" verwendet.

## <a name="syntax"></a>Syntax

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden [Sie im Thema Verwenden von ersetzbaren Parametern (Präprozessor der Registrierungsstelle)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) .

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IRegistrar:: ResourceRegisterSz](#resourceregistersz)|Registriert die Ressource. |
|[IRegistrar:: ResourceUnregisterSz](#resourceunregistersz)| Hebt die Registrierung der Ressource auf.|
|[IRegistrar:: fileregiester](#fileregister)|Registriert die Datei.|
|[Iregistrierungs:: fileunregister](#fileunregister)|Hebt die Registrierung der Datei auf.|
|[IRegistrar:: stringregister](#stringregister)|Registriert die Zeichenfolge.|
|[IRegistrar:: stringunregister](#stringunregister)|Hebt die Registrierung der Zeichenfolge auf|
|[IRegistrar:: resourceregiester](#resourceregister)|Registriert die Ressource.|
|[Iregistrierungs:: ResourceUnregister](#resourceunregister)|Hebt die Registrierung der Ressource auf.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atlif. h

##  <a name="resourceregistersz"></a>IRegistrar:: ResourceRegisterSz

Registriert die Ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregistersz"></a>IRegistrar:: ResourceUnregisterSz

Hebt die Registrierung der Ressource auf.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="fileregister"></a>IRegistrar:: fileregiester

Registriert die Datei.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="fileunregister"></a>Iregistrierungs:: fileunregister

Hebt die Registrierung der Datei auf.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

##  <a name="stringregister"></a>IRegistrar:: stringregister

Registriert die angegebenen Zeichen folgen Daten.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="stringunregister"></a>IRegistrar:: stringunregister

Hebt die Registrierung der angegebenen Zeichen folgen Daten auf.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

##  <a name="resourceregister"></a>IRegistrar:: resourceregiester

Registriert die Ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

##  <a name="resourceunregister"></a>Iregistrierungs:: ResourceUnregister

Hebt die Registrierung der Ressource auf.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Weitere Informationen

[Verwenden von ersetzbaren Parametern (Der Registrierungspräprozessor)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Klassen Übersicht](../../atl/atl-class-overview.md)<br/>
[Modul Klassen](../../atl/atl-module-classes.md)<br/>
[Registrierungskomponente (Registrar)](../../atl/atl-registry-component-registrar.md)
