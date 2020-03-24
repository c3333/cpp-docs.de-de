---
title: 'CVTRES: Schwerwiegender Fehler CVT1100'
ms.date: 11/04/2016
f1_keywords:
- CVT1100
helpviewer_keywords:
- CVT1100
ms.assetid: 886e88dd-5818-4b5f-84f2-d2a3d75f0aaf
ms.openlocfilehash: b7e67df24d41b1e8826673146fcc27fd93d143fd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196546"
---
# <a name="cvtres-fatal-error-cvt1100"></a>CVTRES: Schwerwiegender Fehler CVT1100

doppelte Ressource – Typ: Typ, Name: Name, Sprache: Sprache, Flags: Flags, Größe: Größe

Die angegebene Ressource wurde mehrmals angegeben.

Dieser Fehler kann angezeigt werden, wenn der Linker eine Typbibliothek erstellt und Sie [/TLBID](../../build/reference/tlbid-specify-resource-id-for-typelib.md) nicht angegeben haben und eine Ressource in Ihrem Projekt bereits 1 verwendet. Geben Sie in diesem Fall/TLBID an, und geben Sie eine andere Zahl bis 65535 an.
