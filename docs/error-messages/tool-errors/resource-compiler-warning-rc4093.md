---
title: 'Ressourcencompiler: Warnung RC4093'
ms.date: 11/04/2016
f1_keywords:
- RC4093
helpviewer_keywords:
- RC4093
ms.assetid: 3c61b4a4-b418-465b-a4fd-cb1ff0adb8dd
ms.openlocfilehash: 29d24f1e380f5c531e170e5dc23cf5c77eefb874
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182291"
---
# <a name="resource-compiler-warning-rc4093"></a>Ressourcencompiler: Warnung RC4093

Escapezeichen ohne Escapezeichen in einer Zeichen Konstante im inaktiven Code

Der Konstante Ausdruck einer `#if`-, `#elif`-, **#ifdef**-oder **#ifndef** Präprozessordirektive, die auf 0 (null) ausgewertet wird, sodass der nachfolgende Code inaktiv Innerhalb dieses inaktiven Codes wird ein Zeilen vorzeitiges Zeichen innerhalb eines Satzes von einfachen oder doppelten Anführungszeichen angezeigt.

Der gesamte Text bis zum nächsten doppelten Anführungszeichen galt als innerhalb einer Zeichen Konstante.
