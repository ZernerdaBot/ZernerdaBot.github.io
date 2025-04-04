Пришло время обсудить, как [Zernerda бот](https://zernerda.pro/) обрабатывает ваши данные, и почему это может не соответствовать вашим ожиданиям.

Некоторые из вас могут быть знакомы с пирамидой потребностей Маслоу, где потребности человека распределяются по уровням, от самых базовых до более высоких. Без удовлетворения основных потребностей невозможно удовлетворить более сложные. Безопасность стоит на втором уровне, и как разработчик Zernerda, я считаю, что её нужно обеспечить на максимальном уровне перед тем, как двигаться дальше.

### Пополнение баланса

При пополнении баланса вам потребуется ввести строку из букв и цифр, зашифрованную алгоритмом AES-256. Это позволяет защитить ваши транзакции от связывания с IP, user-agent и другой информацией. Рекомендуется использовать универсальный email-адрес, например email@email.com, если требуется ввести почту.

### Хранящиеся данные

Мы используем базу данных SQLite для хранения следующих данных:

- **ID (INTEGER)**: Ваш Telegram ID.
- **Имя (TEXT)**: Имя вашего аккаунта.
- **Дата регистрации (TEXT)**: Дата первого запуска бота.
- **Запросы (INTEGER)**: Общее количество запросов.
- **Запросы за сутки (INTEGER)**: Успешные запросы за сутки.
- **Лимит запросов в сутки (INTEGER)**: Доступные запросы в сутки.
- **Доступ (INTEGER)**: Наличие возможности поиска.
- **Дата окончания подписки (TEXT)**: Дата окончания подписки.
- **Баланс (INTEGER)**: Баланс в боте.
- **Телефон (TEXT)**: Ваш телефон, хэшированный SHA-512.
- **Рефовод (INTEGER)**: ID рефовода.
- **Реферальная ссылка (TEXT)**: Случайно сгенерированная ссылка.

### Скрытие данных

Номер телефона используется для предотвращения несанкционированного удаления данных и проверки их принадлежности. Данные, которые вы хотите скрыть, дважды хэшируются SHA-512 и проверяются при каждом запросе. Если хэш совпадает, данные не выдаются.

### Логи

В логах отображаются активные поиски и техническая информация, но не собираются личные данные. Логи удаляются каждые 24 часа, и при входе с неавторизованного IP база данных удаляется, а мне отправляется уведомление.

### Зачем?

Почему я уделяю столько внимания защите данных? Я когда-то был обычным пользователем ботов и борцом за конфиденциальность. Мне хотелось бы, чтобы уже существовали боты, которые уважали бы конфиденциальность пользователей. Важные советы по использованию ботов:

- При первом запуске измените своё имя, чтобы минимизировать сбор данных.
- Отправляйте случайный контакт, если бот требует контактные данные.
- Для поиска используйте разнообразные запросы, не только свои данные.
- При пополнении баланса используйте универсальные email-адреса.

Актуальную версию бота всегда можно найти на сайте [https://zernerda.pro/](https://zernerda.pro/).

Я надеюсь, что эти советы окажутся полезными. Ваши собственные советы и замечания приветствуются в комментариях.

Этот пост не является рекламой. Я стремлюсь к тому, чтобы все боты и проекты уважали конфиденциальность своих пользователей и обеспечивали безопасность данных.
