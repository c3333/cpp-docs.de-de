---
title: Projektbuildfehler PRJ0025
ms.date: 08/27/2018
f1_keywords:
- PRJ0025
helpviewer_keywords:
- PRJ0025
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
ms.openlocfilehash: 30445a3abc2a6ad05c983448f57ed5b93df6e61f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192353"
---
# <a name="project-build-error-prj0025"></a>Projektbuildfehler PRJ0025

> Die Batch Datei "*File*" enthält Unicode-Inhalt, der nicht in die ANSI-Codepage des Benutzers übersetzt werden konnte.
>
> *Unicode-Inhalt der Datei*

Das Projekt System hat Unicode-Inhalte in einer benutzerdefinierten Buildregel oder einem Build-Ereignis gefunden, das nicht ordnungsgemäß in die aktuelle ANSI-Codepage des Benutzers übersetzt werden kann.

Die Lösung für diesen Fehler besteht darin, den Inhalt der Buildregel oder des Buildereignisses so zu aktualisieren, dass ANSI verwendet wird, oder die Codepage auf dem Computer zu installieren und als Standardsystem festzulegen.

Weitere Informationen über benutzerdefinierte Buildschritte und Buildereignisse finden Sie Untergrund Legendes zu [benutzerdefinierten Buildschritten und Build-Ereignissen](../../build/understanding-custom-build-steps-and-build-events.md)
