<p align="center">
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/header-dark.png"><img src="assets/header-light.png" width="100%" alt="Максим Никонов — Java Backend Developer, ищу стажировку"></picture>
<a href="https://github.com/nmaksimka/Delivery-Hub"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/deliveryhub-dark.png"><img src="assets/deliveryhub-light.png" width="100%" alt="DeliveryHub — сервис доставки еды на микросервисах и событиях: 10 сервисов, Kafka, сага, 1100+ тестов, Kubernetes"></picture></a>
<a href="https://github.com/nmaksimka/HB-system"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/hb-system-dark.png"><img src="assets/hb-system-light.png" width="33.33%" alt="HB-system — сервис дней рождения: вишлисты, бронь подарка, общий сбор и секретный чат"></picture></a><a href="https://github.com/nmaksimka/tasks-manager"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/tasks-manager-dark.png"><img src="assets/tasks-manager-light.png" width="33.33%" alt="tasks-manager — веб-приложение для личных задач с REST API"></picture></a><a href="https://github.com/nmaksimka/BadChess"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/badchess-dark.png"><img src="assets/badchess-light.png" width="33.33%" alt="BadChess — шахматы на Swing с ботом трёх уровней, часами и PGN"></picture></a>
<a href="https://github.com/nmaksimka/myPetUtil"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/mypetutil-dark.png"><img src="assets/mypetutil-light.png" width="33.33%" alt="myPetUtil — пиксельные питомцы для рабочего стола, гуляют по окнам"></picture></a><a href="https://github.com/nmaksimka/BugTrack"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/bugtrack-dark.png"><img src="assets/bugtrack-light.png" width="33.33%" alt="BugTrack — трекинг багов в студенческих проектах"></picture></a><a href="https://github.com/nmaksimka/PizzaConsoleApp"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/pizza-dark.png"><img src="assets/pizza-light.png" width="33.33%" alt="PizzaConsoleApp — консольный конструктор пиццы и заказов"></picture></a>
<a href="https://t.me/nknv_maks"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/contact-telegram-dark.png"><img src="assets/contact-telegram-light.png" width="25%" alt="Telegram @nknv_maks"></picture></a><a href="mailto:maksimnikonov407@gmail.com"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/contact-email-dark.png"><img src="assets/contact-email-light.png" width="25%" alt="Почта maksimnikonov407@gmail.com"></picture></a><a href="https://vk.com/gghrny"><picture><source media="(prefers-color-scheme: dark)" srcset="assets/contact-vk-dark.png"><img src="assets/contact-vk-light.png" width="25%" alt="ВКонтакте vk.com/gghrny"></picture></a><picture><source media="(prefers-color-scheme: dark)" srcset="assets/contact-location-dark.png"><img src="assets/contact-location-light.png" width="25%" alt="Томск, UTC+7"></picture>
<picture><source media="(prefers-color-scheme: dark)" srcset="assets/stack-dark.png"><img src="assets/stack-light.png" width="100%" alt="Стек: Java, Spring Boot, Spring Cloud, Spring Security, Hibernate / JPA, PostgreSQL, Flyway, Kafka, Redis, Elasticsearch, Keycloak, gRPC, Resilience4j, Thymeleaf, Docker, Kubernetes, Helm, GitHub Actions, Prometheus, Grafana, Gradle, Maven, JUnit 5, Testcontainers, Mockito, WireMock, Swing, JavaFX, React, TypeScript, Git, IntelliJ IDEA"></picture>
</p>

## Кейсы

<details open>
<summary><b>DeliveryHub</b> — доставка еды на микросервисах</summary>

**Задача.** Хотел собрать сервис доставки так, как его строят в продакшене: заказ проходит через ресторан, оплату и курьера, и ни один сбой не должен оставить его в подвешенном состоянии.

**Решение.** Разбил систему на 10 сервисов на Spring Boot 4 и Java 25. Сервисы общаются через Kafka с Avro-схемами, заказ ведёт сага с компенсациями, события не теряются благодаря outbox и inbox. Авторизация на своих JWT с ротацией refresh-токенов, корзина в Redis, поиск в Elasticsearch, курьеры назначаются по геоданным PostGIS, трекинг заказа идёт по WebSocket. Заказ ходит в ресторан по gRPC.

**Итог.** Больше 1100 тестов, включая интеграционные на Testcontainers и контрактные. CI на GitHub Actions собирает образы, деплой в Kubernetes через Helm, метрики и логи в Grafana. [Репозиторий →](https://github.com/nmaksimka/Delivery-Hub)

</details>

<details>
<summary><b>HB-system</b> — сервис дней рождения</summary>

**Задача.** Не забывать про дни рождения друзей и собирать подарок вместе так, чтобы именинник ничего не узнал заранее.

**Решение.** Сделали на хакатоне вдвоём, потом я доработал проект: сбор денег через Kafka с outbox и идемпотентными платежами, вход через Keycloak, бронь подарка с оптимистичной блокировкой, секретный чат на WebSocket, закрытый для именинника и на REST, и на подписке STOMP.

**Итог.** 7 сервисов за gateway, напоминания за 30, 7 и 1 день, новый интерфейс и больше сотни unit-тестов. [Репозиторий →](https://github.com/nmaksimka/HB-system)

</details>

<details>
<summary><b>tasks-manager</b> — менеджер личных задач</summary>

**Задача.** Простое приложение для задач, где каждый видит только свои и может работать и через сайт, и через API.

**Решение.** Spring MVC с Thymeleaf и REST API поверх одного сервисного слоя, Spring Security с «запомнить меня», PostgreSQL и миграции Flyway. Сделал фильтры, поиск, сортировки, светлую и тёмную тему и горячие клавиши.

**Итог.** 63 теста, в том числе интеграционные на Testcontainers с настоящим PostgreSQL. [Репозиторий →](https://github.com/nmaksimka/tasks-manager)

</details>

<details>
<summary><b>BadChess</b> — шахматы на Swing</summary>

**Задача.** В первой версии короля можно было просто съесть. Захотелось довести до настоящих шахмат.

**Решение.** Переписал движок со всеми правилами: рокировка, взятие на проходе, превращение, пат и ничьи. Проверил генерацию ходов perft-тестами. Добавил бота на минимаксе трёх уровней, шахматные часы, историю ходов, сохранение в PGN и темы доски.

**Итог.** Играбельные шахматы в одном jar и 52 теста на движок и бота. [Репозиторий →](https://github.com/nmaksimka/BadChess)

</details>

<details>
<summary><b>myPetUtil</b> — питомцы для рабочего стола</summary>

**Задача.** Сделать для себя и друзей пиксельных питомцев, которые живут на рабочем столе и не мешают работать.

**Решение.** JavaFX с прозрачными окнами, через JNA читаю окна Windows: питомцы ходят по низу экрана или по верхним краям окон, учитывают несколько мониторов и полноэкранные программы. Шесть персонажей, бросок с гравитацией, кормление перетаскиванием, трей и темы настроек. Сборка в exe через jpackage.

**Итог.** В версии 1.0.1 после профилирования CPU упал с 17 до 14% ядра, память со 230 до 155 МБ, размер сборки со 163 до 59 МБ. [Репозиторий →](https://github.com/nmaksimka/myPetUtil)

</details>

<details>
<summary><b>BugTrack</b> — трекинг багов</summary>

**Задача.** Реализовать систему по своим UML-диаграммам: проекты и команды, баги, триаж, исправление и проверка, релизы, отчёты.

**Решение.** Spring Boot 3.5 с Thymeleaf и Spring Security, PostgreSQL и Flyway, почта через SMTP, локально всё поднимается из Docker Compose. Каждое отступление от диаграмм записываю в отдельный документ, чтобы код и модель не расходились молча.

**Итог.** Сущности и схема по диаграммам, вход и регистрация, роли в проекте, демо-данные и тесты на Testcontainers. [Репозиторий →](https://github.com/nmaksimka/BugTrack)

</details>

<details>
<summary><b>PizzaConsoleApp</b> — консольный конструктор пиццы</summary>

**Задача.** Лабораторная: каталог ингредиентов, основ и бортиков, сборка пицц и заказ на компанию, где стоимость делится между гостями.

**Решение.** Перевёл проект на Maven с wrapper, исправил найденные ошибки в расчётах и ограничениях бортиков, разделил модель и консольный интерфейс.

**Итог.** Запускается одной командой, 39 тестов, README с описанием возможностей. [Репозиторий →](https://github.com/nmaksimka/PizzaConsoleApp)

</details>
