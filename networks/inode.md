[[file]]
[[folder]]
У каждого файла в файловой системе есть так называемый inode — описатель файла. В inode хранится информация о файле.

В пределах одной физической файловой системы (_Помните? В Linux есть одна файловая система, которая состоит из различных физических файловых систем. В данном случае имеется в виду именно физическая файловая система._) каждый inode имеет свой уникальный номер. Таким образом, каждый файл имеет уникальный номер.

В inode хранится информация о:

- Правах доступа. Права представлены в виде набора бит.
- Уникальный номер пользователя (UID), которому принадлежит этот файл. Обратите внимание на то, что в inode хранится номер, а не имя пользователя.
- Уникальный номер группы (GID), которой принадлежит данный файл. Точно так же как и с хозяином файла, в inode хранится номер, а не имя группы.
- Временные метки:
    - Время последней модификации файла (modification time).
    - Время последнего доступа к файлу (access time). Если Вы прочитали содержимое файла, даже не изменяя его — это поле будет изменено.
    - Время последнего изменения информации в inode файла (change time). Это поле изменяет свое значение когда изменяется информация в inode. Например, при изменении прав доступа.
- Ссылки на блоки, в которых расположены данные. Данные не хранятся в inode, а располагаются в отдельных блоках на диске. Чем больше максимальный размер дискового пространства, отводимого под inode — тем больше возможное количество ссылок на блоки — тем больше максимальный размер файла.

В inode могут храниться другие атрибуты файла. Какие атрибуты будут использованы — зависит от типа файловой системы.

Современные файловые системы имеют усовершенствованную структуру. Например, ссылки на блоки могут храниться не только в inode но и в самом блоке. То есть получается ссылка на блок ссылок.

В одном блоке может храниться информация, принадлежащая нескольким файлам.

Если информация, хранящаяся в файле, может поместиться в inode, для нее не выделяют отдельный блок и ее размещают непосредственно в inode.

------------------------------------------------------------------------
Inodes (индексовые узлы) — это структура данных в файловых системах Unix и Linux, которая используется для хранения информации о файлах и каталогах. Каждый файл и каталог в файловой системе имеет свой уникальный inode, который содержит метаданные, связанные с файлом.

### Основные характеристики inodes:

1. Метаданные: Inode хранит информацию о файле, такую как:
   - Размер файла
   - Тип файла (обычный файл, каталог, символическая ссылка и т.д.)
   - Время создания, последнего доступа и модификации
   - Права доступа (чтение, запись, выполнение)
   - Ссылки на физический блок данных, где содержится сам файл.

2. Отсутствие имени файла: Inode не содержит информации о имени файла. Файловая система связывает имя файла с его inode через специальные структуры (например, каталоги).

3. Ограниченное количество: Каждая файловая система имеет ограниченное количество inodes, которое устанавливается при её создании. Если все inodes заняты, можно получить сообщение о недостатке inodes, даже если на диске есть свободное место.

4. Управление векторами: В файловых системах, таких как ext4, inodes управляют размещением блочных данных на диске, обеспечивая эффективное управление файлами и потоками данных.

### Управление inodes:

- Чтобы проверить количество занятых и свободных inodes в файловой системе, можно использовать команду:
  ```bash
  df -i
  ```

- Выводит информацию о файловой системе, включая общее количество inodes, количество занятых inodes и количество доступных inodes.