# BC Portal — Quality & Performance

منصّة إدارة الجودة والأداء لمراكز الاتصال. React + TypeScript + Express + Drizzle + PostgreSQL.

## نشر Railway بخطوة واحدة

1. ادفع هذا المستودع إلى GitHub
2. [railway.app/new](https://railway.app/new) → **Deploy from GitHub repo** → اختر الريبو
3. من مشروع Railway: **+ New → Database → Add PostgreSQL** (يُضاف `DATABASE_URL` تلقائياً)
4. من خدمة `bc` → **Variables** → أضف:
   - `SESSION_SECRET` = نص عشوائي طويل
   - `OPENAI_API_KEY` = *(اختياري لتفعيل أنس)*
5. **Settings → Networking → Generate Domain**

Railway يبني وينشر تلقائياً. Admin افتراضي: `admin / admin123` (غيّرها فوراً من `/profile`).

## تشغيل محلي

```bash
npm install
cp .env.example .env    # عدّل DATABASE_URL و SESSION_SECRET
npm run db:push
npm run dev
```

## البنية

- `client/` — React 18 + Vite + Tailwind + shadcn/ui
- `server/` — Express 5 + Drizzle ORM + passport-local
- `shared/` — Drizzle schema (يستخدمه الطرفان)
- `script/` — سكربتات البناء والقاعدة

## المزايا

- **QC** — تقييمات الجودة مع مسار مراجعة وإقرار
- **APR** — رفع Excel لتقارير الأداء
- **Scorecards** — بطاقات أداء شهرية آلية
- **WFM** — جداول أسبوعية + بريكات + تبادل شفت
- **Attendance** — حضور مربوط بالجدول
- **Anas** — مساعد ذكي (OpenAI) داخل البورتل
- **Super Admin** — صلاحيات ديناميكية + Feature Flags

## المتغيّرات المطلوبة

| المتغيّر | إلزامي؟ | الوصف |
|----------|---------|-------|
| `DATABASE_URL` | ✅ | PostgreSQL connection string |
| `SESSION_SECRET` | ✅ | نص عشوائي طويل (32+ حرف) |
| `OPENAI_API_KEY` | ⭕ | لتفعيل مساعد أنس |
| `OPENAI_MODEL` | ⭕ | افتراضي `gpt-4o-mini` |
| `PORT` | ⭕ | Railway يضبطه تلقائياً |
