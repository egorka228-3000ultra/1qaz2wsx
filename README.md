# Расписание группы

## Сайт

Для локального запуска создай `.env.local` по образцу `.env.example`, затем выполни:

```bash
npm install
npm run dev
```

Для Vercel добавь в Project Settings -> Environment Variables:

```env
VITE_SUPABASE_URL=https://твой-проект.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=твой_publishable_или_anon_key
```

После добавления переменных запусти Redeploy. Supabase должен разрешать публичное
чтение таблиц `groups` и `schedule` через RLS-политики.

## Telegram-бот

Бот запускается отдельно от Vercel, потому что использует постоянный polling-процесс.
В `.env` нужны:

```env
BOT_TOKEN=токен_из_BotFather
SUPABASE_URL=https://твой-проект.supabase.co
SUPABASE_KEY=твой_publishable_или_anon_key
```

Установка и запуск:

```bash
pip install -r requirements.txt
python main.py
```

Для работы 24/7:

1. Загрузи проект в GitHub, не добавляя `.env`.
2. В Render создай `Background Worker` из этого репозитория.
3. Render автоматически использует `render.yaml`.
4. В Environment добавь `BOT_TOKEN` и `SUPABASE_KEY`.

Vercel нужен только для сайта. Telegram-бот и сайт используют одни и те же таблицы
Supabase, дополнительный Telegram-код в Supabase не требуется.