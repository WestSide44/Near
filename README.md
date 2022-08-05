# Установка узла NEAR Stakewars

Для установки узла Near использовал сервер CPX31 с конфигурацией: CPU: 4-Core/ RAM: 8GB DDR4 / Storage: 500GB SSD

Приверил совместимость функций CPU для установки узла , командой:

```
lscpu | grep -P '(?=.*avx )(?=.*sse4.2 )(?=.*cx16 )(?=.*popcnt )' > /dev/null \
  && echo "Supported" \
  || echo "Not supported"
```
> Supported

удостоверился что моя Linux-машина обновлена до последней версии использовав команду ```sudo apt update && sudo apt upgrade -y```

[![NEAR-1.png](https://i.postimg.cc/NGZNVv9B/NEAR-1.png)](https://postimg.cc/CdHHBtsQ)

установил  ```Node.js``` и ```npm```

Установил NEAR-CLI используя команду ```sudo npm install -g near-cli```

[![NEAR-3-CLC.png](https://i.postimg.cc/5NZF1WD3/NEAR-3-CLC.png)](https://postimg.cc/fJfbjpzt)

установил все необходимые иструменты разработчика командой : 

```sudo apt install -y git binutils-dev libcurl4-openssl-dev zlib1g-dev libdw-dev libiberty-dev cmake gcc g++ python docker.io protobuf-compiler libssl-dev pkg-config clang llvm cargo```

[![NEAR-2.png](https://i.postimg.cc/rz24MJxF/NEAR-2.png)](https://postimg.cc/RJGhTwgj)


далее утановил и настроил ```Python pip``` используя команду ```sudo apt install python3-pip```

установил Rust ```curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh ```

[![NEAR-RUst.png](https://i.postimg.cc/8kJmQGCy/NEAR-RUst.png)](https://postimg.cc/DmhXLtLs)
Клонировал ```nearcore``` репозиторий 

[![NEAR.png](https://i.postimg.cc/ydP47RnH/NEAR.png)](https://postimg.cc/JDGdqG96)

проверил коммит

[![NEAR.png](https://i.postimg.cc/9FfR5t1c/NEAR.png)](https://postimg.cc/rzvF54vH)

Собрал бинарные файлы ```cargo build -p neard --release --features shardnet```

[![NEAR.png](https://i.postimg.cc/RF53tkcR/NEAR.png)](https://postimg.cc/HJzsDPvc)

далее инициализировал рабочий каталог и загрузил генезис файл
```./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis```

[![NEAR-Genezis.png](https://i.postimg.cc/g0Sfxp8w/NEAR-Genezis.png)](https://postimg.cc/xkmsZWsY)

Скачал config.json с модифицированными параметрами ```
rm ~/.near/config.json 
wget -O ~/.near/config.json https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/config.json```

[![NEAR.png](https://i.postimg.cc/MpW6RWMt/NEAR.png)](https://postimg.cc/pp6MMMBn)


Создал и запустил сервис

[![NEAR.png](https://i.postimg.cc/T36w9z1N/NEAR.png)](https://postimg.cc/56sb9kw8)


Проверил логи ```journalctl -n 100 -f -u neard | ccze -A```

[![NEAR.png](https://i.postimg.cc/6pK9xCdM/NEAR.png)](https://postimg.cc/3dLMg4fG)


и убедился в полной синхронизации узла

[![image.png](https://i.postimg.cc/90dswtX0/image.png)](https://postimg.cc/XBvsT5C6)









Создал и активировал кошелек ```near login```


[![NEAR.png](https://i.postimg.cc/cC4nh6mm/NEAR.png)](https://postimg.cc/VrpvLf2r)

Создал переменные профиля и сохранил в ```.bash_profile```

[![NEAR.png](https://i.postimg.cc/t4zcpKhw/NEAR.png)](https://postimg.cc/G4HKjSgx)


сгенерировал фаил ключа командой ```near generate-key <pool_id>``` и скопировал сгенерированный файл в папку ```shardnet```
 
отредактировал файл согласно оффициальной инструкции 
[![NEAR.png](https://i.postimg.cc/wBphVCpw/NEAR.png)](https://postimg.cc/qN1hBZgK)
и запустил узел валидатора
 Создал и развернул Пул стейкинга 
 
 [![NEAR.png](https://i.postimg.cc/50ydZ7vL/NEAR.png)](https://postimg.cc/McCFBY9p)
 
 
 
 [![NEAR.png](https://i.postimg.cc/bN7nr4wY/NEAR.png)](https://postimg.cc/XpgqDH5t)
 
 
 
 
 изменил параметры комиссии пула и добавил в стейк 
 
 [![NEAR.png](https://i.postimg.cc/hjqvq7cK/NEAR.png)](https://postimg.cc/8FtNRc7Y)







