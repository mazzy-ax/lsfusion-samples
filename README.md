# lsfusion-samples

[project]:https://github.com/mazzy-ax/lsfusion-samples
[license]:https://github.com/mazzy-ax/lsfusion-samples/blob/master/LICENSE
[lsFusion]:https://lsfusion.org/
[docpage]:https://documentation.lsfusion.org/pages/viewpage.action?pageId=2228236
[IntelliJ IDEA]:https://www.jetbrains.com/idea/
[pgadmin]:https://www.pgadmin.org/

<img alt="logo" src="https://lsfusion.org/themes/lsfusion/assets/images/i-logo-lsfusion.svg" align="right">

Примеры для демонстрации возможностей платформы [lsFusion]. Описание [здесь][docpage]. 

Проект [lsfusion-samples][project] должен упростить жизнь тем, кто только начал знакомиться с [lsFusion].
Предполагается, что перед началом работы с примерами вы запускаете сервисы одной командой `docker-compose`,
а дальше работаете только внутри [IntelliJ IDEA].

Причем проект устроен так, что вам не нужно изучать и использовать maven-команды,
достаточно запускать конфигурации нужного вам модуля в [IntelliJ IDEA].

Оглавление:

* [lsFusion в браузере](#lsFusion-в-браузере)
  * [Необходимо установить (prerequisites)](#Необходимо-установить-prerequisites)
  * [Как запустить lsFusion в браузере](#Как-запустить-lsFusion-в-браузере)
  * [Как запустить pgadmin в браузере](#Как-запустить-pgadmin-в-браузере)
* [Desktop-клиент lsFusion](#Desktop-клиент-lsFusion)
  * [Необходимо установить (prerequisites) для desktop-клиента](#Необходимо-установить-prerequisites-для-desktop-клиента)
  * [Как запустить desktop-клиент](#Как-запустить-desktop-клиент)
* [Дополнительно: Docker plugin для IntelliJ IDEA](#Дополнительно-Docker-plugin-для-IntelliJ-IDEA)

## [lsFusion] в браузере

### Необходимо установить (prerequisites)

Предполагается, что вы уже установили на свой компьютер:

* [git](https://git-scm.com/download/)
* [docker](https://docs.docker.com/install/)
* [docker-compose](https://docs.docker.com/compose/install/)
* [IntelliJ IDEA]

  <details>
  <summary>
  Примечания:
  </summary>
  
  1. Для работы с демонстрационными примерами достаточно установить `Community Edition`
  1. На Ubuntu `IDEA Community Edition` можно найти в штатной утилите `Ubuntu software`
     или установить безо всяких заморочек через `snap`:

     ```
     sudo snap install intellij-idea-community --classic 
     ```
     
  </details>
     
* [lsFusion plugin](https://plugins.jetbrains.com/plugin/7601-lsfusion/) для [IntelliJ IDEA]

  <details>
  <summary>
  Как установить:
  </summary>

  * откройте `File \ Settings \ Plugins` в `IDEA`
  * найдите плагин `lsFusion` и нажмите `Install`
    
  </details>

### Как запустить [lsFusion] в браузере

Прежде всего склонируйте проект на свой компьютер:

```
$ git clone https://github.com/mazzy-ax/lsfusion-samples.git
```

Затем:

1. войдите в каталог проекта `lsfusion-samples`
1. выполните команду `docker-compose up -d` чтобы запустить сервер базы данных и `lsFusion-client`

    ```
    $ cd lsfusion-samples
    $ docker-compose up -d
    ```

1. откройте каталог проекта в `IntelliJ IDEA`

   * разрешите maven'у открыть pom.xml и синхронизировать зависимости
   * обязательно дождитесь пока maven загрузит все зависимости
   * иногда приходится делать повторную команду на синхрониацию зависимостей - нажмите `Reimport All Maven Projects` в окне Maven
   * перед первым билдом укажите Project SDK, который предпочитаете (File \ Project Structure \ Project Settings \ Project \ Project SDK)
    
1. выберите конфигурацию с примером. Например, `lsFusion server: hockeystats` (Run \ Edit configurations...)
1. запустите эту конфигурацию (Run \ Run 'lsFusion server: hockeystats')
1. откройте в браузере страницу по адресу `http://localhost:8080`

## Как запустить [pgadmin] в браузере

Прежде всего склонируйте проект на свой компьютер:

```
$ git clone https://github.com/mazzy-ax/lsfusion-samples.git
```

Затем:

1. войдите в каталог проекта `lsfusion-samples`
1. выполните команду `docker-compose up -d` чтобы запустить сервер базы данных и `lsFusion-client`

    ```
    $ cd lsfusion-samples
    $ docker-compose up -d
    ```

1. откройте в браузере страницу по адресу `http://localhost:5050`
1. в первый раз `pgadmin` спросит email и пароль администратора pgadmin

   * введите email: `pgadmin4@pgadmin.org`
   * введите пароль: `11111`
   
1. в первый раз `pgadmin` автоматически добавит сервер с базой данных и попросит пароль администратора `postgres`

   * введите пароль: `11111`
   * если хотите, установите галочку `Save password`

## Desktop-клиент [lsFusion]

### Необходимо установить (prerequisites) для desktop-клиента

* [git](https://git-scm.com/download/)
* [docker](https://docs.docker.com/install/)
* [docker-compose](https://docs.docker.com/compose/install/)
* [IntelliJ IDEA]
* [lsFusion plugin](https://plugins.jetbrains.com/plugin/7601-lsfusion/) для [IntelliJ IDEA]

  <details>
  <summary>
  Как установить:
  </summary>

  * откройте `File \ Settings \ Plugins` в `IDEA`
  * найдите плагин `lsFusion` и нажмите `Install`
    
  </details>

* [java](https://www.java.com) 8+

  <details>
  <summary>
  Примечание:
  </summary>
    
  в Ubuntu достаточно выполнить команду:
    
    ```
    sudo apt install default-jdk
    ```
    
  </details>
    
* (опционально) [IceTea Web Control](https://icedtea.classpath.org/wiki/IcedTea-Web) для запуска desktop-клиента [lsFusion] по jnlp-ссылке

  <details>
  <summary>
  Примечание:
  </summary>

  `IceTea Web Control` &mdash; это проект, который позволяет запускать
  Java-апплеты при помощи jnlp-ссылок.

  Когда билд модуля [lsFusion] подходит к концу, в log пишется jnlp-ссылка
  на desktop-клиента. Если нажать на нее, то `IceTea Web Control` автоматически запустит desktop-клиент.
  
  Если не установить `IceTea Web Control`, то desktop-клиент придется запускать вручную.

  </details>

  <details>
  <summary>
  Как установить:
  </summary>

  Инструкции по установке можно найти на сайте проекта [IceTea Web Control](https://icedtea.classpath.org/wiki/IcedTea-Web).
  На Ubuntu можно найти и установить в штатной утилите `Ubuntu software`. 

  Вы можете убрать назойливый splash, задав переменные окружения:

    ```
    ICEDTEA_WEB_PLUGIN_SPLASH=none
    ICEDTEA_WEB_SPLASH=none
    ```

  </details>

* (опционально) `jar-файл` с desktop-клиентом [lsFusion]

  Desktop-клиент `lsFusion` версии 2.1 можно скачать по ссылке: <https://download.lsfusion.org/java/lsfusion-client-2.1.war>

### Как запустить desktop-клиент

Прежде всего склонируйте проект на свой компьютер:

```
$ git clone https://github.com/mazzy-ax/lsfusion-samples.git
```

Затем:

1. войдите в каталог проекта `lsfusion-samples`
1. выполните команду `docker-compose up -d` чтобы запустить сервер базы данных и `lsFusion-client`

    ```
    $ cd lsfusion-samples
    $ docker-compose up -d
    ```

1. запустите desktop-клиент:

   * если у вас установлен `IceTea Web Control`, то кликните на jnlp-ссылку, которая появится в конце build-лога в информационном окне `Run`
   * или запустите `jar-файл` с desktop-клиентом lsFusion


## Дополнительно: Docker plugin для [IntelliJ IDEA]

[Docker plugin](https://plugins.jetbrains.com/plugin/7724-docker/) позволяет работать с докером непосредственно из [IntelliJ IDEA].
Плагин уже включен в `Ultimate edition`. В `IDEA Community edition` его нужно установить.

  <details>
  <summary>
  Как установить:
  </summary>

  * откройте `File \ Settings \ Plugins` в `IDEA`
  * найдите плагин `Docker` и нажмите `Install`
    
  </details>
