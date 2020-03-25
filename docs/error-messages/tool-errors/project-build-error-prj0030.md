---
title: Projektbuildfehler PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 3675c3796ae37df848e458aa2db665d8c4aa7766
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192509"
---
# <a name="project-build-error-prj0030"></a>Projektbuildfehler PRJ0030

Makro Erweiterungs Fehler. Rekursion auswerten hat 32 Ebenen für $ (Makro) überschritten.

Dieser Fehler wird durch Rekursion in den Makros verursacht. Wenn Sie z. b. die Eigenschaft **zwischen Verzeichnis** (siehe [Allgemeine Eigenschaften Seite (Projekt)](../../build/reference/general-property-page-project.md)) auf $ (IntDir) festlegen, verfügen Sie über eine Rekursion.

Um diesen Fehler zu beheben, definieren Sie keine Makros oder Eigenschaften in Bezug auf Makros, die für die Definition verwendet werden.
