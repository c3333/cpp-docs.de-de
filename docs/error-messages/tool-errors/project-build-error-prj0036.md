---
title: Projektbuildfehler PRJ0036
ms.date: 11/04/2016
f1_keywords:
- PRJ0036
helpviewer_keywords:
- PRJ0036
ms.assetid: ee215cd1-2d66-474d-9a63-b9096f1c4923
ms.openlocfilehash: 67a225f907d06cd240ec2ebef236c0b4e0b849e2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192098"
---
# <a name="project-build-error-prj0036"></a>Projektbuildfehler PRJ0036

Die Eigenschaft "zusätzliche Dateien" für das Webbereitstellungs Tool enthielt einen ungültigen Eintrag.

Die Eigenschaft zusätzliche Dateien auf der Eigenschaften Seite für die Webbereitstellung enthielt einen Fehler, möglicherweise aufgrund eines Makro Evaluierungs Problems. Dieser Fehler kann auch bedeuten, dass der Pfad falsch formatiert ist und Zeichen oder Zeichenkombinationen enthält, die in einem Dateipfad unzulässig sind.

Um diesen Fehler zu beheben, korrigieren Sie das Makro, oder korrigieren Sie die Pfadspezifikation. Der ausgewertete Pfad ist ein absoluter Pfad aus dem Projektverzeichnis.

Dieser Fehler kann auch bedeuten, dass eine der Dateien, auf die verwiesen wird, nicht vorhanden ist.
