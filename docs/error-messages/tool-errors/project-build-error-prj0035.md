---
title: Projektbuildfehler PRJ0035
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: 8486c4f62f637f6f7e9826a289c21f8f194eb9f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192171"
---
# <a name="project-build-error-prj0035"></a>Projektbuildfehler PRJ0035

> Die XML-Datei "*File*" enthält Unicode-Inhalt, der nicht in die ANSI-Codepage des Benutzers übersetzt werden konnte.
>
> *Unicode-Inhalt der Datei*

*File* ist die XML-Datei, die als Befehlszeile für das Webbereitstellungs Tool erstellt wird.

Das Projekt System hat Unicode-Zeichen in einer Eigenschaft auf der Eigenschaften Seite der Webbereitstellung gefunden, die nicht ordnungsgemäß in ANSI übersetzt werden kann.

Die Lösung für diesen Fehler besteht darin, den Inhalt der-Eigenschaft so zu aktualisieren, dass ANSI verwendet wird, oder die Codepage auf dem Computer zu installieren und als Standardsystem festzulegen.
