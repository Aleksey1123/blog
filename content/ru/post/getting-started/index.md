---
title: CI/CD
subtitle: Принципы, внедрение, инструменты

# Summary for listings and search engines
summary: 

# Link this post with a project
projects: []

# Date published
date: '2022-05-06T00:00:00Z'

# Date updated
lastmod: '2022-05-06T00:00:00Z'

# Is this an unpublished draft?
draft: false

# Show this page in the Featured widget?
featured: false

# Featured image
# Place an image named `featured.jpg/png` in this page's folder and customize its options here.
image:
  caption: 
  focal_point: ''
  placement: 2
  preview_only: false

authors:
  - admin

tags:
  - Academic

categories:
  - Demo
---

## Принципы

Концепция непрерывной интеграции и доставки (CI/CD) — основа наших тестирований. Для тех, кто не знает: CI/CD — концепция, которая реализуется как конвейер, облегчая слияние только что закомиченного кода в основную кодовую базу. Концепция позволяет запускать различные типы тестов на каждом этапе (выполнение интеграционного аспекта) и завершать его запуском с развертыванием закомиченного кода в фактический продукт, который видят конечные пользователи (выполнение доставки).

CI/CD необходимы для разработки программного обеспечения с применением Agile-методологии, которая рекомендует использовать автоматическое тестирование для быстрой наладки рабочего программного обеспечения. Автоматическое тестирование дает заинтересованным лицам доступ к вновь созданным функциям и обеспечивает быструю обратную связь.

Недавно я настраивал конвейерную обработку CI/CD для проекта as-of-yet-under-wraps, который предназначен для местных профессионалов, испытывающих трудности с поиском работы. Далее я расскажу, что сделал, и поделюсь своими мыслями о CI/CD.

Содержание

Мы рассмотрим принципы CI/CD.

Первый принцип CI/CD: сегрегация ответственности заинтересованных сторон.
Второй принцип CI/CD: снижение риска.
Третий принцип CI/CD: короткий цикл обратной связи.
Реализации среды в CI/CD.
Инструменты для CI/CD.
Приступим.

Первый принцип CI/CD: сегрегация ответственности заинтересованных сторон
Одним из основных преимуществ CI/CD является своевременное участие различных заинтересованных сторон в любом проекте.

Разработчики и дизайнеры (Devs) создают опыт и логику продукта, представленные в рассказах пользователей, и несут ответственность за создание работающий функций, доказывая это через модульные тесты.

Инженеры по качеству (QE) отвечают за поддержание качества продукции, просмотр функций по мере их выполнения (см. определение «Готово») и вводят сквозные (E2E) функции / приемочные тесты, чтобы установить, что клиент получит продукт работающий без ошибок.

Бизнес-аналитики (BAs) и владельцы продуктов (POs) несут ответственность за приемлемость (например, стоимость бизнеса), что подтверждается взаимодействием с фактическими пользователями и созданием пользовательских историй. Они координируют и анализируют результаты приемочных тестов для проверки рассказов пользователей и, возможно, создания новых, основанных на отзывах.

Оперативный отдел (Ops)/ DevOps-инженеры несут ответственность за доступность продукта пользователям. Работая в области CI/CD, они масштабируют концепции по мере необходимости и разрабатывают логистику кода, чтобы код от разработчиков мог перейти в производственную среду и пользователи могли получать доступ.

Пользователи несут ответственность за использование продукта. Подразумевается, что продукт должен быть полезен и оправдывать усилия.

Каждый этап конвейерной обработки CI/CD создает среду, настроенную на то, чтобы группы брали ответственность за соответствующую стадию тестирования, обеспечивая целостность процесса.

Второй принцип CI/CD: снижение риска

Каждый этап конвейерной обработки CI/CD создается для снижения риска в определенном аспекте. Разработчики отвечают за логические и письменные тесты, чтобы снизить риск нарушения логики. QE отвечают за целостность потока пользователей и записывают тесты для снижения риска сломанных потоков/ историй пользователей. BAs и POs отвечают за удобство использования и принимают участие в приемочных тестах пользователей, чтобы снизить риск создания непригодных / нежелательных функций. Ops/ DevOps несут участвуют в обслуживании CI/CD, связанные с развертыванием операций (анализ схемы данных/ миграции данных) и масштабирование, чтобы снизить риск недоступности продукта.

Поскольку этапы предназначены для снижения конкретного риска, важно отметить, что при настройке конвейерной обработки каждый этап должен также служить шлюзом для контроля качества, который предотвращает прохождение поврежденных/ нежелательных функций.

Третий принцип CI/CD: короткий цикл обратной связи

Причина внедрения конвейерной обработки CI/CD — использование машин для работы с людьми. Это позволяет сократить время, затрачиваемое на обратную связь по разрабатываемым функциям.

Но почему выгоднее использовать машины? Потому что люди не масштабируются, как машины. С помощью масштабирования сокращается время, затрачиваемое на тестирование программного обеспечения, что позволяет автоматизировать процесс развертывания. Эти процедуры займут гораздо больше времени, если будут выполняться человеком.

Однако в ошибкоопасных ситуациях, требующих ввода данных человеком, автоматизация может быть нежелательной/ невозможной. Например, мы никогда не сможем автоматизировать тестер, когда дело доходит до удобства использования. Еще одним важным примером является миграция производственных данных. Автоматизируйте логистику кода (как код упакован/ перемещается между этапами), насколько это возможно, но имейте в виду: автоматизация в конечном итоге предназначена для сокращения времени, затрачиваемого на получение закомиченного кода. Если присутствуют ошибки, которые требуют больше времени для исправления, чем для предотвращения, избегайте автоматизации и старайтесь достичь короткого цикла обратной связи.

Реализации среды в CI/CD

Мы рассмотрим различные среды реализации CI/CD и то, что происходит на каждом этапе, ссылаясь на реализацию в проектах, над которыми я работаю. Каждая среда представлена как ветвь репозитория системы контроля кода.

Разработка

Наша команда разработчиков немногочисленна, поэтому мы используем разработку на базе магистралей, где все коммиты попадают в единую ветвь. Эта ветвь служит средой разработки и запускает тесты модулей/ систем на всех закомиченных кодах. Текущая версия ветви разработки проходит контроль качества (ветвь qa) и развертывается приложении, чтобы все разработчики могли просматривать, тестировать и проверять работоспособность кода, что обеспечивает совместную разработку.

Контроль качества

Продукт проходит процесс сборки, а тесты модулей/ систем снова запускаются в среде с конфигурациями производства на уровне приложений. Код развертывается в QA-версии нашей платформы, а тесты функций запускаются два раза в день. При прохождении регрессионных тестов код в ветви qa продвигается к ветви uat.

Проверка приемлемости

Мы разрешаем доступ к POs, чтобы оценить, были ли созданы функции, поскольку они были предусмотрены и переданы через пользовательские истории. При принятии посредством тестирования с выбранной группой пользователей истории, отмеченные как принятые, будут выпущены в продуктив при следующем развертывании.

Тестирование интеграционных систем

На этом этапе мы разворачиваем приложение в среде, которая имитирует производственную среду и запускает тесты, чтобы подтвердить работоспособность программного обеспечения. Также мы запускаем нефункциональные тесты, такие как тестирование нагрузки и тестирование безопасности, чтобы подтвердить, что приложение будет безопасным. Когда все тесты пройдут, мы наконец достигнем…

Производство

Пользователи получают возможность оценивать выпущенные функции.

Инструменты для CI/CD
Локальные

GitLab CI, TeamCity, Bamboo, GoCD Jenkins, Circle CI.

Облачные

BitBucket Pipelines, Heroku CI, Travis, Codeship, Buddy CI, AWS CodeBuild.

Правительственные

hats, Nectar.

Наша команда использует GitLab в качестве репозитория кода и лидера CI из-за требований локального хостинга. В других проектах мы используем альтернативные варианты, предлагающие локальные опции, — Bamboo от Atlassian, TeamCity от JetBrains и GoCD от ThoughtWorks. Jenkins и CircleCI мы еще не использовали в наших проектах. (Оставьте комментарий, если вы когда-нибудь их использовали и удовлетворены этим.)

Если у вас нет потребности в локальном хостинге, существует множество других облачных инструментов CI, таких как Codeship, Buddy CI и Travis. Для личных проектов все большее число репозиториев кода предоставляют решение «все-в-одном», которое дает доступ к инструментам CI. Недавно BitBucket запустил свой собственный бесплатный CI под названием Pipelines, ограниченный вычислительным временем, как и Heroku. GitHub также имеет бесплатную интеграцию с Travis, на случай если ваш проект — открытый исходный код. Если вы работаете в Amazon Web Services и получаете небольшой бюджет, то имейте в виду, что Amazon имеет собственные CI и CodeBuild.

Для тех, кто работает в правительстве и хочет улучшить качество своих приложений, которые не могут быть размещены в общедоступном облаке, мы создали несколько готовых версий. Они разрешают работать с недавно запущенным решением — Hive Agile Testing Solution, которое позволяет запускать регрессионные тесты в вашем приложении, чтобы гарантировать, что функции не сломаются при обновлении платформы. Создание современного веб-приложения требует тестов для обеспечения соответствия государственной политики и среды развертывания? Используйте Nectar — платформу как услугу для государственных приложений. Она обеспечивает тестирование соответствия, а также развертывание в облаке правительства для приложений, созданных с использованием новейших технологий и методологий.
