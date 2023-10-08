# Домашнее задание к занятию  «Защита хоста»

### Задание 1

1. Установите **eCryptfs**.
2. Добавьте пользователя cryptouser.
3. Зашифруйте домашний каталог пользователя с помощью eCryptfs.


*В качестве ответа  пришлите снимки экрана домашнего каталога пользователя с исходными и зашифрованными данными.*  

---

Установка eCryptfs:

![cry](https://github.com/OhotinDY/sdb-13-02/blob/main/cry1.pmg)

Создание пользователя cryptouser:

![cry](https://github.com/OhotinDY/sdb-13-02/blob/main/cry2.pmg)

Шифрование домашнего каталога пользователя с помощью eCryptfs:

```
sudo ecryptfs-migrate-home -u cryptouser
```

![cry](https://github.com/OhotinDY/sdb-13-02/blob/main/cry3.pmg)

Проверка домашнего каталога пользователя cryptouser с исходными и зашифрованными данными:

![cry](https://github.com/OhotinDY/sdb-13-02/blob/main/cry4.pmg)

### Задание 2

1. Установите поддержку **LUKS**.
2. Создайте небольшой раздел, например, 100 Мб.
3. Зашифруйте созданный раздел с помощью LUKS.

*В качестве ответа пришлите снимки экрана с поэтапным выполнением задания.*

---

Подготовка диска:

```
sudo apt install gparted
```

Установка LUKS и проверка установки:

```
sudo apt-get install cryptsetup
cryptsetup --version
```

Вывод информации о разделах:

![cry](https://github.com/OhotinDY/sdb-13-02/blob/main/cry5.pmg)

Шифрование созданного раздела с помощью LUKS:
- Подготовка раздела:

```
sudo cryptsetup -y -v --type luks2 luksFormat /dev/sdb1
```

![cry](https://github.com/OhotinDY/sdb-13-02/blob/main/cry6.pmg)

- Монтирование раздела:

```
sudo cryptsetup luksOpen /dev/sdb1 disk
 ls /dev/mapper/disk
```


