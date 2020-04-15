---
title: '&lt;filesystem&gt;-Funktionen'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332053"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt;-Funktionen

Diese freien Funktionen im [ \<Dateisystem->-Header](../standard-library/filesystem.md) ändern und abfragen Vorgänge für Pfade, Dateien, Symlinks, Verzeichnisse und Volumes. Weitere Informationen und Codebeispiele finden Sie unter [Dateisystemnavigation (C++)](../standard-library/file-system-navigation.md).

## <a name="absolute"></a><a name="absolute"></a>Absolut

```cpp
path absolute(const path& pval, const path& base = current_path());
```

Die Funktion gibt den absoluten Pfadnamen zurück, `base`der *pval* relativ zum Pfadnamen entspricht:

1. Wenn `pval.has_root_name() && pval.has_root_directory()` die Funktion *pval*zurückgibt.

1. Wenn `pval.has_root_name() && !pval.has_root_directory()` die `pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()`Funktion zurückgibt .

1. Wenn `!pval.has_root_name() && pval.has_root_directory()` die `absolute(base).root_name()`  / Funktion *pval*zurückgibt.

1. Wenn `!pval.has_root_name() && !pval.has_root_directory()` die `absolute(base)`  / Funktion *pval*zurückgibt.

## <a name="begin"></a><a name="begin"></a>Beginnen

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

Beide Funktionen geben *iter*zurück.

## <a name="canonical"></a><a name="canonical"></a>Kanonische

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

Die Funktionen bilden alle `pabs = absolute(pval, base)` einen `pabs = absolute(pval)` absoluten Pfadnamen (oder für die Überladung ohne Basisparameter), und reduzieren ihn dann in der folgenden Reihenfolge der Schritte auf eine kanonische Form:

1. Jede `X` Pfadkomponente, `is_symlink(X)` für die `read_symlink(X)` **true** ist, wird durch ersetzt.

1. Jede Pfadkomponente `.` (Punkt ist das aktuelle Verzeichnis, das von früheren Pfadkomponenten erstellt wurde) wird entfernt.

1. Jedes Paar von `X` / `..` Pfadkomponenten (dot-dot ist das übergeordnete Verzeichnis, das von früheren Pfadkomponenten erstellt wurde) wird entfernt.

Die Funktion `pabs`gibt dann zurück.

## <a name="copy"></a><a name="copy"></a>Kopieren

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Die Funktionen alle alle möglicherweise kopieren *from* oder verknüpfen eine oder mehrere Dateien von `copy_options::none` zu *unter* Kontrolle von *opts*, die als für die Überladungen ohne *opts* Parameter genommen wird. *opts* muss höchstens eine der:

- `skip_existing`, `overwrite_existing` oder `update_existing`

- `copy_symlinks` oder `skip_symlinks`

- `directories_only`, `create_symlinks` oder `create_hard_links`

Die Funktionen bestimmen zunächst `f` die `t` file_status Werte für *von* und *für:*

- if `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`, durch Aufrufen`symlink_status`

- andernfalls, indem Sie`status`

- Andernfalls wird ein Fehler gemeldet.

Wenn `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`, melden sie dann einen Fehler (und tun nichts anderes).

Andernfalls, `is_symlink(f)` wenn dann:

- Wenn `options & copy_options::skip_symlinks`, dann nichts tun.

- Andernfalls, `!exists(t)&& options & copy_options::copy_symlinks`wenn `copy_symlink(from, to, opts)`, dann .

- Andernfalls melden Sie einen Fehler.

Andernfalls, `is_regular_file(f)`wenn , dann:

- Wenn `opts & copy_options::directories_only`, dann nichts tun.

- Andernfalls, `opts & copy_options::create_symlinks`wenn `create_symlink(to, from)`, dann .

- Andernfalls, `opts & copy_options::create_hard_links`wenn `create_hard_link(to, from)`, dann .

- Andernfalls, `is_directory(f)`wenn `copy_file(from, to`  /  `from.filename(), opts)`, dann .

- Andernfalls `copy_file(from, to, opts)`.

Andernfalls, `is_directory(f) && (opts & copy_options::recursive || !opts)`wenn , dann:

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

Andernfalls keinen weiteren Schritt ausführen.

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

Die Funktionen kopieren alle die Datei von *bis* *unter* Kontrolle von `copy_options::none` *opts*, was wie für die Überladungen ohne *opts* Parameter genommen wird. *opts* muss höchstens `skip_existing`eine `overwrite_existing`von `update_existing`enthalten, oder .

Wenn `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`, dann melden Sie als Fehler, dass die Datei bereits vorhanden ist.

Andernfalls wird `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`versucht, den Inhalt und die Attribute der Datei *in* die Datei *zu*kopieren. Wenn beim Kopierversuch ein Fehler auftritt, diesen dann melden.

Die Funktionen geben **true** zurück, wenn die Kopie versucht wird und erfolgreich ist, andernfalls **false**.

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

Wenn `is_directory(from)`, ruft `create_directory_symlink(from, to)`die Funktion auf. Andernfalls ruft `create_symlink(from, to)`es auf .

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

Für einen Pfadnamen\/wie\/a b c erstellt die\/Funktion nach Bedarf Verzeichnisse a\/und\/b, damit sie das Verzeichnis a b c nach Bedarf erstellen kann. Es gibt true nur dann **zurück,** wenn es tatsächlich das Verzeichnis *pval*erstellt.

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

Die Funktion erstellt das Verzeichnis *pval* nach Bedarf. Es gibt true nur zurück, wenn es tatsächlich das Verzeichnis *pval*erstellt, in `perms::all` diesem Fall kopiert es Berechtigungen aus der vorhandenen Datei *attr*oder verwendet für die Überladungen ohne *attr* Parameter.

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Die Funktion erstellt einen Link als Symlink zum Verzeichnis *zu*.

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

Die Funktion erstellt einen Link als hard link zu dem Verzeichnis oder der Datei *zu*.

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

Die Funktion erstellt einen *Link* als Symlink zur Datei *zu*.

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

Die Funktionen ohne Parameter *pval* geben den Pfadnamen für das aktuelle Verzeichnis zurück. Die übrigen Funktionen legen das aktuelle Verzeichnis auf *pval*fest.

## <a name="end"></a><a name="end"></a>Ende

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

Die erste `directory_iterator()` Funktion gibt zurück und die zweite Funktion gibt`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>Entsprechende

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

Die Funktionen geben **true** nur dann zurück, wenn *links* und *rechts* dieselbe Dateisystementität auswählen.

## <a name="exists"></a><a name="exists"></a>Existiert

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `status_known && stat.type() != file_not_found` zurück. Die zweite und `exists(status(pval))`dritte Funktion geben zurück.

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

Die Funktionen geben die Größe der von *pval*ausgewählten Datei in Bytes zurück, wenn `exists(pval) && is_regular_file(pval)` und die Dateigröße bestimmt werden kann. Andernfalls melden sie einen `uintmax_t(-1)`Fehler und geben zurück.

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

Die Funktion gibt die Anzahl der harten \-Links für *pval*zurück, oder 1, wenn ein Fehler auftritt.

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

Die Funktion gibt einen `pval.native()`Hashwert für zurück.

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::block` zurück. Die verbleibenden `is_block_file(status(pval))`Funktionen geben zurück.

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::character` zurück. Die verbleibenden `is_character_file(status(pval))`Funktionen geben zurück.

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::directory` zurück. Die verbleibenden `is_directory_file(status(pval))`Funktionen geben zurück.

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

Wenn `is_directory(pval)`, dann `directory_iterator(pval) == directory_iterator()`gibt die Funktion zurück ; andernfalls kehrt `file_size(pval) == 0`es zurück.

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::fifo` zurück. Die verbleibenden `is_fifo(status(pval))`Funktionen geben zurück.

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::other` zurück. Die verbleibenden `is_other(status(pval))`Funktionen geben zurück.

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::regular` zurück. Die verbleibenden `is_regular_file(status(pval))`Funktionen geben zurück.

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::socket` zurück. Die verbleibenden `is_socket(status(pval))`Funktionen geben zurück.

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

Diese erste Funktion gibt `stat.type() == file_type::symlink` zurück. Die verbleibenden `is_symlink(status(pval))`Funktionen geben zurück.

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

Die ersten beiden Funktionen geben die Zeit der `file_time_type(-1)` letzten Datenänderung für *pval*zurück, oder wenn ein Fehler auftritt. Die letzten beiden Funktionen legen die Zeit der letzten Datenänderung für *pval* auf *new_time*fest.

## <a name="permissions"></a><a name="permissions"></a>Berechtigungen

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

Die Funktionen legen die Berechtigungen für den `mask & perms::mask` von *pval* gewählten Pfadnamen unter Kontrolle von `perms & (perms::add_perms | perms::remove_perms)`fest. *Maske* muss höchstens `perms::add_perms` eine `perms::remove_perms`von und enthalten.

Wenn `mask & perms::add_perms`, legen die `status(pval).permissions() | mask & perms::mask`Funktionen die Berechtigungen auf . Andernfalls legen `mask & perms::remove_perms`die Funktionen die `status(pval).permissions() & ~(mask & perms::mask)`Berechtigungen auf , wenn , die Berechtigungen festlegen. Andernfalls legen die Funktionen `mask & perms::mask`die Berechtigungen auf fest.

## <a name="proximate"></a><a name="proximate"></a>nahe

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

Die Funktionen melden einen `path()` `!is_symlink(pval)`Fehler und geben zurück, wenn . Andernfalls geben die Funktionen ein Objekt vom Typ `path` zurück, das die symbolische Verknüpfung enthält.

## <a name="relative"></a><a name="relative"></a>Relative

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>Entfernen

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

Die Funktionen **true** geben `exists(symlink_status(pval))` true nur dann zurück, wenn die Datei erfolgreich entfernt wurde. Ein Symlink wird selbst entfernt, nicht die datei, die er wählt.

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

Wenn *pval* ein Verzeichnis ist, entfernen die Funktionen rekursiv alle Verzeichniseinträge, dann den Eintrag selbst. Andernfalls rufen die `remove`Funktionen auf. Sie geben die Anzahl aller Elemente zurück, die erfolgreich entfernt wurden.

## <a name="rename"></a><a name="rename"></a>Umbenennen

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

Die Funktionen benennen *von* *in*um. Ein Symlink wird selbst umbenannt, nicht die datei, die er wählt.

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

Die Funktionen ändern die Größe einer Datei so, dass`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>Raum

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

Die Funktion gibt Informationen über das von *pval* `space_info`gewählte Volumen in einer Struktur vom Typ zurück. Die Struktur `uintmax_t(-1)` enthält für jeden Wert, der nicht bestimmt werden kann.

## <a name="status"></a><a name="status"></a>Status

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

Die Funktionen geben den Pfadnamenstatus, den Dateityp und die Berechtigungen zurück, die *pval*zugeordnet sind. Ein Symlink selbst wird nicht getestet, sondern die von ihm gewählte Datei.

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

Die Funktion gibt`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>Swap

```cpp
void swap(path& left, path& right) noexcept;
```

Die Funktion tauscht den Inhalt von *links* und *rechts*aus.

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

Die Funktionen geben den Pfadnamen-Symlink-Status, den Dateityp und die Berechtigungen zurück, die *pval*zugeordnet sind. Die Funktionen verhalten sich `status(pval)` genauso wie mit der Ausnahme, dass ein Symlink selbst getestet wird, nicht die Datei, die er wählt.

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

Die Funktionen geben einen absoluten Pfadnamen zurück, der bei Bedarf das aktuelle Verzeichnis berücksichtigt, das seinem Stammnamen zugeordnet ist. \(Für POSIX geben `absolute(pval)`die Funktionen zurück.\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

Die Funktionen geben einen Pfadnamen für ein Verzeichnis zurück, das für die Aufnahme temporärer Dateien geeignet ist.

## <a name="u8path"></a><a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

Die erste Funktion verhält `path(source)` sich genauso wie die zweite `path(first, last)` Funktion, mit der Ausnahme, dass die jeweils gewählte Quelle als eine Folge von Char-Elementen verwendet wird, die als UTF-8 kodiert sind, unabhängig vom Dateisystem.

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
