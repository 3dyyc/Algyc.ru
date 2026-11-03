# АЛГЫС — ювелирный салон

Статический интернет-магазин для GitHub Pages.

## Supabase
Сайт подключён к отдельному проекту **Algyc.ru** в организации **Satoru project v.2**:
- Project ref: `darjsihmkglmgsefdbfw`
- API URL: `https://darjsihmkglmgsefdbfw.supabase.co`
- Storage bucket: `algys-media`

Таблицы: `algys_categories`, `algys_products`, `algys_banners`, `algys_orders`, `algys_admin_users`.
Фотографии хранятся в отдельном публичном bucket `algys-media`. В браузере используется только publishable key; service-role key в репозитории отсутствует.

## Первый администратор
1. В Supabase → Authentication → Users создайте пользователя с нужной почтой (например, `vmamaev300@gmail.com`) и задайте ему пароль.
2. Откройте SQL Editor этого проекта и выполните:

```sql
insert into public.algys_admin_users (user_id)
select id
from auth.users
where lower(email) = lower('vmamaev300@gmail.com')
on conflict (user_id) do nothing;
```

3. В панели сайта войдите с этим email и паролем. Админ-доступ определяется членством в `algys_admin_users`, а не значением email на стороне браузера. RLS и Storage также проверяют членство.

## Публикация GitHub Pages
Откройте Settings → Pages:
- Source: Deploy from a branch
- Branch: `main`
- Folder: `/(root)`
- Save

Адрес: https://3dyyc.github.io/Algyc.ru/

## Заказы
Заказ сохраняется в `algys_orders` и открывает WhatsApp салона: +7 914 270-87-17. Наличие и окончательная стоимость подтверждаются менеджером.
