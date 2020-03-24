---
title: Projektbuildfehler PRJ0009
ms.date: 11/04/2016
f1_keywords:
- PRJ0009
helpviewer_keywords:
- PRJ0009
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
ms.openlocfilehash: d02325504b04a13cd15dee0bd70891bf5a63b62e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192961"
---
# <a name="project-build-error-prj0009"></a>Projektbuildfehler PRJ0009

Das Buildprotokoll konnte nicht zum Schreiben geöffnet werden.

**Stellen Sie sicher, dass die Datei nicht von einem anderen Prozess geöffnet ist und nicht schreibgeschützt ist.**

Nachdem Sie die Eigenschaft Buildprotokollierung auf **Ja** festgelegt und einen Build oder C++ eine Neuerstellung durchgeführt haben, konnte Visual das Buildprotokoll im exklusiven Modus nicht öffnen. **Build Logging**

Überprüfen Sie die Einstellung für die **Buildprotokollierung** , indem Sie das Dialogfeld **Optionen** öffnen (Klicken Sie **im Menü Extras** auf den Befehl **Optionen** ), und wählen Sie dann **VC + + Build** im **Projekt** Ordner aus. Die Builddatei heißt BuildLog. htm und wird in das zwischen Verzeichnis $ (IntDir) geschrieben.

Mögliche Ursachen für diesen Fehler:

- Sie führen zwei visuelle C++ Verfahren aus und versuchen, dieselbe Konfiguration desselben Projekts gleichzeitig zu erstellen.

- Die Buildprotokollierung wird in einem Prozess geöffnet, der die Datei sperrt.

- Der Benutzer verfügt nicht über die Berechtigung zum Erstellen einer Datei.

- Der aktuelle Benutzer verfügt nicht über Schreibzugriff auf die Datei "BuildLog. htm".
