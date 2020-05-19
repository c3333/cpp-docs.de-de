---
title: pgomgr
ms.date: 03/14/2018
helpviewer_keywords:
- pgomgr program
- profile-guided optimizations, pgomgr
ms.assetid: 74589126-df18-42c9-8739-26d60e148d6a
ms.openlocfilehash: 4e3eb08c88db9d0ed4e47649014a600c3e0ccb78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295238"
---
# <a name="pgomgr"></a>pgomgr

Hiermit werden Profildaten von einer oder mehreren PGC-Dateien zur PGD-Datei hinzugefügt.

## <a name="syntax"></a>Syntax

> **pgomgr** [*options*] *pgcfiles* *pgdfile*

### <a name="parameters"></a>Parameter

*options*<br/>
Die folgenden Optionen können für **pgomgr** angegeben werden:

- **/help** oder **/?** Hiermit werden die verfügbaren **pgomgr**-Optionen angezeigt.

- **/clear** bewirkt, dass die PGD-Datei aus allen Profilinformationen gelöscht wird. Sie können keine PGC-Datei angegeben, wenn **/clear** angegeben ist.

- Mit **/detail** werden ausführliche Statistiken einschließlich Informationen zur Abdeckung mittels eines Flussdiagramms angezeigt.

- Mit **/summary** werden die Statistiken pro Funktion angezeigt.

- **/unique** bewirkt bei der gemeinsamen Verwendung mit **/summary**, dass dekorierte Funktionsnamen angezeigt werden. Wenn **/unique** nicht verwendet wird, dient die Standardeinstellung der Anzeige von undekorierten Funktionsnamen.

- **/merge**\[ **:** <em>n</em>] bewirkt, dass die Daten in der/den PGC-Datei(en) zur PGD-Datei hinzugefügt werden. Mit dem optionalen Parameter *n* können Sie angeben, dass die Daten *n* Mal hinzugefügt werden sollen. Wenn ein Szenario beispielsweise zur Veranschaulichung der Verwendungshäufigkeit durch Kunden in der Regel sechs Mal ausgeführt wird, können Sie es in einem Testlauf einmal ausführen und es der PGD-Datei mit **pgomgr /merge:6** sechs Mal hinzufügen.

*pgcfiles*<br/>
Hierbei handelt es sich um mindestens eine PGC-Datei, deren Profildaten Sie in der PGD-Datei zusammenführen möchten. Sie können eine einzelne oder mehrere PGC-Dateien angeben. Wenn Sie keine PGC-Dateien angeben, führt **pgomgr** alle PGC-Dateien zusammen, deren Dateinamen mit dem der PGD-Datei übereinstimmen.

*pgdfile*<br/>
Dies ist die PGD-Datei, in der Sie Daten aus den PGC-Dateien zusammenführen.

## <a name="remarks"></a>Hinweise

> [!NOTE]
> Sie können dieses Tool nur über eine Developer-Eingabeaufforderung von Visual Studio starten. Sie können es nicht von einer Systemeingabeaufforderung oder vom Datei-Explorer aus starten.

## <a name="example"></a>Beispiel

Mit diesem Beispielbefehl wird die Datei „myapp.pgd“ aus den Profildaten gelöscht:

`pgomgr /clear myapp.pgd`

Dieser Beispielbefehl fügt der PGD-Datei die Profildaten in „myapp1.pgc“ dreimal hinzu:

`pgomgr /merge:3 myapp1.pgc myapp.pgd`

In diesem Beispiel werden der Datei „myapp.pgd“ die Profildaten aus allen „myapp#.pgc“-Dateien hinzugefügt:

`pgomgr -merge myapp1.pgd`

## <a name="see-also"></a>Siehe auch

[Profilgesteuerte Optimierungen](profile-guided-optimizations.md)<br/>
[PgoAutoSweep](pgoautosweep.md)<br/>
[pgosweep](pgosweep.md)<br/>
