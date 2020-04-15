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
ms.openlocfilehash: 98943fe294322715723bd91207a6f3320ca1ffb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329465"
---
# <a name="iregistrar-interface"></a>IRegistrar-Schnittstelle

Diese Schnittstelle ist in atliface.h definiert und wird intern von CAtlModule-Memberfunktionen wie [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)verwendet.

## <a name="syntax"></a>Syntax

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie im Thema [Verwenden ersetzbarer Parameter (Präprozessor des Registrars).](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[IRegistrar::ResourceRegisterSz](#resourceregistersz)|Registriert die Ressource. |
|[IRegistrar::ResourceUnregisterSz](#resourceunregistersz)| Wird die Registrierung der Ressource aufheben.|
|[IRegistrar::FileRegister](#fileregister)|Registriert die Datei.|
|[IRegistrar::FileUnregister](#fileunregister)|Die Registrierung der Datei wird aufheben.|
|[IRegistrar::StringRegister](#stringregister)|Registriert die Zeichenfolge.|
|[IRegistrar::StringUnregister](#stringunregister)|Die Registrierung der Zeichenfolge wird aufheben.|
|[IRegistrar::ResourceRegister](#resourceregister)|Registriert die Ressource.|
|[IRegistrar::ResourceUnregister](#resourceunregister)|Wird die Registrierung der Ressource aufheben.|

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlifase.h

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a>IRegistrar::ResourceRegisterSz

Registriert die Ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a>IRegistrar::ResourceUnregisterSz

Wird die Registrierung der Ressource aufheben.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a>IRegistrar::FileRegister

Registriert die Datei.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a>IRegistrar::FileUnregister

Die Registrierung der Datei wird aufheben.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a>IRegistrar::StringRegister

Registriert die angegebenen Zeichenfolgendaten.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a>IRegistrar::StringUnregister

Heben Sie die Registrierung der angegebenen Zeichenfolgendaten auf.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a>IRegistrar::ResourceRegister

Registriert die Ressource.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a>IRegistrar::ResourceUnregister

Wird die Registrierung der Ressource aufheben.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>Siehe auch

[Verwenden austauschbarer Parameter (Präprozessor des Registrars)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)<br/>
[Modulklassen](../../atl/atl-module-classes.md)<br/>
[Registrierungskomponente (Registrar)](../../atl/atl-registry-component-registrar.md)
