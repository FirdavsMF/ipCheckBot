## ipCheckBot
Бот для проверки IP информации
#### Commands:
-Для обычного пользователя:
  - "/ip [some_ipV4]" - показать информацию о <some_ipV4> 
  - "/history" - показывает все ваши запрошенные IP-адреса
- Для амина:
  - "/admin_new [user_id]" - добавить к пользователю с <user_id> права администратора
  - "/admin_delete [user_id]" - забрать у пользователя с<user_id> права администратора
  - "/admin_user_history [user_id]" - показать все запросы пользователя с <user_id>
  - "/admin_send_all [msg]" - Отправить <msg> всем знакомым пользователям ботов

#### Back-end (response in JSON):
- GET "${CLOUD_FUNCTION_URL}/API/${TELEGRAM_BOT_TOKEN}/add_admin?id={user_id}" - добавить к пользователю с <user_id> права администратора
- GET "${CLOUD_FUNCTION_URL}/API/get_users" -предоставить информацию обо всех пользователях в базе данных бота
- GET "${CLOUD_FUNCTION_URL}/API/get_user?id={user_id}" - дать информацию о пользователе с<user_id>
- GET "${CLOUD_FUNCTION_URL}/API/get_history_by_tg?id={user_id}" - дать информацию об ip в пользователе с <user_id> история
- GET "${CLOUD_FUNCTION_URL}/API/get_global_history" - дать историю IP всех пользователей
- GET "${CLOUD_FUNCTION_URL}/API/get_history_by_tg?id={history_ID}" - удалить одну строку истории с идентификатором <history_ID>

### Настраивать
Для запуска бота необходимо создать файл `.env` с varibales среды:
```env
TELEGRAM_BOT_TOKEN="Your_bot_telegram_token"
IPSTACK_ACCESS_KEY="Your_access_key_for_api_ipstack"
CLOUD_FUNCTION_URL="Your_hosting_url_or_tunnel_to_localhost"
```
Затем просто запустите в корне этого репозитория
```shell
docker-compose up
```
