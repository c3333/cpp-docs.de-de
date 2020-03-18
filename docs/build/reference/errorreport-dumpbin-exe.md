---
title: /ERRORREPORT (dumpbin.exe)
description: Verweis auf die Befehlszeilenoption "Microsoft DUMPBIN Utility/errorreport".
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_dumpbin
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: f701c2e28dcf82194589877709bf6959de4bcbfc
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439932"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> Die/errorreport-Option ist veraltet. Ab Windows Vista wird die Fehlerberichterstattung durch [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen gesteuert.

## <a name="syntax"></a>Syntax

> **/Errorreport**\[**keine** \| **Aufforderung** \| **Warteschlange** **senden \| senden** ]

## <a name="remarks"></a>Bemerkungen

Die **/errorreport** -Argumente werden von den Windows-Fehlerberichterstattung Dienst Einstellungen überschrieben. DUMPBIN sendet automatisch Berichte interner Fehler an Microsoft, wenn die Berichterstellung durch Windows-Fehlerberichterstattung aktiviert wird. Wenn Windows-Fehlerberichterstattung deaktiviert ist, wird kein Bericht gesendet.

## <a name="see-also"></a>Weitere Informationen

[DUMPBIN-Optionen](dumpbin-options.md)
