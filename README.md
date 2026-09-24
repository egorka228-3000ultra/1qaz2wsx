# Расписание группы

## Сайт

Для локального запуска создай `.env.local` по образцу `.env.example`, затем выполни:

```bash
npm install
npm run dev
```

Для Vercel добавь в Project Settings -> Environment Variables переменную
`VITE_SUPABASE_PUBLISHABLE_KEY`. Переменная `VITE_SUPABASE_URL` уже имеет резервное
значение в `main.js`, но ее тоже можно задать явно.

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

Для работы 24/7 размести `main.py` на Render, Railway или другом сервисе фоновых
процессов и добавь туда эти переменные окружения.