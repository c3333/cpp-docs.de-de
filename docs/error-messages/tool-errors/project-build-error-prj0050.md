---
title: Projektbuildfehler PRJ0050
ms.date: 11/04/2016
f1_keywords:
- PRJ0050
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
ms.openlocfilehash: 56e092b5f7c33ad9543951621b2a9d8f6992331f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191989"
---
# <a name="project-build-error-prj0050"></a>Projektbuildfehler PRJ0050

Fehler beim Registrieren der Ausgabe. Stellen Sie sicher, dass Sie über die erforderlichen Berechtigungen zum Ändern der Registrierung verfügen.

Das Visual C++ Build-System konnte die Ausgabe des Builds (dll oder exe) nicht registrieren. Sie müssen als Administrator angemeldet sein, um die Registrierung zu ändern.

Wenn Sie eine DLL-Datei erstellen, können Sie versuchen, die DLL-Datei manuell mithilfe von regsvr32. exe zu registrieren. Dadurch werden Informationen dazu angezeigt, warum der Build fehlgeschlagen ist.

Wenn Sie keine DLL-Datei erstellen, überprüfen Sie das Buildprotokoll nach dem Befehl, der einen Fehler verursacht.
