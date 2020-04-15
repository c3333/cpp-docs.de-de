---
title: CMenuTearOffManager-Klasse
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: f41937179dc055213f3af093e107bcb08c8a8fcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369965"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager-Klasse

Verwaltet abtrennbare Menüs. Ein abtrennbares Menü ist ein Menü in der Menüleiste. Der Benutzer kann ein solches Menü von der Menüleiste abtrennen, wodurch das Menü beliebig positionierbar wird.

   Weitere Informationen finden Sie im Quellcode im **Ordner VC\\atlmfc\\src\\mfc** Ihrer Visual Studio-Installation.

## <a name="syntax"></a>Syntax

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMenuTearoffManager::CMenuTearOffManager](#cmenutearoffmanager)|Erstellt ein `CMenuTearOffManager`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMenuTearOffManager::Build](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Initialisieren](#initialize)|Initialisiert ein `CMenuTearOffManager`-Objekt.|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenutearoffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Bemerkungen

Um Abreißmenüs in Ihrer Anwendung verwenden zu `CMenuTearOffManager` können, benötigen Sie ein Objekt. In den meisten Fällen erstellen oder initialisieren Sie ein `CMenuTearOffManager` Objekt nicht direkt. Dies wird für Sie behandelt, wenn Sie die [CWinAppEx::EnableTearOffMenus-Funktion](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) aufrufen.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, `CMenuTearOffManager` wie ein `CWinAppEX::EnableTearOffMenus` Objekt durch Aufrufen der Methode erstellt und initialisiert wird. Dieser Codeausschnitt ist Teil des [WordPad-Beispiels](../../overview/visual-cpp-samples.md).

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxmenutearoffmanager.h

## <a name="cmenutearoffmanagerbuild"></a><a name="build"></a>CMenuTearOffManager::Build

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>Parameter

[in] *uiTearOffBarID*<br/>

[in] *strText*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmenutearoffmanagercmenutearoffmanager"></a><a name="cmenutearoffmanager"></a>CMenuTearoffManager::CMenuTearOffManager

Erstellt ein [CMenuTearOffManager-Objekt.](../../mfc/reference/cmenutearoffmanager-class.md)

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Bemerkungen

In den meisten Fällen sollten `CMenuTearOffManager` Sie keine manuell erstellen. Das Framework Ihrer Anwendung `CMenuTearOffManager` erstellt das Objekt, wenn Sie [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)aufrufen.

## <a name="cmenutearoffmanagergetregpath"></a><a name="getregpath"></a>CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmenutearoffmanagerinitialize"></a><a name="initialize"></a>CMenuTearOffManager::Initialisieren

Initialisiert ein [CMenuTearOffManager-Objekt.](../../mfc/reference/cmenutearoffmanager-class.md)

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>Parameter

*lpszRegEntry*<br/>
[in] Eine Zeichenfolge, die den Pfad eines Registrierungseintrags enthält. Ihre Anwendungen speichern die Einstellungen für Abreißbalken in diesem Registrierungseintrag.

*uiTearOffMenuFirst*<br/>
[in] Die erste Menü-ID für ein Abreißmenü.

*uiTearOffMenuLast*<br/>
[in] Die letzte Menü-ID für ein Abreißmenü.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Bereich der Menü-IDs von *uiTearOffMenuFirst* bis *uiTearOffMenuLast* muss ein kontinuierliches Intervall sein. Das Intervall definiert die Anzahl der Abreißmenüs, die gleichzeitig in der Anwendung angezeigt werden können.

## <a name="cmenutearoffmanagerisdynamicid"></a><a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>Parameter

[in] *uiID*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmenutearoffmanagerparse"></a><a name="parse"></a>CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>Parameter

[in] *str*<br/>

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

## <a name="cmenutearoffmanagerreset"></a><a name="reset"></a>CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>Parameter

[in] *hmenu*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmenutearoffmanagersetinuse"></a><a name="setinuse"></a>CMenutearoffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>Parameter

[in] *uiCmdId*<br/>

[in] *bVerwenden*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="cmenutearoffmanagersetuptearoffmenus"></a><a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>Parameter

[in] *hMenu*<br/>

### <a name="remarks"></a>Bemerkungen

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[Klassen](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx-Klasse](../../mfc/reference/cwinappex-class.md)
