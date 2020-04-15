---
title: CSimpleDialog-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleDialog
- ATLWIN/ATL::CSimpleDialog
- ATLWIN/ATL::CSimpleDialog::DoModal
helpviewer_keywords:
- CSimpleDialog class
- CSimpleDialog class, modal dialog boxes in ATL
- dialog boxes, modal
- modal dialog boxes, ATL
ms.assetid: 2ae65cc9-4f32-4168-aecd-200b4a480fdf
ms.openlocfilehash: 345372d71ad96a74bb0ae6dd7e89bdf0724cd822
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330826"
---
# <a name="csimpledialog-class"></a>CSimpleDialog-Klasse

Diese Klasse implementiert ein grundlegendes modales Dialogfeld.

## <a name="syntax"></a>Syntax

```
template <WORD t_wDlgTemplateID, BOOL t_bCenter = TRUE>
class CSimpleDialog : public CDialogImplBase
```

#### <a name="parameters"></a>Parameter

*t_wDlgTemplateID*

Die Ressourcen-ID der Dialogfeldvorlagenressource.

*t_bCenter*<br/>
TRUE, wenn das Dialogobjekt im Besitzerfenster zentriert werden soll; andernfalls FALSE.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleDialog::DoModal](#domodal)|Erstellt ein modales Dialogfeld.|

## <a name="remarks"></a>Bemerkungen

Implementiert ein modales Dialogfeld mit grundlegenden Funktionen. `CSimpleDialog`bietet nur Unterstützung für allgemeine Windows-Steuerelemente. Um ein modales Dialogfeld zu erstellen und anzuzeigen, erstellen Sie eine Instanz dieser Klasse, die den Namen einer vorhandenen Ressourcenvorlage für das Dialogfeld bereitstellt. Das Dialogfeldobjekt wird geschlossen, wenn der Benutzer auf ein Steuerelement mit einem vordefinierten Wert (z. B. IDOK oder IDCANCEL) klickt.

`CSimpleDialog`können Sie nur modale Dialogfelder erstellen. `CSimpleDialog`stellt die Dialogfeldprozedur bereit, die die Standardnachrichtenzuordnung verwendet, um Nachrichten an die entsprechenden Handler weiterzuleiten.

Weitere Informationen finden Sie unter [Implementieren eines Dialogfelds.](../../atl/implementing-a-dialog-box.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDialogImplBase`

`CSimpleDialog`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlwin.h

## <a name="csimpledialogdomodal"></a><a name="domodal"></a>CSimpleDialog::DoModal

Ruft ein modales Dialogfeld auf und gibt das Dialogfeldergebnis zurück, wenn dies der Fall ist.

```
INT_PTR DoModal(HWND hWndParent = ::GetActiveWindow());
```

### <a name="parameters"></a>Parameter

*hWndEltern*<br/>
Ein Handle für das übergeordnete Element des Dialogfelds. Wenn kein Wert angegeben wird, wird das übergeordnete Fenster auf das aktuelle aktive Fenster festgelegt.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ist der Rückgabewert die Ressourcen-ID des Steuerelements, das das Dialogfeld verworfen hat.

Wenn die Funktion fehlschlägt, ist der Rückgabewert -1. Um erweiterte Fehlerinformationen abzurufen, rufen Sie `GetLastError` auf.

### <a name="remarks"></a>Bemerkungen

Diese Methode verarbeitet die gesamte Interaktion mit dem Benutzer, während das Dialogfeld aktiv ist. Dies ist es, was das Dialogfeld modal macht; Das heißt, der Benutzer kann erst dann mit anderen Fenstern interagieren, wenn das Dialogfeld geschlossen ist.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)
