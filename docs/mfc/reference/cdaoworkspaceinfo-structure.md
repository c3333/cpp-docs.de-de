---
title: CDaoWorkspaceInfo-Struktur
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253630"
---
# <a name="cdaoworkspaceinfo-structure"></a>CDaoWorkspaceInfo-Struktur

Die `CDaoWorkspaceInfo` Struktur enthält Informationen über einen Arbeitsbereich für den Datenbankzugriff für Data Access Objects (DAO) definiert.

## <a name="syntax"></a>Syntax

```
struct CDaoWorkspaceInfo
{
    CString m_strName;           // Primary
    CString m_strUserName;       // Secondary
    BOOL m_bIsolateODBCTrans;    // All
};
```

#### <a name="parameters"></a>Parameter

*m_strName*<br/>
Den Namen eindeutig im Workspace-Objekts. Um den Wert dieser Eigenschaft direkt zu abzurufen, rufen Sie des Querydef-Objekts [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) Member-Funktion. Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in-DAO-Hilfe.

*m_strUserName*<br/>
Ein Wert, der den Besitzer eines Arbeitsbereichs-Objekts darstellt. Weitere Informationen finden Sie unter dem Thema "UserName-Eigenschaft" in-DAO-Hilfe.

*m_bIsolateODBCTrans*<br/>
Ein Wert, der angibt, ob mehrere Transaktionen, bei denen die gleiche ODBC-Datenbank isoliert werden. Weitere Informationen finden Sie unter [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Verwandte Informationen finden Sie im Thema "IsolateODBCTrans-Eigenschaft" in-DAO-Hilfe.

## <a name="remarks"></a>Hinweise

Der Arbeitsbereich ist ein Objekt der Klasse [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). Die Verweise auf die primäre, sekundäre und alle oben angegeben, wie die Informationen zurückgegeben werden, indem die [GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) Memberfunktion in Klasse `CDaoWorkspace`.

Informationen, die abgerufen, indem die [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) Member-Funktion befindet sich in einem `CDaoWorkspaceInfo` Struktur. `CDaoWorkspaceInfo` definiert auch eine `Dump` -Memberfunktion im Debug-builds. Können Sie `Dump` zum Sichern den Inhalt einer `CDaoWorkspaceInfo` Objekt.

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

## <a name="see-also"></a>Siehe auch

[Strukturen, Stile, Rückrufe und Meldungszuordnungen](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDaoWorkspace-Klasse](../../mfc/reference/cdaoworkspace-class.md)
