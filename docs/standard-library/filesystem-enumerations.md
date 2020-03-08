---
title: '&lt;filesystem&gt;-Enumerationen'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: f148347cd132a604622415c65bb3e0352f5308eb
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875824"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt;-Enumerationen

In diesem Thema werden die Enumerationen filesystem-Header beschrieben.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** \<experimentellen/Dateisystem >

**Namespace:** std::experimental::filesystem

## <a name="copy_options"></a> copy_options

Eine Enumeration von Bitmaskenwerten, die mit den Funktionen [copy](filesystem-functions.md#copy) und [copy_file](filesystem-functions.md#copy_file) verwendet wird, um Verhalten anzugeben.

### <a name="syntax"></a>Syntax

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>Werte

|`Name`|BESCHREIBUNG|
|------------|-----------------|
|`none`|Führen Sie das Standardverhalten für diesen Vorgang aus.|
|`skip_existing`|Erstellen Sie keine Kopie, wenn die Datei bereits vorhanden ist. Melden Sie auch keinen Fehler.|
|`overwrite_existing`|Überschreiben Sie die Datei, wenn sie bereits vorhanden ist.|
|`update_existing`|Überschreiben Sie die Datei, wenn sie bereits vorhanden und älter als die neue ist.|
|`recursive`|Kopieren Sie die Unterverzeichnisse und deren Inhalt rekursiv.|
|`copy_symlinks`|Kopieren Sie symbolische Links als symbolische Verknüpfungen, statt die Dateien zu kopieren, auf die sie zeigen.|
|`skip_symlinks`|Ignorieren Sie symbolische Verknüpfungen.|
|`directories_only`|Nehmen Sie Iterationen nur für Verzeichnisse vor, ignorieren Sie Dateien.|
|`create_symlinks`|Erstellen Sie symbolische Links, anstatt Dateien zu kopieren. Ein absoluter Pfad muss als Quellpfad verwendet werden, es sei denn, das Ziel ist das aktuelle Verzeichnis.|
|`create_hard_links`|Erstellen Sie feste Links, anstatt Dateien zu kopieren.|

## <a name="directory_options"></a> directory_options

Gibt an, ob symbolischen Verknüpfungen zu Verzeichnissen gefolgt oder ob diese ignoriert werden sollen.

### <a name="syntax"></a>Syntax

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>Werte

|Name|BESCHREIBUNG|
|----------|-----------------|
|`none`|Standardverhalten: symbolische Verknüpfungen auf Verzeichnisse ignorieren. „Berechtigung verweigert“ ist ein Fehler.|
|`follow_directory_symlink`|Symbolische Verknüpfungen zu Verzeichnissen als tatsächliche Verzeichnisse behandeln.|

## <a name="file_type"></a> file_type

Eine Enumeration für Dateitypen. Die unterstützten Werte sind regulär, Verzeichnis, NOT_FOUND und unbekannt.

### <a name="syntax"></a>Syntax

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>Werte

|Name|value|BESCHREIBUNG|
|----------|-----------|-----------------|
|`not_found`|-1|Stellt eine nicht vorhandene Datei dar.|
|`none`|0|Stellt eine Datei dar, die über kein Typattribut verfügt. (Nicht unterstützt.)|
|`regular`|1|Stellt eine herkömmliche Datenträgerdatei dar.|
|`directory`|2|Stellt ein Verzeichnis dar.|
|`symlink`|3|Stellt eine symbolische Verknüpfung dar. (Nicht unterstützt.)|
|`block`|4|Stellt eine blockspezifische Datei auf UNIX-basierten Systemen dar. (Nicht unterstützt.)|
|`character`|5|Stellt eine zeichenspezifische Datei auf UNIX-basierten Systemen dar. (Nicht unterstützt.)|
|`fifo`|6|Stellt eine FIFO-Datei auf UNIX-basierten Systemen dar. (Nicht unterstützt.)|
|`socket`|7|Stellt ein Socket auf UNIX-basierten Systemen dar. (Nicht unterstützt.)|
|`unknown`|8|Stellt eine Datei dar, deren Status nicht ermittelt werden kann.|

## <a name="perm_options"></a>perm_options

Enthält Werte `replace`, `add`, `remove`und `nofollow`.

```cpp
enum class perm_options;
```

## <a name="perms"></a> perms

Flags für Dateiberechtigungen. Die unterstützten Werte sind im wesentlichen "schreibgeschützt" und "alle". Bei einer schreibgeschützten Datei sind keine *_write-Bits festgelegt. Andernfalls wird das `all` -Bit (0x0777) festgelegt.

### <a name="syntax"></a>Syntax

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
